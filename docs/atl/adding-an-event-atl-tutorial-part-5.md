---
title: Přidání události (ATL – tutoriál, část 5)
ms.custom: get-started-article
ms.date: 09/27/2018
ms.assetid: 2de12022-3148-4ce3-8606-8a9d4274f0e9
ms.openlocfilehash: 4576af12f73e907fa8826ad71185a42ed9b9308e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643037"
---
# <a name="adding-an-event-atl-tutorial-part-5"></a>Přidání události (ATL – tutoriál, část 5)

V tomto kroku přidáte `ClickIn` a `ClickOut` událostí do ovládacího prvku ATL. Bude platit `ClickIn` událost, když uživatel klikne v rámci mnohoúhelníků a fire `ClickOut` Pokud uživatel klikne na tlačítko mimo. Úlohy pro přidání události jsou následující:

- Přidávání `ClickIn` a `ClickOut` metody

- Generuje knihovnu typů

- Implementace rozhraní bodu připojení

## <a name="adding-the-clickin-and-clickout-methods"></a>Přidání metody clickin – a ClickOut

Pokud jste vytvořili v kroku 2 ovládací prvek ATL, vyberete **spojovací body** zaškrtávací políčko. To vytvoří `_IPolyCtlEvents` rozhraní v souboru Polygon.idl. Všimněte si, že název rozhraní začíná podtržítkem. Toto je konvence, že rozhraní je vnitřní rozhraní. Programy, které umožňují procházet objekty modelu COM proto můžete nechcete zobrazit rozhraní pro uživatele. Všimněte si také, že vyberete **spojovací body** přidejte následující řádek v souboru Polygon.idl označuje, že `_IPolyCtlEvents` je výchozím zdrojovém rozhraní:

`[default, source] dispinterface _IPolyCtlEvents;`

Zdrojový atribut označuje, že je zdroj oznámení, takže bude volat toto rozhraní v kontejneru.

Nyní přidejte `ClickIn` a `ClickOut` metod `_IPolyCtlEvents` rozhraní.

### <a name="to-add-the-clickin-and-clickout-methods"></a>Chcete-li přidat metody clickin – a ClickOut

1. V **Průzkumníka řešení**, otevřete Polygon.idl a přidejte následující kód pod `methods:` v `dispInterface_IPolyCtlEvents` deklarace PolygonLib knihovny:

    ```cpp
   [id(1), helpstring("method ClickIn")] void ClickIn([in] LONG x,[in] LONG y);
   [id(2), helpstring("method ClickOut")] void ClickOut([in] LONG x,[in] LONG y);
    ```

`ClickIn` a `ClickOut` metody vzít x a y souřadnice místem kliknutí jako parametry.

## <a name="generating-the-type-library"></a>Generuje knihovnu typů

Generovat knihovnu typů v tomto okamžiku vzhledem k tomu, že projekt bude používat k získání informací, které potřebuje k vytvoření rozhraní bodu připojení a bod připojení kontejneru rozhraní ovládacího prvku.

### <a name="to-generate-the-type-library"></a>Vytvoření knihovny typů

1. Znovu sestavte projekt.

     -nebo-

1. Klikněte pravým tlačítkem na soubor Polygon.idl v **Průzkumníka řešení** a klikněte na tlačítko **kompilaci** v místní nabídce.

Tím se vytvoří soubor Polygon.tlb, což je knihovna typů. Soubor Polygon.tlb není viditelná z **Průzkumníka řešení**, protože to je binární soubor a nemůžete zobrazit nebo upravit přímo.

## <a name="implementing-the-connection-point-interfaces"></a>Implementace rozhraní bodu připojení

Implementujte rozhraní bodu připojení a bod připojení kontejneru rozhraní ovládacího prvku. V modelu COM jsou události implementované pomocí mechanismu spojovací body. Přijímat události z objektu modelu COM, vytváří kontejner advisory připojení k bodu připojení, která implementuje objekt modelu COM. Protože objekt modelu COM může mít více bodů připojení, objekt modelu COM také implementuje rozhraní kontejneru bodu připojení. Prostřednictvím tohoto rozhraní můžete určit kontejneru, který spojovací body jsou podporovány.

Rozhraní, které implementuje bod připojení je volána `IConnectionPoint`, a rozhraní, které implementuje kontejner bod připojení se nazývá `IConnectionPointContainer`.

Implementaci `IConnectionPoint`, použije průvodce implementace bodu připojení. Tento průvodce vytvoří `IConnectionPoint` rozhraní tak, že knihovna typů pro čtení a provádění funkce pro každou událost, která může být aktivována.

### <a name="to-implement-the-connection-points"></a>K implementaci spojovacích bodů

