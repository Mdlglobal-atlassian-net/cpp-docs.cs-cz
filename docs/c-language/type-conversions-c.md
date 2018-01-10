---
title: Zadejte Conversions (C) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- conversions, type
- type conversion
- converting types
- integral promotions
- type casts, when performed
ms.assetid: d130ee7c-03c3-48f4-af7b-1fdba0d3b086
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b1e4dede1dab1fcaf9ae4de5846539924d0095e4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="type-conversions-c"></a>Převody typu (C)
Převody typu závisí na zadaném operátoru a typu operandu nebo operátorů. Převody typu jsou prováděny v následujících případech:  
  
-   pokud je hodnota jednoho typu přiřazena proměnné jiného typu nebo pokud operátor převede typ operandu či operandů před provedením operace,  
  
-   pokud je hodnota jednoho typu explicitně přetypována na jiný typ,  
  
-   pokud je hodnota předána jako argument funkci nebo pokud je navrácen typ z funkce.  
  
 Znak, short integer nebo celočíselné bitové pole, které mají nebo nemají znaménko, případně objekt typu výčtu lze použít ve výrazu všude tam, kde lze použít celé číslo. Pokud může `int` představovat všechny hodnoty původního typu, pak je hodnota převedena na `int`, jinak je převedena na `unsigned int`. Tento proces se nazývá „integrální povýšení“. Integrální povýšení zachovává hodnotu. To znamená, že hodnota po povýšení zůstane stejná jako před povýšením. V tématu [obvyklé aritmetické převody](../c-language/usual-arithmetic-conversions.md) Další informace.  
  
## <a name="see-also"></a>Viz také  
 [Výrazy a přiřazení](../c-language/expressions-and-assignments.md)