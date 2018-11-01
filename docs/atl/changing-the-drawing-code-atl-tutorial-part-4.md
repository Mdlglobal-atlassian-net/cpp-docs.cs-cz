---
title: Změna kódu kreslení (ATL – tutoriál, část 4)
ms.custom: get-started-article
ms.date: 09/26/2018
helpviewer_keywords:
- _ATL_MIN_CRT macro
ms.assetid: 08ff14e8-aa49-4139-a110-5d071939cf1e
ms.openlocfilehash: ce6492eb2e4da04b261c7a88154674d036bb578a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481416"
---
# <a name="changing-the-drawing-code-atl-tutorial-part-4"></a>Změna kódu kreslení (ATL – tutoriál, část 4)

Ve výchozím nastavení, zobrazí kód pro vykreslování ovládacího prvku čtverec a text **PolyCtl**. V tomto kroku se změní kód, který zobrazí něco zajímavější. Jsou zahrnuty následující úkoly:

- Úprava souboru hlaviček

- Úpravy `OnDraw` – funkce

- Přidání metody k výpočtu bodů mnohoúhelníku

- Inicializuje se barva výplně

## <a name="modifying-the-header-file"></a>Úprava souboru hlaviček

Začněte přidáním podpory pro matematické funkce `sin` a `cos`, který se bude používat vypočítat, bodů mnohoúhelníku a tím, že vytvoříte pole k uložení umístění.

### <a name="to-modify-the-header-file"></a>Chcete-li upravit soubor hlaviček

