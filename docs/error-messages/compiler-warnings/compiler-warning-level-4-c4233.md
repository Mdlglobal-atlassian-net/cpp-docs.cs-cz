---
title: Kompilátoru (úroveň 4) upozornění C4233 | Microsoft Docs
ms.custom: ''
ms.date: 10/25/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4233
dev_langs:
- C++
helpviewer_keywords:
- C4233
ms.assetid: 9aa51fc6-8ef3-43b5-bafb-c9333cf60de3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a933d41fd8e7cf3b94e458efff72193b8ce5e187
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4233"></a>C4233 kompilátoru upozornění (úroveň 4)

> nestandardní rozšíření používané: '*– klíčové slovo*' podporována pouze v jazyce C++, C není – klíčové slovo

Kompilátor kompilovat zdrojový kód jako C, nikoli C++ a použít klíčové slovo, které je platné jenom v C++. Kompilátor zkompiluje zdrojový soubor jako C, pokud rozšíření zdrojového souboru .c nebo použijete [/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md).

Toto upozornění je automaticky povýšen na chybu. Pokud chcete-li toto chování změnit, použijte [#pragma – upozornění](../../preprocessor/warning.md). Například C4233 do problémem upozornění úroveň 4, přidáte tento řádek k souboru zdrojového kódu:

```cpp
#pragma warning(4:4233)
```
