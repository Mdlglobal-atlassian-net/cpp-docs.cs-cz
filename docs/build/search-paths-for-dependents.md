---
title: Cesty hledání pro závislosti | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, dependents
- dependents, NMAKE
ms.assetid: bf998e47-da74-48b5-891d-d3d8ce57264b
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f6093db4ac8e0c88dfe6e4b5a5463e5ee8d24349
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="search-paths-for-dependents"></a>Cesty hledání pro závislosti
Každé závislé má cestu volitelné vyhledávání zadaný následujícím způsobem:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
{directory[;directory...]}dependent  
```  
  
## <a name="remarks"></a>Poznámky  
 NMAKE hledá závislé nejprve v aktuálním adresáři a pak v adresáře v uvedeném pořadí. Makro můžete zadat část hodnoty nebo celou cestu k vyhledávání. Uzavřete názvy adresářů v závorkách ({}); několik adresářů oddělujte středníkem (;). Nesmí být mezery ani karty jsou povoleny.  
  
## <a name="see-also"></a>Viz také  
 [Závislé prvky](../build/dependents.md)