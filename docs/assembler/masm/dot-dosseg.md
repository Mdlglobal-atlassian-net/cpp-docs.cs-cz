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
ms.openlocfilehash: 4d2156161686583ba00d357c1dbca2e2e2867e9b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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