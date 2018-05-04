---
title: Vnitřní objekty a vložené sestavení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8affd4bb-279d-46f3-851f-8be0a9c5ed3f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5b8651bea0b1ee9f54ec0af704d92feef0722368
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="intrinsics-and-inline-assembly"></a>Vnitřní objekty a vložené sestavení
Jedním z omezení [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] kompilátoru je, aby žádná podpora vloženého assembleru. To znamená, že funkce, které nelze zapsat do jazyka C nebo C++ bude buď mít k zapsání jako subrutiny nebo jako vnitřní funkce kompilátoru nepodporuje. Určité funkce jsou citlivé výkonu, zatímco jiné nejsou. Funkce náročné na výkon by měla být implementována jako vnitřní funkce.  
  
 Překladače kompilátorem jsou popsány v [vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md).  
  
## <a name="see-also"></a>Viz také  
 [x64 – softwarové konvence](../build/x64-software-conventions.md)