---
title: is_trivially_move_constructible – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_move_constructible
helpviewer_keywords:
- is_trivially_move_constructible
ms.assetid: 740bdec7-65e5-47b3-b94f-a2479ceac3ec
ms.openlocfilehash: 279da956eaff21c39c6e5ca563f26989105f7e74
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448365"
---
# <a name="istriviallymoveconstructible-class"></a>is_trivially_move_constructible – třída

Testuje, zda typ obsahuje konstruktor triviálního přesunu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>Parametry

*Ty*\
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu má hodnotu true, pokud *je typ,* který je třída, která má konstruktor triviálního přesunu, v opačném případě obsahuje hodnotu false.

Konstruktor přesunu pro třídu *ty* je triviální, pokud:

je implicitně deklarována

jeho typy parametrů jsou ekvivalentní k těm implicitní deklarace.

Třída *ty* nemá žádné virtuální funkce.

Třída *ty* nemá žádné virtuální základy.

Třída nemá žádné nestálé nestatické datové členy.

všechny přímé základny třídy *ty* mají konstruktory triviálního přesunu.

třídy všech nestatických datových členů typu třídy mají konstruktory triviálního přesunu.

třídy všech nestatických datových členů typu Array třídy mají konstruktory triviálního přesunu.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)
