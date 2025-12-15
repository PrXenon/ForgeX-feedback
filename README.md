1. Produktübersicht
ForgeX ist eine spezialisierte Windows-Desktop-Anwendung zur automatisierten, reproduzierbaren und konfigurierbaren Konvertierung von Autodesk-Inventor-Konstruktionsdaten.
Der Fokus der Software liegt auf der Batch-Verarbeitung technischer CAD-Dateien für nachgelagerte Prozesse wie Fertigung, Laserschneiden, Wasserstrahlschneiden, externe Datenweitergabe oder Archivierung.
Im Gegensatz zu manuellen Exportvorgängen direkt aus Autodesk Inventor heraus verfolgt ForgeX den Ansatz, wiederkehrende Konvertierungsaufgaben vollständig zu automatisieren, konsistent auszuführen und von der Benutzeroberfläche von Inventor zu entkoppeln.
________________________________________
Zielsetzung von ForgeX
Die zentrale Zielsetzung von ForgeX ist es, Zeitaufwand, Fehlerquellen und Inkonsistenzen im Exportprozess von Inventor-Daten drastisch zu reduzieren.
Typische Probleme klassischer Workflows sind:
•	manuelles Öffnen einzelner Dateien
•	unterschiedliche Export-Einstellungen je Anwender
•	inkonsistente Linientypen, Skalierungen oder Layer
•	hoher Zeitaufwand bei großen Datenmengen
•	fehlende Reproduzierbarkeit im Batch-Betrieb
ForgeX löst diese Probleme durch:
•	vollautomatische Stapelverarbeitung
•	zentrale, versionierbare Exportkonfiguration
•	deterministisches Verhalten (gleiche Eingabe → gleiches Ergebnis)
•	sauberen, kontrollierten Zugriff auf die Inventor-API
________________________________________
Funktionsprinzip auf hoher Ebene
ForgeX arbeitet als externe Steuerinstanz für Autodesk Inventor.
Die Anwendung startet bzw. nutzt eine Inventor-Instanz im Hintergrund und übernimmt vollständig die Kontrolle über:
1.	Öffnen von Inventor-Dokumenten
2.	Analyse des Dokumenttyps (IPT, IAM, IDW)
3.	Ableitung der notwendigen Exportpfade
4.	Durchführung der konfigurierten Exporte
5.	Sauberes Schließen aller Dokumente
6.	Zusammenfassung der Verarbeitungsergebnisse
Der Anwender interagiert ausschließlich mit ForgeX – Inventor selbst bleibt im Hintergrund und wird nicht manuell bedient.
________________________________________
Typische Einsatzszenarien
ForgeX ist insbesondere für folgende Anwendungsfälle konzipiert:
•	Fertigungsbetriebe
Automatisierte Erstellung von DXF-Dateien aus Blech-Flachmustern für CNC-Maschinen
•	Konstruktionsabteilungen
Einheitlicher Export von STEP-Dateien für Kunden, Lieferanten oder externe Partner
•	Projektbasierte Arbeit
Stapelverarbeitung kompletter Projektordner mit hunderten Dateien
•	Standardisierung
Sicherstellung identischer Exportparameter unabhängig vom ausführenden Mitarbeiter
•	Integration in Prozesse
Nutzung als vorgelagerter Schritt in CAM-, ERP- oder PDM-Workflows
________________________________________
Abgrenzung zu ähnlichen Lösungen
ForgeX ist kein Plugin, kein Makro und keine Erweiterung innerhalb von Inventor.
Stattdessen ist es:
•	eine eigenständige Desktop-Anwendung
•	mit klarer Trennung zwischen UI, Logik und Inventor-Zugriff
•	ohne Abhängigkeit von Benutzeraktionen in Inventor
Diese Architektur ermöglicht:
•	bessere Wartbarkeit
•	stabileren Batch-Betrieb
•	einfachere Erweiterbarkeit
•	klare Fehlerbehandlung
________________________________________
Zielgruppen
ForgeX richtet sich an mehrere Zielgruppen gleichzeitig:
Endanwender
•	Konstrukteure
•	Technische Zeichner
•	Fertigungsplaner
Technische Administratoren
•	Verantwortliche für CAD-Standards
•	Prozessverantwortliche
Die Anwendung ist so ausgelegt, dass Endanwender sie ohne Programmierkenntnisse nutzen können.
________________________________________
Zusammenfassung
ForgeX ist eine professionelle Automatisierungslösung für den CAD-Export aus Autodesk Inventor.
Die Software stellt sicher, dass große Mengen an Konstruktionsdaten schnell, zuverlässig, einheitlich und reproduzierbar in externe Austauschformate überführt werden können.
Damit bildet ForgeX eine stabile Brücke zwischen:
•	Konstruktion
•	Fertigung
•	Datenweitergabe
•	und langfristiger Datenhaltung
 
