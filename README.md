## Requisiti
Le librerie usate nell'ambiente virtuale utilizzato per il notebook sono nel file `requirements.txt`

## Dataset
Per scaricare il dataset clicca [qui](https://www.kaggle.com/datasets/andradaolteanu/gtzan-dataset-music-genre-classification/).
una volta scaricato il dataset compresso 'archive.zip', estrarre nella cartella root del repository.

## Guida al codice: `main.ipynb`

### Caricamento e analisi iniziale dati
Caricamento del CSV in un Pandas.DataFrame e analisi generale del dataframe.
### Test per creazione dataset `audio --> immagine`
Generazione di grafici per analisi audio:
- waveform;
- ampiezza di decibel;
- cromogramma con analisi di Fourier;
- spettrogramma di frequenze Mel.
Analisi più approfondita dei dati con:
- matrice di correlazione;
- Boxplot dei BPM per genere;
- Scatterplot con analisi componenti principali (PCA)
### Preparazione dati
Pulizia del dataframe (colonne vuote, label encoding...).
### Split Train-Val-Test
Split del dataset per i modelli e normalizzazione delle features.
### Creazione e Addestramento Modelli
Funzioni per addestramento del modello:
- classe `MyCallback`: tiene traccia degli output di ogni epoca (threshold: 94%)
- funzione `trainModel`: Setta baseline comuni a tutti i modelli (batch size, funzione loss...) ed effettua compilazione e fit dopo aver preso come input modello e ottimizzatore, ritornando i risultati di ogni epoca
- funzione `plotHistory`: Usa l'output di 'trainModel' per creare un plot che rappresenta il progresso per epoca di loss e accuracy, sia per train che per validation
Queste funzioni sono utilizzate per addestrare e rappresentare i 3 modelli definiti nelle celle successive.
### Test Modelli
Uso la funzione `evaluate()` per ottenere la loss e l'accuracy sui dati di test di ognuno dei 3 modelli addestrati