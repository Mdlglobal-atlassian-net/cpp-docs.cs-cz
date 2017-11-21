---
title: "Vnitřní objekty a vložené sestavení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 8affd4bb-279d-46f3-851f-8be0a9c5ed3f
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c60932b719b25365c7d8f65a4649ef782a4f9888
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="intrinsics-and-inline-assembly"></a>Vnitřní objekty a vložené sestavení
Jedním z omezení [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] kompilátoru je, aby žádná podpora vloženého assembleru. To znamená, že funkce, které nelze zapsat do jazyka C nebo C++ bude buď mít k zapsání jako subrutiny nebo jako vnitřní funkce kompilátoru nepodporuje. Určité funkce jsou citlivé výkonu, zatímco jiné nejsou. Funkce náročné na výkon by měla být implementována jako vnitřní funkce.  
  
 Překladače kompilátorem jsou popsány v [vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md).  
  
## <a name="see-also"></a>Viz také  
 [x64 softwarové konvence](../build/x64-software-conventions.md)