2. Unterstützte Dateitypen & Exportformate
Dieses Kapitel beschreibt vollständig und eindeutig,
•	welche Eingabedateien ForgeX verarbeitet
•	welche Exportformate daraus erzeugt werden können
•	unter welchen Voraussetzungen die Konvertierung erfolgt
•	und wie der jeweilige Export technisch umgesetzt wird
Ziel ist, dass sowohl Anwender als auch Entwickler exakt verstehen, was möglich ist – und was bewusst nicht.
________________________________________
2.1 Unterstützte Eingabeformate (Quellformate)
ForgeX verarbeitet ausschließlich native Autodesk-Inventor-Dateiformate.
Andere CAD-Formate (z. B. SolidWorks, STEP als Quelle, DWG) werden nicht direkt unterstützt.
2.1.1 IPT – Inventor Part (Einzelteil)
IPT-Dateien stellen einzelne Bauteile dar und bilden die häufigste Eingabequelle für ForgeX.
Unterstützt werden:
•	klassische Einzelteile
•	Blechbauteile (Sheet Metal Parts)
•	parametrische Bauteile
•	abgeleitete Teile
ForgeX erkennt automatisch:
•	ob es sich um ein Blechbauteil handelt
•	ob ein Flachmuster vorhanden ist oder erzeugt werden kann
•	welche Exportpfade sinnvoll sind
________________________________________
2.1.2 IAM – Inventor Assembly (Baugruppe)
IAM-Dateien repräsentieren Baugruppen, bestehend aus mehreren IPT-Dateien.
ForgeX kann IAM-Dateien auf zwei Arten verarbeiten:
1.	Direkter Export der Baugruppe
o	z. B. als STEP-Gesamtmodell
2.	Auflösung der Baugruppe
o	Iteration über enthaltene Einzelteile
o	selektiver Export geeigneter Komponenten (z. B. nur Blechteile)
Die konkrete Strategie ist konfigurations- bzw. implementationsabhängig und kann projektspezifisch erweitert werden.
________________________________________
2.1.3 IDW – Inventor Drawing (Zeichnung)
IDW-Dateien sind technische Zeichnungen auf Basis von IPT- oder IAM-Modellen.
ForgeX unterstützt:
•	das Öffnen von IDW-Dateien
•	den Export zeichnungsbasierter Geometrie
•	die Nutzung von Zeichnungseinstellungen für 2D-Exporte
IDW-Dateien werden nicht geometrisch neu interpretiert, sondern immer zeichnungsgetreu exportiert.
________________________________________
2.2 Unterstützte Exportformate (Zielformate)
ForgeX erzeugt aus den oben genannten Eingabeformaten unterschiedliche Zielformate, abhängig vom Dokumenttyp und dessen Eigenschaften.
________________________________________
2.2.1 DXF – Drawing Exchange Format
Quelle → DXF
Eingabe	DXF-Export
IPT (Blech)	Flachmuster
IPT (nicht Blech)	optional / projektspezifisch
IAM	indirekt (über enthaltene IPTs)
IDW	Zeichnungsansichten
________________________________________
Technische Umsetzung
Der DXF-Export erfolgt über:
•	Inventor DataIO
•	eine dynamisch erzeugte INI-Konfigurationsdatei
Diese INI-Datei steuert unter anderem:
•	Linientypen
•	Layer-Zuordnung
•	Skalierung
•	Mapping-Strategien
•	AutoCAD-Zielversion
Der Export erfolgt deterministisch:
Gleiche Eingabedatei + gleiche INI → identisches DXF-Ergebnis
________________________________________
Besonderheiten beim Blech-Export
Bei IPT-Blechbauteilen:
•	wird das Flachmuster verwendet
•	optional automatisch erzeugt, falls nicht vorhanden
•	Fertigungsrelevante Konturen stehen im Fokus
Typische Einsatzfälle:
•	Laserschneiden
•	Stanzen
•	Wasserstrahlschneiden
________________________________________
2.2.2 STEP – ISO 10303
Quelle → STEP
Eingabe	STEP-Export
IPT	Einzelteil als 3D-Modell
IAM	Baugruppe als 3D-Modell
IDW	❌ nicht unterstützt
________________________________________
Technische Umsetzung
Der STEP-Export erfolgt über:
•	die native Inventor-Exportfunktion
•	mit definierter Zielversion (z. B. AP203 / AP214)
Exportmerkmale:
•	vollständige 3D-Geometrie
•	keine Zeichnungsinformationen
•	herstellerneutraler Datenaustausch
ForgeX stellt sicher, dass:
•	Zieldateien nicht schreibgeschützt sind
•	bestehende Dateien korrekt überschrieben werden können
•	alle Dokumente sauber geschlossen werden
________________________________________
2.3 Kombinierte Konvertierungsflüsse
ForgeX ist in der Lage, mehrere Exporte pro Quelldatei auszuführen.
Beispiele:
•	IPT (Blech) → DXF + STEP
•	IAM → STEP (Gesamtmodell) + DXF (Teile)
•	IDW → DXF
Die Ausführungsreihenfolge ist kontrolliert und reproduzierbar.
________________________________________
2.4 Nicht unterstützte Konvertierungen (bewusste Abgrenzung)
ForgeX unterstützt nicht:
•	STEP → DXF
•	DWG → DXF
•	PDF → DXF
•	Fremd-CAD-Formate als Eingabe
•	Geometrie-Rekonstruktion aus Zeichnungen
Diese Abgrenzung ist bewusst gewählt, um:
•	Qualität
•	Stabilität
•	Vorhersagbarkeit
zu gewährleisten.
________________________________________
2.5 Erweiterbarkeit
Die Architektur von ForgeX ist so ausgelegt, dass folgende Erweiterungen möglich sind:
•	zusätzliche Exportformate (z. B. PDF, DWG)
•	neue Exportstrategien pro Dokumenttyp
•	projektspezifische Filter (z. B. nur bestimmte Bauteile)
•	kundenspezifische Exportprofile
Diese Erweiterungen erfolgen auf Code- und Konfigurationsebene, ohne die Grundarchitektur zu verändern.
________________________________________
Zusammenfassung
ForgeX unterstützt eine klar definierte, professionelle Konvertierungskette:
Inventor-Originaldaten → standardisierte Austauschformate
Durch die Beschränkung auf native Inventor-Quellen und kontrollierte Exportmechanismen wird eine hohe Qualität, Stabilität und Reproduzierbarkeit erreicht.
 
3. Anwenderhandbuch
Dieses Kapitel beschreibt die Bedienung von ForgeX aus Sicht des Anwenders.
Es richtet sich an Konstrukteure, technische Zeichner und Fertigungsmitarbeiter, die mit ForgeX arbeiten, ohne den internen Code kennen zu müssen.
Ziel ist, dass ein neuer Anwender die Software allein anhand dieses Kapitels sicher bedienen kann.
________________________________________
3.1 Grundprinzip der Bedienung
ForgeX folgt einem klar strukturierten, schrittweisen Bedienkonzept:
1.	Auswahl der Eingabedaten
2.	Festlegung des Ausgabepfades
3.	Auswahl der gewünschten Exportformate
4.	Start der Batch-Konvertierung
5.	Auswertung der Ergebnisse
Alle Aktionen erfolgen über die Benutzeroberfläche von ForgeX.
Autodesk Inventor läuft dabei im Hintergrund und muss nicht manuell bedient werden.
________________________________________
3.2 Start der Anwendung
Nach dem Start von ForgeX öffnet sich das Hauptfenster der Anwendung.
Dieses stellt die zentrale Steuerzentrale für alle Konvertierungsvorgänge dar.
Typische Bestandteile des Hauptfensters:
•	Bereich zur Auswahl des Eingabeverzeichnisses
•	Bereich zur Festlegung des Ausgabeverzeichnisses
•	Optionen für Exportformate
•	Status- und Fortschrittsanzeige
•	Steuerbuttons (Start, Abbrechen (ab v1.2.0), Einstellungen)
________________________________________
3.3 Auswahl der Eingabedaten
3.3.1 Quellverzeichnis
Der Anwender wählt ein Quellverzeichnis, das die zu verarbeitenden Inventor-Dateien enthält.
Eigenschaften:
•	Es können ganze Ordnerstrukturen gewählt werden
•	Unterordner werden automatisch mit einbezogen
•	Unterstützte Dateitypen werden automatisch erkannt
ForgeX verarbeitet nur:
•	IPT
•	IAM
•	IDW
Alle anderen Dateien im Ordner werden ignoriert.
________________________________________
3.3.2 Verhalten bei großen Datenmengen
ForgeX ist für die Verarbeitung großer Dateimengen ausgelegt.
Der Anwender muss:
•	keine Dateien einzeln auswählen
•	keine Reihenfolge festlegen
•	keine manuellen Öffnungs- oder Speicheraktionen durchführen
Die Verarbeitung erfolgt automatisch und sequenziell.
________________________________________
3.4 Festlegung des Ausgabepfades
3.4.1 Manueller Ausgabepfad
Der Ausgabepfad kann frei vom Anwender festgelegt werden.
Typische Beispiele:
•	C:\Files\
•	D:\Projekte\Export\
•	Netzlaufwerke (z. B. \\Server\Freigabe\DXF)
Der gewählte Ausgabepfad gilt:
•	für alle im aktuellen Lauf erzeugten Dateien
•	unabhängig vom ursprünglichen Speicherort der Quelldateien
________________________________________
3.4.2 Ordnerstruktur im Zielverzeichnis
ForgeX kann:
•	eine flache Zielstruktur verwenden
•	oder eine strukturierte Ablage (z. B. nach Dateityp oder Projekt)
Die konkrete Ablagestrategie ist:
•	standardisiert vorbelegt
•	bei Bedarf konfigurierbar
Der Anwender muss sich nicht um das manuelle Anlegen von Unterordnern kümmern.
________________________________________
3.5 Auswahl der Exportformate
ForgeX erlaubt die gezielte Auswahl, welche Exportformate erzeugt werden sollen.
Mögliche Optionen:
•	DXF aktivieren / deaktivieren
•	STEP aktivieren / deaktivieren
Die Auswahl gilt:
•	für alle Dateien des aktuellen Batch-Laufs
•	abhängig vom jeweiligen Dateityp
Nicht jede Datei erzeugt automatisch jedes Format.
ForgeX entscheidet intelligent, welche Exporte sinnvoll und zulässig sind.
________________________________________
3.6 Start der Batch-Konvertierung
3.6.1 Startvorgang
Mit dem Start der Konvertierung:
•	wird Inventor im Hintergrund verwendet
•	werden Dateien einzeln geöffnet
•	werden Exporte durchgeführt
•	werden Dateien wieder geschlossen
Der Anwender kann währenddessen:
•	den Fortschritt beobachten
•	die Anwendung im Vordergrund belassen
•	keine weiteren Aktionen starten
________________________________________
3.6.2 Fortschrittsanzeige
ForgeX zeigt:
•	den aktuellen Bearbeitungsstatus
•	die Anzahl der verarbeiteten Dateien
•	optionale Statusmeldungen
So behält der Anwender jederzeit den Überblick über den laufenden Prozess.
________________________________________
3.7 Abschluss & Ergebnisübersicht
Nach Abschluss der Batch-Konvertierung zeigt ForgeX:
•	eine Zusammenfassung der verarbeiteten Dateien
•	die Anzahl erfolgreicher Exporte
•	optional Hinweise auf übersprungene oder fehlerhafte Dateien
Der Anwender kann anschließend:
•	die erzeugten Dateien im Ausgabeverzeichnis weiterverwenden
•	einen neuen Batch-Lauf starten
•	die Anwendung schließen
________________________________________
3.8 Fehlerbehandlung aus Anwendersicht
ForgeX ist darauf ausgelegt, robust mit Fehlern umzugehen.
Typische Szenarien:
•	nicht unterstützte Dateien
•	unvollständige Modelle
•	fehlende Flachmuster
•	schreibgeschützte Zieldateien
In solchen Fällen:
•	wird die betroffene Datei übersprungen oder behandelt
•	der Batch-Lauf wird nicht vollständig abgebrochen
•	der Anwender erhält eine zusammenfassende Rückmeldung
________________________________________
3.9 Wiederholbarkeit & Standardisierung
Ein zentraler Vorteil von ForgeX ist die Wiederholbarkeit von Exportvorgängen.
Bei gleicher:
•	Eingabedaten
•	Konfiguration
•	Exportauswahl
entstehen:
•	identische Ergebnisse
Dies ist besonders wichtig für:
•	Serienfertigung
•	Revisionssicherheit
•	standardisierte Unternehmensprozesse
________________________________________
Zusammenfassung
Das Anwenderhandbuch zeigt, dass ForgeX:
•	einfach zu bedienen ist
•	komplexe Prozesse abstrahiert
•	manuelle Fehler vermeidet
•	für große Datenmengen geeignet ist
Der Anwender konzentriert sich ausschließlich auf:
Was soll konvertiert werden und wohin
ForgeX erledigt den Rest.
 
