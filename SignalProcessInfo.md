# Audio Classification in Signal Processing - Internet Review

## @nadimkawwa

This [Medium Post](https://medium.com/@nadimkawwa/can-we-guess-musical-instruments-with-machine-learning-afc8790590b8) written by Nadim Kawwa suggests that short tones of basic music instruments can be easily sorted and identified with a little of Features Engineering and Machine Learning. It uses NSynth dataset which gathers large scale and high quality annotated musical notes. There are 300.000 four second audio snippets wav files sorted over 11 instruments. 

First, the anatomy of a wav file can be described by Librosa package to dissect the wav files: audio and music analysis 
```
y, sr = librosa.load(base_file, sr=None)
```
pour charger un fichier audio avec le sampling rate (fréquence d'échantillonnage) qui caractérise le nombre de valeur du signal échantillonée en 1 seconde. `sr=None` est là uniquement pour préserver la fréquence d'échantillonnage d'origine. Différemment, le signal du fichier peut être ré-échantilloné 

**Waveform** correspond au signal continu avant échantillonnage pour numérisation. 
Les harmoniques sont des multiples de la fréquence fondamentales dans le cadre de Fourier.

```
y_harmonic, y_percussive = librosa.effects.hpss(base_file)
```
pour décomposer le signal en signal percussif et en signal harmonique. 

**Chroma Energy** fait référence en français à la note de musique correspondante. **Pitch** est la hauteur d'un son. **In color** veut dire à l'unisson. 

**Mel Spectrogram** trace l'intensité en échelle log de l'amplitude de la STFT (Short Time Fourier Transform). La STFT est un séquence de FFT sur des segments de données obtenus avec des fenêtres superposées. En fait, l'oreille humaine est un processus en temps réel ce qui justifie les fenêtres superposées. Enfin, le spectrogramme temps réel est encodé par la cochlee de l'oreille interne. 

**Mec Scale** est une rpz empirique du signal où chaque hauteur de son est équidistante des autres. 
```
librosa.feature.melspectrogram(y, sr, n_mels=128, fmax=8000)
```

La Préparation de la data peut être effectuée sur différents features. 
La prédiction peut être effectuée par des moyens divers et variés: Naive Bayes bad, SVM bad, Random Forests bad 
CNN in CIFAR style 55% reliability accuracy. 

## @sukantkhurana [Medium post](https://medium.com/@sukantkhurana/music-classification-using-artificial-intelligence-3d21c59c5cb2)

La classification des musiques peut être utilisée pour :
- Générer des playlists avec des morceaux similaires 
- Recommand similar music in digital music services
- Categorizing music based on genre

Il existe plusieurs dataset pour entraîner ses IA. GITZAN dataset, MIDI files. Mais évidemment le modèle devra être entraîné non pas directement sur le morceau de musique mais sur des échantillons avec des features choisis auparavant. 


## @