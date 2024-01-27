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
<table>
<colgroup>
<col style="width: 4%" />
<col style="width: 32%" />
<col style="width: 12%" />
<col style="width: 10%" />
<col style="width: 14%" />
<col style="width: 11%" />
<col style="width: 13%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>电路图</th>
<th>State table</th>
<th>Characteristic table</th>
<th>Excitation table</th>
<th>K-M</th>
<th>Characteristic equation</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>D</td>
<td>![image4](../../assets/8dc24e90469945738ef1c0b458abf9dd.png)</td>
<td>![image5](../../assets/5bc07ef9b9994ff1844341e8689441c3.png)</td>
<td><p>![image6](../../assets/7c797f35136b46a5a1049e588bca4391.png)</p>
<p></p></td>
<td><p>![image7](../../assets/4b70aeed71354d8ab9a9fc9b1c8ff8cd.png)</p>
<p></p></td>
<td><p>![image8](../../assets/755c2b69c5c846529e5083d3c2c7bcbd.png)</p>
<p></p></td>
<td><p>![image9](../../assets/958ca0f216fd4bf0ab29d5c3c9bc86e8.png)</p>
<p></p></td>
</tr>
<tr class="even">
<td>Master-Slave JK</td>
<td><p>![image10](../../assets/685e6b383f254ba48f85ef51febcfcf3.png)</p>
<p></p></td>
<td><p>![image11](../../assets/ccd8219091c94f249aed5d811ee6125f.png)</p>
<p></p></td>
<td><p>![image12](../../assets/fffed3ded51547d2946fcc23a86f0345.png)</p>
<p></p></td>
<td><p>![image13](../../assets/c3b3c128a663421b93339eb7b14b63a8.png)</p>
<p></p></td>
<td><p>![image14](../../assets/8b9651c9867741b184c03a4dd144bae4.png)</p>
<p></p></td>
<td><p>![image15](../../assets/5bc0a207c6fd47ea8da2f9fb69541940.png)</p>
<p></p></td>
</tr>
</tbody>
</table>

三、
如果这个电路被放置在J-K触发器的输入端，所产生的电路称为边缘触发J-K触发器。这种触发器在时钟从一个逻辑电平转换到另一个逻辑电平时锁存输入值。
Pulse Shaper Circuit
![image16](../../assets/3b31ac4775ac4a318f227d34d6ccdebe.png)

![image17](../../assets/f8775eab03724ebe95d2f6d03f84be68.png)

