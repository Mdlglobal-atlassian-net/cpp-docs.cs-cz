---
title: Chyba kompilátoru C2130
ms.date: 11/04/2016
f1_keywords:
- C2130
helpviewer_keywords:
- C2130
ms.assetid: c6fd5a7e-8f28-4f67-99d1-95a13b0dff90
ms.openlocfilehash: aee0931926cad2ac30631c152aeb94bfd24befd2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397598"
---
# <a name="compiler-error-c2130"></a>Chyba kompilátoru C2130

\#řádek se očekával řetězec obsahující název souboru, nalezeno "token"

Token za název souboru volitelný [#line](../../preprocessor/hash-line-directive-c-cpp.md) `linenumber` musí být řetězec.

Následující ukázka generuje C2130:

```
// C2130.cpp
int main() {
   #line 1000 test   // C2130
   #line 1000 "test"   // OK
}
```