---
title: '&lt;nové&gt; – definice TypeDef | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
ms.openlocfilehash: bbfe7d2c24cb589925c70c70235f6de112d274f1
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/16/2018
ms.locfileid: "42465120"
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
