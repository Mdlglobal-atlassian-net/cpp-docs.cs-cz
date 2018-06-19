---
title: Specifikátory typu jazyka C | Microsoft Docs
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- type specifiers, C
- specifiers, type
ms.assetid: fbe13441-04c3-4829-b047-06d374adc2b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e37ac421627d4c4503d75eaf65188bbe234af015
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32388380"
---
# <a name="c-type-specifiers"></a>Specifikátory typu jazyka C

Specifikátory typu v deklaracích definování typu deklarace proměnné nebo funkce.

## <a name="syntax"></a>Syntaxe

*Specifikátor typu*:  
&nbsp;&nbsp;**Void**  
&nbsp;&nbsp;**Char**  
&nbsp;&nbsp;**krátký**  
&nbsp;&nbsp;**celá čísla**  
&nbsp;&nbsp;**dlouhá**  
&nbsp;&nbsp;**Plovoucí desetinná čárka**  
&nbsp;&nbsp;**Double**  
&nbsp;&nbsp;**Podepsané**  
&nbsp;&nbsp;**Bez znaménka**  
&nbsp;&nbsp;*Struktura nebo sjednocení – specifikátor*  
&nbsp;&nbsp;*enum – specifikátor*  
&nbsp;&nbsp;*Název definice TypeDef*  

**Podepsané char**, **podepsané int**, **podepsané krátká celočíselná**, a **podepsané dlouho int** typy, společně s jejich **bez znaménka**  svými protějšky a **výčtu**, se nazývají *integrální* typy. **Float**, **dvojité**, a **long double** specifikátory typu se označují jako *plovoucí* nebo *splovoucídesetinnoučárkou* typy. V deklaraci proměnné nebo funkce, můžete použít všechny specifikace typu integrální nebo s plovoucí desetinnou čárkou. Pokud *specifikátor typu* není zadaný v deklaraci, se provede na **int**.

Volitelné klíčová slova **podepsané** a **nepodepsané** lze předcházet nebo postupovat podle některého z celočíselných typů, s výjimkou **výčtu**a mohou sloužit také samostatně jako specifikátory typu, v takovém případě jsou pochopeny jako **podepsané int** a **nepodepsané int**, v uvedeném pořadí. Při použití samostatného klíčové slovo **int** předpokládá se, že **podepsané**. Při použití samostatného klíčová slova **dlouho** a **krátké** jsou pochopeny jako **dlouho int** a **krátká celočíselná**.

Výčtové typy jsou považovány za základní typy. Specifikátory typu pro výčtové typy jsou popsané v [deklarace výčtů](../c-language/c-enumeration-declarations.md).

Klíčové slovo **void** se třemi způsoby: Chcete-li určit funkce návratový typ, určení seznamu typ argumentu pro funkci, která nezadávaly žádné argumenty a k určení ukazatel na neurčeného typu. Můžete použít **void** typu deklarovat funkce, které vrací žádná hodnota nebo deklarovat ukazatel na neurčeného typu. V tématu [argumenty](../c-language/arguments.md) informace o **void** když se zobrazí v závorkách následující název funkce samostatně.

**Konkrétní Microsoft**

Kontrola typu je nyní ANSI standardem, což znamená, že typ **krátké** a typ **int** jsou odlišné typy. Toto je například předefinování v kompilátoru Microsoft C, která byla přijata v předchozích verzích nástroje kompilátoru.

```C
int   myfunc();
short myfunc();
```

Tento další příklad rovněž vygeneruje upozornění týkající se indirection pro různé typy:

```C
int *pi;
short *ps;

ps = pi;  /* Now generates warning */
```

Kompilátor Microsoft C také generuje upozornění pro rozdíly v přihlášení. Příklad:

```C
signed int *pi;
unsigned int *pu

pi = pu;  /* Now generates warning */
```

Typ **void** se vyhodnotí výrazy pro vedlejší účinky. Nelze použít (neexistující) hodnotu výraz, který má typ **void** v jakékoli způsob ani může můžete převést **void** výrazu (podle implicitního nebo explicitního převodu) k libovolnému typu s výjimkou **void** . Pokud používáte výrazu žádným jiným typem v kontextu, kde **void** výrazu je vyžadován, jeho hodnota se zahodí.

Tak, aby odpovídala specifikace ANSI **void\* \***  nelze použít jako **int\*\***. Pouze **void\***  slouží jako ukazatel na neurčeného typu.

**Konkrétní Microsoft END**

Můžete vytvořit další typ specifikátory s **typedef** deklarace, jak je popsáno v [Typedef – deklarace](../c-language/typedef-declarations.md). V tématu [úložiště základních typů](../c-language/storage-of-basic-types.md) informace o velikost každého typu.

## <a name="see-also"></a>Viz také

[Deklarace a typy](../c-language/declarations-and-types.md)  
