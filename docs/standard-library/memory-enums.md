---
title: '&lt;paměť&gt; výčty | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
ms.openlocfilehash: 4d33cf941341f26c88f3a73c5a3d9ac0326db545
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33859264"
---
# <a name="ltmemorygt-enums"></a>&lt;paměť&gt; výčty

||
|-|
|[pointer_safety](#pointer_safety)|

## <a name="pointer_safety"></a>  pointer_safety – výčet

Výčet možných hodnot vrácených `get_pointer_safety`.

pointer_safety – třída {volný, upřednostňované, striktní};

### <a name="remarks"></a>Poznámky

Oboru `enum` definuje hodnoty, které mohou být vráceny `get_pointer_safety()`:

`relaxed` – odvozené neprovádí bezpečné ukazatele (samozřejmě ukazatelé na objekty deklarované nebo přidělené), se považují stejné jako ty bezpečně odvozené.

`preferred` --jako předtím, ale neměli přímo odkázat ukazatele odvozené neprovádí bezpečné.

`strict` – odvozené neprovádí bezpečné ukazatele mohou být považovány jinak než ty bezpečně odvozené.

## <a name="see-also"></a>Viz také

[\<paměť >](../standard-library/memory.md)<br/>
