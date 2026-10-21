# Nexa3D - Vollständiger Datei- und Ordnerkatalog

**Stand: 21.10.2026 | Dokumentversion: 2.0.**
**466 im Manifest einzeln erfasste Dateien**. Davon: 87 STARTER, 356 GEPLANT, 22 DOKUMENTATION, 1 REFERENZ.

> Status beschreibt die **Datei**, nicht den Fertigstellungsgrad des Features. `STARTER` = teilweise vorhandene Datenlogik, kein vollwertiger Editor; `GEPLANT` = Platzhalter/TODO; `DOKUMENTATION` = Projektunterlagen; `REFERENZ` = vom Benutzer bereitgestellter Text.

## Ordnerstruktur (Zuständigkeiten)

| Ordner | Zweck |
|---|---|
| `Apps/NexaMac` | Native macOS-Benutzeroberfläche, Tastatur, Panels |
| `Apps/NexaMobile` | iPad/iPhone UI, Touch/Pencil, Mobile GPU Profile |
| `Modules/Sources/NexaDomain` / `NexaDocuments` | Datenhoheit, Projektpakete |
| `Modules/Sources/NexaECS` / `NexaEngine` | Entity-Komponenten, Update-/Frame-Loop |
| `Modules/Sources/NexaGeometry` / `NexaRetopology` | Mesh, BVH, Retopo, Baking |
| `Modules/Sources/NexaRigging` / `NexaAnimation` | Bones/Skinning, Timeline, Kurven |
| `Modules/Sources/NexaRendering` / `NexaRenderGraph` | RealityKit MVP, Metal GPU-Pipeline |
| `Modules/Sources/NexaRayTracing` / `NexaCompositing` | Optional Ray/Path-Tracing, HDR/PostFX |
| `Modules/Sources/NexaVFX` / `NexaCinematics` | Partikel/Simulation, Shots/MovieQueue |
| `Modules/Sources/NexaAssetPipeline` | Asset Import, Export, Game-Presets |
| `Modules/Tests`, `Tests/` | Domain, Render- und Integrations-/Benchmarktests |
| `Backend/`, `Contracts/` | KI-/GPU-Jobs und versionierte Austauschformate |
| `Docs/`, `Docs/PDF/` | Architektur, Roadmap, ADRs, PDF-Berichte |
| `Scripts/`, `.github/workflows` | Builds, Generatoren und CI |

## Jede einzelne Datei und ihre Aufgabe

### 3D-Rendering & Mesh-Engine (29)

- `Modules/Sources/NexaGeometry/BooleanOperations.swift` - Union, Difference, Intersection. **[GEPLANT]**
- `Modules/Sources/NexaGeometry/BVH.swift` - Beschleunigungsstruktur für Picking/Kollision. **[GEPLANT]**
- `Modules/Sources/NexaGeometry/Decimator.swift` - Polygonreduktion mit Fehlermaß. **[GEPLANT]**
- `Modules/Sources/NexaGeometry/MeshBuffer.swift` - Eigenes Vertex-/Indexformat als Wahrheitsebene. **[GEPLANT]**
- `Modules/Sources/NexaGeometry/MeshBuilder.swift` - Primitive und prozedurale Meshes. **[GEPLANT]**
- `Modules/Sources/NexaGeometry/MeshTopology.swift` - Kanten, Faces und Adjazenzlisten. **[GEPLANT]**
- `Modules/Sources/NexaGeometry/MeshValidator.swift` - Degenerierte Dreiecke, Normalen, UV und Manifold-Checks. **[GEPLANT]**
- `Modules/Sources/NexaGeometry/NormalsGenerator.swift` - Berechnung von Vertex- und Face-Normalen. **[GEPLANT]**
- `Modules/Sources/NexaGeometry/RetopologyService.swift` - Spätere manuelle/automatische Retopologie. **[GEPLANT]**
- `Modules/Sources/NexaGeometry/Subdivision.swift` - Subdivision/Smoothing für Meshes. **[GEPLANT]**
- `Modules/Sources/NexaGeometry/TangentGenerator.swift` - Tangenten für Normal-Maps. **[GEPLANT]**
- `Modules/Sources/NexaGeometry/UVUnwrapper.swift` - UV-Unwrapping als spätere Funktion. **[GEPLANT]**
- `Modules/Sources/NexaRendering/CameraController.swift` - Orbit, Pan, Zoom und Kamera-Limits. **[GEPLANT]**
- `Modules/Sources/NexaRendering/GizmoRenderer.swift` - Transformationspfeile und Rotationsgizmos. **[GEPLANT]**
- `Modules/Sources/NexaRendering/GridRenderer.swift` - Bodenraster und Achsenhilfen. **[GEPLANT]**
- `Modules/Sources/NexaRendering/MetalDevice.swift` - GPU-Auswahl und Ressourcenverwaltung. **[GEPLANT]**
- `Modules/Sources/NexaRendering/MetalRenderer.swift` - Späterer eigener Metal-Renderpfad. **[GEPLANT]**
- `Modules/Sources/NexaRendering/PickingEngine.swift` - Raycast-Objektauswahl mit Pixel-/Ray-Koordinaten. **[GEPLANT]**
- `Modules/Sources/NexaRendering/Preview3DView.swift` - Plattformübergreifende erste RealityKit-Vorschau. **[STARTER]**
- `Modules/Sources/NexaRendering/RenderDiagnostics.swift` - FPS, VRAM- und Renderzeit-Messung. **[GEPLANT]**
- `Modules/Sources/NexaRendering/RenderPipeline.swift` - Renderpasses, Depth, MSAA und Transparenz. **[GEPLANT]**
- `Modules/Sources/NexaRendering/SceneBridge.swift` - Abbildung der eigenen Szenenobjekte auf Renderer. **[GEPLANT]**
- `Modules/Sources/NexaRendering/SelectionOutline.swift` - Auswahlumriss und Hover-Highlight. **[GEPLANT]**
- `Modules/Sources/NexaRendering/Shaders/Grid.metal` - Rastershader für Editormodus. **[GEPLANT]**
- `Modules/Sources/NexaRendering/Shaders/PBR.metal` - PBR-Vertex-/Fragmentshader. **[GEPLANT]**
- `Modules/Sources/NexaRendering/Shaders/Picking.metal` - GPU-ID-Picking für große Szenen. **[GEPLANT]**
- `Modules/Sources/NexaRendering/ShaderTypes.swift` - Gemeinsame Layouts für Swift und Metal Shader. **[GEPLANT]**
- `Modules/Sources/NexaRendering/TextureCache.swift` - GPU-Textur-Caching, Limits und Entladen. **[GEPLANT]**
- `Modules/Sources/NexaRendering/ViewportController.swift` - Viewport-Zustand, Auswahl und Rendering-Invalidierung. **[GEPLANT]**

### Anwendungsfälle, Editor und UI (25)

- `Modules/Sources/NexaApplication/CreatePrimitiveUseCase.swift` - Objekt anlegen und Undo-Schritt erzeugen. **[GEPLANT]**
- `Modules/Sources/NexaApplication/DeleteSelectionUseCase.swift` - Mehrfachlöschung inkl. Rückgängig. **[GEPLANT]**
- `Modules/Sources/NexaApplication/EditorPreferences.swift` - Editoroptionen und Geräteeinstellungen. **[GEPLANT]**
- `Modules/Sources/NexaApplication/EditorSession.swift` - Anwendungszustand, Auswahl und Dokumentlebenszyklus. **[GEPLANT]**
- `Modules/Sources/NexaApplication/ExportAssetUseCase.swift` - Exportpipeline mit Voreinstellungen. **[GEPLANT]**
- `Modules/Sources/NexaApplication/GenerateAIAssetUseCase.swift` - KI-Job starten und Ergebnis in Szene einfügen. **[GEPLANT]**
- `Modules/Sources/NexaApplication/ImportAssetUseCase.swift` - Asset-Importpipeline mit Fehlerbehandlung. **[GEPLANT]**
- `Modules/Sources/NexaApplication/TransformObjectUseCase.swift` - Positionieren, Drehen, Skalieren und Validieren. **[GEPLANT]**
- `Modules/Sources/NexaApplication/UndoRedoController.swift` - Undo-/Redo-Historie und Transaktionen. **[GEPLANT]**
- `Modules/Sources/NexaDesignSystem/AccessibilitySupport.swift` - VoiceOver und Tastatur-/Touch-Zugänglichkeit. **[GEPLANT]**
- `Modules/Sources/NexaDesignSystem/NexaColors.swift` - Farbdesign und Kontrast-Token. **[GEPLANT]**
- `Modules/Sources/NexaDesignSystem/NexaControls.swift` - Wiederverwendbare Slider und Inspector-Controls. **[GEPLANT]**
- `Modules/Sources/NexaDesignSystem/NexaTypography.swift` - Textstile für beide Plattformen. **[GEPLANT]**
- `Modules/Sources/NexaEditor/AIPromptPanel.swift` - Text-/Bildprompt, Settings und Jobstatus. **[GEPLANT]**
- `Modules/Sources/NexaEditor/AssetBrowserView.swift` - Projektasset-Liste, Suchfilter und Thumbnails. **[GEPLANT]**
- `Modules/Sources/NexaEditor/ExportDialog.swift` - Exportformat, LOD und Qualitätsprüfungen. **[GEPLANT]**
- `Modules/Sources/NexaEditor/GenerationHistoryView.swift` - Vorherige KI-Jobs mit Provenienz. **[GEPLANT]**
- `Modules/Sources/NexaEditor/InspectorView.swift` - Eigenschaften des ausgewählten Elements. **[GEPLANT]**
- `Modules/Sources/NexaEditor/MaterialInspector.swift` - PBR-Oberflächen und Texturkanäle. **[GEPLANT]**
- `Modules/Sources/NexaEditor/NexaEditorRootView.swift` - Gemeinsames Editorlayout und erste UI. **[STARTER]**
- `Modules/Sources/NexaEditor/ProgressCenter.swift` - Laufende Jobs, Abbruch und Fehlerdetails. **[GEPLANT]**
- `Modules/Sources/NexaEditor/SceneHierarchyView.swift` - Szenengraph, Gruppierung und Selektion. **[GEPLANT]**
- `Modules/Sources/NexaEditor/TransformInspector.swift` - Numerische Position-/Rotation-/Scale-Eingaben. **[GEPLANT]**
- `Modules/Sources/NexaEditor/ViewportToolbar.swift` - Werkzeugauswahl und Anzeigeoptionen. **[GEPLANT]**
- `Modules/Sources/NexaEditor/WelcomeView.swift` - Vorlagen, Zuletzt geöffnet, Einstieg. **[GEPLANT]**

