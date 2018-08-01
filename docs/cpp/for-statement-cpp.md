---
title: for – příkaz (C++) | Dokumentace Microsoftu
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
ms.openlocfilehash: feb14056e3054cdf0e802b16ce9ff20f67da43fe
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39401571"
---
# <a name="for-statement-c"></a>for – příkaz (C++)
Spustí příkaz opakovaně, dokud podmínka nebude nepravda. Informace o podle rozsahu je pro příkaz, naleznete v tématu [Range-based for Statement (C++)](../cpp/range-based-for-statement-cpp.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
for ( init-expression ; cond-expression ; loop-expression )   
    statement;  
```  
  
## <a name="remarks"></a>Poznámky  
 Použití **pro** příkaz k vytvoření smyček, které musí být spuštěn zadaného počtu opakování.  
  
 **Pro** příkaz se skládá ze tří volitelných částí, jak je znázorněno v následující tabulce.  
  
### <a name="for-loop-elements"></a>Prvky smyčky for  
  
|Název syntaxe|Při provedení|Popis|  
|-----------------|-------------------|-----------------|  
|`init-expression`|Před jakýmkoli jiným prvkem příkazu **pro** příkazu `init-expression` provedeno pouze jednou. Ovládací prvek pak předá do `cond-expression`.|Často se používá k inicializaci indexů smyčky. Může obsahovat výrazy nebo deklarace.|  
|`cond-expression`|Před spuštěním každé iterace `statement`, včetně první iterace. `statement` provádí pouze v případě `cond-expression` vyhodnotí na hodnotu true (nenulový).|Výraz, jehož výsledkem je integrální typ nebo typ třídy, která má jednoznačný převod na integrální typ. Obvykle se používá k testování kritérií pro ukončení smyčky.|  
|`loop-expression`|Na konci každé iterace `statement`. Po `loop-expression` provádí, `cond-expression` vyhodnocena.|Obvykle se používá pro zvýšení indexu smyčky.|  
  
 Následující příklady ukazují různé způsoby použití **pro** příkazu.  
  
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
  
 `init-expression` a `loop-expression` může obsahovat více příkazů oddělených čárkami. Příklad:  
  
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
  
 `loop-expression` může být zvýšena nebo snížen či jinak změněn jiným způsobem.  
  
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
  
 A **pro** smyčky skončí, když [přerušení](../cpp/break-statement-cpp.md), [vrátit](../cpp/return-statement-cpp.md), nebo [goto](../cpp/goto-statement-cpp.md) (na označený příkaz mimo **pro**smyčky) v rámci `statement` provádí. A [pokračovat](../cpp/continue-statement-cpp.md) výroky **pro** smyčku ukončí pouze aktuální iteraci.  
  
 Pokud `cond-expression` je tento parametr vynechán, bude považován za true a **pro** nebude bez ukončení smyčky **přerušení**, **vrátit**, nebo **goto** v rámci `statement`.  
  
 I když jsou tři pole příkazu **pro** obvykle používána pro inicializaci, ukončení, testování a zvyšování hodnoty, nejsou omezena na tato použití. Následující kód například tiskne čísla 0 až 4. V takovém případě `statement` je příkaz null:  
  
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
 Standard jazyka C++ říká, že proměnná deklarovaná ve **pro** smyčky se dostanou mimo rozsah po **pro** skončení smyčky. Příklad:  
  
```cpp  
for (int i = 0 ; i < 5 ; i++) {  
   // do something  
}  
// i is now out of scope under /Za or /Zc:forScope  
```  
  
 Ve výchozím nastavení v části [/Ze](../build/reference/za-ze-disable-language-extensions.md), proměnná deklarovaná ve **pro** smyčky zůstává v oboru až do **pro** smyčky ukončení nadřazeného oboru.  
  
 [/ Zc: forscope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) povoluje standardní chování proměnných deklarovaných ve smyčkách for aniž byste museli zadat `/Za`.  
  
 Je také možné použít rozdíly oboru **pro** smyčky k předeklarování proměnných v rámci `/Ze` následujícím způsobem:  
  
```cpp  
// for_statement5.cpp  
int main(){  
   int i = 0;   // hidden by var with same name declared in for loop  
   for ( int i = 0 ; i < 3; i++ ) {}  
  
   for ( int i = 0 ; i < 3; i++ ) {}  
}  
```  
  
 Toto lépe napodobuje standardní chování proměnné deklarované ve **pro** smyčku, která vyžaduje proměnné deklarované v **pro** smyčky po jejím dokončení dostaly mimo obor. Pokud je proměnná deklarována v **pro** smyčky, kompilátor ji interně zvýší úroveň na místní proměnnou **pro** oboru nadřazeném smyčce i v případě, že místní proměnná se stejným názvem již existuje.  
  
## <a name="see-also"></a>Viz také:  
 [Příkazy iterace](../cpp/iteration-statements-cpp.md)   
 [klíčová slova](../cpp/keywords-cpp.md)   
 [while – příkaz (C++)](../cpp/while-statement-cpp.md)   
 [Proveďte-while – příkaz (C++)](../cpp/do-while-statement-cpp.md)   
 [Příkaz For založený na rozsahu (C++)](../cpp/range-based-for-statement-cpp.md)