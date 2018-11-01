---
title: is_final – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_final
helpviewer_keywords:
- is_final
ms.assetid: 9dbad82f-6685-4909-94e8-98e4a93994b9
ms.openlocfilehash: f605b160f6ed71aaafcc7c391e17180e4b243444
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50446536"
---
# <a name="isfinal-class"></a>is_final – třída

Ověřuje, zda typ není typem třídy označené `final`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_final;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *T* je označená typem třídy `final`, v opačném případě obsahuje hodnotu false. Pokud *T* je typ třídy, musí být dokončený typ.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
[final – specifikátor](../cpp/final-specifier.md)<br/>
