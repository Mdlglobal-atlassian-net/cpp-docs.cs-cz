---
title: ALIAS (MASM) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- Alias
dev_langs:
- C++
helpviewer_keywords:
- ALIAS directive
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c1487afc250646b5cf1a12673dd43f6b1996a4f0
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="alias-masm"></a>ALIAS (MASM)
**ALIAS** – direktiva vytvoří alternativní název pro funkci.  To umožňuje vytvořit více názvů pro funkci nebo knihovny, které umožňují linkeru (LINK.exe) pro mapování staré funkce na novou funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ALIAS  <  
alias  
> = <  
actual-name  
>  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `actual-name`  
 Skutečný název funkce nebo procedury.  Lomené závorky jsou povinné.  
  
 `alias`  
 Název alternativní nebo alias.  Lomené závorky jsou povinné.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)