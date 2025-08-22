# Übersicht: Permit Management Lösung

Kurzbeschreibung
- Verwaltung von Bau‑ und Genehmigungsprozessen in Dataverse (Permits, Inspections, Permit Types, Build Sites, Contacts).
- Enthält Model‑driven App (Office), Canvas App (Inspector), Formularskripte, Custom API + Plugins, PCF‑Control, Power Automate Flows und Azure‑Integration.

Datenmodell
- Kernentitäten: Permit, Inspection, Permit Type, Build Site, Contact.
- Visuelle Darstellung:
  - PNG (falls vorhanden): ![Datenmodell](Allfiles/Labs/L01/PermitManagement.png)
  - PDF (Original, öffnen zum Anzeigen/Exportieren): [Datenmodell (PDF)](Allfiles/Labs/L01/PermitManagement.pdf)

Hauptfunktionen
- Model‑driven App: Zentrale Verwaltung von Permits, Inspektionen, Formularen und Views.
- Canvas App (Inspector): Mobile App für Inspektoren — Liste offener Inspektionen, Details, Ergebnis/Kommentare setzen (SubmitForm / Patch).
- Formularskripte & Custom API: UI‑Logik (Sichtbarkeit, Pflichtfelder) + "Lock Permit" Befehl, der Custom API aufruft.
- Server‑seitige Plugins: Verhindert doppelte Permits bei gesperrten Einträgen; sperrt Permit, storniert Inspektionen und erstellt Notizen.
- PCF Control: Timeline‑Darstellung der Inspektionshistorie, farbcodiert nach Status.
- Power Automate: Instant‑ und geplante Flows (z. B. ClearInspectionComments, Reset Inspections).
- Azure / Custom Connector: Azure Function und OpenAPI‑Connector für externe Integrationen.

Typischer Ablauf (Beispiel)
1. Office‑User legt Build Site / Permit Type an und erstellt einen Permit in der Model‑driven App.  
2. Inspektor öffnet die Canvas App → wählt offene Inspektionen → aktualisiert Status/Kommentare → speichert.  
3. Office‑User kann Permit sperren (Lock Permit) → Custom API + Plugin führen Sperrung und Stornierung von Inspektionen durch.

Wichtige Dateien / Pfade
- Datenmodell: Allfiles/Labs/L01/PermitManagement.xml (und PermitManagement.pdf/png)
- Model‑driven App Setup: Instructions/Setup/LAB[PL-400]_Setup02_Model_Driven_App.md
- Canvas App: Instructions/Setup/LAB[PL-400]_Setup03_Canvas_App.md, Allfiles/Setup/Resources/ContosoComponents.msapp
- Formularskripte: Allfiles/Labs/L06/Resources/PermitFormFunctions.js
- Plugins: Allfiles/Labs/L08/Resources/PreOperationPermitCreate.cs, Allfiles/Labs/L08/Resources/LockPermitCancelInspections.cs
- PCF: Allfiles/Labs/L07/Resources/ControlManifest.Input.xml
- Flows & Azure: Instructions/Labs/LAB[PL-400]_Lab03_Flow.md, Allfiles/Demos/openapi.json

Kurzanleitung zum Start
1. Lösung importieren / Umgebung gemäß Instructions/Setup einrichten.  
2. Model‑driven App öffnen → Stammdaten (Build Site, Permit Type) anlegen → Permit erstellen.  
3. Canvas App (Inspector) öffnen → Inspektion durchführen und speichern.  
4. "Lock Permit" im Permit‑Formular testen und Ergebnis prüfen (Plugin‑Logs, Power Automate Runs).

Hinweis zu Bildern
- Falls nur die PDF des Datenmodells vorhanden ist, empfehle ich, die Seite als PNG zu exportieren (z. B. mit Edge/Adobe oder ImageMagick) und unter Allfiles/Labs/L01/ abzulegen, damit sie direkt in der Markdown‑Datei angezeigt