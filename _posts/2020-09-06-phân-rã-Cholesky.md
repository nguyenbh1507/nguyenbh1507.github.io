---
layout: post
title: Phân rã Cholesky
subtitle: Each post also has a subtitle
gh-repo: datacuriosity/datacuriosity.github.io
gh-badge: [star, fork, follow]
tags: [Cholesky decomposition]
category: [Dimensionlity-reduction, Decomposition]
comments: true
---
# Phân rã Cholesky
### 1. Nhắc lại: 

#### a.	Ma trận Hermitian:

Nếu chuyển vị liên hợp của một ma trận phức bằng với chính nó <span>$$\mathbf{A\cdot H} = \mathbf{A}$$</span>, thì ta nói đó là ma trận Hermitian.

#### b.	Ma trận hoán vị:
Ma trận hoán vị là một ma trận thu được từ việc hoán vị dòng hay cột từ ma trận I. Một ma trận hoán vị là không suy biến có định thức bằng 1 hoặc -1. Nếu A là một ma trận hoán vị thì 
<div><span>$$\mathbf{A}\cdot \mathbf{A}^T = \mathbf{I}$$</span></div>

#### c.	Ma trận tam giác trên(dưới) đơn vị

Nếu tất cả các phần tử trên đường chéo chính của ma trận tam giác (trên hoặc dưới) đều là 1, ma trận được gọi là ma trận tam giác (trên hoặc dưới) đơn vị

#### d.	Căn bậc 2 của ma trận

Một ma trận <span>$$\mathbf{B}$$</span> được gọi là căn bậc hai của ma trận <span>$$\mathbf{A}$$</span> nếu tích của hai ma trận <span>$$\mathbf{B \cdot B = A}$$</span>

Một vài tác giả sử dụng tên “căn bậc 2” hoặc ký hiệu <span>$$\mathbf{A}^{1/2}$$</span> chỉ cho trường hợp cụ thể khi <span>$$\mathbf{A}$$</span> là nửa xác định dương, để biểu thị ma trận <span>$$\mathbf{B}$$</span> duy nhất nửa xác định dương sao cho <span>$$\mathbf{B \cdot B} = \mathbf{B \cdot B^T} = \mathbf{A} $$</span>.

Một ma trận thực vuông nửa xác định dương <span>$$\Leftrightarrow \mathbf{A}=\mathbf{B}\cdot\mathbf{B}^T$$</span>. Có thể có nhiều ma trận như <span>$$\mathbf{B}$$</span>.

Một ma trận nửa xác định dương <span>$$\mathbf{A}$$</span> có thể có nhiều ma trận <span>$$\mathbf{B}$$</span> sao cho<span>$$\mathbf{A=B\cdot B}$$</span>. Tuy nhiên <span>$$\mathbf{A}$$</span> chỉ có duy nhất một <span>$$\mathbf{B}$$</span> là nửa xác định dương.

Ví dụ 1: 

Ma trận <span>$$\mathbf{I}_2$$</span> có vô số căn bậc 2:
<div>
<span>$$
\begin{bmatrix}
 & a & b\\ 
 & c &-a
\end{bmatrix}
$$</span>
</div>
Với <span>$$a, b, c$$</span> (thực hoặc phức) sao cho <span>$$a^2 + bc = 1$$</span>

Ví dụ 2:

Ta có <span>$$\mathbf{A} = \mathbf{B}\cdot\mathbf{B}$$</span>

Định lý: <span>$$\mathbf{A}$$</span> là nửa xác định dương (thực hoặc phức) thì có duy nhất 1 ma trận <span>$$\mathbf{B}$$</span> là nửa xác định dương sao cho <span>$$\mathbf{B\cdot B}=\mathbf{A}$$</span>.

Ma trận duy nhất <span>$$\mathbf{B}$$</span> được gọi là: principal, non-negative, hoặc positive square root. (dịch là căn bậc 2 chính).

Căn bậc hai chính của ma trận nửa xác định dương thực là ma trận thực, căn bậc hai chính của ma trận xác định dương là ma trận xác định dương. 

Tổng quát hơn hạng của căn bậc hai chính của <span>$$\mathbf{A}$$</span> bằng với hạng của <span>$$\mathbf{A}$$</span>.

### 2.	Phát biểu:
Phân rã Cholesky là phân rã một ma trận xác định dương Hermitian(ma trận phức xác định dương) thành tích của ma trận tam giác dưới và phép chuyển vị liên hợp của nó.
Phân rã Cholesky một ma trận Hermitian xác định dương có dạng sau:

-	Với <span>$$\mathbf{L}$$</span> là ma trận tam giác dưới với các phần tử trên đường chéo là thực dương. <span>$$\mathbf{L^*}$$</span> là chuyển vị liên hợp. Mọi ma trận xác định dương Hermitian (mọi ma trận thực đối xứng xác định dương) có phân rã Cholesky là duy nhất. 
-	Điều ngược lại: Nếu <span>$$\mathbf{A}$$</span> được biểu diễn dưới dạng <span>$$\mathbf{L\cdot L^*}$$</span> đối với một vài: <span>$$\mathbf{L}$$</span> khả nghịch, hoặc <span>$$\mathbf{L}$$</span> tam giác dưới hoặc một số thứ khác nữa thì <span>$$\mathbf{A}$$</span> là ma trận Hermitian xác định dương.
-	Khi <span>$$\mathbf{A}$$</span> là thực đối xứng xác định dương thì ta viết: <span>$$\mathbf{A = L\cdot L}^T$$</span>

### 3.	Ma trận đối xứng nửa xác định dương:

