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
ms.openlocfilehash: 8bcb0f5ea26218b74034eb0a41199a1104ba944d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344769"
---
# <a name="crtdbgmapalloc"></a>_CRTDBG_MAP_ALLOC

Když **_CRTDBG_MAP_ALLOC** příznak je definován v ladicí verzi aplikace, základní verze funkcí haldy se mapují přímo na jejich ladicí verze. Příznak se používá v souboru Crtdbg.h provést mapování. Tento příznak je k dispozici pouze pokud [_DEBUG](../c-runtime-library/debug.md) příznak je definována v aplikaci.

Další informace o používání verze ladění a základní verze funkcí haldy najdete v tématu [pomocí ladění verze oproti the základní verze](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="see-also"></a>Viz také:

[Příznaky řízení](../c-runtime-library/control-flags.md)
