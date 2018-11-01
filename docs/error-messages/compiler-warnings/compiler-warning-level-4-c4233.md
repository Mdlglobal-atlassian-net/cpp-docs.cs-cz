---
title: Kompilátor upozornění (úroveň 4) C4233
ms.date: 10/25/2017
f1_keywords:
- C4233
helpviewer_keywords:
- C4233
ms.assetid: 9aa51fc6-8ef3-43b5-bafb-c9333cf60de3
ms.openlocfilehash: 361e00b7361aab51ea077d7e248503f3654e5e58
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516516"
---
# <a name="compiler-warning-level-4-c4233"></a>Kompilátor upozornění (úroveň 4) C4233

> používá se nestandardní rozšíření: '*– klíčové slovo*"– klíčové slovo pouze v jazyce C++, C není podporována

Kompilátor kompilaci zdrojového kódu jako C a C++ a použít klíčové slovo, které platí pouze v jazyce C++. Zdrojový soubor se kompilátor zkompiluje jako C, pokud je rozšíření zdrojový soubor .c nebo používáte [/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md).

Toto upozornění je automaticky povýšen na chybu. Pokud chcete toto chování upravit, použijte [varování #pragma](../../preprocessor/warning.md). Například převeďte C4233 na problém upozornění úrovně 4, přidejte tento řádek do souboru zdrojového kódu:

```cpp
#pragma warning(4:4233)
```
