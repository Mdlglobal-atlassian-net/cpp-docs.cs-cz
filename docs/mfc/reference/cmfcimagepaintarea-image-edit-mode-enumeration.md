---
title: "CMFCImagePaintArea::IMAGE_EDIT_MODE – výčet | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IMAGE_EDIT_MODE Enumeration
dev_langs: C++
helpviewer_keywords: IMAGE_EDIT_MODE Enumeration method [MFC]
ms.assetid: e51db66a-fa1c-4766-9dac-a25b595f871a
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cd59e80dfd019627c0ebe88e116e225f92e3a8ec
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cmfcimagepaintareaimageeditmode-enumeration"></a>CMFCImagePaintArea::IMAGE_EDIT_MODE – výčet
Určuje režim kreslení, který používáte k úpravě bitovou kopii v dialogovém okně editor bitové kopie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
enum IMAGE_EDIT_MODE  
{  
    IMAGE_EDIT_MODE_PEN = 0,  
    IMAGE_EDIT_MODE_FILL, 
    IMAGE_EDIT_MODE_LINE, 
    IMAGE_EDIT_MODE_RECT, 
    IMAGE_EDIT_MODE_ELLIPSE, 
    IMAGE_EDIT_MODE_COLOR 
};  
```  
  
## <a name="members"></a>Členové  
  
|||  
|-|-|  
|Název|Popis|  
|`IMAGE_EDIT_MODE_PEN`|Použít k vykreslení jednotlivých pixelů.|  
|`IMAGE_EDIT_MODE_FILL`|Použitou k vyplnění všech sousedících oblastí, které obsahují barvu na aktuální umístění kurzoru.|  
|`IMAGE_EDIT_MODE_LINE`|Použít kreslení čáry.|  
|`IMAGE_EDIT_MODE_RECT`|Použít k vykreslení obdélníku.|  
|`IMAGE_EDIT_MODE_ELLIPSE`|Použít k vykreslení elipsy.|  
|`IMAGE_EDIT_MODE_COLOR`|Slouží k nastavení aktuální barvu na barvu na aktuální pozici kurzoru.|  
  
### <a name="remarks"></a>Poznámky  
 `CMFCImagePaintArea` a `CMFCImageEditorDialog` třídy můžete nastavit aktuální režim kreslení pomocí tento výčet. Režim kreslení a aktuální barva se používají k úpravě oblasti obrázku v dialogovém okně editor bitové kopie. Další informace o `CMFCImagePaintArea` a `CMFCImageEditorDialog`, najdete v části [CMFCImagePaintArea třída](../../mfc/reference/cmfcimagepaintarea-class.md) a [CMFCImageEditorDialog třída](../../mfc/reference/cmfcimageeditordialog-class.md).  
  
 Když vyberete barvy z obrázku pomocí `IMAGE_EDIT_MODE_COLOR` režim kreslení rozhraní nastaví aktuální režim kreslení na `IMAGE_EDIT_MODE_PEN`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afximagepaintarea.h  
  
## <a name="see-also"></a>Viz také  
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCImagePaintArea – třída](../../mfc/reference/cmfcimagepaintarea-class.md)   
 [CMFCImageEditorDialog – třída](../../mfc/reference/cmfcimageeditordialog-class.md)
