---
title: "XMMWORD – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: XMMWORD
dev_langs: C++
helpviewer_keywords: XMMWORD directive
ms.assetid: 18026d32-5cab-403e-ad7e-382fb41aa9b8
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 34bed9288320a5a8eadca88c67da72dd6ee2094d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="xmmword"></a>XMMWORD
Použít pro operandy multimédií 128-bit s pokyny k MMX a SSE (XMM).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
XMMWORD  
```  
  
## <a name="remarks"></a>Poznámky  
 `XMMWORD`reprezentuje stejného typu jako [__m128](../../cpp/m128.md).  
  
## <a name="example"></a>Příklad  
  
```  
movdqa   xmm0, xmmword ptr [ebx]  
```