---
title: Implementace panelu nástrojů MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- toolbars [MFC], creating
- buttons [MFC], MFC toolbars
- toolbars [MFC], docking
- CToolBar class [MFC], creating toolbars
- MFC toolbars
- floating toolbars [MFC]
- toolbars [MFC], floating
- docking toolbars [MFC]
- bitmaps [MFC], toolbar
- toolbar controls [MFC]
- CToolBarCtrl class [MFC], implementing toolbars
- tool tips [MFC], enabling
- toolbars [MFC]
- toolbars [MFC], implementing MFC toolbars
ms.assetid: af3319ad-c430-4f90-8361-e6a2c06fd084
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b0fd3a41d7574d627ebd374af170ce47801cd351
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-toolbar-implementation"></a>Implementace panelu nástrojů v prostředí MFC
Panel nástrojů je [ovládacích pruhů](../mfc/control-bars.md) obsahující obrázky rastrový obrázek ovládacích prvků. Tyto Image můžete chovat jako tlačítek, zaškrtněte políčka nebo přepínače. Poskytuje třídy MFC [ctoolbar –](../mfc/reference/ctoolbar-class.md) ke správě panely nástrojů.  
  
 Pokud ho povolíte, můžete uživatelům panely nástrojů rozhraní MFC ukotvení je hrany okno nebo "float" je kdekoli v okně aplikace. MFC nepodporuje upravitelných panelů nástrojů stejně jako ve vývojovém prostředí.  
  
 MFC podporuje také popisy: malé automaticky otevíraná okna, které popisují tlačítka panelu nástrojů účel při umístit ukazatel myši nad tlačítko. Ve výchozím nastavení při stisknutí tlačítka panelu nástrojů, řetězec stav se zobrazí ve stavovém řádku (pokud existuje). "Překrýt podle" stavovém řádku aktualizace zobrazí řetězec stav, když myši je umístěn nad tlačítko bez stisknutím ji můžete aktivovat.  
  
> [!NOTE]
>  Od verze knihovny MFC verze 4.0 panely nástrojů a tipů nástrojů se implementují pomocí systému Windows 95 a novější funkce místo předchozí implementace, které jsou specifické pro MFC.  
  
 Z důvodu zpětné kompatibility MFC uchovává starší implementace panelu nástrojů v třídě **COldToolBar**. Popisují dokumentaci pro starší verze knihovny MFC **COldToolBar** pod `CToolBar`.  
  
 Vytvoření první panelu nástrojů v programu výběrem možnosti panelu nástrojů v Průvodci aplikací. Můžete také vytvořit další panely nástrojů.  
  
 V tomto článku byly zavedeny následující text:  
  
