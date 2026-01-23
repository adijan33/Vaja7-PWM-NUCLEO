# Vaja7-PWM-NUCLEO



Pinout slika:

<img width="821" height="624" alt="image" src="https://github.com/user-attachments/assets/f42285b6-2e2c-4e59-8b6a-cd24673ec110" />

okno od TIM1 configuration-parameter settings 

<img width="798" height="766" alt="image" src="https://github.com/user-attachments/assets/77e1331b-13e3-434a-b4b6-b62c02a3266d" />

Slika vezja:
<img width="341" height="492" alt="image" src="https://github.com/user-attachments/assets/4cb179d3-6633-4c15-a11f-ed9568abe3ff" />

Slika osciloskopa pri 25%

<img width="354" height="260" alt="image" src="https://github.com/user-attachments/assets/5e075449-6a26-46f8-8a95-4f7a0fdc6951" />


Slika osciloskopa pri 50%

<img width="353" height="360" alt="image" src="https://github.com/user-attachments/assets/f3ba54d7-3200-4450-a005-f496b51b160d" />




b) Aktivirali smo pin PA8, pri katerem se ob izbiri prikaže oznaka TIM1_CH1, kar pomeni, da je pin povezan s prvim kanalom časovnika TIM1.

d) Nastavljena vrednost Prescalerja je 16, s čimer se zmanjša vhodna frekvenca časovnika.

e) Ko vrednost Counter Period določimo na 100, dobimo frekvenco časovnika 10 kHz, kar vpliva na osnovno periodo PWM signala.

f) V polju PWM Generation Channel Pulse določimo širino impulza, s katero nastavimo delovni cikel. Delovni cikel predstavlja razmerje med časom, ko je signal v aktivnem stanju, in celotno periodo. Če vpišemo vrednost 50, signal deluje s 50 % delovnim ciklom.

3.)

b) Ukaz, ki ga je samodejno ustvaril program CubeMX za nastavitev širine impulza, je:

sConfigOC.Pulse = 50;


c) Zagon PWM signala na prvem kanalu časovnika TIM1 izvedemo z naslednjim ukazom:

HAL_TIM_PWM_Start(&htim1, TIM_CHANNEL_1);


4.)

f) Iz meritev na osciloskopu je razvidno, da je perioda signala T = 26,84 µs, medtem ko trajanje vklopljenega stanja (Ton) znaša 13,42 µs.

5.)

a) Če želimo nastaviti delovni cikel na 25 %, spremenimo vrednost impulza z ukazom:

sConfigOC.Pulse = 25;


g) Razlaga uporabljenih ukazov:

Z ukazom

htim1.Instance->CCR1 = dutyCycle;


v register CCR1 zapišemo trenutno vrednost spremenljivke dutyCycle, ki neposredno določa širino PWM impulza.

Ukaz

dutyCycle += 10;


poveča vrednost delovnega cikla za 10 enot.

S pogojnim stavkom

if(dutyCycle > 90) dutyCycle = 10;


poskrbimo, da se ob preseženi vrednosti 90 delovni cikel ponastavi nazaj na 10.

Ukaz

HAL_Delay(1000);


povzroči premor v programu za 1 sekundo, preden se cikel nadaljuje.
