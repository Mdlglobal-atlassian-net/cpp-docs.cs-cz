---
title: '&lt;paměť&gt; výčty | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
ms.openlocfilehash: 9b9ea485bb66292c3c0509036c22dd161a694dd3
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38961412"
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
