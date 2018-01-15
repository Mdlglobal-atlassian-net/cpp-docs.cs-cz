---
title: "Konstanty obor názvů souběžnosti (AMP) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp/Concurrency::HLSL_MAX_NUM_BUFFERS
- amp/Concurrency::MODULENAME_MAX_LENGTH
dev_langs: C++
ms.assetid: 13a8e8cd-2eec-4e60-a91d-5d271072747b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a28853f91c6d75a322d6edfd15b96f5589b74e0a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="concurrency-namespace-constants-amp"></a>Konstanty obor názvů souběžnosti (AMP)
|||  
|-|-|  
|[HLSL_MAX_NUM_BUFFERS –](#hlsl_max_num_buffers)|[MODULENAME_MAX_LENGTH –](#modulename_max_length)|  
  
##  <a name="hlsl_max_num_buffers"></a>Hlsl_max_num_buffers – konstanta  
 Maximální počet povolený DirectX vyrovnávací paměti.  
  
```  
static const UINT HLSL_MAX_NUM_BUFFERS = 64 + 128;  
```  
  
##  <a name="modulename_max_length"></a>Modulename_max_length – konstanta  
 Ukládá maximální délka názvu modulu. Tato hodnota musí být stejný v kompilátoru a modulu runtime.  
  
```  
static const UINT MODULENAME_MAX_LENGTH = 1024;  
```  
  
## <a name="see-also"></a>Viz také  
 [Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
