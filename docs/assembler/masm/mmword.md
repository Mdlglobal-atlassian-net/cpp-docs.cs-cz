---
title: "MMWORD – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MMWORD
dev_langs: C++
helpviewer_keywords: MMWORD directive
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bbe20f842a97186071431cd73e7de65fa8170bd4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="mmword"></a>MMWORD
Použít pro operandy multimédií 64-bit s pokyny k MMX a SSE (XMM).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
MMWORD  
```  
  
## <a name="remarks"></a>Poznámky  
 `MMWORD`je typu.  Před mmword – který se přidává do MASM ekvivalentní funkce by bylo dosaženo pomocí:  
  
```  
mov mm0, qword ptr [ebx]  
```  
  
 Při i pokyny pracovat na 64-bit operandy `QWORD` je typem pro 64bitové znaménka a `MMWORD` je typem pro hodnotu 64-bit multimédií.  
  
 `MMWORD`reprezentuje stejného typu jako [__m64](../../cpp/m64.md).  
  
## <a name="example"></a>Příklad  
  
```  
movq     mm0, mmword ptr [ebx]  
```