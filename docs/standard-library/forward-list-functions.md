---
title: '&lt;forward_list&gt; funkce'
ms.date: 11/04/2016
f1_keywords:
- forward_list/std::swap
ms.assetid: 0d6bc656-7049-4651-a4bd-c9a805e47756
ms.openlocfilehash: 78b1eaa44ed464de67d8ec45fab3241179bb94b9
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78875842"
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
