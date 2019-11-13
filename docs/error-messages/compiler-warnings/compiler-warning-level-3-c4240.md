---
title: Upozornění kompilátoru (úroveň 3) C4240
ms.date: 11/04/2016
f1_keywords:
- C4240
helpviewer_keywords:
- C4240
ms.assetid: a2657cdb-18e1-493f-882b-4e10c0bca71d
ms.openlocfilehash: 3636e902e8d6ecd34cdc3e1135761c8595dc5998
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051760"
---
# <a name="compiler-warning-level-3-c4240"></a>Upozornění kompilátoru (úroveň 3) C4240

používá se nestandardní rozšíření: přístup k objektu ClassName je teď definovaný jako specifikátor přístupu, dřív byl definovaný jako specifikátor přístupu.

V části Kompatibilita s ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)) nemůžete změnit přístup na vnořenou třídu. V rámci výchozího rozšíření Microsoft Extensions (/ze) můžete s tímto upozorněním.

## <a name="example"></a>Příklad

```cpp
// C4240.cpp
// compile with: /W3
class X
{
private:
   class N;
public:
   class N
   {   // C4240
   };
};

int main()
{
}
```