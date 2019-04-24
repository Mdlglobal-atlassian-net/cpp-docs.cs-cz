---
title: Specifikátory typu jazyka C
ms.date: 01/29/2018
helpviewer_keywords:
- type specifiers, C
- specifiers, type
ms.assetid: fbe13441-04c3-4829-b047-06d374adc2b6
ms.openlocfilehash: 1191cf4d2912cda535547f465fe4bfbedebe8fa2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313191"
---
# <a name="c-type-specifiers"></a>Specifikátory typu jazyka C

Specifikátory typu v deklaracích definování typu deklarace proměnné nebo funkce.

## <a name="syntax"></a>Syntaxe

*Specifikátor typu*: &nbsp; &nbsp; &nbsp; &nbsp; **void** &nbsp; &nbsp; &nbsp; &nbsp; **char** &nbsp; &nbsp; &nbsp; &nbsp; **krátký** &nbsp; &nbsp; &nbsp; &nbsp; **int** &nbsp; &nbsp; &nbsp; &nbsp; **dlouhé** &nbsp; &nbsp; &nbsp; &nbsp; **float** &nbsp; &nbsp; &nbsp; &nbsp; **double** &nbsp; &nbsp; &nbsp; &nbsp; **podepsané** &nbsp; &nbsp; &nbsp; &nbsp; **bez znaménka** &nbsp; &nbsp; &nbsp; &nbsp; *struct nebo sjednocení – specifikátor* &nbsp; &nbsp; &nbsp; &nbsp; *specifikátoru výčtu* &nbsp; &nbsp; &nbsp; &nbsp; *název typedef*

**Podepsané char**, **znaménkem**, **podepsané krátká celočíselná**, a **podepsané long int** typy, společně s jejich **bez znaménka**  protějšky a **výčtu**, se nazývají *integrální* typy. **Float**, **double**, a **long double** specifikátory typu jsou označovány jako *s plovoucí desetinnou čárkou* nebo *splovoucídesetinnoučárkou* typy. Můžete použít libovolný typ s plovoucí desetinnou čárkou nebo celočíselné specifikátor v deklaraci proměnné nebo funkce. Pokud *specifikátor typu* není k dispozici v deklaraci, je slov za **int**.

Volitelné klíčová slova **podepsané** a **bez znaménka** lze předcházet nebo postupovat podle některého z celočíselných typů s výjimkou **výčtu**a je také možné samostatně jako specifikátory typu, v takovém případě jsou chápat jako **znaménkem** a **unsigned int**v uvedeném pořadí. Při použití samostatného klíčové slovo **int** je považován za **podepsané**. Při použití samostatného klíčová slova **dlouhé** a **krátký** vyplývají z jako **long int** a **krátká celočíselná**.

Výčtové typy jsou považovány za základní typy. Specifikátory typu pro typy výčtu jsou popsány v [deklarace výčtů](../c-language/c-enumeration-declarations.md).

Klíčové slovo **void** má tři použití: Chcete-li určit funkce, návratový typ, můžete určit přehledu typ argumentu pro funkci, která nepřijímá žádné argumenty a zadejte ukazatel neurčeného typu. Můžete použít **void** typu k deklaraci funkce, které vrací žádná hodnota nebo deklarovat ukazatel na neurčeného typu. V tématu [argumenty](../c-language/arguments.md) informace o **void** když se zobrazí pouze v závorkách za názvem funkce.

**Microsoft Specific**

Kontrola typu je nyní vyhovující standardu ANSI, což znamená, že tento typ **krátký** a typ **int** jsou odlišné typy. Například toto je nová definice v kompilátoru C společnosti Microsoft, který byl přijat předchozími verzemi kompilátoru.

```C
int   myfunc();
short myfunc();
```

Tento další příklad také vygeneruje varování týkající se nepřímý odkaz na různé typy:

```C
int *pi;
short *ps;

ps = pi;  /* Now generates warning */
```

Kompilátor Microsoft C také vygeneruje upozornění na rozdíly v přihlašování. Příklad:

```C
signed int *pi;
unsigned int *pu

pi = pu;  /* Now generates warning */
```

Typ **void** vedlejší účinky, se vyhodnotí výrazy. Nelze použít hodnotu (neexistující), která má typ výrazu **void** v libovolné způsobem, ani použít převedete **void** výrazu (podle implicitní nebo explicitní konverze) na libovolný typ s výjimkou **void.** . Pokud použijete výraz libovolného typu v rámci kde **void** výraz je vyžadován, jeho hodnota se zahodí.

Chcete-li se řídí specifikací ANSI <strong>void\* \*</strong>  nelze použít jako <strong>int\*\*</strong>. Pouze **void** <strong>\*</strong> může sloužit jako ukazatel na neurčeného typu.

**Specifické pro END Microsoft**

Můžete vytvořit další typ specifikátory s **typedef** deklarace, jak je popsáno v [deklarace Typedef](../c-language/typedef-declarations.md). Zobrazit [úložiště základních typů](../c-language/storage-of-basic-types.md) informace o velikosti každého typu.

## <a name="see-also"></a>Viz také:

[Deklarace a typy](../c-language/declarations-and-types.md)
