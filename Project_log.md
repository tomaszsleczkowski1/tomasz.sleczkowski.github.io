# ESP32 3.1 Audio System

> **Status projektu:** 🟡 W trakcie realizacji
> **Typ projektu:** Projekt własny / Embedded / Elektronika / Audio
> **Autor:** Tomasz Ślęczkowski
> **Data rozpoczęcia:** 20.09.2026

---

# 1. Opis projektu

## 1.1 Cel projektu

Celem projektu jest zaprojektowanie i zbudowanie własnego systemu audio **3.1** opartego na platformie **ESP32**.

Urządzenie ma łączyć funkcje bezprzewodowego odtwarzania muzyki, cyfrowego przetwarzania sygnału audio oraz wielokanałowego wzmacniacza audio.

Docelowo system ma umożliwiać:

* odtwarzanie muzyki przez **Spotify Connect**,
* odtwarzanie muzyki przez **Bluetooth**,
* komunikację przez **Wi-Fi**,
* obsługę konfiguracji **3.1**,
* niezależną obsługę kanału lewego,
* niezależną obsługę kanału prawego,
* obsługę kanału subwoofera,
* cyfrowe przetwarzanie sygnału audio,
* podział pasma dla subwoofera,
* współpracę z wielokanałowym wzmacniaczem,
* stworzenie własnego hardware'u oraz firmware'u.

Projekt będzie rozwijany etapami — od analizy wymagań i architektury, przez prototyp, aż po działające urządzenie i jego końcową obudowę.

---

# 2. Dlaczego powstaje ten projekt?

Projekt jest realizowany jako własne przedsięwzięcie inżynierskie mające na celu praktyczne połączenie wiedzy z zakresu:

* elektroniki,
* systemów embedded,
* mikrokontrolerów,
* projektowania PCB,
* projektowania zasilania,
* komunikacji bezprzewodowej,
* cyfrowego przetwarzania sygnałów,
* audio,
* programowania C/C++,
* diagnostyki i pomiarów.

Projekt będzie dokumentowany od samego początku, włącznie z błędami, zmianami koncepcji oraz decyzjami projektowymi.

---

# 3. Założenia funkcjonalne

| Funkcja              | Założenie          | Status |
| -------------------- | ------------------ | ------ |
| Mikrokontroler ESP32 | Tak                | 🟡     |
| Wi-Fi                | Tak                | 🟡     |
| Spotify Connect      | Tak                | 🟡     |
| Bluetooth Audio      | Tak                | 🟡     |
| System 3.1           | Tak                | 🟡     |
| Kanał lewy           | Tak                | 🟡     |
| Kanał prawy          | Tak                | 🟡     |
| Kanał subwoofera     | Tak                | 🟡     |
| Cyfrowe audio        | Tak                | 🟡     |
| DAC / CODEC          | Do wyboru          | ⚪      |
| DSP                  | Do ustalenia       | ⚪      |
| Wzmacniacz           | Do wyboru          | ⚪      |
| Zasilacz             | Do zaprojektowania | ⚪      |
| Dedykowana PCB       | Planowana          | ⚪      |
| Obudowa              | Planowana          | ⚪      |

### Oznaczenia

* 🟢 Zakończone
* 🟡 W trakcie
* ⚪ Planowane / do ustalenia
* 🔴 Problem / zablokowane

---

# 4. Wymagania techniczne

Ta sekcja będzie stopniowo uzupełniana w miarę podejmowania decyzji projektowych.

## 4.1 Audio

| Parametr                   | Wymaganie | Wartość rzeczywista | Status |
| -------------------------- | --------- | ------------------- | ------ |
| Konfiguracja               | 3.1       | TBD                 | 🟡     |
| Częstotliwość próbkowania  | TBD       | TBD                 | ⚪      |
| Rozdzielczość              | TBD       | TBD                 | ⚪      |
| Pasmo przenoszenia         | TBD       | TBD                 | ⚪      |
| SNR                        | TBD       | TBD                 | ⚪      |
| THD+N                      | TBD       | TBD                 | ⚪      |
| Moc kanału L               | TBD       | TBD                 | ⚪      |
| Moc kanału R               | TBD       | TBD                 | ⚪      |
| Moc kanału SUB             | TBD       | TBD                 | ⚪      |
| Częstotliwość podziału SUB | TBD       | TBD                 | ⚪      |

