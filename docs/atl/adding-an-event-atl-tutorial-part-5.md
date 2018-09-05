---
title: Přidání události (ATL – tutoriál, část 5) | Dokumentace Microsoftu
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
ms.openlocfilehash: 1bb72babcc4bf425e4ea588e4e2a155b077c47cc
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43754875"
---
# <a name="adding-an-event-atl-tutorial-part-5"></a>Přidání události (ATL – tutoriál, část 5)

V tomto kroku přidáte `ClickIn` a `ClickOut` událostí do ovládacího prvku ATL. Bude platit `ClickIn` událost, když uživatel klikne v rámci mnohoúhelníků a fire `ClickOut` Pokud uživatel klikne na tlačítko mimo. Úlohy pro přidání události jsou následující:

- Přidávání `ClickIn` a `ClickOut` metody

- Generuje knihovnu typů

- Implementace rozhraní bodu připojení

## <a name="adding-the-clickin-and-clickout-methods"></a>Přidání clickin – a ClickOut metody

Pokud jste vytvořili v kroku 2 ovládací prvek ATL, vyberete **spojovací body** zaškrtávací políčko. To vytvoří `_IPolyCtlEvents` rozhraní v souboru Polygon.idl. Všimněte si, že název rozhraní začíná podtržítkem. Toto je konvence, že rozhraní je vnitřní rozhraní. Programy, které umožňují procházet objekty modelu COM proto můžete nechcete zobrazit rozhraní pro uživatele. Všimněte si také, že vyberete **spojovací body** přidejte následující řádek v souboru Polygon.idl označuje, že `_IPolyCtlEvents` je výchozím zdrojovém rozhraní:

`[default, source] dispinterface _IPolyCtlEvents;`

Zdrojový atribut označuje, že je zdroj oznámení, takže bude volat toto rozhraní v kontejneru.

Nyní přidejte `ClickIn` a `ClickOut` metod `_IPolyCtlEvents` rozhraní.

#### <a name="to-add-the-clickin-and-clickout-methods"></a>Chcete-li přidat metody clickin – a ClickOut

1. V zobrazení tříd rozbalte mnohoúhelníků a PolygonLib zobrazíte _IPolyCtlEvents.

2. Klikněte pravým tlačítkem na _IPolyCtlEvents. V místní nabídce klikněte na tlačítko **přidat**a potom klikněte na tlačítko **přidat metodu**.

3. Vyberte **návratový typ** z `void`.

4. Zadejte *clickin –* v **název metody** pole.

5. V části **atributy parametru**, vyberte **v** pole.

6. Vyberte **typ parametru** z `LONG`.

7. Typ *x* jako **název parametru**a klikněte na tlačítko **přidat**.

8. Opakujte kroky 5 až 7, tentokrát pro **název parametru** z *y*.

9. Klikněte na tlačítko **Další**.

10. Typ `method ClickIn` jako **helpstring**.

11. Klikněte na tlačítko **Dokončit**.

12. Zopakujte výše uvedené kroky a definovat `ClickOut` metody se stejným `LONG` parametry *x* a *y*, stejné **atributy parametru** a stejné `void` návratového typu.

Zkontrolujte soubor Polygon.idl a ověřte, že kód byla přidána do `_IPolyCtlEvents` dispinterface.

`_IPolyCtlEvents` Dispinterface v souboru Polygon.idl by teď měl vypadat takto:

