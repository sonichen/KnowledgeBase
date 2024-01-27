---
title: 9-D,JK,主从JK
updated: 2020-12-22T10:33:28.0000000+08:00
created: 2020-11-14T10:47:57.0000000+08:00
---

2，D Flipflop【保存值，输入=输出】
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>1 电路</p>
<p>![image1](../../assets/821b05e3a8fa47a7b7b64b0ea3f27cde.png)</p>
<p></p>
<p>![image2](../../assets/6904ca1662cd4450a562daa874c66511.png)</p>
<p>2 state table</p>
<p>![image3](../../assets/a89998ed35b341aeae16daab5cac1691.png)</p>
<p></p>
<p></p>
<p>3 symbol</p>
<p>4 requirement table</p>
<p>![image4](../../assets/0d246a053cd14189b7ada6289e53ce4a.png)</p>
<p></p>
<p>5 next state</p>
<p>![image5](../../assets/2debb9b4000a4ae3a07fcf41df3bcc65.png)</p>
<p>6 state diagram</p>
<p>![image6](../../assets/afbce0023bfc46ea895b6510b20ee91b.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

3,JK
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>1 电路</p>
<p>![image7](../../assets/c1b02a9b4acc49fdb83727f40bbc3d9e.png)</p>
<p>2 state table</p>
<p>![image8](../../assets/4bf4a3216b2d44e2ad1363c8f88b4120.png)</p>
<p>3 symbol</p>
<p>4 requirement table</p>
<p>![image9](../../assets/91a30fbcb0314405b9b90a54bad7258b.png)</p>
<p>5 next state</p>
<p>![image10](../../assets/0c501a81bfc345b081e5cd6b76ee70a2.png)</p>
<p>6 state diagram</p>
<p>![image11](../../assets/7c0ac29e14f24a119bc1069826304eec.png)</p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

4，主从SR触发器 Master-Slave SR flipflop
![image12](../../assets/c062a12e7f0844b9b8e18f5ec62a01be.png)
Clock=1，master flipflip影响output，slave device is disabled并且它的结果不变
Clock=0, slave flipflop影响output。Master flipflop is now disabled so its outputs are unchanged during this LOW clock
cycle.

