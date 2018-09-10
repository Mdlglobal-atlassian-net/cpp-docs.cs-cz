---
title: is_trivially_move_constructible – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_move_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_move_constructible
ms.assetid: 740bdec7-65e5-47b3-b94f-a2479ceac3ec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ad5631fc5d689ccb6632ac230aebdaf40f18f80
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44106480"
---
# <a name="istriviallymoveconstructible-class"></a>is_trivially_move_constructible – třída

Konstruktor přesunu testuje, zda má typ jednoduchého dotazu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *Ty* je třída, která má triviální konstruktor přesunutí, jinak má hodnotu false.

Konstruktor přesunu pro třídu *Ty* triviální pokud:

je implicitně deklarován

typy parametrů jsou rovnocenné těm implicitní deklaraci

Třída *Ty* nemá žádné virtuální funkce

Třída *Ty* nemá žádné virtuálních základních tříd

Třída nemá žádné nestálá nestatické datové členy

všechny přímo základů třídy *Ty* mají triviální konstruktorů

třídy všechny nestatické datové členy typu třídy mají triviální konstruktorů

třídy nestatických datových členů typu pole třídy mají triviální konstruktorů

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
