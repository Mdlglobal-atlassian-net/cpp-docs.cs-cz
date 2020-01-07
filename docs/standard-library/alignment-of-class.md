---
title: alignment_of – třída
ms.date: 12/11/2019
f1_keywords:
- type_traits/std::alignment_of
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
ms.openlocfilehash: d241848edf57fe4876c35e22f1762abf5d6888fa
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302312"
---
# <a name="alignment_of-class"></a>alignment_of – třída

Získá zarovnání určeného typu. Tato struktura je implementována z podmínek [alignof](../cpp/alignment-cpp-declarations.md). **Alignof** použijte přímo v případě, že jednoduše potřebujete zadat dotaz na hodnotu zarovnání. Použijte alignment_of, pokud potřebujete integrální konstantu, například při odeslání značky.

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

**Záhlaví:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[< type_traits >](../standard-library/type-traits.md)\
[aligned_storage – třída](../standard-library/aligned-storage-class.md)
