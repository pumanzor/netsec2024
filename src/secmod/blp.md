Bell-Lapadula y otros modelos de seguridad.

- Bell-LaPadula model
- Biba model
- Chinese Wall model
- (Clark-Wilson model)

Modelo Bell-Lapadula

- Most famous security model
- First developed around 1973
- ”Unified exposition and Multics interpretation”, 1976
- Focus on confidentiality, not integrity
- Based on state transitions
- Both mandatory and discretionary access control
   * Multilevel security
   * Access control matrix
 
Set of subjects

- Set of objects O
- Set of access operations A
  * execute, read, append, write
 
Set of security levels L with ordering ≤

Functions

- fS: S → L, maximum security level
- fC: S → L, current security level
- fO: O → L, security level of object

Multilevel security

- Categories
  *{Division A, Division B}
- Security level given by pair

(h1,c1) ≤ (h2 ,c2) if and only if h1 ≤ h2 and c1 ⊆ c2
 



