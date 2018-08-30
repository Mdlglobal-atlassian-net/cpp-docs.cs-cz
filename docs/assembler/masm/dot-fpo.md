---
title: . FPO | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .FPO
dev_langs:
- C++
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 234ec5bd703a390d1e2ee60e48d99d346d4aad95
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43203110"
---
# <a name="fpo"></a>.FPO
Na. FPO – direktiva určuje emisí záznamů ladění .debug$ F segment nebo část.  
  
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
 Počet místních proměnných, je hodnota bez znaménka 32 bitů.  
  
 `cdwParams`  
 Velikost parametrů v DWORD, je hodnota bez znaménka 16 bitů.  
  
 *cbProlog*  
 Počet bajtů v kódu prologu funkce, je hodnota bez znaménka 8 bitů.  
  
 `cbRegs`  
 Uložit číslo registrů.  
  
 `fUseBP`  
 Určuje, zda byl přidělen do registru EBP. 0 nebo 1.  
  
 *cbFrame*  
 Určuje typ rámce.  Zobrazit [FPO_DATA](/windows/desktop/api/winnt/ns-winnt-_fpo_data) Další informace.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)