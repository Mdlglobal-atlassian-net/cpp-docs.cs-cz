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

Specifikátory typu v deklaracích definují typ deklarace proměnné nebo funkce.

## <a name="syntax"></a>Syntaxe

*specifikátor typu* &nbsp; &nbsp; &nbsp;: &nbsp; **void** &nbsp; **float** **char** &nbsp; **short** &nbsp; *typedef-name* **unsigned** **long** **double** **int** &nbsp; **signed** *struct-or-union-specifier* *enum-specifier* char short Celé_číslo Long &nbsp;int Double signed &nbsp;unsigned struct-or- &nbsp;Union- &nbsp;Specifikátor-specifikátor-specifikátore enum &nbsp;-name &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;

Typ **signed char**, **signed int**, **signed short int**a **signed long int** , spolu s jejich **nepodepsanými** protějšky a **výčty**, se nazývají *celočíselné* typy. Specifikátory typu **float**, **Double**a **Long** jsou označovány jako typy s *plovoucí desetinnou* čárkou nebo s *plovoucí* desetinnou čárkou. V deklaraci proměnné nebo funkce můžete použít libovolný specifikátor typu integrálního nebo plovoucího bodu. Pokud není v deklaraci *specifikátor typu* k dispozici, bude se jednat o typ **int**.

Volitelná klíčová slova **signed** a **unsigned** mohou předcházet nebo následovat za libovolnými celočíselnými typy s výjimkou **výčtu**a lze je také použít samostatně jako specifikátory typu. v takovém případě se rozumí jako **signed int** a **unsigned int**v uvedeném pořadí. Při samostatném použití se předpokládá, že klíčové slovo **int** bude **Podepsáno**. Při samostatném použití se klíčová slova **Long** a **short** považují za **Long int** a **short int**.

Výčtové typy se považují za základní typy. Specifikátory typu pro výčtové typy jsou popsány v tématu [deklarace výčtu](../c-language/c-enumeration-declarations.md).

Klíčové slovo **void** má tři použití: k určení návratového typu funkce pro určení seznamu typu argumentu pro funkci, která nepřijímá žádné argumenty, a pro určení ukazatele na nespecifikovaný typ. Typ **void** lze použít k deklarování funkcí, které nevrací žádnou hodnotu, nebo k deklaraci ukazatele na nespecifikovaný typ. Viz [argumenty](../c-language/arguments.md) pro informace o **void** , když se objeví samostatně v závorkách za názvem funkce.

**Specifické pro Microsoft**

Kontrola typu je nyní kompatibilní se standardem ANSI, což znamená, že typ **short** a typ **int** jsou odlišné typy. Toto je například předefinování v kompilátoru jazyka Microsoft C, které bylo přijato předchozími verzemi kompilátoru.

```C
int   myfunc();
short myfunc();
```

Tento další příklad také vygeneruje upozornění na nepřímý odkaz na různé typy:

```C
int *pi;
short *ps;

ps = pi;  /* Now generates warning */
```

Kompilátor jazyka Microsoft C také generuje upozornění na rozdíly v Sign. Příklad:

```C
signed int *pi;
unsigned int *pu

pi = pu;  /* Now generates warning */
```

Pro vedlejší účinky se vyhodnotí výrazy typu **void** . Nemůžete použít hodnotu (neexistující) výrazu, který má typ **void** , ani převést výraz **void** (implicitní nebo explicitní převod) na libovolný typ s výjimkou **void**. Pokud použijete výraz jiného typu v kontextu, kde je požadován výraz **void** , jeho hodnota je zahozena.

Aby bylo možné v souladu se specifikací ANSI, nelze použít <strong>void\* </strong> jako <strong>int\*</strong>. Pouze typ **void** <strong>\*</strong> lze použít jako ukazatel na nespecifikovaný typ.

**Specifické pro konec Microsoftu**

Můžete vytvořit další Specifikátory typu s deklaracemi **typedef** , jak je popsáno v tématu [deklarace typedef](../c-language/typedef-declarations.md). Informace o velikosti každého typu najdete v tématu [úložiště základních typů](../c-language/storage-of-basic-types.md) .

## <a name="see-also"></a>Viz také

[Deklarace a typy](../c-language/declarations-and-types.md)
