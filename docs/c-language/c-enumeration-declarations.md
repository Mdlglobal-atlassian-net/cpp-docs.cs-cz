---
title: Deklarace výčtů C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declarations, enumerations
- define directive (#define), alternative to
- enumerators, declaring
- '#define directive, alternative to'
- named constants, enumeration declarations
- declaring enumerations
ms.assetid: bd18f673-4dda-4bc1-92fd-d1ce10074910
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 697e4f37c8a59c40df80e29ff89f2021f61fb468
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="c-enumeration-declarations"></a>Deklarace výčtů v jazyce C
Výčet obsahuje sadu s názvem celočíselné konstanty. Deklarace typu výčtu poskytuje název značky – výčet (volitelné) a definuje sadu identifikátorů pojmenované celé číslo (nazývá "– výčet sady," "enumerátor konstanty," "výčty" nebo "členové"). Proměnné s typem výčtu ukládá jednu z hodnot – výčet sady definované typu.  
  
 Proměnné `enum` typ lze použít v indexu výrazy a jako operandy všechny aritmetické a relační operátory. Výčty jako alternativu k `#define` direktivy preprocesoru s výhody, že hodnoty může být generována pro vás a orientují normální oboru pravidla.  
  
 ANSI C výrazů, které definují hodnotu konstanty výčtu vždy mít `int` typ; proto úložiště přidružený proměnné výčtu je místo na disku požadované pro jeden `int` hodnotu. Lze použít konstanta výčtu nebo hodnotu výčtového typu kdekoli jazyka C umožňuje výraz celého čísla.  
  
## <a name="syntax"></a>Syntaxe  
 *enum – specifikátor*:  
 **výčet***identifikátor* opt **{** *enumerátor seznamu* **}**   
  
 **výčet***identifikátor*  
  
 Volitelné *identifikátor* názvy typ výčtu definované *enumerátor seznamu*. Tento identifikátor se často nazývá "značky" výčtu určeného v seznamu. Specifikátor typu formuláře  
  
```  
  
enum  
identifier  
{  
enumerator-list  
}  
  
```  
  
 deklaruje *identifikátor* jako značky výčtu určeného *enumerátor seznamu* nonterminal. *Enumerátor seznamu* definuje "obsah enumerátor." *Enumerátor seznamu* je podrobně popsaná níže.  
  
 Pokud deklarace značky je viditelná, následných deklarace, které používat značky, ale vynechejte *enumerátor seznamu* zadejte dříve deklarované výčtového typu. Značky musí odkazovat definovaný typ výčtu a tento typ výčtu musí být v aktuálním oboru. Vzhledem k tomu, že typ výčtu je definována jinam, *enumerátor seznamu* nezobrazí tuto deklaraci. Deklarace typy odvozené od výčty a `typedef` deklarace pro výčtové typy může použít výčet značky, než je definovaný typ výčtu.  
  
## <a name="syntax"></a>Syntaxe  
 *Enumerátor seznamu*:  
 *Enumerátor*  
  
 *Enumerátor seznamu* **,**  `enumerator`  
  
 `enumerator`:  
 *Konstanta výčtu*  
  
 *Konstanta výčtu***=***konstantní výraz*  
  
 *Konstanta výčtu*:  
 *Identifikátor*  
  
 Každý *konstanta výčtu* v *seznamu výčtu* názvy hodnotu – výčet sady. Ve výchozím nastavení první *konstanta výčtu* souvisí s hodnotou 0. Další *konstanta výčtu* v seznamu souvisí s hodnotou ( *konstantní výraz* + 1), pokud ji explicitně spojit s jinou hodnotou. Název *konstanta výčtu* je ekvivalentní na jeho hodnotu.  
  
 Můžete použít *konstanta výčtu = konstantní výraz* přepsat výchozí pořadí hodnot. Proto pokud *konstanta výčtu = konstantní výraz* se zobrazí v *enumerátor seznamu*, *konstanta výčtu* je spojena s hodnota podle *konstantní výraz*. *Konstantní výraz* musí mít `int` zadejte a může být záporné.  
  
 Následující pravidla platí při členy – výčet sady:  
  
-   Sadu výčet může obsahovat duplicitní konstantní hodnoty. Je třeba přiřadit hodnotu 0 s dva různé identifikátory, třeba s názvem `null` a `zero`, ve stejné sadě.  
  
-   Identifikátory v seznamu výčtu musí být odlišný od dalších identifikátorů ve stejném oboru s stejné viditelnost, včetně běžné názvy proměnných a identifikátory v jiné seznamy výčtu.  
  
-   Výčtové tagy orientují normální oboru pravidla. Musí být odlišné z jiných výčtu, struktury a sjednocení značky s stejně viditelné.  
  
## <a name="examples"></a>Příklady  
 Tyto příklady ilustrují deklarace výčtů:  
  
```  
enum DAY            /* Defines an enumeration type    */  
{  
    saturday,       /* Names day and declares a       */  
    sunday = 0,     /* variable named workday with    */   
    monday,         /* that type                      */  
    tuesday,  
    wednesday,      /* wednesday is associated with 3 */  
    thursday,  
    friday  
} workday;  
```  
  
 Hodnota 0 je přidružen `saturday` ve výchozím nastavení. Identifikátor `sunday` explicitně nastaven na hodnotu 0. Zbývajících identifikátorů mají ve výchozím nastavení hodnoty 1 až 5.  
  
 V tomto příkladu hodnotu ze sady `DAY` je přiřazen k proměnné `today`.  
  
```  
enum DAY today = wednesday;  
```  
  
 Všimněte si, že název konstanta výčtu slouží k přiřazení hodnoty. Vzhledem k tomu `DAY` typ výčtu bylo dříve deklarované, pouze značce – výčet `DAY` je nezbytné.  
  
 Explicitně přiřadit celočíselnou hodnotu proměnné Výčtový typ dat., použijte přetypování:  
  
```  
workday = ( enum DAY ) ( day_value - 1 );  
```  
  
 Toto přetypování se doporučuje v jazyce C, ale není nutné.  
  
```  
enum BOOLEAN  /* Declares an enumeration data type called BOOLEAN */  
{  
    false,     /* false = 0, true = 1 */  
    true   
};   
  
enum BOOLEAN end_flag, match_flag; /* Two variables of type BOOLEAN */  
```  
  
 Toto prohlášení dá se zadat taky jako  
  
```  
enum BOOLEAN { false, true } end_flag, match_flag;\  
```  
  
 nebo jako  
  
```  
enum BOOLEAN { false, true } end_flag;  
enum BOOLEAN match_flag;  
```  
  
 Příklad, který používá tyto proměnné může vypadat například takto:  
  
```  
if ( match_flag == false )  
    {  
     .  
     .   /* statement */   
     .  
    }  
    end_flag = true;  
```  
  
 Enumerátor nepojmenované datové typy lze také deklarovat. Název typu dat, je tento parametr vynechán, ale lze deklarovat proměnné. Proměnná `response` je proměnná typu definovaného:  
  
```  
enum { yes, no } response;  
```  
  
## <a name="see-also"></a>Viz také  
 [Výčty](../cpp/enumerations-cpp.md)