---

# 5. Architektura systemu

Pierwsza koncepcja systemu:

```text
                     ┌─────────────────────┐
                     │        ESP32        │
                     │                     │
                     │       Wi-Fi         │
                     │   Spotify Connect   │
                     │   Bluetooth Audio   │
                     │                     │
                     └──────────┬──────────┘
                                │
                                │ Cyfrowy sygnał audio
                                │
                                ▼
                     ┌─────────────────────┐
                     │  PRZETWARZANIE AUDIO│
                     │                     │
                     │     DAC / CODEC     │
                     │        DSP          │
                     │        TBD          │
                     └──────────┬──────────┘
                                │
                    ┌───────────┼───────────┐
                    │           │           │
                    ▼           ▼           ▼
                 KANAŁ L     KANAŁ R      SUB
                    │           │           │
                    ▼           ▼           ▼
                 AMP L        AMP R      AMP SUB
                    │           │           │
                    ▼           ▼           ▼
               GŁOŚNIK L    GŁOŚNIK R   SUBWOOFER
```

> **Uwaga:** Jest to wstępna architektura. Poszczególne elementy zostaną dobrane na podstawie wymagań technicznych.

---

# 6. Pytania projektowe

Przed rozpoczęciem projektowania finalnego hardware'u należy odpowiedzieć na następujące pytania:

### ESP32

* [ ] Jaki wariant ESP32 zostanie wykorzystany?
* [ ] Czy wybrany układ posiada wystarczające zasoby?
* [ ] Jakie interfejsy audio są dostępne?
* [ ] Czy Wi-Fi i Bluetooth będą mogły pracować zgodnie z wymaganiami?

### Audio

* [ ] Jaki będzie format danych audio?
* [ ] Jaki interfejs cyfrowego audio zostanie zastosowany?
* [ ] Czy wymagany będzie zewnętrzny DAC?
* [ ] Czy potrzebny będzie CODEC?
* [ ] Czy wymagany będzie DSP?
* [ ] Gdzie będzie realizowany podział pasma?
* [ ] Jak zostanie wygenerowany kanał subwoofera?

### Wzmacniacz

* [ ] Jaka będzie wymagana moc wyjściowa?
* [ ] Jaka będzie impedancja głośników?
* [ ] Jakie napięcie zasilania będzie wymagane?
* [ ] Jaka topologia wzmacniacza zostanie zastosowana?
* [ ] Jakie będą wymagania termiczne?

### Zasilanie

* [ ] Jakie będzie napięcie wejściowe?
* [ ] Jaka będzie maksymalna moc systemu?
* [ ] Jakie napięcia będą wymagane dla poszczególnych bloków?
* [ ] Jak zostaną rozdzielone sekcje zasilania?
* [ ] Jak zostaną rozwiązane kwestie zakłóceń pomiędzy sekcją cyfrową i audio?

---

# 7. Decyzje projektowe

Jednym z najważniejszych elementów dokumentacji jest zapisywanie **dlaczego** została podjęta konkretna decyzja.

Nie wystarczy:

> „Wybrałem układ X.”

Lepiej:

> „Wybrałem układ X zamiast Y, ponieważ zapewnia wymagany interfejs, odpowiednią liczbę kanałów oraz pozwala ograniczyć liczbę dodatkowych komponentów.”

---

## Decyzja #001 — Wybór mikrokontrolera

**Data:** 20.09.2026

**Status:** 🟡 W trakcie analizy

### Rozważane rozwiązania

* ESP32
* ESP32-S3
* Inny wariant ESP32

### Wymagania

Wybrany mikrokontroler powinien zapewniać:

* Wi-Fi,
* Bluetooth,
* odpowiednią wydajność,
* wymagane interfejsy,
* możliwość obsługi audio,
* możliwość dalszego rozwoju firmware'u.

