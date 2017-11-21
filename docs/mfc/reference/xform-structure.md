---
title: "Xform – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: XFORM
dev_langs: C++
helpviewer_keywords: XFORM structure [MFC]
ms.assetid: 4fb4ef5b-05d2-4884-82d1-1cb8f7be6302
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3c9e5978d82b1bbaed08eaa05dda53c78160579f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="xform-structure"></a>XFORM – struktura
`XFORM` Struktura má následující formát:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct  tagXFORM {  /* xfrm */  
    FLOAT eM11;  
    FLOAT eM12;  
    FLOAT eM21;  
    FLOAT eM22;  
    FLOAT eDx;  
    FLOAT eDy;  
} XFORM;  
```  
  
## <a name="remarks"></a>Poznámky  
 `XFORM` Struktura určuje world místo k transformaci stránky místa. **EDx** a **eDy** členové zadat komponenty vodorovného a svislého posunutí v uvedeném pořadí. Následující tabulka ukazuje, jak se používají další členy, v závislosti na operaci:  
  
|Operace|eM11|eM12|eM21|eM22|  
|---------------|----------|----------|----------|----------|  
|`Rotation`|Kosinus úhlu otočení|Sinus úhlu otočení|Záporné sinus úhlu otočení|Kosinus úhlu otočení|  
|**Změna měřítka**|Vodorovné škálování součásti|Nothing|Nothing|Svislé škálování součásti|  
|**Zkosení**|Nothing|Vodorovné úměrnosti konstanta|Svislé úměrnosti konstanta|Nothing|  
|**Reflexe**|Součást vodorovné reflexe|Nothing|Nothing|Součást svislé reflexe|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** wingdi.h systému  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRgn::CreateFromData](../../mfc/reference/crgn-class.md#createfromdata)

