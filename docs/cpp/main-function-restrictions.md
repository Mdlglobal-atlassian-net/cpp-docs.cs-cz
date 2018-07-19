---
title: Main – omezení funkce | Dokumentace Microsoftu
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
ms.openlocfilehash: 3114f1ef379495f36f4231dbad6fd41ac145bcfe
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941743"
---
# <a name="main-function-restrictions"></a>main – omezení funkce
Vztahuje několik omezení `main` funkce, která se nedá použít u jiných funkcí jazyka C++. `main` Funkce:  
  
-   Nemohou být přetíženy (viz [přetížení funkce](function-overloading.md)).  
  
-   Nelze deklarovat jako **vložené**.  
  
-   Nelze deklarovat jako **statické**.  
  
-   Nelze zabrat její adresu.  
  
-   Nelze ji volat.  
  
## <a name="see-also"></a>Viz také  
 [main: spuštění programu](../cpp/main-program-startup.md)