1. Přidejte řádek `#include <math.h>` do horní části souboru PolyCtl.h. Horní části souboru by měla vypadat nějak takto:

    [!code-cpp[NVC_ATL_Windowing#47](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_1.cpp)]

1. Implementace `IProvideClassInfo` rozhraní přidáním následujícího kódu do souboru PolyCtl.h poskytnout informace o metodě ovládacího prvku. V `CPolyCtl` třídy, nahraďte řádek:

    ```cpp
    public CComControl<CPolyCtl>
    ```

    with

    ```cpp
    public CComControl<CPolyCtl>,
    public IProvideClassInfo2Impl<&CLSID_PolyCtl, &DIID__IPolyCtlEvents, &LIBID_PolygonLib>
    ```

    a v `BEGIN_COM_MAP(CPolyCtl)`, přidejte řádky:

    ```cpp
    COM_INTERFACE_ENTRY(IProvideClassInfo)
    COM_INTERFACE_ENTRY(IProvideClassInfo2)
    ```

1. Jakmile se počítají bodů mnohoúhelníku, se uloží do pole typu `POINT`, proto přidat pole po příkazu definice `short m_nSides;` v souboru PolyCtl.h:

    [!code-cpp[NVC_ATL_Windowing#48](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_2.h)]

## <a name="modifying-the-ondraw-method"></a>Úprava OnDraw – metoda

Teď byste měli upravit `OnDraw` metody v souboru PolyCtl.h. Přidáte kód vytvoří novou pera a štětce, pomocí kterého se má nakreslit vaše mnohoúhelník a pak zavolá `Ellipse` a `Polygon` funkce rozhraní Win32 API provádět skutečný kreslení.

### <a name="to-modify-the-ondraw-function"></a>Chcete-li změnit OnDraw – funkce

1. Nahraďte existující `OnDraw` metody v souboru PolyCtl.h následujícím kódem:

    [!code-cpp[NVC_ATL_Windowing#49](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_3.cpp)]

## <a name="adding-a-method-to-calculate-the-polygon-points"></a>Přidání metody k výpočtu bodů mnohoúhelníku

Přidat metodu nazvanou `CalcPoints`, která vypočítá souřadnice bodů, které tvoří hraniční mnohoúhelníku. Tyto výpočty budou založeny na proměnnou OBDÉLNÍK, který je předán do funkce.

### <a name="to-add-the-calcpoints-method"></a>Chcete-li přidat CalcPoints – metoda

1. Přidat deklaraci `CalcPoints` k `IPolyCtl` veřejnou část `CPolyCtl` třída v souboru PolyCtl.h:

    [!code-cpp[NVC_ATL_Windowing#50](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_4.h)]

    Poslední část veřejnou část `CPolyCtl` třídy bude vypadat například takto:

    [!code-cpp[NVC_ATL_Windowing#51](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_5.h)]

1. Přidejte tato implementace `CalcPoints` funkce za účelem PolyCtl.cpp:

    [!code-cpp[NVC_ATL_Windowing#52](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_6.cpp)]

## <a name="initializing-the-fill-color"></a>Inicializuje se barva výplně

Inicializovat `m_clrFillColor` s výchozí barvu.

### <a name="to-initialize-the-fill-color"></a>Inicializace barvu výplně

1. Použití zelená jako výchozí barva přidáním tohoto řádku `CPolyCtl` konstruktoru v souboru PolyCtl.h:

    [!code-cpp[NVC_ATL_Windowing#53](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_7.h)]

Konstruktoru nyní vypadá takto:

[!code-cpp[NVC_ATL_Windowing#54](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_8.h)]

## <a name="building-and-testing-the-control"></a>Vytváření a testování ovládacího prvku

Znovu sestavte ovládací prvek. Ujistěte se, že soubor PolyCtl.htm zavřená, pokud je stále otevřen a potom klikněte na tlačítko **sestavit mnohoúhelník** na **sestavení** nabídky. Může zobrazit ovládací prvek ještě jednou ze stránky PolyCtl.htm, ale tentokrát použijte kontejner testů ovládacích prvků ActiveX.

### <a name="to-use-the-activex-control-test-container"></a>Chcete-li použít kontejner testů ovládacích prvků ActiveX

1. Sestavte a spusťte kontejner testů ovládacích prvků ActiveX. [Lze kontejner TSTCON vzorku: kontejner testů ovládacích prvků ActiveX](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole/TstCon) najdete na Githubu.

    > [!NOTE]
    > Chyby zahrnující `ATL::CW2AEX`, v Script.Cpp, nahraďte řádek `TRACE( "XActiveScriptSite::GetItemInfo( %s )\n", pszNameT );` s `TRACE( "XActiveScriptSite::GetItemInfo( %s )\n", pszNameT.m_psz );`a řádek `TRACE( "Source Text: %s\n", COLE2CT( bstrSourceLineText ) );` s `TRACE( "Source Text: %s\n", bstrSourceLineText );`.<br/>
    > Chyby zahrnující `HMONITOR`, otevřete StdAfx.h v `TCProps` projektu a nahradit:
    > ```
    > #ifndef WINVER
    > #define WINVER 0x0400
    > #endif
    > ```
    > with
    > ```
    > #ifndef WINVER
    > #define WINVER 0x0500
    > #define _WIN32_WINNT 0x0500
    > #endif
    > ```

1. V **kontejner testu**na **upravit** nabídky, klikněte na tlačítko **vložte nový ovládací prvek**.

1. Vyhledání ovládacího prvku, která bude volána `PolyCtl class`a klikněte na tlačítko **OK**. Zobrazí se zelený trojúhelník v kruhu.

Zkuste změnit počet stran podle dalšího postupu. K úpravě vlastností na duální rozhraní v rámci **kontejner testu**, použijte **vyvolání metody**.

### <a name="to-modify-a-controls-property-from-within-the-test-container"></a>Chcete-li změnit vlastnosti ovládacího prvku z v rámci testovacího kontejneru

1. V **kontejner testu**, klikněte na tlačítko **vyvolání metody** na **ovládací prvek** nabídky.

    **Vyvolání metody** zobrazí dialogové okno.

1. Vyberte **PropPut** verzi **strany** vlastnost z **název metody** rozevíracího seznamu.

1. Typ `5` v **hodnota parametru** klikněte **nastavit hodnotu**a klikněte na tlačítko **Invoke**.

Všimněte si, že ovládací prvek se nezmění. I když změníte počet stran interně tak, že nastavíte `m_nSides` proměnné, to nezpůsobil překreslit ovládací prvek. Pokud můžete přepnout na jinou aplikaci a pak přejděte zpátky do **kontejner testu**, zjistíte, že ovládací prvek má překreslit a má správný počet stran.

Chcete-li tento problém, přidejte volání `FireViewChange` funkci definovanou v `IViewObjectExImpl`, jakmile nastavíte počet stran. Pokud ovládací prvek běží v samostatném okně `FireViewChange` zavolá `InvalidateRect` metoda přímo. Pokud je ovládací prvek bez oken, `InvalidateRect` metoda bude volána na rozhraní webu kontejneru. To přinutí repaint samotný ovládací prvek.

### <a name="to-add-a-call-to-fireviewchange"></a>Chcete-li přidat volání FireViewChange

1. Aktualizovat tak, že přidáte volání PolyCtl.cpp `FireViewChange` k `put_Sides` metody. Jakmile budete hotovi, `put_Sides` metoda by měla vypadat přibližně takto:

    [!code-cpp[NVC_ATL_Windowing#55](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_9.cpp)]

Po přidání `FireViewChange`, sestavení a zkuste to znovu za kontejner testu ovládacího prvku ActiveX ovládacího prvku. Tentokrát po změnit počet stran a kliknutí na `Invoke`, měli byste vidět ovládací prvek okamžitě změnit.

V dalším kroku přidejte událost.

[Zpátky ke kroku 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md) &#124; [ke kroku 5](../atl/adding-an-event-atl-tutorial-part-5.md)

## <a name="see-also"></a>Viz také

[Kurz](../atl/active-template-library-atl-tutorial.md)<br/>
[Testování vlastností a událostí pomocí testovacího kontejneru](../mfc/testing-properties-and-events-with-test-container.md)