### Asset Import/Export, Baking und Delivery (14)

- `Modules/Sources/NexaAssetPipeline/AssetExporter.swift` - Mehrformatfähige Export-Registry und Feature-Matrix. **[GEPLANT]**
- `Modules/Sources/NexaAssetPipeline/AssetImporter.swift` - Sniffing statt blindem Vertrauen auf Endung. **[GEPLANT]**
- `Modules/Sources/NexaAssetPipeline/AssetProvenance.swift` - AI-Provider, Rechte, Lizenz, Ursprung und Version. **[GEPLANT]**
- `Modules/Sources/NexaAssetPipeline/AssetValidationLimits.swift` - Dateigrößen-, Vertex-, Texture- und Objektlimits. **[STARTER]**
- `Modules/Sources/NexaAssetPipeline/GLBWriter.swift` - glTF 2.0 Binärcontainer und korrekte Alignment-Regeln. **[GEPLANT]**
- `Modules/Sources/NexaAssetPipeline/GodotPreset.swift` - Export-Presets für Godot glTF 2.0. **[GEPLANT]**
- `Modules/Sources/NexaAssetPipeline/ImportSecurityPolicy.swift` - Untrusted Files, Pfade, ZIP-Bombs, Limits. **[GEPLANT]**
- `Modules/Sources/NexaAssetPipeline/MeshCompression.swift` - Quantisierung und optionale Meshopt/Draco Adapter. **[GEPLANT]**
- `Modules/Sources/NexaAssetPipeline/MeshLODGenerator.swift` - LOD Bake und Silhouettenerhalt. **[GEPLANT]**
- `Modules/Sources/NexaAssetPipeline/OBJWriter.swift` - OBJ+MTL Export für statische Meshes. **[GEPLANT]**
- `Modules/Sources/NexaAssetPipeline/TextureBakePipeline.swift` - Normal/AO/Curvature/ID Bake auf GPU/CPU. **[GEPLANT]**
- `Modules/Sources/NexaAssetPipeline/UnityPreset.swift` - Export-Presets für Unity Koordinaten/Normals/Texturen. **[GEPLANT]**
- `Modules/Sources/NexaAssetPipeline/UnrealPreset.swift` - Export-Presets für Unreal Einheit/Skinned-Limits. **[GEPLANT]**
- `Modules/Sources/NexaAssetPipeline/USDZPackageWriter.swift` - USDZ-Export über geprüfte USD APIs. **[GEPLANT]**

### Backend & GPU-Service (39)

- `Backend/.env.example` - Konfigurationsschlüssel ohne reale Secrets. **[STARTER]**
- `Backend/app/__init__.py` - Python-Paket-Initialisierung. **[STARTER]**
- `Backend/app/api/__init__.py` - API-Router-Paket. **[GEPLANT]**
- `Backend/app/api/account.py` - Profil, Datenexport und Account-Löschung. **[GEPLANT]**
- `Backend/app/api/billing.py` - Abo-Status und Credit-Kontingent. **[GEPLANT]**
- `Backend/app/api/downloads.py` - Geschützter Zugriff auf Generierungsergebnisse. **[GEPLANT]**
- `Backend/app/api/health.py` - Readiness und Liveness. **[GEPLANT]**
- `Backend/app/api/jobs.py` - Create/List/Get/Cancel der KI-Aufträge. **[GEPLANT]**
- `Backend/app/api/uploads.py` - Anfordern signierter Upload-URLs. **[GEPLANT]**
- `Backend/app/auth.py` - JWT-Prüfung und User-Scopes. **[GEPLANT]**
- `Backend/app/config.py` - Validierte Environment- und Secret-Konfiguration. **[GEPLANT]**
- `Backend/app/db.py` - Datenbankverbindung und Transaktionsmanagement. **[GEPLANT]**
- `Backend/app/errors.py` - Öffentliche Fehlercodes und strukturierte Fehler. **[GEPLANT]**
- `Backend/app/main.py` - FastAPI-Einstieg mit funktionsfähigem Health-Check. **[STARTER]**
- `Backend/app/models/__init__.py` - DB-Model-Paket. **[GEPLANT]**
- `Backend/app/models/asset.py` - Objektspeicher-Metadaten und TTL. **[GEPLANT]**
- `Backend/app/models/job.py` - Persistierte Jobs und Statusübergänge. **[GEPLANT]**
- `Backend/app/models/usage.py` - GPU-Minuten, Credits und Abuse-Limits. **[GEPLANT]**
- `Backend/app/models/user.py` - User, Consent und Account-Status. **[GEPLANT]**
- `Backend/app/services/job_service.py` - Job-Autorisierung und atomare Statuswechsel. **[GEPLANT]**
- `Backend/app/services/moderation_service.py` - Abuse-/Rechteprüfung in Prompts und Uploads. **[GEPLANT]**
- `Backend/app/services/provider_router.py` - Routing auf konkrete KI-Modelle. **[GEPLANT]**
- `Backend/app/services/quota_service.py` - Budget-Schutz und API-Limits. **[GEPLANT]**
- `Backend/app/services/storage_service.py` - Private Buckets und presigned URLs. **[GEPLANT]**
- `Backend/app/worker/__init__.py` - Jobworker-Paket. **[GEPLANT]**
- `Backend/app/worker/pipeline.py` - Text/Bild zu Mesh, Materials, Vorschau, QA. **[GEPLANT]**
- `Backend/app/worker/postprocess.py` - Mesh-Validierung, Zentrierung, LOD, Decimation. **[GEPLANT]**
- `Backend/app/worker/providers/base.py` - Provider-Interface für Modelle. **[GEPLANT]**
- `Backend/app/worker/providers/external_api.py` - Adapter für lizenzierten Drittanbieter. **[GEPLANT]**
- `Backend/app/worker/providers/self_hosted.py` - Adapter für selbst gehostetes Modell. **[GEPLANT]**
- `Backend/app/worker/runner.py` - GPU-Verarbeitungsprozess mit Job-Claiming. **[GEPLANT]**
- `Backend/compose.yaml` - Lokale API-, Postgres- und Redis-Entwicklungsumgebung. **[STARTER]**
- `Backend/Dockerfile` - Container-Build des API-Dienstes. **[STARTER]**
- `Backend/migrations/README.md` - Regeln für Alembic-/SQL-Schema-Migrationen. **[GEPLANT]**
- `Backend/pyproject.toml` - Python-Abhängigkeiten und Test-Konfiguration. **[STARTER]**
- `Backend/tests/test_health.py` - Smoke-Test des vorhandenen Health-Endpunkts. **[STARTER]**
- `Backend/tests/test_job_auth.py` - Geplante Tests gegen unautorisierte Jobaufrufe. **[GEPLANT]**
- `Backend/tests/test_jobs.py` - Geplante Job-State-Machine-Tests. **[GEPLANT]**
- `Backend/tests/test_quota.py` - Geplante Tests gegen unkontrollierte Kosten. **[GEPLANT]**

### Beispiele / Werkzeuge / Spezifikationen (4)

- `Examples/Cinematic/shotlist.json` - Examples/Cinematic/shotlist.json **[STARTER]**
- `Examples/Retopology/retopo-plan.json` - Examples/Retopology/retopo-plan.json **[STARTER]**
- `Examples/Rigging/minimal-rig.json` - Examples/Rigging/minimal-rig.json **[STARTER]**
- `Examples/VFX/sparks.json` - Examples/VFX/sparks.json **[STARTER]**

### CI und Tests (9)

