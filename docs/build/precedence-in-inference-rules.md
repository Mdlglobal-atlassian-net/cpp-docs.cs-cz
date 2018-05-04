---
title: Priorita odvozených pravidel | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- precedence, inference rule
ms.assetid: 69e3dc02-0815-4c3a-b02b-1cb85fceaf24
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 36d462d4222cbfc143dd7487d4cb6b1b8bb3ba3b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="precedence-in-inference-rules"></a>Priorita odvozených pravidel
Pokud pravidlo odvození násobkem definované, používá NMAKE definici nejvyšší prioritou. V následujícím seznamu jsou uvedeny pořadí priorit od nejvyšší po nejnižší:  
  
1.  Pravidlo odvození definované v souboru pravidel; novější definice mají přednost před.  
  
2.  Pravidlo odvození definované v Tools.ini; novější definice mají přednost před.  
  
3.  Předdefinované odvozené pravidlo.  
  
## <a name="see-also"></a>Viz také  
 [Odvozená pravidla](../build/inference-rules.md)