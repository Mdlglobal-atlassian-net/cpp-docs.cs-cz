---
title: "Číselné literály, logické a literály typu ukazatele (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- literals, C++
- constants, literals
- literals [C++]
ms.assetid: 17c09fc3-3ad7-47e2-8b48-ba8ae994edc8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 91f79a2703dee8a162b971a78eba7e13a9849b43
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="numeric-boolean-and-pointer-literals--c"></a>Číselné literály, logické a literály typu ukazatele (C++)
Literál je program elementu, který přímo představuje hodnotu. Tento článek se zabývá literály typu integer, s plovoucí desetinnou čárkou, logické a ukazatel. Informace o řetězce a znak literály najdete v tématu [řetězec a znakové literály (C++)](../cpp/string-and-character-literals-cpp.md). Můžete také definovat vlastní literály na základě některé z těchto kategorií; Další informace najdete v části [uživatelem definované literály (C++)](../cpp/user-defined-literals-cpp.md)  
  
 . Literály v mnoha kontexty, ale většina můžete použít běžně inicializovat proměnné s názvem a předání argumentů do funkce:  
  
```  
const int answer = 42; // integer literal  
double d = sin(108.87);     //floating point literal passed to sin function  
bool b = true;              // boolean literal  
MyClass* mc = nullptr;      // pointer literal  
  
```  
  
 Někdy je důležité pro oznámení kompilátoru, jak interpretovat literál nebo jaké konkrétního typu poskytnout k němu. Provedete to přidáním předpony nebo přípony k literál. Například předponu 0 x říká kompilátoru interpretovat číslo následujícího jako šestnáctkové hodnoty, například 0x35. Přípona Vyžádat říká kompilátoru zacházet s hodnota `unsigned long long` typu, jako 5894345ULL. Najdete v následujících částech úplný seznam předpon a přípony pro každý typ literálu.  
  
## <a name="syntax"></a>Syntaxe  
  
## <a name="integer-literals"></a>Literály celé číslo  
 Celé číslo literály začínat číslicí a mít bez zlomkové části nebo exponenty. Ve formuláři decimal, osmičková nebo hexadecimální můžete zadat literály celé číslo. Je možné určit typy se znaménkem nebo bez znaménka, dlouhé nebo krátké.  
  
 Pokud žádné předponu nebo příponu, kompilátor získáte typ integrální literálovou hodnotou `int` (32bitová verze), bude-li hodnotu, jinak se bude poskytněte typ `long long` (64bitová verze).  
  
 K určení desetinné celočíselný literál, začněte specifikace s nenulovou číslice. Příklad:  
  
```  
int i = 157;   // Decimal literal  
int j = 0198;       // Not a decimal number; erroneous octal literal  
int k = 0365;       // Leading zero specifies octal literal, not decimal  
int m = 36'000'000  // digit separators make large values more readable  
int   
```  
  
 Chcete-li zadat osmičková celočíselný literál, začněte specifikace s 0, za nímž následuje posloupností číslic v rozsahu 0 až 7. Číslice 8 a 9 jsou chyby v určení osmičková literál. Příklad:  
  
```  
int i = 0377;   // Octal literal  
int j = 0397;        // Error: 9 is not an octal digit  
```  
  
 Chcete-li zadat šestnáctkové celočíselný literál, začněte specifikace s `0x` nebo `0X` (v případě "x", nezáleží), za nímž následuje posloupností číslic v rozsahu `0` prostřednictvím `9` a `a` (nebo `A`) prostřednictvím `f` (nebo `F`). Šestnáctkové číslice `a` (nebo `A`) až `f` (nebo `F`) představují hodnoty v rozsahu 10 až 15. Příklad:  
  
```  
int i = 0x3fff;   // Hexadecimal literal  
int j = 0X3FFF;        // Equal to i  
```  
  
 Pokud chcete zadat typ bez znaménka, použijte buď **u** nebo **U** příponu. K určení typu long, použijte buď **l** nebo **L** příponu. Určení typu integrální 64-bit, použijte UDOU nebo udou příponu. Přípona i64 se pořád podporuje, ale měli vyhnout, protože je specifické pro Microsoft a není přenosné. Příklad:  
  
