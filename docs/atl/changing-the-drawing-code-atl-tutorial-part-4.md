---
title: "Změna kódu kreslení (ATL – tutoriál, část 4) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords: _ATL_MIN_CRT macro
ms.assetid: 08ff14e8-aa49-4139-a110-5d071939cf1e
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ccbf7dab7d39a80efa2b0b0b88b615c55cd9e56d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="changing-the-drawing-code-atl-tutorial-part-4"></a>Změna kódu kreslení (ATL – tutoriál, část 4)
Ve výchozím nastavení, zobrazí kód vykreslování ovládacího prvku čtverce a text **PolyCtl**. V tomto kroku se změní kód zobrazit něco zajímavějšího. Se podílejí následující úlohy:  
  
-   Úprava soubor hlaviček  
  
-   Úpravy `OnDraw` – funkce  
  
-   Přidání metodu pro výpočet bodů mnohoúhelníku  
  
-   Inicializace barvu výplně  
  
## <a name="modifying-the-header-file"></a>Úprava soubor hlaviček  
 Začněte tím, že přidání podpory pro matematické funkce `sin` a `cos`, který se používá vypočítat bodů mnohoúhelníku a vytvořením pole k uložení umisťuje.  
  
#### <a name="to-modify-the-header-file"></a>Chcete-li upravit soubor hlaviček  
  
