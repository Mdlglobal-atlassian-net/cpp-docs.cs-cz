---
title: make_signed – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::make_signed
dev_langs:
- C++
helpviewer_keywords:
- make_signed class
- make_signed
ms.assetid: 686247c0-247c-496b-9b1b-ba9dcd633621
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7fe6eb3ffa83316071de2ba26cf80e6e6cbd5245
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957344"
---
# <a name="makesigned-class"></a>make_signed – třída

Vytvoří typ nebo nejmenší znaménkem typu větší než nebo rovno velikosti typu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct make_signed;

template <class T>
using make_signed_t = typename make_signed<T>::type;
```

### <a name="parameters"></a>Parametry

*T* typ, který chcete upravit.

## <a name="remarks"></a>Poznámky

Instance modifikátoru typu obsahuje změněný typ, který je *T* Pokud `is_signed<T>` platí. V opačném případě je nejmenší typ bez znaménka `UT` pro kterou `sizeof (T) <= sizeof (UT)`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
