---
title: ". DOSSEG – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: .DOSSEG
dev_langs: C++
helpviewer_keywords: .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8a53159911c47d1c88df90c53f3302f813e5bd95
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="dosseg"></a>.DOSSEG
Řadí segmenty podle konvence segment MS-DOS: kód nejprve pak segmentuje není v DGROUP a pak v DGROUP segmentuje.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.DOSSEG  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Segmentů v DGROUP podle tomto pořadí: segmenty není v BSS nebo zásobníku, pak BSS segmentů a nakonec segmenty zásobníku. Používá se především pro zajištění podpory CodeView v samostatné programy MASM. Stejné jako [dosseg –](../../assembler/masm/dosseg.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)