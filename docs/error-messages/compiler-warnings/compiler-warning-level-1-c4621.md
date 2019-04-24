---
title: Kompilátor upozornění (úroveň 1) C4621
ms.date: 11/04/2016
f1_keywords:
- C4621
helpviewer_keywords:
- C4621
ms.assetid: 40931bd9-cb89-497e-86f0-cec9f016c63c
ms.openlocfilehash: d35c4143d5b90c7a6a49337931dad4ba73804f20
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62221355"
---
# <a name="compiler-warning-level-1-c4621"></a>Kompilátor upozornění (úroveň 1) C4621

'operator--' pro typ 'type', používá se prefixová podoba se nenašla postfixová podoba

Došlo k dispozici žádné definované pro daný typ příponového operátoru dekrementace. Kompilátor používá přetížené prefixový operátor.

Toto upozornění se můžete vyhnout tak, že definujete příponový `--` operátor. Vytvořit verzi dvěma argumenty `--` operátor, jak je znázorněno níže:

```
// C4621.cpp
// compile with: /W1
class A
{
public:
   A(int nData) : m_nData(nData)
   {
   }

   A operator--()
   {
      m_nData -= 1;
      return *this;
   }

   // A operator--(int)
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
   --a;
   a--;   // C4621
}
```