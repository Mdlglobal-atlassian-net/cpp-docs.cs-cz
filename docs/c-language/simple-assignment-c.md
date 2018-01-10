---
title: "Jednoduché Assignment (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- type conversion [C++], simple assignment
- data type conversion [C++], simple assignment
- operators [C], simple assignment
- assignment operators [C++], simple
- simple assignment operator
- equal sign
ms.assetid: e7140a0a-7104-4b3a-b293-7adcc1fdd52b
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1cf9c5675affb6dcaea78e0cabf2a4427ad03938
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="simple-assignment-c"></a>Jednoduché přiřazení (C)
Operátor jednoduchého přiřazení přiřadí svůj pravý operand levému operandu. Hodnota pravého operandu je převedena na typ výrazu přiřazení a nahradí hodnotu uloženou v objektu určeném levým operandem. Použití pravidel převodu pro přiřazení (viz [převody přiřazení](../c-language/assignment-conversions.md)).  
  
```  
double x;  
int y;  
  
x = y;  
```  
  
 V tomto příkladu hodnota `y` je převést na typ **dvojité** a přiřazení `x`.  
  
## <a name="see-also"></a>Viz také  
 [Operátory přiřazení v jazyce C](../c-language/c-assignment-operators.md)