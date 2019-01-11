---
layout: page
title: Characteristic Polynomial Database
permalink: /cpdb/
use_math: true
---

{% include nav-breadcrumbs.html %}

The __characteristic polynomial database__ contains characteristic polynomials,
minimal polynomials and properties for a variety of families of Bohemian matrices. Currently the database contains __1,762,728,065__ characteristic polynomials from __2,366,960,967,336__ matrices.

## Bohemian Families

### <a href="{{ '/cpdb/unstructured' | prepend: site.baseurl | prepend: site.url }}">Unstructured</a>
Matrices with no structure. For example, $5 \times 5$ matrices with entries from the set $\\{-1, 0, +1\\}$.

### <a href="{{ '/cpdb/upperhessenberg' | prepend: site.baseurl | prepend: site.url }}">Upper Hessenberg</a>
Upper Hessenberg matrices with subdiagonal entries fixed at 1.

## Data Files

### Polynomial Files
All characteristic polynomial and minimal polynomial files are CSV files with
no header. They have been provided in uncompressed format, as well as
compressed as zip files and tar.gz files. The characteristic polynomial files
follow the naming convention `CharPolys_nxn.csv` where `n` is the dimension of
the matrices in the family they are computed from. Similarly, the minimal
polynomial files follow the naming convention `MinPolys_nxn.csv` where `n` is
the dimension of the matrices in the family they are computed from. Each row in the CSV files is of the form:

`count, c_{n}, c_{n-1}, ..., c_0`

where `count` is the number of times the characteristic polynomial appears in
the family. `c_{n}` to `c_0` are the coefficients of the characteristic
polynomial beginning with the degree n coefficient down to the constant
coefficient.

