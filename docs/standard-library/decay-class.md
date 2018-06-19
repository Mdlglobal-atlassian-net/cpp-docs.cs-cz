---
title: decay – třída | Microsoft Docs
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
ms.openlocfilehash: e0451b8565a4d021181d79d15437637e1b2f3b27
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33841795"
---
# <a name="decay-class"></a>decay – třída

Vytvoří typ jako předaná hodnota. Díky bez – odkaz na typ, není const, stálé nebo je ukazatel typu z funkce nebo typ pole.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct decay;

template <class T>
using decay_t = typename decay<T>::type;
```

### <a name="parameters"></a>Parametry

`T` Typ, který chcete upravit.

## <a name="remarks"></a>Poznámky

Šablona decay slouží k vytvoření výsledný typ, jako kdyby byl předán typ podle hodnoty jako argument. Typedef člena třídy šablony `type` obsahuje upravené typ, který je definován v těchto fází:

- Typ `U` je definován jako `remove_reference<T>::type`.

- Pokud `is_array<U>::value` má hodnotu true, typ upravené `type` je `remove_extent<U>::type *`.

- Jinak Pokud `is_function<U>::value` má hodnotu true, typ upravené `type` je `add_pointer<U>::type`.

- Jinak upravené typ `type` je `remove_cv<U>::type`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[<type_traits>](../standard-library/type-traits.md)<br/>