[!code-cpp[NVC_ATL_Windowing#56](../atl/codesnippet/cpp/adding-an-event-atl-tutorial-part-5_1.idl)]

`ClickIn` a `ClickOut` metody vzít x a y souřadnice místem kliknutí jako parametry.

## <a name="generating-the-type-library"></a>Generuje knihovnu typů

V tomto okamžiku generovat knihovnu typů, protože Průvodce bodem připojení ji použít k získání informace potřebné k sestavení kompletních rozhraní bodu připojení a bod připojení kontejneru rozhraní ovládacího prvku.

#### <a name="to-generate-the-type-library"></a>Vytvoření knihovny typů

1. Znovu sestavte projekt.

     -nebo-

2. Klikněte pravým tlačítkem na soubor Polygon.idl v Průzkumníku řešení a klikněte na tlačítko **kompilaci** v místní nabídce.

Tím se vytvoří soubor Polygon.tlb, což je knihovna typů. Soubor Polygon.tlb není viditelná z Průzkumníku řešení, protože to je binární soubor a nemůžete zobrazit nebo upravit přímo.

## <a name="implementing-the-connection-point-interfaces"></a>Implementace rozhraní bodu připojení

Implementujte rozhraní bodu připojení a bod připojení kontejneru rozhraní ovládacího prvku. V modelu COM jsou události implementované pomocí mechanismu spojovací body. Přijímat události z objektu modelu COM, vytváří kontejner advisory připojení k bodu připojení, která implementuje objekt modelu COM. Protože objekt modelu COM může mít více bodů připojení, objekt modelu COM také implementuje rozhraní kontejneru bodu připojení. Prostřednictvím tohoto rozhraní můžete určit kontejneru, který spojovací body jsou podporovány.

Rozhraní, které implementuje bod připojení je volána `IConnectionPoint`, a rozhraní, které implementuje kontejner bod připojení se nazývá `IConnectionPointContainer`.

Implementaci `IConnectionPoint`, použije průvodce implementace bodu připojení. Tento průvodce vytvoří `IConnectionPoint` rozhraní tak, že knihovna typů pro čtení a provádění funkce pro každou událost, která může být aktivována.

#### <a name="to-use-the-implement-connection-point-wizard"></a>Chcete-li použít Průvodce implementací bodu připojení

1. V zobrazení tříd klikněte pravým tlačítkem na implementace třídy ovládacího prvku `CPolyCtl`.

2. V místní nabídce klikněte na tlačítko **přidat**a potom klikněte na tlačítko **přidat bod připojení**.

3. Vyberte `_IPolyCtlEvents` z **rozhraní zdroje** seznamu a poklepejte na něj a přidejte ji tak **body připojení implementovat** sloupce. Klikněte na tlačítko **Dokončit**. Proxy třída bodu připojení se vygeneruje, v tomto případě `CProxy_IPolyCtlEvents`.

Když se podíváte na _IPolyCtlEvents_CP.h generovaného souboru v Průzkumníku řešení, zobrazí se, že obsahuje třídu s názvem `CProxy_IPolyCtlEvents` , která je odvozena z `IConnectionPointImpl`. _IPolyCtlEvents_CP.h také definuje dvě metody `Fire_ClickIn` a `Fire_ClickOut`, které přebírají dva parametry souřadnic. Tyto metody volat, pokud chcete vyvolat událost z ovládacího prvku.

Průvodce také přidá `CProxy_PolyEvents` a `IConnectionPointContainerImpl` do ovládacího prvku seznamu více dědičnosti. Průvodce také zobrazuje `IConnectionPointContainer` vám tak, že přidáte do mapy modelu COM odpovídající položky.

Budete mít, provádění kódu, který podporuje události. Teď přidejte nějaký kód, aby se mohly aktivovat události v tuto chvíli odpovídající. Nezapomeňte, že chcete vyvolat `ClickIn` nebo `ClickOut` událost, když uživatel klikne levým tlačítkem myši v ovládacím prvku. Chcete-li zjistit, když uživatel klikne na tlačítko, přidejte obslužnou rutinu pro `WM_LBUTTONDOWN` zprávy.

#### <a name="to-add-a-handler-for-the-wmlbuttondown-message"></a>Chcete-li přidat obslužné rutiny pro zprávy WM_LBUTTONDOWN

1. V zobrazení tříd, klikněte pravým tlačítkem na třídu CPolyCtl a klikněte na tlačítko **vlastnosti** v místní nabídce.

2. V **vlastnosti** okna, klikněte na tlačítko **zprávy** ikonu a pak klikněte na tlačítko `WM_LBUTTONDOWN` ze seznamu na levé straně.

3. V rozevíracím seznamu, který se zobrazí, klikněte na  **\<Přidat > onlbuttondown –**. `OnLButtonDown` Deklaraci obslužné rutiny se přidají do souboru PolyCtl.h a implementaci obslužné rutiny se přidají do PolyCtl.cpp.

Dále upravte obslužnou rutinu.

#### <a name="to-modify-the-onlbuttondown-method"></a>Chcete-li změnit onlbuttondown – metoda

1. Změňte kód, který se skládá z `OnLButtonDown` metoda ve PolyCtl.cpp (odstranění libovolný kód umístěný v průvodci) tak, aby vypadal takto:

     [!code-cpp[NVC_ATL_Windowing#57](../atl/codesnippet/cpp/adding-an-event-atl-tutorial-part-5_2.cpp)]

Tento kód provede použití bodů počítá v `OnDraw` funkci, která vytvoří oblast, která zjistí uživatele myší volání `PtInRegion`.

*UMsg* parametru je ID zprávy Windows zpracovává. Můžete mít jednu funkci, která zpracovává řadu zpráv. *WParam* a *lParam* parametry jsou standardní hodnoty pro zpracovávanou zprávu. Parametr bHandled umožňuje určit, zda funkce zpracování zprávy, nebo ne. Ve výchozím nastavení je hodnota nastavena na hodnotu TRUE označuje, že funkce zpracování zprávy, ale můžete ho nastavit na hodnotu FALSE. To způsobí, že ATL, abyste mohli pokračovat, hledá další funkci obslužné rutiny zprávy k odeslání zprávy do.

## <a name="building-and-testing-the-control"></a>Vytváření a testování ovládacího prvku

Vyzkoušejte teď události. Vytvoření ovládacího prvku a znovu spusťte kontejner testů ovládacích prvků ActiveX. Tentokrát, zobrazte okno protokolu událostí. Směrování událostí do okna výstup, klikněte na tlačítko **protokolování** z **možnosti** nabídky a vybereme **protokolu do okna výstup**. Vložit ovládací prvek a akci kliknutím v okně. Všimněte si, že `ClickIn` se aktivuje, pokud klepnete na tlačítko v rámci plného mnohoúhelníku a `ClickOut` se spustí po kliknutí mimo ní.

V dalším kroku přidáte stránku vlastností.

[Zpátky ke kroku 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md) &#124; [ke kroku 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)

## <a name="see-also"></a>Viz také

[Kurz](../atl/active-template-library-atl-tutorial.md)

