# ESP32-4848 Dashboard

ESPHome-Konfiguration für das Guition ESP32-4848S040 (480 × 480) mit LVGL,
GT911-Touchscreen und Home-Assistant-Daten.

## Einrichtung

1. Installiere ESPHome und kopiere `secrets.yaml.example` als `secrets.yaml`.
2. Trage WLAN-SSID, WLAN-Passwort und einen gültigen API-Verschlüsselungsschlüssel ein.
   `secrets.yaml` wird von Git ignoriert und enthält keine Projekt-Standardzugangsdaten.
3. Prüfe die Home-Assistant-Entity-IDs in `esp32-4848.yaml` und passe sie bei Bedarf an.
4. Prüfe und flashe die Konfiguration mit `esphome run esp32-4848.yaml`.

Die Home-Ansicht zeigt Wohnzimmer-Temperatur und Wetterstatus. Über die Navigation
erreichst du die PV-Seite, Wärmepumpen-Seite, Wettervorhersage, Zimmertemperatur
und Einstellungen. Die Wärmepumpen-Seite zeichnet die Warmwassertemperatur alle
zwei Stunden auf und zeigt zwölf Werte als 24-Stunden-Verlauf seit dem letzten
Neustart.

Die Einstellungen ändern die Displayhelligkeit und schalten Hintergrundfarben
(Dunkelgrün, Dunkelrot, Dunkelblau, Schwarz) sowie Schriftfarben (Weiß, Hellgrau,
Gelb, Hellgrün, Hellblau) durch. Die aktuelle Farbwahl wird im laufenden Gerät
verwendet, aber nicht über Neustarts hinweg gespeichert.

## Home-Assistant-Entities

Die Konfiguration verwendet folgende Entity-IDs:

- `sensor.sh5_0rt_local_total_dc_power`
- `sensor.sh5_0rt_local_battery_level`
- `sensor.lohome_domestic_hot_water_0_tank_temperature`
- `sensor.eg_wohnen_hm_eg_wohnen`
- `weather.forecast_home` (Status und Attribut `temperature`)

Der Wärmepumpen-Verlauf wird lokal im Display geführt und nicht aus der
Home-Assistant-Historie geladen.