- `.github/workflows/docs-status.yml` - CI prüft Dateimanifest, Dateiindex und README-Status. **[STARTER]**
- `Scripts/generate-file-index.py` - DATEIINDEX.md synchron aus JSON Manifest erzeugen. **[STARTER]**
- `Scripts/update-readme-status.py` - README Statussektion als überprüfbares Spiegelbild des Dateimanifests generieren. **[STARTER]**
- `Tests/Benchmarks/Scene100kBenchmarks.swift` - Szenen-Graph Performance und GPU-Memory auf Mac messen. **[GEPLANT]**
- `Tests/Benchmarks/TimelineDeterminismBenchmarks.swift` - Deterministische Offline-Frame-Auswertung. **[GEPLANT]**
- `Tests/Compatibility/AssetFixtures.md` - Rig/GLB/USDZ/EXR-Testassets mit Lizenzinfos. **[GEPLANT]**
- `Tests/Compatibility/DeviceMatrix.md` - GPU und Codec Capability-Matrix realer Apple-Geräte. **[GEPLANT]**
- `Tests/GoldenImages/PBR/README.md` - HDR/PBR Goldens pro Plattform, Toleranzen und Reviewregeln. **[GEPLANT]**
- `Tests/GoldenImages/RayTracing/README.md` - Reference-Images und fallback regression expectations. **[GEPLANT]**

### Dokumentation & Prozesse (13)

- `Docs/adr/0003-metal-render-graph.md` - ADR zur hybrid RealityKit/Metal Renderer-Architektur. **[DOKUMENTATION]**
- `Docs/adr/0004-cinematic-deterministic-frames.md` - ADR deterministische Framezeit und Offline Movie Jobs. **[DOKUMENTATION]**
- `Docs/adr/0005-geometry-topology-source.md` - ADR Geometry Kern bleibt Dateihoheit, nicht GPU Cache. **[DOKUMENTATION]**
- `Docs/adr/0006-ray-tracing-feature-gates.md` - ADR Hardware Capability-Gates und Raster-Fallback. **[DOKUMENTATION]**
- `Docs/FEATURE_STATUS.md` - Feature-Matrix mit ehrlicher Abgrenzung Starter vs produktive Funktionen. **[DOKUMENTATION]**
- `Docs/GITHUB_BETRIEB.md` - Pflegeprozess für README, Statusindex, Release Notes und PR Reviews. **[DOKUMENTATION]**
- `Docs/PDF/01_Nexa3D_Entwicklungsplan.pdf` - PDF Hauptbauplan, Architektur, Meilensteine und Scope. **[DOKUMENTATION]**
- `Docs/PDF/02_Nexa3D_Technische_Architektur.pdf` - PDF Metal/RenderGraph, Rigging, Retopo, VFX, RT und Video Pipeline. **[DOKUMENTATION]**
- `Docs/PDF/03_Nexa3D_Roadmap_und_Tests.pdf` - PDF M0-M10 Abnahmekriterien und technische Testmatrix. **[DOKUMENTATION]**
- `Docs/PDF/04_Nexa3D_Datei_und_Ordnerkatalog.pdf` - PDF Einzeldateikatalog für vollständige Struktur. **[DOKUMENTATION]**
- `Docs/PDF/05_Nexa3D_GitHub_und_Status.pdf` - PDF GitHub README Pflicht und Feature-Status. **[DOKUMENTATION]**
- `Docs/ROADMAP_ABNAHME.md` - Meilensteine M0-M10 mit messbaren Abnahmekriterien, Tests und Gerätefaktoren. **[DOKUMENTATION]**
- `Docs/TECHNISCHE_ARCHITEKTUR.md` - Technische Engine-Spezifikation zu ECS, RenderGraph, GPU/PBR, Cinema, VFX, Retopo, Rigging und RT. **[DOKUMENTATION]**

### Dokumentation & Quellreferenz (1)

- `Docs/reference/XCODE_ENGINE_ARCHITECTURE_REFERENCE.txt` - Vom Benutzer eingereichte Naming-/Systemreferenz, unverändert übernommen. **[REFERENZ]**

### Dokumente & lokale Daten (8)

- `Modules/Sources/NexaDocuments/AutosaveCoordinator.swift` - Autosave/Checkpoint-Abstimmung, Fehlerbehandlung. **[GEPLANT]**
- `Modules/Sources/NexaDocuments/FileAccessScope.swift` - Security-scoped Ressourcen auf macOS/iOS. **[GEPLANT]**
- `Modules/Sources/NexaDocuments/NexaProjectDocument.swift` - Versioniertes Projektpaket mit Manifestprüfung und Erhalt zusätzlicher Dateien. **[STARTER]**
- `Modules/Sources/NexaDocuments/PackageValidator.swift` - Prüfen von Dateigrößen, Pfaden und Dateiintegrität. **[GEPLANT]**
- `Modules/Sources/NexaDocuments/ProjectManifest.swift` - Manifest mit Schemaversion, Zeitstempeln und Inhalt. **[GEPLANT]**
- `Modules/Sources/NexaDocuments/ProjectMigration.swift` - Aufwärtsmigration älterer Projektschemata. **[GEPLANT]**
- `Modules/Sources/NexaDocuments/ProjectThumbnail.swift` - Vorschaubild und Quick-Look-Metadaten. **[GEPLANT]**
- `Modules/Sources/NexaDocuments/ProjectType.swift` - Registrierung des benutzerdefinierten UTType. **[STARTER]**

### Engine / Loop / GPU-Integration (9)

- `Modules/Sources/NexaEngine/DisplayLinkDriver.swift` - CADisplayLink für iOS und CVDisplayLink/Display-Link-Adapter für macOS. **[GEPLANT]**
- `Modules/Sources/NexaEngine/EngineClock.swift` - Monotone Zeitbasis, Pausieren, Zeit-Skalierung und Framelimit. **[GEPLANT]**
- `Modules/Sources/NexaEngine/EngineEventBus.swift` - Typisierte Events ohne globale Singleton-Abhängigkeit. **[GEPLANT]**
- `Modules/Sources/NexaEngine/FixedUpdateSystem.swift` - Schnittstelle für deterministische Fixed-Update-Logik. **[GEPLANT]**
- `Modules/Sources/NexaEngine/FrameProfiler.swift` - CPU/GPU Framezeit, Moving Average, Trace-ID und Signposts. **[GEPLANT]**
- `Modules/Sources/NexaEngine/FrameScheduler.swift` - Testbarer Fixed-Step-Akkumulator ohne hardcodierte 60-FPS-Annahme. **[STARTER]**
- `Modules/Sources/NexaEngine/GameLoop.swift` - Fixierter Physik-Takt, variabler Render-Takt und deterministische Simulation. **[GEPLANT]**
- `Modules/Sources/NexaEngine/LateUpdateSystem.swift` - Animation -> Kinematik -> Kamera in definierter Reihenfolge. **[GEPLANT]**
- `Modules/Sources/NexaEngine/SceneRuntime.swift` - Abbildung einer bearbeitbaren Szene auf Laufzeitsysteme. **[GEPLANT]**

### Entity-Component-System (18)

- `Modules/Sources/NexaECS/AnimationComponent.swift` - Verweis auf Clip, Rig und aktive Layer. **[GEPLANT]**
- `Modules/Sources/NexaECS/AudioComponent.swift` - Räumlicher Audio-Clip mit Doppler- und Distanzparametern. **[GEPLANT]**
- `Modules/Sources/NexaECS/AudioSystem.swift` - Räumliche Audio-Updates nach Kameraposition. **[GEPLANT]**
- `Modules/Sources/NexaECS/CameraComponent.swift` - FOV, Near/Far, optische Brennweite, Apertur. **[GEPLANT]**
- `Modules/Sources/NexaECS/ComponentDescriptor.swift` - Komponentenreferenzen und serialisierbare Konfigurationen. **[GEPLANT]**
- `Modules/Sources/NexaECS/ComponentKind.swift` - Bekannte Komponentenarten als versionierbare Identifikatoren. **[STARTER]**
- `Modules/Sources/NexaECS/EntityID.swift` - Plattformneutrale stabile Entity-ID (UUID). **[STARTER]**
- `Modules/Sources/NexaECS/EntityRegistry.swift` - Effiziente Registrierung von Entities und Komponenten. **[GEPLANT]**
- `Modules/Sources/NexaECS/LightComponent.swift` - Lichttyp, Intensität, Temperatur und Schattenparameter. **[GEPLANT]**
- `Modules/Sources/NexaECS/MaterialComponent.swift` - PBR-Materialverknüpfung pro Submesh. **[GEPLANT]**
- `Modules/Sources/NexaECS/MeshComponent.swift` - Referenzierte Mesh-Daten und LOD-Auswahl. **[GEPLANT]**
- `Modules/Sources/NexaECS/MovementSystem.swift` - Integrationsschritt für Positionsänderungen. **[GEPLANT]**
- `Modules/Sources/NexaECS/PhysicsBodyComponent.swift` - Physikkörper, Layer und Kollisionsmaske. **[GEPLANT]**
- `Modules/Sources/NexaECS/PhysicsSystem.swift` - Physik-Adapter für Kollisionen und Gravity. **[GEPLANT]**
- `Modules/Sources/NexaECS/RenderSystem.swift` - Sichtbarkeit und Draw-List-Erzeugung. **[GEPLANT]**
- `Modules/Sources/NexaECS/SystemScheduler.swift` - Korrekte Update-Reihenfolge für Movement, Physics, Animation, Render, Audio. **[GEPLANT]**
- `Modules/Sources/NexaECS/TransformComponent.swift` - Komponente für Transform und Parent-Beziehung. **[GEPLANT]**
- `Modules/Sources/NexaECS/VFXComponent.swift` - Partikelemitter und VFX-Graph-Referenz. **[GEPLANT]**

### iOS-/iPadOS-App (10)

