---
title: is_copy_assignable třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_copy_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_copy_assignable
ms.assetid: 3ae6bca1-85fb-4829-9ee9-0183b081ff50
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f9c63aa54675bd0b1d5a52a1c0a9d80a73f53290
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="iscopyassignable-class"></a>is_copy_assignable – třída

Testy, zda má typ lze zkopírovat na přiřazení.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_copy_assignable;
```

### <a name="parameters"></a>Parametry

`Ty` Typ k dotazu.

## <a name="remarks"></a>Poznámky

Instance predikátem typu obsahuje hodnotu true, pokud typ `Ty` je třída, která má kopírování operátor přiřazení, jinak má hodnotu false. Ekvivalentní is_assignable\<Ty & const Ty & >.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[<type_traits>](../standard-library/type-traits.md)<br/>
