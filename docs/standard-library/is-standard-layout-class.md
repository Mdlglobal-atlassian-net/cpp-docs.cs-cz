---
title: is_standard_layout – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_standard_layout
helpviewer_keywords:
- is_standard_layout class
- is_standard_layout
ms.assetid: 15ccf111-f537-45ef-b552-59152a7ba312
ms.openlocfilehash: 75691c1b09b71580474cc22cdc8382bff55a5e29
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413492"
---
# <a name="isstandardlayout-class"></a>is_standard_layout – třída

Testuje, zda je typ standardního rozložení.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_standard_layout;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Ty*|Typ, který má dotaz|

## <a name="remarks"></a>Poznámky

Instance této predikátu typu obsahuje hodnotu true, pokud typ *Ty* je třída, která má standardní rozložení objektů členů v paměti, jinak má hodnotu false.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