### Wybrana opcja

**TBD**

### Uzasadnienie

**TBD**

### Alternatywy

**TBD**

---

## Decyzja #002 — Interfejs audio

**Status:** ⚪ Do ustalenia

### Rozważane rozwiązania

* I2S
* inne rozwiązanie — TBD

### Wybrana opcja

**TBD**

### Uzasadnienie

**TBD**

---

## Decyzja #003 — DAC / CODEC

**Status:** ⚪ Do ustalenia

### Rozważane układy

* TBD

### Wybrana opcja

**TBD**

### Uzasadnienie

**TBD**

---

## Decyzja #004 — Wzmacniacz

**Status:** ⚪ Do ustalenia

### Wymagania

Dobór wzmacniacza będzie zależał między innymi od:

* impedancji głośników,
* wymaganej mocy,
* napięcia zasilania,
* sprawności,
* temperatury pracy,
* dostępnej przestrzeni,
* kosztu,
* parametrów audio.

### Wybrana opcja

**TBD**

### Uzasadnienie

**TBD**

---

# 8. Dziennik badań i analiz

W tej sekcji będą trafiać wyniki researchu.

---

## Analiza #001 — Możliwości platformy ESP32

**Data:** 20.09.2026

### Cel

Sprawdzenie, czy wybrany wariant ESP32 może obsłużyć wymagane funkcje systemu.

### Do sprawdzenia

* możliwości audio,
* I2S,
* Wi-Fi,
* Bluetooth,
* dostępna pamięć,
* wydajność CPU,
* możliwości DMA,
* biblioteki audio,
* możliwości jednoczesnej pracy poszczególnych interfejsów.

### Wyniki

TBD

### Źródła

TBD

### Wnioski

TBD

---

## Analiza #002 — Spotify Connect

**Data:** TBD

### Cel

Określenie sposobu implementacji Spotify Connect.

### Sprawdzone rozwiązania

TBD

### Wyniki

TBD

### Problemy

TBD

### Wnioski

TBD

---

## Analiza #003 — Bluetooth Audio

**Data:** TBD

### Cel

Określenie sposobu obsługi dźwięku przez Bluetooth.

### Sprawdzone rozwiązania

TBD

### Wyniki

TBD

### Wnioski

TBD

---

# 9. Historia projektu

## 20.09.2026 — Rozpoczęcie projektu

### Wykonano

* zdefiniowano koncepcję urządzenia,
* określono konfigurację 3.1,
* wybrano rodzinę ESP32 jako podstawę systemu,
* określono Spotify Connect jako jedno ze źródeł audio,
* określono Bluetooth jako drugie źródło audio,
* rozpoczęto dokumentację projektu.

### Aktualny rezultat

Powstała pierwsza koncepcja architektury urządzenia.

### Następny krok

Analiza wariantów ESP32 oraz architektury toru audio.

---

# 10. Eksperymenty

Każdy istotny eksperyment będzie dokumentowany.

---

## Eksperyment #001 — TBD

**Data:** TBD

### Cel

TBD

### Hipoteza

TBD

### Konfiguracja

TBD

### Wykorzystany sprzęt

* TBD

### Procedura

1. TBD
2. TBD
3. TBD

### Oczekiwany rezultat

TBD

### Wynik

TBD

### Wnioski

TBD

### Zdjęcia

TBD

---

# 11. Pomiary

W tej sekcji będą umieszczane rzeczywiste pomiary wykonane podczas budowy urządzenia.

W miarę możliwości każdy pomiar powinien zawierać:

* mierzoną wielkość,
* przyrząd pomiarowy,
* model przyrządu,
* warunki pomiaru,
* napięcie zasilania,
* obciążenie,
* wynik,
* datę.

---

## Pomiar #001

**Data:** TBD

**Parametr:** TBD

**Przyrząd:** TBD

**Model:** TBD

**Warunki:** TBD

**Wynik:** TBD

### Zdjęcie

TBD

### Wnioski

TBD

---

# 12. Dokumentacja sprzętowa

## 12.1 Schemat

**Status:** ⚪ Nie rozpoczęto