- `Apps/NexaMobile/FilesImportController.swift` - Import über Dateien-App und Share Sheet. **[GEPLANT]**
- `Apps/NexaMobile/Info.plist` - Bundle- und Dokumentkonfiguration auf Mobilgeräten. **[STARTER]**
- `Apps/NexaMobile/iPadWorkspace.swift` - iPad-Layout mit Seitenleisten und Inspektor. **[GEPLANT]**
- `Apps/NexaMobile/iPhoneWorkspace.swift` - iPhone-Layout mit vereinfachten Werkzeugen. **[GEPLANT]**
- `Apps/NexaMobile/MobileToolbar.swift` - Kompakte Werkzeugleiste für iPhone/iPad. **[GEPLANT]**
- `Apps/NexaMobile/NexaMobileApp.swift` - iOS- und iPadOS-Einstiegspunkt zum selben Dokumentformat. **[STARTER]**
- `Apps/NexaMobile/PencilInteraction.swift` - Apple-Pencil-Eingaben, sofern verfügbar. **[GEPLANT]**
- `Apps/NexaMobile/Resources/Assets.xcassets/AppIcon.appiconset/Contents.json` - App-Icon-Metadaten für iOS. **[STARTER]**
- `Apps/NexaMobile/Resources/Assets.xcassets/Contents.json` - Mobiler Asset-Katalog. **[STARTER]**
- `Apps/NexaMobile/TouchGestureRouter.swift` - Pinch-, Orbit-, Pan- und Tap-Gesten. **[GEPLANT]**

### KI, Import/Export & Infrastruktur (22)

- `Modules/Sources/NexaAIClient/AIClient.swift` - HTTP-Klient für die eigene Server-API. **[GEPLANT]**
- `Modules/Sources/NexaAIClient/GenerationJob.swift` - Jobstatus, Fortschritt und Ergebnis-URLs. **[GEPLANT]**
- `Modules/Sources/NexaAIClient/GenerationProvider.swift` - Austauschbare AI-Provider-Schnittstelle. **[GEPLANT]**
- `Modules/Sources/NexaAIClient/GenerationRequest.swift` - Typisierte KI-Parameter inklusive Seed und Qualität. **[GEPLANT]**
- `Modules/Sources/NexaAIClient/JobPolling.swift` - Backoff und Statusabfragen. **[GEPLANT]**
- `Modules/Sources/NexaAIClient/PromptSafety.swift` - Prompt-Vorvalidierung und Hinweise. **[GEPLANT]**
- `Modules/Sources/NexaAIClient/UploadClient.swift` - Signierte Uploads, Wiederaufnahme, Prüfsumme. **[GEPLANT]**
- `Modules/Sources/NexaExport/AssetValidationReport.swift` - Game-Ready-Check vor Export. **[GEPLANT]**
- `Modules/Sources/NexaExport/ExportFormat.swift` - Formate, Fähigkeiten und Verfügbarkeit. **[GEPLANT]**
- `Modules/Sources/NexaExport/GLTFExporter.swift` - Validierter glTF-/GLB-Export über separaten Konverter. **[GEPLANT]**
- `Modules/Sources/NexaExport/LODPipeline.swift` - LOD-Gruppen und Triangulation. **[GEPLANT]**
- `Modules/Sources/NexaExport/OBJExporter.swift` - OBJ mit Geometrie und Materialreferenzen. **[GEPLANT]**
- `Modules/Sources/NexaExport/TexturePacker.swift` - Materialtexturen bündeln und kanalmappen. **[GEPLANT]**
- `Modules/Sources/NexaExport/USDExporter.swift` - USD/USDZ-Pipeline mit Materialprüfung. **[GEPLANT]**
- `Modules/Sources/NexaInfrastructure/APIEnvironment.swift` - Server-URLs und Environment-Auswahl. **[GEPLANT]**
- `Modules/Sources/NexaInfrastructure/AuthSession.swift` - Authentifizierungszustand und Token-Rotation. **[GEPLANT]**
- `Modules/Sources/NexaInfrastructure/CacheManager.swift` - Bereinigung temporärer 3D-/KI-Dateien. **[GEPLANT]**
- `Modules/Sources/NexaInfrastructure/FeatureFlags.swift` - Kontrollierte Freischaltung neuer Funktionen. **[GEPLANT]**
- `Modules/Sources/NexaInfrastructure/KeychainStore.swift` - Sichere Ablage von Tokens. **[GEPLANT]**
- `Modules/Sources/NexaInfrastructure/NetworkMonitor.swift` - Offline-/Online-Erkennung. **[GEPLANT]**
- `Modules/Sources/NexaInfrastructure/SubscriptionStore.swift` - StoreKit und Rechte-Prüfung. **[GEPLANT]**
- `Modules/Sources/NexaInfrastructure/Telemetry.swift` - Opt-in-Fehlertelemetrie ohne private Prompts. **[GEPLANT]**

### macOS-App (10)

- `Apps/NexaMac/AppCommands.swift` - Menüleiste, Tastaturkürzel und Befehle. **[GEPLANT]**
- `Apps/NexaMac/Info.plist` - App- und Dateityp-Registrierung für macOS. **[STARTER]**
- `Apps/NexaMac/MacDropHandler.swift` - Drag-and-drop für Assets aus Finder. **[GEPLANT]**
- `Apps/NexaMac/MacKeyboardShortcuts.swift` - Professionelle Tastaturbelegung. **[GEPLANT]**
- `Apps/NexaMac/MacToolbar.swift` - macOS-spezifische Werkzeugleiste. **[GEPLANT]**
- `Apps/NexaMac/NexaMac.entitlements` - App Sandbox, Benutzerdateien und Netzwerkberechtigung. **[STARTER]**
- `Apps/NexaMac/NexaMacApp.swift` - macOS-Einstiegspunkt und SwiftUI-Dokumentfenster. **[STARTER]**
- `Apps/NexaMac/Resources/Assets.xcassets/AppIcon.appiconset/Contents.json` - Metadaten für spätere App-Icon-Dateien. **[STARTER]**
- `Apps/NexaMac/Resources/Assets.xcassets/Contents.json` - Mac-Asset-Katalog. **[STARTER]**
- `Apps/NexaMac/WindowManagement.swift` - Mehrfenster- und Inspektor-Verwaltung. **[GEPLANT]**

### Metal GPU Render-Graph & PBR (32)

- `Modules/Sources/NexaRenderGraph/CascadedShadowMaps.swift` - Cascaded Shadow Maps für Sonnenlicht. **[GEPLANT]**
- `Modules/Sources/NexaRenderGraph/CommandBuffer.swift` - GPU-Frame-Lebenszyklus mit Fehlerdiagnostik. **[GEPLANT]**
- `Modules/Sources/NexaRenderGraph/CommandQueue.swift` - Kapselung von MTLCommandQueue und Latenzprofiling. **[GEPLANT]**
- `Modules/Sources/NexaRenderGraph/ComputeCommandEncoder.swift` - Compute-Passes für Skinning, Partikel und PostFX. **[GEPLANT]**
- `Modules/Sources/NexaRenderGraph/ComputePipelineStateCache.swift` - Compute Pipeline Caching pro Funktion/Feature-Set. **[GEPLANT]**
- `Modules/Sources/NexaRenderGraph/DepthStencilStateCache.swift` - Depth-/Stencil-Varianten. **[GEPLANT]**
- `Modules/Sources/NexaRenderGraph/FrustumCulling.swift` - Sichtbarkeitsprüfung über Frustum und Bounds. **[GEPLANT]**
- `Modules/Sources/NexaRenderGraph/GPUCapabilities.swift` - GPU-Fähigkeiten pro Gerät erkennen und dokumentiert begrenzen. **[GEPLANT]**
- `Modules/Sources/NexaRenderGraph/HDRColorPipeline.swift` - Linear HDR, Exposure, SDR/HDR Ausgabe. **[GEPLANT]**
- `Modules/Sources/NexaRenderGraph/IBLPrecompute.swift` - HDR-Probe, BRDF LUT und Mip-Prefilter. **[GEPLANT]**
- `Modules/Sources/NexaRenderGraph/IndexBuffer.swift` - Index Stream Upload und Submesh-Sortierung. **[GEPLANT]**
- `Modules/Sources/NexaRenderGraph/InstancedRendering.swift` - Instanzierung statischer oder gleichartiger Meshes. **[GEPLANT]**
- `Modules/Sources/NexaRenderGraph/LODManager.swift` - Bildschirmfehler und LOD-Hysterese. **[GEPLANT]**
- `Modules/Sources/NexaRenderGraph/MetalFXUpscaler.swift` - Spatial / Temporal Upscaling mit Capability-Fallback. **[GEPLANT]**
- `Modules/Sources/NexaRenderGraph/PBRMaterial.swift` - PBR Texturslots BaseColor/Normal/Metallic/Roughness/AO/Emissive. **[GEPLANT]**
- `Modules/Sources/NexaRenderGraph/RenderCommandEncoder.swift` - Draw-Befehle und Zustandswechsel. **[GEPLANT]**
- `Modules/Sources/NexaRenderGraph/RenderFrame.swift` - Unveränderlicher Snapshot für GPU-Frames. **[GEPLANT]**
- `Modules/Sources/NexaRenderGraph/RenderGraph.swift` - Renderpass-DAG mit Ressourcenabhängigkeiten und Barrieren. **[GEPLANT]**
- `Modules/Sources/NexaRenderGraph/RenderPassNode.swift` - Einzelner Draw/Compute/Blit-Pass inklusive Inputs/Outputs. **[GEPLANT]**
- `Modules/Sources/NexaRenderGraph/RenderPipelineStateCache.swift` - MTLRenderPipelineState-Caching nach Shader-Features. **[GEPLANT]**
- `Modules/Sources/NexaRenderGraph/ResourceManager.swift` - CPU/GPU Ressourcencache, Budgets und Eviction. **[GEPLANT]**
- `Modules/Sources/NexaRenderGraph/SamplerStateCache.swift` - Texture-Sampler und anisotrope Filterung. **[GEPLANT]**
- `Modules/Sources/NexaRenderGraph/Shaders/BRDFIntegrate.metal` - Precompute BRDF Integrations-LUT. **[GEPLANT]**
- `Modules/Sources/NexaRenderGraph/Shaders/PBRFragment.metal` - GGX BRDF mit Fresnel/Geometrie-Term und IBL. **[GEPLANT]**
- `Modules/Sources/NexaRenderGraph/Shaders/PBRVertex.metal` - PBR Vertices, Tangentenraum und Skinned Geometry. **[GEPLANT]**
- `Modules/Sources/NexaRenderGraph/Shaders/ShadowDepth.metal` - Schatten-Depth-only Pass. **[GEPLANT]**
- `Modules/Sources/NexaRenderGraph/Shaders/SkinningCompute.metal` - GPU Joint-Influence Skinning. **[GEPLANT]**
- `Modules/Sources/NexaRenderGraph/ShadowMapping.swift` - Schattenkarten als eigener Renderpass. **[GEPLANT]**
- `Modules/Sources/NexaRenderGraph/TextureLoader.swift` - MTKTextureLoader und validierte Farbprofile. **[GEPLANT]**
- `Modules/Sources/NexaRenderGraph/TransientTexturePool.swift` - Temporäre GPU-Texturen und Lebensdaueranalyse. **[GEPLANT]**
- `Modules/Sources/NexaRenderGraph/UniformBuffer.swift` - Per-Frame Konstantenring und Alignment. **[GEPLANT]**
- `Modules/Sources/NexaRenderGraph/VertexBuffer.swift` - GPU Vertex Streams und Staging Upload. **[GEPLANT]**

