---
title: Upozornění (úroveň 1) C4274 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4274
dev_langs:
- C++
helpviewer_keywords:
- C4274
ms.assetid: 5a948680-7ed1-469f-978d-ae99d154e161
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5f6db0ee96674beda51ab02c8651e6f4960a0bf8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094683"
---
# <a name="compiler-warning-level-1-c4274"></a>Kompilátor upozornění (úroveň 1) C4274

\#Ident ignorovány; najdete v dokumentaci #pragma Comment (exestr, 'řetězec')

`#ident` – Direktiva, která vloží řetězec uživatelem zadaný objekt nebo spustitelný soubor, se již nepoužívá. V důsledku toho kompilátor ignoruje direktivy.

> [!CAUTION]
>  Upozornění C4274 výzvou k použití [#pragma comment (exestr, 'řetězec')](../../preprocessor/comment-c-cpp.md) směrnice. Ale toto doporučení je zastaralá a bude v budoucí verzi kompilátoru revidován. Pokud používáte `#pragma` direktiv, nástroj linker (LINK.exe) ignoruje poznámku vytvářených směrnice a vydá upozornění [LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md). Místo `#ident` direktiv, doporučujeme použít zdrojový řetězec verze souboru v aplikaci.

## <a name="to-correct-this-error"></a>Oprava této chyby

- Odeberte `#ident "` *řetězec* `"` směrnice.

## <a name="see-also"></a>Viz také

[comment (C/C++)](../../preprocessor/comment-c-cpp.md)<br/>
[Upozornění linkerů LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)<br/>
[Práce se zdrojovými soubory](../../windows/working-with-resource-files.md)