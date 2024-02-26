---
date: 2024-02-26T09:25:00
---
    python
    plot = pg.PlotWidget(enableAutoRange=True, useOpenGL=True)
        graph_widget_layout = QVBoxLayout()
        graph_widget_layout.addWidget(plot)
        frame.setLayout(graph_widget_layout)
        plot.setLabel("left", ylabel)
        plot.setLabel("bottom", xlabel)
        plot.setTitle(title, color='k')
        plot.setBackground(background=None)
        plot.getAxis('left').setPen('k')
        plot.getAxis('left').setTextPen('k')
        plot.getAxis('bottom').setPen('k')
        plot.getAxis('bottom').setTextPen('k')
        plot.getAxis('top').setPen('k')
        plot.getAxis('right').setPen('k')
        plot.showAxes(True)
        plot.showGrid(x=False, y=True)
        curve = plot.plot(pen=pg.mkPen(color=(255,85,48), width=2))
        curve.setData(tcspc_x, tcspc_y) # add plot
