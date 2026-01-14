# Vaja7-PWM-NUCLEO

Pinout slika:
<img width="821" height="624" alt="image" src="https://github.com/user-attachments/assets/f42285b6-2e2c-4e59-8b6a-cd24673ec110" />

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