Planowana dokumentacja:

```text
hardware/
└── schematic/
```

---

## 12.2 PCB

**Status:** ⚪ Planowane

Planowana dokumentacja:

* schemat,
* PCB,
* Gerbery,
* BOM,
* Pick & Place,
* informacje produkcyjne,
* wersje PCB,
* zmiany pomiędzy rewizjami.

---

# 13. Lista komponentów

| Oznaczenie | Element     | Model / Part Number | Ilość | Status |
| ---------- | ----------- | ------------------- | ----: | ------ |
| U1         | ESP32       | TBD                 |     1 | ⚪      |
| U2         | DAC / CODEC | TBD                 |     1 | ⚪      |
| U3         | Wzmacniacz  | TBD                 |     1 | ⚪      |
| PSU        | Zasilacz    | TBD                 |     1 | ⚪      |

Lista będzie aktualizowana podczas projektowania.

---

# 14. Firmware

## 14.1 Planowana struktura

```text
firmware/
│
├── main/
│
├── audio/
│
├── bluetooth/
│
├── wifi/
│
├── spotify/
│
├── dsp/
│
└── system/
```

Struktura może ulec zmianie w trakcie projektu.

---

## 14.2 Kamienie milowe

| Funkcja             | Status |
| ------------------- | ------ |
| Uruchomienie ESP32  | ⚪      |
| Podstawowy firmware | ⚪      |
| Wi-Fi               | ⚪      |
| Bluetooth           | ⚪      |
| Wyjście audio       | ⚪      |
| Spotify Connect     | ⚪      |
| Routing audio       | ⚪      |
| DSP                 | ⚪      |
| Crossover           | ⚪      |
| Obsługa systemu     | ⚪      |

---

# 15. Problemy i debugowanie

Ta sekcja będzie zawierała również nieudane próby.

Nie należy usuwać błędnych rozwiązań.

Są one częścią procesu inżynierskiego.

---

## Problem #001 — TBD

**Data:** TBD

### Objaw

TBD

### Oczekiwane zachowanie

TBD

### Rzeczywiste zachowanie

TBD

### Pierwsza hipoteza

TBD

### Wykonane testy

TBD

### Przyczyna

TBD

### Rozwiązanie

TBD

### Weryfikacja

TBD

### Wnioski

TBD

---

# 16. Zmiany konstrukcyjne

---

## Zmiana #001

**Data:** TBD

### Poprzednie rozwiązanie

TBD

### Nowe rozwiązanie

TBD

### Powód zmiany

TBD

### Oczekiwany efekt

TBD

### Rezultat

TBD

---

# 17. Rewizje sprzętu

## Rev. 0 — Koncepcja

**Status:** 🟡

Pierwsza koncepcja systemu.

---

## Rev. 1 — Prototyp

**Status:** ⚪ Planowane

Planowane elementy:

* pierwsza wersja hardware'u,
* ESP32,
* podstawowy tor audio,
* pierwsze testy,
* pierwsze pomiary.

---

## Rev. 2

**Status:** ⚪ Planowane

### Zmiany

TBD

---

# 18. Plan testów

## Testy funkcjonalne

* [ ] ESP32 uruchamia się prawidłowo
* [ ] Wi-Fi działa
* [ ] Bluetooth działa
* [ ] Spotify Connect działa
* [ ] Wyjście audio działa
* [ ] Kanał L działa
* [ ] Kanał R działa
* [ ] Kanał SUB działa
* [ ] Routing audio działa
* [ ] System reaguje poprawnie na utratę połączenia

## Testy audio

* [ ] Pasmo przenoszenia
* [ ] Poziom wyjściowy
* [ ] Separacja kanałów
* [ ] Poziom szumów
* [ ] THD / THD+N
* [ ] Częstotliwość podziału subwoofera
* [ ] Maksymalny poziom wyjściowy

## Testy sprzętowe

* [ ] Pobór prądu
* [ ] Temperatura pracy
* [ ] Stabilność długoterminowa
* [ ] Zachowanie podczas uruchamiania
* [ ] Zachowanie po utracie zasilania
* [ ] Odporność na zakłócenia

