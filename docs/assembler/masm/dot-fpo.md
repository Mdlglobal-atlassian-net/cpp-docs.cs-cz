---
title: . FPO | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- .FPO
dev_langs:
- C++
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 76f3fb3d06e3d09cdd63e48ef2ab8a6ce95c81e6
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="fpo"></a>.FPO
Na. FPO – direktiva určuje emisí záznamů ladění .debug$ F segmentu nebo oddíl.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
FPO (  
cdwLocals  
,   
cdwParams  
,   
cbProlog  
,   
cbRegs  
,   
fUseBP  
,   
cbFrame  
)  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `cdwLocals`  
 Počet místní proměnné a hodnotu nepodepsané 32bitové.  
  
 `cdwParams`  
 Velikost parametrů v DWORD hodnotou nepodepsané 16 bitů.  
  
 *cbProlog*  
 Počet bajtů v kódu prologu funkce hodnotou nepodepsané 8bitové.  
  
 `cbRegs`  
 Číslo registry uložit.  
  
 `fUseBP`  
 Určuje, zda byl přidělen EBP registrace. 0 nebo 1.  
  
 *cbFrame*  
 Určuje typ rámce.  V tématu [FPO_DATA](http://msdn.microsoft.com/library/windows/desktop/ms679352) Další informace.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)