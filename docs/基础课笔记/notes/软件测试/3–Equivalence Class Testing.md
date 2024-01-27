---
title: '3–Equivalence Class Testing  '
updated: 2021-01-03T14:38:24.0000000+08:00
created: 2020-09-13T13:23:34.0000000+08:00
---

一，基本了解
1，Functional Testing
别名：Black-Box Testing ,Specification-Based Testing
优点：助我们选择有效的有错误的子测试
缺点：无法确定测试的系统个数
2，
Techniques
Each was developed to cover a particular aspect of the specification
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Equivalence Class Testing</p>
<p>Boundary Value Testing</p>
<p>Combinational Testing</p>
<p>Sequential (State-based) Testing</p>
<p>Testing with Random Data</p>
<p>Error Guessing/Expert Testing</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

3，Equivalence Class Testing
A，概述
（1）将测试用例的数量减少到一个可管理的水平，同时保持合理的测试覆盖率。
（2）将输入域或输出范围分割为有限数量的子域/子范围(即分区或价类)
（3）选一个代表值测试
（4）如果被测试的软件使用代表值通过，测试时，我们假设等价类中的所有值都是正确的
B，性质
互斥 and collectively exhaustive

![image1](../../assets/209e09b61a454d009aaf910bcf7a67ec.png)

二，等价测试的步骤
1，步骤
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>1，根据题目，分析出所有的输入和输出的可能性【合法+非法】</p>
<p>输入的数：如果是连续范围，要全覆盖；如果是一个集合，所有情况都包含</p>
<p></p>
<p>2，列出Test Case</p>
<p>（1）要写出非法输入和不预期出现的值</p>
<blockquote>
<p>非法的值标志*，<strong>(*)表示错误(此时的错误不代表false)的test，必须被单独测试</strong></p>
</blockquote>
<p></p>
<p>3，Test Data</p>
<p>（1）根据指定范围选取代表值作为测试数据</p>
<blockquote>
<p>非法的放在最后一起测，非法不要和合法的一起测试</p>
</blockquote>
<p>（2）再次出现的值打[]</p>
<p></p>
<p>4，进行测试</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

案例
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>2，案例</p>
<p></p>
<p>![image2](../../assets/8d32fd1fe05c42c6aebdca3c5ad6268b.png)</p>
<p></p>
<p>1，根据题目，分析出所有的输入和输出的可能性【合法+非法】</p>
<p>输入的数：如果是连续范围，要全覆盖；如果是一个集合，所有情况都包含</p>
<p>![image3](../../assets/524bcee1f34649c6a7e9623349e2aa34.png)</p>
<p>2，列出Test Case</p>
<p>（1）要写出非法输入和不预期出现的值</p>
<blockquote>
<p>非法的值标志*，<strong>(*)表示错误(此时的错误不代表false)的test，必须被单独测试</strong></p>
</blockquote>
<p></p>
<p>![image4](../../assets/f93d0a868af44c63b8f02dbe9421407a.png)</p>
<p></p>
<p>3，Test Data</p>
<p>（1）根据指定范围选取代表值作为测试数据</p>
<p>非法的放在最后一起测，非法不要和合法的一起测试</p>
<p>（2）再次出现的值打[]</p>
<p>![image5](../../assets/4a800a220bbe4265a1f14a8dd73ad052.png)</p>
<p></p>
<p>完善test case</p>
<p>![image6](../../assets/8cf61d413d854667961ee3216ced14c7.png)</p>
<p></p>
<p>4，进行测试</p>
<p></p>
<p>![image7](../../assets/4c9217246b9f4b6b8af198580649d08b.png)</p>
<p></p>
<p></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
2，测试方式
方法1：A Naïve Approach

![image8](../../assets/7e8db697ea044aa69d68d548c6e53d07.png)

方法2：Using Testing Frameworks
![image9](../../assets/449f497b57d849b694905932ca9d05a3.png)

方法3【常用】
![image7](../../assets/4c9217246b9f4b6b8af198580649d08b.png)
![image10](../../assets/216b24c7c9fa47998ac680ce50c4d77b.png)

3，导入数据方式
导入数据方式【少量数据时】
方法1
![image7](../../assets/4c9217246b9f4b6b8af198580649d08b.png)
方法2
![image11](../../assets/0ccbea9b21a34996bc635fa87c8c9437.png)

导入数据方式2【大量数据】
![image12](../../assets/46d998bbabb3477da292e4752919b683.png)

| @DisplayName   | 测试的名字                         |
|----------------|------------------------------------|
| @Parameterized | 参数化测试使用不同参数多次运行测试 |

<table>
<colgroup>
<col style="width: 92%" />
<col style="width: 7%" />
</colgroup>
<thead>
<tr class="header">
<th><p>@CsvSourse（{数据1，数据2，数据三1}）</p>
<p>![image13](../../assets/f87d282d4d474505a6c6e18c05248875.png)</p>
<p></p></th>
<th>在此处输入要测试的数据，此时输入的都为字符串类型，在对应的方法中，数据会自动转换成所要求的类型</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>@CsvFileSource(resources="文件路径")</p>
<p>![image14](../../assets/b7fc0795ea8f4fcc805816aee08e3120.png)</p>
<p></p></td>
<td>通过excel文件来获取数据，文件存放的只允许是基本数据类型和字符串</td>
</tr>
</tbody>
</table>

5，其他测试
5.1，Weak Normal Equivalence Class Testing
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>弱正规测试</p>
<p>1.在测试用例中从每个等价类中使用一个变量（单故障假设）</p>
<p>2.在期望值比较低的时候，可以使用此方法</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

5.2 Strong Normal Equivalence Class Testing
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>测试所有有效域的组合(多故障假设)</strong></p>
<p>它的测试用例数量等于所有参数的有效域数量的乘积。</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

5.3Weak Robust Equivalence Class Testing
<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p>每个有效和无效域的一个测试用例(单一故障假设)</p>
<p></p>
<p>仍然基于单一故障假设，但测试有效和无效域,比弱正规等价类测试强</p>
<p>注意如何为无效域选择测试用例(提示:假设单个故障)</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

5.4Strong Robust Equivalence Class Testing
**测试有效和无效域的所有组合(多故障假设**

完全符合完整性和不完整性的性质(全面)
执行这样一个完整的测试可能太耗时。
•根据软件设计过程的不同，可能根本不需要一个健壮的测试

5.5
![image15](../../assets/ad346c5c6f1a4044b5a79c6e11806ee1.png)
| Weak Normal Equivalence Class Testing   | 部分样本的有些范围       |
|-----------------------------------------|--------------------------|
| Strong Normal Equivalence Class Testing | 所有的有效范围           |
| Weak Robust Equivalence Class Testing   | 部分有效范围和无效范围   |
| Strong Robust Equivalence Class Testing | 所有的有效范围和无效范围 |

6，Design-by-Contract vs. Defensive Design
不同情况选择不同测试
![image16](../../assets/5fc42a4b1dde462fbc63e16273795b0c.png)

