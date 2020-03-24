---
title: Upozornění kompilátoru (úroveň 1) C4274
ms.date: 11/04/2016
f1_keywords:
- C4274
helpviewer_keywords:
- C4274
ms.assetid: 5a948680-7ed1-469f-978d-ae99d154e161
ms.openlocfilehash: 5f2350f275f883e7bf18aa1621d08b34132e8dfb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175843"
---
# <a name="compiler-warning-level-1-c4274"></a>Upozornění kompilátoru (úroveň 1) C4274

\#Ident se ignoruje; zobrazit dokumentaci #pragma komentář (exestr, ' String ')

Direktiva `#ident`, která vloží řetězec zadaný uživatelem do objektu nebo spustitelného souboru, je zastaralá. V důsledku toho kompilátor ignoruje direktivu.

> [!CAUTION]
>  Upozornění C4274 vás upozorní na použití direktivy [#pragma Comment (exestr, "String")](../../preprocessor/comment-c-cpp.md) . Tato doporučení je však zastaralá a v budoucí verzi kompilátoru bude revidována. Použijete-li direktivu `#pragma`, nástroj Linker (LINK. exe) ignoruje záznam komentáře vyprodukovaný direktivou a problémy s upozorněním [linkerů lnk4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md). Místo direktivy `#ident` doporučujeme použít v aplikaci řetězec prostředku verze souboru.

## <a name="to-correct-this-error"></a>Oprava této chyby

- Odeberte direktivu `#ident "`*řetězec*`"`.

## <a name="see-also"></a>Viz také

[comment (C/C++)](../../preprocessor/comment-c-cpp.md)<br/>
[Upozornění linkerů LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)<br/>
[Práce se zdrojovými soubory](../../windows/working-with-resource-files.md)
