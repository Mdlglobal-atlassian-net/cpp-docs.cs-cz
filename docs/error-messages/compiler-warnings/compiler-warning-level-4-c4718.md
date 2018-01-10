---
title: "Kompilátoru (úroveň 4) upozornění C4718 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4718
dev_langs: C++
helpviewer_keywords: C4718
ms.assetid: 29507f8a-b024-42c1-a3b8-f35d1f2641f3
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 214c481f4ad77a7a67190cd7427e0cd5775ccc8c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4718"></a>C4718 kompilátoru upozornění (úroveň 4)
volání funkce: rekurzivní volání nemá žádné vedlejší účinky odstranění  
  
 Funkce obsahuje zpětného volání, ale jinak nemá žádné vedlejší účinky. Volání této funkce se teď odstraňuje. Správnost programu nemá vliv, ale bude se chování. Zatímco ponechat volání v může mít za následek výjimku přetečení zásobníku modulu runtime, odstraňování volání Odebere tuto možnost.