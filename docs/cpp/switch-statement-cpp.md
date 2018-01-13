---
title: "přepínače – příkaz (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- default_cpp
- switch_cpp
- case_cpp
dev_langs: C++
helpviewer_keywords:
- switch keyword [C++]
- case keyword [C++], in switch statements
- default keyword [C++]
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e668756e8cabafbdef522d6754487efe452f96de
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="switch-statement-c"></a>switch – příkaz (C++)
Umožňuje výběr mezi více oddílů kódu, v závislosti na hodnotě výrazu integrální.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
   switch ( init; expression )  
   case constant-expression : statement  
   [default  : statement]  
```  
  
## <a name="remarks"></a>Poznámky  
 *Výraz* musí být celočíselné typu nebo typu třídy, pro kterou je konverzi jednoznačným integrální typu. Integrální povýšení se provádí, jak je popsáno v [standardní převody](standard-conversions.md).  
  
 `switch` Těla příkazu se skládá z řady **případ** popisky a volitelné **výchozí** popisek. Žádné dvě konstantní výrazy v **případ** příkazy lze vyhodnotit na stejnou hodnotu. **Výchozí** popisek může vyskytovat pouze jednou. Příkaz s popiskem nejsou syntaktické požadavky, ale `switch` příkaz nemá význam bez nich.   Příkaz výchozí nemusí pocházet na konci; může vyskytovat kdekoli v těle příkazem switch. Případ nebo výchozí štítek může vyskytovat pouze uvnitř příkazu switch.  
  
 *Konstantní výraz* v každé **případ** popisek je převést na typ *výraz* a v porovnání s *výraz* pro rovnosti. Ovládací prvek předává do příkazu, jehož **případ** *konstantní výraz* odpovídá hodnotě *výraz*. Výsledné chování je uvedené v následující tabulce.  
  
### <a name="switch-statement-behavior"></a>Chování příkazů přepínače  
  
|Podmínka|Akce|  
|---------------|------------|  
|Převedená hodnota odpovídá propagovaných řízení výrazu.|Ovládací prvek je přenesen do příkazu následující tohoto popisku.|  
|Konstanty neodpovídají konstanty v **případ** popisků; **výchozí** popisek je k dispozici.|Ovládací prvek je přenesen na **výchozí** popisek.|  
|Konstanty neodpovídají konstanty v **případ** popisků; **výchozí** popisek není k dispozici.|Ovládací prvek je přenesen do příkazu po `switch` příkaz.|  
  
 Pokud je nalezen odpovídající výraz, ovládací prvek není bránit následné **případ** nebo **výchozí** popisky. [Zalomení](../cpp/break-statement-cpp.md) příkaz slouží k zastavit provádění a přenos řízení na příkaz po `switch` příkaz. Bez **zalomení** příkaz, každý příkaz z odpovídající **případ** popisek na konec `switch`, včetně **výchozí**, je proveden. Příklad:  
  
```  
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
  
 V předchozím příkladu `capa` se zvýší, pokud `c` je velkým `A`. `break` Příkaz po `capa++` ukončí provádění `switch` těla příkazu a řízení předá do `while` smyčky. Bez `break` prohlášení, provádění by "předáno" do další příkaz s popiskem, tak, aby `lettera` a `nota` by se taky zvýší. Je podobné účel poskytovaný `break` příkaz pro `case 'a'`. Pokud `c` je jedno malé písmeno `a`, `lettera` se zvýší a `break` ukončuje příkaz `switch` těla příkazu. Pokud `c` není `a` nebo `A`, `default` spustit příkaz.  

 **Visual Studio 2017 a novější:** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)) `[[fallthrough]]` atribut je uveden v standardu C ++ 17. Je možné v `switch` příkaz jako nápovědu pro kompilátor (nebo na nikoho čtení kódu) je určený chování pro tento patří. – Kompilátor Visual C++ aktuálně neupozorňuje na fallthrough chování, takže tento atribut má chování kompilátoru žádný vliv. Všimněte si, že atribut je použit prázdný příkaz v rámci příkaz s popiskem; jinými slovy je nutné středník.

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

 **Visual Studio 2017 verze 15.3 a novější** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): příkaz switch může znamenat a inicializace proměnné, jejíž obor je omezený na blok příkazu switch:

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

 Vnitřní blok `switch` příkaz může obsahovat definice s inicializacích, dokud jsou dostupné – to znamená, není přeskočí všechny možné provádění cesty. Názvy zavedená pomocí tyto deklarace mít místní rozsah. Příklad:  
  
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
  
 A `switch` příkaz mohou být použity. V takových případech **případ** nebo **výchozí** popisky přidružit na nejbližší `switch` příkaz, který je uzavře.  

 
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Microsoft C neomezuje počet případů hodnot v `switch` příkaz. Číslo je omezena pouze dostupné paměti. ANSI C vyžaduje alespoň 257 případu popisky povolené v `switch` příkaz.  
  
 Výchozí nastavení pro Microsoft C je, že jsou povolené rozšíření Microsoft. Použití [/Za](../build/reference/za-ze-disable-language-extensions.md) – možnost kompilátoru zakázání tyto rozšíření.  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Příkazy výběru](../cpp/selection-statements-cpp.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)   
 