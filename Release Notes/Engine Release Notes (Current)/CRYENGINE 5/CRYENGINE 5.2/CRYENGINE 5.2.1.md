# CRYENGINE 5.2.1

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/47316993/pages/44962646
- Page ID: 44962646
- Breadcrumb: Engine Release Notes (Current) > CRYENGINE 5 > CRYENGINE 5.2 > CRYENGINE 5.2.1
- Parent: CRYENGINE 5.2

## Content

## Audio

#### Audio General

- **Fixed**: Default Audio Entities plus some areas in game templates are not working. Audio Entities and dependencies added to game templates.

#### ACE (Audio Controls Editor)

- **Fixed**: ACE sometimes crashes when opened while running either FMOD Studio or SDL_mixer.

## Core/System

#### Engine General

- **Fixed**: Game projects missing assets in the Engine's templates folder.
- **Fixed**: Added missing main layer to project upgrade packages.
- **Fixed**: Crash during Engine initialization when no PAK encryption is provided.
- **Fixed:** Windows dedicated server did not support the new project setup.

## Graphics and Rendering

#### Renderer General

- **Fixed**: Missing shader-item/resource ref-counting.

#### GPU Particles

- **Fixed**: GPU particle temporal anti-aliasing was inverted.

## Sandbox

#### Editor General

- **Fixed**: A Layer will be created as fallback even if a Level is loaded with no layers.
- **Fixed**: Editor crashes when an object creation fails.
- **Fixed:** The Notification Center gets spammed with notification (>500) when opening a GameSDK project in the Editor.

## Known Issues

- Unable to initialize the Engine after downloading CRYENGINE 5.2 through Launcher.
- The engine crashes when users try to open the Mannequin editor two times in a row.
- By loading a non-exported map into the launcher causes the map to corrupt indefinitely.
- Mouse cursor does not lock to the game window when a template project is launched in the game mode.
- Rolling ball template cannot be opened using the launcher without reinstalling the launcher.
- Alembic caches are unable to be imported.
