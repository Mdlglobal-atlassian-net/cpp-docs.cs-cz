---
title: ALIAS (MASM) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Alias
dev_langs: C++
helpviewer_keywords: ALIAS directive
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 39f539c18ce23fb3ef9630e4bfdfca8f265beb33
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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