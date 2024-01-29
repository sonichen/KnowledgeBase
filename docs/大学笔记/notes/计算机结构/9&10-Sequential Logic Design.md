---
title: '9&10-Sequential Logic Design '
updated: 2021-01-04T17:00:31.0000000+08:00
created: 2020-11-14T10:08:09.0000000+08:00
---

Combinational logic is where the output of a digital circuit is produced by combining the inputs in a manner defined by the logic.
Sequential logic is where the output of a digital
circuit depends on both the inputs and also on the
previous output state of the circuit.

一，two main classes of digital logic
1，Combinational Logic'

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>输入的改变会马上影响输出，而且还有延迟问题</p>
<p>If the inputs A and B should change, then a change would be immediately propagated to the output f. There would be a small propagation delay, of approximately three gate delays, before the correct output became available</p>
<p>![image1](../../assets/4da36340e6a848958f16d84ec1ddf5b8.png)</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
![image1](D:\Workplace\github\soni_notes\docs\基础课笔记\notes\计算机结构\assets\4da36340e6a848958f16d84ec1ddf5b8.png)

2'Sequential Logic'.
makes use of **flip-flops to generate circuits**
whose **outputs are time dependent** and are a function of both
the inputs to the circuit and the current state of its outputs.

3，basic flip-flop circuit operation
假设A=1, B=1, --\>C=0 and D=1.
![image2](../../assets/a7940a91761745b29505cf322e9d9f32.png)

![image3](../../assets/b0328bc4e0054078b8c435a7350f04f8.png)
at time 0, when A=1 and B=1, the output values were C = 0
and D = 1.
Now, at time 5Dt, when A=1 and B=1, the output values are C = 1
and D = 0.
The circuit is seen to be bistable.

二

![image-20240129111458321](assets\image-20240129111458321.png)


三、
如果这个电路被放置在J-K触发器的输入端，所产生的电路称为边缘触发J-K触发器。这种触发器在时钟从一个逻辑电平转换到另一个逻辑电平时锁存输入值。
Pulse Shaper Circuit
![image16](../../assets/3b31ac4775ac4a318f227d34d6ccdebe.png)

![image17](../../assets/f8775eab03724ebe95d2f6d03f84be68.png)

