---
title: Přidání události (ATL – tutoriál, část 5)
ms.custom: get-started-article
ms.date: 09/27/2018
ms.assetid: 2de12022-3148-4ce3-8606-8a9d4274f0e9
ms.openlocfilehash: c9a7c6f38a2f47ec808081e440a200737ad1928a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127571"
---
# <a name="adding-an-event-atl-tutorial-part-5"></a>Přidání události (ATL – tutoriál, část 5)

V tomto kroku přidáte `ClickIn` a událost `ClickOut` k ovládacímu prvku ATL. Pokud uživatel klikne na možnost mimo jiné, dojde k události `ClickIn`, pokud uživatel klikne v rámci mnohoúhelníku a požáru `ClickOut`. Úkoly pro přidání události jsou následující:

- Přidání metod `ClickIn` a `ClickOut`

- Generování knihovny typů

- Implementace rozhraní bodu připojení

## <a name="adding-the-clickin-and-clickout-methods"></a>Přidání metod ClickIn a kliknutí

Při vytvoření ovládacího prvku ATL v kroku 2 jste zaškrtli políčko **spojovací body** . Tímto se vytvořilo rozhraní `_IPolyCtlEvents` v souboru mnohoúhelník. idl. Všimněte si, že název rozhraní začíná podtržítkem. Toto je konvence, která označuje, že rozhraní je interní rozhraní. Programy, které umožňují procházení objektů COM, tedy mohou zvolit, že se má pro uživatele zobrazit rozhraní. Všimněte si také, že při výběru **bodů připojení** do souboru mnohoúhelník. idl byly přidány následující řádky, které označují, že `_IPolyCtlEvents` výchozí zdrojové rozhraní:

`[default, source] dispinterface _IPolyCtlEvents;`

Zdrojový atribut označuje, že ovládací prvek je zdrojem oznámení, takže bude volat toto rozhraní na kontejneru.

Nyní do rozhraní `_IPolyCtlEvents` přidejte metody `ClickIn` a `ClickOut`.

### <a name="to-add-the-clickin-and-clickout-methods"></a>Postup přidání ClickIn a kliknutí na metody

1. V **Průzkumník řešení**otevřete mnohoúhelník. idl a přidejte následující kód do části `methods:` v deklaraci `dispInterface_IPolyCtlEvents` knihovny PolygonLib:

    ```cpp
   [id(1), helpstring("method ClickIn")] void ClickIn([in] LONG x,[in] LONG y);
   [id(2), helpstring("method ClickOut")] void ClickOut([in] LONG x,[in] LONG y);
    ```

Metody `ClickIn` a `ClickOut` přebírají souřadnice x a y kliklého bodu jako parametry.

## <a name="generating-the-type-library"></a>Generování knihovny typů

V tomto okamžiku vygenerujte knihovnu typů, protože projekt bude používat k získání informací, které potřebuje k vytvoření rozhraní bodu připojení a rozhraní kontejneru spojovacího bodu pro váš ovládací prvek.

### <a name="to-generate-the-type-library"></a>Generování knihovny typů

1. Znovu sestavte projekt.

     -nebo-

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na soubor mnohoúhelník. idl a v místní nabídce klikněte na **kompilovat** .

Tím se vytvoří soubor mnohoúhelník. tlb, který je vaší knihovnou typů. Soubor mnohoúhelník. tlb není viditelný z **Průzkumník řešení**, protože se jedná o binární soubor a nedá se přímo zobrazit nebo upravit.

## <a name="implementing-the-connection-point-interfaces"></a>Implementace rozhraní bodu připojení

Implementujte rozhraní bodu připojení a rozhraní kontejneru spojovacího bodu pro váš ovládací prvek. V modelu COM jsou události implementovány pomocí mechanismu spojovacích bodů. Pokud chcete přijímat události z objektu modelu COM, kontejner vytvoří poradní připojení k bodu připojení, který implementuje objekt COM. Vzhledem k tomu, že objekt COM může mít více spojovacích bodů, objekt COM také implementuje rozhraní kontejneru spojovacího bodu. Prostřednictvím tohoto rozhraní může kontejner určit, které spojovací body se podporují.

Rozhraní, které implementuje spojovací bod, se nazývá `IConnectionPoint`a rozhraní, které implementuje kontejner spojovacího bodu, se nazývá `IConnectionPointContainer`.

K implementaci `IConnectionPoint`budete používat Průvodce implementací bodu připojení. Tento průvodce vygeneruje rozhraní `IConnectionPoint` přečtením knihovny typů a implementací funkce pro každou událost, kterou lze aktivovat.

