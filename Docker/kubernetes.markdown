# π μΏ λ²λ€ν°μ€?

μΏ λ²λ€ν°μ€(Kubernetes)λ μ»¨νμ΄λν λ μ νλ¦¬μΌμ΄μμ λκ·λͺ¨ λ°°ν¬, 
μ€μΌμΌλ§ λ° κ΄λ¦¬λ₯Ό κ°νΈνκ² λ§λ€μ΄μ£Όλ μ€ν μμ€ κΈ°λ° `μ»¨νμ΄λ μ€μΌμ€νΈλ μ΄μ(Container Orchestration) λκ΅¬`λ€.


- μΏ λ²λ€ν°μ€λ μ»¨νμ΄λνλ μν¬λ‘λμ μλΉμ€λ₯Ό κ΄λ¦¬νκΈ° μν μ΄μμ±μ΄ μκ³ , νμ₯κ°λ₯ν μ€νμμ€ νλ«νΌμ΄λ€.
- μΏ λ²λ€ν°μ€λ μ μΈμ  κ΅¬μ±κ³Ό μλνλ₯Ό λͺ¨λ μ©μ΄νκ² ν΄μ€λ€. 
- μΏ λ²λ€ν°μ€λ ν¬κ³ , λΉ λ₯΄κ² μ±μ₯νλ μνκ³λ₯Ό κ°μ§κ³  μλ€. 
- μΏ λ²λ€ν°μ€ μλΉμ€, κΈ°μ  μ§μ λ° λκ΅¬λ μ΄λμλ μ½κ² μ΄μ©ν  μ μλ€.


## π¦ μ€μΌμ€νΈλ μ΄μμ΄λ?

> "μ»¨νμ΄λν λ μ νλ¦¬μΌμ΄μμ λν μλνλ μ€μ , κ΄λ¦¬ λ° μ μ΄ μ²΄κ³"

λ§μ΄ν¬λ‘μλΉμ€ μν€νμ²(MSA; Microservice Architecture)μμλ νλ‘μ νΈμ ν¬ν¨λ μΈλΆ κΈ°λ₯λ€μ΄ μμ μλΉμ€ λ¨μλ‘ λΆλ¦¬λμ΄ κ΅¬μΆλλ©°
μ΄ κ°κ°μ μλΉμ€λ₯Ό κ΅¬νν  λ μ»¨νμ΄λ κΈ°μ μ΄ μ΄μ©λλ€. 
λκ·λͺ¨μ μμ© νλ‘μ νΈ νκ²½μμ μλ§μ μ»¨νμ΄λλ₯Ό μ΄λ° μμΌλ‘ μ μ΄νλ κ²μ λΆκ°λ₯νλ©° 
λμμ μλ°±, μμ² κ°μ μ»¨νμ΄λλ₯Ό λ°°ν¬νκ³  κ΄λ¦¬ν΄μΌ νλ μν©μ΄λΌλ©΄ `4κ°μ§ μ΄μ`μ λν ν΄λ΅μ λ°λμ μ°ΎμμΌ νλ€.

### 4κ°μ§ μ΄μ

- λ°°ν¬ κ΄λ¦¬ : μ΄λ€ μ»¨νμ΄λλ₯Ό μ΄λ νΈμ€νΈμ λ°°μΉνμ¬ κ΅¬λμν¬ κ²μΈκ°? κ° νΈμ€νΈκ° κ°μ§ νμ λ λ¦¬μμ€μ λ§μΆ° μ΄λ»κ² μ΅μ μ μ€μΌμ€λ§μ κ΅¬νν  κ²μΈκ°? μ΄λ»κ² νλ©΄ μ΄λ¬ν λ°°ν¬ μνλ₯Ό μ΅μνμ λΈλ ₯μΌλ‘ μ μ§ κ΄λ¦¬ν  μ μμ κ²μΈκ°?
- μ μ΄ λ° λͺ¨λν°λ§ : κ΅¬λ μ€μΈ κ° μ»¨νμ΄λλ€μ μνλ₯Ό μ΄λ»κ² μΆμ νκ³  κ΄λ¦¬ν  κ²μΈκ°?
- μ€μΌμΌλ§ : μμλ‘ λ³ννλ μ΄μ μν©κ³Ό μ¬μ©λ κ·λͺ¨μ μ΄λ»κ² λμν  κ²μΈκ°?
- λ€νΈμνΉ : μ΄λ κ² μ΄μλλ μΈμ€ν΄μ€ λ° μ»¨νμ΄λλ€μ μ΄λ»κ² μνΈ μ°κ²°ν  κ²μΈκ°?

μ 4κ°μ§ μ΄μλ₯Ό ν΄κ²°νκΈ° μν΄ λ§λ€μ΄μ§ κ°λμ΄ `μ»¨νμ΄λ μ€μΌμ€λ₯΄λ μ΄μ`μ΄λ€.

## π¦ μΏ λ²λ€ν°μ€ ν΅μ¬ μ€κ³ μ¬μ

### μ μΈμ  κ΅¬μ± κΈ°λ°μ λ°°ν¬ νκ²½
μΏ λ²λ€ν°μ€λ μνλ μν(Desired state)μ νμ¬μ μν(Current state)κ° μνΈ μΌμΉνλμ§λ₯Ό μ§μμ μΌλ‘ μ²΄ν¬νκ³  μλ°μ΄νΈνλ€.