-   [Tlačítka panelu nástrojů](#_core_toolbar_buttons)  
  
-   [Ukotvitelné a plovoucí panely nástrojů](#_core_docking_and_floating_toolbars)  
  
-   [Panely nástrojů a tipů nástrojů](#_core_toolbars_and_tool_tips)  
  
-   [Ctoolbar – a CToolBarCtrl třídy](#_core_the_ctoolbar_and_ctoolbarctrl_classes)  
  
-   [Rastrového obrázku panelu nástrojů](#_core_the_toolbar_bitmap)  
  
##  <a name="_core_toolbar_buttons"></a> Tlačítka panelu nástrojů  
 Tlačítka na panelu nástrojů, jsou obdobou položky v nabídce. Oba typy objektů uživatelského rozhraní Generovat příkazy, které váš program zpracovává tím, že poskytuje funkce obslužných rutin. Často tlačítka panelu nástrojů duplicitní funkce příkazy nabídky, poskytuje alternativní uživatelské rozhraní ke stejné funkce. Takové duplikace uspořádána jednoduše tím, že položka nabídky a tlačítko stejným ID.  
  
 Můžete nastavit tlačítek na panelu nástrojů zobrazí a chovat jako tlačítek, zaškrtněte políčka nebo přepínače. Další informace najdete v tématu třídy [ctoolbar –](../mfc/reference/ctoolbar-class.md).  
  
##  <a name="_core_docking_and_floating_toolbars"></a> Ukotvitelné a plovoucí panely nástrojů  
 Panelu nástrojů MFC můžete:  
  
-   Zůstanou stojící na jedné straně jeho nadřazeného okna.  
  
-   Přetáhnout a "ukotven" nebo připojen uživatel na žádné straně nebo stranách nadřazené okno, které zadáte.  
  
-   "Obtékané" nebo odpojit z okna rámce v samostatném okně zkrácená rámečku, může uživatel přesunout ho na všechny vhodné poloze.  
  
-   Změnit velikost při číslo s plovoucí čárkou.  
  
 Další informace najdete v článku [stabilní umístění a plovoucí panely nástrojů](../mfc/docking-and-floating-toolbars.md).  
  
##  <a name="_core_toolbars_and_tool_tips"></a> Panely nástrojů a tipů nástrojů  
 Panely nástrojů rozhraní MFC lze také zobrazit "nástroj tipy" – windows jen nepatrnou místní obsahující krátký textový popis tlačítka panelu nástrojů účel. Jako uživatel přesune myši nad tlačítka panelu nástrojů, panel nástrojů tip objeví nabídka nápovědu. Další informace najdete v článku [tlačítek na panelu nástrojů nástroje](../mfc/toolbar-tool-tips.md).  
  
##  <a name="_core_the_ctoolbar_and_ctoolbarctrl_classes"></a> Ctoolbar – a třídy CToolBarCtrl  
 Spravovat panelů nástrojů vaší aplikace pomocí třídy [ctoolbar –](../mfc/reference/ctoolbar-class.md). Od verze knihovny MFC verze 4.0 `CToolBar` má byla reimplemented používat běžné prvku panel nástrojů dostupných v systému Windows 95 nebo novější a Windows NT 3.51 nebo novější verze.  
  
 Tato opětovná implementace výsledkem menší MFC kód pro panely nástrojů, protože MFC umožňuje použití podporu operačního systému. Opětovná implementace také zlepšuje funkce. Můžete použít `CToolBar` členské funkce k manipulaci s panely nástrojů, nebo můžete získat odkaz na základní [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) objektu a volat jeho členské funkce pro přizpůsobení panelu nástrojů a další funkce.  
  
> [!TIP]
>  Pokud budete mít výraznou investovali do starší implementace MFC `CToolBar`, že podpora je stále k dispozici. Najdete v článku [pomocí vaše starých panelů nástrojů](../mfc/using-your-old-toolbars.md).  
  
 Také naleznete v ukázce MFC Obecné [DOCKTOOL](../visual-cpp-samples.md).  
  
##  <a name="_core_the_toolbar_bitmap"></a> Rastrového obrázku panelu nástrojů  
 Jednou sestavený, `CToolBar` objekt vytvoří bitovou kopii nástrojů načtením jeden rastrový obrázek, který obsahuje jeden obrázek pro každé tlačítko. Vytvoří Průvodce standardním panelu nástrojů rastrového obrázku, kterou si můžete přizpůsobit s Visual C++ [editor panelu nástrojů](../windows/toolbar-editor.md).  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Principy panelů nástrojů](../mfc/toolbar-fundamentals.md)  
  
-   [Ukotvitelné a plovoucí panely nástrojů](../mfc/docking-and-floating-toolbars.md)  
  
-   [Popisy tlačítek panelu nástrojů](../mfc/toolbar-tool-tips.md)  
  
-   [Práce s ovládacím prvkem panel nástrojů](../mfc/working-with-the-toolbar-control.md)  
  
-   [Použití starých panelů nástrojů](../mfc/using-your-old-toolbars.md)  
  
-   [Ctoolbar –](../mfc/reference/ctoolbar-class.md) a [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) třídy  
  
## <a name="see-also"></a>Viz také  
 [Panely nástrojů](../mfc/toolbars.md)   
 [Editor panelu nástrojů](../windows/toolbar-editor.md)

