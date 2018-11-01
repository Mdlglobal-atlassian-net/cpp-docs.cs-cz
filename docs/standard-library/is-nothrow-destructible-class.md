---
title: is_nothrow_destructible – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_destructible
helpviewer_keywords:
- is_nothrow_destructible
ms.assetid: 0bbd8a28-e312-4d72-bd28-aac027f974d3
ms.openlocfilehash: 366b40af45c57d058d918c4c2f21d1b2ba486d35
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50656739"
---
# <a name="isnothrowdestructible-class"></a>is_nothrow_destructible – třída

Testuje, jestli je typ zničitelné a destruktor je pro kompilátor známým nedochází.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_nothrow_destructible;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *T* zničitelné typ a destruktor je pro kompilátor známým nedochází. V opačném případě obsahuje hodnotu false.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
