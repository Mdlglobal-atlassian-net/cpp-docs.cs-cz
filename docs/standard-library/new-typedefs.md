---
title: '&lt;nové&gt; – definice TypeDef'
ms.date: 11/04/2016
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
ms.openlocfilehash: 85c8d0c2974f734783e3d9c2ad1269f84d605dec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223633"
---
# <a name="ltnewgt-typedefs"></a>&lt;nové&gt; – definice TypeDef

| |
| - |
|[new_handler](#new_handler)|

## <a name="new_handler"></a>  new_handler

Typu odkazuje na funkci vhodný pro použití jako novou obslužnou rutinu.

```cpp
typedef void (*new_handler)();
```

### <a name="remarks"></a>Poznámky

Tento typ obslužné rutiny funkce je volána **operatornew** nebo `operator new[]` když nemohou vyhovět požadavku další úložiště.

### <a name="example"></a>Příklad

Zobrazit [set_new_handler](../standard-library/new-functions.md#set_new_handler) příklad použití `new_handler` jako návratovou hodnotu.

## <a name="see-also"></a>Viz také:

[\<new>](../standard-library/new.md)<br/>
