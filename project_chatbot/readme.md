# Chatbot-Projekt – E3FIAE_Team2
## Projektstruktur
```plaintext
project_chatbot/
├─ scripts/
│  └─ main.py           
├─ venv/                
├─ requirements.txt     # Projekt-Abhängigkeiten
├─ .gitignore           # Ignorierte Dateien
└─ readme.md            # Dokumentation
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