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
ms.openlocfilehash: 981d4c8c0ef30993811e5dbb6fd0a112a6447011
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406491"
---
# <a name="main-function-restrictions"></a>main – omezení funkce
Vztahuje několik omezení **hlavní** funkce, která se nedá použít u jiných funkcí jazyka C++. **Hlavní** funkce:  
  
-   Nemohou být přetíženy (viz [přetížení funkce](function-overloading.md)).  
  
-   Nelze deklarovat jako **vložené**.  
  
-   Nelze deklarovat jako **statické**.  
  
-   Nelze zabrat její adresu.  
  
-   Nelze ji volat.  
  
## <a name="see-also"></a>Viz také:  
 [main: spuštění programu](../cpp/main-program-startup.md)