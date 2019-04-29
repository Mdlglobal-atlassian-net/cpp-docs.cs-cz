---
title: Kompilátor upozornění (úroveň 1) C4620
ms.date: 11/04/2016
f1_keywords:
- C4620
helpviewer_keywords:
- C4620
ms.assetid: fed29934-b797-47e8-bbea-c7e5f8dd6e93
ms.openlocfilehash: 8e2d11d63704c86c824fd80e1c8a933c10e062d6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404015"
---
# <a name="compiler-warning-level-1-c4620"></a>Kompilátor upozornění (úroveň 1) C4620

postfixová podoba ' operator ++' nalezen pro typ 'type', používá se prefixová podoba

Neexistuje žádná příponového operátoru Inkrementace definované pro daný typ. Kompilátor používá přetížené prefixový operátor.

Toto upozornění se můžete vyhnout tak, že definujete příponový `++` operátor. Vytvořit verzi dvěma argumenty `++` operátor, jak je znázorněno zde:

```
// C4620.cpp
// compile with: /W1
class A
{
public:
   A(int nData) : m_nData(nData)
   {
   }

   A operator++()
   {
      m_nData -= 1;
      return *this;
   }

   // A operator++(int)
   // {
   //    A tmp = *this;
   //    m_nData -= 1;
   //    return tmp;
   // }

private:
   int m_nData;
};

int main()
{
   A a(10);
   ++a;
   a++;   // C4620
}
```