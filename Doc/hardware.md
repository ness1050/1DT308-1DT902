# Hårdvara

## Grunduppsättning
Enheter som används:
- Pycom lopy-4
- Expansion Board 3.1

![pycom](img/Expansion_Board_3_LoPy4.png)

Länkar:

[Expansion Board 3.1](https://docs.pycom.io/datasheets/expansionboards/expansion3/)

[LoPy4](https://pycom.io/product/lopy4/)

## Sensorer
I projektet kommer vi använda oss av 
- PIR (Passive infrared sensor)

<img src="img/pir.jpg" width="500"/>

- LDR (Photoresistor) 

![LDR](img/photoresistor.jpg)

Länkar: 

[PIR rörelsedetektor HC-SR501](https://www.electrokit.com/produkt/pir-rorelsedetektor-hc-sr501/)

[LDR (Photoresistor) ](https://www.electrokit.com/produkt/fotomotstand-cds-2-5-kohm/)

## LoRa-antenn

<img src="img/lora-antenna-kit-pycom-ant-807.jpg" width="500"/>

Länkar:

[LoRa antenn](https://pycom.io/product/lora-868mhz-915mhz-sigfox-antenna-kit/)


## Övrig

- 3-6 st LED
- Kablar
- Resistor (1kΩ)
- Batteri eller powerbanks

## Anslutningar

Sammanfattning av samband. "←→ " betyder en kabel eller anslutning

- LOPY4 GND ←→ Black/Blue Power Rail (BPR)
- LOPY4 3V3 ←→  Red Power Rail (RPR)
- LOPY4 (P11) ←→  [ Anode (+) - LED - Cathode (-) ] ←→  [ resistor ] ←→  BPR(GND)
- BPR (GND) ←→ [ resistor ] ←→ [ LOPY4 (P16) ] ←→ [LDR] ←→ BPR(3V3)
- PIR ←→  [ BPR (GND) ←→ PIR(-) ] ←→  [ BPR (3V3) ←→ PIR(+) ] ←→[ BPR  (LOPY4 (P13)) ←→ PIR(OutPut) ]


## Kopplingsschema

### Koppling mellan LED, photoresistor och Pir sensor

![LDR](img/LED__LDR___PRI.png)








