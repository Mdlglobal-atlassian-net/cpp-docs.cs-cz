---
title: Informace běhového typu
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- RTTI compiler option
- run-time type information
- run time, type checking
- type information, run-time type checking
- run-time checks, type checking
ms.assetid: becbd0e5-0439-4c61-854f-8a74f7160c54
ms.openlocfilehash: 195274d7bcef0ff4d82383a8ec828ca9267573b0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178935"
---
# <a name="run-time-type-information"></a>Informace běhového typu

Informace o typu modulu runtime (RTTI) je mechanismus, který umožňuje stanovit typ objektu při provádění programu. RTTI byl přidán do jazyka C++, protože mnoho dodavatelů knihoven tříd implementovalo tuto funkci samostatně. Tím došlo k nekompatibilitě mezi knihovnami. Podpora informací o typu modulu runtime na úrovni jazyka se stala samozřejmostí.

V zájmu přehlednosti je popis mechanismu RTTI téměř zcela omezen na ukazatele. Uvedenou koncepci lze však také použít pro odkazy.

Existují tři hlavní prvky jazyka C++ informující o typu modulu runtime:

- Operátor [dynamic_cast](../cpp/dynamic-cast-operator.md) .

   Používá se pro převod polymorfních typů.

- Operátor [typeid](../cpp/typeid-operator.md) .

   Používá se k identifikaci přesného typu objektu.

- Třída [type_info](../cpp/type-info-class.md) .

   Slouží k uchování informací o typu vrácených operátorem **typeid** .

## <a name="see-also"></a>Viz také

[Přetypování](../cpp/casting.md)