4. Systemarchitektur & interner Ablauf
Dieses Kapitel beschreibt die technische Architektur von ForgeX, den internen Ablauf der Verarbeitung sowie die grundlegenden Designentscheidungen, die der Anwendung zugrunde liegen.
Ziel ist es, ein vollständiges Verständnis darüber zu vermitteln:
•	wie ForgeX intern aufgebaut ist
•	wie die einzelnen Komponenten zusammenspielen
•	und warum bestimmte architektonische Entscheidungen bewusst getroffen wurden
________________________________________
4.1 Architektur-Überblick
ForgeX ist als klassische Desktop-Anwendung mit klarer Schichtung aufgebaut.
Die Architektur folgt dem Prinzip der Trennung von Verantwortlichkeiten (Separation of Concerns).
Auf hoher Ebene besteht ForgeX aus folgenden Hauptkomponenten:
1.	Benutzeroberfläche (UI-Schicht)
2.	Anwendungs- und Konvertierungslogik
3.	Inventor-Integrationsschicht
4.	Datei- und Konfigurationsinfrastruktur
Jede Schicht hat eine klar definierte Aufgabe und kommuniziert über wohldefinierte Schnittstellen.
________________________________________
4.2 Benutzeroberfläche (UI-Schicht)
Die UI-Schicht ist verantwortlich für:
•	Darstellung der Anwendung
•	Entgegennahme von Benutzereingaben
•	Anzeige von Status und Fortschritt
•	Weitergabe von Befehlen an die Logikschicht
Eigenschaften:
•	keine direkte Inventor-Logik
•	keine Dateioperationen
•	keine Exportlogik
Die UI fungiert ausschließlich als Steuer- und Anzeigeebene.
________________________________________
4.3 Anwendungs- & Konvertierungslogik
Diese Schicht bildet das Herzstück von ForgeX.
Verantwortlichkeiten:
•	Validierung der Benutzereingaben
•	Aufbau der Verarbeitungsliste
•	Steuerung des Batch-Ablaufs
•	Fehlerbehandlung auf Prozessebene
•	Koordination aller Exporte
Die Konvertierungslogik kennt:
•	die unterstützten Dokumenttypen
•	die zulässigen Exportkombinationen
•	die Reihenfolge der Verarbeitungsschritte
Sie kennt nicht:
•	UI-Details
•	konkrete Benutzerinteraktionen
________________________________________
4.4 Inventor-Integrationsschicht
Diese Schicht kapselt sämtliche Zugriffe auf die Autodesk Inventor API.
Ziele dieser Kapselung:
•	Minimierung der Abhängigkeit von COM
•	klare Verantwortlichkeiten
•	einfachere Wartung bei Inventor-Updates
Typische Aufgaben:
•	Starten oder Verbinden mit einer Inventor-Instanz
•	Öffnen von IPT-, IAM- und IDW-Dokumenten
•	Typprüfung und Dokumentanalyse
•	Auslösen von Exportfunktionen
•	sauberes Schließen aller Dokumente
Kein anderer Teil der Anwendung greift direkt auf Inventor zu.
________________________________________
4.5 Datei- & Infrastruktur-Schicht
Diese Schicht ist zuständig für:
•	Pfadverwaltung
•	Dateioperationen
•	temporäre Dateien
•	Exportkonfigurationen (z. B. DXF-INI-Dateien)
Sie stellt sicher, dass:
•	Zielverzeichnisse existieren
•	Dateiattribute korrekt gesetzt sind
•	bestehende Dateien überschrieben werden können
•	temporäre Artefakte sauber aufgeräumt werden
________________________________________
4.6 Interner Ablauf einer Batch-Konvertierung
Der folgende Ablauf beschreibt einen vollständigen Konvertierungslauf von Start bis Ende.
________________________________________
4.6.1 Initialisierung
1.	Anwender startet die Konvertierung
2.	UI übergibt Parameter an die Logikschicht:
o	Quellverzeichnis
o	Ausgabeverzeichnis
o	gewünschte Exportformate
3.	Grundlegende Validierungen werden durchgeführt
________________________________________
4.6.2 Dateisammlung & Analyse
1.	Rekursive Suche im Quellverzeichnis
2.	Filterung nach unterstützten Dateitypen
3.	Aufbau einer internen Verarbeitungsliste
4.	Sortierung und Priorisierung
________________________________________
4.6.3 Inventor-Session-Management
1.	Start oder Wiederverwendung einer Inventor-Instanz
2.	Initialisierung der API-Umgebung
3.	Vorbereitung für den Batch-Betrieb
Inventor wird kontrolliert und deterministisch verwendet.
________________________________________
4.6.4 Dokumentverarbeitung
Für jede Datei:
1.	Öffnen des Dokuments
2.	Ermittlung des Dokumenttyps
3.	Ableitung der möglichen Exporte
4.	Durchführung der Exporte
5.	Schließen des Dokuments
6.	Freigabe aller Ressourcen
Fehler in einzelnen Dateien:
•	werden isoliert behandelt
•	stoppen nicht den gesamten Batch-Lauf
________________________________________
4.6.5 Abschlussphase
1.	Beenden oder Freigeben der Inventor-Session
2.	Aufräumen temporärer Ressourcen
3.	Zusammenfassung der Ergebnisse
4.	Rückmeldung an die UI
________________________________________
4.7 Fehlerbehandlung & Stabilität
ForgeX ist auf stabile Langläufe ausgelegt.
Grundprinzipien:
•	Fehler werden lokal behandelt
•	Ressourcen werden immer freigegeben
•	keine versteckten Abhängigkeiten
•	kein impliziter Zustand zwischen Dateien
Dies ist essenziell für:
•	große Datenmengen
•	unbeaufsichtigte Verarbeitung
•	reproduzierbare Ergebnisse
________________________________________
4.8 Erweiterbarkeit der Architektur
Die Architektur erlaubt:
•	neue Exportformate
•	neue Dokumentstrategien
•	projektspezifische Sonderlogik
Dies geschieht durch:
•	Ergänzung der Konvertierungslogik
•	Erweiterung der Inventor-Integrationsschicht
•	Anpassung der Konfigurationslogik
Die bestehende Struktur bleibt dabei erhalten.
________________________________________
Zusammenfassung
Die Systemarchitektur von ForgeX ist:
•	klar strukturiert
•	wartbar
•	erweiterbar
•	auf Stabilität ausgelegt
Sie stellt sicher, dass:
komplexe CAD-Operationen kontrolliert, reproduzierbar und automatisiert ablaufen
 
