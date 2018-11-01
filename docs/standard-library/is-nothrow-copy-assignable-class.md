---
title: is_nothrow_copy_assignable – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_copy_assignable
helpviewer_keywords:
- is_nothrow_copy_assignable
ms.assetid: baa8abd6-4f53-489f-abba-8d5d5c53bbbc
ms.openlocfilehash: bb3aca47b61bdcc5b28eeedc1a6b4edefc303c4e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50583752"
---
# <a name="isnothrowcopyassignable-class"></a>is_nothrow_copy_assignable – třída

Ověřuje, zda má typ, který je pro kompilátor známým nedochází operátor přiřazení kopie.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_nothrow_copy_assignable;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true pro typ označím *T* kde `is_nothrow_assignable<T&, const T&>` obsahuje hodnotu true; v opačném případě obsahuje hodnotu false.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_nothrow_assignable – třída](../standard-library/is-nothrow-assignable-class.md)<br/>