### <a name="to-implement-the-connection-points"></a>Implementace přípojných bodů

1. V **Průzkumník řešení**otevřete _IPolyCtlEvents_CP. h a do příkazu `public:` v `CProxy_IPolyCtlEvents` třídy přidejte následující kód:

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

Uvidíte, že tento soubor obsahuje třídu s názvem `CProxy_IPolyCtlEvents`, která je odvozena z `IConnectionPointImpl`. _IPolyCtlEvents_CP. h nyní definuje dvě metody `Fire_ClickIn` a `Fire_ClickOut`, které přebírají dva parametry souřadnic. Tyto metody zavoláte, pokud chcete vyvolat událost z vašeho ovládacího prvku.

Vytvořením vybraného ovládacího prvku s vybranými **body připojení** se pro vás vygeneroval soubor _IPolyCtlEvents_CP. h. Přidal také `CProxy_PolyEvents` a `IConnectionPointContainerImpl` do seznamu vícenásobné dědičnosti vašeho ovládacího prvku a zpřístupněné `IConnectionPointContainer` pro vás přidáním vhodných položek do mapy modelu COM.

Dokončili jste implementaci kódu pro podporu událostí. Nyní přidejte nějaký kód, který události spustí v příslušném okamžiku. Nezapomeňte, že budete chtít vyvolat událost `ClickIn` nebo `ClickOut`, když uživatel klikne levým tlačítkem myši v ovládacím prvku. Chcete-li zjistit, kdy uživatel klikne na tlačítko, přidejte obslužnou rutinu pro `WM_LBUTTONDOWN`ovou zprávu.

### <a name="to-add-a-handler-for-the-wm_lbuttondown-message"></a>Přidání obslužné rutiny pro zprávu WM_LBUTTONDOWN

1. V **zobrazení tříd**klikněte pravým tlačítkem myši na třídu `CPolyCtl` a v místní nabídce klikněte na možnost **vlastnosti** .

1. V okně **vlastnosti** klikněte na ikonu **zprávy** a potom v seznamu na levé straně klikněte na `WM_LBUTTONDOWN`.

1. V rozevíracím seznamu, který se zobrazí, klikněte **\<přidat > OnLButtonDown**. Deklarace obslužné rutiny `OnLButtonDown` bude přidána do PolyCtl. h a implementace obslužné rutiny bude přidána do PolyCtl. cpp.

Dále upravte obslužnou rutinu.

### <a name="to-modify-the-onlbuttondown-method"></a>Postup úpravy metody OnLButtonDown

1. Změňte kód, který zahrnuje metodu `OnLButtonDown` v PolyCtl. cpp (odstranění libovolného kódu uloženého průvodcem) tak, aby vypadal takto:

    [!code-cpp[NVC_ATL_Windowing#57](../atl/codesnippet/cpp/adding-an-event-atl-tutorial-part-5_2.cpp)]

Tento kód využívá body, které jsou vypočítány ve funkci `OnDraw` k vytvoření oblasti, která detekuje kliknutí myší uživatele s voláním `PtInRegion`.

Parametr *uMsg* je ID zpracovávané zprávy systému Windows. To vám umožní mít jednu funkci, která zpracuje určitý rozsah zpráv. Parametry *wParam* a *lParam* jsou standardními hodnotami pro zpracovávanou zprávu. Parametr *bHandled* umožňuje určit, zda funkce zpracovala zprávu, nebo ne. Ve výchozím nastavení je hodnota nastavena na TRUE, aby označovala, že funkce zpracovala zprávu, ale můžete ji nastavit na FALSE. To způsobí, že knihovna ATL bude pokračovat ve vyhledávání jiné funkce obslužné rutiny zpráv, do které se zpráva pošle.

## <a name="building-and-testing-the-control"></a>Sestavování a testování ovládacího prvku

Teď Vyzkoušejte své události. Sestavte ovládací prvek a znovu spusťte kontejner testu ovládacího prvku ActiveX. Tentokrát si prohlédněte okno Protokol událostí. Chcete-li směrovat události do okna výstup, klikněte na **protokolování** v nabídce **Možnosti** a vyberte možnost **protokol do okna výstup**. Vložte ovládací prvek a zkuste kliknout v okně. Všimněte si, že `ClickIn` je vyvolána, pokud kliknete na vyplněný mnohoúhelník a `ClickOut` je aktivována, když kliknete na mimo ni.

V dalším kroku přidáte stránku vlastností.

[Zpět ke kroku 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md) &#124; pro [Krok 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)

## <a name="see-also"></a>Viz také

[Kurz](../atl/active-template-library-atl-tutorial.md)