λ°λΌμ λ΄κ² νμν μμμ λν΄ μνλ μνλ₯Ό μ€μ νλ κ²λ§μΌλ‘λ νΈμ€νΈμ λ¦¬μμ€ νν©μ λ§μΆ° μ΅μ μ λ°°μΉλ‘ λ°°ν¬λκ±°λ λ³κ²½λλ©° 
λ§μ½ νΉμ  μμμ λ¬Έμ κ° μκ²Όμ κ²½μ°, μΏ λ²λ€ν°μ€λ ν΄λΉ μμκ° μνλ μνλ‘ λ€μ λ³΅κ΅¬λ  μ μλλ‘ νμν μ‘°μΉλ₯Ό μλμΌλ‘ μ·¨νλ€.

![](https://seongjin.me/content/images/2022/02/declarative.jpg)

### κΈ°λ₯λ¨μμ λΆμ°
μΏ λ²λ€ν°μ€μμλ κ°κ°μ κΈ°λ₯λ€μ΄ κ°λ³μ μΈ κ΅¬μ± μμλ‘μ λλ¦½μ μΌλ‘ λΆμ°λμ΄ μλ€. 

μ€μ λ‘ Node, ReplicaSet, Deployment, Namespace λ± ν΄λ¬μ€ν°λ₯Ό κ΅¬μ±νλ μ£Όμ μμλ€μ΄ λͺ¨λ Controller λ‘μ κ΅¬μ±λμ΄ μμΌλ©°, 
μ΄λ€μ Kube Controller Manager μμ ν¨ν€μ§ λμ΄ μλ€.

![](https://seongjin.me/content/images/2022/02/kube-controller.png)


### ν΄λ¬μ€ν° λ¨μ μ€μ μ μ΄
μΏ λ²λ€ν°μ€μμλ μ μ²΄ λ¬Όλ¦¬ λ¦¬μμ€λ₯Ό ν΄λ¬μ€ν° λ¨μλ‘ μΆμννμ¬ κ΄λ¦¬νλ€. 

ν΄λ¬μ€ν° λ΄λΆμλ ν΄λ¬μ€ν°μ κ΅¬μ± μμλ€μ λν΄ μ μ΄ κΆνμ κ°μ§ Control Plane μ­ν μ Master Nodeλ₯Ό λκ² λλ©°, 
κ΄λ¦¬μλ μ΄ λ§μ€ν° λΈλλ₯Ό μ΄μ©νμ¬ ν΄λ¬μ€ν° μ μ²΄λ₯Ό μ μ΄νλ€.

![](https://seongjin.me/content/images/2022/02/cluster.png)

### λμ  κ·Έλ£Ήν
μΏ λ²λ€ν°μ€μ κ΅¬μ± μμλ€μλ μΏΌλ¦¬ κ°λ₯ν Labelκ³Ό λ©νλ°μ΄ν°μ© (Annotationμ μμλ‘ ν€-κ° μμ μ½μν  μ μλ€. 

κ΄λ¦¬μλ selectorλ₯Ό μ΄μ©ν΄μ λ μ΄λΈ κΈ°μ€μΌλ‘ κ΅¬μ± μμλ€μ μ μ°νκ² κ΄λ¦¬ν  μ μκ³ , 
μ΄λΈνμ΄μμ κΈ°μ¬λ λ΄μ©μ μ°Έκ³ νμ¬ ν΄λΉ μμμ νΉμ§μ μΈ λ΄μ­μ μΆμ ν  μ μλ€.

![](https://seongjin.me/content/images/2022/02/labels.png)

### API κΈ°λ° μνΈμμ©

μΏ λ²λ€ν°μ€μ κ΅¬μ± μμλ€μ μ€μ§ Kubernetes API serverλ₯Ό ν΅ν΄μλ§ μνΈ μ κ·Όμ΄ κ°λ₯ν κ΅¬μ‘°λ₯Ό κ°μ§λ€. 

λ§μ€ν° λΈλμμ `kubectl`μ κ±°μ³ μ€νλλ λͺ¨λ  λͺλ Ήμ μ΄ API μλ²λ₯Ό κ±°μ³ μνλλ©°, Control Planeμ ν¬ν¨λ ν΄λ¬μ€ν° 
μ μ΄ μμλ Worker Nodeμ ν¬ν¨λ kubelet, νλ‘μ μ­μ API μλ²λ₯Ό ν­μ λ°λΌλ³΄κ² λμ΄ μλ€.

![](https://seongjin.me/content/images/2022/02/apiserver.png)

## π¦ λμ»€μ μΏ λ²λ€ν°μ€μ μ°¨μ΄

λμ»€λ νλμ imageλ₯Ό μ»¨νμ΄λμ λμ°μ§λ§
μΏ λ²λ€ν°μ€λ μ»¨νμ΄λλ₯Ό λμ μΌλ‘ μ¬λ¬κ°λ¦ μ»¨νμ΄λλ‘ νμν λ§νΌ μμ±νκ±°λ λΆλ¦¬νμ¬ MS μ΄μνλ λκ΅¬μ΄λ€.

# Reference
[μΏ λ²λ€ν°μ€μ μ»¨νμ΄λ μ€μΌμ€νΈλ μ΄μ](https://seongjin.me/kubernetes-core-concepts/)