5. Entwicklerdokumentation
Dieses Kapitel richtet sich an Entwickler, Maintainer und technische Projektverantwortliche.
Es beschreibt den internen Aufbau des Codes, die wichtigsten Klassen und Verantwortlichkeiten, sowie die Entwicklungsprinzipien, die in ForgeX angewendet werden.
Ziel ist es, dass ein Entwickler:
•	den Code strukturell versteht
•	Änderungen gezielt vornehmen kann
•	neue Funktionen sauber integrieren kann
•	typische Fehler vermeidet
________________________________________
5.1 Technologie-Stack & Grundlagen
ForgeX basiert auf folgenden Technologien:
•	Programmiersprache: C#
•	Framework: .NET (Desktop)
•	UI-Technologie: WinForms
•	CAD-Integration: Autodesk Inventor API (COM / Interop)
•	Dateizugriff: System.IO
Die Anwendung ist nicht webbasiert und benötigt:
•	eine lokale Inventor-Installation
•	Zugriff auf das Dateisystem
________________________________________
5.2 Projektstruktur (logische Aufteilung)
Die Codebasis ist logisch in funktionale Bereiche gegliedert.
Die tatsächlichen Namespace-Namen können variieren, folgen aber diesem Prinzip:
ForgeX
│
├─ UI
│   ├─ MainForm
│   └─ Dialoge / Settings
│
├─ Core
│   ├─ BatchController
│   ├─ ConversionManager
│   └─ ProcessingContext
│
├─ InventorIntegration
│   ├─ InventorSession
│   ├─ DocumentHandler
│   └─ ExportServices
│
├─ Export
│   ├─ DxfExporter
│   ├─ StepExporter
│   └─ ExportConfiguration
│
├─ Infrastructure
│   ├─ FileSystemHelper
│   ├─ PathResolver
│   └─ AttributeHelper
│
└─ Utilities
    ├─ Logging
    └─ ErrorHandling
Diese Trennung ist konzeptionell, aber bewusst so angelegt.
________________________________________
5.3 Zentrale Steuerung: BatchController
Der BatchController ist die zentrale Orchestrierungseinheit.
Verantwortlichkeiten:
•	Starten eines Batch-Laufs
•	Iteration über alle Dateien
•	Koordination der Exportvorgänge
•	Übergabe von Statusinformationen
Er kennt:
•	die Verarbeitungsliste
•	die Konfiguration
•	den aktuellen Status
Er kennt nicht:
•	UI-Details
•	konkrete Inventor-API-Aufrufe
________________________________________
5.4 InventorSession & Lebenszyklus
Die Klasse InventorSession kapselt den gesamten Lebenszyklus der Inventor-Anwendung.
Aufgaben:
•	Starten oder Verbinden mit Inventor
•	Bereitstellen eines stabilen API-Zugriffs
•	Beenden oder Freigeben der Session
Designziele:
•	genau eine kontrollierte Session
•	keine „verwaisten“ COM-Objekte
•	kein mehrfaches Starten
________________________________________
5.5 Dokumentverarbeitung: DocumentHandler
Der DocumentHandler ist verantwortlich für:
•	Öffnen von IPT / IAM / IDW
•	Typbestimmung
•	Übergabe an passende Exportlogik
Er entscheidet:
•	welche Exporter angewendet werden
•	ob ein Dokument geeignet ist
•	ob Sonderfälle vorliegen
Der Handler selbst exportiert nicht, sondern delegiert.
________________________________________
5.6 Exporter-Architektur
5.6.1 Grundprinzip
Jedes Exportformat hat:
•	einen eigenen Exporter
•	eine klar definierte Schnittstelle
•	keine Abhängigkeit zur UI
Beispiel:
•	DxfExporter
•	StepExporter
Diese Klassen:
•	erhalten ein geöffnetes Inventor-Dokument
•	führen exakt einen Export aus
•	geben Erfolg oder Fehler zurück
________________________________________
5.6.2 DXF-Export (DxfExporter)
Der DXF-Export:
•	nutzt Inventor DataIO
•	verwendet eine generierte INI-Datei
•	ist vollständig konfigurierbar
Typische Schritte:
1.	Erzeugen der INI-Datei
2.	Übergabe an DataIO
3.	Auslösen des Exports
4.	Aufräumen temporärer Dateien
________________________________________
5.6.3 STEP-Export (StepExporter)
Der STEP-Export:
•	nutzt die native Inventor-Exportfunktion
•	erzeugt ein 3D-Austauschformat
•	ist unabhängig von Zeichnungen
Besonderheiten:
•	Behandlung vorhandener Dateien
•	Normalisierung von Dateiattributen (optional)
•	saubere Fehlerbehandlung
________________________________________
5.7 Infrastruktur-Helferklassen
FileSystemHelper
•	Erstellen von Verzeichnissen
•	Prüfen von Dateizugriffen
•	Löschen / Überschreiben von Dateien
PathResolver
•	Ableitung von Zielpfaden
•	Namenskonventionen
•	Kollisionsvermeidung
AttributeHelper
•	Normalisierung von Dateiattributen
•	Entfernung von Schreibschutz
________________________________________
5.8 Fehlerbehandlung & Logging
ForgeX verfolgt einen defensiven Fehlerbehandlungsansatz:
•	Fehler werden möglichst lokal abgefangen
•	ein Fehler stoppt nicht den gesamten Batch
•	relevante Informationen werden gesammelt
Logging kann:
•	für Debug-Zwecke erweitert werden
•	projektspezifisch angepasst werden
________________________________________
5.9 Erweiterung der Anwendung
Neues Exportformat hinzufügen
1.	Neue Exporter-Klasse erstellen
2.	Einheitliche Schnittstelle implementieren
3.	Registrierung im DocumentHandler
4.	UI-Option ergänzen
Neue Regeln hinzufügen
•	im ConversionManager
•	ohne Änderungen an der UI
________________________________________
5.10 Entwicklungsrichtlinien
Empfohlene Grundsätze:
•	klare Verantwortlichkeiten
•	keine Logik im UI
•	kein direkter Inventor-Zugriff außerhalb der Integrationsschicht
•	saubere Freigabe von COM-Objekten
Diese Regeln sind entscheidend für die Stabilität.
________________________________________
Zusammenfassung
Die Entwicklerdokumentation zeigt, dass ForgeX:
•	strukturiert
•	wartbar
•	erweiterbar
•	professionell aufgebaut
ist und langfristig gepflegt werden kann.
 
