---
title: decay – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::decay
helpviewer_keywords:
- decay class
ms.assetid: 96baa2fd-c8e0-49af-be91-ba375ba7f9dc
ms.openlocfilehash: 3b22dfecb1162ce67a0d648197465115acb044ba
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688118"
---
# <a name="decay-class"></a>decay – třída

Vytvoří typ jako předaný hodnotou. Vytvoří neodkazový typ, který není typu const, není volatile, nebo vytvoří ukazatel na typ z funkce nebo typu pole.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct decay;

template <class T>
using decay_t = typename decay<T>::type;
```

### <a name="parameters"></a>Parametry

*T* \
Typ, který chcete upravit.

## <a name="remarks"></a>Poznámky

Použijte šablonu Decay k vytvoření výsledného typu, jako by byl typ předán pomocí value jako argument. Definice typedef člena šablony třídy `type` obsahuje upravený typ, který je definován v následujících fázích:

- Typ `U` je definován jako `remove_reference<T>::type`.

- Pokud je `is_array<U>::value` true, upravený typ `type` `remove_extent<U>::type *`.

- V opačném případě, pokud `is_function<U>::value` má hodnotu true, je upravený typ `type` `add_pointer<U>::type`.

- V opačném případě je upravený typ `type` `remove_cv<U>::type`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)
