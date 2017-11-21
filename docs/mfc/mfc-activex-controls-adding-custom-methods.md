---
title: "Ovládací prvky MFC ActiveX: Přidání vlastních metod | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
- PtInCircle custom method [MFC]
ms.assetid: 8f8dc344-44a0-4021-8db5-4cdd3d700e18
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ead8411d22539218c18d21b8af7d020cc267879f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mfc-activex-controls-adding-custom-methods"></a>MFC – ovládací prvky ActiveX: Přidání vlastních metod
Vlastní metody se liší od uložených metod v tom, že již nejsou implementované pomocí `COleControl`. Je třeba zadat implementace pro jednotlivé vlastní metody, které přidáte do vašeho ovládacího prvku.  
  
 Uživatelé ovládacího prvku ActiveX můžete kdykoli provádět akce specifické pro ovládací prvek volání vlastní metody. Položka mapy odesílání pro vlastní metody je ve formátu `DISP_FUNCTION`.  
  
##  <a name="_core_adding_a_custom_method_with_classwizard"></a>Přidání vlastní metody pomocí Průvodce přidáním metody  
 Následující postup předvádí, přidávání ptincircle – vlastní metoda do ovládacího prvku ActiveX kostru kódu. Ptincircle – Určuje, zda souřadnice předán do ovládacího prvku uvnitř nebo vně kruhu. Stejný postup lze také přidat další vlastní metody. Nahraďte název vlastní metody a jeho parametry pro název metody ptincircle – a parametry.  
  
> [!NOTE]
>  Tento příklad používá `InCircle` funkce z článku události. Další informace o této funkci najdete v článku [MFC – ovládací prvky ActiveX: Přidání vlastních událostí do ovládacího prvku ActiveX](../mfc/mfc-activex-controls-adding-custom-events.md).  
  
#### <a name="to-add-the-ptincircle-custom-method-using-the-add-method-wizard"></a>Chcete-li přidat ptincircle – vlastní metoda pomocí Průvodce přidáním metody  
  
1.  Načtení projektu ovládacího prvku.  
  
2.  V zobrazení tříd rozbalte uzel knihovny ovládacího prvku.  
  
3.  Klikněte pravým tlačítkem na uzel rozhraní pro vlastní ovládací prvek (druhého uzlu uzlu knihovny) a místní nabídce.  
  
4.  V místní nabídce klikněte na **přidat** a pak klikněte na **přidat metodu**.  
  
     Otevře se Průvodce přidáním metody.  
  
5.  V **název metody** zadejte `PtInCircle`.  
  
6.  V **interní název** pole, zadejte název metody – vnitřní funkce nebo použijte výchozí hodnotu (v tomto případě `PtInCircle`).  
  
7.  V **návratového typu** pole, klikněte na tlačítko **VARIANT_BOOL** pro návratový typ metody.  
  
8.  Pomocí **typ parametru** a **název parametru** ovládacích prvků, přidejte parametr s názvem `xCoord` (typ **OLE_XPOS_PIXELS**).  
  
9. Pomocí **typ parametru** a **název parametru** ovládacích prvků, přidejte parametr s názvem `yCoord` (typ **OLE_YPOS_PIXELS**).  
  
10. Klikněte na tlačítko **Dokončit**.  
  
##  <a name="_core_classwizard_changes_for_custom_methods"></a>Přidat metoda průvodce změní pro vlastní metody  
 Když přidáte vlastní metodu, Průvodce přidáním metody zajistí některé změny do ovládacího prvku záhlaví – třída (. H) a implementace (. Soubory CPP). Následující řádek je přidán do deklaraci mapy odesílání v hlavičce třídy ovládacího prvku (. H) soubor:  
  
 [!code-cpp[NVC_MFC_AxUI#18](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_1.h)]  
  
 Tento kód deklaruje obslužnou rutinu odesílání metoda volána `PtInCircle`. Tuto funkci jde volat pomocí externí název ptincircle – ovládací prvek uživatel.  
  
 Následující řádek je přidán do ovládacího prvku. IDL soubor:  
  
 [!code-cpp[NVC_MFC_AxUI#19](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_2.idl)]  
  
 Tento řádek přiřadí ptincircle – metoda specifické číslo ID, metoda pozici v seznamu metod a vlastností, Průvodce přidáním metody. Protože došlo k přidání vlastní metody Průvodce přidáním metody, položka pro něj byl automaticky přidat do projektu. IDL soubor.  
  
 Kromě toho na následujícím řádku umístěný v implementaci (. Expediční mapy ovládacího prvku se přidá soubor CPP) třídy ovládacího prvku:  
  
 [!code-cpp[NVC_MFC_AxUI#20](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_3.cpp)]  
  
 `DISP_FUNCTION` Makro mapuje metodu ptincircle – funkce obslužná rutina ovládacího prvku, `PtInCircle`, deklaruje návratový typ, který má být **VARIANT_BOOL**a deklaruje dva parametry typu **vts_xpos_pixels –** a **VTS_YPOSPIXELS** mají být předány `PtInCircle`.  
  
 Nakonec Průvodce přidáním metody přidá funkce se zakázaným inzerováním `CSampleCtrl::PtInCircle` k dolnímu okraji implementaci ovládacího prvku (. Soubor CPP). Pro `PtInCircle` fungují jako už jsme si říkali, je nejprve nutné upravit takto:  
  
 [!code-cpp[NVC_MFC_AxUI#21](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_4.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky MFC ActiveX](../mfc/mfc-activex-controls.md)   
 [Zobrazení tříd a ikony v prohlížeči objektů](/visualstudio/ide/class-view-and-object-browser-icons)

