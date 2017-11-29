---
title: "Sémantika výrazů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- grammar, expressions
- expressions [C++], semantics
- expression evaluation
- expression evaluation, about expression evaluation
ms.assetid: 4a792154-533b-48b9-8709-31bfc170f0a7
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6c41ed94dcaee6632c3db7ae8590d570bb0e06c0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="semantics-of-expressions"></a>Sémantika výrazů
Výrazy jsou vyhodnocovány podle priority a seskupení jejich operátorů. ([Operátorů a Asociativnost](../cpp/cpp-built-in-operators-precedence-and-associativity.md) v [lexikální pravidla](../cpp/lexical-conventions.md), znázorňuje vztahy C++ operátory kladou na výrazy.)  
  
## <a name="order-of-evaluation"></a>Pořadí vyhodnocení  
 Vezměte v úvahu v tomto příkladu:  
  
```cpp  
// Order_of_Evaluation.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
int main()  
{  
    int a = 2, b = 4, c = 9;  
  
    cout << a + b * c << "\n";  
    cout << a + (b * c) << "\n";  
    cout << (a + b) * c << "\n";  
}  
```  
  
```Output  
38  
38  
54  
```  
  
 ![Pořadí vyhodnocení ve výrazu](../cpp/media/vc38zv1.gif "vc38ZV1")  
Pořadí vyhodnocení výrazu  
  
 Pořadí, ve kterém je výraz podle výše uvedeného obrázku vyhodnocen, se stanoví pomocí přednosti a asociativity operátorů:  
  
1.  Násobení (*) má v tomto výrazu nejvyšší prioritu, proto je podvýraz `b * c` vyhodnocen jako první.  
  
2.  Sčítání (+) má další nejvyšší prioritu, takže hodnota proměnné `a` je přičtena k výsledku operace s proměnnými `b` a `c`.  
  
3.  Levý posun (<<) má ve výrazu nejnižší prioritu, ale existují dva výskyty. Vzhledem k tomu, že operátor levého posunu seskupuje zleva doprava, je levý podvýraz vyhodnocen jako první, a potom je vyhodnocen pravý podvýraz.  
  
 Použití závorek k seskupení podvýrazů mění prioritu a také pořadí, ve kterém je výraz vyhodnocen, jak je znázorněno na následujícím obrázku.  
  
 ![Pořadí vyhodnocení výrazu v závorkách](../cpp/media/vc38zv2.gif "vc38ZV2")  
Pořadí vyhodnocení výrazu se závorkami  
  
 Výrazy, například na výše uvedeném obrázku, jsou vyhodnoceny výhradně z hlediska jejich vedlejších účinků, v tomto případě pro přenos informací na standardní výstup zařízení.  
  
## <a name="notation-in-expressions"></a>Zápis ve výrazech  
 Jazyk C++ určuje určité kompatibility při zadávání operandy. Následující tabulka uvádí typy operandů přijatelné pro operátory, které vyžadují operandy typu *typu*.  
  
### <a name="operand-types-acceptable-to-operators"></a>Typy operandů přijatelné pro operátory  
  
|Očekávaný typ|Povolené typy|  
|-------------------|-------------------|  
|*Typ*|`const`*typu*<br /> `volatile`*typu*<br /> *Typ*&<br /> `const`*typu*&<br /> `volatile`*typu*&<br /> `volatile const`*typu*<br /> `volatile const`*typu*&|  
|*Typ*\*|*Typ*\*<br /> `const`*typu*\*<br /> `volatile`*typu*\*<br /> `volatile const`*typu*\*|  
|`const`*typu*|*Typ*<br /> `const`*typu*<br />`const`*typu*&|  
|`volatile`*typu*|*Typ*<br /> `volatile`*typu*<br /> `volatile`*typu*&|  
  
 Protože předchozí pravidla lze vždy použít v kombinaci, můžete je nutné zadat const ukazatel na objekt volatile, kde je očekávána ukazatel.  
  
