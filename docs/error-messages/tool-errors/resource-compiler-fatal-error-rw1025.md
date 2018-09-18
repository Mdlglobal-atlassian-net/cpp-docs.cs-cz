---
title: Závažná chyba kompilátoru prostředků RW1025 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW1025
dev_langs:
- C++
helpviewer_keywords:
- RW1025
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2bf7bdeed320c004ffb75fa1d25d9b89147b0c13
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117397"
---
# <a name="resource-compiler-fatal-error-rw1025"></a>Závažná chyba kompilátoru prostředků RW1025

Nedostatek paměti úplně haldy

Zkontrolujte rezidentní software, který může být zabíraly příliš velkého prostoru. Použijte CHKDSK program a zjistěte, kolik paměti máte.

Pokud vytváříte velkého souboru prostředků, rozdělte do dvou souborů skriptu prostředků. Po vytvoření dva soubory res, použijte příkazový řádek systému MS-DOS k nim dohromady:

```
copy first.res /b + second.res /b full.res
```