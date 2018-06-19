---
title: is_trivially_move_assignable třída | Microsoft Docs
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
ms.openlocfilehash: 1248c8efd06069863a9f78a94378fe7aed651011
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33856082"
---
# <a name="istriviallymoveassignable-class"></a>is_trivially_move_assignable – třída

Ověřuje, zda má tento typ operátor přiřazení přesunutí trivial.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>Parametry

`Ty` Typ k dotazu.

## <a name="remarks"></a>Poznámky

Instance predikátem typu obsahuje hodnotu true, pokud typ `Ty` je třída, která má trivial přesunutí operátor přiřazení, jinak má hodnotu false.

Operátor přiřazení přesunutí pro třídu `Ty` je jednoduchá pokud:

implicitně je poskytována

Třída `Ty` nemá žádné virtuální funkce

Třída `Ty` nemá žádné virtuální základny

operátory přiřazení pro přesunutí trivial mít třídy všechny členy nestatické datového typu třídy

operátory přiřazení pro přesunutí trivial mít třídy všechny členy nestatické datové pole typu třídy

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[<type_traits>](../standard-library/type-traits.md)<br/>