6. Schnittstellen & Abhängigkeiten
Dieses Kapitel beschreibt alle externen und internen Abhängigkeiten von ForgeX sowie die verwendeten Schnittstellen.
Ziel ist es, transparent darzulegen:
•	wovon ForgeX technisch abhängig ist
•	welche Bibliotheken eingebunden werden
•	wie diese Abhängigkeiten genutzt werden
•	und welche Auswirkungen Änderungen daran haben
Dieses Kapitel ist besonders wichtig für:
•	Wartung
•	Updates
•	Migration auf neue Inventor-Versionen
•	Build- & Deployment-Prozesse
________________________________________
6.1 Überblick über externe Abhängigkeiten
ForgeX ist bewusst schlank gehalten und verwendet nur wenige, gezielt ausgewählte externe Abhängigkeiten.
Hauptabhängigkeiten:
1.	Autodesk Inventor (Installation)
2.	Autodesk Inventor API (COM / Interop)
3.	Microsoft .NET Runtime
4.	Windows-Betriebssystem
Zusätzliche Drittanbieter-Libraries werden nicht verwendet, sofern sie nicht zwingend notwendig sind.
________________________________________
6.2 Autodesk Inventor als Systemabhängigkeit
6.2.1 Erforderliche Inventor-Installation
ForgeX setzt eine lokale Installation von Autodesk Inventor voraus.
Eigenschaften:
•	Inventor muss ordnungsgemäß installiert sein
•	Die Version muss zur verwendeten Interop passen
•	ForgeX startet Inventor nicht interaktiv, sondern steuert es programmatisch
ForgeX ist keine eigenständige CAD-Engine, sondern nutzt Inventor als Ausführungsumgebung.
________________________________________
6.2.2 Zugriff über COM-Automation
Die Kommunikation mit Inventor erfolgt ausschließlich über:
•	COM-Automation
•	bereitgestellt durch die Inventor Type Library
Dies bedeutet:
•	starke Abhängigkeit von der installierten Inventor-Version
•	COM-Objekte müssen explizit freigegeben werden
•	Lebenszyklen müssen exakt kontrolliert werden
________________________________________
6.3 Interop.Inventor (Primäre API-Abhängigkeit)
6.3.1 Einbindung der Interop
ForgeX bindet die Inventor-API über:
•	Interop.Inventor.dll
Diese Assembly wird:
•	über eine COM-Referenz eingebunden
•	beim Build referenziert
•	zur Laufzeit durch die Inventor-Installation bereitgestellt
Wichtig:
Die Interop-Datei selbst wird nicht mit ausgeliefert, sondern verweist auf die lokal installierte Inventor-Version.
________________________________________
6.3.2 Zentrale verwendete API-Bereiche
ForgeX nutzt u. a. folgende Inventor-API-Bereiche:
•	Inventor.Application
•	Inventor.Documents
•	Inventor.PartDocument
•	Inventor.AssemblyDocument
•	Inventor.DrawingDocument
•	Inventor.DataIO
•	Inventor.TransientObjects
Diese werden ausschließlich in der Inventor-Integrationsschicht verwendet.
________________________________________
6.3.3 Versionsabhängigkeiten
Die Inventor-API ist:
•	weitgehend abwärtskompatibel
•	dennoch versionsabhängig
Empfehlungen:
•	ForgeX gegen eine definierte Inventor-Hauptversion bauen
•	Versionswechsel testen, bevor produktiv eingesetzt
•	API-Änderungen dokumentieren
________________________________________
6.4 Microsoft .NET Runtime
6.4.1 Ziel-Framework
ForgeX basiert auf:
•	.NET (klassisches Desktop-Framework)
Eigenschaften:
•	native Windows-Anwendung
•	volle Unterstützung für COM-Interop
•	stabile Dateisystem-Integration
Die Wahl von .NET ist bewusst erfolgt, da:
•	Autodesk Inventor selbst COM-basiert ist
•	.NET eine robuste COM-Integration bietet
________________________________________
6.4.2 Systembibliotheken
ForgeX nutzt ausschließlich Standard-.NET-Bibliotheken, u. a.:
•	System
•	System.IO
•	System.Linq
•	System.Collections.Generic
•	System.Windows.Forms
Diese gelten als:
•	stabil
•	langfristig verfügbar
•	wartungsarm
________________________________________
6.5 Windows-Betriebssystem
ForgeX ist eine Windows-only Anwendung.
Abhängigkeiten:
•	Windows Dateisystem (NTFS)
•	COM-Infrastruktur
•	Benutzerrechte für Dateioperationen
Netzlaufwerke werden unterstützt, sofern:
•	entsprechende Zugriffsrechte vorhanden sind
•	die Pfade erreichbar sind
________________________________________
6.6 Keine versteckten Shell- oder UI-Abhängigkeiten
ForgeX verwendet:
•	keine Windows-Shell-Operationen
•	keine Explorer-Automation
•	keine Desktop-Interaktion
Alle Operationen erfolgen:
•	direkt über .NET
•	direkt über Inventor-API
Dies reduziert:
•	Seiteneffekte
•	unerwartetes Verhalten
•	Abhängigkeiten von Benutzerprofilen
________________________________________
6.7 Interne Schnittstellen
Zwischen den internen Modulen bestehen klar definierte Schnittstellen.
Beispiele:
•	UI → BatchController
•	BatchController → ConversionManager
•	ConversionManager → Exporter
•	Exporter → Inventor-API
Diese Schnittstellen:
•	sind bewusst schmal gehalten
•	erleichtern Refactoring
•	ermöglichen Tests und Erweiterungen
________________________________________
6.8 Auswirkungen von Änderungen an Abhängigkeiten
Inventor-Update
•	möglich, aber zu testen
•	potenziell API-Änderungen
.NET-Update
•	in der Regel unkritisch
•	Build-Tests empfohlen
Betriebssystem
•	Windows-Versionen mit COM-Unterstützung erforderlich
________________________________________
Zusammenfassung
ForgeX besitzt eine klar definierte, überschaubare Abhängigkeitsstruktur.
Die wichtigste Erkenntnis:
Inventor ist die zentrale externe Abhängigkeit – alles andere ist bewusst minimal gehalten.
Diese Reduktion erhöht:
•	Stabilität
•	Wartbarkeit
•	Vorhersagbarkeit
 
