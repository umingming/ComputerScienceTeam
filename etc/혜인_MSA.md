# MSA

<aside>
π‘ **MSA(MicroService Architecture)**
: νλμ ν° μ΄νλ¦¬μΌμ΄μμ μ¬λ¬ κ°μ μμ μ΄νλ¦¬μΌμ΄μμΌλ‘ μͺΌκ°μ΄ λ³κ²½κ³Ό μ‘°ν©μ΄ κ°λ₯νλλ‘ λ§λ  μν€νμ³

</aside>

## MSA λ±μ₯ λ°°κ²½

### Monolithic Architecture
![img1 daumcdn (1)](https://user-images.githubusercontent.com/90780701/166146302-28edbfce-6c5a-4c26-8850-9650ad4cb994.png)

**μ μ**

- μννΈμ¨μ΄μ λͺ¨λ  κ΅¬μ±μμκ° ν νλ‘μ νΈμ ν΅ν©λμ΄ μλ νν

**νΉμ§**

- μ μ²΄ μ΄νλ¦¬μΌμ΄μμ΄ νλλ‘ λμ΄μμ΄μ λμΌν κ°λ° ν΄μ μ¬μ©
- λ°°ν¬ λ° νμ€νΈλ νλμ μ΄νλ¦¬μΌμ΄μλ§ μννλ©΄ λ¨
- κ° μ»΄ν¬λνΈλ€μ΄ ν¨μλ‘ νΈμΆλκΈ° λλ¬Έμ μ±λ₯μ μ μ½μ΄ λ νκ³  μ΄μ κ΄λ¦¬κ° μ©μ΄

**νκ³**

- λΆλΆ μ₯μ κ° μ μ²΄ μλΉμ€μ μ₯μ λ‘ νλλ  μ μλ€.
- λΆλΆμ μΈ Scale-outμ΄ μ΄λ ΅λ€.
    - Scale-Out: μ¬λ¬ μλ²λ‘ λλμ΄ μΌμ μ²λ¦¬νλ λ°©μ

- λΉλ μκ° λ° νμ€νΈμκ°, λ°°ν¬ μκ°μ΄ μ€λ κ±Έλ¦°λ€
- ν νλ μμν¬μ μΈμ΄μ μ’μμ μ΄λ€

## **Micro service**

<aside>
π‘ **Micro service
:** μ€μ€λ‘ λμκ° μ μμΌλ©°, λλ¦½μ  λ°°ν¬ κ°λ₯ν μμ μλΉμ€

</aside>

- κ°κ°μ μλΉμ€λ κ·Έ ν¬κΈ°κ° μμ λΏ, μλΉμ€ μμ²΄λ νλμ λͺ¨λλ¦¬μ μν€νμ³μ μ μ¬ν κ΅¬μ‘°λ₯Ό κ°μ§
- κ°κ°μ μλΉμ€λ λλ¦½μ μΌλ‘ λ°°ν¬κ° κ°λ₯ ν΄μΌν¨
- κ°κ°μ μλΉμ€λ λ€λ₯Έ μλΉμ€μ λν μμ‘΄μ±μ΄ μ΅μν λμ΄μΌ ν¨
- κ° μλΉμ€λ κ°λ³ νλ‘μΈμ€λ‘ κ΅¬λλλ©°, RESTμ κ°μ κ°λ²Όμ΄ λ°©μμΌλ‘ ν΅μ λμ΄μΌ ν¨

## **MSAμ μ₯λ¨μ **

### MSAμ μ₯μ 

- μλΉμ€ λ³ κ°λ³ λ°°ν¬ κ°λ₯
    - λ°°ν¬ μ μ μ²΄ μλΉμ€μ μ€λ¨μ΄ μμ
    - μκ΅¬μ¬ν­μ μ μνκ² λ°μνμ¬ λΉ λ₯΄κ² λ°°ν¬ν  μ μμ
- νΉμ  μλΉμ€μ λν νμ₯μ±μ΄ μ©μ΄ν¨
    - ν΄λΌμ°λ μ¬μ©μ μ ν©ν μν€νμ³
- μ₯μ κ° μ μ²΄ μλΉμ€λ‘ νμ₯λ  κ°λ₯μ±μ΄ μ μ
    - λΆλΆμ  μ₯μ μ λν κ²©λ¦¬κ° μμν¨
- ν΄λΉ κΈ°λ₯μ λ§λ κΈ°μ , μΈμ΄ λ±μ μ ννμ¬ μ¬μ©ν  μ μλ€. (μ κΈ°μ μ μ μ©μ΄ μ μ°, μλΉμ€λ₯Ό polyglotνκ² κ°λ°/μ΄μ κ°λ₯)

### MSAμ λ¨μ 

- μλΉμ€ κ° νΈμΆ μ APIλ₯Ό μ¬μ©νκΈ° λλ¬Έμ, ν΅μ  λΉμ©μ΄λ Latencyκ° κ·Έλ§νΌ λμ΄λκ² λ¨
- μλΉμ€κ° λΆλ¦¬λμ΄ μκΈ° λλ¬Έμ νμ€νΈμ νΈλμ­μμ λ³΅μ‘λκ° μ¦κ°νκ³  λ§μ μμμ νμλ‘ ν¨
- λ°μ΄ν°κ° μ¬λ¬ μλΉμ€μ κ±Έμ³ λΆμ°λκΈ° λλ¬Έμ νλ²μ μ‘°ννκΈ° μ΄λ ΅κ³ , λ°μ΄ν°μ μ ν©μ± λν κ΄λ¦¬νκΈ° μ΄λ ΅λ€.
    - msaλ λ°μ΄ν° μ μ₯ μ νλμ DBμ μ€μ μ§μ€νλ₯Ό νμ§ μκ³  μλΉμ€ λ³ λ³λμ DBλ₯Ό μ¬μ©
    - DBμ μ’λ₯λ₯Ό λ³λλ‘ κ°μ Έκ° μλ μκ³ , κ°μ DBλ₯Ό μ¬μ©νλλΌλ λλμ΄μ μ¬μ©
