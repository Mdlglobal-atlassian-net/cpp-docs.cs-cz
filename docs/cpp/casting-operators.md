---
title: "Operátory přetypování | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: 'index-page '
dev_langs: C++
helpviewer_keywords:
- operators [C++], casting
- casting operators [C++]
ms.assetid: 16240348-26bc-4f77-8eab-57253f00ce52
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 04ee6e8e35667c9cc08c18f05fbfc09cdad30ccf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="casting-operators"></a>Operátory přetypování
Existuje několik operátorů přetypování specifických pro jazyk C++. Účelem těchto operátorů je odstranit některé nejasnosti a nebezpečí spojená s původními přetypováními jazyka C. Těmito operátory jsou:  
  
-   [dynamic_cast](../cpp/dynamic-cast-operator.md) nepoužije pro převod typů polymorfní.  
  
-   [static_cast](../cpp/static-cast-operator.md) nepoužije pro převod typů nonpolymorphic.  
  
-   [const_cast –](../cpp/const-cast-operator.md) slouží k odebírání `const`, `volatile`, a `__unaligned` atributy.  
  
-   [reinterpret_cast](../cpp/reinterpret-cast-operator.md) použít pro jednoduché reinterpretation bitů.  
  
-   [safe_cast](../windows/safe-cast-cpp-component-extensions.md) používají k vytvoření ověřitelných MSIL.  
  
 Operátory `const_cast` a `reinterpret_cast` používejte jako poslední možnost, protože představují stejné nebezpečí jako stará přetypování. Pro úplné nahrazení starých přetypování jsou však stále zapotřebí.  
  
## <a name="see-also"></a>Viz také  
 [Přetypování](../cpp/casting.md)