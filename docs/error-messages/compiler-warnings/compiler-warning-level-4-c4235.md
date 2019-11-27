---
title: Upozornění kompilátoru (úroveň 4) C4235
ms.date: 11/04/2016
f1_keywords:
- C4235
helpviewer_keywords:
- C4235
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
ms.openlocfilehash: 3e3cb2e40ed42b24ee52252003b26ec09cd86710
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541762"
---
# <a name="compiler-warning-level-4-c4235"></a>Upozornění kompilátoru (úroveň 4) C4235

používá se nestandardní rozšíření: klíčové slovo klíčové slovo není v této architektuře podporované.

Kompilátor nepodporuje klíčové slovo, které jste použili.

Toto upozornění je automaticky povýšeno na chybu. Pokud chcete toto chování změnit, použijte [#pragma upozornění](../../preprocessor/warning.md). Pokud například chcete, aby se C4235 do upozornění úrovně 2, použijte následující řádek kódu.

```cpp
#pragma warning(2:4235)
```

v souboru zdrojového kódu.