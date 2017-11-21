---
title: "Kompilátoru (úroveň 4) upozornění C4233 | Microsoft Docs"
ms.custom: 
ms.date: 10/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4233
dev_langs: C++
helpviewer_keywords: C4233
ms.assetid: 9aa51fc6-8ef3-43b5-bafb-c9333cf60de3
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 16e32686451ba7ce0c9a633878f1158a8457163a
ms.sourcegitcommit: 69632887f7a85f4841c49b4c1353d3144927a52c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/11/2017
---
# <a name="compiler-warning-level-4-c4233"></a>C4233 kompilátoru upozornění (úroveň 4)

> nestandardní rozšíření používané: '*– klíčové slovo*' podporována pouze v jazyce C++, C není – klíčové slovo

Kompilátor kompilovat zdrojový kód jako C, nikoli C++ a použít klíčové slovo, které je platné jenom v C++. Kompilátor zkompiluje zdrojový soubor jako C, pokud rozšíření zdrojového souboru .c nebo použijete [/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md).

Toto upozornění je automaticky povýšen na chybu. Pokud chcete-li toto chování změnit, použijte [#pragma – upozornění](../../preprocessor/warning.md). Například C4233 do problémem upozornění úroveň 4, přidáte tento řádek k souboru zdrojového kódu:

```cpp
#pragma warning(4:4233)
```
