---
title: Bitová pole jazyka C++
ms.date: 11/19/2018
helpviewer_keywords:
- bitfields [C++]
- fields [C++], bit
- bit fields
ms.assetid: 6f4b62e3-cc1d-4e5d-bf34-05904104f71a
ms.openlocfilehash: 747920378472cc091928a080e303a0543e287aaa
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175090"
---
# <a name="c-bit-fields"></a>Bitová pole jazyka C++

Třídy a struktury mohou obsahovat členy, které zabírají méně úložného prostoru než celočíselný typ. Tyto členy jsou určeny jako bitová pole. Syntaxe bitového pole *deklarátor členu* následuje specifikace:

## <a name="syntax"></a>Syntaxe

*deklarátor* **:** *konstantního výrazu.*

## <a name="remarks"></a>Poznámky

(Volitelné) *deklarátor* je název, kterým se přistupuje členu v programu. Musí být celočíselného typu (včetně výčtových typů). *Konstantní výraz* určuje počet bitů, které člen zaujímá ve struktuře. Anonymní bitová pole, tedy členy bitových polí bez identifikátoru, slouží pro odsazení.

> [!NOTE]
> Nepojmenované bitové pole šířky 0 vynutí zarovnání dalšího bitového pole na další **typ** hranice, ve kterém **typ** je typ člena.

Následující příklad deklaruje strukturu, která obsahuje bitová pole:

```cpp
// bit_fields1.cpp
// compile with: /LD
struct Date {
   unsigned short nWeekDay  : 3;    // 0..7   (3 bits)
   unsigned short nMonthDay : 6;    // 0..31  (6 bits)
   unsigned short nMonth    : 5;    // 0..12  (5 bits)
   unsigned short nYear     : 8;    // 0..100 (8 bits)
};
```

Koncepční rozvržení paměti objektu typu `Date` je znázorněno na následujícím obrázku.

![Rozložení paměti objektu date](../cpp/media/vc38uq1.png "rozložení paměti objektu date") <br/>
Rozložení paměti objektu Date

Všimněte si, že `nYear` je 8 bitů dlouhý a přeteče hranice slova deklarovaného typu **bez znaménka** **krátký**. Proto je zahájen na začátku nového **bez znaménka** **krátký**. Není nutné, aby se všechna bitová pole vešla do jednoho objektu použitého typu. Nové jednotky úložiště jsou přidělovány podle vyžadovaného počtu bitů v deklaraci.

**Specifické pro Microsoft**

Řazení dat, která jsou deklarována jako bitová pole, je od nízkého po vysoký bit, jak je znázorněno na obrázku výše.

**Specifické pro END Microsoft**

Pokud deklarace struktury obsahuje nepojmenované pole o délce 0, jak je znázorněno v následujícím příkladu,

```cpp
// bit_fields2.cpp
// compile with: /LD
struct Date {
   unsigned nWeekDay  : 3;    // 0..7   (3 bits)
   unsigned nMonthDay : 6;    // 0..31  (6 bits)
   unsigned           : 0;    // Force alignment to next boundary.
   unsigned nMonth    : 5;    // 0..12  (5 bits)
   unsigned nYear     : 8;    // 0..100 (8 bits)
};
```

potom rozložení paměti je, jak je znázorněno na následujícím obrázku:

![Rozložení objektu Date s nulovou&#45;bitové pole délky](../cpp/media/vc38uq2.png "rozložení datum objektu s nulou&#45;délkou bitového pole") <br/>
Rozložení objektu Date s nulovou délkou bitového pole

Základní typ bitového pole musí být integrálního typu, jak je popsáno v [základní typy](../cpp/fundamental-types-cpp.md).

Pokud se inicializátor pro odkaz typu `const T&` l-hodnotou, která odkazuje na bitové pole typu `T`, odkaz není vázán na bitové pole přímo. Místo toho odkaz je vázán na dočasný inicializován pro uchování hodnoty bitové pole.

## <a name="restrictions-on-bit-fields"></a>Omezení u bitových polí

V následujícím seznamu jsou uvedeny chybné operace u bitových polí:

- Převzetí adresy bitového pole.

- Inicializace non -**const** odkazu pomocí bitového pole.

## <a name="see-also"></a>Viz také:

[Třídy a struktury](../cpp/classes-and-structs-cpp.md)