1.  Přidejte řádek `#include <math.h>` do horní části PolyCtl.h. Horní části souboru by měl vypadat takto:  
  
     [!code-cpp[NVC_ATL_Windowing#47](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_1.cpp)]  
  
2.  Jakmile jsou vypočítávány bodů mnohoúhelníku, se uloží v poli typu `POINT`, proto přidejte pole po definování `m_nSides` v PolyCtl.h:  
  
     [!code-cpp[NVC_ATL_Windowing#48](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_2.h)]  
  
## <a name="modifying-the-ondraw-method"></a>Úprava OnDraw – metoda  
 Teď by měl změnit `OnDraw` metoda v PolyCtl.h. Přidáte kód vytvoří novou pera a štětce, ke které má vaše mnohoúhelníku kreslení a potom zavolá `Ellipse` a `Polygon` funkce rozhraní API Win32 k provedení skutečné kreslení.  
  
#### <a name="to-modify-the-ondraw-function"></a>Chcete-li upravit OnDraw – funkce  
  
1.  Nahradit existující `OnDraw` metoda v PolyCtl.h následujícím kódem:  
  
     [!code-cpp[NVC_ATL_Windowing#49](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_3.cpp)]  
  
## <a name="adding-a-method-to-calculate-the-polygon-points"></a>Přidání metodu pro výpočet bodů mnohoúhelníku  
 Přidejte metodu, s názvem `CalcPoints`, která vypočítá souřadnice body, které tvoří hraniční mnohoúhelníku. Tyto výpočty budou založeny na Rect – proměnné, která je předána do funkce.  
  
#### <a name="to-add-the-calcpoints-method"></a>Chcete-li přidat metodu CalcPoints  
  
1.  Přidejte deklaraci `CalcPoints` k `IPolyCtl` veřejné části `CPolyCtl` třídy v PolyCtl.h:  
  
     [!code-cpp[NVC_ATL_Windowing#50](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_4.h)]  
  
     Poslední část veřejné části `CPolyCtl` třída bude vypadat například takto:  
  
     [!code-cpp[NVC_ATL_Windowing#51](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_5.h)]  
  
2.  Přidat tato implementace `CalcPoints` funkce na konec PolyCtl.cpp:  
  
     [!code-cpp[NVC_ATL_Windowing#52](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_6.cpp)]  
  
## <a name="initializing-the-fill-color"></a>Inicializace barvu výplně  
 Inicializace `m_clrFillColor` barvou výchozí.  
  
#### <a name="to-initialize-the-fill-color"></a>K chybě při inicializaci barvu výplně  
  
1.  Použití zelená jako výchozí barvu přidáním tohoto řádku `CPolyCtl` konstruktor v PolyCtl.h:  
  
     [!code-cpp[NVC_ATL_Windowing#53](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_7.h)]  
  
 Konstruktor je nyní vypadat třeba takto:  
  
 [!code-cpp[NVC_ATL_Windowing#54](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_8.h)]  
  
## <a name="building-and-testing-the-control"></a>Vytváření a testování ovládacího prvku  
 Opětovné sestavení ovládacího prvku. Zajistěte, aby PolyCtl.htm soubor se zavřel, pokud je stále otevřen a pak klikněte na **sestavení mnohoúhelníku** na **sestavení** nabídky. Může zobrazit ještě jednou ze stránky PolyCtl.htm ovládacího prvku, ale tentokrát použijte kontejner testů ovládacích prvků ActiveX.  
  
#### <a name="to-use-the-activex-control-test-container"></a>Chcete-li použít kontejner testů ovládacích prvků ActiveX  
  
1.  Sestavte a spusťte kontejner testů ovládacích prvků ActiveX. Další informace najdete v tématu [TSTCON ukázka: kontejner testů ovládacích prvků ActiveX](../visual-cpp-samples.md).  
  
2.  V testu kontejneru na **upravit** nabídky, klikněte na tlačítko **vložit nový ovládací prvek**.  
  
3.  Najít ovládací prvek, která bude volána `PolyCtl Class`a klikněte na tlačítko **OK**. Zobrazí se zeleným trojúhelníkem v rámci kruh.  
  
 Zkuste změnit počet stran za dalším postupem. Chcete-li upravit vlastnosti duální rozhraní z v rámci – kontejner testů, použijte **vyvolání metody**.  
  
#### <a name="to-modify-a-controls-property-from-within-the-test-container"></a>K úpravě vlastností ovládacího prvku z v rámci kontejner testů  
  
1.  V testu kontejneru, klikněte na tlačítko **vyvolání metody** na **řízení** nabídky.  
  
     **Vyvolání metody** se zobrazí dialogové okno.  
  
2.  Vyberte **propput –** verzi **stranách** vlastnost z **název metody** rozevíracího seznamu.  
  
3.  Typ `5` v **hodnota parametru** pole, klikněte na tlačítko **nastavit hodnotu**a klikněte na tlačítko **Invoke**.  
  
 Všimněte si, že ovládací prvek se nemění. I když jste změnili počet stran, interně nastavením `m_nSides` proměnné, to nezpůsobila chcete překreslit ovládacího prvku. Pokud přepnete na jinou aplikaci a pak přejděte zpátky do testovacího kontejneru, zjistíte, že ovládací prvek má překreslen a má správný počet stran.  
  
 Problém vyřešíte tak, že přidáte volání `FireViewChange` funkce, které jsou definované v `IViewObjectExImpl`, jakmile nastavíte počet stran. Pokud ovládací prvek běží v samostatném okně `FireViewChange` zavolá `InvalidateRect` metoda přímo. Pokud ovládací prvek běží bez oken, `InvalidateRect` metoda bude volána při rozhraní lokality kontejneru. Vynutí se ovládací prvek chcete překreslit sám sebe.  
  
#### <a name="to-add-a-call-to-fireviewchange"></a>Chcete-li přidat volání FireViewChange  
  
1.  Aktualizovat PolyCtl.cpp tak, že přidáte volání `FireViewChange` k `put_Sides` metoda. Po dokončení, `put_Sides` metoda by měla vypadat takto:  
  
     [!code-cpp[NVC_ATL_Windowing#55](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_9.cpp)]  
  
 Po přidání `FireViewChange`, znovu sestavit a zkuste to znovu za kontejner testů ovládacích prvků ActiveX ovládacího prvku. Tuto chvíli, kdy změnit počet strany a klikněte na tlačítko `Invoke`, měli byste vidět ovládacího prvku změnit okamžitě.  
  
 V dalším kroku přidáte událost.  
  
 [Zpátky ke kroku 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md) &#124; [Na krok 5](../atl/adding-an-event-atl-tutorial-part-5.md)  
  
## <a name="see-also"></a>Viz také  
 [Kurz](../atl/active-template-library-atl-tutorial.md)   
 [Testování vlastností a událostí pomocí testovacího kontejneru](../mfc/testing-properties-and-events-with-test-container.md)

