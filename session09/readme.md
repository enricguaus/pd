# MalaM-ent-
> Matemàtiques aplicades a la Música (pensament)

## Introducció

Aquest recurs forma part d'una sessió de l'assignatura de **Matemàtiques aplicades a la Música** de la **Doble titulació en Matemàtiques i Música UPC-ESMUC** impartit per l'[ESMUC](https://www.esmuc.cat/estudis/grau/musica-i-matematiques/) i [UPC](https://fme.upc.edu/ca/estudis/graus/doble-titulacio-en-matematiques-i-musica). 

La sessió ha estat coordinada per **Laura Farré Rozada** i impartida per **Fèlix Pastor** i **Enric Guaus** el dimecres 3 de desembre de 2025.

L'objectiu de la sessió és mostrar com les diferents tecnologies relacionades amb la intel·ligència artificial poden ser usades en entorns musicals com a font d'inspiració. Per això s'han repassat diferents propostes del col·lectiu [Sheepdog](http://sheepdog.es/), passant per ArInt, Darwin, Neural Impro, nanAI, Physis i Tierras Raras. 

El present recurs presenta l'activitat pràctica associada a la sessió i que consisteix en l'exploració musical d'uns models pre-entrenats de [síntesi neuronal](https://www.rncm.ac.uk/research/research-activity/research-centres-rncm/prism/prism-blog/a-short-history-of-neural-synthesis/) usant el software de programació [PureData](https://puredata.info/).

## Instal·lació

### PureData

