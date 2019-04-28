---
title: Závažná chyba kompilátoru prostředků RW1025
ms.date: 11/04/2016
f1_keywords:
- RW1025
helpviewer_keywords:
- RW1025
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
ms.openlocfilehash: 8ecfc11f5cc991294d966a4b6c75d8da6669d5b1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62347204"
---
# <a name="resource-compiler-fatal-error-rw1025"></a>Závažná chyba kompilátoru prostředků RW1025

Nedostatek paměti úplně haldy

Zkontrolujte rezidentní software, který může být zabíraly příliš velkého prostoru. Použijte CHKDSK program a zjistěte, kolik paměti máte.

Pokud vytváříte velkého souboru prostředků, rozdělte do dvou souborů skriptu prostředků. Po vytvoření dva soubory res, použijte příkazový řádek systému MS-DOS k nim dohromady:

```
copy first.res /b + second.res /b full.res
```