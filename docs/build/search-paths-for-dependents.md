---
title: Cesty hledání pro závislosti | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, dependents
- dependents, NMAKE
ms.assetid: bf998e47-da74-48b5-891d-d3d8ce57264b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 577fc7e44bfff35cf7efdcff20dc4cdca1c7001e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380482"
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