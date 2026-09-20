# Project Log — ESP32 3.1 Audio System

> Dziennik projektowy — decyzje, eksperymenty, pomiary, problemy i kolejne wersje projektu.

---

# 1. Project Overview

## Nazwa projektu

**ESP32 3.1 Audio System**

## Cel projektu

Zaprojektowanie i wykonanie własnego systemu audio 3.1 opartego o platformę ESP32.

Urządzenie ma umożliwiać odtwarzanie muzyki poprzez:

* Spotify Connect
* Bluetooth Audio

System będzie posiadał trzy kanały audio:

* Left (L)
* Right (R)
* Subwoofer (SUB)

Projekt obejmuje przygotowanie elektroniki, PCB, firmware, toru audio, wzmacniacza oraz zasilania.

---

# 2. Current Status

**Status:** 🟡 W toku

**Current revision:** Concept / Rev. 0.1

**Last update:** [DD.MM.RRRR]

---

# 3. Initial Requirements

> Sekcja będzie uzupełniana w trakcie definiowania projektu.

| Parametr             | Wartość     | Status |
| -------------------- | ----------- | ------ |
| Mikrokontroler       | ESP32 — TBD | 🟡     |
| Spotify Connect      | Tak         | 🟢     |
| Bluetooth Audio      | Tak         | 🟢     |
| System audio         | 3.1         | 🟢     |
| DAC / CODEC          | TBD         | 🟡     |
| DSP                  | TBD         | 🟡     |
| Wzmacniacz           | TBD         | 🟡     |
| Moc wyjściowa        | TBD         | 🟡     |
| Impedancja głośników | TBD         | 🟡     |
| Zasilanie            | TBD         | 🟡     |
| Obudowa              | TBD         | 🟡     |

---

# 4. System Architecture

## Initial concept

```text
                    ┌─────────────────────┐
                    │        ESP32        │
                    │                     │
                    │     Wi-Fi           │
                    │ Spotify Connect     │
                    │ Bluetooth Audio     │
                    └──────────┬──────────┘
                               │
                               │ Digital Audio
                               ▼
                    ┌─────────────────────┐
                    │    Audio Section    │
                    │                     │
                    │   CODEC / DAC / DSP │
                    └──────────┬──────────┘
                               │
                     ┌─────────┴─────────┐
                     │                   │
                     ▼                   ▼
                  L / R                 SUB
                     │                   │
                     ▼                   ▼
              ┌─────────────┐     ┌─────────────┐
              │ Amplifier   │     │ Amplifier   │
              │ L / R       │     │ SUB         │
              └──────┬──────┘     └──────┬──────┘
                     │                   │
                     ▼                   ▼
                  Speakers            Subwoofer
```

> **UWAGA:** Powyższy diagram przedstawia jedynie początkową koncepcję. Architektura może zostać zmieniona w trakcie projektu.

---

# 5. Project Decisions

Ta sekcja będzie zawierała najważniejsze decyzje projektowe.

Każdą istotną decyzję zapisujemy według schematu:

```text
Problem
↓
Wymagania
↓
Rozważane rozwiązania
↓
Test / analiza
↓
Decyzja
↓
Uzasadnienie
```

---

## Decision #001 — Platforma MCU

**Status:** 🟡 Do analizy

### Problem

Jaki mikrokontroler powinien odpowiadać za obsługę sieci, Spotify Connect oraz Bluetooth Audio?

### Wymagania

* Wi-Fi
* Bluetooth
* odpowiednia wydajność CPU
* wystarczająca ilość RAM
* odpowiednie interfejsy audio
* możliwość wykorzystania I2S
* dostępne biblioteki / SDK
* możliwość dalszego rozwoju firmware

### Rozważane rozwiązania

* ESP32
* ESP32-S3
* [inne]

### Analiza

[Tutaj wpiszemy informacje zebrane podczas analizy.]

### Decyzja

[TBD]

### Uzasadnienie

[TBD]

---

# 6. Audio Architecture

**Status:** 🟡 W toku

Na tym etapie należy określić:

* sposób odbioru audio,
* format danych audio,
* częstotliwość próbkowania,
* rozdzielczość,
* DAC / CODEC,
* DSP,
* sposób utworzenia kanału SUB,
* regulację głośności,
* filtry,
* wzmacniacz.

### Aktualna koncepcja

```text
Spotify Connect
       │
       ▼
     ESP32
       │
       ▼
   Digital Audio
       │
       ▼
    DAC / DSP
       │
       ├──────── L
       │
       ├──────── R
       │
       └──────── SUB
```

> Architektura zostanie doprecyzowana po analizie wymagań audio.

---

# 7. Hardware

## MCU

**Component:** TBD

**Part number:** TBD

**Reason for selection:** TBD

---

## DAC / CODEC

**Component:** TBD

**Part number:** TBD

**Interface:** TBD

**Reason for selection:** TBD

---

## DSP

**Component:** TBD

**Reason for selection:** TBD

---

## Amplifier

**Component:** TBD

**Part number:** TBD

**Configuration:** 3.1

**Target output power:** TBD

**Speaker impedance:** TBD

---

# 8. Power Supply

