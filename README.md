# Nexa3D Studio - macOS / iOS / iPadOS

**3D-Asset-Editor und geplante Cinematic-/VFX-Pipeline mit optionaler KI-Unterstützung.**

**Version:** `0.2.0-dev` | **Stand:** 21. Oktober 2026 | **Status:** Architektur + Startercode, **kein veröffentlichtes / professionell fertiges Produkt**.

Nexa3D kombiniert in der geplanten Zielarchitektur einen plattformübergreifenden Szenen- und Mesh-Kern mit SwiftUI-Editor, eigener Metal-Rendering-Pipeline, Retopologie, Rigging, Sequencer, VFX, PBR, Post-Processing, hardwareabhängigem Ray-Tracing, Cinematic-Frameexport und optionalem KI-Backend. Die Workspaces werden phasenweise aufgebaut; der ZIP-Stand enthält viele leere/kommentierte TODO-Dateien, damit Verantwortlichkeiten und Abhängigkeiten vor Beginn klar sind.

## Direkt zu den Unterlagen

- [Entwicklungsplan (vollständige Roadmap)](ENTWICKLUNGSPLAN.md)
- [Technische Architektur (RenderGraph, VFX, ECS, Film, Rigging, RT)](Docs/TECHNISCHE_ARCHITEKTUR.md)
- [Abnahmekriterien und Testmatrix](Docs/ROADMAP_ABNAHME.md)
- [Tatsächlicher Feature-Status](Docs/FEATURE_STATUS.md)
- [Jede einzelne Datei im Repo](DATEIINDEX.md)
- [GitHub-README- und Releasepflichten](Docs/GITHUB_BETRIEB.md)
- [PDF-Dokumentationen](Docs/PDF/)
- [Originale Engine-Benennungsreferenz](Docs/reference/XCODE_ENGINE_ARCHITECTURE_REFERENCE.txt)

## Featurefortschritt (keine Produktversprechen)

| Bereich | Nachweisbarer Stand im Repository | Ziel |
|---|---|---|
| macOS/iOS Workspace | Editor-App auf Mac gebaut und gestartet; Dokumenttests vorhanden | Pro Editor |
| Engine + ECS | `FrameScheduler`, `EntityID`, `ComponentKind` | GameLoop, Systems, GPU Dispatch |
| Metal Renderer / PBR | Entwurf + Plandateien | eigener Rasterrenderer mit PBR, HDR, IBL |
| Retopologie | `RetopologyPlan` + Validierung | PolyBuild, Quad-Flow, Baking |
| Rigging / IK | `RigDefinition`/`SkeletonValidator` | Skinning, Weights, IK, Morph |
| Animation / Sequencer | `FrameRate`, `ScalarKeyframe`, `TimelineEvaluator` | Spuren, Shots, F-Curves, Audio |
| Cinematic Video | `RenderJobSpec` | MovieRenderQueue, PNG, H264/HEVC/ProRes nach Support |
| GPU VFX | `ParticleEmitterConfiguration` | Compute Particles / Trails / Fog |
| PostFX / Color | `ColorPipelineSettings` | Bloom, DoF, MotionBlur, SSAO, LUT |
| Ray-Tracing | `RayTracingCapabilities.detect()` | optional BLAS/TLAS, Shadow/Reflections, PathTrace |
| Cloud-KI | FastAPI-/Provider-Stubs, Health-Route | echte GPU Job Pipeline |
| Game Export | Format/Limit-Entwürfe | getestetes OBJ/glTF/GLB/USDZ |

**Kritische Einschränkungen:** Ray-Tracing nur auf kompatibler GPU (`MTLDevice.supportsRaytracing`); ProRes je unterstütztem Codec/Device; GPU Performance messabhängig; iPhone bietet perspektivisch reduzierte Pro-Tools; Mocap nur nach ARKit-Geräte- und Datenschutzprüfung. Kein vollständiger Videoexport und keine echte automatisierte Retopologie oder 3D-KI im Stand `0.2.0-dev`.

<!-- STATUS-BEGIN (generated; do not edit manually) -->
### Manifest und Datei-Reife (automatisch erzeugt)

