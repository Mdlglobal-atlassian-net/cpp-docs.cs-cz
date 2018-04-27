---
title: is_move_assignable třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- type_traits/std::is_move_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_move_assignable
ms.assetid: f33137f2-0639-4912-8745-bc0f9fd18d28
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cd47437ad673a928817a7698b58099ba0b9f4607
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="ismoveassignable-class"></a>is_move_assignable – třída

Testy, pokud typ lze přesunout přiřazené.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_move_assignable;
```

### <a name="parameters"></a>Parametry

`T` Typ k dotazu.

## <a name="remarks"></a>Poznámky

Typ je přesunout přiřadit, pokud lze přiřadit deklarátor odkazu na typ odkaz na typ. Je ekvivalentní predikátem typu `is_assignable<T&, T&&>`. Přesuňte typy Přiřaditelné obsahují kde Skalární typy a typy tříd, které mají generované kompilátorem nebo uživatelsky definovaných přesunout operátory přiřazení.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[<type_traits>](../standard-library/type-traits.md)<br/>
