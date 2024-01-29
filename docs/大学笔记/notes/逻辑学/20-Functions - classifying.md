---
title: 20-Functions - classifying
updated: 2020-08-15T15:52:54.0000000+08:00
created: 2020-08-15T15:22:28.0000000+08:00
---

## 一、Domain, codomain and image
![image1](../../assets/092ae7ae09b246feb4ea8e3df0f47e18.png)

![image2](../../assets/0c1adfcec7eb4ea292dcebbb38a923b2.png)

## 二、Injective and Surjective Functions
For any sets sets X and Y and a function f ⊆ X ×Y, we say that the function f is:
<table>
<colgroup>
<col style="width: 13%" />
<col style="width: 86%" />
</colgroup>
<thead>
<tr class="header">
<th>Injective</th>
<th><p>(one-to-one) if each element in the image is mapped to by just one element in the domain; that is, if(∀x,y ·(x ∈ X ∧y ∈ X ∧f (x) = f (y)) → x = y)</p>
<p>Eg.Hash Tables</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>surjective</td>
<td><p>(onto) if each element in the codomain is mapped to by at least one element in the domain; that is, if (∀z ·z ∈ Y → (∃x ·x ∈ X ∧f (x) = z))</p>
<p><strong>For a surjective function the image is the whole codomain</strong></p></td>
</tr>
<tr class="even">
<td>bijective</td>
<td><p>if it is both injective and surjective.</p>
<p>Thus if there is a bijection between two sets, then those sets have the same number of elements.</p></td>
</tr>
</tbody>
</table>

![image3](../../assets/5fb81cf96bc14cd190fd9f931fd6ac3f.png)

## 三、Total vs. Partial Functions
1，Paritial Functions:不一定得到结果
Total function:输入一定返回结果

![image4](../../assets/909577d089cd4266804ff44285288b28.png)

![image5](../../assets/59bcaa383d0d48ddabae4ee7fb7cde31.png)
Eg.classifying functions
![image6](../../assets/fa0bf22eecc74529852be83f37461003.png)

![image7](../../assets/b93e7c41e0104f40b6f9a3b11cdf61ef.png)

## 四、Sets, bags, and sequences
| A set is a collection of objects |                                                      |
|----------------------------------|-------------------------------------------------------|
| A bag is like a set,             | but we also remember how many times an object occurs. |
| A sequence is like a set,        | but we also remember where an object occurs.          |
1，Bags
A bag (or multiset) is like a set except that members are allowed to occur many times.
The number of times an element occurs in a bag is called the multiplicity of that element.
For example: \[\[a,a,b,b,b,c\]\] is the bag where a occurs twice, b occurs thrice and c occurs once.
Notes: The notation \[\[···\]\] is not very standard.
The order of elements in a bag doesn’t matter.
![image8](../../assets/3e254a18ba594941a515d0376de2bcd1.png)

![image9](../../assets/8c147ec98ce84878b8dbec551175d853.png)

![image10](../../assets/3534a05daac2416e932a2598d511eeaa.png)
2、Sequence
![image11](../../assets/6e8a8a8511a4474e8b528751785cdaad.png)

![image12](../../assets/fe69bf1c80254e97960c3092f7d81b0c.png)

![image13](../../assets/ecee13516fc944d59fc34206d9bb4281.png)

![image14](../../assets/79c379b56b0d4a3dbf52343aba864a85.png)

![image15](../../assets/073008e978934eeead5e75d4b7fc5e63.png)

![image16](../../assets/ef84e590246f434595e3d12603c74e05.png)

