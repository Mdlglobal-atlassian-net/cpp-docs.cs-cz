---
title: make_unsigned – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::make_unsigned
dev_langs:
- C++
helpviewer_keywords:
- make_unsigned class
- make_unsigned
ms.assetid: 7a6a3c4f-1a4c-47e8-9ee2-ac1f7b669353
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f379500f9455ed9ad9a581966e0f8ed7bfed13f7
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953911"
---
# <a name="makeunsigned-class"></a>make_unsigned – třída

Vytvoří typ nebo nejmenší bez znaménka typu větší než nebo rovno velikosti typu.

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

Instance modifikátoru typu obsahuje změněný typ, který je *T* Pokud `is_unsigned<T>` platí. V opačném případě je nejmenší typ se znaménkem `ST` pro kterou `sizeof (T) <= sizeof (ST)`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
