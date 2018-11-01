---
title: Závažná chyba kompilátoru prostředků RW1025
ms.date: 11/04/2016
f1_keywords:
- RW1025
helpviewer_keywords:
- RW1025
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
ms.openlocfilehash: 8ecfc11f5cc991294d966a4b6c75d8da6669d5b1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575679"
---
# <a name="resource-compiler-fatal-error-rw1025"></a>Závažná chyba kompilátoru prostředků RW1025

Nedostatek paměti úplně haldy

Zkontrolujte rezidentní software, který může být zabíraly příliš velkého prostoru. Použijte CHKDSK program a zjistěte, kolik paměti máte.

Pokud vytváříte velkého souboru prostředků, rozdělte do dvou souborů skriptu prostředků. Po vytvoření dva soubory res, použijte příkazový řádek systému MS-DOS k nim dohromady:

```
copy first.res /b + second.res /b full.res
```