---
title: "Grafické objekty | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- HRGN
- HFONT
- HBITMAP
dev_langs:
- C++
helpviewer_keywords:
- CRgn class [MFC], HRGN handle type
- HPEN [MFC]
- objects [MFC], graphic
- palettes [MFC], creating in device context
- pens [MFC], creating in device context
- bitmaps [MFC], creating in device contexts
- palette objects [MFC]
- memory [MFC], display contexts
- MFC, graphic objects
- regions [MFC], creating in device context
- CPen class [MFC], HPEN handle type
- GDI objects [MFC]
- HRGN [MFC]
- graphic objects [MFC]
- GDI objects [MFC], graphic-object classes
- CFont class [MFC], HFONT handle type
- HFONT and class CFont [MFC]
- HBITMAP and class CBitmap [MFC]
- fonts [MFC], creating in device context
- images [MFC], graphic objects [MFC]
- CBitmap class [MFC], HBITMAP handle type
- HPALETTE and class CPalette [MFC]
- CBrush class [MFC], HBRUSH handle type
- objects [MFC], graphic objects
- drawing [MFC], in device contexts
- device contexts [MFC], graphic objects [MFC]
- brushes [MFC], creating in device context
- region objects [MFC]
- pen objects [MFC]
- GDI [MFC], graphic-object classes
- graphic objects [MFC], creating in device context
- HBRUSH and class CBrush [MFC]
- painting and device context [MFC]
- CPalette class [MFC], HPALETTE handle type
ms.assetid: 41963b25-34b7-4343-8446-34ba516b83ca
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6dfdba311ed13b1ffbd5e1f830d6fa87cfce915d
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2018
---
# <a name="graphic-objects"></a>Grafické objekty
Systém Windows nabízí celou řadu kreslení nástroje dostupné v kontextech zařízení. Poskytuje pera kreslení čar, štětce výplně vnitřek a písem pro kreslení textu. Knihovna MFC poskytuje třídy grafických objektů ekvivalentní nástrojů pro kreslení v systému Windows. Následující tabulka uvádí dostupných tříd a ekvivalentní grafika Windows typy popisovač rozhraní GDI zařízení.  
  
> [!NOTE]
>  Další informace najdete v dokumentaci rozhraní GDI + SDK na: [http://msdn.microsoft.com/library/default.aspurl=/library/gdicpp/GDIPlus/GDIPlus.asp](http://msdn.microsoft.com/library/default.aspurl=/library/gdicpp/gdiplus/gdiplus.asp).  
  
 Tento článek vysvětluje použití tyto třídy grafických objektů:  
  
### <a name="classes-for-windows-gdi-objects"></a>Třídy pro Windows GDI – objekty  
  
|Třída|Windows zpracovat typ|  
|-----------|-------------------------|  
|[CPen](../mfc/reference/cpen-class.md)|`HPEN`|  
|[CBrush](../mfc/reference/cbrush-class.md)|`HBRUSH`|  
|[CFont](../mfc/reference/cfont-class.md)|**HFONT**|  
|[CBitmap](../mfc/reference/cbitmap-class.md)|`HBITMAP`|  
|[CPalette](../mfc/reference/cpalette-class.md)|`HPALETTE`|  
|[CRgn](../mfc/reference/crgn-class.md)|**HRGN**|  
  
> [!NOTE]
>  Třída [CImage](../atl-mfc-shared/reference/cimage-class.md) poskytuje podporu rozšířené rastrového obrázku.  
  
 Každá třída grafických objektů v knihovně tříd má konstruktor, který vám umožní vytvořit grafické objekty této třídy, které je třeba pak inicializovat pomocí funkce vhodné vytvořit, jako `CreatePen`.  
  
 Každá třída grafických objektů v knihovně tříd má operátor přetypování, který bude převeden objekt MFC tak, aby přidružené popisovačů systému Windows. Výsledný popisovač je platný, dokud přidružený objekt umožňuje odpojit ho. Pomocí objektu **odpojení** – členská funkce odpojit popisovač.  
  
 Následující kód přetypování `CPen` objekt, který chcete popisovačů systému Windows:  
  
 [!code-cpp[NVC_MFCDocViewSDI#5](../mfc/codesnippet/cpp/graphic-objects_1.cpp)]  
  
#### <a name="to-create-a-graphic-object-in-a-device-context"></a>Chcete-li vytvořit grafického objektu v kontextu zařízení  
  
1.  Definujte grafického objektu v rámci zásobníku. Například inicializaci objektu pomocí funkce specifické pro typ vytvořit `CreatePen`. Alternativně inicializaci objektu v konstruktoru. Přečtěte si diskuzi o [jednofázová a dvoufázová vytváření](../mfc/one-stage-and-two-stage-construction-of-objects.md), který poskytuje ukázkový kód.  
  
2.  [Vyberte objekt, do aktuálního kontextu zařízení](../mfc/selecting-a-graphic-object-into-a-device-context.md), před ukládání je původní objekt, který byl vybrán.  
  
3.  Po dokončení je aktuální objekt, vyberte je původní objekt zpět do kontextu zařízení k obnovení stavu.  
  
4.  Povolit přidělené rámce grafického objektu a automaticky odstraněn, když je byl ukončen oboru.  
  
> [!NOTE]
>  Pokud budete používat grafického objektu opakovaně, můžete ho po přidělovat a vyberte ho v kontextu zařízení pokaždé, když je to potřeba. Nezapomeňte odstranit takového objektu, když už nepotřebujete.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Jednofázová a dvoufázová konstrukce grafické objekty](../mfc/one-stage-and-two-stage-construction-of-objects.md)  
  
-   [Příklad v jedné a dvě fáze vytváření pera](../mfc/one-stage-and-two-stage-construction-of-objects.md)  
  
-   [Výběr grafického objektu v kontextu zařízení](../mfc/selecting-a-graphic-object-into-a-device-context.md)  
  
-   [Kontexty zařízení](../mfc/device-contexts.md)  
  
## <a name="see-also"></a>Viz také  
 [Objekty oken](../mfc/window-objects.md)

