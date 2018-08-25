---
layout: page
title: Characteristic Polynomial Database
permalink: /cpdb/
use_math: true
---

{% include nav-breadcrumbs.html %}

The __characteristic polynomial database__ contains characteristic polynomials,
minimal polynomials and properties for a variety of families of Bohemian matrices. Currently the database contains __1,762,728,075__ characteristic polynomials from __2,366,960,967,336__ matrices.

## Bohemian Families

### <a href="{{ '/cpdb/unstructured' | prepend: site.baseurl | prepend: site.url }}">Unstructured</a>
Matrices with no structure. For example, $5 \times 5$ matrices with entries from the set $\\{-1, 0, +1\\}$.

### <a href="{{ '/cpdb/upperhessenberg' | prepend: site.baseurl | prepend: site.url }}">Upper Hessenberg</a>
Upper Hessenberg matrices with subdiagonal entries fixed at 1.

## Data Files

### Characteristic Polynomial Files
All characteristic polynomial files are CSV files with no header. They have
been provided in uncompressed format, as well as compressed as zip files and
tar.gz files. The characteristic polynomial files follow the naming convention
`CharPolys_nxn.csv` where `n` is the dimension of the matrices in the family
they are computed from. Each row in the CSV files is of the form:

`count, c_{n-1}, c_{n-2}, ..., c_0`

where `count` is the number of times the characteristic polynomial appears in the family. `c_{n-1}` to `c_0` are the coefficients of the characteristic polynomial beginning with the degree n-1 coefficient down to the constant coefficient. The leading coefficient (`c_n`) is omitted from the files as this will always be equal to 1.

