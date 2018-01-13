---
title: . FPO | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: .FPO
dev_langs: C++
helpviewer_keywords: .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 61d9209b5cf817d89e9e017626222a9cc73e209e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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