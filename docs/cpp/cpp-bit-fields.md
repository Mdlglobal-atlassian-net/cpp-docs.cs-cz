---
title: Bitová pole jazyka C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- bitfields [C++]
- fields [C++], bit
- bit fields
ms.assetid: 6f4b62e3-cc1d-4e5d-bf34-05904104f71a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: db5ecac0263f1e8ebbfe41f654f2ef2e03b2395f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="c-bit-fields"></a>Bitová pole jazyka C++
Třídy a struktury mohou obsahovat členy, které zabírají méně úložného prostoru než celočíselný typ. Tyto členy jsou určeny jako bitová pole. Syntaxe pro pole bit *člen deklarátor* specifikace následovně:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
declarator  : constant-expression  
```  
  
## <a name="remarks"></a>Poznámky  
 (Volitelný) `declarator` je název, jehož prostřednictvím je k členu v programu přistupováno. Musí být celočíselného typu (včetně výčtových typů). *Konstantní výraz* určuje počet bitů člen sídlí ve struktuře. Anonymní bitová pole, tedy členy bitových polí bez identifikátoru, slouží pro odsazení.  
  
> [!NOTE]
>  Nepojmenované bitové pole šířky 0 vynutí zarovnání dalšího bitového pole na další hranici `type`, kde `type` je typ člena.  
  
 Následující příklad deklaruje strukturu, která obsahuje bitová pole:  
  
```  
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
  
 ![Rozložení paměti objektu datum](../cpp/media/vc38uq1.png "vc38UQ1")  
Rozložení paměti objektu Date  
  
 Všimněte si, že `nYear` je 8 bitů a k přetečení hranice slova deklarovaného typu **nepodepsané prostě**. Proto je spuštěno na začátku nového **nepodepsané prostě**. Není nutné, aby se všechna bitová pole vešla do jednoho objektu použitého typu. Nové jednotky úložiště jsou přidělovány podle vyžadovaného počtu bitů v deklaraci.  
  
 **Konkrétní Microsoft**  
  
 Řazení dat, která jsou deklarována jako bitová pole, je od nízkého po vysoký bit, jak je znázorněno na obrázku výše.  
  
 **Konkrétní Microsoft END**  
  
 Pokud deklarace struktury obsahuje nepojmenované pole o délce 0, jak je znázorněno v následujícím příkladu,  
  
```  
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
  
 je rozložení paměti stejné jako na následujícím obrázku.  
  
 ![Rozložení Date – objekt s hodnotou nula&#45;pole bitová délka](../cpp/media/vc38uq2.png "vc38UQ2")  
Rozložení objektu Date s nulovou délkou bitového pole  
  
 Základní typ bit pole musí být celočíselné typu, jak je popsáno v [základní typy](../cpp/fundamental-types-cpp.md).  
  
## <a name="restrictions-on-bit-fields"></a>Omezení bitová pole  
 V následujícím seznamu jsou uvedeny chybné operace u bitových polí:  
  
1.  Převzetí adresy bitového pole.  
  
2.  Inicializace odkazu pomocí bitového pole.  
  
## <a name="see-also"></a>Viz také  
 [Třídy a struktury](../cpp/classes-and-structs-cpp.md)