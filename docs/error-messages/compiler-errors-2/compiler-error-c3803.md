---
title: Chyba kompilátoru C3803
ms.date: 11/04/2016
f1_keywords:
- C3803
helpviewer_keywords:
- C3803
ms.assetid: bad5fb9a-ed9a-4c15-96e7-cf06e200a50d
ms.openlocfilehash: 771530c2d05d378b86732938aa7a2b7881608446
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755301"
---
# <a name="compiler-error-c3803"></a>Chyba kompilátoru C3803

' Property ': vlastnost má typ, který je nekompatibilní s jedním z jeho přístupových objektů ' přistupující objekty '

Typ vlastnosti definované s [vlastností](../../cpp/property-cpp.md) neodpovídá návratový typ pro jednu z jeho přístupových funkcí.

Následující ukázka generuje C3803:

```cpp
// C3803.cpp
struct A
{
   __declspec(property(get=GetIt)) int i;
   char GetIt()
   {
      return 0;
   }

   /*
   // try the following definition instead
   int GetIt()
   {
      return 0;
   }
   */
}; // C3803

int main()
{
}
```
