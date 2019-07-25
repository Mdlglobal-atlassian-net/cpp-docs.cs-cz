---
title: make_signed – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::make_signed
helpviewer_keywords:
- make_signed class
- make_signed
ms.assetid: 686247c0-247c-496b-9b1b-ba9dcd633621
ms.openlocfilehash: c3c35e28dec3270299329c0186273e324effc2bb
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453682"
---
# <a name="makesigned-class"></a>make_signed – třída

Typ nebo nejmenší podepsaný typ, který je větší nebo roven velikosti pro typ.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct make_signed;

template <class T>
using make_signed_t = typename make_signed<T>::type;
```

### <a name="parameters"></a>Parametry

*Š*\
Typ, který chcete upravit.

## <a name="remarks"></a>Poznámky

Instance modifikátoru typu obsahuje upravený typ, který je *T* , pokud `is_signed<T>` má hodnotu true. V opačném případě je to nejmenší `UT` typ bez `sizeof (T) <= sizeof (UT)`znaménka, pro který.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)
