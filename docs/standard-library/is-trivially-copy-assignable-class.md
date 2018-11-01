---
title: is_trivially_copy_assignable – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_copy_assignable
helpviewer_keywords:
- is_trivially_copy_assignable
ms.assetid: 7410133e-f367-493f-92a7-e34e3ec5e879
ms.openlocfilehash: 831e7c5afdd39980876a8e8284a68fec2084a4e5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630981"
---
# <a name="istriviallycopyassignable-class"></a>is_trivially_copy_assignable – třída

Ověřuje, zda má typ jednoduchého dotazu kopírovacího operátoru přiřazení.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *T* je třída, která má triviální operátor přiřazení kopie, jinak má hodnotu false.

Přiřazení konstruktor pro třídu *T* je jednoduché, pokud je implicitně určen, třída *T* nemá žádné virtuální funkce třídy *T* nemá žádné virtuální báze třídy všechny nestatické datové členy typu třídy mají operátory jednoduchého dotazu přiřazení a třídy nestatických datových členů typu pole třídy mají operátory přiřazení triviální.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
