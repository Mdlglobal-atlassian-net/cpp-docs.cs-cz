---
title: Kompilátoru (úroveň 1) upozornění C4350 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4350
dev_langs:
- C++
helpviewer_keywords:
- C4350
ms.assetid: 4cc8ed67-64c4-4da5-a7a5-a639232baa23
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b7e13b73eeee9c24841e97419b702b3e41be3982
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33286926"
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