-	Nếu <span>$$\mathbf{A}$$</span> là Hermitian nửa xác định dương thì có phân rã Cholesky, nhưng phân rã Cholesky không là duy nhất và đường chéo của <span>$$\mathbf{L}$$</span> có thể bằng 0.

Ví dụ:




-	Tuy nhiên nếu hạng của <span>$$\mathbf{A}$$</span> là <span>$$r$$</span> thì tồn tại duy nhất một dạng ma trận tam giác dưới <span>$$\mathbf{L}$$</span>: Có đúng <span>$$r$$</span> phần tử đường chéo dương và <span>$$n-r$$</span> hàng chứa tất cả các số 0.

-	Nếu <span>$$\mathbf{A}$$</span> là một ma trận nửa xác định dương <span>$$n\times n$$</span> có hạng <span>$$r$$</span>, thì có ít nhất một ma trận hoán vị <span>$$\mathbf{P}$$</span> sao cho <span>$$\mathbf{P\cdot A\cdot P}^T$$</span> có phân rã Cholesky duy nhất:

<div><span>$$\mathbf{P\cdot A\cdot P}^T = \mathbf{L\cdot L^*}$$</span></div>
 với:


Trong đó <span>$$\mathbf{L}_1$$</span> là ma trận tam giác dưới <span>$$r\times r$$</span> với các phần tử trên đường chéo dương.
### 4.	Phân rã <span>$$\mathbf{L\cdot D\cdot L}$$</span>
Một biến thể có liên quan chặt chẽ đến phân rã Cholesky là phân rã <span>$$\mathbf{L\cdot D\cdot L}_1$$</span>:

Trong đó <span>$$\mathbf{L}$$</span> là ma trận tam giác dưới đơn vị, <span>$$\mathbf{D}$$</span> là ma trận đường chéo.

Đối với ma trận thực, phân tích thừa số có dạng <span>$$\mathbf{A=L\cdot D\cdot L}^T$$</span> và thường được gọi là phân rã <span>$$\mathbf{L\cdot D\cdot L}^T$$</span> . Nó liên quan chặt chẽ đến chéo hóa của ma trận thực đối xứng <span>$$\mathbf{A=Q\cdot Q}^T$$</span> .
Phân rã <span>$$\mathbf{L\cdot D\cdot L}$$</span> liên quan đến phân rã Cholesky của dạng <span>$$\mathbf{L\cdot L^*}$$</span> như sau:

Ngược lại: Phân rã Cholesky <span>$$\mathbf{A=C\cdot C}^* $$</span> của ma trận xác định dương. nếu <span>$$\mathbf{S}$$</span> là ma trận đường chéo chứa đường chéo chính của <span>$$\mathbf{C}$$</span> thì <span>$$\mathbf{A}$$</span> được phân rã dạng <span>$$\mathbf{L\cdot D\cdot L}^* $$</span> trong đó: <span>$$\mathbf {L\cdot D\cdot L}^* $$</span>
<span>$$\mathbf{L=C\cdot S^{-1}}$$</span> (Thay đổi tỷ lệ mỗi cột để tạo thành phần tử đường chéo 1).
	<span>$$\mathbf{D= S}^2$$</span>
Nếu <span>$$\mathbf{A}$$</span> là xác định dương thì các phần tử đường chéo của <span>$$\mathbf{D}$$</span> đều dương. Nếu <span>$$\mathbf{A}$$</span> nửa xác định dương thì phân rã <span>$$\mathbf{L\cdot D\cdot L}^* $$</span> tồn tại trong đó số phần tử khác 0 trên đường chéo <span>$$\mathbf{D}$$</span> chính xác là hạng của <span>$$\mathbf{A}$$</span>.

### 5.	Ví dụ:
Ví dụ 1: Phân rã Cholesky của ma trận thực đối xứng:

Ví dụ 2: Phân rã <span>$$\mathbf{L\cdot D\cdot L}^T$$</span> 


### 6.	Tham Khảo
- Higham, Nicholas J. (April 1986), "Newton's Method for the Matrix Square Root" (PDF), Mathematics of Computation, 46(174): 537–549, doi:10.2307/2007992, JSTOR 2007992
- Horn & Johnson (2013), p. 439, Theorem 7.2.6 with k = 2
- Golub & Van Loan (1996, p. 143), Horn & Johnson (1985, p. 407), Trefethen & Bau (1997, p. 174).
- Horn & Johnson (1985, p. 407).
- "Matrices - Diagonalizing a Complex Symmetric Matrix". MathOverflow. Retrieved 2020-01-25.
- Schabauer, Hannes; Pacher, Christoph; Sunderland, Andrew G.; Gansterer, Wilfried N. (2010-05-01). "Toward a parallel solver for generalized complex symmetric eigenvalue problems". Procedia Computer Science. ICCS 2010. 1 (1): 437–445. doi:10.1016/j.procs.2010.04.047. ISSN 1877-0509
- Golub & Van Loan (1996, p. 147)
- Gentle, James E. (1998). Numerical Linear Algebra for Applications in Statistics. Springer. p. 94. ISBN 978-1-4612-0623-1.
- Higham, Nicholas J. (1990). "Analysis of the Cholesky Decomposition of a Semi-definite Matrix". In Cox, M. G.; Hammarling, S. J. (eds.). Reliable Numerical Computation. Oxford, UK: Oxford University Press. pp. 161–185. ISBN 978-0-19-853564-5.
- Krishnamoorthy, Aravindh; Menon, Deepak (2011). "Matrix Inversion Using Cholesky Decomposition". 1111: 4144. arXiv:1111.4144. Bibcode:2011arXiv1111.4144K
- So, Anthony Man-Cho (2007). A Semidefinite Programming Approach to the Graph Realization Problem: Theory, Applications and Extensions (PDF) (PhD). Theorem 2.2.6