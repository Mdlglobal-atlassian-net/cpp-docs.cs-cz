---
title: MMWORD – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- MMWORD
dev_langs:
- C++
helpviewer_keywords:
- MMWORD directive
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e97b1e58116d633519b1a780928e05862ac1771d
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
ms.locfileid: "32054777"
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