---
title: Kompilátor upozornění (úroveň 3) C4240
ms.date: 11/04/2016
f1_keywords:
- C4240
helpviewer_keywords:
- C4240
ms.assetid: a2657cdb-18e1-493f-882b-4e10c0bca71d
ms.openlocfilehash: fe5306cc7909138fea0159553b53c2adc6a46dc0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402213"
---
# <a name="compiler-warning-level-3-c4240"></a>Kompilátor upozornění (úroveň 3) C4240

používá se nestandardní rozšíření: přístup k "classname" teď definovaný jako "specifikátor přístupu", dřív byl definovaný jako "přístup specifikátor"

V části kompatibility ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)), nelze změnit přístup na vnořenou třídu. V části výchozí rozšíření Microsoft (/Ze) je to možné, se toto upozornění.

## <a name="example"></a>Příklad

```
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