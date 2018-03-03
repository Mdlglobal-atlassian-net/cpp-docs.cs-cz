---
title: "Kompilátoru (úroveň 1) upozornění C4743 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4743
dev_langs:
- C++
helpviewer_keywords:
- C4743
ms.assetid: 2ee76ea3-77f3-4c2f-9a57-0751823c89fd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1a7169afdf7fb4c9a03e509f0332e738a66a06f7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4743"></a>C4743 kompilátoru upozornění (úroveň 1)
'*typ*, má jinou velikost v'*file1*'a'*file2*': *číslo* a *číslo* bajtů  
  
 Proměnná externí odkazuje nebo definované v dva soubory obsahuje různé typy v těchto souborů a kompilátor určili, že velikost proměnné v *file1* se liší od velikost proměnné v *file2*.  
  
 Se důležité nestane, pokud toto upozornění můžete vygenerované jazyka C++. Pokud je deklarovat stejné typy se stejným názvem ve dvou různých souborů, pokud tyto deklarace obsahovat virtuální funkce a deklarací nejsou stejné, můžete kompilátor emitování upozornění C4744 pro tabulky virtuální funkce. Upozornění dojde, protože existují dvě různé velikostí virtuální funkce tabulky pro stejného typu a linkeru musíte zvolit jeden z nich začlenit do spustitelného souboru.  Je možné, že to může způsobit v programu volání nesprávný virtuální funkce.  
  
 Chcete-li vyřešit toto upozornění, použijte stejné definice typu nebo použijte odlišné názvy pro typy nebo proměnné.  
  
## <a name="example"></a>Příklad  
 Tato ukázka obsahuje jednu definici typu.  
  
```  
// C4743a.cpp  
// compile with: /c  
class C {  
public:  
    virtual void f1(void);  
    virtual void f2(void);  
    virtual void f3(void);  
};  
  
void C::f1(void) {}  
void C::f2(void) {}  
void C::f3(void) {}  
C q;  
```  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4743.  
  
```  
// C4743b.cpp  
// compile with: C4743a.cpp /W1 /GL /O2  
// C4743 expected  
class C {  
public:  
    virtual void f1(void);  
    virtual void f2(void);  
    virtual void f3(void);  
    virtual void f4(void);  
    virtual void f5(void);  
};  
  
void C::f4(void) {}  
void C::f5(void) {}  
C x;  
  
int main() {}   
```