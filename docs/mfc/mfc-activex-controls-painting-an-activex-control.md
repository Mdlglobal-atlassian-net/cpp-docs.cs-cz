---
title: 'Ovládací prvky MFC ActiveX: Vykreslování ovládacího prvku ActiveX | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], painting
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 25fff9c0-4dab-4704-aaae-8dfb1065dee3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f7026dd5ffaab04eb445ae68449127e65c772394
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354086"
---
# <a name="mfc-activex-controls-painting-an-activex-control"></a>MFC – ovládací prvky ActiveX: Vykreslování ovládacího prvku ActiveX
Tento článek popisuje proces vykreslování ovládacího prvku ActiveX a jak můžete změnit kód Malování optimalizovat proces. (Viz [optimalizace vykreslování ovládacího prvku](../mfc/optimizing-control-drawing.md) pro techniky o tom, jak optimalizovat kreslení pomocí nemá ovládací prvky jednotlivě obnovit dříve vybrané objekty GDI. Po vykreslení všechny ovládací prvky kontejneru automaticky obnovit původní objekty.)  
  
 Příklady v tomto článku jsou z ovládacího prvku vytvořené Průvodce ovládacím prvkem ActiveX knihovny MFC s výchozím nastavením. Další informace o vytvoření aplikace kostru ovládacího prvku pomocí Průvodce ovládacím prvkem ActiveX knihovny MFC, najdete v článku [Průvodce ovládacím prvkem ActiveX knihovny MFC](../mfc/reference/mfc-activex-control-wizard.md).  
  
 Jsou pokryta následující témata:  
  
