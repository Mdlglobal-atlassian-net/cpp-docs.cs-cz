---
title: "MMWORD – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- MMWORD
dev_langs:
- C++
helpviewer_keywords:
- MMWORD directive
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0570a55dc11994e12acedb85d3ae8015abefb54c
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="mmword"></a>MMWORD
Použít pro operandy multimédií 64-bit s pokyny k MMX a SSE (XMM).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
MMWORD  
```  
  
## <a name="remarks"></a>Poznámky  
 `MMWORD` je typu.  Před mmword – který se přidává do MASM ekvivalentní funkce by bylo dosaženo pomocí:  
  
```  
mov mm0, qword ptr [ebx]  
```  
  
 Při i pokyny pracovat na 64-bit operandy `QWORD` je typem pro 64bitové znaménka a `MMWORD` je typem pro hodnotu 64-bit multimédií.  
  
 `MMWORD` reprezentuje stejného typu jako [__m64](../../cpp/m64.md).  
  
## <a name="example"></a>Příklad  
  
```  
movq     mm0, mmword ptr [ebx]  
```