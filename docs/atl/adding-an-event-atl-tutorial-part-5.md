---
title: Přidání události (ATL – tutoriál, část 5) | Microsoft Docs
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 2de12022-3148-4ce3-8606-8a9d4274f0e9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a118cf29546ac8dae2e882d5658b07e3b5e085f6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361262"
---
# <a name="adding-an-event-atl-tutorial-part-5"></a>Přidání události (ATL – tutoriál, část 5)
V tomto kroku přidáte `ClickIn` a `ClickOut` události do vašeho ATL ovládacího prvku. Bude platit `ClickIn` událost, pokud uživatel klikne v mnohoúhelníku a ještě efektivněji `ClickOut` Pokud uživatel klikne na mimo. Úlohy postup přidání události jsou následující:  
  
-   Přidávání `ClickIn` a `ClickOut` metody  
  
-   Generování knihovny typů  
  
-   Implementace rozhraní bodu připojení  
  
## <a name="adding-the-clickin-and-clickout-methods"></a>Přidání clickin – a ClickOut metody  
 Vytvoření ovládacího prvku knihovny ATL v kroku 2 jste vybrali **spojovací body** zaškrtávací políčko. To vytvořili `_IPolyCtlEvents` rozhraní v souboru Polygon.idl. Všimněte si, že název rozhraní začíná podtržítkem. Jedná se o konvenci k označení, že rozhraní je vnitřní rozhraní. Proto programy, které vám umožní procházet objekty modelu COM můžete vybrat není zobrazení rozhraní pro uživatele. Všimněte si, že vyberete **spojovací body** přidejte následující řádek v souboru Polygon.idl k označení, že `_IPolyCtlEvents` je výchozí zdroj rozhraní:  
  
 `[default, source] dispinterface _IPolyCtlEvents;`  
  
 Zdrojový atribut označuje, že ovládací prvek je zdroj oznámení, takže ho bude volat toto rozhraní v kontejneru.  
  
 Nyní přidejte `ClickIn` a `ClickOut` metody `_IPolyCtlEvents` rozhraní.  
  
#### <a name="to-add-the-clickin-and-clickout-methods"></a>Chcete-li přidat clickin – a ClickOut metody  
  
1.  V zobrazení tříd rozbalte položku mnohoúhelníku a PolygonLib pro zobrazení _IPolyCtlEvents.  
  
2.  Klikněte pravým tlačítkem na _IPolyCtlEvents. V místní nabídce klikněte na tlačítko **přidat**a potom klikněte na **přidat metodu**.  
  
3.  Vyberte **návratový typ** z `void`.  
  
4.  Zadejte `ClickIn` v **název metody** pole.  
  
5.  V části **atributy parametru**, vyberte **v** pole.  
  
6.  Vyberte **typ parametru** z `LONG`.  
  
7.  Typ `x` jako **název parametru**a klikněte na tlačítko **přidat**.  
  
8.  Opakujte kroky 5 až 7, tentokrát pro **název parametru** z `y`.  
  
9. Klikněte na tlačítko **Další**.  
  
10. Typ `method ClickIn` jako **helpstring**.  
  
11. Klikněte na tlačítko **Dokončit**.  
  
