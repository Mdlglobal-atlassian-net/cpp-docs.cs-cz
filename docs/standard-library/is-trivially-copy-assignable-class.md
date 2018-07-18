---
title: is_trivially_copy_assignable – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_copy_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_copy_assignable
ms.assetid: 7410133e-f367-493f-92a7-e34e3ec5e879
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f7c4c748d7328f534aebfb2133c72635bbdc36f
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953963"
---
# <a name="istriviallycopyassignable-class"></a>is_trivially_copy_assignable – třída

Ověřuje, zda má typ jednoduchého dotazu kopírovacího operátoru přiřazení.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>Parametry

*T* typ dotazu.

## <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *T* je třída, která má triviální operátor přiřazení kopie, jinak má hodnotu false.

Přiřazení konstruktor pro třídu *T* je jednoduché, pokud je implicitně určen, třída *T* nemá žádné virtuální funkce třídy *T* nemá žádné virtuální báze třídy všechny nestatické datové členy typu třídy mají operátory jednoduchého dotazu přiřazení a třídy nestatických datových členů typu pole třídy mají operátory přiřazení triviální.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
