---
title: Logbrush – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- LOGBRUSH
dev_langs:
- C++
helpviewer_keywords:
- LOGBRUSH structure [MFC]
ms.assetid: 1bf96768-52c5-4444-9bb8-d41ba2e27e68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 15b904a07eb668a59a269741973424aa30e15877
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37336403"
---
# <a name="logbrush-structure"></a>LOGBRUSH – struktura
`LOGBRUSH` Struktury definuje styl, barvu a vzor fyzické štětce. Používá se Windows [CreateBrushIndirect](http://msdn.microsoft.com/library/windows/desktop/dd183487) a [ExtCreatePen](http://msdn.microsoft.com/library/windows/desktop/dd162705) funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tag LOGBRUSH { /* lb */  
    UINT lbStyle;  
    COLORREF lbColor;  
    LONG lbHatch;  
} LOGBRUSH;  
```  
  
#### <a name="parameters"></a>Parametry  
 *lbStyle*  
 Určuje styl štětce. `lbStyle` Člena musí být jedna z následujících styly:  
  
- Štětec vzor BS_DIBPATTERN A určené device independent bitmap specifikace (DIB). Pokud *lbStyle* BS_DIBPATTERN, je `lbHatch` člena obsahuje popisovač sbalené DIB.  
  
- Štětec vzor BS_DIBPATTERNPT A určené device independent bitmap specifikace (DIB). Pokud *lbStyle* je BS_DIBPATTERNPT, `lbHatch` člena obsahuje ukazatel na sbalené DIB.  
  
- Zasílána BS_HATCHED štětce.  
  
- Prázdný BS_HOLLOW štětce.  
  
- BS_NULL stejné jako BS_HOLLOW.  
  
- Vzor BS_PATTERN štětce určené paměti rastrový obrázek.  
  
- BS_SOLID plného štětce.  
  
 *lbColor*  
 Určuje barvu, ve kterém má být vykreslen štětec. Pokud *lbStyle* není daný styl BS_HOLLOW nebo BS_PATTERN *lbColor* se ignoruje. Pokud *lbStyle* BS_DIBPATTERN nebo BS_DIBPATTERNBT nižší řád slova *lbColor* Určuje, zda `bmiColors` členy [bitmapinfo –](../../mfc/reference/bitmapinfo-structure.md) struktura obsahovat explicitní červená, zelená, modrá hodnoty (RGB) nebo indexů do aktuálně realizované logickou paletu. `lbColor` Člena musí být jedna z následujících hodnot:  
  
- DIB_PAL_COLORS tabulku barvy se skládá z pole indexů 16-bit do aktuálně realizované logickou paletu.  
  
- Tabulky barev DIB_RGB_COLORS obsahuje literálové hodnoty RGB.  
  
 *lbHatch*  
 Určuje styl šrafování. Význam závisí na styl štětce určené *lbStyle*. Pokud *lbStyle* BS_DIBPATTERN, je `lbHatch` člena obsahuje popisovač sbalené DIB. Pokud *lbStyle* je BS_DIBPATTERNPT, `lbHatch` člena obsahuje ukazatel na sbalené DIB. Pokud *lbStyle* je BS_HATCHED, `lbHatch` člen Určuje orientaci čáry použité k vytvoření šrafování. Může být jeden z následujících hodnot:  
  
- Šrafování HS_BDIAGONAL A 45 stupňů nahoru, zleva doprava  
  
- HS_CROSS vodorovné a svislé mřížkovaný  
  
- Mřížkovaný HS_DIAGCROSS 45 stupňů  
  
- Šrafování HS_FDIAGONAL A 45 stupňů směrem dolů, zleva doprava  
  
- Vodorovné HS_HORIZONTAL šrafování  
  
- Svislé HS_VERTICAL šrafování  
  
 Pokud *lbStyle* je BS_PATTERN, *lbHatch* je popisovač rastrový obrázek, který definuje vzor. Pokud *lbStyle* BS_SOLID nebo BS_HOLLOW, *lbHatch* se ignoruje.  
  
## <a name="remarks"></a>Poznámky  
 I když *lbColor* řídí barvu popředí šrafování štětce, [CDC::SetBkMode](../../mfc/reference/cdc-class.md#setbkmode) a [CDC::SetBkColor](../../mfc/reference/cdc-class.md#setbkcolor) funkce řídí barvu pozadí.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** wingdi.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)

