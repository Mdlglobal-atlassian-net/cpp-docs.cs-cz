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
ms.openlocfilehash: fc26358e1da11ada6b23364576bfedb379bc4030
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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