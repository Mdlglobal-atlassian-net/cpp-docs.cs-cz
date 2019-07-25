---
title: is_literal_type Class
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_literal_type
helpviewer_keywords:
- is_literal_type
ms.assetid: a03a4ebb-ee66-48d6-91bb-41cf72b2401f
ms.openlocfilehash: 450c32d050a18f64e71992bd7a30412ebafe93de
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456214"
---
# <a name="isliteraltype-class"></a>is_literal_type Class

Testuje, zda lze typ použít jako `constexpr` proměnnou nebo jej sestavit, použít nebo vrátit z `constexpr` funkcí.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_literal_type;
```

### <a name="parameters"></a>Parametry

*Š*\
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu má hodnotu true, pokud typ *T* je literální *typ*, jinak obsahuje hodnotu false. Typ literálu je **void**, skalární typ, odkazový typ, pole typu literálu, nebo literální typ třídy. Typ třídy literálu je typ třídy, která má triviální destruktor, je buď agregovaný typ, nebo má alespoň jeden nepřesunutý a nekopírovací `constexpr` konstruktor a všechny jeho základní třídy a nestatické datové členy jsou nestálé literální typy. I když je typ literálu vždycky typu literálu, koncept typu literálu obsahuje cokoli, co kompilátor může vyhodnotit jako `constexpr` v době kompilace.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)
