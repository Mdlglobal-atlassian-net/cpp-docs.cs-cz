---
title: FILETIME – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- FILETIME
dev_langs:
- C++
helpviewer_keywords:
- FILETIME structure [MFC]
ms.assetid: e09557e2-b6d7-4dd5-a5b9-6328bca88595
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b0d1128442300d3f6fc153733be8b23b9d69444d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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