### Plattform & professionelle UI (14)

- `Apps/NexaMac/MacRetopoLayout.swift` - Desktop Retopo-Workspace, Brush-Shortcuts und UV-Panels. **[GEPLANT]**
- `Apps/NexaMac/MacRiggingLayout.swift` - Rigging-Workspace mit Joint-Outliner und Weight Paint. **[GEPLANT]**
- `Apps/NexaMac/MacSequencerLayout.swift` - 3-Panel-Cinematic-Workspace mit Timeline am unteren Rand. **[GEPLANT]**
- `Apps/NexaMobile/iPadSequencerWorkspace.swift` - Touch/Pencil Sequencer mit Video Scrubbing. **[GEPLANT]**
- `Apps/NexaMobile/iPadVFXWorkspace.swift` - VFX Preview und Emitterparameter für iPad. **[GEPLANT]**
- `Apps/NexaMobile/MobilePerformanceProfiles.swift` - Thermal State, RAM, Gerätekompatibilität und Scaling. **[GEPLANT]**
- `Modules/Sources/NexaEditor/CinematicTimelinePanel.swift` - Frames, Keyframes, Shot-Track und Audiowaveform. **[GEPLANT]**
- `Modules/Sources/NexaEditor/GPUSettingsView.swift` - Raytracing, Upscaling, Shaderqualität und Renderer-Profile. **[GEPLANT]**
- `Modules/Sources/NexaEditor/PostProcessingInspector.swift` - PostFX-Stack und Color Grading. **[GEPLANT]**
- `Modules/Sources/NexaEditor/RetopologyInspector.swift` - Zielbudget, Quality Report und Surface Snapping. **[GEPLANT]**
- `Modules/Sources/NexaEditor/RiggingInspector.swift` - Bone-Eigenschaften, Constraints, Weight Maps. **[GEPLANT]**
- `Modules/Sources/NexaEditor/VFXInspector.swift` - Emission, Lifetime, Turbulence und Playback. **[GEPLANT]**
- `Modules/Sources/NexaEditor/VideoExportPanel.swift` - Videoauflösung, Codec, Queue und Frame-Range. **[GEPLANT]**
- `Modules/Sources/NexaEditor/WorkspacePicker.swift` - Studio-, Retopo-, Rigging-, VFX- und Cinematic-Ansichten umschalten. **[GEPLANT]**

### Post-FX und Compositing (22)

- `Modules/Sources/NexaCompositing/BloomPass.swift` - HDR-Threshold, Downsample und Upsample. **[GEPLANT]**
- `Modules/Sources/NexaCompositing/ColorGradingPass.swift` - 3D LUT, Primaries, Log/Linear Farben. **[GEPLANT]**
- `Modules/Sources/NexaCompositing/ColorManagement.swift` - sRGB/Display-P3/HDR-Transfer und Farbkonvertierungen. **[GEPLANT]**
- `Modules/Sources/NexaCompositing/ColorPipelineSettings.swift` - Validierte Parameter für Exposure/Bloom/Tonemapping. **[STARTER]**
- `Modules/Sources/NexaCompositing/Compositor.swift` - Layer, Z-Order, Masks, Premultiplied Alpha und Blendmode. **[GEPLANT]**
- `Modules/Sources/NexaCompositing/DepthOfFieldPass.swift` - Circle-of-confusion und bokeh sample budget. **[GEPLANT]**
- `Modules/Sources/NexaCompositing/EXRImageWriter.swift` - HDR/EXR Export nur über geprüften Codec/Library. **[GEPLANT]**
- `Modules/Sources/NexaCompositing/FilmGrainPass.swift` - Film Grain, reproduzierbarer Seed. **[GEPLANT]**
- `Modules/Sources/NexaCompositing/HBAOPass.swift` - Horizon Based Ambient Occlusion. **[GEPLANT]**
- `Modules/Sources/NexaCompositing/LensDistortionPass.swift` - Camera Lens Distortion. **[GEPLANT]**
- `Modules/Sources/NexaCompositing/MotionBlurPass.swift` - Velocity Buffer und Kamera-/Objekt-Blurring. **[GEPLANT]**
- `Modules/Sources/NexaCompositing/PostEffectsInspector.swift` - Eigenschaften und Live-Vorschau von Effects. **[GEPLANT]**
- `Modules/Sources/NexaCompositing/PostProcessingGraph.swift` - Knoten-DAG mit Masken, Inputs und Renderpassplanung. **[GEPLANT]**
- `Modules/Sources/NexaCompositing/Shaders/Bloom.metal` - Bloom/HDR Downsample/Upsample. **[GEPLANT]**
- `Modules/Sources/NexaCompositing/Shaders/DoF.metal` - DoF mit CoC. **[GEPLANT]**
- `Modules/Sources/NexaCompositing/Shaders/MotionBlur.metal` - Velocity Pass Rekonstruktion. **[GEPLANT]**
- `Modules/Sources/NexaCompositing/Shaders/SSAO.metal` - SSAO Sampling Kernel. **[GEPLANT]**
- `Modules/Sources/NexaCompositing/Shaders/ToneMap.metal` - ToneMap und Output-Transfer. **[GEPLANT]**
- `Modules/Sources/NexaCompositing/SSAOPass.swift` - Screen-Space Ambient Occlusion. **[GEPLANT]**
- `Modules/Sources/NexaCompositing/TemporalAAPass.swift` - TAA mit Motion Vector und History Rejection. **[GEPLANT]**
- `Modules/Sources/NexaCompositing/ToneMappingPass.swift` - ACES/Reinhard + Exposition in linearer Pipeline. **[GEPLANT]**
- `Modules/Sources/NexaCompositing/VignettePass.swift` - Vignette und Lens-FX. **[GEPLANT]**

### Projektsteuerung & Konfiguration (14)

- `.editorconfig` - Zeilenenden und Einrückung vereinheitlichen. **[STARTER]**
- `.gitignore` - Build-Artefakte, temporäre Dateien und Secrets ausschließen. **[STARTER]**
- `.swiftlint.yml` - Optionale Swift-Linting-Regeln. **[STARTER]**
- `CHANGELOG.md` - Nachvollziehbare Änderungen je Version. **[DOKUMENTATION]**
- `CONTRIBUTING.md` - Code-Stil, Pull-Request-Regeln und Review-Prozess. **[DOKUMENTATION]**
- `DATEIINDEX.md` - Jede geplante Datei mit Einzelverantwortung und Status. **[DOKUMENTATION]**
- `DATEIMANIFEST.json` - Maschinenlesbare Liste aller einzeln beschriebenen geplanten und vorhandenen Dateien. **[STARTER]**
- `ENTWICKLUNGSPLAN.md` - Gesamtplan mit Architektur, Phasen, Datenmodell und Abnahmekriterien. **[DOKUMENTATION]**
- `LICENSE-DECISIONS.md` - Entscheidungen zu Lizenzen von Modellen, Libraries und Assets. **[GEPLANT]**
- `LocalConfig.example.xcconfig` - Vorlage für lokale, nicht vertrauliche Xcode-Einstellungen. **[STARTER]**
- `Makefile` - Kommandos zur Projektgenerierung und Testausführung. **[STARTER]**
- `project.yml` - XcodeGen-Spezifikation für beide App-Targets. **[STARTER]**
- `README.md` - Startseite, Entwicklungsstatus und Quickstart. **[DOKUMENTATION]**
- `SECURITY.md` - Meldung und Behandlung von Sicherheitsproblemen. **[GEPLANT]**

