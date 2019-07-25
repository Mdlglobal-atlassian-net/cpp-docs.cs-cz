---
title: is_standard_layout – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_standard_layout
helpviewer_keywords:
- is_standard_layout class
- is_standard_layout
ms.assetid: 15ccf111-f537-45ef-b552-59152a7ba312
ms.openlocfilehash: 4f999eaa4a5c1ea7e9672a5efdc6000a4d3d9759
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457419"
---
# <a name="isstandardlayout-class"></a>is_standard_layout – třída

Testuje, zda je typ standardní rozložení.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_standard_layout;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Ty*|Typ, který se má dotazovat|

## <a name="remarks"></a>Poznámky

Instance tohoto predikátu typu má hodnotu true, *Pokud typ this* je třída, která má standardní rozložení členských objektů v paměti, v opačném případě obsahuje hodnotu false.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)
