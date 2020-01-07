---
title: Bitová pole jazyka C++
ms.date: 11/19/2018
helpviewer_keywords:
- bitfields [C++]
- fields [C++], bit
- bit fields
ms.assetid: 6f4b62e3-cc1d-4e5d-bf34-05904104f71a
ms.openlocfilehash: bba57d495553e9622fcece9d036fc4f6eff3fa04
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301597"
---
# <a name="c-bit-fields"></a>Bitová pole jazyka C++

Třídy a struktury mohou obsahovat členy, které zabírají méně úložného prostoru než celočíselný typ. Tyto členy jsou určeny jako bitová pole. Syntaxe bitového pole *-deklarátor specifikace členů* je následující:

## <a name="syntax"></a>Syntaxe

*deklarátor* **:** *konstantní výraz*

## <a name="remarks"></a>Poznámky

(Nepovinný) *deklarátor* je název, ke kterému se člen přistupoval v programu. Musí být celočíselného typu (včetně výčtových typů). *Konstantní výraz* určuje počet bitů, které člen zabírá ve struktuře. Anonymní bitová pole, tedy členy bitových polí bez identifikátoru, slouží pro odsazení.

> [!NOTE]
> Nepojmenované bitové pole Width 0 nutí zarovnání dalšího bitového pole na další hranici **typu** , kde **Type** je typ člena.

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

![Rozložení paměti objektu Date](../cpp/media/vc38uq1.png "Rozložení paměti objektu Date") <br/>
Rozložení paměti objektu Date

Všimněte si, že `nYear` je 8 bitů dlouhé a přetečení hranice slova deklarovaného typu, **bez znaménka** **short**. Proto je zahájen na začátku nového **nepodepsaného znaménka** **.** Není nutné, aby se všechna bitová pole vešla do jednoho objektu použitého typu. Nové jednotky úložiště jsou přidělovány podle vyžadovaného počtu bitů v deklaraci.

**Specifické pro společnost Microsoft**

Řazení dat, která jsou deklarována jako bitová pole, je od nízkého po vysoký bit, jak je znázorněno na obrázku výše.

**Specifické pro konec Microsoftu**

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

rozložení paměti pak je znázorněno na následujícím obrázku:

![Rozložení objektu Date s bitovým&#45;polem s nulovou délkou](../cpp/media/vc38uq2.png "Rozložení objektu Date s bitovým&#45;polem s nulovou délkou") <br/>
Rozložení objektu Date s nulovou délkou bitového pole

Podkladový typ bitového pole musí být integrálního typu, jak je popsáno v [předdefinovaných typech](../cpp/fundamental-types-cpp.md).

Pokud inicializátor pro odkaz typu `const T&` je l-hodnota, která odkazuje na bitové pole typu `T`, odkaz není přímo vázán na bitové pole. Místo toho je odkaz svázán s dočasnou inicializací pro uchování hodnoty bitového pole.

## <a name="restrictions-on-bit-fields"></a>Omezení bitových polí

V následujícím seznamu jsou uvedeny chybné operace u bitových polí:

- Převzetí adresy bitového pole.

- Inicializuje se odkaz, který není typu**const** , s bitovým polem.

## <a name="see-also"></a>Viz také:

[Třídy a struktury](../cpp/classes-and-structs-cpp.md)