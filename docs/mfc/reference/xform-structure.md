---
title: Xform – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- XFORM
dev_langs:
- C++
helpviewer_keywords:
- XFORM structure [MFC]
ms.assetid: 4fb4ef5b-05d2-4884-82d1-1cb8f7be6302
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1a1c3a8abd39f7f190f36a18e7691475d951cab8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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

