---
date: 2024-02-27T12:37:00
---
When you use such code:
```python
task = nidaqmx.Task()
channel = task.ci_channels.add_ci_count_edges_chan(

    counter='Dev2\ctr0',

    edge=Edge.RISING,

    count_direction=CountDirection.COUNT_UP

)
```
`channel` 将返回`CI_CHANNEL` 类实例，具有很多可以设置的property，一下是edge counting可能用到的properties：

```python
property chan_type
```
Indicates the type of the virtual channel.
Type: [`nidaqmx.constants.ChannelType`](https://nidaqmx-python.readthedocs.io/en/latest/constants.html#nidaqmx.constants.ChannelType "nidaqmx.constants.ChannelType")


```python
property channel_names
```
Specifies the unflattened list of the virtual channels.
Type: List[str]
```python
task = nidaqmx.Task()
channel = task.ci_channels.add_ci_count_edges_chan(

    counter='Dev2/ctr0',

    name_to_assign_to_channel='counter0',

    edge=Edge.RISING,

    count_direction=CountDirection.COUNT_UP

)

print(channel.chan_type)

print(channel.channel_names)
#returns
#ChannelType.COUNTER_INPUT 
#['counter0']
```
![[Pasted image 20240227131555.png]]
![[Pasted image 20240227131605.png]]
![[Pasted image 20240227132558.png]]
- `nidaqmx.constants.TerminalConfiguration.DEFAULT`: 默认配置。
- `nidaqmx.constants.TerminalConfiguration.NRSE`: 非参考单
- （Non-Referenced Single-Ended）。
- `nidaqmx.constants.TerminalConfiguration.RSE`: 参考单端（Referenced Single-Ended）。(参考GND)
	NI-6363没有这个选项
![[Pasted image 20240227132837.png]]
	NI-6363没有
![[Pasted image 20240227133022.png]]
![[Pasted image 20240227133221.png]]

Reset counts and terminal setting：
![[Pasted image 20240227133845.png]]
![[Pasted image 20240227134050.png]]`   ci_count_edges_count_reset_thresh_voltage` 是 `CI_CHANNEL` 的一个属性，用于指定识别计数复位事件的电压水平。这个属性的类型是 `float`，表示电压水平。
![[Pasted image 20240227134207.png]]与`add_ci_count_edges_chan`里的edge参数传递的信息一致
![[Pasted image 20240227135452.png]]![[Pasted image 20240227135500.png]]
NI-6363的counter没有gate的选项
![[Pasted image 20240227135712.png]]![[Pasted image 20240227135729.png]]