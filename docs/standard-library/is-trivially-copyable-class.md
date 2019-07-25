---
title: is_trivially_copyable – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_copyable
helpviewer_keywords:
- is_trivially_copyable
ms.assetid: 89a53bf8-036c-4108-91e1-fe34adbde8b3
ms.openlocfilehash: d3062ae311b63be76ba07185f4f8173afa4229cc
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459752"
---
# <a name="istriviallycopyable-class"></a>is_trivially_copyable – třída

Testuje, zda je typ triviálním kopírovacím typem.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_trivially_copyable;
```

### <a name="parameters"></a>Parametry

*Š*\
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu má hodnotu true, pokud typ *T* je triviální kopírovací typ, jinak má hodnotu false. Triviální typy bez operace kopírování, operace přesunutí nebo destruktorů. Obecně platí, že operace kopírování je považována za triviální, pokud může být implementována jako bitová kopie. Předdefinované typy a pole triviálních kopírovaných typů jsou triviální kopie.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)