A Maple function `read_poly_data` is available [here](https://github.com/BohemianMatrices/characteristic-polynomial-database/blob/master/src/Maple/read_poly_data.mpl) for reading the polynomials (and optionally their counts) into Maple. See the header in the file for details on its usage. Polynomials can be read into Maple as follows:

```
# Read polynomials into an array, counts are discarded.
char_polys := read_poly_data("CharPolys_4x4.csv", x, isMonic=true):

# Read polynomials and their counts into arrays.
char_polys, char_poly_counts := read_poly_data("CharPolys_4x4.csv", x, isMonic=true, keepCount=true):
```

### Minimal Polynomial Files
All minimal polynomial files are CSV files with no header. They have been
provided in uncompressed format, as well as compressed as zip files and
tar.gz files. The minimal polynomial files follow the naming convention
`MinPolys_nxn.csv` where `n` is the dimension of the matrices in the family
they are computed from. Each row in the CSV files is of the form:

`count, c_{n}, c_{n-1}, ..., c_0`

where `count` is the number of times the minimal polynomial appears in the family. `c_{n}` to `c_0` are the coefficients of the minimal polynomial beginning with the degree n coefficient down to the constant coefficient.

A Maple function `read_poly_data` is available [here](https://github.com/BohemianMatrices/characteristic-polynomial-database/blob/master/src/Maple/read_poly_data.mpl) for reading the polynomials (and optionally their counts) into Maple. See the header in the file for details on its usage. Polynomials can be read into Maple as follows:

```
# Read polynomials into an array, counts are discarded.
min_polys := read_poly_data("MinPolys_4x4.csv", x, isMonic=false):

# Read polynomials and their counts into arrays.
min_polys, min_poly_counts := read_poly_data("MinPolys_4x4.csv", x, isMonic=false, keepCount=true):
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
Number of matrices in the Bohemian family where the real part of all eigenvalues is strictly negative ($\textrm{Re}(\lambda) < 0$). These are the matrices where the differential equation $\dot{y} = Ay$ converges.

### Number of Type II Stable Matrices
Number of matrices in the Bohemian family where all eigenvalues are strictly within the unit circle ($|\lambda| < 1$). These are the matrices where the recursion $y_{n+1} = A y_n$ converges.

## Conjectures

While computing properties for the families of matrices available in the database, we came across many cases where a property appears to match a sequence on the [OEIS](http://oeis.org/) but we were unable to find a proof. Below we list sequences that appear to match, for which we have no proof of their validity. If you prove any of the conjectures below, or know of a reference with their proof, please send an email to <a href="http://steventhornton.ca" target="_blank">Steven Thornton</a> at <a href="mailto:sthornt7@uwo.ca">sthornt7@uwo.ca</a>, or <a href="http://www.apmaths.uwo.ca/~rcorless/" target="_blank">Rob Corless</a> at <a href="mailto:rcorless@uwo.ca">rcorless@uwo.ca</a> with details. Full credit will be given.

1. The number of nilpotent $n \times n$ matrices with entries from the
   set $\\{0, +1\\}$ is given by the sequence
   [A003024](http://oeis.org/A003024).
2. The maximal characteristic height of $n \times n$ matrices with entries from
   the set $\\{0, +1\\}$ is given by the sequence [A082914](http://oeis.org/A082914).
3. The number of nilpotent $n \times n$ matrices with entries from the
   set $\\{0, +1\\}$ and diagonal entries fixed at 0 is given by the
   sequence [A003024](http://oeis.org/A003024).
4. The maximal absolute determinant of $n \times n$ matrices with entries from
   the set $\\{-1, 0, +1\\}$ is given by the sequence
   [A003433](http://oeis.org/A003433).
5. The number of nilpotent $n \times n$ matrices with entries from the
   set $\\{-1, 0, +1\\}$ and diagonal entries fixed at 0 is given by the
   sequence [A085506](http://oeis.org/A085506).
6. The number of nilpotent $n \times n$ matrices with entries from the
   set $\\{0, +1, +2\\}$ is given by the sequence
   [A188457](http://oeis.org/A188457).
7. The maximum absolute determinant of an $n \times n$ upper-Hessenberg matrix
   with entries from the set $\\{0, +1\\}$ and subdiagonal entries fixed at 1 is
   given by the Fibonacci sequence [A000045](http://oeis.org/A000045).
8. The maximum absolute determinant of an $n \times n$ upper-Hessenberg matrix
   with entries from the set $\\{0, +1, +2\\}$ and subdiagonal entries fixed at
   1 is given by sequence [A052542](http://oeis.org/A052542).
9. The number of distinct determinants of an $n \times n$ upper-Hessenberg
   matrix with entries from the set $\\{0, 1\\}$, subdiagonal entries fixed at
   1, and diagonal entries fixed at 0 is given by sequence
   [A212264](http://oeis.org/A212264).
10. All upper-Hessenberg matrices with subdiagonal entries fixed at 1 are
    non-derogatory.
11. The maximum characteristic height of an $n \times n$ upper-Hessenberg matrix
    with entries from the set $\\{0, +1, +2\\}$, subdiagonal entries fixed at 1,
    and diagonal entries fixed at 0 is given by sequence
    [A058764](http://oeis.org/A058764).
12. The number of distinct determinants an $n \times n$ upper-Hessenberg matrix
    with entries from the set $\\{-1, 0\\}$, subdiagonal entries fixed at 1,
    and diagonal entries fixed at 0 is given by sequence [A001611](http://oeis.org/A001611).
13. The maximum absolute determinant of an $n \times n$ upper-Hessenberg matrix
    with entries from the set $\\{-1, 0\\}$, subdiagonal entries fixed at 1,
    and diagonal entries fixed at 0 is given by the Fibonacci sequence
    [A000045](http://oeis.org/A000045).
14. The number of distinct determinants an $n \times n$ upper-Hessenberg matrix
    with entries from the set $\\{-1, 0, +1\\}$, subdiagonal entries fixed at 1,
    and diagonal entries fixed at 0 is given by sequence [A001588](http://oeis.org/A001588).
15. The maximum absolute determinant of an $n \times n$ upper-Hessenberg matrix
    with entries from the set $\\{-1, 0, +1\\}$, subdiagonal entries fixed at 1,
    and diagonal entries fixed at 0 is given by the Fibonacci sequence
    [A000045](http://oeis.org/A000045).
16. The number of distinct determinants an $n \times n$ upper-Hessenberg matrix
    with entries from the set $\\{-1, +1\\}$, subdiagonal entries fixed at 1,
    and diagonal entries fixed at 0 is given by sequence [A001611](http://oeis.org/A001611).
17. The maximum absolute determinant of an $n \times n$ upper-Hessenberg matrix
    with entries from the set $\\{-1, +1\\}$, subdiagonal entries fixed at 1,
    and diagonal entries fixed at 0 is given by the Fibonacci sequence
    [A000045](http://oeis.org/A000045).
18. The number of distinct determinants an $n \times n$ upper-Hessenberg matrix
    with entries from the set $\\{-1, 0\\}$ and subdiagonal entries fixed at 1
    is given by sequence [A000051](http://oeis.org/A000051).
19. The number of distinct determinants an $n \times n$ upper-Hessenberg matrix
    with entries from the set $\\{-1, 0, +1\\}$ and subdiagonal entries fixed
    at 1 is given by sequence [A000051](http://oeis.org/A000051).
20. The number of distinct determinants an $n \times n$ upper-Hessenberg matrix
    with entries from the set $\\{-1, +1\\}$ and subdiagonal entries fixed at 1
    is given by sequence [A000051](http://oeis.org/A000051).
