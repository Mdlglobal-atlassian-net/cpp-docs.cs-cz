---
title: Chyba linkerů LNK1264
ms.date: 11/04/2016
f1_keywords:
- LNK1264
helpviewer_keywords:
- LNK1264
ms.assetid: 23b1aad7-d382-42c1-bae8-db68575c57a8
ms.openlocfilehash: ca17b6946b9e988507af2786825223e042356d0e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160585"
---
# <a name="linker-tools-error-lnk1264"></a>Chyba linkerů LNK1264

/LTCG:PGINSTRUMENT zadána, ale generování kódu se nevyžaduje. instrumentace se nezdařilo

**/LTCG:PGINSTRUMENT** byla zadána, ale žádné obj nebyly nalezeny soubory, které byly zkompilovány pomocí [/GL](../../build/reference/gl-whole-program-optimization.md). Instrumentace nelze provést a odkaz se nezdařilo. Musí existovat alespoň jeden soubor .obj na příkazovém řádku, zkompilovaný pomocí **/GL** aby mohla probíhat instrumentace.

Optimalizace na základě profilu (PGO) je dostupná pouze v 64bitové kompilátory.