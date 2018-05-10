---
title: is_nothrow_copy_constructible – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_nothrow_copy_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_copy_constructible
ms.assetid: f13a0bea-63b1-492a-9a45-d445df35c282
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd3a9818b6334ddd2d2769fc79c55fc8fd72e6dd
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="isnothrowcopyconstructible-class"></a>is_nothrow_copy_constructible – třída

Kontroluje, zda má typ **nothrow** kopírovacího konstruktoru.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_nothrow_copy_constructible;
```

### <a name="parameters"></a>Parametry

`Ty` Typ k dotazu.

## <a name="remarks"></a>Poznámky

Instance predikátem typu obsahuje hodnotu true, pokud typ `Ty` má nothrow kopírovacího konstruktoru, jinak má hodnotu false.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[<type_traits>](../standard-library/type-traits.md)<br/>
