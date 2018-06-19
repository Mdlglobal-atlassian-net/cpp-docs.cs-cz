---
title: . ZÁSOBNÍK | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .STACK
dev_langs:
- C++
helpviewer_keywords:
- .STACK directive
ms.assetid: 70019463-5d4f-41b6-8464-023a8ac2466f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dab47677da8db2afca73a078b110300a017e7c8d
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
ms.locfileid: "32052297"
---
# <a name="stack"></a>.STACK
Při použití s [. MODEL](../../assembler/masm/dot-model.md), definuje segment zásobníku (s názvem segmentu zásobníku). Volitelné `size` určuje počet bajtů pro zásobníku (výchozí nastavení 1 024 jednotek). `.STACK` – Direktiva automaticky zavře příkaz zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STACK [[size]]  
```  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)