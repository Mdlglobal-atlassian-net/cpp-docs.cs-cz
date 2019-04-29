---
title: is_nothrow_constructible – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_constructible
helpviewer_keywords:
- is_nothrow_constructible
ms.assetid: 8be3f927-283e-4d67-95a5-8bf5dc4e7a3d
ms.openlocfilehash: 9ea11d54d49bf8f6ae6416f9663c2593cc66ea3e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383604"
---
# <a name="isnothrowconstructible-class"></a>is_nothrow_constructible – třída

Testuje, jestli constructible typu a se ví, že vyvolat zadáním zadanými typy argumentu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class... Args>
struct is_nothrow_constructible;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ, na který chcete odeslat dotaz.

*Args*<br/>
Typy argumentů tak, aby odpovídaly v konstruktoru sady *T*.

## <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *T* je constructible pomocí typy argumentů v *Args*a konstruktor se ví, že kompilátor vyvolá; v opačném případě obsahuje hodnotu false. Typ *T* je constructible Pokud za definicí proměnné `T t(std::declval<Args>()...);` ve správném formátu. Obě *T* a všechny typy v *Args* musí být kompletními typy **void**, nebo pole s neznámým rozsahem.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
