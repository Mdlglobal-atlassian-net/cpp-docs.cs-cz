---
title: "C2059 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2059
dev_langs: C++
helpviewer_keywords: C2059
ms.assetid: 2be4eb39-3f37-4b32-8e8d-75835e07c78a
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a87f9c3dbb1405463804b7abd5c94abe04a42845
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2059"></a>C2059 chyby kompilátoru
Chyba syntaxe: 'tokenu.  
  
 Token způsobila chybu syntaxe.  
  
 Následující příklad vytvoří chybovou zprávu pro řádek, který deklaruje `j`.  
  
```  
// C2059e.cpp  
// compile with: /c  
// C2143 expected  
// Error caused by the incorrect use of '*'.  
   int j*; // C2059   
```  
  
 Pokud chcete zjistit příčinu chyby, zkontrolujte pouze na řádku, který je uvedený v chybové zprávě, ale také řádcích nad ním. Pokud zkoumání řádky nese žádné potvrzením o problému, zkuste komentářů řádek, který je uvedený v chybové zprávě a případně několika řádcích nad ním.  
  
 Pokud chybová zpráva se zobrazí na symbol, který následuje `typedef` proměnnou, ujistěte se, že je proměnná definovaná ve zdrojovém kódu.  
  
 C2059 může dojít, pokud je symbol výsledkem nothing, protože může dojít, když **/D** `symbol`  **=**  se používá ke kompilaci.  
  
```  
// C2059a.cpp  
// compile with: /DTEST=  
#include <stdio.h>  
  
int main() {  
   #ifdef TEST  
      printf_s("\nTEST defined %d", TEST);   // C2059  
   #else  
      printf_s("\nTEST not defined");  
   #endif  
}  
```  
  
 Při kompilaci aplikace, která určuje strukturu v výchozí argumenty pro funkci je jiný případ, ve kterém může dojít, C2059. Výchozí hodnota pro argument musí být výraz. Seznamu inicializátoru – například ten, který použitý k inicializaci strukturou – není výraz.  Chcete-li vyřešit tento problém, definujte konstruktor k provedení požadované inicializace.  
  
 Následující příklad generuje C2059:  
  
```  
// C2059b.cpp  
// compile with: /c  
struct ag_type {  
   int a;  
   float b;  
   // Uncomment the following line to resolve.  
   // ag_type(int aa, float bb) : a(aa), b(bb) {}   
};  
  
void func(ag_type arg = {5, 7.0});   // C2059  
void func(ag_type arg = ag_type(5, 7.0));   // OK  
```  
  
 Můžete také získat C2059 Pokud definujete člen šablony třídy nebo funkce mimo třídu. Informace najdete v tématu [článku znalostní báze 241949](http://support.microsoft.com/kb/241949).  
  
 C2059 může stát nedůvěryhodný přetypování.  
  
 Následující ukázka generuje C2059:  
  
```  
// C2059c.cpp  
// compile with: /clr  
using namespace System;  
ref class From {};  
ref class To : public From {};  
  
int main() {  
   From^ refbase = gcnew To();  
   To^ refTo = safe_cast<To^>(From^);   // C2059  
   To^ refTo2 = safe_cast<To^>(refbase);   // OK  
}  
```  
  
 C2059 může také nastat, pokud se pokusíte vytvořit název oboru názvů, který obsahuje tečku.  
  
 Následující ukázka generuje C2059:  
  
```  
// C2059d.cpp  
// compile with: /c  
namespace A.B {}   // C2059  
  
// OK  
namespace A  {  
   namespace B {}  
}  
```  
  
 C2059 může dojít, když operátor, kterou je možné získat název (`::`, `->`, a `.`) musí být následováno klíčové slovo `template`, jak je uvedeno v následujícím příkladu:  
  
```cpp  
template <typename T> struct Allocator {  
    template <typename U> struct Rebind {  
        typedef Allocator<U> Other;  
    };  
};  
  
template <typename X, typename AY> struct Container {  
    typedef typename AY::Rebind<X>::Other AX; // error C2059  
};  
  
```  
  
 Ve výchozím nastavení, C++ předpokládá, že `AY::Rebind` není šablonu; proto následující `<` interpretována jako méně – znaménko.  Se musí zjistit kompilátor explicitně který `Rebind` je šablona, aby ho mohou správně analyzovat lomená závorka. Chcete-li opravit tuto chybu, použijte `template` – klíčové slovo na název závislého typu, jak je vidět tady:  
  
```cpp  
template <typename T> struct Allocator {  
    template <typename U> struct Rebind {  
        typedef Allocator<U> Other;  
    };  
};  
  
template <typename X, typename AY> struct Container {  
    typedef typename AY::template Rebind<X>::Other AX; // correct  
};  
  
```