---
title: . DOSSEG – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .DOSSEG
dev_langs:
- C++
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3817cfe98758faf86ea87d74e02657598c3e806b
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
ms.locfileid: "32054881"
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