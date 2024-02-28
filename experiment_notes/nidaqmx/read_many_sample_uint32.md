使用方式：
```python
from nidaqmx.stream_readers import CounterReader
reader = CounterReader(task.in_stream)
number_of_samples = 100
data_array = np.zeros(number_of_samples,dtype=np.uint32)
reader = CounterReader(task.in_stream)
reader.read_many_sample_uint32(
    data=data_array,
    number_of_samples_per_channel=number_of_samples,
    timeout=10
)
```
==**读取逻辑**==：
1. 在`task.start()`之后DAQ卡即开始读数，其数据会实时更新在`channel.ci_count`里面，但是`read_many_sample_uint32`读取的数据只会在clock信号到达之后即pulse_streamer的信号到达后开始计数。
2. `read_many_sample_uint32`函数只有在把number_of_samples长度的数据读取完后才能`print`或者其他的方式处理data_array，否则nidaqmx会报错：nidaqmx.errors.DaqReadError: Some or all of the samples requested have not yet been acquired.
3. 当clock信号和和signal信号同时到达DAQ卡时，DAQ卡仍会计数
4. DAQ卡会依据时钟信号把数据存储在缓存里，每次读取的数据会按缓存里的顺序读取。例如下面这样的一个信号，$D_0$ 为signal，$D_1$为gate，重复10次。DAQ卡设置`number_of_samples = 10`，pulse streamer的信号可以很快就能运行完，但是DAQ卡读取数据可以很慢，读取10次可以将所有的数据读取完，读取的数据如下：
   [0,1,3,6,10,15,21,28,36,45]
   [55,56,58,61,65,70,76,83,91,100]....
![[Pasted image 20240228142659.png]]