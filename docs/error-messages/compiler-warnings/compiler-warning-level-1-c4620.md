---
title: Upozornění (úroveň 1) C4620 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4620
dev_langs:
- C++
helpviewer_keywords:
- C4620
ms.assetid: fed29934-b797-47e8-bbea-c7e5f8dd6e93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 117cd6d34ca25aebcfa392efcd95940891491e70
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118202"
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