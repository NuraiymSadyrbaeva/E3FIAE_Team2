# CSS-Dokumentation – YourChatbot

Diese Dokumentation richtet sich an **Webshop-Betreiber**, die den Chatbot in ihren eigenen Webshop einbinden und das Aussehen per eigener CSS-Datei anpassen möchten.

---

## Inhaltsverzeichnis

1. [So funktioniert das Styling](#so-funktioniert-das-styling)
2. [HTML-Struktur des Chatbots](#html-struktur-des-chatbots)
3. [CSS-Variablen](#css-variablen)
4. [CSS-Klassen-Referenz](#css-klassen-referenz)
5. [HTML-Tags im Chatbot](#html-tags-im-chatbot)
6. [IDs (JavaScript-relevant)](#ids-javascript-relevant)

---

## So funktioniert das Styling

Beim Erstellen oder Bearbeiten eines Chatbots können Sie eine **eigene CSS-Datei hochladen**. Diese wird automatisch **nach** dem Standard-CSS (`chat.css`) geladen und überschreibt dadurch die Standard-Styles.

**Reihenfolge der Stylesheets:**

1. `chat.css` – Standard-Styles des Chatbots
2. **Ihre CSS-Datei** – wird als `<style>`-Block im `<head>` eingefügt

Da Ihre Styles zuletzt geladen werden, überschreiben sie die Standardwerte. Sie müssen lediglich die Klassen und Eigenschaften angeben, die Sie ändern möchten.

---

## HTML-Struktur des Chatbots

So ist der Chatbot im HTML aufgebaut:

```html
<body>
  <main class="shell">
    <section class="card chat">
      <!-- Chat-Fenster mit allen Nachrichten -->
      <div id="chat-window" class="chat-window">
        <!-- Bot-Nachricht -->
        <div class="bubble bot">
          <div class="bubble-body">
            <div class="bubble-text">Willkommensnachricht ...</div>
          </div>
        </div>

        <!-- Benutzer-Nachricht -->
        <div class="bubble user">
          <div class="bubble-body">
            <div class="bubble-text">Benutzernachricht ...</div>
          </div>
        </div>
      </div>

      <!-- Tipp-Indikator (wird per JS ein-/ausgeblendet) -->
      <div id="typing" class="typing hidden">
        <span></span><span></span><span></span>
      </div>

      <!-- Eingabeformular -->
      <form id="chat-form" class="chat-form">
        <textarea
          id="user-input"
          name="message"
          placeholder="Nachricht eingeben …"
        ></textarea>
        <button class="btn primary" type="submit">Senden</button>
        <button id="reset-btn" class="btn secondary" type="button">
          Reset
        </button>
      </form>
    </section>
  </main>
</body>
```

---

## CSS-Variablen

Der Chatbot verwendet die CSS-Variable `--primary` für die Akzentfarbe. Sie können diese im `:root`-Selektor überschreiben, um die Hauptfarbe des Chatbots zu ändern.

| Variable    | Standard-Wert | Beschreibung                         |
| ----------- | ------------- | ------------------------------------ |
| `--primary` | `#2f7cff`     | Hauptfarbe (Tipp-Indikator, Buttons) |

**Beispiel:**

```css
:root {
  --primary: #e91e63; /* Pink als Hauptfarbe */
}
```

---

## CSS-Klassen-Referenz

### Layout & Container

| Klasse   | Element     | Beschreibung                                                                          |
| -------- | ----------- | ------------------------------------------------------------------------------------- |
| `.shell` | `<main>`    | Äußerer Container, zentriert den Inhalt mit max. Breite und Padding.                  |
| `.card`  | `<section>` | Karten-Container mit Hintergrund, Rahmen, Rundung und Schatten.                       |
| `.chat`  | `<section>` | Zusätzliche Klasse auf der Karte – kann für Chat-spezifisches Styling genutzt werden. |

### Chat-Fenster

| Klasse         | Element | Beschreibung                                                                                            |
| -------------- | ------- | ------------------------------------------------------------------------------------------------------- |
| `.chat-window` | `<div>` | Scrollbarer Bereich, in dem alle Nachrichten angezeigt werden. Flexbox-Layout (vertikal, 12px Abstand). |

### Nachrichten-Bubbles

| Klasse         | Element | Beschreibung                                                                         |
| -------------- | ------- | ------------------------------------------------------------------------------------ |
| `.bubble`      | `<div>` | Wrapper für eine einzelne Nachricht (Bot oder User). Hat Rahmen und max. Breite 75%. |
| `.bubble.bot`  | `<div>` | Bot-Nachricht – standardmäßig linksbündig.                                           |
| `.bubble.user` | `<div>` | Benutzer-Nachricht – rechtsbündig (`align-self: flex-end`).                          |
| `.bubble-body` | `<div>` | Innerer Container der Nachricht mit Padding (10px 14px).                             |
| `.bubble-text` | `<div>` | Enthält den eigentlichen Nachrichtentext.                                            |

### Eingabebereich

| Klasse                | Element      | Beschreibung                                                            |
| --------------------- | ------------ | ----------------------------------------------------------------------- |
| `.chat-form`          | `<form>`     | Formular-Container unter dem Chat-Fenster (margin-top: 12px).           |
| `.chat-form textarea` | `<textarea>` | Eingabefeld, nimmt volle Breite ein (width: 100%).                      |
| `.btn`                | `<button>`   | Basis-Button-Klasse mit Rahmen und Rundung.                             |
| `.btn.primary`        | `<button>`   | Primärer Button (Senden) – Hintergrundfarbe `--primary`, weiße Schrift. |
| `.btn.secondary`      | `<button>`   | Sekundärer Button (Reset) – transparenter Hintergrund.                  |

### Tipp-Indikator

| Klasse           | Element  | Beschreibung                                                                          |
| ---------------- | -------- | ------------------------------------------------------------------------------------- |
| `.typing`        | `<div>`  | Container für die animierten Punkte, die angezeigt werden, während der Bot antwortet. |
| `.typing.hidden` | `<div>`  | Versteckt den Tipp-Indikator (`display: none`).                                       |
| `.typing span`   | `<span>` | Einzelner animierter Punkt (3 Stück). Rund, 8×8px, mit Bounce-Animation.              |

---

## HTML-Tags im Chatbot

Übersicht der verwendeten HTML-Tags, die Sie per CSS ansprechen können:

| Tag          | Verwendung                                | Beispiel-Selektor             |
| ------------ | ----------------------------------------- | ----------------------------- |
| `<body>`     | Seiten-Hintergrund und Grundschrift       | `body { background: #fff; }`  |
| `<main>`     | Haupt-Container (hat Klasse `.shell`)     | `main.shell { ... }`          |
| `<section>`  | Chat-Karte (hat Klassen `.card.chat`)     | `section.card.chat { ... }`   |
| `<div>`      | Chat-Fenster, Bubbles, Tipp-Indikator     | `.chat-window { ... }`        |
| `<form>`     | Eingabeformular (hat Klasse `.chat-form`) | `.chat-form { ... }`          |
| `<textarea>` | Texteingabefeld                           | `.chat-form textarea { ... }` |
| `<button>`   | Senden- und Reset-Button                  | `.btn.primary { ... }`        |
| `<span>`     | Animierte Punkte im Tipp-Indikator        | `.typing span { ... }`        |

---

## IDs (JavaScript-relevant)

Diese IDs werden vom JavaScript verwendet. Sie können sie für CSS-Styling nutzen, aber **nicht umbenennen oder entfernen**, da sonst die Chat-Funktionalität nicht mehr funktioniert.

| ID             | Element      | Beschreibung            |
| -------------- | ------------ | ----------------------- |
| `#chat-window` | `<div>`      | Chat-Nachrichtenfenster |
| `#chat-form`   | `<form>`     | Eingabeformular         |
| `#user-input`  | `<textarea>` | Texteingabefeld         |
| `#typing`      | `<div>`      | Tipp-Indikator          |
| `#reset-btn`   | `<button>`   | Reset-Button            |

> **Wichtig:** Diese IDs dürfen nicht verändert werden, sie werden vom JavaScript benötigt.

---

## Hinweise

- Ihre CSS-Datei wird **nach** dem Standard-CSS geladen und überschreibt es automatisch.
- Sie müssen **nicht** alle Klassen überschreiben – nur die, die Sie ändern möchten.
- Verwenden Sie `!important` nur wenn nötig, da Ihre Styles bereits Vorrang haben.
- Die **IDs** (`#chat-window`, `#chat-form`, `#user-input`, `#typing`, `#reset-btn`) sind für die JavaScript-Funktionalität reserviert und dürfen nicht umbenannt werden.
- Die CSS-Datei kann im Chatbot-Manager unter **"Bearbeiten" → "CSS-Datei hochladen"** hochgeladen werden.