7. Konfiguration & Anpassung
Dieses Kapitel beschreibt alle Möglichkeiten zur Konfiguration und Anpassung von ForgeX,
ohne dass der grundlegende Code oder die Architektur verändert werden muss.
Ziel ist es aufzuzeigen:
•	welche Einstellungen zur Laufzeit beeinflussbar sind
•	welche Anpassungen projektspezifisch sinnvoll sind
•	wo die Grenze zwischen Konfiguration und Codeänderung liegt
Dieses Kapitel ist besonders relevant für:
•	CAD-Administratoren
•	Projektverantwortliche
•	Entwickler, die kundenspezifische Anpassungen vornehmen
________________________________________
7.1 Grundprinzip der Konfiguration
ForgeX folgt dem Grundsatz:
So viel wie möglich konfigurierbar, so wenig wie nötig fest im Code
Konfigurationen steuern:
•	Exportverhalten
•	Dateiausgabe
•	technische Parameter (z. B. DXF-Einstellungen)
Nicht konfigurierbar sind:
•	grundlegende Prozesslogik
•	Sicherheitsrelevante Abläufe
•	Stabilitätskritische COM-Steuerung
________________________________________
7.2 Konfigurierbare Anwenderoptionen
7.2.1 Eingabepfad
Der Anwender kann:
•	beliebige lokale Ordner
•	Netzlaufwerke
•	Projektverzeichnisse
als Quellverzeichnis festlegen.
Die Auswahl erfolgt:
•	manuell über die UI
•	pro Batch-Lauf neu
________________________________________
7.2.2 Ausgabepfad
Der Ausgabepfad ist vollständig frei wählbar.
Eigenschaften:
•	gilt für alle Exporte eines Batch-Laufs
•	unabhängig vom Speicherort der Quelldateien
•	kann jederzeit geändert werden
Typische Anwendungsfälle:
•	zentrales Exportverzeichnis
•	projektbezogene Zielordner
•	Übergabeverzeichnisse für Fertigung oder CAM
________________________________________
7.2.3 Auswahl der Exportformate
Der Anwender kann pro Lauf festlegen:
•	DXF aktiv / inaktiv
•	STEP aktiv / inaktiv
ForgeX stellt sicher:
•	dass nur gültige Kombinationen ausgeführt werden
•	dass nicht unterstützte Exporte automatisch übersprungen werden
________________________________________
7.3 Technische Exportkonfiguration (DXF)
7.3.1 INI-basierte DXF-Konfiguration
Der DXF-Export wird über eine INI-Datei gesteuert, die zur Laufzeit erzeugt oder geladen wird.
Diese Datei definiert u. a.:
•	AutoCAD-Zielversion
•	Layer-Mapping
•	Linientypen
•	Skalierung
•	Geometrieoptionen
Die INI-Struktur entspricht der von Inventor unterstützten Exportdefinition.
________________________________________
7.3.2 Anpassung der Linientypen
Linientypen können projektspezifisch angepasst werden, z. B.:
•	Continuous
•	Dashed
•	Long Dash Dotted
•	Chain
Dabei wird:
•	ein fest definiertes LIN-File verwendet
•	eine konsistente Darstellung in Ziel-CAD-Systemen angestrebt
________________________________________
7.3.3 Mapping & Skalierung
Die Konfiguration erlaubt:
•	geometriegetreue Exporte
•	kontrollierte Skalierung
•	projektspezifische Mapping-Strategien
Dies ist besonders relevant für:
•	CNC-Fertigung
•	Laserschneiden
•	externe Datenweitergabe
________________________________________
7.4 STEP-Export-Konfiguration
Der STEP-Export ist bewusst schlank konfigurierbar.
Typische Einstellungen:
•	Zielpfad
•	Überschreiben vorhandener Dateien
•	Zielversion (z. B. AP203 / AP214)
Nicht konfigurierbar (bewusst):
•	Geometrievereinfachung
•	Feature-Reduktion
Der Fokus liegt auf vollständiger 3D-Geometrie.
________________________________________
7.5 Versions- & Build-Konfiguration
7.5.1 Versionsnummer
Die Versionsnummer der Anwendung wird:
•	zentral im Projekt definiert
•	über Application.ProductVersion ausgelesen
•	automatisch in der UI angezeigt
Empfohlenes Schema:
•	Major.Minor.Patch
•	z. B. 1.0.36
________________________________________
7.5.2 Build-Konfiguration
ForgeX kann:
•	als Release-Build
•	oder Debug-Build
erstellt werden.
Empfehlung:
•	Debug nur für Entwicklung
•	Release für produktiven Einsatz
________________________________________
7.6 Projektspezifische Anpassungen (ohne Architekturbruch)
Mögliche Anpassungen:
•	zusätzliche Filterlogik
•	projektspezifische Exportprofile
•	unterschiedliche Zielordnerlogiken
•	kundenindividuelle Defaults
Diese Anpassungen erfolgen:
•	in der Konvertierungslogik
•	ohne Änderung der UI-Grundstruktur
________________________________________
7.7 Grenzen der Konfiguration
Nicht über Konfiguration lösbar sind:
•	neue Dateiformate
•	neue Exportarten
•	grundlegende Prozessänderungen
Diese erfordern:
•	gezielte Codeänderungen
•	Erweiterung der Exporter
•	Anpassung der Architektur
________________________________________
Zusammenfassung
ForgeX bietet eine klare Trennung zwischen Konfiguration und Code.
Das bedeutet:
•	Anwender können flexibel arbeiten
•	Administratoren können Standards definieren
•	Entwickler behalten volle Kontrolle über Stabilität
 
