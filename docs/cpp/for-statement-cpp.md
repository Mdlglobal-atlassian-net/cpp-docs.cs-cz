---
title: pro příkaz (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- for keyword [C++]
ms.assetid: 6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 38181a43134c35c4db1db3d78a79d3338934b7d2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32417181"
---
# <a name="for-statement-c"></a>for – příkaz (C++)
Spustí příkaz opakovaně, dokud podmínka nebude nepravda. Informace o založený na rozsahu pro příkaz, naleznete v části [na základě rozsahu pro příkaz (C++)](../cpp/range-based-for-statement-cpp.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
for ( init-expression ; cond-expression ; loop-expression )   
    statement;  
```  
  
## <a name="remarks"></a>Poznámky  
 Použití `for` příkaz k vytvoření smyčky, které musí být spuštěn zadaného počtu opakování.  
  
 `for` Příkaz se skládá ze tří částí volitelné, jak je znázorněno v následující tabulce.  
  
### <a name="for-loop-elements"></a>Prvky smyčky for  
  
|Název syntaxe|Při provedení|Popis|  
|-----------------|-------------------|-----------------|  
|`init-expression`|Před jakýkoli další prvek **pro** příkaz `init-expression` se spustí jenom jednou. Řízení potom předává do `cond-expression`.|Často se používá k inicializaci indexů smyčky. Může obsahovat výrazy nebo deklarace.|  
|`cond-expression`|Před spuštěním každé iteraci `statement`, včetně první iterací. `statement` se spustí pouze v případě `cond-expression` vyhodnotí na hodnotu true (nenulové hodnoty).|Výraz, jehož výsledkem je integrální typ nebo typ třídy, která má jednoznačný převod na integrální typ. Obvykle se používá k testování kritérií pro ukončení smyčky.|  
|`loop-expression`|Na konci každé iteraci `statement`. Po `loop-expression` proveden, `cond-expression` vyhodnotí.|Obvykle se používá pro zvýšení indexu smyčky.|  
  
 Následující příklady ukazují různé způsoby použití `for` příkaz.  
  
```cpp  
#include <iostream>  
using namespace std;  
  
int main() {  
    // The counter variable can be declared in the init-expression.  
    for (int i = 0; i < 2; i++ ){   
       cout << i;  
    }  
    // Output: 01  
    // The counter variable can be declared outside the for loop.  
    int i;  
    for (i = 0; i < 2; i++){  
        cout << i;  
    }  
    // Output: 01  
    // These for loops are the equivalent of a while loop.  
    i = 0;  
    while (i < 2){  
        cout << i++;  
    }  
}  
    // Output: 012  
```  
  
 `init-expression` a `loop-expression` může obsahovat více příkazů, které jsou oddělené čárkami. Příklad:  
  
```cpp  
#include <iostream>  
using namespace std;  
  
int main(){  
    int i, j;  
    for ( i = 5, j = 10 ; i + j < 20; i++, j++ ) {  
        cout << "i + j = " << (i + j) << '\n';  
    }  
}  
    // Output:  
    i + j = 15  
    i + j = 17  
    i + j = 19  
```  
  
 `loop-expression` může být zvýšena nebo snížena nebo upravené jinými způsoby.  
  
```cpp  
#include <iostream>  
using namespace std;  
  
int main(){  
for (int i = 10; i > 0; i--) {  
        cout << i << ' ';  
    }  
    // Output: 10 9 8 7 6 5 4 3 2 1  
    for (int i = 10; i < 20; i = i+2) {  
        cout << i << ' ';  
    }  
    // Output: 10 12 14 16 18  
```  
  
 A `for` ukončí smyčky, kdy [zalomení](../cpp/break-statement-cpp.md), [vrátit](../cpp/return-statement-cpp.md), nebo [goto](../cpp/goto-statement-cpp.md) (pro příkaz s popiskem mimo **pro** smyčky) v rámci `statement` se spustí. A [pokračovat](../cpp/continue-statement-cpp.md) příkaz v `for` ukončí jenom na aktuální iteraci smyčky.  
  
 Pokud `cond-expression` je tento parametr vynechán, bude považován za true a **pro** nebude bez ukončení smyčky `break`, `return`, nebo `goto` v rámci `statement`.  
  
 I když tři pole `for` příkaz se obvykle používají pro inicializaci testování pro ukončení, a roste, nejsou omezeny na těchto použití. Následující kód například tiskne čísla 0 až 4. V takovém případě `statement` je null příkaz:  
  
```cpp  
#include <iostream>  
using namespace std;  
  
int main()  
{  
    int i;  
    for( i = 0; i < 5; cout << i << '\n', i++){  
        ;  
    }  
}  
```  
  
## <a name="for-loops-and-the-c-standard"></a>Smyčky for a standard jazyka C++  
 Standardní C++ říká, že proměnná definovaná v `for` smyčky se dostala mimo rozsah po `for` cykly elementy end. Příklad:  
  
```cpp  
for (int i = 0 ; i < 5 ; i++) {  
   // do something  
}  
// i is now out of scope under /Za or /Zc:forScope  
```  
  
 Ve výchozím nastavení v části [/Ze](../build/reference/za-ze-disable-language-extensions.md), proměnná definovaná v `for` smyčky zůstane v oboru, dokud `for` smyčky je obklopuje koncích obor.  
  
 [/Zc:forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) umožňuje standardní chování proměnných deklarovaných v smyčky for, aniž by museli zadat /Za.  
  
 Je také možné použít z oboru rozdíly `for` opakování ve smyčce bude redeclare proměnné v části /Ze následujícím způsobem:  
  
```cpp  
// for_statement5.cpp  
int main(){  
   int i = 0;   // hidden by var with same name declared in for loop  
   for ( int i = 0 ; i < 3; i++ ) {}  
  
   for ( int i = 0 ; i < 3; i++ ) {}  
}  
```  
  
 Tím přesněji napodobuje standardní chování proměnná definovaná v `for` smyčky, který vyžaduje proměnných deklarovaných v `for` opakování ve smyčce bude po dokončení smyčky se dostala mimo rozsah. Když je proměnná definovaná v `for` smyčky, kompilátor interně zvýší úroveň ji do místní proměnné v `for` smyčky je obklopuje oboru, i v případě, že místní proměnné se stejným názvem již existuje.  
  
## <a name="see-also"></a>Viz také  
 [Příkazy iterace](../cpp/iteration-statements-cpp.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [while – příkaz (C++)](../cpp/while-statement-cpp.md)   
 [Proveďte-while – příkaz (C++)](../cpp/do-while-statement-cpp.md)   
 [Příkaz For založený na rozsahu (C++)](../cpp/range-based-for-statement-cpp.md)