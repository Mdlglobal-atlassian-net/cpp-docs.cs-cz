---
title: _CRTDBG_MAP_ALLOC | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- CRTDBG_MAP_ALLOC
- _CRTDBG_MAP_ALLOC
dev_langs:
- C++
helpviewer_keywords:
- _CRTDBG_MAP_ALLOC macro
- memory allocation, in debug builds
- CRTDBG_MAP_ALLOC macro
ms.assetid: 435242b8-caea-4063-b765-4a608200312b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c48095acceefa4bb4852dab18d35284492e7ba0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069398"
---
# <a name="crtdbgmapalloc"></a>_CRTDBG_MAP_ALLOC

Když **_CRTDBG_MAP_ALLOC** příznak je definován v ladicí verzi aplikace, základní verze funkcí haldy se mapují přímo na jejich ladicí verze. Příznak se používá v souboru Crtdbg.h provést mapování. Tento příznak je k dispozici pouze pokud [_DEBUG](../c-runtime-library/debug.md) příznak je definována v aplikaci.

Další informace o používání verze ladění a základní verze funkcí haldy najdete v tématu [pomocí ladění verze oproti the základní verze](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="see-also"></a>Viz také

[Příznaky řízení](../c-runtime-library/control-flags.md)