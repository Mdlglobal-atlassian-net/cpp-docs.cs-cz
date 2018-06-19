---
title: Přizpůsobení vzhledu ovládacího prvku panel nástrojů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TBSTYLE_
dev_langs:
- C++
helpviewer_keywords:
- flat toolbars
- CToolBar class [MFC], styles
- transparent toolbars
- TBSTYLE_ styles [MFC]
- CToolBarCtrl class [MFC], object styles
- toolbar controls [MFC], style
ms.assetid: fd0a73db-7ad1-4fe4-889b-02c3980f49e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 96ec459e1c956c805991f2e37d22b8260f0ffdf2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343691"
---
# <a name="customizing-the-appearance-of-a-toolbar-control"></a>Přizpůsobení vzhledu ovládacího prvku panel nástrojů
Třída `CToolBarCtrl` poskytuje mnoho stylů, které ovlivňují vzhled (a v některých případech chování) objektu panelu nástrojů. Změnit objekt nástrojů nastavením `dwCtrlStyle` parametr `CToolBarCtrl::Create` (nebo `CToolBar::CreateEx`) – členská funkce, při prvním vytváření ovládací prvek panelu nástrojů.  
  
 Následující styly ovlivňují "3D" aspektů tlačítka panelu nástrojů a umístění text tlačítka:  
  
-   **TBSTYLE_FLAT** vytvoří ploché kde jsou transparentní panelu nástrojů a tlačítka panelu nástrojů. Text tlačítka se zobrazí pod tlačítko bitmapy. Když tento styl se používá, se automaticky zvýrazní tlačítko pod kurzor.  
  
-   **TBSTYLE_TRANSPARENT** vytvoří transparentní panelu nástrojů. Na panelu nástrojů, transparentní panelu nástrojů je transparentní, ale nejsou tlačítka. Text tlačítka se zobrazí pod tlačítko bitmapy.  
  
-   **TBSTYLE_LIST** místech tlačítko text doprava tlačítko bitmapy.  
  
> [!NOTE]
>  Aby se zabránilo překreslit problémy, **TBSTYLE_FLAT** a **TBSTYLE_TRANSPARENT** styly musí být nastavená před objekt nástrojů je zobrazen.  
  
 Následující styly určují, pokud je panelu nástrojů umožňuje uživatelům změnit umístění jednotlivých tlačítek panelu nástrojů objektu pomocí přetahování a vyřadit:  
  
-   **TBSTYLE_ALTDRAG** umožňuje uživatelům změnit umístění tlačítka panelu nástrojů přetažením podržíte klávesu ALT. Pokud není zadán tento styl, musí uživatel podržte stisknutou klávesu SHIFT při přetahování tlačítko.  
  
    > [!NOTE]
    >  `CCS_ADJUSTABLE` Pro povolení tlačítka panelu nástrojů přetáhnout je nutné zadat stylu.  
  
-   **TBSTYLE_REGISTERDROP** generuje **TBN_GETOBJECT** oznámení zprávy o vyřadit cílové objekty, když ukazatel myši prochází přes tlačítka panelu nástrojů.  
  
 Zbývající styly ovlivní visual a nevizuální aspektů objekt nástrojů:  
  
-   `TBSTYLE_WRAPABLE` Vytvoří panel nástrojů, který může mít více řádků tlačítek. Tlačítka panelu nástrojů může "obtékat" na další řádek při panelu nástrojů příliš úzké zahrnout všechny tlačítka na stejném řádku. Zabalení proběhne oddělení a nongroup hranice.  
  
-   **TBSTYLE_CUSTOMERASE** generuje **NM_CUSTOMDRAW** zprávy oznámení, pokud ho zpracuje `WM_ERASEBKGND` zprávy.  
  
-   `TBSTYLE_TOOLTIPS` Vytvoří prvkem popis tlačítka, které aplikace můžete použít k zobrazení popisný text pro tlačítka na panelu nástrojů.  
  
 Úplný seznam všech nástrojů styly a styly rozšířené, najdete v části [Toolbar – ovládací prvek a styly tlačítek](http://msdn.microsoft.com/library/windows/desktop/bb760439) a [rozšířené styly nástrojů](http://msdn.microsoft.com/library/windows/desktop/bb760430) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

