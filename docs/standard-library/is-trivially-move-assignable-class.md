---
title: is_trivially_move_assignable – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_move_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_move_assignable
ms.assetid: 374f7322-0706-4bc1-a1a5-4191d0315e28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 19346075d0b52be7820adfe60e77e0f76113bc98
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44099906"
---
# <a name="istriviallymoveassignable-class"></a>is_trivially_move_assignable – třída

Ověřuje, zda tento typ nemá operátor přiřazení přesunutí triviální.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *Ty* je třída, která má triviální operátor přiřazení přesunutí, jinak má hodnotu false.

Operátor přiřazení přesunu pro třídu *Ty* triviální pokud:

implicitně se poskytuje

Třída *Ty* nemá žádné virtuální funkce

Třída *Ty* nemá žádné virtuálních základních tříd

třídy všechny nestatické datové členy typu třídy mají operátory přiřazení pro přesunutí jednoduchého dotazu

třídy nestatických datových členů typu pole třídy mají operátory přiřazení pro přesunutí jednoduchého dotazu

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
