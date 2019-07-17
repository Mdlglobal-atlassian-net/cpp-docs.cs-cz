---
title: is_aggregate třídy
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_aggregate
helpviewer_keywords:
- is_aggregate
ms.openlocfilehash: 7d979d4e4019ada12b72fb563c0b969fffe2c12d
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268048"
---
# <a name="isaggregate-class"></a>is_aggregate třídy

Ověřuje, zda typ není typem třídy označené `aggregate`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_aggregate;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *T* je označená typem třídy `aggregate`, v opačném případě obsahuje hodnotu false. Pokud *T* je typ třídy, musí být dokončený typ.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
