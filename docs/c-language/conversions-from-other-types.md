---
title: "Převody z ostatních typů | Microsoft Docs"
ms.custom: 
ms.date: 01/29/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- values, converting
- type casts, conversion
ms.assetid: 30fbd974-8f5a-4b70-ac44-d3937b96b702
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 30021ad4058eed7d9fbca31b8e3d3141a55987f2
ms.sourcegitcommit: 30ab99c775d99371ed22d1a46598e542012ed8c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/03/2018
---
# <a name="conversions-from-other-types"></a>Převody z ostatních typů

Vzhledem k tomu, **výčtu** hodnota je **int** hodnotu podle definice převody do a z **výčtu** hodnota jsou stejné jako u **int** typu. Pro kompilátor Microsoft C celé číslo, je stejná jako **dlouho**.

**Microsoft Specific**

Nejsou povoleny žádné převody mezi typy struktury a sjednocení.

Libovolná hodnota můžete převést na typ **void**, ale výsledek takový převod lze použít pouze v kontextu, kde je hodnotu výrazu zrušených, například příkaz výrazu.

**Void** typ nemá žádnou hodnotu, podle definice. Proto jej nelze převést na jiný typ, a dalších typů nelze převést na **void** podle přiřazení. Ale explicitně převést hodnotu na typ **void**, jak je popsáno v [převody přetypování](../c-language/type-cast-conversions.md).

**Konkrétní Microsoft END**

## <a name="see-also"></a>Viz také

[Převody přiřazení](../c-language/assignment-conversions.md)  
