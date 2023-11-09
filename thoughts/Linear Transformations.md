# Linear Transformations
Transformations are basically functions, but for sets.

Types: (here mapping V → W)
- $image(T)$ = collection of all vectors in W that can be gotten by transformation (by T) from V
- Injective: the transformation is one-to-one → distinct vectors will have distinct images
- Surjective: $image(T) = W$ → image of T spans the all of W
- Linear (mostly applied to transformations): image of linear combination = linear combination of images → **preserves** linear transformations
	- $$ T(\alpha a+\beta B) = \alpha T(a) + \beta T(B)$$

Determining if it’s a linear transformation:
Check general definition by setting arbitrary $\alpha\  \text{and}\ \beta$ and then carry out standard operations.
$$ S{:}\mathbb{R}^2\to\mathbb{R}^2,S[a\quad b]=[\begin{array}{cc}a^2&b^2\end{array}].$$


Given that it’s a linear transformation find the function/transformation itself:
Apply the transformation to the given starting values and compare using properties

$$ \begin{array}{ll}\mathrm{Find~}\boldsymbol{T}(\mathbf{v})\mathrm{~for~a~linear~transformation}&\boldsymbol{T}\mathrm{~if~it~is~known~that~}\boldsymbol{T}(\mathbf{u}+\mathbf{v})=\mathbf{u}\mathrm{~and}\\\boldsymbol{T}(\mathbf{u})=\mathbf{u}-2\mathbf{v}.\end{array}$$

Pre-multiplication by a matrix (mult on the left) is linear:
- L maps all vectors in $R^n$ to some vectors in $R^m$ → is linear transformation
- Can be used to prove that a given transformation is linear

$$ \begin{aligned}&\text{Determine whether the given transformation is linear:}\\&\boldsymbol{S}{:}\mathbb{R}^3\to\mathbb{R}^2,\boldsymbol{S}\left[\begin{matrix}a&b&c\end{matrix}\right]=\left[\begin{matrix}a+2b-3c&0\end{matrix}\right]\end{aligned}$$

## Transformation acting on basis vectors
If a vector $v \in V$, it can be represented as a linear combination of the basis with coefficients $c_1,c_2,c_3...$ → called coordinates of v with respect to basis B.

Using the definition of a linear combination transformation, the result of a transformation are determined by how it transforms the basis of the domain.
$$Tv = T(c_1v_1+c_2v_{2+...)}= c_1Tv_1+c_1Tv_2+c_1Tv_3+...$$
- All you need to know to get the transformation of any vector v is each image of the basis and the coordinates $c_1,c_2,c_3...$

Generalization to something called the **coordinate representation** of a transformation:
Simply the act of mapping a given vector to the vector basis, which is linear, 1:1, and onto.
$$T(v)=(v)_{B,}\ \  B={v_1,...,v_n}$$