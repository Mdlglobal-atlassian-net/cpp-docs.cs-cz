---
title: is_final – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_final
dev_langs:
- C++
helpviewer_keywords:
- is_final
ms.assetid: 9dbad82f-6685-4909-94e8-98e4a93994b9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 101d987574ca789ce674c7ed01726847a66a4747
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38962010"
---
# <a name="isfinal-class"></a>is_final – třída

Ověřuje, zda typ není typem třídy označené `final`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_final;
```

### <a name="parameters"></a>Parametry

*T* typ dotazu.

## <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *T* je označená typem třídy `final`, v opačném případě obsahuje hodnotu false. Pokud *T* je typ třídy, musí být dokončený typ.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
[final – specifikátor](../cpp/final-specifier.md)<br/>