Instal.lar la darrera versió de [PureData](https://puredata.info/), la versió *vanilla* (sense cap extensió) disponible a la subplana de [Downloads](https://puredata.info/downloads).

### nn~ per pureData

Cal instal·lar una llibreria externa anomenada [nn~](https://acids-ircam.github.io/nn_tilde/). El [PureData](https://puredata.info/) ofereix una utilitat per instal·lar llibreries amb facilitat, adaptant-se a la plataforma existent. El procediment és el següent:

1. Obrir el [PureData](https://puredata.info/).
2. Anar al menú *Help ->  Find Externals*.
3. Especificar *Search for -> Libraries*.
4. Cercar la  paraula `nn~`.
5. Quan la trobi, prémer el botó *Install*.
6. Trigarà uns instants. Quan acabi, tancar el [PureData](https://puredata.info/) i tornar-lo a obrir.
7. La llibreria ja està instal·lada.

### Detallets sobre el [PureData](https://puredata.info/)

Un cop instal·lada la llibreria *nn~*, ja es pot obrir el patch (programa) fent doble click damunt el nom. A l'obrir el [PureData](https://puredata.info/) cal tenir en compte uns detallets:

1. Finestra del programa: A banda del patch, el [PureData](https://puredata.info/) obre una finestra pròpia on mostra els missatges de l'execució (log), permet activar o desactivar el DSP, etc. A banda, també obre els patchos, però aquesta finestra sempre està present.
2. També cal especificar els dispositius d'àudio que cal fer servir, tant d'entrada com de sortida a *pd -> Preferences -> Edit preferences*, i seleccionar que corresponguin.
3. En el [PureData](https://puredata.info/) cal activar o desactivar l'*Edit mode* per tal de poder incloure, moure o editar objectes (*Edit mode* activat) o executar el patch tot movent els sliders, prement botons, etc. (*Edit mode* desactivat). Per activar o desactivar l'*Edit mode* cal prémer `command + e`.

## Execució del patch

### Descàrrega del patch

Per descarregar el patch, cal descarregar TOT el projecte a una carpeta coneguda (per exemple, *Baixades*). Per fer-ho, cal:

1. Anar a la plana principal del projecte a [Github](https://github.com/enricguaus/MalaM-ent-).
2. Obrir el menú identificat en color verd com a *<> Code -> Download ZIP*.
3. Descomprimir el fitxer *.zip* descarregat.

El patch té aquest aspecte:

![Aspecte del neural_synthesis.pd](./neural_synthesis.png "Aspecte del Neural Synthesis.pd")

### Descàrrega dels models

EL Github permet pujar fitxers amb una mida màxima. Els models pre-entrenats de síntesi neuronal sobrepassen el límit establert així que s'han penjat a una carpeta compartida a OneDrive. Concretament, cal descarregar dos models i posar-los a la mateixa carpeta on hi ha el patch (descarregat a l'apartat anterior). Els models són:

- [aigua_48k.ts](https://esmuc-my.sharepoint.com/:v:/g/personal/eguaus_esmuc_cat/IQCe5mBdReeUTZd1WJCzL7mbAai6iotG0uQ1oHojUJgnIgg?nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJPbmVEcml2ZUZvckJ1c2luZXNzIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXciLCJyZWZlcnJhbFZpZXciOiJNeUZpbGVzTGlua0NvcHkifX0&e=WL2nbg)
- [veu_44k1.ts](https://esmuc-my.sharepoint.com/:v:/g/personal/eguaus_esmuc_cat/IQC4dBLUKGR2RZvqSHd61lqiAQkBy_M-f4jEP9y8e5w11nk?nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJPbmVEcml2ZUZvckJ1c2luZXNzIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXciLCJyZWZlcnJhbFZpZXciOiJNeUZpbGVzTGlua0NvcHkifX0&e=wRyR5b)

Nota: pot ser que el navegador intenti reproduir un ditxer multimedia. Ni cas, quan no pugui, cal indicar que es vol descarregar.

### Execució del patch

El patch està pensat per experimentar amb 4 configuracions diferents:

| Model | Mode |
| ----- | ---- |
| Aigua | Forward |
| Aigua | Encode/Decode |
| Veu | Forward |
| Veu | Encode/Decode |

on:

- Model: 
    - Aigua: Sintetitza el so d'aigua a partir de l'entrada d'àudio donada (a temps real).
    - Veu: Sintetitza el so d'aigua a partir de l'entrada d'àudio donada (a temps real).
- Mode:
    - Forward: Intenta sintetitzar el so el més semblant possible al de l'entrada d'àudio donada.
    - Encode/Decode: Permet jugar amb el valor dels 4 primers paràmetres de l'espai latent (veure l'estructura d'un [Autoencoder](https://ca.wikipedia.org/wiki/Autoencoder)) de manera *boja* sense cap sentit musical.

Amb això, el patch està pensar perquè l'usuari interaccioni només amb els objectes amb color groc de fons, que són:

- Activar l'àudio d'entrada (on/of)
- Seleccionar el model (aigua/veu)
- Seleccionar el mode (forward/encode-decode)
- Mute (on/off)
- Volum de sortida (0..1)

Per interactuar amb el patch, aquest ha de tenir el *Edit mode* desactivat. Funciona a temps real, però amb certa latència entre l'entrada i la sortida.

## Pràctica

Per fer la pràctica es demana:

1. Instal·lar el [PureData](https://puredata.info/).
2. Instal·lar la llibreria [nn~](https://acids-ircam.github.io/nn_tilde/).
3. Descarregar el patch desde [Github](https://github.com/enricguaus/MalaM-ent-).
4. Descarregar els models:
    - [aigua_48k.ts](https://esmuc-my.sharepoint.com/:v:/g/personal/eguaus_esmuc_cat/IQCe5mBdReeUTZd1WJCzL7mbAai6iotG0uQ1oHojUJgnIgg?nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJPbmVEcml2ZUZvckJ1c2luZXNzIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXciLCJyZWZlcnJhbFZpZXciOiJNeUZpbGVzTGlua0NvcHkifX0&e=WL2nbg).
    - [veu_44k1.ts](https://esmuc-my.sharepoint.com/:v:/g/personal/eguaus_esmuc_cat/IQC4dBLUKGR2RZvqSHd61lqiAQkBy_M-f4jEP9y8e5w11nk?nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJPbmVEcml2ZUZvckJ1c2luZXNzIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXciLCJyZWZlcnJhbFZpZXciOiJNeUZpbGVzTGlua0NvcHkifX0&e=wRyR5b).
5. Jugar amb les 4 possibilitats del model.
6. Respondre el Formulari disponible al OneDrive:
    - [Formulari de respostes](https://forms.office.com/Pages/ResponsePage.aspx?id=MziA2ZQOU0WslHunsTY0a0VRaWMJKshNtV-vVzFcnDZUNUE3UThRNFZCTk1OTkhESkpLQjMyVERaQy4u).

## Referències

### Explicació i llibreries:

- [Síntesi neuronal](https://www.rncm.ac.uk/research/research-activity/research-centres-rncm/prism/prism-blog/a-short-history-of-neural-synthesis/)
- [Rave @ IRCAM](https://forum.ircam.fr/projects/detail/rave/)
- [Rave @ Github](https://github.com/acids-ircam/RAVE)
- [nn~ per PureData](https://acids-ircam.github.io/nn_tilde/)

### Models pre-entrenats:

- [IRCAM](https://acids-ircam.github.io/rave_models_download)
- [Intelligent Instruments Lab](https://huggingface.co/Intelligent-Instruments-Lab/rave-models)
- [Altres](https://www.dropbox.com/scl/fo/6th53cqxmpf106jj84usk/AFd9AYaZ3fuYBsGHtzPgWAg?rlkey=auvetbzxc89kv1uzvl7u3kc4n&e=1&dl=0)
