---
title: '&lt;nové&gt; – definice TypeDef'
ms.date: 11/04/2016
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
ms.openlocfilehash: 85c8d0c2974f734783e3d9c2ad1269f84d605dec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549116"
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

[\<Nový >](../standard-library/new.md)<br/>