---

# 19. Zdjęcia projektu

Zdjęcia będą dodawane podczas kolejnych etapów.

Planowana struktura:

```text
images/
│
├── poczatek/
├── prototyp/
├── pcb/
├── pomiary/
├── debugowanie/
└── final/
```

Przykład dodania zdjęcia:

```markdown
![Pierwszy prototyp](images/poczatek/pierwszy-prototyp.jpg)
```

---

# 20. Dokumentacja projektu

| Plik             | Zawartość                 |
| ---------------- | ------------------------- |
| `README.md`      | Główny opis projektu      |
| `PROJECT_LOG.md` | Dziennik rozwoju projektu |
| `docs/`          | Dokumentacja techniczna   |
| `hardware/`      | Hardware                  |
| `firmware/`      | Firmware                  |
| `images/`        | Zdjęcia                   |
| `measurements/`  | Pomiary                   |

---

# 21. Czego nauczyłem się podczas projektu

Ta sekcja będzie rozwijana wraz z projektem.

---

## Lekcja #001

**Data:** TBD

### Temat

TBD

### Czego się nauczyłem?

TBD

### Jak wpłynęło to na projekt?

TBD

---

# 22. Aktualny stan projektu

**Status:** 🟡 W trakcie realizacji

### Ukończone

* [x] Koncepcja urządzenia
* [x] Założenie systemu 3.1
* [x] Wstępna architektura
* [x] Wybór platformy ESP32 jako punktu wyjścia
* [x] Rozpoczęcie dokumentacji

### W trakcie

* [ ] Analiza wariantów ESP32
* [ ] Projekt architektury audio
* [ ] Analiza Spotify Connect
* [ ] Analiza Bluetooth Audio
* [ ] Dobór DAC / CODEC
* [ ] Dobór wzmacniacza
* [ ] Projekt zasilania

### Planowane

* [ ] Prototyp
* [ ] Firmware
* [ ] Schemat
* [ ] PCB
* [ ] Pomiary
* [ ] Testy audio
* [ ] Obudowa
* [ ] Testy końcowe
* [ ] Dokumentacja końcowa

---

# 23. Następne kroki

### Priorytet 1

Ustalenie dokładnego wariantu ESP32.

### Priorytet 2

Analiza możliwości implementacji Spotify Connect.

### Priorytet 3

Analiza Bluetooth Audio.

### Priorytet 4

Zaprojektowanie cyfrowej ścieżki audio.

### Priorytet 5

Wybór DAC / CODEC.

### Priorytet 6

Określenie sposobu realizacji kanału subwoofera i crossovera.

### Priorytet 7

Dobór wzmacniacza.

### Priorytet 8

Projekt zasilania.

---

# 24. Podsumowanie projektu

> **Sekcja zostanie uzupełniona po zakończeniu projektu.**

### Finalna architektura

TBD

### Najważniejsze komponenty

TBD

### Najważniejsze parametry

TBD

### Wyniki pomiarów

TBD

### Problemy napotkane podczas budowy

TBD

### Najważniejsze decyzje projektowe

TBD

### Koszt wykonania

TBD

### Czas realizacji

TBD

### Co zmieniłbym w kolejnej rewizji?

TBD

---

# 25. Opis do portfolio

Krótki opis projektu, który może zostać wykorzystany na stronie portfolio:

> **ESP32 3.1 Audio System**
> Projekt własnego systemu audio 3.1 opartego na platformie ESP32. Urządzenie łączy bezprzewodowe źródła audio, w tym Spotify Connect i Bluetooth, z cyfrowym przetwarzaniem sygnału oraz wielokanałowym wzmacniaczem. Projekt obejmuje analizę wymagań, projekt architektury, dobór komponentów, rozwój firmware'u, projekt hardware'u, prototypowanie, pomiary, debugowanie oraz końcową integrację.

---

# 26. Historia zmian dokumentacji

| Data       | Wersja | Zmiana                           |
| ---------- | ------ | -------------------------------- |
| 20.09.2026 | v0.1   | Utworzenie dokumentacji projektu |