8. Lizenzierung & Nutzungsrechte
Dieses Kapitel beschreibt die Lizenzierungsform, die Nutzungsrechte sowie die rechtlichen Rahmenbedingungen für den Einsatz von ForgeX.
Es dient sowohl als Grundlage für Endanwender als auch als Orientierung für Vertrieb, Projektverantwortliche und Entwickler.
Ziel ist es, klar festzulegen:
•	wer ForgeX nutzen darf
•	unter welchen Bedingungen die Nutzung erfolgt
•	was ausdrücklich erlaubt ist
•	und was ausdrücklich untersagt ist
________________________________________
8.1 Grundlegendes Lizenzmodell
ForgeX ist als kommerzielle Software konzipiert und wird nicht als Open-Source-Produkt vertrieben.
Das bedeutet:
•	der Quellcode ist nicht öffentlich
•	Nutzungsrechte werden vertraglich eingeräumt
•	Eigentumsrechte verbleiben beim Hersteller / Rechteinhaber
ForgeX wird dem Anwender lizenziert, nicht verkauft.
________________________________________
8.2 Eigentum & Urheberrecht
Alle Rechte an ForgeX verbleiben bei:
•	dem Entwickler
•	bzw. dem rechtlich definierten Rechteinhaber
Dies umfasst insbesondere:
•	Quellcode
•	Binärdateien
•	Dokumentation
•	Konzepte, Architektur und Designentscheidungen
ForgeX unterliegt dem Urheberrecht.
________________________________________
8.3 Umfang der eingeräumten Nutzungsrechte
Mit Erwerb einer gültigen Lizenz erhält der Lizenznehmer das Recht:
•	ForgeX für eigene betriebliche Zwecke zu nutzen
•	die Software gemäß Dokumentation einzusetzen
•	die erzeugten Exportdaten uneingeschränkt weiterzuverwenden
Die Nutzung erfolgt:
•	auf eigene Verantwortung
•	innerhalb des vertraglich vereinbarten Rahmens
________________________________________
8.4 Zulässige Nutzungsformen
Je nach Lizenzmodell können folgende Nutzungsarten erlaubt sein:
8.4.1 Einzelplatzlizenz
•	Nutzung auf einem Arbeitsplatz
•	durch einen Anwender oder mehrere Anwender zeitlich versetzt
8.4.2 Mehrplatz- / Unternehmenslizenz
•	Nutzung innerhalb eines Unternehmens
•	auf mehreren Arbeitsplätzen
•	unter Einhaltung der vereinbarten Lizenzbedingungen
8.4.3 Projektbezogene Nutzung
•	zeitlich oder projektbezogen begrenzte Nutzung
•	insbesondere für externe Dienstleister oder Projektpartner
Die konkrete Ausgestaltung erfolgt vertraglich.
________________________________________
8.5 Nicht erlaubte Nutzungsformen
Ohne ausdrückliche schriftliche Genehmigung sind insbesondere nicht erlaubt:
•	Weitergabe der Software an Dritte
•	Verkauf, Vermietung oder Verleih
•	Unterlizenzierung
•	öffentliche Bereitstellung
•	Reverse Engineering
•	Dekompilierung oder Disassemblierung
•	Entfernung von Lizenz- oder Copyright-Hinweisen
Diese Einschränkungen gelten unabhängig davon, ob:
•	die Software verändert wurde
•	sie kostenfrei weitergegeben werden soll
•	sie intern angepasst wurde
________________________________________
8.6 Anpassungen & Erweiterungen
8.6.1 Kundenspezifische Anpassungen
Anpassungen durch den Hersteller oder autorisierte Entwickler sind erlaubt und vorgesehen.
Beispiele:
•	projektspezifische Exportlogik
•	zusätzliche Filter
•	kundenspezifische Workflows
Diese Anpassungen:
•	bleiben Bestandteil von ForgeX
•	unterliegen weiterhin dem Urheberrecht
________________________________________
8.6.2 Eigene Erweiterungen durch den Kunden
Eigene Erweiterungen oder Änderungen am Quellcode durch den Lizenznehmer sind:
•	nur mit ausdrücklicher Genehmigung erlaubt
•	andernfalls nicht zulässig
Auch bei genehmigten Änderungen gilt:
•	keine Weitergabe
•	keine Veröffentlichung
•	keine kommerzielle Verwertung
________________________________________
8.7 Abhängigkeit von Autodesk Inventor
ForgeX ist kein Ersatz für Autodesk Inventor.
Wichtig:
•	eine gültige Inventor-Lizenz ist zwingend erforderlich
•	ForgeX enthält keine Inventor-Komponenten
•	alle Rechte an Inventor verbleiben bei Autodesk
ForgeX steht in keinem direkten Lizenzverhältnis zu Autodesk.
________________________________________
8.8 Haftungsausschluss & Gewährleistung
ForgeX wird bereitgestellt:
•	„wie gesehen“
•	ohne Garantie auf Fehlerfreiheit
•	ohne Haftung für Folgeschäden
Insbesondere ausgeschlossen sind:
•	Produktionsausfälle
•	Datenverluste
•	wirtschaftliche Schäden
Sofern gesetzlich zulässig, ist die Haftung auf Vorsatz und grobe Fahrlässigkeit beschränkt.
________________________________________
8.9 Laufzeit & Beendigung der Lizenz
Die Lizenz:
•	kann zeitlich unbegrenzt oder befristet sein
•	endet bei Vertragsverletzung automatisch
Nach Beendigung der Lizenz ist:
•	die Nutzung einzustellen
•	die Software zu deinstallieren
Erzeugte Exportdaten bleiben im Besitz des Lizenznehmers.
________________________________________
8.10 Zusammenfassung der Lizenzprinzipien
ForgeX folgt klaren Grundsätzen:
•	kommerziell
•	nicht Open Source
•	keine Weitergabe
•	keine Veränderung ohne Genehmigung
•	klare Trennung zu Autodesk
Dieses Kapitel schafft die Grundlage für:
•	rechtssicheren Einsatz
•	Vertrieb
•	Kundenverträge
•	interne Compliance
 
9. Wartung, Erweiterung & Troubleshooting
Dieses Kapitel beschreibt, wie ForgeX langfristig betrieben, gewartet und erweitert werden kann und wie mit typischen Problemen umzugehen ist.
Es richtet sich an:
•	Entwickler
•	technische Administratoren
•	Support-Verantwortliche
•	zukünftige Maintainer des Projekts
________________________________________
9.1 Wartungskonzept
ForgeX ist als langfristig wartbare Software konzipiert.
Grundprinzipien der Wartung:
•	klare Architektur
•	begrenzte externe Abhängigkeiten
•	reproduzierbares Verhalten
•	saubere Ressourcenverwaltung
Die Wartung umfasst:
•	Fehlerkorrekturen
•	Anpassungen an neue Inventor-Versionen
•	kleinere funktionale Erweiterungen
________________________________________
9.2 Updates & Versionierung
9.2.1 Versionsstrategie
ForgeX verwendet eine semantische Versionierung:
MAJOR.MINOR.PATCH
•	MAJOR: grundlegende Architekturänderungen
•	MINOR: funktionale Erweiterungen
•	PATCH: Bugfixes, Stabilitätsverbesserungen
Diese Versionierung wird:
•	zentral im Projekt gepflegt
•	automatisch in der Anwendung angezeigt
________________________________________
9.2.2 Update-Prozess
Ein Update von ForgeX umfasst in der Regel:
1.	Austausch der Programmdateien
2.	ggf. Anpassung von Konfigurationsdateien
3.	Funktionstest mit Beispielprojekten
Ein Neuaufsetzen der Umgebung ist nicht erforderlich, sofern:
•	die Inventor-Version kompatibel bleibt
•	keine Major-Änderungen vorgenommen wurden
________________________________________
9.3 Erweiterung der Funktionalität
9.3.1 Neue Exportformate
Neue Exportformate können integriert werden durch:
•	Hinzufügen eines neuen Exporters
•	Anbindung an die Inventor-API
•	Erweiterung der Konvertierungslogik
Die bestehende Architektur bleibt dabei erhalten.
________________________________________
9.3.2 Projektspezifische Erweiterungen
Typische projektspezifische Anpassungen:
•	Filterlogiken
•	alternative Zielpfadstrategien
•	kundenindividuelle Exportprofile
•	automatisierte Vor- oder Nachbearbeitung
Diese Erweiterungen sind gezielt lokal umsetzbar.
________________________________________
9.4 Typische Fehlerquellen & Ursachen
9.4.1 Inventor nicht verfügbar
Ursachen:
•	Inventor nicht installiert
•	falsche Version
•	fehlende Lizenz
Auswirkung:
•	ForgeX kann keine Konvertierung starten
________________________________________
9.4.2 Fehlerhafte oder unvollständige Modelle
Ursachen:
•	ungültige Geometrie
•	fehlende Abhängigkeiten
•	defekte Referenzen
Auswirkung:
•	einzelne Dateien können nicht exportiert werden
•	Batch läuft weiter
________________________________________
9.4.3 Schreibgeschützte Zieldateien
Ursachen:
•	manuell gesetzter Schreibschutz
•	Rechteprobleme
•	Netzlaufwerke
Auswirkung:
•	Datei kann nicht überschrieben werden
ForgeX behandelt diese Fälle defensiv.
________________________________________
9.5 Troubleshooting-Strategie
Empfohlene Vorgehensweise bei Problemen:
1.	Reproduzierbarkeit prüfen
2.	Einzeldatei isoliert testen
3.	Ausgabepfade und Rechte prüfen
4.	Inventor-Version kontrollieren
5.	Logs oder Statusmeldungen auswerten
Die klare Trennung der Komponenten erleichtert die Fehlersuche.
________________________________________
9.6 Support & Betrieb
ForgeX ist für:
•	produktiven Dauerbetrieb
•	unbeaufsichtigte Batch-Läufe
geeignet.
Für den Betrieb empfohlen:
•	dedizierter Arbeitsplatz oder Server
•	stabile Inventor-Installation
•	definierte Update-Zyklen
________________________________________
9.7 Übergabe an neue Entwickler oder Teams
Durch:
•	klare Dokumentation
•	modulare Architektur
•	eindeutige Verantwortlichkeiten
kann ForgeX problemlos:
•	an neue Entwickler übergeben
•	von externen Dienstleistern betreut
•	langfristig weitergeführt werden
________________________________________
9.8 Zukunftssicherheit
ForgeX ist darauf ausgelegt:
•	neue Inventor-Versionen aufzunehmen
•	neue Exportanforderungen zu integrieren
•	in bestehende Prozesse eingebunden zu bleiben
Die Architektur bildet dafür eine stabile Grundlage.
________________________________________
Abschließende Zusammenfassung
ForgeX ist:
•	technisch sauber aufgebaut
•	für den professionellen Einsatz geeignet
•	langfristig wartbar und erweiterbar
Diese Dokumentation stellt sicher, dass:
das Wissen über ForgeX nicht an einzelne Personen gebunden ist
und bildet die Grundlage für nachhaltigen Einsatz und Weiterentwicklung.
 
