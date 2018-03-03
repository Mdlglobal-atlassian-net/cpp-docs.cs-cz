---
title: "Logbrush – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LOGBRUSH
dev_langs:
- C++
helpviewer_keywords:
- LOGBRUSH structure [MFC]
ms.assetid: 1bf96768-52c5-4444-9bb8-d41ba2e27e68
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ec6cc9b61f837db4c9766c077fa60f4d9c2b95bd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="logbrush-structure"></a>LOGBRUSH – struktura
`LOGBRUSH` Struktura definuje styl, barvu a vzor fyzické štětce. Se používají v systému Windows [CreateBrushIndirect](http://msdn.microsoft.com/library/windows/desktop/dd183487) a [ExtCreatePen](http://msdn.microsoft.com/library/windows/desktop/dd162705) funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tag LOGBRUSH { /* lb */  
    UINT lbStyle;  
    COLORREF lbColor;  
    LONG lbHatch;  
} LOGBRUSH;  
```  
  
#### <a name="parameters"></a>Parametry  
 `lbStyle`  
 Určuje styl štětce. `lbStyle` Člen musí mít jednu z následujících styly:  
  
- **BS_DIBPATTERN** vzor štětce definované specifikací device independent bitmap (DIB). Pokud `lbStyle` je **BS_DIBPATTERN**, **lbHatch** člen obsahuje popisovač pro sbalený DIB.  
  
- **BS_DIBPATTERNPT** vzor štětce definované specifikací device independent bitmap (DIB). Pokud `lbStyle` je **BS_DIBPATTERNPT**, **lbHatch** člen obsahuje ukazatel sbalené DIB.  
  
- **BS_HATCHED** zasílána štětce.  
  
- **BS_HOLLOW** nástroj prázdný štětce.  
  
- **BS_NULL** stejné jako **BS_HOLLOW**.  
  
- **BS_PATTERN** vzor štětce definované rastrový obrázek paměti.  
  
- **BS_SOLID** plného štětce.  
  
 `lbColor`  
 Určuje barvu, ve kterém má být odeslána stopy. Pokud `lbStyle` je **BS_HOLLOW** nebo **BS_PATTERN** styl, **lbColor** je ignorována. Pokud `lbStyle` je **BS_DIBPATTERN** nebo **BS_DIBPATTERNBT**, word nejnižší z **lbColor** Určuje, zda **bmiColors**členy [bitmapinfo –](../../mfc/reference/bitmapinfo-structure.md) struktura obsahovat explicitní červená, zelená, modrá hodnoty (RGB) nebo indexy, které do aktuálně zjištěné logické palety. **LbColor** člen musí mít jednu z následujících hodnot:  
  
- **DIB_PAL_COLORS** tabulce barev se skládá z pole indexů 16bitové do aktuálně zjištěné logické palety.  
  
- **DIB_RGB_COLORS** tabulce barev obsahuje literál hodnoty RGB.  
  
 *lbHatch*  
 Určuje styl šrafování. Význam závisí na styl štětce definované `lbStyle`. Pokud `lbStyle` je **BS_DIBPATTERN**, **lbHatch** člen obsahuje popisovač pro sbalený DIB. Pokud `lbStyle` je **BS_DIBPATTERNPT**, **lbHatch** člen obsahuje ukazatel sbalené DIB. Pokud `lbStyle` je **BS_HATCHED**, **lbHatch** člen Určuje orientaci čáry použité k vytvoření šrafování. Může být jedna z následujících hodnot:  
  
- `HS_BDIAGONAL`45 stupňů vzestupný, zleva doprava šrafování  
  
- `HS_CROSS`Mřížkovaný vodorovně a svisle  
  
- `HS_DIAGCROSS`Mřížkovaný 45 stupňů  
  
- `HS_FDIAGONAL`45 stupňů směrem dolů, doleva doprava šrafování  
  
- `HS_HORIZONTAL`Vodorovné šrafování  
  
- `HS_VERTICAL`Vertikální šrafování  
  
 Pokud `lbStyle` je **BS_PATTERN**, **lbHatch** je popisovač pro bitovou mapu, která definuje vzoru. Pokud `lbStyle` je **BS_SOLID** nebo **BS_HOLLOW**, **lbHatch** je ignorována.  
  
## <a name="remarks"></a>Poznámky  
 I když **lbColor** prvky štětcem šrafování barvu popředí [CDC::SetBkMode](../../mfc/reference/cdc-class.md#setbkmode) a [CDC::SetBkColor](../../mfc/reference/cdc-class.md#setbkcolor) funkce řízení barvu pozadí.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** wingdi.h systému  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)

