---
title: Upozornění kompilátoru (úroveň 4) C4234
ms.date: 11/04/2016
f1_keywords:
- C4234
helpviewer_keywords:
- C4234
ms.assetid: f7fecd5c-8248-4fde-8446-502aedc357ca
ms.openlocfilehash: 63a22fed0832677837eb786268fc92946d295b79
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541779"
---
# <a name="compiler-warning-level-4-c4234"></a>Upozornění kompilátoru (úroveň 4) C4234

používá se nestandardní rozšíření: klíčové slovo klíčové slovo rezervované pro budoucí použití

Kompilátor ještě neimplementuje klíčové slovo, které jste použili.

Toto upozornění je automaticky povýšeno na chybu. Pokud chcete toto chování změnit, použijte [#pragma upozornění](../../preprocessor/warning.md). Pokud například chcete, aby se C4234 problém s upozorněním na úrovni 4,

```cpp
#pragma warning(2:4234)
```

v souboru zdrojového kódu.