---
title: "Kompilátoru (úroveň 1) upozornění C4350 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4350
dev_langs: C++
helpviewer_keywords: C4350
ms.assetid: 4cc8ed67-64c4-4da5-a7a5-a639232baa23
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e05320bcfeac5ba340d286851e13439e53734a7a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4350"></a>C4350 kompilátoru upozornění (úroveň 1)
změna chování: byl zavolán člen 'member1' místo členu 'member2'  
  
 Rvalue nelze navázat na jiný const odkaz. Ve verzích Visual C++ před Visual Studio 2003 bylo možné vytvořit vazbu rvalue s odkazem na jiný const v přímé inicializace. Tento kód se nyní zobrazí upozornění.  
  
 Pro zpětnou kompatibilitu je stále možné svázat rvalue bez const odkazy, ale standardní převody jsou upřednostňované, pokud je to možné.  
  
 Toto upozornění představuje změnu chování z kompilátoru Visual C++ .NET 2002. Pokud je povoleno, toto upozornění může mít pravděpodobně pro správný kód. Například je může mít při používání **std::auto_ptr** šablona třídy.  
  
 Pokud se zobrazí toto upozornění, zkontrolujte v kódu, které chcete zobrazit, pokud je závislý na rvalue vazbu na jiný const odkazy. Přidání const k odkazu nebo zadáním další přetížení const odkaz může problém vyřešit.  
  
 Toto upozornění je ve výchozím nastavení vypnutý. Další informace najdete v tématu [kompilátoru upozornění, že jsou vypnout ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
 Následující ukázka generuje C4350:  
  
```cpp  
// C4350.cpp  
// compile with: /W1  
#pragma warning (default : 4350)  
class A {};  
  
class B  
{  
public:  
   B(B&){}  
   // try the following instead:  
   // B(const B&){}  
  
   B(A){}  
   operator A(){ return A();}  
};  
  
B source() { return A(); }  
  
int main()  
{  
   B ap(source());   // C4350  
}  
```