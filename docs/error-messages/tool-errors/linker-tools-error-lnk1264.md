---
title: Chyba Linkerů LNK1264 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1264
dev_langs:
- C++
helpviewer_keywords:
- LNK1264
ms.assetid: 23b1aad7-d382-42c1-bae8-db68575c57a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8232e83774dc53755b77ad9c8b3bbb2a0bcc6ae6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102739"
---
# <a name="linker-tools-error-lnk1264"></a>Chyba linkerů LNK1264

/LTCG:PGINSTRUMENT zadána, ale generování kódu se nevyžaduje. instrumentace se nezdařilo

**/LTCG:PGINSTRUMENT** byla zadána, ale žádné obj nebyly nalezeny soubory, které byly zkompilovány pomocí [/GL](../../build/reference/gl-whole-program-optimization.md). Instrumentace nelze provést a odkaz se nezdařilo. Musí existovat alespoň jeden soubor .obj na příkazovém řádku, zkompilovaný pomocí **/GL** aby mohla probíhat instrumentace.

Optimalizace na základě profilu (PGO) je dostupná pouze v 64bitové kompilátory.