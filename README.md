# 📻 System Radio Multiroom dla Home Assistant

Kompletna instrukcja konfiguracji systemu radiowego z wyborem urządzenia wyjściowego (Multiroom) przy użyciu Browser Mod.

## ⚠️ Ważna informacja na start
Aby zarejestrować nowe urządzenie (tablet, telefon, przeglądarka) w dodatku **Browser Mod**, musisz być zalogowany na tym urządzeniu jako **ADMINISTRATOR**. W przeciwnym razie przycisk "Register" może być niewidoczny.

---

## 1️⃣ Krok 1: Pomocnik (Input Select)
Stwórz pomocnika, który będzie przechowywał listę Twoich głośników.
- **Typ:** Lista rozwijana (Dropdown)
- **Nazwa:** `Wybór Głośnika Radio`
- **ID encji:** `input_select.wybor_glosnika_radio`
- **Opcje:**
  - `Tablet`
  - `Sciana`
  - `Salon`

---

## 2️⃣ Krok 2: Skrypt (Logic)
Skrypt sterujący, który sprawdza co wybrałeś na liście i wysyła tam strumień audio.

```yaml
alias: "Radio Multiroom Play"
sequence:
  - action: media_player.play_media
    target:
      entity_id: >
        {% if is_state('input_select.wybor_glosnika_radio', 'Tablet') %}
          media_player.tablet
        {% elif is_state('input_select.wybor_glosnika_radio', 'Sciana') %}
          media_player.tablet_wall
        {% else %}
          media_player.salon
        {% endif %}
    data:
      media_content_id: "{{ m_id }}"
      media_content_type: audio/mpeg
mode: single
