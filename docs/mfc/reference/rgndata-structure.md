---
title: "Rgndata – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: RGNDATA
dev_langs: C++
helpviewer_keywords: RGNDATA structure [MFC]
ms.assetid: 72257c00-f440-4dca-979e-9b6b5b2d5f2f
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f637dfd76ba293454c7a5c51b12ad60926280a72
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="rgndata-structure"></a>RGNDATA – struktura
`RGNDATA` Struktura obsahuje hlavičku a pole obdélníky, které tvoří oblast. Tyto obdélníky seřazené nahoře vlevo dolů vpravo, se nepřekrývají.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _RGNDATA { /* rgnd */  
    RGNDATAHEADER rdh;  
    char Buffer[1];  
} RGNDATA;  
```  
  
#### <a name="parameters"></a>Parametry  
 *rdh*  
 Určuje [RGNDATAHEADER](http://msdn.microsoft.com/library/windows/desktop/dd162941) struktury. (Další informace o tuto strukturu, najdete v části Windows SDK.) Členy této struktury zadejte typ oblast (jestli je obdélníková nebo lichoběžníkové), počet obdélníků, které tvoří oblasti, velikost vyrovnávací paměti, který obsahuje struktury obdélníku, a tak dále.  
  
 `Buffer`  
 Určuje libovolný velikost vyrovnávací paměti, který obsahuje [Rect –](../../mfc/reference/rect-structure1.md) struktury, které tvoří oblasti.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** wingdi.h systému  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRgn::CreateFromData](../../mfc/reference/crgn-class.md#createfromdata)   
 [CRgn::GetRegionData](../../mfc/reference/crgn-class.md#getregiondata)
