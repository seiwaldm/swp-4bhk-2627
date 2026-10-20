# seiwald-mitschrift

Das ist die README.md-Datei. MD steht für Markdown. Markdown ist eine heutzutage weit verbreitete Auszeichungssprache (_Markup Language_, [Wikipedia](https://de.wikipedia.org/wiki/Auszeichnungssprache)).

Weiter bekannte Auszeichnungssprachen sind:

- Hypertext Markup Language (HTML)
- Extensible Markup Language (XML)
- Yet Another Markup Language (YAML, YML)

## Installation von Node.js

Javascript läuft unter normalen Umständen in einer Browser-Sandbox (nur im Browser).
Seit ca. 2010 gibt es eine Laufzeitumgebung (_Runtime Environment_) für JS, damit man auch serverseitig JS programmieren und ausführen kann: [Node.js](https://nodejs.org/en).

## Installation von pnpm

Der standardmäßige _Package Manager_ für Node.js ist `npm` (_node package manager_). Eine etwas modernere und inzwischen beliebtere Variante ist [`pnpm`](https://pnpm.io/).

## Installation von strapi

Installation mit dem Skript `pnpm create strapi`. Daraufhin führt das CLI (_Command Line Interface_) durch die Installation. Falls bei der Installation sogenannte `build scripts` nicht ausgeführt werden können, schlägt die CLI die Fehlerbehandlung selbständig vor:

1. Wechsel in das Installationsverzeichnis (z.B. mit `cd my-strapi-project`)
2. Neuerlicher Versuch der Installation mit `pnpm install`. Dieser scheitert in der Regel - die Build-Skripte müssen mit `pnpm approve-builds` manuell freigegeben werden.

---

# Historische Entwicklung von WebDev

Webdevelopment hat im Laufe der letzten rund 35 Jahre einige Evolutionsstufen durchlaufen:

1. Statische Website (HTML, CSS, ggf. JavaScript) - initiale Phase des Webdevelopments, bei der Inhalte fest im HTML-Code verankert sind. Dominant in den 1990er-Jahren.

2. Dynamische Website (mit serverseitiger Programmiersprache - PHP, Python, NodeJS - und Datenbankanbindung). Dominant in den 2000er-Jahren.

3. _Single-Page Application_ (SPA) - mit JavaScript-Frameworks (z.B. React, Vue, Angular, Svelte, ...) erstellte "Webapps", die ähnliche Funktionen wie klassische Desktop-Anwendungen bzw. Handy-Apps bieten. Dominant in den 2010er-Jahren. Um Handy-Apps möglichst nahe zu kommen, wurde der _Progressive Web App_ (PWA)-Standard entwickelt. Damit können Webapps offline funktionieren, Push-Benachrichtigungen senden und auf bestimmte native Funktionen des Geräts zugreifen. Es gibt drei Voraussetzungen, die eine Webapp erfüllen muss, um als PWA zu gelten:
   1. Die Webapp muss über ein Web-App-Manifest verfügen (`manifest.json`), das grundlegende Informationen über die App enthält (Name, Icons, Start-URL, etc.).
   2. Die Webapp muss einen Service Worker implementieren, der das Caching von Ressourcen und die Offline-Funktionalität ermöglicht. Ein Service Worker ist eine JavaScript-Datei, die im Hintergrund des Browsers läuft - selbst wenn der Browser geschlossen ist.
   3. Die Webapp muss über HTTPS bereitgestellt werden, um die Sicherheit und Integrität der Anwendung zu gewährleisten.

   Frontend-Frameworks wenden folgende Architekturprinzipien an, um eine möglichst gute _User Experience_ (UX) zu erreichen:
   - **Komponenten** - Komponenten sind die wiederverwendbaren "Lego"-Bausteine einer Webapp. Sie kapseln HTML, CSS und JavaScript in einer einzigen Einheit, die unabhängig von anderen Komponenten entwickelt, getestet und gewartet werden kann.
   - **Deklarative Programmierung** - der Javascript- und Template(HTML)-Code beschreiben, wie die Benutzeroberfläche aussehen soll, anstatt die einzelnen Schritte zur Erstellung der Benutzeroberfläche zu definieren. Das Framework kümmert sich um die Umsetzung. Dabei kommt **Reaktivität** (_reactivity_) ins Spiel: Wenn sich der Zustand der Anwendung ändert, aktualisiert das Framework automatisch die Benutzeroberfläche (UI), um den neuen Zustand (_state_) widerzuspiegeln. Wenn die Aktualisierung auch in die andere Richtung funktioniert (d.h. wenn sich die Benutzeroberfläche ändert, weil der Benutzer mit ihr interagiert, und der Zustand der Anwendung entsprechend aktualisiert wird), spricht man von bidirektionaler Datenbindung (_two-way data binding_). **Logikbausteine** (Schleifen zur Darstellung von Listen und Bedingungen für das konditinale Ein- und Ausblenden von UI-Elementen) werden in den Templates (HTML) der Komponenten definiert. Die Templates werden vom Framework in die eigentliche Benutzeroberfläche übersetzt. Komponenten können auch andere Komponenten enthalten (verschachtelt werden), wodurch eine hierarchische Struktur entsteht. Die Kommunikation zwischen Komponenten erfolgt über **Props** (Eigenschaften) und **Events** (Ereignisse). Props sind Daten, die von einer übergeordneten Komponente an eine untergeordnete Komponente weitergegeben werden. Events sind Benachrichtigungen, die von einer untergeordneten Komponente an eine übergeordnete Komponente gesendet werden, um auf Benutzerinteraktionen oder andere Ereignisse zu reagieren.

## VibeCoding / AgenticEngineering mit VS-Code und GitHub Copilot

VibeCoding passiert in VS-Code in erster Linie über die neu eingeführte Agent View. Dort können alle Anpassungen der "Coding Harness" vorgenommen werden. Wir können unseren Harmess mit verschiedenen Methoden anpassen:

- MCP-Server MCP steht für _Model Context Protocoll_. Es ist ein von Anthropic entwickelter Standard. Mit Hilfe von MCP können ChatBots/LLMs (_Large Language Models_) auf zusätzliche Tools zugreifen, die sie zu Experten in einem bestimmten Themenbereich machen.

---

# Frontend-Enwicklung

## Ordnerstruktur

Die Ordnerstruktur einer typischen Frontend-Anwendung sieht in etwa so aus:

![Ordnerstruktur einer Svelte-Anwendung](image.png)

Der Ordner `.vscode` enthält Einstellungen für den VS-Code-Editor. Der Ordner `node_modules` enthält die Abhängigkeiten (_dependencies_) der Anwendung. Das sind jene Pakete, die bei der Entwicklung (_build time_) und/oder bei der Ausführung (_runtime_) der Anwendung benötigt werden. Alle Abhängigkeiten sind in der Datei `package.json`aufgelistet. Außerdem enthält die Datei `package.json` Informationen über die Anwendung selbst (Name, Version, Autor, Lizenz, etc.) und Skripte, die bestimmte Aufgaben automatisieren (z.B. Starten der Anwendung, Testen der Anwendung, Erstellen einer Produktionsversion der Anwendung). Der Ordner `public` enthält statische Dateien (z.B. Bilder, Fonts, Icons), die direkt vom Browser unter dem jeweiligen Pfad geladen werden können.

![Unterstuktur des src-Ordners](image-1.png)

Der Ordner `src`enthält den Quellcode der Anwendung. Die Dateien `app.css`, `App.svelte` und `main.ts` sind die Einstiegspunkte der Anwendung (in diesem Fall eine SPA). Sie werden vom Browser als erstes geladen, wenn die entsprechende Website aufgerufen wird. Die Datei `app.css` enthält die globalen CSS-Stile. Die Datei `App.svelte` ist die Hauptkomponente, die andere Komponenten importiert und in der Benutzeroberfläche anzeigt. Die Datei `main.ts` ist der Einstiegspunkt für das JavaScript/TypeScript. Sie initialisiert die Anwendung in der `App.svelte` und bindet sie an das HTML-Dokument (`index.html` im Root-Ordner).
