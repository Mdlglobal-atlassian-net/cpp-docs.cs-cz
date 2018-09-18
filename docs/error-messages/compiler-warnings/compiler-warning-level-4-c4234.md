---
title: Upozornění (úroveň 4) C4234 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4234
dev_langs:
- C++
helpviewer_keywords:
- C4234
ms.assetid: f7fecd5c-8248-4fde-8446-502aedc357ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a6ce6ba622cb480096144706589a01dee7326f38
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118229"
---
# <a name="compiler-warning-level-4-c4234"></a>Kompilátor upozornění (úroveň 4) C4234

používá se nestandardní rozšíření: klíčové slovo '– klíčové slovo' vyhrazený pro budoucí použití

Kompilátor ještě neimplementuje klíčové slovo, které jste použili.

Toto upozornění je automaticky povýšen na chybu. Pokud chcete toto chování upravit, použijte [varování #pragma](../../preprocessor/warning.md). Chcete-li například vytvořit C4234 jako chybu upozornění úrovně 4

```
#pragma warning(2:4234)
```

v souboru zdrojového kódu.