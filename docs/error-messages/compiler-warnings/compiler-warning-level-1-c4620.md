---
title: Kompilátoru (úroveň 1) upozornění C4620 | Microsoft Docs
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
ms.openlocfilehash: bdd192ad130a1a1cc1aa96bd8e423b01554b0720
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4620"></a>C4620 kompilátoru upozornění (úroveň 1)
žádné operátory formu ' operátor ++' nebyla nalezena pro typ "typ" pomocí předpony formuláře  
  
 Neexistuje žádný operátor přírůstku operátory definovaný pro daný typ. Kompilátor použít operátor přetížené předponu.  
  
 Toto upozornění můžete vyhnout tak, že definujete operátory `++` operátor. Vytvořit dva argument verzi `++` operátor, jak je vidět tady:  
  
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