---
title: Operátory přetypování | Dokumentace Microsoftu
ms.custom: index-page
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], casting
- casting operators [C++]
ms.assetid: 16240348-26bc-4f77-8eab-57253f00ce52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4d64a25475ad7ac40f63d29798768f8f57866b3c
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941622"
---
# <a name="casting-operators"></a>Operátory přetypování
Existuje několik operátorů přetypování specifických pro jazyk C++. Účelem těchto operátorů je odstranit některé nejasnosti a nebezpečí spojená s původními přetypováními jazyka C. Těmito operátory jsou:  
  
-   [přetypování dynamic_cast](../cpp/dynamic-cast-operator.md) používán pro převod polymorfních typů.  
  
-   [static_cast](../cpp/static-cast-operator.md) používán pro převod nepolymorfních typů.  
  
-   [const_cast](../cpp/const-cast-operator.md) slouží k odebrání **const**, **volatile**, a **__unaligned** atributy.  
  
-   [reinterpret_cast](../cpp/reinterpret-cast-operator.md) používá pro jednoduchou reinterpretaci bitů.  
  
-   [safe_cast](../windows/safe-cast-cpp-component-extensions.md) použít k tvorbě ověřitelného kódu MSIL.  
  
 Operátory `const_cast` a `reinterpret_cast` používejte jako poslední možnost, protože představují stejné nebezpečí jako stará přetypování. Pro úplné nahrazení starých přetypování jsou však stále zapotřebí.  
  
## <a name="see-also"></a>Viz také  
 [Přetypování](../cpp/casting.md)