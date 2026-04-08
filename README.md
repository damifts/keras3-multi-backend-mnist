# Keras 3 Multi-Backend MNIST Classifier

Un'implementazione professionale di un classificatore per il dataset MNIST, sviluppata con **Keras 3** e alimentata dal backend **PyTorch**. Questo progetto mette in luce la flessibilità del nuovo ecosistema Keras Core per la creazione di modelli deep learning agnostici e performanti.

## 🛠️ Caratteristiche Tecniche

- **Backend Agnostico:** Configurato tramite `os.environ["KERAS_BACKEND"] = "torch"`, permettendo al modello di girare nativamente come un modulo PyTorch.
- **Preprocessing Integrato:** Utilizzo di una `Lambda` layer per la normalizzazione dei dati ($x/255$), garantendo che il modello accetti input grezzi (pixel 0-255) anche in fase di inferenza.
- **Training Pipeline Robusta:** 
  - `ModelCheckpoint`: Salvataggio automatico dei pesi migliori basato sulla validation loss.
  - `EarlyStopping`: Monitoraggio intelligente per interrompere l'addestramento ed evitare l'overfitting.
  - `TensorBoard`: Log dettagliati delle metriche per un'analisi visiva delle performance.

## 🏗️ Architettura del Modello

Il progetto implementa una **Convolutional Neural Network (CNN)** ottimizzata per il riconoscimento di cifre scritte a mano:
1. **Input Layer:** (28, 28, 1)
2. **Rescaling:** Lambda Layer (Normalization 1/255)
3. **Feature Extraction:** Conv2D (32 filtri, kernel 3x3, ReLU) + MaxPooling2D (pool 2x2)
4. **Classification:** Flatten + Dense (10 unità, Softmax)

## 💻 Installazione e Utilizzo

1. **Clona il repository:**
   ```bash
   git clone https://github.com
   cd pytorch-mnist-from-scratch
   ```
   
2. **Installa le dipendenze:**
  ```bash
  pip install keras>=3.0.0 torch torchvision tensorboard
  ```

3. **Esecuzione:**
Apri il notebook keras_tutorial.ipynb in VS Code o Jupyter Lab per avviare il training.

## 📊 Monitoraggio delle Metriche

Per visualizzare le curve di accuratezza e perdita in tempo reale, avvia TensorBoard dalla root del progetto:
  ```bash
  tensorboard --logdir=logs
  ```
