---
title: Upozornění kompilátoru (úroveň 1) C4274
ms.date: 11/04/2016
f1_keywords:
- C4274
helpviewer_keywords:
- C4274
ms.assetid: 5a948680-7ed1-469f-978d-ae99d154e161
ms.openlocfilehash: 5d005fccc5920aea61698a65edf9284d56366a1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377081"
---
# <a name="compiler-warning-level-1-c4274"></a>Upozornění kompilátoru (úroveň 1) C4274

\#ident ignorován; viz dokumentace pro #pragma komentář (exestr, 'řetězec')

Směrnice, `#ident` která vloží řetězec zadaný uživatelem do objektu nebo spustitelného souboru, je zastaralá. V důsledku toho kompilátor ignoruje směrnice.

> [!CAUTION]
> Upozornění C4274 doporučuje použít [#pragma comment(exestr, 'string')](../../preprocessor/comment-c-cpp.md) směrnice. Tato rada je však zastaralé a bude revidována v budoucí verzi kompilátoru. Pokud použijete `#pragma` direktivu, nástroj linkeru (LINK.exe) ignoruje komentář záznam vytvořený směrnice a problémy upozornění [LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md). Namísto `#ident` směrnice doporučujeme použít řetězec prostředků verze souboru v aplikaci.

## <a name="to-correct-this-error"></a>Oprava této chyby

- Odeberte `#ident "` *direktivu řetězce.* `"`

## <a name="see-also"></a>Viz také

[comment (C/C++)](../../preprocessor/comment-c-cpp.md)<br/>
[Upozornění na nástroje propojovacího serveru LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)<br/>
[Práce se zdrojovými soubory](../../windows/working-with-resource-files.md)
