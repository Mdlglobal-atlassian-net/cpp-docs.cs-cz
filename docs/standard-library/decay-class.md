---
title: decay – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::decay
helpviewer_keywords:
- decay class
ms.assetid: 96baa2fd-c8e0-49af-be91-ba375ba7f9dc
ms.openlocfilehash: 73b9e2d8ef9a14830c13ee3f6566137bb51e939d
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450645"
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

*Š*\
Typ, který chcete upravit.

## <a name="remarks"></a>Poznámky

Použijte šablonu Decay k vytvoření výsledného typu, jako by byl typ předán pomocí value jako argument. Definice typedef `type` člena třídy šablony obsahuje upravený typ, který je definován v následujících fázích:

- Typ `U` je definován jako `remove_reference<T>::type`.

- Pokud `is_array<U>::value` má hodnotu true, je upravený `remove_extent<U>::type *`typ `type` .

- V opačném `is_function<U>::value` případě, pokud má hodnotu true `type` , `add_pointer<U>::type`je upravený typ.

- V opačném případě je `type` `remove_cv<U>::type`upravený typ.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)
