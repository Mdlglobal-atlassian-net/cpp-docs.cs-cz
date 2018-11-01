---
title: is_literal_type – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_literal_type
helpviewer_keywords:
- is_literal_type
ms.assetid: a03a4ebb-ee66-48d6-91bb-41cf72b2401f
ms.openlocfilehash: 804ef0462308b967fc0c4c95d8dfa96476475aab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50513996"
---
# <a name="isliteraltype-class"></a>is_literal_type – třída

Ověřuje, zda typ lze použít jako `constexpr` proměnné nebo vytvořen, používá nebo vrácená z `constexpr` funkce.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_literal_type;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *T* je *typ literálu*, v opačném případě obsahuje hodnotu false. Typ literálu je buď **void**, skalárního typu, typ odkazu, pole literálu typu nebo typu literál třídy. Typ literálu třídy je typ třídy, který má destruktor triviální, je typ agregace nebo má alespoň jeden bez – přesun, bez kopírování `constexpr` konstruktor a všechny její základní třídy a nestatické datové členy jsou typy literálu není typu volatile. Typ literálu je vždy typu literálu, koncept literál zahrnuje cokoli, co kompilátor můžete vyhodnotit jako `constexpr` v době kompilace.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
