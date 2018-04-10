---
title: Priorita odvozených pravidel | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- precedence, inference rule
ms.assetid: 69e3dc02-0815-4c3a-b02b-1cb85fceaf24
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f7374da0541fc66464947af5a7b2ea7ea7b5c1d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="precedence-in-inference-rules"></a>Priorita odvozených pravidel
Pokud pravidlo odvození násobkem definované, používá NMAKE definici nejvyšší prioritou. V následujícím seznamu jsou uvedeny pořadí priorit od nejvyšší po nejnižší:  
  
1.  Pravidlo odvození definované v souboru pravidel; novější definice mají přednost před.  
  
2.  Pravidlo odvození definované v Tools.ini; novější definice mají přednost před.  
  
3.  Předdefinované odvozené pravidlo.  
  
## <a name="see-also"></a>Viz také  
 [Odvozená pravidla](../build/inference-rules.md)