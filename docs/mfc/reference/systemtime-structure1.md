---
title: "SYSTEMTIME – Struktura1 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SYSTEMTIME
dev_langs: C++
helpviewer_keywords: SYSTEMTIME structure [MFC]
ms.assetid: 9aaef4d6-de79-4fa1-8158-86b245ef5bff
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 07af222a3d51ff1cc71076d5bbcc3513a3d6cad4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="systemtime-structure1"></a>SYSTEMTIME – Struktura1
`SYSTEMTIME` Struktura představuje datum a čas pomocí jednotlivé členy pro měsíc, den, roku, den v týdnu, hodinu, minutu, sekundu a milisekundu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _SYSTEMTIME {  
    WORD wYear;  
    WORD wMonth;  
    WORD wDayOfWeek;  
    WORD wDay;  
    WORD wHour;  
    WORD wMinute;  
    WORD wSecond;  
    WORD wMilliseconds;  
} SYSTEMTIME;  
```  
  
#### <a name="parameters"></a>Parametry  
 *wYear*  
 Do aktuálního roku.  
  
 *Přechodu*  
 V aktuálním měsíci; Leden je 1.  
  
 *wDayOfWeek*  
 Aktuální den v týdnu; Neděle je 0, pondělí je 1 a tak dále.  
  
 *wDay*  
 Aktuální den v měsíci.  
  
 *wHour*  
 Do aktuální hodiny.  
  
 *wMinute*  
 Do aktuální minuty.  
  
 *wSecond*  
 Do aktuální sekundy.  
  
 *wMilliseconds*  
 Aktuální milisekundu.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#39](../../mfc/codesnippet/cpp/systemtime-structure1_1.cpp)]  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** winbase.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CTime::CTime](../../atl-mfc-shared/reference/ctime-class.md#ctime)

