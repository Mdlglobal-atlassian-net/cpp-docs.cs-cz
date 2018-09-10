---
title: is_literal_type – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_literal_type
dev_langs:
- C++
helpviewer_keywords:
- is_literal_type
ms.assetid: a03a4ebb-ee66-48d6-91bb-41cf72b2401f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd4481be124cbcbba04f6b45b4c5a08beb34f04d
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44103302"
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
