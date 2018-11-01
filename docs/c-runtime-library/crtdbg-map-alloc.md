---
title: _CRTDBG_MAP_ALLOC
ms.date: 11/04/2016
f1_keywords:
- CRTDBG_MAP_ALLOC
- _CRTDBG_MAP_ALLOC
helpviewer_keywords:
- _CRTDBG_MAP_ALLOC macro
- memory allocation, in debug builds
- CRTDBG_MAP_ALLOC macro
ms.assetid: 435242b8-caea-4063-b765-4a608200312b
ms.openlocfilehash: a6b6ca5d3e6fdc1bac43d082b0d7df5a87830050
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50453436"
---
# <a name="crtdbgmapalloc"></a>_CRTDBG_MAP_ALLOC

Když **_CRTDBG_MAP_ALLOC** příznak je definován v ladicí verzi aplikace, základní verze funkcí haldy se mapují přímo na jejich ladicí verze. Příznak se používá v souboru Crtdbg.h provést mapování. Tento příznak je k dispozici pouze pokud [_DEBUG](../c-runtime-library/debug.md) příznak je definována v aplikaci.

Další informace o používání verze ladění a základní verze funkcí haldy najdete v tématu [pomocí ladění verze oproti the základní verze](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="see-also"></a>Viz také

[Příznaky řízení](../c-runtime-library/control-flags.md)