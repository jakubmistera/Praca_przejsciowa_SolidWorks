# 📐 Optymalizacja Rysunków 2D Odlewów (SolidWorks)

Praca badawczo-inżynierska analizująca i optymalizująca proces tworzenia dokumentacji płaskiej (2D) dla elementów odlewanych w środowisku **Dassault Systèmes SolidWorks**. Celem projektu było opracowanie najszybszej i najmniej awaryjnej metody generowania przekrojów z widocznymi naddatkami obróbkowymi, przy zachowaniu parametrycznego powiązania rysunku z modelem 3D.

## 🎯 Problem Inżynierski
Zgodnie z normami rysunku technicznego maszynowego, rysunek odlewu musi przedstawiać kontur surowy (linia gruba ciągła) oraz nałożony na niego zarys przedmiotu gotowego (linia cienka, długa kreska - dwie kropki). Dodatkowo, obszar naddatków obróbkowych w przekroju musi posiadać podwójną gęstość kreskowania. 

SolidWorks natywnie napotyka trudności w automatycznym generowaniu takich nałożonych widoków bez utraty powiązań (asocjatywności) podczas późniejszych modyfikacji modelu.

## 🛠 Metodyka Badawcza
W ramach pracy przetestowano cztery różne podejścia do modelowania 3D i generowania dokumentacji:
1. **Złożenie wieloczęściowe (Wstaw > Część):** Tworzenie osobnych plików dla odlewu i detalu gotowego.
2. **Zarządzanie Konfiguracjami:** Operowanie wygaszaniem operacji w ramach jednego pliku `.sldprt`.
3. **Modelowanie Powierzchniowe:** Wykorzystanie narzędzia `Wstaw > Powierzchnia`.
4. **Narzędzia Formierskie (Podziel):** Zastosowanie kombinacji `Wstaw > Powierzchnia` oraz `Wstaw > Formy > Podziel`.

## ⚙️ Wnioski i Wybór Optymalnej Metody
W wyniku testów na modelach o różnym stopniu skomplikowania (w tym detal z rowkami i otworami gwintowanymi), za **optymalną uznano Metodę IV (Narzędzia Formierskie)**.

**Główne zalety wybranego rozwiązania:**
* Wymaga tylko jednego pliku źródłowego (brak bałaganu w PDM/strukturze plików).
* 
* **Asocjatywność:** Jako jedyna metoda zachowuje w pełni poprawne i automatyczne kreskowanie naddatków przy parametrycznej zmianie geometrii modelu 3D (np. dodanie nowego kołnierza).
* Brak problemów z wymiarowaniem specyficznych cech (np. pochyleń odlewniczych).

**Ograniczenia metody:**
* Narzuca konieczność ręcznej ukrywania nakładających się krawędzi (detalu i odlewu) w celu nadania im poprawnego stylu linii z poziomu właściwości dokumentu.
* Przy bardzo skomplikowanych cechach (np. nieprzelotowe otwory gwintowane) wymaga zastosowania dodatkowych operacji logicznych w drzewie operacji (FeatureManager).

## 📁 Zawartość Repozytorium
* `images/` - zrzuty ekranu prezentujące rozwiązanie problemów z kreskowaniem i stylami linii.

## 📷 Prezentacja Wyników

### Model odlewu
<img width="459" height="354" alt="image" src="https://github.com/user-attachments/assets/31e33b5f-9747-4ad5-963e-3f7465e7be8f" />

### Metoda I – gotowy rysunek
<img width="701" height="464" alt="image" src="https://github.com/user-attachments/assets/f751b25d-bfd3-4eb1-b4c6-f6c4049ecd7f" />

### Gotowy rysunek
<img width="932" height="1222" alt="image" src="https://github.com/user-attachments/assets/bdc2e123-2052-41c6-b3f7-137bf42943f1" />

---
*Praca zrealizowana w Instytucie Technik Wytwarzania (Zakład Automatyzacji i Obróbki Skrawaniem) na Politechnice Warszawskiej (Kierunek: Automatyzacja i Robotyzacja Procesów Produkcyjnych).*
