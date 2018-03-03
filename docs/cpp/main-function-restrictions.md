---
title: "Main – omezení funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Main
dev_langs:
- C++
helpviewer_keywords:
- main function, restrictions on using
ms.assetid: 7b3df731-344b-44a8-850c-11cbcbfbfa83
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8a94844a0d5636c58a764114ed6f413923d69950
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="main-function-restrictions"></a>main – omezení funkce
Několik omezení se vztahují na **hlavní** funkce, která se nevztahují na jiných funkcí jazyka C++. **Hlavní** funkce:  
  
-   Nemohou být přetíženy (viz [přetížení funkcí](function-overloading.md)).  
  
-   Nelze deklarovat jako **vložené**.  
  
-   Nelze deklarovat jako **statické**.  
  
-   Nelze zabrat její adresu.  
  
-   Nelze ji volat.  
  
## <a name="see-also"></a>Viz také  
 [main: spuštění programu](../cpp/main-program-startup.md)