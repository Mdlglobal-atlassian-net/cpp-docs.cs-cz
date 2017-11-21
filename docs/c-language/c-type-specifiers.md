---
title: "Specifikátory typu jazyka C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- type specifiers, C
- specifiers, type
ms.assetid: fbe13441-04c3-4829-b047-06d374adc2b6
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 78cd6292c97f41cb7e862389113404346da80460
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="c-type-specifiers"></a>Specifikátory typu jazyka C
Specifikátory typu v deklaracích definování typu deklarace proměnné nebo funkce.  
  
## <a name="syntax"></a>Syntaxe  
 *Specifikátor typu*:  
 **void**  
  
 **Char**  
  
 **krátký**  
  
 **celá čísla**  
  
 **dlouhá**  
  
 **plovoucí desetinná čárka**  
  
 **Double**  
  
 **podepsané**  
  
 **bez znaménka**  
  
 *Struktura nebo sjednocení – specifikátor*  
  
 *enum – specifikátor*  
  
 *Název definice TypeDef*  
  
 **Podepsané char**, **podepsané int**, **podepsané krátká celočíselná**, a **podepsané dlouho int** typy, společně s jejich `unsigned` svými protějšky a `enum`, se nazývají "celočíselné" typy. **Float**, **dvojité**, a `long double` specifikátory typu jsou označovány jako "plovoucí" nebo "s plovoucí desetinnou čárkou" typů. V deklaraci proměnné nebo funkce, můžete použít všechny specifikace typu integrální nebo s plovoucí desetinnou čárkou. Pokud *specifikátor typu* není zadaný v deklaraci, se provede na `int`.  
  
 Volitelné klíčová slova **podepsané** a `unsigned` lze předcházet nebo postupovat podle některého z celočíselných typů, s výjimkou `enum`a mohou sloužit také samostatně jako specifikátory typu, v takovém případě se jsou pochopeny jako **podepsaná celá čísla**  a `unsigned int`, v uvedeném pořadí. Při použití samostatného klíčové slovo `int` předpokládá se, že **podepsané**. Při použití samostatného klíčová slova **dlouho** a **krátké** jsou pochopeny jako **dlouho int** a `short int`.  
  
 Výčtové typy jsou považovány za základní typy. Specifikátory typu pro výčtové typy jsou popsané v [deklarace výčtů](../c-language/c-enumeration-declarations.md).  
  
 Klíčové slovo `void` se třemi způsoby: Chcete-li určit funkce návratový typ, určení seznamu typ argumentu pro funkci, která nezadávaly žádné argumenty a k určení ukazatel na neurčeného typu. Můžete použít `void` typu deklarovat funkce, které vrací žádná hodnota nebo deklarovat ukazatel na neurčeného typu. V tématu [argumenty](../c-language/arguments.md) informace o `void` když se zobrazí v závorkách následující název funkce samostatně.  
  
 **Konkrétní Microsoft**  
  
 Kontrola typu je nyní ANSI standardem, což znamená, že typ **krátké** a typ `int` jsou odlišné typy. Toto je například předefinování v kompilátoru Microsoft C, která byla přijata v předchozích verzích nástroje kompilátoru.  
  
```  
int   myfunc();  
short myfunc();  
```  
  
 Tento další příklad rovněž vygeneruje upozornění týkající se indirection pro různé typy:  
  
```  
int *pi;  
short *ps;  
  
ps = pi;  /* Now generates warning */  
```  
  
 Kompilátor Microsoft C také generuje upozornění pro rozdíly v přihlášení. Příklad:  
  
```  
signed int *pi;  
unsigned int *pu  
  
pi = pu;  /* Now generates warning */  
```  
  
 Typ `void` se vyhodnotí výrazy pro vedlejší účinky. Nelze použít (neexistující) hodnotu výraz, který má typ `void` v jakékoli způsob ani může můžete převést `void` výrazu (podle implicitního nebo explicitního převodu) k libovolnému typu s výjimkou `void`. Pokud používáte výrazu žádným jiným typem v kontextu, kde `void` výrazu je vyžadován, jeho hodnota se zahodí.  
  
 Tak, aby odpovídala specifikace ANSI **void\* \***  nelze použít jako **int\*\***. Pouze **void\***  slouží jako ukazatel na neurčeného typu.  
  
 **Konkrétní Microsoft END**  
  
 Můžete vytvořit další typ specifikátory s `typedef` deklarace, jak je popsáno v [Typedef – deklarace](../c-language/typedef-declarations.md). V tématu [úložiště základních typů](../c-language/storage-of-basic-types.md) informace o velikost každého typu.  
  
## <a name="see-also"></a>Viz také  
 [Deklarace a typy](../c-language/declarations-and-types.md)