**Status:** 🟡 Not designed

### Requirements

* [ ] napięcie wejściowe
* [ ] moc wzmacniacza
* [ ] zasilanie ESP32
* [ ] zasilanie sekcji audio
* [ ] filtracja
* [ ] zabezpieczenie
* [ ] chłodzenie

### Initial concept

```text
                 POWER INPUT
                      │
          ┌───────────┴───────────┐
          │                       │
          ▼                       ▼
     POWER AMP               DC/DC / LDO
          │                       │
          ▼                       ▼
       3.1 AMP                 5V / 3.3V
                                  │
                                  ▼
                              ESP32
```

---

# 9. PCB

**Status:** ⬜ Not started

### Planned PCB sections

* ESP32
* power supply
* digital audio
* DAC / CODEC
* DSP
* amplifier
* connectors
* protection

### PCB considerations

* [ ] separation of analog and digital sections
* [ ] ground strategy
* [ ] power distribution
* [ ] audio signal routing
* [ ] decoupling
* [ ] thermal management
* [ ] EMI / EMC considerations

---

# 10. Firmware

**Status:** ⬜ Not started

### Planned functionality

* [ ] Wi-Fi configuration
* [ ] Spotify Connect
* [ ] Bluetooth Audio
* [ ] audio streaming
* [ ] volume control
* [ ] source selection
* [ ] DSP control
* [ ] system status
* [ ] error handling
* [ ] OTA updates

---

# 11. Experiments

Tutaj zapisujemy eksperymenty wykonane podczas projektu.

---

## Experiment #001

**Date:** [DD.MM.RRRR]

### Objective

[Co chciałem sprawdzić?]

### Setup

[Jak wyglądało stanowisko testowe?]

### Equipment

* [Oscilloscope]
* [Multimeter]
* [Logic Analyzer]
* [Power Supply]
* [inne]

### Procedure

[Jak przeprowadziłem test?]

### Result

[Wynik.]

### Conclusion

[Wniosek.]

---

# 12. Measurements

Wszystkie istotne pomiary zapisujemy tutaj.

| Date | Parameter | Expected | Measured | Equipment | Result |
| ---- | --------- | -------: | -------: | --------- | ------ |
| —    | —         |        — |        — | —         | —      |

---

# 13. Problems & Debugging

> Problemy są częścią projektu i nie powinny być usuwane z dokumentacji.

---

## Problem #001

**Date:** [DD.MM.RRRR]

### Symptom

[Co nie działało?]

### Conditions

[W jakich warunkach występował problem?]

### Hypothesis

[Co mogło być przyczyną?]

### Test

[Jak sprawdziłem hipotezę?]

### Measurement

[Co zmierzyłem?]

### Result

[Wynik.]

### Root Cause

[Ostateczna przyczyna.]

### Solution

[Co zmieniłem?]

### Verification

[Jak sprawdziłem, że problem został rozwiązany?]

---

# 14. Design Changes

## Revision A

**Date:** [DD.MM.RRRR]

### Changes

* Initial design

---

## Revision B

**Date:** [DD.MM.RRRR]

### Changes

* [zmiana]
* [zmiana]

### Reason

[Dlaczego wprowadzono zmiany?]

---

# 15. Photos

Zdjęcia dokumentujące rozwój projektu.

### Project Start

![Project Start](images/project-start.jpg)

### Prototype

![Prototype](images/prototype.jpg)

### PCB

![PCB](images/pcb.jpg)

### Measurements

![Measurements](images/measurements.jpg)

### Final Device

![Final Device](images/final.jpg)

---

# 16. Project Milestones

* [ ] Project concept
* [ ] Requirements
* [ ] System architecture
* [ ] Component selection
* [ ] Schematic
* [ ] PCB
* [ ] PCB manufacturing
* [ ] First prototype
* [ ] Firmware
* [ ] First bring-up
* [ ] Audio testing
* [ ] Power testing
* [ ] Thermal testing
* [ ] Debugging
* [ ] Rev. B
* [ ] Final prototype
* [ ] Final measurements
* [ ] Documentation

---

# 17. Lessons Learned

## What worked?

[TBD]

## What didn't work?

[TBD]

## What would I change?

[TBD]

## What did I learn?

[TBD]

---

# 18. Future Improvements

* [ ] [Improvement]
* [ ] [Improvement]
* [ ] [Improvement]

---

# 19. Project Notes

Tutaj można dodawać krótkie notatki, pomysły i rzeczy do sprawdzenia.

### TODO

* [ ] sprawdzić możliwości ESP32
* [ ] przeanalizować Spotify Connect
* [ ] przeanalizować Bluetooth Audio
* [ ] określić wymagania audio
* [ ] określić moc wzmacniacza
* [ ] wybrać DAC / CODEC
* [ ] zaprojektować architekturę zasilania
* [ ] zaplanować PCB

---

# 20. Changelog

## [0.1] — Project Start

* Utworzono projekt
* Zdefiniowano wstępną koncepcję systemu
* Określono Spotify Connect i Bluetooth jako źródła audio
* Określono konfigurację 3.1
* Rozpoczęto analizę platformy sprzętowej
