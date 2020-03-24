---
title: Upozornění kompilátoru (úroveň 1) C4620
ms.date: 11/04/2016
f1_keywords:
- C4620
helpviewer_keywords:
- C4620
ms.assetid: fed29934-b797-47e8-bbea-c7e5f8dd6e93
ms.openlocfilehash: f044d3e10928bc1aaa1e111d01d04b8562b5c025
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185890"
---
# <a name="compiler-warning-level-1-c4620"></a>Upozornění kompilátoru (úroveň 1) C4620

pro typ Type se nenašla žádná přípona operator + + s použitím formuláře s předponou.

Pro daný typ není definován žádný operátor přírůstku přípony. Kompilátor použil přetížený operátor předpony.

Toto upozornění lze zabránit definováním přípony `++` operátoru. Vytvořte verzi `++` operátoru se dvěma argumenty, jak je znázorněno zde:

```cpp
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
