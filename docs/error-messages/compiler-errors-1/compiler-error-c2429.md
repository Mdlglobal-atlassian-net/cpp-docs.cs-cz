---
title: "C2429 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2429
dev_langs: C++
helpviewer_keywords: C2429
ms.assetid: 57ff6df9-5cf1-49f3-8bd8-4e550dfd65a0
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f263673e6b325557694b26b1fd71e86c22029d05
ms.sourcegitcommit: 78f3f8208d49b7c1d87f4240f4a1496b7c29333e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/17/2017
---
# <a name="compiler-error-c2429"></a>C2429 chyby kompilátoru

> '*funkce jazyka*, vyžaduje kompilátoru příznak'*– možnost kompilátoru*.

Funkce jazyka vyžaduje možnost konkrétní kompilátoru pro podporu.

Chyba **C2429: jazyk funkce 'vnořené – obor názvů – definice' vyžaduje kompilátoru příznak "/ std:c ++ 17'** se vygeneruje, pokud se pokusíte definovat *složené obor názvů*, obor názvů, který obsahuje jeden nebo více názvy vnořené oboru názvů, počínaje Visual Studio 2015 Update 5. (Ve Visual Studio 2017 verze 15.3, **/std: c ++ nejnovější** přepínač je povinný.) Složené obor názvů, který definice nejsou povoleny v jazyce C++ před C ++ 17. Kompilátor podporuje složené obor názvů definice při [/std: c ++ 17](../../build/reference/std-specify-language-standard-version.md) je zadána možnost kompilátoru:

```cpp
// C2429a.cpp
namespace a::b { int i; } // C2429 starting in Visual C++ 2015 Update 3.
                          // Use /std:c++17 to fix, or do this:
// namespace a { namespace b { int i; }}

int main() {
   a::b::i = 2;
}
```