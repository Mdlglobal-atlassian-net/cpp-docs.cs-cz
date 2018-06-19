---
title: '&lt;forward_list –&gt; funkce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- forward_list/std::swap
ms.assetid: 0d6bc656-7049-4651-a4bd-c9a805e47756
ms.openlocfilehash: 4585b1998309d7c17c8f02e2b0597cb595b2c4a3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33844839"
---
# <a name="ltforwardlistgt-functions"></a>&lt;forward_list –&gt; funkce

||
|-|
|[Swap](#swap)|

## <a name="swap"></a>  Swap

Výměny elementy dva seznamy předat dál.

```cpp
void swap(
    forward_list <Type, Allocator>& left,
    forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`left`|Objekt typu `forward_list`.|
|`right`|Objekt typu `forward_list`.|

### <a name="remarks"></a>Poznámky

Tato funkce šablony provede `left.swap(right)`.

## <a name="see-also"></a>Viz také

[<forward_list>](../standard-library/forward-list.md)<br/>
