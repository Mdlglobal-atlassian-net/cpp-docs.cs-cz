---
title: make_unsigned – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::make_unsigned
helpviewer_keywords:
- make_unsigned class
- make_unsigned
ms.assetid: 7a6a3c4f-1a4c-47e8-9ee2-ac1f7b669353
ms.openlocfilehash: 4c0224bd5fd7dc8c6589ae474bb9acb9a8f09cf6
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456315"
---
# <a name="makeunsigned-class"></a>make_unsigned – třída

Předává typ nebo nejmenší typ bez znaménka větší než nebo rovno velikosti pro typ.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct make_unsigned;

template <class T>
using make_unsigned_t = typename make_unsigned<T>::type;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*T*|Typ, který chcete upravit.|

## <a name="remarks"></a>Poznámky

Instance modifikátoru typu obsahuje upravený typ, který je *T* , pokud `is_unsigned<T>` má hodnotu true. V opačném případě je to nejmenší `ST` podepsaný typ `sizeof (T) <= sizeof (ST)`, pro který.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)
