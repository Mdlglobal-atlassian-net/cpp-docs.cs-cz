---
title: "FILETIME – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- FILETIME
dev_langs:
- C++
helpviewer_keywords:
- FILETIME structure [MFC]
ms.assetid: e09557e2-b6d7-4dd5-a5b9-6328bca88595
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f23f9d4a508158b392de6eb5c872f0b5762e1ae3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="filetime-structure"></a>FILETIME – struktura
`FILETIME` Struktura je 64 bitů hodnotu představující počet 100nanosekundových intervalů od 1. ledna 1601.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _FILETIME {  
    DWORD dwLowDateTime;   /* low 32 bits */  
    DWORD dwHighDateTime;  /* high 32 bits */  
} FILETIME, *PFILETIME, *LPFILETIME;  
```  
  
#### <a name="parameters"></a>Parametry  
 *dwLowDateTime*  
 Určuje nízkou 32bitová verze souboru času.  
  
 *dwHighDateTime*  
 Určuje 32bitová verze času souboru vysokou.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** windef.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CTime::CTime](../../atl-mfc-shared/reference/ctime-class.md#ctime)

