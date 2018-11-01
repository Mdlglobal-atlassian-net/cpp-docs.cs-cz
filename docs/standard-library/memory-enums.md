---
title: '&lt;paměť&gt; výčty'
ms.date: 11/04/2016
f1_keywords:
- memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
ms.openlocfilehash: 5c5f87905b772ef277a72ef11defef8cb1001661
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495001"
---
# <a name="ltmemorygt-enums"></a>&lt;paměť&gt; výčty

||
|-|
|[pointer_safety](#pointer_safety)|

## <a name="pointer_safety"></a>  pointer_safety – výčet

Výčet možných hodnot vrácených `get_pointer_safety`.

pointer_safety – třída {volný, upřednostňované, striktní};

### <a name="remarks"></a>Poznámky

Rámci oboru **výčtu** definuje hodnoty, které může být vrácen `get_pointer_safety()`:

`relaxed` --odvozené neprovádí bezpečné (samozřejmě ukazatelů na objekty deklarované nebo bez přidělení) s ukazateli stejné jako ty bezpečně odvozené.

`preferred` – stejně jako předtím, ale neprovádí bezpečné odvozené ukazatele by neměla být dereferencována.

`strict` --odvozené neprovádí bezpečné ukazatele může být zpracovány jinak než tyto bezpečně odvozené.

## <a name="see-also"></a>Viz také:

[\<paměť >](../standard-library/memory.md)<br/>