12. Opakujte tento postup můžete definovat `ClickOut` metoda se stejným `LONG` parametry `x` a `y`, stejné **atributy parametru** a stejné `void` návratovým typem.  
  
 Zkontrolujte soubor Polygon.idl a ověřte, že kód byla přidána do `_IPolyCtlEvents` dispinterface.  
  
 `_IPolyCtlEvents` Dispinterface v souboru Polygon.idl by teď měl vypadat takto:  
  
 [!code-cpp[NVC_ATL_Windowing#56](../atl/codesnippet/cpp/adding-an-event-atl-tutorial-part-5_1.idl)]  
  
 `ClickIn` a `ClickOut` metody proveďte x a y souřadnice bodu klepnutí jako parametry.  
  
## <a name="generating-the-type-library"></a>Generování knihovny typů  
 V tomto okamžiku vygenerujte knihovny typů, protože průvodce bodu připojení ji použít k získání informací, které potřebuje k vytvoření rozhraní bodu připojení a rozhraní kontejneru bodu připojení pro ovládací prvek.  
  
#### <a name="to-generate-the-type-library"></a>Vytvoření knihovny typů  
  
1.  Znovu sestavte projekt.  
  
     -nebo-  
  
2.  Polygon.idl soubor v Průzkumníku řešení klikněte pravým tlačítkem myši a klikněte na tlačítko **zkompilovat** v místní nabídce.  
  
 Tím se vytvoří soubor Polygon.tlb, který je vaše knihovna typu. Soubor Polygon.tlb není viditelné v Průzkumníku řešení, protože je binární soubor a nelze ho zobrazit nebo upravit přímo.  
  
## <a name="implementing-the-connection-point-interfaces"></a>Implementace rozhraní bodu připojení  
 Implementujte rozhraní bodu připojení a rozhraní kontejneru bodu připojení pro ovládací prvek. V modelu COM události se implementují prostřednictvím mechanismus spojovací body. Přijímat události z objektu COM, vytvoří kontejner poradní připojení ke spojovacímu bodu, který implementuje objekt COM. Vzhledem k tomu, že objekt COM může mít více bodů připojení, objekt COM také implementuje rozhraní kontejneru bod připojení. Prostřednictvím tohoto rozhraní můžete určit kontejneru, které body připojení jsou podporovány.  
  
 Rozhraní, které implementuje bod připojení je volána `IConnectionPoint`, a rozhraní, které implementuje kontejner bod připojení se nazývá `IConnectionPointContainer`.  
  
 Při provádění `IConnectionPoint`, použijete Průvodce implementace bodu připojení. Tento průvodce vytvoří `IConnectionPoint` rozhraní čtení vaší knihovny typů a implementace funkce pro každou jednotlivou událost, která může být aktivována.  
  
#### <a name="to-use-the-implement-connection-point-wizard"></a>Chcete-li použít Průvodce implementací bodu připojení  
  
1.  V zobrazení tříd, klikněte pravým tlačítkem na třídu pro implementaci ovládacího prvku `CPolyCtl`.  
  
2.  V místní nabídce klikněte na tlačítko **přidat**a potom klikněte na **přidat bod připojení**.  
  
3.  Vyberte `_IPolyCtlEvents` z **zdroje rozhraní** seznamu a dvojím kliknutím ho přidat do **implementovat body připojení** sloupce. Klikněte na tlačítko **Dokončit**. Třídu proxy bodu připojení se budou generovat, v takovém případě `CProxy_IPolyCtlEvents`.  
  
 Pokud se podíváte na _IPolyCtlEvents_CP.h vygenerovaný soubor v Průzkumníku řešení, uvidíte, že má třída nazvaná `CProxy_IPolyCtlEvents` která je odvozena od `IConnectionPointImpl`. _IPolyCtlEvents_CP.h také definuje tyto dvě metody `Fire_ClickIn` a `Fire_ClickOut`, která trvat dva parametry souřadnic. Tyto metody volat, když chcete aktivovat událost na základě vlastního ovládacího prvku.  
  
 Průvodce také přidat `CProxy_PolyEvents` a `IConnectionPointContainerImpl` do ovládacího prvku více dědičnosti seznamu. Průvodce také vystaveny `IConnectionPointContainer` můžete přidáním příslušné položky do modelu COM mapy.  
  
 Budete hotovi, implementace kódu, které podporují události. Nyní přidáte kód, který fire události v příslušné chvíli. Pamatujte si, že se chystáte provést, `ClickIn` nebo `ClickOut` událostí po kliknutí levým tlačítkem myši v ovládacím prvku. Chcete-li zjistit, když uživatel klikne na tlačítko, přidejte obslužnou rutinu pro `WM_LBUTTONDOWN` zprávy.  
  
#### <a name="to-add-a-handler-for-the-wmlbuttondown-message"></a>Chcete-li přidat obslužnou rutinu pro zprávu WM_LBUTTONDOWN  
  
1.  V zobrazení tříd, klikněte pravým tlačítkem na třídu CPolyCtl a klikněte na **vlastnosti** v místní nabídce.  
  
2.  V **vlastnosti** okně klikněte na tlačítko **zprávy** ikonu a pak klikněte na tlačítko `WM_LBUTTONDOWN` ze seznamu na levé straně.  
  
3.  V rozevíracím seznamu klikněte na tlačítko  **\<Přidat > onlbuttondown –**. `OnLButtonDown` Obslužná rutina deklarace budou přidány do PolyCtl.h a implementaci obslužné rutiny se zařadí do PolyCtl.cpp.  
  
 V dalším kroku změňte obslužná rutina.  
  
#### <a name="to-modify-the-onlbuttondown-method"></a>Chcete-li upravit onlbuttondown – metoda  
  
1.  Změnit kód, který se skládá z `OnLButtonDown` metoda v PolyCtl.cpp (odstranění všech kódu umístit průvodcem) tak, aby vypadá takto:  
  
     [!code-cpp[NVC_ATL_Windowing#57](../atl/codesnippet/cpp/adding-an-event-atl-tutorial-part-5_2.cpp)]  
  
 Tento kód díky použití bodů počítá v `OnDraw` funkce vytvořit oblasti, která zjistí uživatele myší s volání `PtInRegion`.  
  
 `uMsg` Parametr je ID zprávy systému Windows ke zpracování. To umožňuje mít jednu funkci, která zpracovává řadu zprávy. `wParam` a `lParam` parametry jsou standardní hodnoty pro zprávu ke zpracování. Parametr bHandled umožňuje určit, zda funkce zpracovává zprávy, nebo ne. Ve výchozím nastavení, je hodnota nastavena `TRUE` označíte, že funkce zpracovat zprávu, ale můžete ho nastavit `FALSE`. To způsobí, že ATL – Chcete-li pokračovat, hledá jinou funkci obslužné rutiny zpráv k odeslání zprávy do.  
  
## <a name="building-and-testing-the-control"></a>Vytváření a testování ovládacího prvku  
 Teď vyzkoušejte události. Sestavení ovládacího prvku a znovu spusťte kontejner testů ovládacích prvků ActiveX. Tentokrát zobrazte okno protokolu událostí. Do okna výstupu směrovat události, klikněte na tlačítko **protokolování** z **možnosti** nabídku a vyberte **protokolu do okna výstupu**. Vložení ovládacího prvku a zkuste klepnout v okně. Všimněte si, že `ClickIn` je aktivována, pokud kliknete v rámci vyplněný mnohoúhelníku a `ClickOut` je aktivována, když kliknete mimo.  
  
 V dalším kroku přidáte stránky vlastností.  
  
 [Zpátky ke kroku 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md) &#124; [na krok 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)  
  
## <a name="see-also"></a>Viz také  
 [Kurz](../atl/active-template-library-atl-tutorial.md)