### Ray-Tracing & Path-Tracing (12)

- `Modules/Sources/NexaRayTracing/AccelerationStructureBuilder.swift` - BLAS/TLAS mit Update/Refit und Build-Budgets. **[GEPLANT]**
- `Modules/Sources/NexaRayTracing/Denoiser.swift` - Temporaler/spatial Denoiser und Ghosting-Checks. **[GEPLANT]**
- `Modules/Sources/NexaRayTracing/PathTracer.swift` - Progressives Multi-Bounce Path-Tracing für Offline-Standbilder. **[GEPLANT]**
- `Modules/Sources/NexaRayTracing/RayTracedReflections.swift` - Reflections und Ray Reprojection. **[GEPLANT]**
- `Modules/Sources/NexaRayTracing/RayTracedShadows.swift` - Soft Shadows über Stochastic Rays. **[GEPLANT]**
- `Modules/Sources/NexaRayTracing/RayTracingCapabilities.swift` - MTLDevice.supportsRaytracing abfragen und als Profil veröffentlichen. **[STARTER]**
- `Modules/Sources/NexaRayTracing/RayTracingFallback.swift` - Raster/Screenspace/IBL Fallback ohne hartes Hardwareversprechen. **[GEPLANT]**
- `Modules/Sources/NexaRayTracing/RayTracingRenderer.swift` - Raygen, Intersections, Shadow / Reflection Rays. **[GEPLANT]**
- `Modules/Sources/NexaRayTracing/RayTracingScene.swift` - Instanzen, Geometrieindices und Material-Lookup. **[GEPLANT]**
- `Modules/Sources/NexaRayTracing/RayTracingStatistics.swift` - Ray Budget, AS Buildzeiten und Quality Gates. **[GEPLANT]**
- `Modules/Sources/NexaRayTracing/Shaders/PathTrace.metal` - Monte Carlo Integration und RNG. **[GEPLANT]**
- `Modules/Sources/NexaRayTracing/Shaders/RayTrace.metal` - Intersection- und Radiance-Shading. **[GEPLANT]**

### Retopologie & Mesh-Aufbereitung (13)

- `Modules/Sources/NexaRetopology/AutomaticRetopologizer.swift` - Automatische Quad-Retopologie über separaten Solver. **[GEPLANT]**
- `Modules/Sources/NexaRetopology/EdgeLoopTool.swift` - Kontinuierliche Edge-Loops für Deformationsbereiche. **[GEPLANT]**
- `Modules/Sources/NexaRetopology/FeaturePreservation.swift` - Harte Kanten, Silhouetten und anatomische Guides. **[GEPLANT]**
- `Modules/Sources/NexaRetopology/NormalBakeService.swift` - Highpoly-auf-Lowpoly Normal- und AO-Baking. **[GEPLANT]**
- `Modules/Sources/NexaRetopology/PolyBuildTool.swift` - Manuelles Quad-Zeichnen auf Highpoly-Oberflächen. **[GEPLANT]**
- `Modules/Sources/NexaRetopology/QuadFlowSolver.swift` - Quad-Orientierung mit anisotropen Edge-Fields. **[GEPLANT]**
- `Modules/Sources/NexaRetopology/RetopoBrush.swift` - Brush für Surface-Snapping und Guide-Curves. **[GEPLANT]**
- `Modules/Sources/NexaRetopology/RetopologyPlan.swift` - Parametervalidierung für Topologie-Zielbudget. **[STARTER]**
- `Modules/Sources/NexaRetopology/RetopoQualityReport.swift` - Valenzverteilung, Pole, Self-Intersections und Meshchecks. **[GEPLANT]**
- `Modules/Sources/NexaRetopology/RetopoSession.swift` - Highpoly-Referenz, Lowpoly-Ziel, Modus und History. **[GEPLANT]**
- `Modules/Sources/NexaRetopology/RetopoWorkspaceView.swift` - Separate Retopologie-Oberfläche und Poly-Build-Modus. **[GEPLANT]**
- `Modules/Sources/NexaRetopology/SurfaceSnapper.swift` - Project-onto-surface mit BVH, Offset und Toleranzen. **[GEPLANT]**
- `Modules/Sources/NexaRetopology/UVProjectionTransfer.swift` - Transfer von UV und Vertex Colors. **[GEPLANT]**

### Rigging, Skinning, Animation (14)

- `Modules/Sources/NexaRigging/BlendShape.swift` - Morph Targets für Gesicht und Expressions. **[GEPLANT]**
- `Modules/Sources/NexaRigging/Bone.swift` - Bone-IDs, Elternreferenz und Rest-Pose. **[GEPLANT]**
- `Modules/Sources/NexaRigging/ForwardKinematics.swift` - Welttransforms und Hierarchieauswertung. **[GEPLANT]**
- `Modules/Sources/NexaRigging/GPUDeformer.swift` - GPU-Skinning und Morph Blending mit CPU-Fallback. **[GEPLANT]**
- `Modules/Sources/NexaRigging/InverseKinematicsSolver.swift` - IK-Ketten mit deterministischen Convergence-Limits. **[GEPLANT]**
- `Modules/Sources/NexaRigging/JointConstraint.swift` - Grenzen für IK/Rotation/Translation. **[GEPLANT]**
- `Modules/Sources/NexaRigging/PoseLibrary.swift` - Benannte Posen und Pose-Blending. **[GEPLANT]**
- `Modules/Sources/NexaRigging/RetargetingService.swift` - Mapping zwischen Skeletons mit Skalierungs- und Root-Motion-Regeln. **[GEPLANT]**
- `Modules/Sources/NexaRigging/RigDefinition.swift` - Skelett-Bones und Parenting mit überprüfbaren Invarianten. **[STARTER]**
- `Modules/Sources/NexaRigging/RiggingWorkspaceView.swift` - Bone/Weights/UI und Overlay. **[GEPLANT]**
- `Modules/Sources/NexaRigging/SkeletonEditor.swift` - Bone erstellen, parenten, symmetrieren. **[GEPLANT]**
- `Modules/Sources/NexaRigging/SkeletonValidator.swift` - Zyklentest, eindeutige Bone-IDs und Referenzvalidierung. **[STARTER]**
- `Modules/Sources/NexaRigging/SkinWeight.swift` - Gewichtseinschränkungen pro Vertex und Normalisierung. **[GEPLANT]**
- `Modules/Sources/NexaRigging/SkinWeightPainter.swift` - Weights malen, glätten, spiegeln und normalisieren. **[GEPLANT]**

### Swift Tests (9)

- `Modules/Tests/NexaAnimationTests/NexaAnimationSmokeTests.swift` - Smoke-/Vertragstests für NexaAnimation. **[STARTER]**
- `Modules/Tests/NexaAssetPipelineTests/NexaAssetPipelineSmokeTests.swift` - Smoke-/Vertragstests für NexaAssetPipeline. **[STARTER]**
- `Modules/Tests/NexaCinematicsTests/NexaCinematicsSmokeTests.swift` - Smoke-/Vertragstests für NexaCinematics. **[STARTER]**
- `Modules/Tests/NexaCompositingTests/NexaCompositingSmokeTests.swift` - Smoke-/Vertragstests für NexaCompositing. **[STARTER]**
- `Modules/Tests/NexaEngineTests/NexaEngineSmokeTests.swift` - Smoke-/Vertragstests für NexaEngine. **[STARTER]**
- `Modules/Tests/NexaRayTracingTests/NexaRayTracingSmokeTests.swift` - Smoke-/Vertragstests für NexaRayTracing. **[STARTER]**
- `Modules/Tests/NexaRetopologyTests/NexaRetopologySmokeTests.swift` - Smoke-/Vertragstests für NexaRetopology. **[STARTER]**
- `Modules/Tests/NexaRiggingTests/NexaRiggingSmokeTests.swift` - Smoke-/Vertragstests für NexaRigging. **[STARTER]**
- `Modules/Tests/NexaVFXTests/NexaVFXSmokeTests.swift` - Smoke-/Vertragstests für NexaVFX. **[STARTER]**

### Swift-Package & Domain (16)

