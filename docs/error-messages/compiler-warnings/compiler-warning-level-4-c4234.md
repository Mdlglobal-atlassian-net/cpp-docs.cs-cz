---
title: Kompilátor upozornění (úroveň 4) C4234
ms.date: 11/04/2016
f1_keywords:
- C4234
helpviewer_keywords:
- C4234
ms.assetid: f7fecd5c-8248-4fde-8446-502aedc357ca
ms.openlocfilehash: 314ee068fb2be6148304360b0aaa3bd8029c283b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441012"
---
# <a name="compiler-warning-level-4-c4234"></a>Kompilátor upozornění (úroveň 4) C4234

používá se nestandardní rozšíření: klíčové slovo '– klíčové slovo' vyhrazený pro budoucí použití

Kompilátor ještě neimplementuje klíčové slovo, které jste použili.

Toto upozornění je automaticky povýšen na chybu. Pokud chcete toto chování upravit, použijte [varování #pragma](../../preprocessor/warning.md). Chcete-li například vytvořit C4234 jako chybu upozornění úrovně 4

```
#pragma warning(2:4234)
```

v souboru zdrojového kódu.