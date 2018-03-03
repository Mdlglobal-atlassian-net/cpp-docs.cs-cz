---
title: "Kompilátoru (úroveň 4) upozornění C4437 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
dev_langs:
- C++
ms.assetid: dc07e350-20eb-474c-a7ad-f841ae7ec339
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a50534ca7e25b18d32d37a9120e478f78ea56daf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4437"></a>C4437 kompilátoru upozornění (úroveň 4)
dynamic_cast z virtuální základní "třída1" na "třída2" může selhat v některých kontextech kompilace s /vd2 nebo definovat "třída2" s #pragma vtordisp(2) v platnosti  
  
 Toto upozornění je ve výchozím nastavení vypnutý. V tématu [kompilátoru upozornění, že jsou vypnout ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.  
  
 Kompilátor došlo `dynamic_cast` operaci s následujícími vlastnostmi.  
  
-   Přetypování je ze základní třídy ukazatel ukazatel odvozené třídy.  
  
-   Odvozené třídy dědí prakticky základní třídy.  
  
-   Odvozené třídy nemá `vtordisp` pole pro virtuální základní.  
  
-   Přetypování nebyl nalezen v konstruktoru nebo destruktor odvozené třídy nebo některé třída, která další dědí z odvozené třídy (, jinak hodnota upozornění kompilátoru, které budou vydávat C4436).  
  
 Upozornění znamená, že `dynamic_cast` nemusí provádět správně, pokud ho pracuje na objekt částečně zkonstruovat.  Tato situace nastane, když nadřazených funkce je volána z konstruktoru nebo destruktor třídu, která dědí z třídy odvozené s názvem v upozornění.  Pokud odvozené třídy s názvem v upozornění se nikdy další odvozené, nebo nadřazených funkce není volána při vytváření objektů nebo odstraňování, upozornění můžete ignorovat.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4437 a předvádí problém generování kódu, který vyplývá z chybějící `vtordisp` pole.  
  
```cpp  
// C4437.cpp  
// To see the warning and runtime assert, compile with: /W4  
// To eliminate the warning and assert, compile with: /W4 /vd2  
//       or compile with: /W4 /DFIX  
#pragma warning(default : 4437)  
#include <cassert>  
  
struct A  
{  
public:  
    virtual ~A() {}  
};  
  
#if defined(FIX)  
#pragma vtordisp(push, 2)  
#endif  
struct B : virtual A  
{  
    B()  
    {  
        func();  
    }  
  
    void func()  
    {  
        A* a = static_cast<A*>(this);  
        B* b = dynamic_cast<B*>(a);     // C4437  
        assert(this == b);              // assert unless compiled with /vd2  
    }  
};  
#if defined(FIX)  
#pragma vtordisp(pop)  
#endif  
  
struct C : B  
{  
    int i;  
};  
  
int main()  
{  
    C c;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [dynamic_cast – operátor](../../cpp/dynamic-cast-operator.md)   
 [vtordisp](../../preprocessor/vtordisp.md)   
 [Upozornění kompilátoru (úroveň 1) C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)