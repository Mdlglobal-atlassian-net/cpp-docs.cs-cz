---
title: "Hse_version_info – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: HSE_VERSION_INFO
dev_langs: C++
helpviewer_keywords: HSE_VERSION_INFO structure [MFC]
ms.assetid: 4837312d-68c8-4d05-9afa-1934d7d49b20
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 78b1ed79093db179e00f262b61934ff9c293ff18
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="hseversioninfo-structure"></a>HSE_VERSION_INFO – struktura
Tato struktura ukazuje `pVer` parametr ve `CHttpServer::GetExtensionVersion` – členská funkce. Poskytuje číslo verze ISA a text popisu ISA.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _HSE_VERSION_INFO {  
    DWORD dwExtensionVersion;  
    CHAR lpszExtensionDesc[HSE_MAX_EXT_DLL_NAME_LEN];  
} HSE_VERSION_INFO, *LPHSE_VERSION_INFO;  
```  
  
#### <a name="parameters"></a>Parametry  
 *dwExtensionVersion*  
 Číslo verze ISA.  
  
 *lpszExtensionDesc*  
 Textový popis ISA. Poskytuje výchozí implementaci zástupný text; přepsání `CHttpServer::GetExtensionVersion` poskytnout vlastní popis.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** httpext.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

