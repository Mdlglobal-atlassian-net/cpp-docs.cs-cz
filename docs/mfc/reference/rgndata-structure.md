---
title: Rgndata – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- RGNDATA
dev_langs:
- C++
helpviewer_keywords:
- RGNDATA structure [MFC]
ms.assetid: 72257c00-f440-4dca-979e-9b6b5b2d5f2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 591c2dd65fdb9dde00f0ac1373c39affbe82da85
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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