- `Modules/Package.swift` - SwiftPM-Module; geplante Shaderordner bis zur Rendererimplementierung vom Build ausgeschlossen. **[STARTER]**
- `Modules/Sources/NexaDomain/AnimationClip.swift` - Keyframes und spätere Animationsclips. **[GEPLANT]**
- `Modules/Sources/NexaDomain/AssetMetadata.swift` - Einheiten, Ursprung, Lizenzen, Ersteller und Hashes. **[GEPLANT]**
- `Modules/Sources/NexaDomain/CameraNode.swift` - Kamera-Projektion und Kameraeigenschaften. **[GEPLANT]**
- `Modules/Sources/NexaDomain/EditorCommand.swift` - Undo-fähige Domain-Kommandos als Typen. **[GEPLANT]**
- `Modules/Sources/NexaDomain/LightNode.swift` - Lichtquellen und physikalische Intensitäten. **[GEPLANT]**
- `Modules/Sources/NexaDomain/MaterialAsset.swift` - PBR-Materialmodell und Textur-Slots. **[GEPLANT]**
- `Modules/Sources/NexaDomain/MeshAsset.swift` - Geometrie-Referenzen, Vertex-/Index-Metadaten. **[GEPLANT]**
- `Modules/Sources/NexaDomain/NexaScene.swift` - Versionsfähiges, plattformneutrales Szenenmodell. **[STARTER]**
- `Modules/Sources/NexaDomain/PrimitiveKind.swift` - Vordefinierte Primitive und deren Typen. **[STARTER]**
- `Modules/Sources/NexaDomain/ProjectError.swift` - Fehlertypen mit benutzerverständlichen Codes. **[GEPLANT]**
- `Modules/Sources/NexaDomain/RigSkeleton.swift` - Skelettdefinition als spätere Profi-Funktion. **[GEPLANT]**
- `Modules/Sources/NexaDomain/SceneNode.swift` - Hierarchischer Szenenknoten mit stabiler UUID. **[STARTER]**
- `Modules/Sources/NexaDomain/SelectionState.swift` - Aktuelle Objekt- und Komponenten-Selektion. **[GEPLANT]**
- `Modules/Sources/NexaDomain/TextureAsset.swift` - Textur-Metadaten, Farbprofil und Kanalzuordnung. **[GEPLANT]**
- `Modules/Sources/NexaDomain/TransformData.swift` - Position, Rotation und Skalierung, serialisierbar. **[STARTER]**

### Timeline, Kurven und Sequencer (12)

- `Modules/Sources/NexaAnimation/AnimationLayers.swift` - Blended Animationslayer und Masking. **[GEPLANT]**
- `Modules/Sources/NexaAnimation/AnimationRetargeter.swift` - Animatorische Clip-Retargeting-Pipeline. **[GEPLANT]**
- `Modules/Sources/NexaAnimation/AnimationTime.swift` - Frametimes und rationalisierte FPS mit integerbasierten Frames. **[STARTER]**
- `Modules/Sources/NexaAnimation/CurveEditor.swift` - Bézier/Hermite F-Curves, tangent modes und easing. **[GEPLANT]**
- `Modules/Sources/NexaAnimation/ScalarKeyframe.swift` - Keyframe-Datenmodell für numerische Animationsspuren. **[STARTER]**
- `Modules/Sources/NexaAnimation/Shot.swift` - Shot-Länge, Sequenzreferenz und Kamerabindung. **[GEPLANT]**
- `Modules/Sources/NexaAnimation/ShotTrack.swift` - Shot-Schnitt und Crossfade auf Timeline. **[GEPLANT]**
- `Modules/Sources/NexaAnimation/TimelineEvaluator.swift` - Interpolation zwischen skalar definierten Keyframes. **[STARTER]**
- `Modules/Sources/NexaAnimation/TimelineManager.swift` - Scrubbing, Loop, Marker, Snap und Keyframe-Selektion. **[GEPLANT]**
- `Modules/Sources/NexaAnimation/TimelineSequence.swift` - Mehrspurige nonlineare Sequenz mit Arbeitsbereich. **[GEPLANT]**
- `Modules/Sources/NexaAnimation/TimelineTrack.swift` - Spuren für Transform, Material, Kamera, Light, VFX und Audio. **[GEPLANT]**
- `Modules/Sources/NexaAnimation/TimelineView.swift` - UI mit Wellenform, Keyframes, Spurgruppen. **[GEPLANT]**

### Verträge, Qualitätsprüfung & Auslieferung (35)

- `.github/workflows/apple-builds.yml` - macOS-CI für Xcode-Projekt und Swift-Package. **[STARTER]**
- `.github/workflows/backend-tests.yml` - Backend-Test-Pipeline unter Linux. **[STARTER]**
- `.github/workflows/security-audit.yml` - Abhängigkeits- und Secret-Prüfung. **[GEPLANT]**
- `Contracts/error-codes.md` - Fehlercodes zwischen Backend und SwiftUI. **[GEPLANT]**
- `Contracts/openapi.yaml` - Versionierter REST-Vertrag mit DTOs und Auth. **[STARTER]**
- `Contracts/project.schema.json` - JSON-Schema für die nexa3d-Manifestdatei. **[STARTER]**
- `Contracts/sample-job.json` - Beispiel einer KI-Jobantwort. **[STARTER]**
- `Contracts/scene.schema.json` - JSON-Schema für Szene, Knoten und Geometrie-Refs. **[STARTER]**
- `Docs/adr/0001-cross-platform.md` - ADR für SwiftUI und Shared SwiftPM. **[GEPLANT]**
- `Docs/adr/0002-own-scene-format.md` - ADR für eigenes versionsfähiges Dokumentformat. **[GEPLANT]**
- `Docs/architecture/ai-lifecycle.md` - KI-Jobstatus und Datentransfer. **[GEPLANT]**
- `Docs/architecture/domain-model.md` - Scene Graph, Geometrie, Materialdefinitionen. **[GEPLANT]**
- `Docs/architecture/overview.md` - Abhängigkeitsgraph und Architekturrichtlinien. **[GEPLANT]**
- `Docs/architecture/project-format.md` - Paketinhalt, Migrationen und Autosave. **[GEPLANT]**
- `Docs/architecture/rendering.md` - RealityKit zu Metal ohne Domain-Kopplung. **[GEPLANT]**
- `Docs/operations/release-checklist.md` - Store-, QA- und Deployment-Checkliste. **[GEPLANT]**
- `Docs/operations/runbook.md` - Monitoring, Fehlerreaktion und Rollbacks. **[GEPLANT]**
- `Docs/product/design-system.md` - Design-System und UI-Konventionen. **[GEPLANT]**
- `Docs/product/feature-matrix.md` - Featurezuordnung zu Mac, iPad und iPhone. **[GEPLANT]**
- `Docs/product/requirements.md` - Produktanforderungen und Akzeptanzkriterien. **[GEPLANT]**
- `Docs/security/privacy.md` - Datenschutz, Upload-Opt-in und Löschfristen. **[GEPLANT]**
- `Docs/security/threat-model.md` - Risiken: Tokens, Uploads, Malware, Kosten. **[GEPLANT]**
- `Examples/SampleProject.nexa3d/Assets/README.md` - Hinweis zum Speichern externer Meshes/Texturen. **[GEPLANT]**
- `Examples/SampleProject.nexa3d/manifest.json` - Beispielprojekt-Manifesteintrag. **[STARTER]**
- `Examples/SampleProject.nexa3d/scene.json` - Beispielszene mit Cube und Kamera. **[STARTER]**
- `Modules/Tests/NexaDocumentsTests/NexaProjectDocumentTests.swift` - Swift-Testing: Paket-Roundtrip auf Datenträger, Dateierhalt und ungültige Projekte. **[STARTER]**
- `Modules/Tests/NexaDomainTests/NexaSceneTests.swift` - Codable-Roundtrip, Schema und Default-Szene. **[STARTER]**
- `Modules/Tests/NexaExportTests/ExportConformanceTests.swift` - OBJ-/GLB-/USD-Verifikation nach Import in Game Engines. **[GEPLANT]**
- `Modules/Tests/NexaGeometryTests/MeshValidatorTests.swift` - Entartete Dreiecke und Mesh-Grenzfälle. **[GEPLANT]**
- `Scripts/check-project-layout.py` - Validiert das erwartete Dateilayout. **[STARTER]**
- `Scripts/generate-xcode.sh` - XcodeGen-Generierung lokaler Projekte. **[STARTER]**
- `Scripts/run-quality.sh` - Swift-, Backend- und Schema-Checks. **[STARTER]**
- `Tests/Fixtures/Meshes/README.md` - Goldene Testmodelle mit Lizenzinformationen. **[GEPLANT]**
- `Tests/Performance/ViewportBenchmarks.md` - Referenzszenen und FPS-/RAM-Messplan. **[GEPLANT]**
- `Tests/UITests/EditorSmokeTests.swift` - Plattformübergreifender End-to-End-Smoke-Test. **[GEPLANT]**

### VFX, GPU Partikel, Simulation (16)

