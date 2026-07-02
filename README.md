# FaceOnLive — Face Recognition & Liveness SDK for Windows (C++)

Native C++ SDK for Windows providing face detection, **face liveness (anti-spoofing)**, and 1:1 / 1:N face matching. Runs entirely on the machine.

> Part of the [FaceOnLive](https://faceonlive.com) on-premises biometric SDK suite.

## Features
- Face detection with landmarks and a **liveness score**.
- Biometric template extraction and similarity comparison.
- On-premises and offline; C/C++ API for desktop and server apps.

## Requirements
| | |
|---|---|
| OS | Windows 10/11 x64 |
| Toolchain | Visual Studio 2019+ (v16), C++17 |
| Dependency | OpenCV (bundled under `opencv/`) |
| Engine | `ttvfaceengine` (headers + libs included) |

## Setup
1. Open the solution in **Visual Studio**.
2. Get a license key — free trial at **https://faceonlive.com**.
3. In `ttvfacedemo/ttvfacedemo.cpp`, replace `<YOUR_LICENSE_KEY>` in `ttv_set_activation(...)`.
4. Build (x64) and run.

## Quick start (C++)
```cpp
#include "ttvfaceengine.h"

const char* hwid = ttv_get_hwid(LOCAL);                     // for offline licensing
int ret = ttv_set_activation((char*)"<YOUR_LICENSE_KEY>", LOCAL);
if (ret == 0) ret = ttv_init(/* model path */);

// detect, extract, and compare faces via the engine API in ttvfaceengine.h
```

## API reference (`ttvfaceengine.h`)
| Function | Description |
|---|---|
| `ttv_version()` | SDK version. |
| `ttv_get_hwid(mode)` | Machine hardware ID (for offline licensing). |
| `ttv_set_activation(license, mode)` | Activate the SDK. Returns `0` on success. |
| `ttv_init(...)` | Initialize the engine / load models. |
| `ttv_detect_face(...)` | Detect faces with liveness score. |
| `ttv_extract_feature(...)` | Extract a face template. |
| `ttv_compare_feature(...)` | Compare two templates (`0.0–1.0`). |

## License & support
Requires a valid license key — get one at **[faceonlive.com](https://faceonlive.com)**. Never commit your key. Questions: contact@faceonlive.com

## 📦 Full SDK download
This repository contains the source/demo code only. Download the complete SDK — engine libraries and models, with full project structure — from the [Releases](../../releases) page and extract it over this project.