## <a name="ambiguous-expressions"></a>Nejednoznačné výrazy  
 Některé výrazy jsou ve svém významu nejednoznačné. Tyto výrazy se nejčastěji vyskytují, je-li hodnota objektu ve stejném výrazu změněna více než jednou. Tyto výrazy se spoléhají na určité pořadí vyhodnocování tam, kde jazyk žádné nedefinuje. Podívejte se na následující příklad:  
  
```  
int i = 7;  
  
func( i, ++i );  
```  
  
 Jazyk C++ nezaručuje pořadí, ve kterém jsou argumenty pro volání funkce vyhodnocovány. Proto by v předcházejícím příkladu mohla `func` pro své parametry přijímat hodnoty 7 a 8 nebo 8 a 8 podle toho, zda jsou parametry vyhodnoceny zleva doprava nebo zprava doleva.  
  
## <a name="c-sequence-points-microsoft-specific"></a>Body sekvence jazyka C++ (specifické pro Microsoft)  
 Výraz může změnit hodnotu objektu mezi po sobě jdoucími „body sekvence“ pouze jednou.  
  
 Definice jazyka C++ aktuálně nespecifikuje body sekvence. Jazyk C++ společnosti Microsoft používá stejné body sekvence jako standard ANSI C pro všechny výrazy zahrnující operátory jazyka C a nevyžaduje přetížené operátory. Pokud jsou operátory přetíženy, sémantika se změní ze sekvence operátorů na sekvenci volání funkce. Jazyk C++ společnosti Microsoft používá následující body sekvence:  
  
-   Levý operand logického operátoru AND (&&). Levý operand logického operátoru AND je kompletně vyhodnocen a všechny vedlejší účinky jsou před pokračováním dokončeny. Není zaručeno, že bude pravý operand logického operátoru AND vyhodnocen.  
  
-   Levý operand logický operátor OR (&#124; &#124;). Levý operand logického operátoru OR je kompletně vyhodnocen a všechny vedlejší účinky jsou před pokračováním dokončeny. Není zaručeno, že bude pravý operand logického operátoru OR vyhodnocen.  
  
-   Levý operand operátoru čárky. Levý operand logického operátoru čárky je kompletně vyhodnocen a všechny vedlejší účinky jsou před pokračováním dokončeny. Oba operandy operátoru čárky jsou vždy vyhodnoceny.  
  
-   Operátor volání funkce. Výraz volání funkce a všechny argumenty funkce, včetně výchozích argumentů, jsou vyhodnoceny a všechny vedlejší účinky dokončeny před vstupem do této funkce. Neexistuje žádné zadané pořadí vyhodnocování mezi argumenty nebo výrazem volání funkce.  
  
-   První operand podmíněného operátoru. První operand podmíněného operátoru je kompletně vyhodnocen a všechny vedlejší účinky jsou před pokračováním dokončeny.  
  
-   Konec úplného výrazu inicializace, jako je konec inicializace v příkazu deklarace.  
  
-   Výraz v příkazu výrazu. Příkazy výrazů se skládají z volitelného výrazu následovaného středníkem (;). Tento výraz je zcela vyhodnocen pro jeho vedlejší účinky.  
  
-   Řídicí výraz v příkazu výběru (if nebo switch). Výraz je vyhodnocen úplně a všechny vedlejší účinky jsou dokončeny před provedením kódu závislého na výběru.  
  
-   Řídicí výraz příkazu while nebo do. Výraz je zcela vyhodnocen a všechny vedlejší účinky jsou dokončeny před vykonáním jakýchkoli příkazů v další iteraci smyčky while nebo do.  
  
-   Všechny tři výrazy příkazu for. Každý výraz je úplně vyhodnocen a všechny vedlejší účinky dokončeny před přesunem k dalšímu výrazu.  
  
-   Výraz v příkazu return. Výraz je vyhodnocován úplně a všechny vedlejší účinky jsou dokončeny před návratem řízení do funkce volání.  
  
## <a name="see-also"></a>Viz také  
 [Výrazy](../cpp/expressions-cpp.md)