| Kategorie | Einzeldateien | Bedeutung |
|---|---:|---|
| STARTER | 87 | Erste reale Logik oder Konfiguration, keine vollständige Featurefreigabe |
| GEPLANT | 356 | Aufgaben-/Dateigerüst, noch nicht funktional |
| DOKUMENTATION | 22 | Pläne, PDF und Nachweise |
| REFERENZ | 1 | Vom Nutzer gelieferte Benennungsreferenz |
| IMPLEMENTIERT | 0 | Vollständige, nachweislich getestete Einzeldatei |
| **GESAMT** | **466** | **Dateistatus, keine Aussage über Feature-Reife** |

Jede Einzeldatei inklusive Aufgabe und Status: [`DATEIINDEX.md`](DATEIINDEX.md).
<!-- STATUS-END -->

## Quickstart (macOS mit Xcode erforderlich)

```bash
brew install xcodegen
./Scripts/generate-xcode.sh
open Nexa3D.xcodeproj
```

In Xcode `Nexa3DMac` oder `Nexa3DiOS` auswählen und Signing-Bundle-Identifier/Team konfigurieren. Deploymentplan: macOS 15+ und iOS/iPadOS 18+, Swift 6; tatsächlichen Xcode/SDK-Build beim Start der Implementierung auf dem Mac verifizieren. `.xcodeproj` wird erst per XcodeGen generiert, nicht als fertiges Xcode-Projekt mitgeliefert.

## Tests und Statuspflege

```bash
python3 Scripts/check-project-layout.py
python3 Scripts/generate-file-index.py --check
python3 Scripts/update-readme-status.py --check
cd Backend && python3 -m pip install -e '.[test]' && pytest -q
# Auf macOS/Xcode zusätzlich:
cd ../Modules && swift test
```

**Lokale Verifikation 21.10.2026:** Xcode 27.2 (27B5038j), Swift 6.4.2, macOS arm64. Das geöffnete Target `Nexa3D` verlinkt jetzt `NexaEditor` und `NexaDocuments`, baut erfolgreich und wurde auf dem Mac gestartet. `DocumentGroup` ersetzt die ursprüngliche Startansicht. Der Navigator enthält Quellen, Tests, Backend, Beispiele und Dokumentation. `.nexa3d` ist als editierbarer Pakettyp registriert.

Das Swift-Paket enthält zehn bestehende XCTest-Tests und sieben Dokumenttests mit Swift Testing (einschließlich parametrisierter Fälle). Der Dokumenttest schreibt ein Paket auf den Datenträger und liest dessen JSON-Dateien zurück; UUIDs, Namen und Transformationen bleiben erhalten. Fehlende Pflichtdateien, defekte JSON-Daten und unbekannte Versionen werden abgewiesen; zusätzliche Assets und Manifestfelder bleiben beim Speichern erhalten. Der eigenständige Testprozess liest die gespeicherten Bytes direkt, weil sein `FileWrapper(url:)`-Aufruf mit einem Launch-Services-Metadatenfehler scheitert. Dies ersetzt keinen Finder-/Dokumentdialog-Test.

Testkommando: `swift test --disable-sandbox --package-path Modules` (lokale Einschränkung durch verschachtelte Sandbox). Kommentarbasierte Metal-Platzhalter bleiben vom Paketbuild ausgeschlossen. Noch offen: vollständiger UI-Ablauf Neu/Öffnen/Speichern/Undo, iPad-/iOS-Laufprüfung, XcodeGen-Targets und GitHub-CI. XcodeGen und pytest sind lokal nicht installiert.

Die PDFs sind archivierte Planungsstände; aktuelle Buildnachweise stehen hier und in `Docs/FEATURE_STATUS.md`.

## Beitrag und offene Aufgaben

Ein Pull Request muss Code, Tests, Changelog, `DATEIMANIFEST.json` Status und bei Bedarf neue ADRs ändern. Danach `python3 Scripts/generate-file-index.py` und `python3 Scripts/update-readme-status.py` aufrufen, damit GitHub **immer den aktuellen, überprüfbaren Stand** zeigt. CI prüft mit `--check`; inhaltliche Featurefreigabe erfolgt anhand von `Docs/ROADMAP_ABNAHME.md`. Siehe [CONTRIBUTING.md](CONTRIBUTING.md), [SECURITY.md](SECURITY.md), [Changelog](CHANGELOG.md).

**Priorität für die nächste Entwicklungsrunde:** Dokumentdialoge und Undo end-to-end prüfen, iOS-Build nachweisen, anschließend Objekttransformationen/Gizmos und erster Metal Renderpass; Cinematics/Rigging/VFX/Ray-Tracing im Anschluss nach Abnahme.
