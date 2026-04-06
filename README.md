# OCTMNIST: Klasyfikacja chorób siatkówki (CNV vs NORMAL)

Projekt uczenia maszynowego mający na celu automatyczną diagnostykę neowaskularyzacji naczyniówkowej (CNV) w porównaniu ze zdrową siatkówką (NORMAL) na podstawie medycznych obrazów OCT (Optical Coherence Tomography). Rozwiązanie opiera się na zbiorze [MedMNIST (OCTMNIST)](https://medmnist.com/) i wykorzystuje techniki Transfer Learningu.

## O projekcie
Cały kod oraz proces analityczny znajdują się w notatniku Jupyter: `umwdm_OCTMNIST_CNV_vs_NORMAL.ipynb`.

W projekcie przeprowadzono kompleksowy proces budowy i analizy medycznego modelu klasyfikacyjnego, ze szczególnym naciskiem na jego wyjaśnialność (Explainable AI - XAI):
* **Przetwarzanie obrazów (Preprocessing):** Zastosowanie algorytmu CLAHE do poprawy kontrastu oraz filtru Gaussa (Gaussian Blur) w celu redukcji szumów.
* **Balansowanie danych:** Użycie `WeightedRandomSampler`, aby zniwelować problem niezbalansowanych klas w zbiorze treningowym.
* **Transfer Learning:** Wykorzystanie pretrenowanej architektury **ResNet18** (wagi ImageNet) z zamrożonym *backbonem* i dostosowaną warstwą klasyfikacyjną.
* **Tuning hiperparametrów:** Automatyczna optymalizacja (learning rate, dropout, optymalizator) za pomocą biblioteki **Optuna**.
* **Ewaluacja:** Ocena modelu z wykorzystaniem macierzy pomyłek (Confusion Matrix), krzywych ROC (AUC) oraz Precision-Recall.
* **Zaawansowana Wyjaśnialność (XAI):** Zastosowanie zaawansowanych metod interpretacji decyzji modelu obrazowego, aby sprawdzić, na co "patrzy" sieć neuronowa:
  * *Grad-CAM*
  * *Saliency Maps*
  * *Integrated Gradients*
  * *Occlusion Sensitivity*

## Użyte technologie
Projekt został napisany w języku Python. Główne wykorzystane biblioteki to:
* `PyTorch`, `torchvision` (budowa i trening sieci neuronowej)
* `medmnist` (oficjalna biblioteka udostępniająca zbiór danych)
* `optuna` (optymalizacja hiperparametrów)
* `opencv-python` (`cv2`), `Pillow` (przetwarzanie i augmentacja obrazów)
* `scikit-learn` (metryki ewaluacyjne)
* `matplotlib`, `seaborn` (wizualizacja danych, wykresów i map aktywacji)

## Jak uruchomić projekt
1. Sklonuj repozytorium na swój komputer:
   ```bash
   git clone [https://github.com/PassivelyIronic/umwdm_OCTMNIST_CNV_prediction.git](https://github.com/PassivelyIronic/umwdm_OCTMNIST_CNV_prediction.git)
