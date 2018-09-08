---
title: is_copy_assignable – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 863c842fe3d5635848b569ad0cad6dad0556e302
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44102535"
---
# <a name="iscopyassignable-class"></a>is_copy_assignable – třída

Testy, zda má typ je zkopírovat na přiřazení.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_copy_assignable;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *Ty* je třída, která má operátor přiřazení kopie, jinak má hodnotu false. Ekvivalentní is_assignable –\<Ty & const Ty & >.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
