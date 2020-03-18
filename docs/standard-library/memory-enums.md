---
title: výčty &lt;paměti&gt;
ms.date: 11/04/2016
f1_keywords:
- memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
ms.openlocfilehash: 78cdb0fe6c0d9487500804d21fe4ad4870fcad0f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419978"
---
# <a name="ltmemorygt-enums"></a>výčty &lt;paměti&gt;

## <a name="pointer_safety"></a>Výčet pointer_safety

Výčet možných hodnot vrácených funkcí `get_pointer_safety`.

```cpp
class pointer_safety {
   relaxed,
   preferred,
   strict
};
```

### <a name="remarks"></a>Poznámky

Rozsah **výčtu** definuje hodnoty, které mohou být vráceny `get_pointer_safety()`:

`relaxed` ukazatelé nejsou bezpečně odvozené (zjevným ukazatelům na deklarované nebo přidělené objekty) se považují za stejné jako bezpečně odvozené.

`preferred` – stejně jako dřív, ale nemusíte odvodit ukazatele, které nejsou bezpečně odvozené.

`strict` ukazatele, které nejsou bezpečně odvozené, mohou být zpracovány jinak než ty, které jsou bezpečně odvozené.
