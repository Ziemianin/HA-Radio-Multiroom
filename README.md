# 📻 Home Assistant Radio Multiroom Package

Kompletny system radiowy dla Home Assistant z wyborem głośnika (Multiroom). 

## ⚙️ Wymagania wstępne
1. **Radio Browser** – Upewnij się, że masz zainstalowaną integrację *Radio Browser* (standardowa w HA).
2. **Browser Mod** – Wymagany do odtwarzania dźwięku na tabletach/przeglądarkach (instalacja przez HACS).
3. **Uprawnienia** – Rejestracja nowego urządzenia w Browser Mod musi być wykonana przez **Administratora**.

---

## 🚀 Szybka Instalacja

### 1. Skopiuj konfigurację (Logika)
Skopiuj plik `radio_multiroom.yaml` do folderu `packages/` w Twoim Home Assistant. Stworzy to automatycznie:
- Pomocnika (listę wyboru głośników)
- Skrypt (logikę przekierowania dźwięku)

### 2. Skopiuj interfejs (Karta)
Wklej zawartość `dashboard_card.yaml` do nowej karty typu **Ręczny (Manual)** na swoim dashboardzie.

---

## 🎵 Jak dodać własne stacje radiowe?

System korzysta z integracji **Radio Browser**. Aby dodać własną stację lub zmienić istniejące, wykonaj te kroki:

1. Wejdź w HA w sekcję **Media** -> **Radio Browser**.
2. Znajdź swoją ulubioną stację.
3. Kliknij trzy kropki przy stacji i wybierz **Dodaj do ulubionych** lub po prostu ją uruchom.
4. Aby pobrać dokładną ścieżkę (ID) stacji do kodu:
   - Otwórz **Narzędzia deweloperskie** -> **Stany**.
   - Znajdź odtwarzacz, na którym aktualnie gra radio (np. `media_player.tablet`).
   - Skopiuj wartość atrybutu `media_content_id`. Będzie to wyglądać mniej więcej tak: 
     `media-source://radio_browser/47c5dd82-470a-11e9-aa55-52543be04c81`
5. Wklej ten link w kodzie karty (Dashboard) w sekcji `m_id:`.

---

## 🛠 Rozwiązywanie problemów
- **Brak przycisku Register:** Zaloguj się na urządzeniu (tablecie) jako administrator.
- **Radio nie gra:** Sprawdź w "Narzędziach deweloperskich", czy nazwy encji `media_player.tablet`, `media_player.tablet_wall` oraz `media_player.salon` są identyczne w Twoim systemie.
