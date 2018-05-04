---
title: Main – omezení funkce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- Main
dev_langs:
- C++
helpviewer_keywords:
- main function, restrictions on using
ms.assetid: 7b3df731-344b-44a8-850c-11cbcbfbfa83
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ed5be2df6e152b26bcade1970b35ad33655e8e02
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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