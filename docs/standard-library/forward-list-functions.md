---
title: '&lt;forward_list&gt; funkce'
ms.date: 11/04/2016
f1_keywords:
- forward_list/std::swap
ms.assetid: 0d6bc656-7049-4651-a4bd-c9a805e47756
ms.openlocfilehash: 78b1eaa44ed464de67d8ec45fab3241179bb94b9
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419096"
---
# <a name="ltforward_listgt-functions"></a>&lt;forward_list&gt; funkce

## <a name="swap"></a>adresu

Vyměňuje prvky dvou seznamů pro přeposílání.

```cpp
void swap(forward_list <Type, Allocator>& left, forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `forward_list`.

*pravé*\
Objekt typu `forward_list`.

### <a name="remarks"></a>Poznámky

Tato funkce šablony provádí `left.swap(right)`.
