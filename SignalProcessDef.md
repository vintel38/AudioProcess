# Une petite documentation sur le traitement du signal en machine learning 

**Bit depth** : resolution d'un microphone (16 bits ou 24 bits) pour le nombre de valeurs différentes que le microphone peut prendre en sortie 2^16 ou 2^24 valeurs 

**Nyquist frequency** : fréquence d'échantillonage max pour vérifier le critére de Shannon (fech = 1/2 * fmax), fmax étant la fréquence max contenue dans le spectre du signal 

Dans des audios vocaux, la plupart des changements se traduisent à faible fréquence donc on peut se concentrer sur ces basses fréquences et faire un down-sampling du signal dans le preprocess. 

**Periodogram** : an estimate of the spectral density of a signal.
**Spectrogam** : stacking periodogram during time. L'info est représentée en version fréquentielle selon le temps et la fréquence 

**Short Time Fourier Transform** : prendre une petite fenêtre dans le temps et supposer que l'évolution du signal est stationnaire sur cette fenêtre. La fenêtre bouge au cours du temps sur tout le signal. Puis, un periodogram est performé sur la fenêtre. 

**Hamming window** : fenêtre pour effectuer le prélèvement sur le signal en forme de cloche pour éviter le spectral leakage. 

Melscale - Mel Filterbank: facile de faire la différence entre deux son à fréquences médium mais compliquée de faire la différence à hautes fréquences. Log scale pour faire facilement la différence entre deux signaux de fréquences médium sans s'intéresser à la différence entre deux signaux de hautes fréquences. Pour cela créer une banque de filtre à des fréquences log : créee les features pour le CNN. Convertit la FFT en mel scale spectrogram. 

**Mel-Frequency Cepstral Coefficient** : jeu réduit de paramètres qui décrit la forme globale de l'envelope spectrale

**Chroma Frequencies** : le spectre est entièrement projeté sur les 12 valeurs qui représentent les 12 demi-tons d'une octave musicale 

STFT et Melscale donnes des filtres et transformations qui se recouvrent. Ainsi les données et features produits à la suite du Mel Filterbank sont très corrélés. 
Pour décorréler, utiliser la Discrete Cosin Transform : bcp utilisé en audio/image compression, filtre passe bas pour compacter les informations dans les features à basses fréquences, enlever les informations à hautes fréquences. Produit les Mel Spectrum Coefficients. 

**Zero crossing rate** : fréquence de variation du signal entre les valeurs négatives et positives 

**Spectral centroid** : centre de masse pour un signal, somme pondérée des fréquences présentes dans le signal

**Spectral Rollof** : seuil de fréquence sous laquelle est contenue 85% de l'énergie spectrale totale



**Links for understanding the all content** :

- [Feature Engineering for Audio](http://practicalcryptography.com/miscellaneous/machine-learning/guide-mel-frequency-cepstral-coefficients-mfccs/)

- [Explanation of Audio Machine Learning](https://haythamfayek.com/2016/04/21/speech-processing-for-machine-learning.html)

- [Discrete Cosin Transform](http://datagenetics.com/blog/november32012/index.html)

- [Installation procedures for Python Speech Features](https://github.com/jameslyons/python_speech_features)