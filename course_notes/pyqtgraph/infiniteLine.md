---
date: 2024-02-26T09:28:00
---
Add infiniteLine:
```python
signal_start_pos = int(self.signal_start_spbx.value())

signal_span = int(self.signal_span_spbx.value())

ref_start_pos = int(self.ref_start_spbx.value())

ref_span = int(self.ref_span_spbx.value())

signal_stop_pos = signal_start_pos + signal_span

ref_stop_pos = ref_start_pos + ref_span



data_pen = pg.mkPen(color='b', width=1)

ref_pen = pg.mkPen(color='g', width=1)


data_start = generate_infinite_line(pen=data_pen,pos=signal_start_pos,label='start')

data_stop = generate_infinite_line(pen=data_pen,pos=signal_stop_pos,label='stop')

ref_start = generate_infinite_line(pen=ref_pen,pos=ref_start_pos,label='start')

ref_stop = generate_infinite_line(pen=ref_pen,pos=ref_stop_pos,label='stop')

plot.addItem(self.data_start)

plot.addItem(self.data_stop)

plot.addItem(self.ref_start)

plot.addItem(self.ref_stop)
```
InfiniteLine signals:
![[Pasted image 20240226093100.png]]
```python
data_start.sigPositionChangeFinished.connect(self.reset_infinite_line_spbx_value)
```
Set and get value:
```python
#set
data_start.setValue(signal_start_pos)
#get
data_start.value()
```