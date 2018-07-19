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
ms.openlocfilehash: ae0db2b789e16a39396a329a64dfb8794eef5775
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38961906"
---
# <a name="istriviallymoveassignable-class"></a>is_trivially_move_assignable – třída

Ověřuje, zda tento typ nemá operátor přiřazení přesunutí triviální.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>Parametry

*Ty* typ dotazu.

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
