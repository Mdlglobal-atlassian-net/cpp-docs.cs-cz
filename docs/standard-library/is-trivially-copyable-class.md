---
title: is_trivially_copyable – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_copyable
helpviewer_keywords:
- is_trivially_copyable
ms.assetid: 89a53bf8-036c-4108-91e1-fe34adbde8b3
ms.openlocfilehash: 181152bff1d7c2e4f97678b48310f744080822ce
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50554363"
---
# <a name="istriviallycopyable-class"></a>is_trivially_copyable – třída

Ověřuje, zda typ typu snadno kopírovatelná.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_trivially_copyable;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *T* triviálně kopírovatelné typ, jinak má hodnotu false. Triviálně kopírovatelné typy mít žádné operace kopírování netriviální, operací přesunutí nebo destruktory. Obecně platí operace kopírování je považovány za bezvýznamné, pokud je možné implementovat jako bitové kopie. Předdefinované typy a pole triviálně kopírovatelné typy jsou snadno kopírovatelná.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
