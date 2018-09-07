---
title: decay – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::decay
dev_langs:
- C++
helpviewer_keywords:
- decay class
ms.assetid: 96baa2fd-c8e0-49af-be91-ba375ba7f9dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7d3ad5bae067bb9661b6cf475d0831b2b2dfcd2a
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44099522"
---
# <a name="decay-class"></a>decay – třída

Vytvoří typ jako předán podle hodnoty. Díky není typ odkazu, nekonstantní, není typu volatile nebo vytvoří ukazatel na typ z typu pole nebo funkce.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct decay;

template <class T>
using decay_t = typename decay<T>::type;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ, který chcete upravit.

## <a name="remarks"></a>Poznámky

Šablona decay vytvoří výsledný typ, jako kdyby byl předán typ podle hodnoty jako argument. Definice typu člena šablony třídy `type` obsahuje upravený typ, který je definován v následujících fázích:

- Typ `U` je definován jako `remove_reference<T>::type`.

- Pokud `is_array<U>::value` PRAVDA, upravený typ `type` je `remove_extent<U>::type *`.

- Jinak, pokud `is_function<U>::value` PRAVDA, upravený typ `type` je `add_pointer<U>::type`.

- V opačném případě upravený typ `type` je `remove_cv<U>::type`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
