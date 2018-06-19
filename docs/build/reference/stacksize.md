---
title: VELIKOST ZÁSOBNÍKU | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- STACKSIZE
dev_langs:
- C++
helpviewer_keywords:
- STACKSIZE .def file statement
ms.assetid: 4d8c79bd-1cb4-4e4d-90f2-b5a7a4d20e7a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1b2093762b3c6f21d319c53a85da5ec5b430a1fd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376244"
---
# <a name="stacksize"></a>VELIKOST ZÁSOBNÍKU
Nastaví velikost zásobníku v bajtech.  
  
```  
STACKSIZE reserve[,commit]  
```  
  
## <a name="remarks"></a>Poznámky  
 Je ekvivalentní způsob, jak v zásobníku [přidělení zásobníku](../../build/reference/stack-stack-allocations.md) (/ STACK) – možnost. Najdete v dokumentaci na tuto možnost Podrobnosti *rezervovat* a `commit` argumenty.  
  
 Tato možnost nemá žádný vliv na knihovny DLL.  
  
## <a name="see-also"></a>Viz také  
 [Pravidla pro příkazy definice modulu](../../build/reference/rules-for-module-definition-statements.md)