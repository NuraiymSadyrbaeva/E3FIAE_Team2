# Chatbot-Projekt – E3FIAE_Team2
## Projektstruktur
```plaintext
├─ app/                         # Haupt-Anwendung
│  ├─ __init__.py              # Flask-App wird hier erstellt
│  ├─ routes.py                # Flask-Routen 
│  ├─ static/                 
│  │  │  └─ style.css          # Design der Webseite
│  │  │  └─ script.js          # Optional: Chatfunktionen
│  │  └─ images/              
│  │     ├─ logo.svg           # Logos & Hintergründe
│  │     └─ bg.svg
│  └─ templates/
│     ├─ index.html            
│
├─ venv/                       # Virtuelle Umgebung (nicht in GitHub hochladen!)
├─ main.py                     # Startpunkt der App → `python main.py`
├─ requirements.txt            # Notwendige Python-Bibliotheken (Flask usw.)
└─ README.md                   # Dokumentation
```

## Anleitung zur Nutzung

### 1 Virtuelle Umgebung anlegen und aktivieren

#### Virtuelle Umgebung anlegen
```bash
cd project_chatbot
python -m venv venv
```
#### Virtuelle Umgebung aktivieren
Windows
```bash
venv\Scripts\activate
````
Linux/macOS
```bash
source venv/bin/activate
```
### 2 Abhängigkeiten installieren
```bash
pip install -r requirements.txt
```
oder 
```bash
pip install flask
```
## 3. Projekt starten
```bash
cd project_chatbot
source venv/bin/activate
python scripts/main.py   # Startet Flask auf http://localhost:5050
```
### projektstruktur

```project_chatbot/

```
### webseite öffnen
Browser öffnen → http://localhost:5050
