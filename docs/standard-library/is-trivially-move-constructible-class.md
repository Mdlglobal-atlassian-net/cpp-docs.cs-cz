---
title: is_trivially_move_constructible – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_move_constructible
helpviewer_keywords:
- is_trivially_move_constructible
ms.assetid: 740bdec7-65e5-47b3-b94f-a2479ceac3ec
ms.openlocfilehash: a1aef356716fac903b4e44a358602c709572e8ff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544349"
---
# <a name="istriviallymoveconstructible-class"></a>is_trivially_move_constructible – třída

Konstruktor přesunu testuje, zda má typ jednoduchého dotazu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *Ty* je třída, která má triviální konstruktor přesunutí, jinak má hodnotu false.

Konstruktor přesunu pro třídu *Ty* triviální pokud:

je implicitně deklarován

typy parametrů jsou rovnocenné těm implicitní deklaraci

Třída *Ty* nemá žádné virtuální funkce

Třída *Ty* nemá žádné virtuálních základních tříd

Třída nemá žádné nestálá nestatické datové členy

všechny přímo základů třídy *Ty* mají triviální konstruktorů

třídy všechny nestatické datové členy typu třídy mají triviální konstruktorů

třídy nestatických datových členů typu pole třídy mají triviální konstruktorů

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
