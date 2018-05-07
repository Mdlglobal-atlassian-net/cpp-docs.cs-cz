---
title: Kompilátoru (úroveň 1) upozornění C4436 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
ms.assetid: 2b54a1fc-c9c6-4cc9-90be-faa44fc715d5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a1da06a329a9c0bdfcff6877ce69c8e3672619bb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4436"></a>C4436 kompilátoru upozornění (úroveň 1)
může selhat s částečně sestavený objekt kompilace s /vd2 nebo definovat "třída2" s #pragma vtordisp(2) platí dynamic_cast z virtuální základní "třída1" na "třída2" v konstruktoru nebo – destruktor  
  
 Kompilátor došlo `dynamic_cast` operaci s následujícími vlastnostmi.  
  
-   Přetypování je ze základní třídy ukazatel ukazatel odvozené třídy.  
  
-   Odvozené třídy dědí prakticky základní třídy.  
  
-   Odvozené třídy nemá `vtordisp` pole pro virtuální základní.  
  
-   Přetypování se nachází v konstruktoru nebo destruktor odvozené třídy nebo některé třída, která další dědí z odvozené třídy.  
  
 Označuje upozornění `dynamic_cast` nemusí provádět správně, pokud ho pracuje na objekt částečně zkonstruovat.  K tomu dojde, pokud odvozené konstruktor/destruktor pracuje na objekt dílčí některé další odvozené objektu.  Pokud odvozené třídy s názvem v upozornění se nikdy další odvozené, můžete ignorovat upozornění.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4436 a předvádí problém generování kódu, který vyplývá z chybějící `vtordisp` pole.  
  
```cpp  
// C4436.cpp  
// To see the warning and runtime assert, compile with: /W1  
// To eliminate the warning and assert, compile with: /W1 /vd2  
//       or compile with: /W1 /DFIX  
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
        A* a = static_cast<A*>(this);  
        B* b = dynamic_cast<B*>(a);     // C4436  
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
 [Upozornění kompilátoru (úroveň 4) C4437](../../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)