- `Modules/Sources/NexaVFX/BillboardRenderer.swift` - AlphaBlend / Premultiplied und sorting. **[GEPLANT]**
- `Modules/Sources/NexaVFX/EmitterShape.swift` - Punkt, Cone, Mesh und Volumen als Emitter. **[GEPLANT]**
- `Modules/Sources/NexaVFX/GPUSimulationScheduler.swift` - Compute-Tick, Ressourcenbarrieren und GPU-Budgets. **[GEPLANT]**
- `Modules/Sources/NexaVFX/ParticleBufferPool.swift` - Ping-Pong GPU Buffer und Speichergrenzen. **[GEPLANT]**
- `Modules/Sources/NexaVFX/ParticleCollision.swift` - Depth-/SDF-basierte GPU-Kollisionen. **[GEPLANT]**
- `Modules/Sources/NexaVFX/ParticleEmitterConfiguration.swift` - Reproduzierbare Partikelemitter-Konfiguration mit Grenzwerten. **[STARTER]**
- `Modules/Sources/NexaVFX/ParticleForces.swift` - Gravity, Drag, Turbulence und Attractors. **[GEPLANT]**
- `Modules/Sources/NexaVFX/ParticleSystem.swift` - CPU-Fallback und GPU-Compute-Partikelsimulation. **[GEPLANT]**
- `Modules/Sources/NexaVFX/Shaders/ParticlesCompute.metal` - Partikelsimulation in Compute. **[GEPLANT]**
- `Modules/Sources/NexaVFX/Shaders/ParticlesDraw.metal` - Sichtbare Partikel und Trails. **[GEPLANT]**
- `Modules/Sources/NexaVFX/Shaders/VolumetricFog.metal` - Volumetrische Lichtstreuung. **[GEPLANT]**
- `Modules/Sources/NexaVFX/TrailRenderer.swift` - Partikel-Trails, Ribbons und Streaks. **[GEPLANT]**
- `Modules/Sources/NexaVFX/VFXEditorView.swift` - Node-Editor für Emitter und VFX-Systeme. **[GEPLANT]**
- `Modules/Sources/NexaVFX/VFXGraph.swift` - Knotenbasierter VFX-Graph mit typisierten Ports. **[GEPLANT]**
- `Modules/Sources/NexaVFX/VFXNode.swift` - Emitter, Spawn, Noise, Collision, Render, Event. **[GEPLANT]**
- `Modules/Sources/NexaVFX/VolumetricFog.swift` - Froxel/volumetric Fog mit Qualitätsstufen. **[GEPLANT]**

### Videoszenen, Audio & Movie Render Queue (18)

- `Modules/Sources/NexaCinematics/AudioMixer.swift` - Audiotracks, Gain-Automation und Sync. **[GEPLANT]**
- `Modules/Sources/NexaCinematics/CameraRail.swift` - Spline-Kamerafahrt und LookAt-Rig. **[GEPLANT]**
- `Modules/Sources/NexaCinematics/CineCamera.swift` - Brennweite, Sensorgröße, Apertur, Shutter und Fokusdistanz. **[GEPLANT]**
- `Modules/Sources/NexaCinematics/DepthOfFieldController.swift` - DoF mit physikalischem Fokus. **[GEPLANT]**
- `Modules/Sources/NexaCinematics/FaceBlendShapeMapper.swift` - ARKit-Blends zu Modell-Targets via Profil-Mapping. **[GEPLANT]**
- `Modules/Sources/NexaCinematics/FrameBufferPool.swift` - PixelBuffer-Backpressure und GPU-Readback-Synchronisierung. **[GEPLANT]**
- `Modules/Sources/NexaCinematics/ImageSequenceExporter.swift` - PNG / EXR Einzelbilder und Restart-Fähigkeit. **[GEPLANT]**
- `Modules/Sources/NexaCinematics/MotionCaptureReceiver.swift` - Validierter Livestream von iPhone ARKit; Clock Sync und Network Security. **[GEPLANT]**
- `Modules/Sources/NexaCinematics/MovieRenderQueue.swift` - Persistente Offline-Frame-Jobs mit Pause/Resume/Retry. **[GEPLANT]**
- `Modules/Sources/NexaCinematics/OffscreenRenderer.swift` - Framegenaue GPU-Ausgabe ohne Viewport-Framerate-Zwang. **[GEPLANT]**
- `Modules/Sources/NexaCinematics/RenderJobSpec.swift` - Auflösung, FPS, Framebereich und Codec-Konfiguration. **[STARTER]**
- `Modules/Sources/NexaCinematics/RenderProgressView.swift` - Job-Status, ETA aus Messwerten, Fehler und Abbrechen. **[GEPLANT]**
- `Modules/Sources/NexaCinematics/SequencePlayer.swift` - Deterministische Vorschau anhand Projektzeit. **[GEPLANT]**
- `Modules/Sources/NexaCinematics/ShotDirector.swift` - Shot-Boundaries, Cuts, Takes und Übergänge. **[GEPLANT]**
- `Modules/Sources/NexaCinematics/SoundtrackClip.swift` - Audio-Metadaten, Trims, Fades. **[GEPLANT]**
- `Modules/Sources/NexaCinematics/Timecode.swift` - Zeitskalen und Drop-Frame-Anzeige (sofern notwendig). **[GEPLANT]**
- `Modules/Sources/NexaCinematics/VideoCodecCapabilities.swift` - ProRes/H264/HEVC Verfügbarkeit je Device/OS und Profil prüfen. **[GEPLANT]**
- `Modules/Sources/NexaCinematics/VideoExporter.swift` - AVAssetWriter-Backend, moderne PixelBufferReceiver-API, Legacy-Fallback. **[GEPLANT]**

### Xcode-App-Grundlage (8)

- `Nexa3D.xcodeproj/project.xcproj` - Xcode-Projekt mit Datei-/Dokumentreferenzen und verlinkten lokalen Paketprodukten. **[STARTER]**
- `Nexa3D.xcodeproj/project.xcworkspace/contents.xcworkspacedata` - Bestehendes Xcode-Startprojekt; noch nicht mit den Editor-Modulen verbunden. **[STARTER]**
- `Nexa3D/Assets.xcassets/AccentColor.colorset/Contents.json` - Bestehendes Xcode-Startprojekt; noch nicht mit den Editor-Modulen verbunden. **[STARTER]**
- `Nexa3D/Assets.xcassets/AppIcon.appiconset/Contents.json` - Bestehendes Xcode-Startprojekt; noch nicht mit den Editor-Modulen verbunden. **[STARTER]**
- `Nexa3D/Assets.xcassets/Contents.json` - Bestehendes Xcode-Startprojekt; noch nicht mit den Editor-Modulen verbunden. **[STARTER]**
- `Nexa3D/ContentView.swift` - Verbindet das Projektdokument mit dem gemeinsamen NexaEditor. **[STARTER]**
- `Nexa3D/Info.plist` - Registriert .nexa3d-Projektpakete als editierbaren Dokumenttyp. **[STARTER]**
- `Nexa3D/Nexa3DApp.swift` - Dokumentbasierter App-Einstieg mit angebundenem NexaDocuments-Paket. **[STARTER]**

### Zusätzliche Infrastruktur und Verträge (20)

- `Backend/app/api/render_jobs.py` - Zukünftiger gesicherter API-Endpunkt für remote Video-/GPU-Jobs. **[GEPLANT]**
- `Backend/app/worker/gpu_render.py` - GPU Workernutzung für teure Offline-Frames mit Rate-Limits. **[GEPLANT]**
- `Backend/app/worker/mesh_retopology.py` - Provider/Worker Integration für automatische Retopologie. **[GEPLANT]**
- `Backend/app/worker/texture_baking.py` - Worker-Service für Highpoly zu Lowpoly Baking. **[GEPLANT]**
- `Backend/tests/test_gpu_job_limits.py` - Abbruch, Budget und Ressourcenlimits in GPU Jobs. **[GEPLANT]**
- `Backend/tests/test_render_permissions.py` - Zugriff und Quota für remote Movie Jobs. **[GEPLANT]**
- `Contracts/cinematic.schema.json` - Geplantes versioniertes Cinematic-/Timeline-JSON-Schema. **[STARTER]**
- `Contracts/render-job.schema.json` - Video Jobs, Zielcodec und Upload-Ergebnisse. **[STARTER]**
- `Contracts/rig.schema.json` - Geplantes versioniertes Rig-/Skinned-Mesh-Schema. **[STARTER]**
- `Contracts/vfx.schema.json` - Geplantes VFX-Emitter-/Graph Schema. **[STARTER]**
- `Examples/Cinematic/README.md` - Beispielszene mit Shotlist, Keyframes und Renderprofil. **[DOKUMENTATION]**
- `Examples/Retopology/README.md` - Highpoly->Lowpoly Referenz und Quality Gate. **[DOKUMENTATION]**
- `Examples/Rigging/README.md` - Referenz-Rig, Skindaten und Import/Export-Soll. **[DOKUMENTATION]**
- `Examples/VFX/README.md` - Partikelbeispiel und deterministische Wiedergabe. **[DOKUMENTATION]**
- `Modules/Sources/NexaDocuments/AssetDependencyManifest.swift` - Hash, Größe und Dateiverweise aller Projektassets. **[GEPLANT]**
- `Modules/Sources/NexaDocuments/CinematicDocument.swift` - Verknüpft Timeline und render job state mit Projektpaket. **[GEPLANT]**
- `Modules/Sources/NexaDocuments/RecoveryJournal.swift` - Crash recovery mit Transaktionslog und Checkpoints. **[GEPLANT]**
- `Modules/Sources/NexaDocuments/SceneFormatV2Migration.swift` - Migration für ECS, Sequencer und Rigging Strukturen. **[GEPLANT]**
- `Modules/Sources/NexaInfrastructure/BenchmarkRecorder.swift` - Performance Profil für Render Features auf Zielgeräten. **[GEPLANT]**
- `Modules/Sources/NexaInfrastructure/GPUDeviceMonitor.swift` - GPU Modell, Gerätespeicher, Feature Matrix und Thermalbudget. **[GEPLANT]**

## Pflegeanleitung

Neue Dateien mit Pfad, Kurzbeschreibung, Gruppe und ehrlichem Status in `DATEIMANIFEST.json` erfassen.
Anschließend `python3 Scripts/generate-file-index.py` aufrufen und den Status in `README.md` über `python3 Scripts/update-readme-status.py` erneuern. CI verwendet `--check`.
Neue PDF-Dokumente werden als eigenständige Dateien in `Docs/PDF/` gespeichert.
