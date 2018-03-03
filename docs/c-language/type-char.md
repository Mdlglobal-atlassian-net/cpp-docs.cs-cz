---
title: Typ char | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- type char
- unsigned char keyword [C]
- char keyword [C]
ms.assetid: a5da0866-e780-4793-be87-15a8426e7ea0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f9e3df3b4fd3e2763ef1704133cb111ee8ac067e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="type-char"></a>Znakový typ
`char` Typ se používá k ukládání celočíselnou hodnotu členem reprezentovat znaková sada. Zda je celočíselná hodnota kód ASCII odpovídající zadanému znaku.  
  
 **Konkrétní Microsoft**  
  
 Znak hodnoty typu `unsigned char` mít rozsahu od 0 do 0xFF hexadecimální. A **podepsané char** má rozsah 0x80 do 0x7F. Tyto rozsahy převede 0 do 255 desítkové soustavy a -128 do + 127 decimal, v uvedeném pořadí. Možnost kompilátoru /J změní výchozí hodnoty **podepsané** k `unsigned`.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Úložiště základních typů](../c-language/storage-of-basic-types.md)