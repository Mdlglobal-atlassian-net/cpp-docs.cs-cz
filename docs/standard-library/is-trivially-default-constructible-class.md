---
title: is_trivially_default_constructible – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_default_constructible
helpviewer_keywords:
- is_trivially_default_constructible
ms.assetid: 653ecd73-909f-4dd8-b95a-d1164d1c2da4
ms.openlocfilehash: b35458ca280285eb699c9b12b15b705660299ef2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563667"
---
# <a name="istriviallydefaultconstructible-class"></a>is_trivially_default_constructible – třída

Testuje, zda má typ jednoduchého dotazu výchozí konstruktor.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_trivially_default_constructible;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *Ty* je třída, která má triviální konstruktor, jinak má hodnotu false.

Výchozí konstruktor pro třídu *Ty* triviální pokud:

- je implicitně deklarovaný výchozí konstruktor

- Třída *Ty* nemá žádné virtuální funkce

- Třída *Ty* nemá žádné virtuálních základních tříd

- všechny přímo základů třídy *Ty* mít triviální konstruktory

- třídy všechny nestatické datové členy typu třídy mají triviální konstruktory

- třídy nestatických datových členů typu pole třídy mají triviální konstruktory

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
