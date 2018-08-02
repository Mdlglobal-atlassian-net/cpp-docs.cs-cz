---
title: Switch – příkaz (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- default_cpp
- switch_cpp
- case_cpp
dev_langs:
- C++
helpviewer_keywords:
- switch keyword [C++]
- case keyword [C++], in switch statements
- default keyword [C++]
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a5a8858d48a38d42dea7fba0fdce7c3a4d407a3a
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39462183"
---
# <a name="switch-statement-c"></a>switch – příkaz (C++)
Umožňuje výběr mezi více částí kódu v závislosti na hodnotě integrálního výrazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
   switch ( init; expression )  
   case constant-expression : statement  
   [default  : statement]  
```  
  
## <a name="remarks"></a>Poznámky  
 *Výraz* musí být integrálního typu nebo typu třídy, pro kterou existuje jednoznačný převod na integrální typ. Integrální propagace se provádí, jak je popsáno v [standardní převody](standard-conversions.md).  
  
 **Přepnout** tělo s příkazy se skládá z řady **případ** popisky a volitelně **výchozí** popisek. Žádné dva konstantní výrazy u **případ** nemohou hodnotit stejnou hodnotu. **Výchozí** popisek se může objevit pouze jednou. Označené příkazy nejsou syntaktickými požadavky, ale **přepnout** příkaz je bez nich nemá význam.   Výchozí příkaz se nemusí nacházet pouze na konci; může se zobrazit kdekoli v textu příkazu switch. Případ nebo výchozí popisek může být použito pouze uvnitř příkazu switch.  
  
 *Konstantní výraz* v každém **případ** popisek je převeden na typ *výraz* a ve srovnání s *výraz* pro rovnost. Ovládací prvek se předá příkazu jehož **případ** *konstantní výraz* odpovídá hodnotě *výraz*. Výsledné chování je uvedeno v následující tabulce.  
  
### <a name="switch-statement-behavior"></a>Chování příkazů přepínače  
  
|Podmínka|Akce|  
|---------------|------------|  
|Převedená hodnota odpovídá zpropagovanému kontrolnímu výrazu.|Ovládací prvek bude převeden na příkaz následující po daném štítku.|  
|Žádná Konstanta neodpovídá konstantě v **případ** popisků; **výchozí** popisek je k dispozici.|Ovládací prvek bude převeden na **výchozí** popisek.|  
|Žádná Konstanta neodpovídá konstantě v **případ** popisků; **výchozí** popisek není k dispozici.|Ovládací prvek bude převeden na příkaz následující po **přepnout** příkazu.|  
  
 Pokud je nalezen odpovídající výraz, ovládací prvek není ovlivněn následujícími **případ** nebo **výchozí** popisky. [Přerušení](../cpp/break-statement-cpp.md) prohlášení se používá k zastavení spuštěného procesu a předání řízení příkazu následujícímu po **přepnout** příkazu. Bez **přerušení** prohlášení, každý příkaz ze spárovaného **případ** popisek na konec objektu **přepnout**, včetně **výchozí**, je spustit. Příklad:  
  
```cpp 
// switch_statement1.cpp  
#include <stdio.h>  
  
int main() {  
   char *buffer = "Any character stream";  
   int capa, lettera, nota;  
   char c;  
   capa = lettera = nota = 0;  
  
   while ( c = *buffer++ )   // Walks buffer until NULL  
   {  
      switch ( c )  
      {  
         case 'A':  
            capa++;  
            break;  
         case 'a':  
            lettera++;  
            break;  
         default:  
            nota++;  
      }  
   }  
   printf_s( "\nUppercase a: %d\nLowercase a: %d\nTotal: %d\n",  
      capa, lettera, (capa + lettera + nota) );  
}  
```  
  
 Ve výše uvedeném příkladu `capa` se zvýší, pokud `c` je velké písmeno `A`. **Přerušení** příkazem za `capa++` ukončí provádění **přepnout** tělo s příkazy a řízení se předá **při** smyčky. Bez **přerušení** prohlášení, provádění by "předáno" do další příkaz s popiskem, tak, aby `lettera` a `nota` by se také zvýší. K podobnému účelu slouží **přerušení** příkaz pro `case 'a'`. Pokud `c` je malým `a`, `lettera` je zvýšen a **přerušení** příkaz ukončí **přepnout** těla příkazu. Pokud `c` není `a` nebo `A`, **výchozí** je proveden příkaz.  

 **Visual Studio 2017 a novější:** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)) `[[fallthrough]]` je zadán atribut v standardu C ++ 17. Je možné v **přepnout** příkaz jako Nápověda pro kompilátor (nebo každému, kdo čte kód) je určena propuštěním chování. Kompilátor Visual C++ aktuálně neupozorňuje na fallthrough chování, tento atribut nemá žádný vliv na chování kompilátoru. Všimněte si, že atribut je použit prázdný příkaz v rámci příkaz s popiskem; jinými slovy je nezbytné středník.

```cpp
int main()
{
    int n = 5;
    switch (n)
    {

    case 1:
        a();
        break;
    case 2:
        b();
        d();
        [[fallthrough]]; // I meant to do this!
    case 3:
        c();
        break;
    default:
        d();
        break;
    }

    return 0;
}
```

 **Visual Studio 2017 verze 15.3 nebo novější** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): příkaz switch může zavádět a inicializujte proměnnou, jejíž rozsah je omezen na blok příkazu switch:

```cpp
 switch (Gadget gadget(args); auto s = gadget.get_status())
        {
        case status::good:
            gadget.zip();
            break;
        case status::bad:
            throw BadGadget();
        };
```

 Vnitřní blok **přepnout** příkaz může obsahovat definice s inicializacemi, dokud budou dosažitelné – to znamená nebudou obcházeny všemi možnými cestami spuštění. Názvy zavedené pomocí těchto prohlášení mají místní rozsah. Příklad:  
  
```cpp  
// switch_statement2.cpp  
// C2360 expected  
#include <iostream>  
using namespace std;  
int main(int argc, char *argv[])  
{  
   switch( tolower( *argv[1] ) )  
   {  
       // Error. Unreachable declaration.  
       char szChEntered[] = "Character entered was: ";  
  
   case 'a' :  
       {  
       // Declaration of szChEntered OK. Local scope.  
       char szChEntered[] = "Character entered was: ";  
       cout << szChEntered << "a\n";  
       }  
       break;  
  
   case 'b' :  
       // Value of szChEntered undefined.  
       cout << szChEntered << "b\n";  
       break;  
  
   default:  
       // Value of szChEntered undefined.  
       cout << szChEntered << "neither a nor b\n";  
       break;  
   }  
}  
```  
  
 A **přepnout** příkaz mohou být vnořené. V takových případech **případ** nebo **výchozí** popisky přidružují k nejbližšímu **přepnout** příkaz, který je obklopuje.  

## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Microsoft C neomezuje počet případových hodnoty v **přepnout** příkazu. Počet je omezen pouze dostupnou paměť. ANSI C vyžaduje alespoň 257 povolených popisků případu v **přepnout** příkazu.  
  
 Výchozí nastavení pro Microsoft C je, že jsou povolena rozšíření společnosti Microsoft. Použití [/Za](../build/reference/za-ze-disable-language-extensions.md) – možnost kompilátoru pro zákaz těchto rozšíření.  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [Příkazy výběru](../cpp/selection-statements-cpp.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)   