10. Endbenutzer-Lizenzvereinbarung (EULA), Lizenz & Copyright
Dieses Kapitel stellt die rechtlich verbindliche Endbenutzer-Lizenzvereinbarung (End User License Agreement, EULA) für die Software ForgeX dar.
Es regelt die Nutzung, die Rechte und Pflichten des Lizenznehmers sowie die Rechte des Rechteinhabers.
________________________________________
10.1 Präambel
Diese Lizenzvereinbarung ist ein rechtsgültiger Vertrag zwischen dem Lizenznehmer (nachfolgend „Nutzer“) und dem Rechteinhaber der Software ForgeX.
Mit der Installation, Nutzung oder Weitergabe der Software im Rahmen dieser Lizenz erklärt sich der Nutzer mit den nachfolgenden Bedingungen einverstanden.
________________________________________
10.2 Softwarebeschreibung
ForgeX ist eine Windows-Desktop-Software zur automatisierten Konvertierung von Autodesk-Inventor-Dateien in verschiedene Austauschformate.
Die Software nutzt die Autodesk Inventor API und setzt eine gültige Inventor-Installation voraus.
________________________________________
10.3 Urheber & Rechteinhaber
Entwickler:
Jonas Eisenmann
Rechteinhaber:
PEGO Holding GmbH
Copyright:
© 2026 PEGO Holding GmbH. Alle Rechte vorbehalten.
ForgeX ist urheberrechtlich geschützt.
Alle nicht ausdrücklich gewährten Rechte bleiben dem Rechteinhaber vorbehalten.
________________________________________
10.4 Lizenzgewährung
Der Rechteinhaber räumt dem Nutzer eine nicht exklusive, nicht übertragbare, zeitlich begrenzte oder unbefristete Lizenz zur Nutzung der Software ForgeX ein – abhängig vom individuell geschlossenen Lizenzvertrag.
Die Lizenz berechtigt ausschließlich zur Nutzung der Software gemäß dieser Vereinbarung.
________________________________________
10.5 Erlaubte Nutzung
Der Nutzer ist berechtigt:
•	ForgeX für eigene betriebliche oder private Zwecke zu verwenden
•	die Software auf den vereinbarten Systemen zu installieren
•	mit ForgeX erzeugte Dateien uneingeschränkt weiterzuverwenden
•	die Software entsprechend der Dokumentation einzusetzen
Die Nutzung ist nur im Rahmen der jeweils erworbenen Lizenz zulässig.
________________________________________
10.6 Unzulässige Nutzung
Ohne ausdrückliche schriftliche Genehmigung des Rechteinhabers ist es nicht gestattet:
•	die Software oder Teile davon weiterzugeben
•	die Software zu verkaufen, zu vermieten oder zu verleihen
•	Unterlizenzen zu vergeben
•	die Software öffentlich zugänglich zu machen
•	den Quellcode zu analysieren, zu dekompilieren oder zu disassemblieren
•	Schutzmechanismen oder Lizenzprüfungen zu umgehen
•	Copyright- oder Lizenzhinweise zu entfernen
Diese Einschränkungen gelten unabhängig davon, ob die Software verändert wurde oder nicht.
________________________________________
10.7 Änderungen & Erweiterungen
Änderungen oder Erweiterungen an ForgeX sind nur zulässig, wenn:
•	sie durch den Rechteinhaber selbst erfolgen
oder
•	sie ausdrücklich schriftlich genehmigt wurden
Auch bei genehmigten Anpassungen verbleiben sämtliche Rechte am ursprünglichen Werk beim Rechteinhaber.
________________________________________
10.8 Abhängigkeit von Drittsoftware
ForgeX setzt eine gültige Lizenz von Autodesk Inventor voraus.
•	Autodesk Inventor ist nicht Bestandteil dieser Software
•	Autodesk ist kein Vertragspartner dieser Lizenz
•	alle Rechte an Autodesk Inventor verbleiben bei Autodesk, Inc.
Der Nutzer ist selbst verantwortlich für die rechtmäßige Lizenzierung der Drittsoftware.
________________________________________
10.9 Gewährleistungsausschluss
ForgeX wird bereitgestellt „wie es ist“.
Der Rechteinhaber übernimmt keine Garantie dafür, dass:
•	die Software fehlerfrei läuft
•	sie bestimmte Anforderungen erfüllt
•	sie unterbrechungsfrei verfügbar ist
Die Nutzung erfolgt auf eigenes Risiko.
________________________________________
10.10 Haftungsbeschränkung
Soweit gesetzlich zulässig haftet der Rechteinhaber nicht für:
•	direkte oder indirekte Schäden
•	Produktionsausfälle
•	entgangenen Gewinn
•	Datenverluste
•	Folgeschäden jeglicher Art
Die Haftung ist auf Vorsatz und grobe Fahrlässigkeit beschränkt.
________________________________________
10.11 Laufzeit & Kündigung
Diese Lizenz gilt:
•	bis zur Kündigung
•	oder bis zum Ablauf einer befristeten Lizenz
Bei Verstoß gegen diese Lizenzbedingungen endet das Nutzungsrecht automatisch.
Nach Beendigung der Lizenz ist:
•	die Nutzung einzustellen
•	die Software zu deinstallieren
________________________________________
10.12 Anwendbares Recht
Es gilt das Recht der Bundesrepublik Deutschland.
Gerichtsstand ist – soweit zulässig – der Sitz des Rechteinhabers.
________________________________________
10.13 Salvatorische Klausel
Sollten einzelne Bestimmungen dieser Vereinbarung unwirksam sein oder werden, bleibt die Wirksamkeit der übrigen Bestimmungen unberührt.
________________________________________
Abschließender Hinweis
Diese EULA ist integraler Bestandteil der Software ForgeX und gilt ab dem Zeitpunkt der Installation oder Nutzung.