-   [Celkový proces vykreslování ovládacího prvku a kód vytvořený pomocí Průvodce ovládacím prvkem ActiveX pro podporu Malování](#_core_the_painting_process_of_an_activex_control)  
  
-   [Jak optimalizovat proces Malování](#_core_optimizing_your_paint_code)  
  
-   [Postupy pro vaše ovládací prvek s použitím metasoubory Malování](#_core_painting_your_control_using_metafiles)  
  
##  <a name="_core_the_painting_process_of_an_activex_control"></a> Proces vykreslování ovládacího prvku ActiveX  
 Pokud ovládací prvky ActiveX se zpočátku zobrazují nebo jsou překreslen, se řídí podobně jako ostatní aplikace vyvinuté pomocí jednoho zásadní rozdíl MFC, proces vykreslování: ovládací prvky ActiveX může být aktivní nebo neaktivní stavu.  
  
 Aktivní ovládací prvek je reprezentována v kontejneru ovládacího prvku ActiveX ve podřízeného okna. Jako další windows je zodpovědná za samotný vykreslování při `WM_PAINT` je přijatá zpráva. Základní třída ovládacího prvku, [COleControl](../mfc/reference/colecontrol-class.md), zpracovává tuto zprávu v jeho `OnPaint` funkce. Tato výchozí implementace volá `OnDraw` funkce ovládacího prvku.  
  
 Jinak vykreslení ovládacího prvku neaktivní. Pokud je ovládací prvek neaktivní, je její okno neviditelná nebo neexistuje, proto ho nemůže přijmout zprávu Malování. Místo toho přímo volá kontejneru ovládacího prvku `OnDraw` funkce ovládacího prvku. Tím se liší od aktivní prvek Malování procesu v tom, že `OnPaint` volána členské funkce.  
  
 Popsané v předchozích odstavcích, jak je aktualizovat ovládacího prvku ActiveX závisí na stavu ovládacího prvku. Ale protože volá framework `OnDraw` – členská funkce v obou případech přidáte většinu kódu malování v této funkci člen.  
  
 `OnDraw` – Členská funkce zpracovává vykreslování ovládacího prvku. Po neaktivní ovládacího prvku kontejneru ovládacího prvku volá `OnDraw`, předáním kontextu zařízení kontejneru ovládacího prvku a souřadnice obdélníkovou oblast obsazena ovládacího prvku.  
  
 Rámeček předaná rozhraní k `OnDraw` – členská funkce obsahuje oblasti obsazena ovládacího prvku. Pokud je aktivní ovládací prvek, je levém horním rohu (0, 0) a kontext zařízení předaná pro podřízeného okna, který obsahuje ovládací prvek. Pokud ovládací prvek je neaktivní, není nezbytně představovat souřadnice levého horního (0, 0) a kontext zařízení předaná k řízení kontejneru obsahující ovládacího prvku.  
  
> [!NOTE]
>  Je důležité, vaše změny `OnDraw` nezávisí na horním levém bodu obdélníku se rovná (0, 0) a kreslení pouze uvnitř obdélníku předáno `OnDraw`. Kreslení nad rámec obdélníku oblasti může dojít k neočekávaným výsledkům.  
  
 Výchozí implementace poskytované Průvodce ovládacím prvkem ActiveX knihovny MFC v řídicím souboru implementace (. CPP), zobrazí níže vybarví rámeček štětcem bílé a vyplní se třemi tečkami aktuální barvou pozadí.  
  
 [!code-cpp[NVC_MFC_AxUI#1](../mfc/codesnippet/cpp/mfc-activex-controls-painting-an-activex-control_1.cpp)]  
  
> [!NOTE]
>  Při vykreslování ovládacího prvku, neprovádějte předpoklady o stavu zařízení kontext, který se předá jako *primárního řadiče domény* parametru `OnDraw` funkce. Příležitostně kontextu zařízení poskytl kontejneru aplikace a nebude nutně inicializovat do výchozího stavu. Konkrétně se explicitně vyberte per, štětce, barvy, písma a další prostředky, které závisí kreslení kódu.  
  
##  <a name="_core_optimizing_your_paint_code"></a> Optimalizace kódu Malování  
 Po ovládací prvek je úspěšně vykreslování sám sebe, dalším krokem je za účelem optimalizace `OnDraw` funkce.  
  
 Výchozí implementace vykreslování ovládacího prvku ActiveX vybarví oblasti celý ovládací prvek. Toto je dostačující pro jednoduché ovládací prvky, ale v mnoha případech překreslení ovládacího prvku by rychleji, pokud jenom překreslen části potřebné aktualizace, ale místo celý ovládací prvek.  
  
 `OnDraw` Funkce způsobem snadno optimalizace předáním `rcInvalid`, obdélníkovou oblast ovládací prvek, který potřebuje překreslování. Pomocí této oblasti, obvykle menší než oblasti celý ovládací prvek pro urychlení proces vykreslování.  
  
##  <a name="_core_painting_your_control_using_metafiles"></a> Vykreslování ovládacího prvku pomocí metasoubory  
 Ve většině případů `pdc` parametru `OnDraw` funkce odkazuje na obrazovce kontextu zařízení (DC). Při tisku bitových kopií ovládací prvek nebo během relace náhledu tisku, je řadič domény pro vykreslování však speciální typu s názvem "metasoubory řadiče domény". Na rozdíl od obrazovky řadiče domény, která okamžitě zpracovává požadavky do něj odeslané, metafile řadič domény ukládá žádosti o přehrání později. Některé aplikace typu kontejner se také rozhodnout k vykreslení ovládacího prvku obrázek s použitím metafile řadiče domény v režimu návrhu.  
  
 Metafile kreslení požadavků můžete provést pomocí kontejneru, přistoupit přes dvě funkce rozhraní: **IViewObject::Draw** (Tato funkce také lze volat pro jiný metafile kreslení) a **IDataObject::GetData**. Když metasoubory řadiče domény se předá jako jeden z parametrů, rozhraní MFC framework zavolá [COleControl::OnDrawMetafile](../mfc/reference/colecontrol-class.md#ondrawmetafile). Funkci ve třídě ovládacího prvku udělat žádné speciální zpracování přepište, protože člen virtuální funkce. Výchozí chování volání `COleControl::OnDraw`.  
  
 Pokud chcete mít jistotu, že lze rozlišovat ovládacího prvku v kontextech zařízení obrazovky a metafile, musíte použít pouze členské funkce, které jsou podporovány v obrazovky a metasoubory řadiče domény. Upozorňujeme, že souřadnicový systém nemusí měřená v pixelech.  
  
 Protože výchozí implementaci `OnDrawMetafile` volání ovládacího prvku `OnDraw` fungovat, použijte pouze členské funkce, která jsou vhodná pro metasoubory a kontextu obrazovky zařízení, pokud přepíšete `OnDrawMetafile`. Následující seznam obsahuje podmnožinu `CDC` členské funkce, které mohou být používány metasoubory a kontextu obrazovky zařízení. Další informace o těchto funkcích najdete v tématu třídy [CDC](../mfc/reference/cdc-class.md) v *odkaz knihovny MFC*.  
  
|Oblouk|BibBlt|Tětivy|  
|---------|------------|-----------|  
|**třemi tečkami**|**Řídicí**|`ExcludeClipRect`|  
|`ExtTextOut`|`FloodFill`|`IntersectClipRect`|  
|`LineTo`|`MoveTo`|`OffsetClipRgn`|  
|`OffsetViewportOrg`|`OffsetWindowOrg`|`PatBlt`|  
|`Pie`|**mnohoúhelníku**|`Polyline`|  
|`PolyPolygon`|`RealizePalette`|`RestoreDC`|  
|`RoundRect`|`SaveDC`|`ScaleViewportExt`|  
|`ScaleWindowExt`|`SelectClipRgn`|`SelectObject`|  
|`SelectPalette`|`SetBkColor`|`SetBkMode`|  
|`SetMapMode`|`SetMapperFlags`|`SetPixel`|  
|`SetPolyFillMode`|`SetROP2`|`SetStretchBltMode`|  
|`SetTextColor`|`SetTextJustification`|`SetViewportExt`|  
|`SetViewportOrg`|`SetWindowExt`|`SetWindowORg`|  
|`StretchBlt`|`TextOut`||  
  
 Kromě `CDC` členské funkce existuje několik dalších funkcí, které jsou kompatibilní v metafile řadiče domény. Mezi ně patří [CPalette::AnimatePalette](../mfc/reference/cpalette-class.md#animatepalette), [CFont::CreateFontIndirect](../mfc/reference/cfont-class.md#createfontindirect)a tři členské funkce `CBrush`: [CreateBrushIndirect](../mfc/reference/cbrush-class.md#createbrushindirect), [CreateDIBPatternBrush](../mfc/reference/cbrush-class.md#createdibpatternbrush), a [CreatePatternBrush](../mfc/reference/cbrush-class.md#createpatternbrush).  
  
 Funkce, které nejsou zaznamenaná v metasoubory jsou: [DrawFocusRect](../mfc/reference/cdc-class.md#drawfocusrect), [DrawIcon](../mfc/reference/cdc-class.md#drawicon), [DrawText](../mfc/reference/cdc-class.md#drawtext), [ExcludeUpdateRgn](../mfc/reference/cdc-class.md#excludeupdatergn), [FillRect](../mfc/reference/cdc-class.md#fillrect), [FrameRect](../mfc/reference/cdc-class.md#framerect), [GrayString](../mfc/reference/cdc-class.md#graystring), [InvertRect](../mfc/reference/cdc-class.md#invertrect), [ScrollDC](../mfc/reference/cdc-class.md#scrolldc)a [TabbedTextOut](../mfc/reference/cdc-class.md#tabbedtextout). Protože metafile řadič domény není ve skutečnosti související se zařízením, nemůžete použít SetDIBits, GetDIBits a CreateDIBitmap s metafile řadiče domény. SetDIBitsToDevice a StretchDIBits s metafile řadič domény můžete použít jako cíl. [CreateCompatibleDC](../mfc/reference/cdc-class.md#createcompatibledc), [CreateCompatibleBitmap](../mfc/reference/cbitmap-class.md#createcompatiblebitmap), a [CreateDiscardableBitmap](../mfc/reference/cbitmap-class.md#creatediscardablebitmap) nejsou smysluplný s metafile řadiče domény.  
  
 Jiné vzít v úvahu při použití metafile řadič domény je, že souřadnicový systém nemusí měřená v pixelech. Z tohoto důvodu všechny kreslení kódu, upraví se vešla do obdélníku předáno `OnDraw` v `rcBounds` parametr. Tím zabráníte náhodnému Malování mimo ovládací prvek, protože `rcBounds` představuje velikost okna ovládacího prvku.  
  
 Poté, co jste implementovali metafile vykreslování ovládacího prvku, použijte k testování metafile Test kontejneru. V tématu [testování vlastností a událostí pomocí Test kontejneru](../mfc/testing-properties-and-events-with-test-container.md) informace o tom, jak přístup kontejner testů.  
  
#### <a name="to-test-the-controls-metafile-using-test-container"></a>K testování metafile ovládacího prvku pomocí kontejner testů  
  
1.  Test kontejneru **upravit** nabídky, klikněte na tlačítko **vložit nový ovládací prvek**.  
  
2.  V **vložit nový ovládací prvek** pole, vyberte ovládací prvek a klikněte na tlačítko **OK**.  
  
     Ovládací prvek se zobrazí v testu kontejneru.  
  
3.  Na **řízení** nabídky, klikněte na tlačítko **kreslení Metafile**.  
  
     Samostatném okně se zobrazí, ve kterém se zobrazí metafile. Můžete změnit velikost tohoto okna zobrazíte škálování jak ovlivňuje metafile ovládacího prvku. Kdykoli můžete zavřít toto okno.  
  
## <a name="see-also"></a>Viz také  
 [MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)

