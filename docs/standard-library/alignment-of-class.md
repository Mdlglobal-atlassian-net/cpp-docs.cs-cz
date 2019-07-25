---
title: alignment_of – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::alignment_of
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
ms.openlocfilehash: 5222e70965db69d33ec62039bf9013a52d145705
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456454"
---
# <a name="alignmentof-class"></a>alignment_of – třída

Získá zarovnání určeného typu. Tato struktura je implementována z podmínek [alignof](../cpp/alignof-and-alignas-cpp.md). Použijte `alignof` přímo v případě, že jednoduše potřebujete zadat dotaz na hodnotu zarovnání. Použijte alignment_of, pokud potřebujete integrální konstantu, například při odeslání značky.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct alignment_of;
```

### <a name="parameters"></a>Parametry

*Ty*\
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Dotaz typu obsahuje hodnotu zarovnání *typu.*

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[< type_traits >](../standard-library/type-traits.md)\
[aligned_storage – třída](../standard-library/aligned-storage-class.md)