```  
unsigned val_1 = 328u;             // Unsigned value  
long val_2 = 0x7FFFFFL;                 // Long value specified   
                                        //  as hex literal  
unsigned long val_3 = 0776745ul;        // Unsigned long value  
auto val_4 = 108LL;                           // signed long long  
auto val_4 = 0x8000000000000000ULL << 16;     // unsigned long long   
```  
  
 **Oddělovače číslice**: znak jednoduchou uvozovku (apostrof) můžete oddělit místo hodnoty ve větší počty snadnější pro člověka ke čtení. Oddělovače mít žádný vliv na kompilace.  
  
```  
long long i = 24'847'458'121  
```  
  
## <a name="floating-point-literals"></a>Plovoucí bodu literály  
 S plovoucí desetinnou čárkou literály zadejte hodnoty, které musí mít zlomkové části. Tyto hodnoty obsahovat desetinných míst (**.**) a může obsahovat exponenty.  
  
 S plovoucí desetinnou čárkou literály mít "mantisa,", který určuje hodnotu číslo, "exponentem," který určuje odhad čísla, a volitelné příponu, která určuje typ je literál. Mantisa je zadána jako posloupnost číslic následovaných čárkou a je následována řadou číslic představující zlomkovou část čísla. Příklad:  
  
```  
18.46  
38.  
```  
  
 Exponent, pokud je k dispozici, určuje velikost čísla jako mocninu 10, jak je znázorněno v následujícím příkladu:  
  
```  
18.46e0      // 18.46  
18.46e1           // 184.6  
```  
  
 Exponent, může být určen pomocí **e** nebo **E**, které mají stejný význam, za nímž následuje symbolem volitelné (+ nebo -) a posloupností číslic.  Je-li exponent použit, koncová desetinná čárka není nutná u celých čísel, jako je `18E0`.  
  
 S plovoucí desetinnou čárkou literály jako výchozí typ **dvojité**. Pomocí přípon **f** nebo **l** (nebo **F** nebo **L** – přípona není velká a malá písmena), je literál lze zadat jako  **float** nebo `long double`, v uvedeném pořadí.  
  
 I když `long double` a **dvojité** mají stejnou reprezentaci, nejsou stejného typu. Například je možné mít přetížené funkce jako  
  
```  
void func( double );  
```  
  
 and  
  
```  
void func( long double );  
```  
  
## <a name="boolean-literals"></a>Boolean – literály  
 Logická hodnota literály jsou `true` a `false`.  
  
## <a name="pointer-literal-c11"></a>Literál ukazatele (C ++ 11)  
 Zavádí C++ [nullptr](../cpp/nullptr.md) literálu zadejte ukazatel inicializovat nula. V přenosných kódu `nullptr` místo integrální typ nula nebo makra například NULL by použít.  
  
## <a name="binary-literals-c14"></a>Binární literály (C ++ 14)  
 Při použití lze zadat binární literál `0B` nebo `0b` předponu posloupnost na 1 a na 0:  
  
```  
  
auto x = 0B001101 ; // int  
auto y = 0b000001 ; // int  
```  
  
## <a name="avoid-using-literals-as-magic-constants"></a>Nepoužívejte literály jako "magic konstanty"  
 Literály přímo v výrazy a příkazy můžete použít, i když není vždy dobrým programovacím postupem:  
  
```  
if (num < 100)  
    return "Success";  
  
```  
  
 V předchozím příkladu může být vhodnější použít s názvem konstanta, která přenese tak jasné význam, například "MAXIMUM_ERROR_THRESHOLD". A pokud návratovou hodnotu, kterou "ÚSPĚCH" je zobrazen pro koncové uživatele a pak může být vhodnější použít s názvem řetězcová konstanta, které můžou být uložené na jednom místě v souboru, ze které je možné lokalizovat do jiných jazyků. Použití s názvem konstanty pomáhá ostatním a také sami, abyste porozuměli záměr kódu.  
  
## <a name="see-also"></a>Viz také  
 [Lexikální pravidla](../cpp/lexical-conventions.md)   
 [C++ textové literály](../cpp/string-and-character-literals-cpp.md)   
 [Uživateli definované literály C++](../cpp/user-defined-literals-cpp.md)