1. V **Průzkumníku řešení**, otevřete _IPolyCtlEvents_CP.h a přidejte následující kód `public:` výroky `CProxy_IPolyCtlEvents` třídy:

    ```cpp
    VOID Fire_ClickIn(LONG x, LONG y)
    {
        T* pT = static_cast<T*>(this);
        int nConnectionIndex;
        CComVariant* pvars = new CComVariant[2];
        int nConnections = m_vec.GetSize();

        for (nConnectionIndex = 0; nConnectionIndex < nConnections; nConnectionIndex++)
        {
            pT->Lock();
            CComPtr<IUnknown> sp = m_vec.GetAt(nConnectionIndex);
            pT->Unlock();
            IDispatch* pDispatch = reinterpret_cast<IDispatch*>(sp.p);
            if (pDispatch != NULL)
            {
                pvars[1].vt = VT_I4;
                pvars[1].lVal = x;
                pvars[0].vt = VT_I4;
                pvars[0].lVal = y;
                DISPPARAMS disp = { pvars, NULL, 2, 0 };
                pDispatch->Invoke(0x1, IID_NULL, LOCALE_USER_DEFAULT, DISPATCH_METHOD, &disp, NULL, NULL, NULL);
            }
        }
        delete[] pvars;

    }
    VOID Fire_ClickOut(LONG x, LONG y)
    {
        T* pT = static_cast<T*>(this);
        int nConnectionIndex;
        CComVariant* pvars = new CComVariant[2];
        int nConnections = m_vec.GetSize();

        for (nConnectionIndex = 0; nConnectionIndex < nConnections; nConnectionIndex++)
        {
            pT->Lock();
            CComPtr<IUnknown> sp = m_vec.GetAt(nConnectionIndex);
            pT->Unlock();
            IDispatch* pDispatch = reinterpret_cast<IDispatch*>(sp.p);
            if (pDispatch != NULL)
            {
                pvars[1].vt = VT_I4;
                pvars[1].lVal = x;
                pvars[0].vt = VT_I4;
                pvars[0].lVal = y;
                DISPPARAMS disp = { pvars, NULL, 2, 0 };
                pDispatch->Invoke(0x2, IID_NULL, LOCALE_USER_DEFAULT, DISPATCH_METHOD, &disp, NULL, NULL, NULL);
            }
        }
        delete[] pvars;

    }
    ```

Zobrazí se, že tento soubor obsahuje třídu s názvem `CProxy_IPolyCtlEvents` , která je odvozena z `IConnectionPointImpl`. _IPolyCtlEvents_CP.h teď definuje dvě metody `Fire_ClickIn` a `Fire_ClickOut`, které přebírají dva parametry souřadnic. Tyto metody volat, pokud chcete vyvolat událost z ovládacího prvku.

Tím, že vytvoříte ovládací prvek s **spojovací body** možnost aktivní, soubor _IPolyCtlEvents_CP.h byla vygenerována. Také přidala `CProxy_PolyEvents` a `IConnectionPointContainerImpl` do ovládacího prvku seznamu více dědičnosti a zveřejnění `IConnectionPointContainer` vám tak, že přidáte odpovídající položky do mapy modelu COM.

Budete mít, provádění kódu, který podporuje události. Teď přidejte nějaký kód, aby se mohly aktivovat události v tuto chvíli odpovídající. Nezapomeňte, že chcete vyvolat `ClickIn` nebo `ClickOut` událost, když uživatel klikne levým tlačítkem myši v ovládacím prvku. Chcete-li zjistit, když uživatel klikne na tlačítko, přidejte obslužnou rutinu pro `WM_LBUTTONDOWN` zprávy.

### <a name="to-add-a-handler-for-the-wmlbuttondown-message"></a>Chcete-li přidat obslužné rutiny pro zprávy WM_LBUTTONDOWN

1. V **zobrazení tříd**, klikněte pravým tlačítkem myši `CPolyCtl` třídy a klikněte na tlačítko **vlastnosti** v místní nabídce.

1. V **vlastnosti** okna, klikněte na tlačítko **zprávy** ikonu a pak klikněte na tlačítko `WM_LBUTTONDOWN` ze seznamu na levé straně.

1. V rozevíracím seznamu, který se zobrazí, klikněte na  **\<Přidat > onlbuttondown –**. `OnLButtonDown` Deklaraci obslužné rutiny se přidají do souboru PolyCtl.h a implementaci obslužné rutiny se přidají do PolyCtl.cpp.

Dále upravte obslužnou rutinu.

### <a name="to-modify-the-onlbuttondown-method"></a>Chcete-li změnit onlbuttondown – metoda

1. Změňte kód, který se skládá z `OnLButtonDown` metoda ve PolyCtl.cpp (odstranění libovolný kód umístěný v průvodci) tak, aby vypadal takto:

    [!code-cpp[NVC_ATL_Windowing#57](../atl/codesnippet/cpp/adding-an-event-atl-tutorial-part-5_2.cpp)]

Tento kód provede použití bodů počítá v `OnDraw` funkci, která vytvoří oblast, která zjistí uživatele myší volání `PtInRegion`.

*UMsg* parametru je ID zprávy Windows zpracovává. Můžete mít jednu funkci, která zpracovává řadu zpráv. *WParam* a *lParam* parametry jsou standardní hodnoty pro zpracovávanou zprávu. Parametr *bHandled* umožňuje určit, zda funkce zpracování zprávy, nebo ne. Ve výchozím nastavení je hodnota nastavena na hodnotu TRUE označuje, že funkce zpracování zprávy, ale můžete ho nastavit na hodnotu FALSE. To způsobí, že ATL, abyste mohli pokračovat, hledá další funkci obslužné rutiny zprávy k odeslání zprávy do.

## <a name="building-and-testing-the-control"></a>Vytváření a testování ovládacího prvku

Vyzkoušejte teď události. Vytvoření ovládacího prvku a znovu spusťte kontejner testů ovládacích prvků ActiveX. Tentokrát, zobrazte okno protokolu událostí. Směrování událostí do okna výstup, klikněte na tlačítko **protokolování** z **možnosti** nabídky a vybereme **protokolu do okna výstup**. Vložit ovládací prvek a akci kliknutím v okně. Všimněte si, že `ClickIn` se aktivuje, pokud klepnete na tlačítko v rámci plného mnohoúhelníku a `ClickOut` se spustí po kliknutí mimo ní.

V dalším kroku přidáte stránku vlastností.

[Zpátky ke kroku 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md) &#124; [ke kroku 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)

## <a name="see-also"></a>Viz také

[Kurz](../atl/active-template-library-atl-tutorial.md)
