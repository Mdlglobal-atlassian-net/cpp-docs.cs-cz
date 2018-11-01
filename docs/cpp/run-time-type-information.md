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
ms.openlocfilehash: 1d11ee3ea472f935120c59f0faefee905361ee97
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50656136"
---
# <a name="run-time-type-information"></a>Informace běhového typu

Informace o typu modulu runtime (RTTI) je mechanismus, který umožňuje stanovit typ objektu při provádění programu. RTTI byl přidán do jazyka C++, protože mnoho dodavatelů knihoven tříd implementovalo tuto funkci samostatně. Tím došlo k nekompatibilitě mezi knihovnami. Podpora informací o typu modulu runtime na úrovni jazyka se stala samozřejmostí.

V zájmu přehlednosti je popis mechanismu RTTI téměř zcela omezen na ukazatele. Uvedenou koncepci lze však také použít pro odkazy.

Existují tři hlavní prvky jazyka C++ informující o typu modulu runtime:

- [Dynamic_cast](../cpp/dynamic-cast-operator.md) operátor.

   Používá se pro převod polymorfních typů.

- [Typeid](../cpp/typeid-operator.md) operátor.

   Používá se k identifikaci přesného typu objektu.

- [Type_info](../cpp/type-info-class.md) třídy.

   Sloužící k uchování informací o typu vrácené **typeid** operátor.

## <a name="see-also"></a>Viz také:

[Přetypování](../cpp/casting.md)