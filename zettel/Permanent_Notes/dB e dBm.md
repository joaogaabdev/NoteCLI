## 1. Por que dB e dBm são centrais em ISPs

Em redes ópticas, **não se mede tensão nem corrente**, mas **potência luminosa**.  
Essa potência varia em ordens de grandeza muito grandes — e é aí que entram **dB** e **dBm**.

Em ISPs, praticamente todo diagnóstico físico passa por:
- Potência óptica
- Perdas
- Margem do enlace

Tudo isso é expresso em **decibéis**.

---

## 2. O que é dB (decibel)

### Definição

**dB** é uma **unidade logarítmica relativa**, usada para expressar **ganho ou perda** entre dois valores de potência.

> dB **não é valor absoluto**.  
> dB **sempre compara**.

### Fórmula conceitual

$$
dB=10⋅log⁡10(PoutPin)dB = 10 \cdot \log_{10}\left(\frac{P_{out}}{P_{in}}\right)dB=10⋅log10​(Pin​Pout​​)

$$
### Interpretação prática

- dB negativo → perda
- dB positivo → ganho
- 0 dB → sem alteração

### Exemplos em ISP

- Emenda: −0,05 a −0,3 dB
- Conector: −0,2 dB
- Splitter 1:8: ≈ −10,5 dB
- Fibra: ≈ −0,35 dB/km (1310 nm)


**dB soma**.  
Perdas ao longo do enlace são somadas linearmente (porque já estão em log).

---

## 3. O que é dBm

### Definição

**dBm** é uma **medida absoluta de potência**, referenciada a **1 milliwatt (mW)**.

> dBm = potência real do sinal óptico.

### Referência

- 0 dBm = 1 mW
- −10 dBm ≈ 0,1 mW
- −20 dBm ≈ 0,01 mW

Em fibra, valores costumam ser **negativos**, pois a potência é muito pequena.

---

## 4. Diferença essencial entre dB e dBm

|Aspecto|dB|dBm|
|---|---|---|
|Tipo|Relativo|Absoluto|
|Mede|Ganho/perda|Potência|
|Referência|Dois valores|1 mW|
|Uso típico|Atenuação|Sinal recebido|
|Soma direta|Sim|Não (só após conversão)|

Regra mental:

> **dB compara. dBm informa.**

---

## 5. dB e dBm no FTTH (na prática)

### Exemplo de raciocínio típico

- OLT transmite: **+3 dBm**
- Perdas do enlace:
    - Fibra (10 km): −3,5 dB
    - Splitter 1:16: −13,5 dB
    - Conectores/emendas: −1,5 dB  
        **Total:** −18,5 dB
        

Potência na ONT:

+3 dBm−18,5 dB=−15,5 dBm+3\ dBm − 18,5\ dB = −15,5\ dBm+3 dBm−18,5 dB=−15,5 dBm

Se a ONT opera entre −8 e −28 dBm → **link saudável**.

---

## 6. Valores típicos de potência em ISPs

### GPON (referência comum)

- OLT Tx: +1 a +5 dBm
- ONT Rx aceitável:
    - Mínimo: ~ −28 dBm
    - Ideal: −8 a −20 dBm
- Abaixo de −28 dBm → instabilidade ou link down

Potência “muito boa” demais também pode ser problema (saturação).

---

## 7. Erros conceituais comuns

❌ “O sinal está −25 dB”  
✔️ “O sinal está −25 dBm”

❌ “Perda de −20 dBm”  
✔️ “Perda de −20 dB”

Misturar dB com dBm é como confundir **velocidade** com **distância**.

---

## 8. Uso no diagnóstico de falhas

- **dBm baixo demais:**
    - Fibra rompida
    - Emenda ruim
    - Conector sujo
    
- **dBm oscilando:**
    - Microcurvatura
    - Drop tensionado
        
- **dBm normal, cliente sem navegação:**
    - Problema acima da camada física
        

dBm bom **não garante** serviço, mas dBm ruim **quase sempre explica** o problema.