A Maple function `read_poly_data` is available [here](https://github.com/BohemianMatrices/characteristic-polynomial-database/blob/master/src/Maple/read_poly_data.mpl) for reading the polynomials (and optionally their counts) into Maple. See the header in the file for details on its usage. Polynomials can be read into Maple as follows:

```
# Read polynomials into an array, counts are discarded.
char_polys := read_poly_data("CharPolys_4x4.csv", x):

# Read polynomials and their counts into arrays.
char_polys, char_poly_counts := read_poly_data("CharPolys_4x4.csv", x, keepCount=true):
```

## Property Definitions

### Number of Matrices
The number of matrices in the family.

### Number of Characteristic Polynomials
The number of distinct characteristic polynomials in the family.

### Number of Minimal Polynomials
The number of distinct minimal polynomials of the matrices in the family.

### Number of Non-Derogatory Matrices
The number of matrices in the family where their minimal polynomial and characteristic polynomial coincide (up to a factor of $\pm1$), see  
 [https://www.encyclopediaofmath.org/index.php/Non-derogatory_matrix](https://www.encyclopediaofmath.org/index.php/Non-derogatory_matrix).

### Maximum Characteristic Height
The characteristic height of a matrix is the maximum absolute coefficient of
its characteristic polynomial when written in the monomial basis. The maximum characteristic height over a family of Bohemian matrices is the maximum of the
characteristic heights of the matrices in the family.

### Number of Distinct Eigenvalues
The cardinality of the set of all eigenvalues from all matrices in a Bohemian
family.

### Number of Distinct Real Eigenvalues
The cardinality of the subset of all eigenvalues from all matrices in a
Bohemian family that have zero complex part.

### Number of Distinct Purely Complex Eigenvalues
The cardinality of the subset of all eigenvalues from all matrices in a
Bohemian family that have non-zero complex part.

### Number of Distinct Jordan Canonical Forms
The cardinality of the set of Jordan canonical forms from all matrices in a
Bohemian family up to permutations of the Jordan blocks. More precisely, this
is the cardinality of the set of all Frobenius forms from all matrices in a
Bohemian family. Or equivalently, the cardinality of the subset of a family of
Bohemian matrices such that no two matrices in the subset are similar.

### Number of Singular Matrices
Number of matrices that are singular (i.e. $\det(A) = 0$).

### Number of Non-Singular Matrices
Number of matrices that are non-singular (i.e. $\det(A) \ne 0$).

### Number of Rank n Matrices
Number of matrices in the Bohemian family with a rank of n.

### Number of Distinct Determinants
Number of unique determinants in the family of Bohemian matrices.

### Maximum Determinant
Maximum absolute determinant over all matrices in the family.

### Number of Unimodular Matrices
Number of unimodular matrices, i.e. matrices with determinant of $+1$ or $-1$.

### Number of Normal Matrices
Number of matrices in the family such that $AA^T - A^TA = 0$.

### Number of Rhapsodic Matrices
Number of matrices in the Bohemian family such that its inverse also belongs to the same Bohemian family.

### Number of Nilpotent Matrices
Number of matrices such that there exists a positive integer $k$ where $A^k = 0$.

### Number of Totally Unimodular Matrices
Number of matrices in the Bohemian family such that every square non-singular submatrix is unimodular.

### Number of Type I Stable Matrices
Number of matrices in the Bohemian family where the real part of all eigenvalues is strictly negative ($\textrm{Re}(\lambda) < 0$). These are the matrices $A$ where the differential equation $\dot{y} = Ay$ will ultimately decay as $t \to \infty$.

### Number of Type II Stable Matrices
Number of matrices in the Bohemian family where all eigenvalues are strictly within the unit circle ($|\lambda| < 1$). These are the matrices where the recursion $y_{n+1} = A y_n$ will ultimately decay to 0 as $n \to \infty$.

## Conjectures

While computing properties for the families of matrices available in the database, we came across many cases where a property appears to match a sequence on the [OEIS](http://oeis.org/) but we were unable to find a proof. Below we list sequences that appear to match, for which we have no proof of their validity. If you prove any of the conjectures below, or know of a reference with their proof, please send an email to <a href="http://steventhornton.ca" target="_blank">Steven Thornton</a> at <a href="mailto:sthornt7@uwo.ca">sthornt7@uwo.ca</a>, or <a href="http://www.apmaths.uwo.ca/~rcorless/" target="_blank">Rob Corless</a> at <a href="mailto:rcorless@uwo.ca">rcorless@uwo.ca</a> with details. Full credit will be given.

#### Conjecture 1
- __Conjecture:__ The number of nilpotent $n \times n$ matrices with entries from the set $\\{0, +1\\}$ is given by the sequence [A003024](http://oeis.org/A003024).
- __Status:__ True
- __Reference:__ Cvetković, D., Doob, M., & Sachs, H. (1980). Spectra of Graphs-Theory and Application. Third ed., Barth, Heidelber, 1995.
- __Proof:__ [p. 81] show that a digraph G contains no cycle if and only if all eigenvalues of the adjacency matrix are 0, which is the explicit bijection between nilpotent $n×n$ matrices and DAGs.
- __Proof Provided By:__ Jianxiang Chen

#### Conjecture 2
- __Conjecture:__ The maximal characteristic height of $n \times n$ matrices with entries from the set $\\{0, +1\\}$ is given by the sequence [A082914](http://oeis.org/A082914).
- __Status:__ False
- __Proof:__  According to the conjecture, the largest characteristic height of a $20 \times 20$ $\\{0,1\\}$ matrix should be 9754214400. But observe that the $j$-th coefficient of the characteristic polynomial is an alternate sum of all the determinants of the $(n − j) \times (n − j)$ diagonal minors, and the determinant of a $\\{0,1\\}$ matrix is bounded by A003432, the coefficient is bounded by $C(n,j)$A003432$(n-j)$. The values of $C(n,j)$A003432$(n-j)$ for a $20\times20$ matrix are: 390625000, 648273920, 1270087680, 1587609600, 2032140288, 988961400, 734657040, 459160650, 244885680, 59121920, 24186240, 7054320, 2480640, 348840, 77520, 14535, 2280, 190, 20, which are all smaller than 9754214400.
Therefore, the conjecture is false.
- __Proof Provided By:__ Jianxiang Chen

#### Conjecture 3
- __Conjecture:__ The number of nilpotent $n \times n$ matrices with entries from the set $\\{0, +1\\}$ and diagonal entries fixed at 0 is given by the sequence [A003024](http://oeis.org/A003024).
- __Status:__ True
- __Reference:__ Cvetković, D., Doob, M., & Sachs, H. (1980). Spectra of Graphs-Theory and Application. Third ed., Barth, Heidelber, 1995.
- __Proof:__ [p. 81] show that a digraph G contains no cycle if and only if all eigenvalues of the adjacency matrix are 0, which is the explicit bijection between nilpotent $n×n$ matrices and DAGs.
- __Proof Provided By:__ Jianxiang Chen

#### Conjecture 4
- __Conjecture:__ The maximal absolute determinant of $n \times n$ matrices with entries from the set $\\{-1, 0, +1\\}$ is given by the sequence
   [A003433](http://oeis.org/A003433).
- __Status:__ True
- __Proof:__ __Lemma.__ For square matrices $A$, $B$, $C$ with $2A_{m,n}=B_{m,n}+C_{m,n}$ and all other elements equal, their determinants satisfy $2\|A\|=\|B\|+\|C\|$. __Proof.__ By Laplace expansion on the $m$th row or $n$th column. So for every $\\{-1,0,1\\}$ matrix with some element $A_{m,n}=0$, we can construct two matrices $B$ and $C$ with $B_{m,n}=1$ and $C_{m,n}=-1$ with all other elements equal. Then at least one of $\|B\|$ and $\|C\|$ is not smaller than $\|A\|$. By repeating the procedure we can eliminate all zeros of $A$, arriving at a $\\{-1,1\\}$ matrix with maximum determinant, which is the definition of [A003433](http://oeis.org/A003433).
- __Proof Provided By:__ Jianxiang Chen

#### Conjecture 5
- __Conjecture:__ The number of nilpotent $n \times n$ matrices with entries from the set $\\{-1, 0, +1\\}$ and diagonal entries fixed at 0 is given by the sequence [A085506](http://oeis.org/A085506).
- __Status:__ True
- __Reference:__ McKay, B. D., Oggier, F. E., Royle, G. F., Sloane, N. J. A., Wanless, I. M., & Wilf, H. S. (2004). Acyclic digraphs and eigenvalues of (0, 1)-matrices. _Journal of Integer Sequences_, 7(2), 3.
- __Proof:__ Follows from proof on [p. 2].
- __Proof Provided By:__ Jianxiang Chen

#### Conjecture 6
- __Conjecture:__ The number of nilpotent $n \times n$ matrices with entries from the set $\\{0, +1, +2\\}$ is given by the sequence [A188457](http://oeis.org/A188457).
- __Status:__ Open

#### Conjecture 7
- __Conjecture:__ The maximum absolute determinant of an $n \times n$ upper-Hessenberg matrix with entries from the set $\\{0, +1\\}$ and subdiagonal entries fixed at 1 is given by the Fibonacci sequence [A000045](http://oeis.org/A000045).
- __Status:__ True
- __Reference:__ Ching, L. (1993). The maximum determinant of an $n \times n$ lower Hessenberg (0, 1) matrix. _Linear algebra and its applications, 183_, 147-153.
- __Proof Provided By:__ [Nick Higham](https://nickhigham.wordpress.com/)

#### Conjecture 8
- __Conjecture:__ The maximum absolute determinant of an $n \times n$ upper-Hessenberg matrix with entries from the set $\\{0, +1, +2\\}$ and subdiagonal entries fixed at 1 is given by sequence [A052542](http://oeis.org/A052542).
- __Status:__ Open

#### Conjecture 9
- __Conjecture:__ The number of distinct determinants of an $n \times n$ upper-Hessenberg matrix with entries from the set $\\{0, 1\\}$, subdiagonal entries fixed at 1, and diagonal entries fixed at 0 is given by sequence [A212264](http://oeis.org/A212264).
- __Status:__ Open

#### Conjecture 10
- __Conjecture:__ All upper-Hessenberg matrices with subdiagonal entries fixed at 1 are non-derogatory.
- __Status:__ True
- __Reference:__ Chan, E., Corless, R. M., Gonzalez-Vega, L., Sendra, J. R., Sendra, J., & Thornton, S. (2018). Bohemian Upper Hessenberg Matrices. _arXiv preprint [arXiv:1809.10653](https://arxiv.org/abs/1809.10653)_,
- __Proof:__ Proposition 5.3.
- __Proof Provided By:__ Steven E. Thornton

#### Conjecture 11
- __Conjecture:__ The maximum characteristic height of an $n \times n$ upper-Hessenberg matrix with entries from the set $\\{0, +1, +2\\}$, subdiagonal entries fixed at 1, and diagonal entries fixed at 0 is given by sequence [A058764](http://oeis.org/A058764).
- __Status:__ Open

#### Conjecture 12
- __Conjecture:__ The number of distinct determinants of an $n \times n$ upper-Hessenberg matrix with entries from the set $\\{-1, 0\\}$, subdiagonal entries fixed at 1, and diagonal entries fixed at 0 is given by sequence [A001611](http://oeis.org/A001611).
- __Status:__ Open

#### Conjecture 13
- __Conjecture:__ The maximum absolute determinant of an $n \times n$ upper-Hessenberg matrix with entries from the set $\\{-1, 0\\}$, subdiagonal entries fixed at 1, and diagonal entries fixed at 0 is given by the Fibonacci sequence [A000045](http://oeis.org/A000045).
- __Status:__ Open

#### Conjecture 14
- __Conjecture:__ The number of distinct determinants of an $n \times n$ upper-Hessenberg matrix with entries from the set $\\{-1, 0, +1\\}$, subdiagonal entries fixed at 1, and diagonal entries fixed at 0 is given by sequence [A001588](http://oeis.org/A001588).
- __Status:__ Open

#### Conjecture 15
- __Conjecture:__ The maximum absolute determinant of an $n \times n$ upper-Hessenberg matrix with entries from the set $\\{-1, 0, +1\\}$, subdiagonal entries fixed at 1, and diagonal entries fixed at 0 is given by the Fibonacci sequence [A000045](http://oeis.org/A000045).
- __Status:__ Open

#### Conjecture 16
- __Conjecture:__ The number of distinct determinants of an $n \times n$ upper-Hessenberg matrix with entries from the set $\\{-1, +1\\}$, subdiagonal entries fixed at 1, and diagonal entries fixed at 0 is given by sequence [A001611](http://oeis.org/A001611).
- __Status:__ Open

#### Conjecture 17
- __Conjecture:__ The maximum absolute determinant of an $n \times n$ upper-Hessenberg matrix with entries from the set $\\{-1, +1\\}$, subdiagonal entries fixed at 1, and diagonal entries fixed at 0 is given by the Fibonacci sequence [A000045](http://oeis.org/A000045).
- __Status:__ Open

#### Conjecture 18
- __Conjecture:__ The number of distinct determinants of an $n \times n$ upper-Hessenberg matrix with entries from the set $\\{-1, 0\\}$ and subdiagonal entries fixed at 1 is given by sequence [A000051](http://oeis.org/A000051).
- __Status:__ Open

#### Conjecture 19
- __Conjecture:__ The number of distinct determinants of an $n \times n$ upper-Hessenberg matrix with entries from the set $\\{-1, 0, +1\\}$ and subdiagonal entries fixed at 1 is given by sequence [A000051](http://oeis.org/A000051).
- __Status:__ Open

#### Conjecture 20
- __Conjecture:__ The number of distinct determinants of an $n \times n$ upper-Hessenberg matrix with entries from the set $\\{-1, +1\\}$ and subdiagonal entries fixed at 1 is given by sequence [A000051](http://oeis.org/A000051).
- __Status:__ Open

## Referencing the CPDB
If the database helped your work and you wish to reference it, the following citation format should be used:

S. E. Thornton, _The Characteristic Polynomial Database_, published electronically at http://bohemianmatrices.com/cpdb, [date]

### Bibtex
```
@online{CPDB,
  author = {Steven E. Thornton},
  title = {The Characteristic Polynomial Database},
  url = {http://bohemianmatrices.com/cpdb},
  urldate = {[date]}
}
```

or

```
@misc{CPDB,
  author = {Steven E. Thornton},
  title = {The Characteristic Polynomial Database},
  howpublished = {Available at \url{http://bohemianmatrices.com/cpdb} ([date])}
}
```
