---
title: Xform – struktura | Dokumentace Microsoftu
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
ms.openlocfilehash: 6084882bed6690269fbb926f394159491d22978a
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37885881"
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
 `XFORM` Struktura určuje globálním prostoru k transformaci místo stránky. `eDx` a `eDy` členy určete součásti vodorovného a svislého posunutí, v uvedeném pořadí. Následující tabulka ukazuje, jak jsou používána jinými členy, v závislosti na operaci:  
  
|Operace|eM11|eM12|eM21|eM22|  
|---------------|----------|----------|----------|----------|  
|`Rotation`|Kosinus úhlu otočení|Sinus úhlu otočení|Záporná sinus úhlu otočení|Kosinus úhlu otočení|  
|`Scaling`|Horizontální škálování komponenty|Nothing|Nothing|Vertikální škálování komponenty|  
|`Shear`|Nothing|Vodorovné přiměřenost – konstanta|Svislé přiměřenost – konstanta|Nothing|  
|`Reflection`|Komponenta vodorovné reflexe|Nothing|Nothing|Komponenta svislé reflexe|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** wingdi.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRgn::CreateFromData](../../mfc/reference/crgn-class.md#createfromdata)

