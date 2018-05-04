---
title: Převody z ostatních typů | Microsoft Docs
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- values, converting
- type casts, conversion
ms.assetid: 30fbd974-8f5a-4b70-ac44-d3937b96b702
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e919782022ee64f657611a14d6eae6173a67b8c0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="conversions-from-other-types"></a>Převody z ostatních typů

Vzhledem k tomu, **výčtu** hodnota je **int** hodnotu podle definice převody do a z **výčtu** hodnota jsou stejné jako u **int** typu. Pro kompilátor Microsoft C celé číslo, je stejná jako **dlouho**.

**Konkrétní Microsoft**

Nejsou povoleny žádné převody mezi typy struktury a sjednocení.

Libovolná hodnota můžete převést na typ **void**, ale výsledek takový převod lze použít pouze v kontextu, kde je hodnotu výrazu zrušených, například příkaz výrazu.

**Void** typ nemá žádnou hodnotu, podle definice. Proto jej nelze převést na jiný typ, a dalších typů nelze převést na **void** podle přiřazení. Ale explicitně převést hodnotu na typ **void**, jak je popsáno v [převody přetypování](../c-language/type-cast-conversions.md).

**Konkrétní Microsoft END**

## <a name="see-also"></a>Viz také

[Převody přiřazení](../c-language/assignment-conversions.md)  
