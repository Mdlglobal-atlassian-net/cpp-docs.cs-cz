---
title: MÍSTNÍ (MASM) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- Local
dev_langs:
- C++
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed9926d23f2e1e8636f31a6f586609ae22d38acd
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="local-masm"></a>LOCAL (MASM)
V první – direktiva v rámci makra **místní** definuje popisky, které jsou jedinečné pro každou instanci makro.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      LOCAL localname [[, localname]]...  
LOCAL label [[ [count ] ]] [[:type]] [[, label [[ [count] ]] [[type]]]]...  
```  
  
## <a name="remarks"></a>Poznámky  
 V druhé – direktiva v rámci postupu definice (**PROC**), **místní** vytvoří na základě zásobníku proměnné, které existují po dobu trvání procesu. *Popisek* může být jednoduché proměnné nebo pole obsahující *počet* elementy.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)