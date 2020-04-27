---
title: Změna kódu kreslení (ATL – tutoriál, část 4)
ms.custom: get-started-article
ms.date: 09/26/2018
helpviewer_keywords:
- _ATL_MIN_CRT macro
ms.assetid: 08ff14e8-aa49-4139-a110-5d071939cf1e
ms.openlocfilehash: 319a27b55c394349de751546457b0741c0799cfc
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167640"
---
# <a name="changing-the-drawing-code-atl-tutorial-part-4"></a>Změna kódu kreslení (ATL – tutoriál, část 4)

Ve výchozím nastavení zobrazí kód pro kreslení ovládacího prvku čtverc a text **PolyCtl**. V tomto kroku změníte kód tak, aby zobrazoval něco zajímavějšího. Jsou zapojeny následující úlohy:

- Úprava hlavičkového souboru

- Změna `OnDraw` funkce

- Přidání metody pro výpočet bodů mnohoúhelníku

- Inicializuje se barva výplně.

## <a name="modifying-the-header-file"></a>Úprava hlavičkového souboru

Začněte přidáním podpory pro matematické funkce `sin` a `cos`, které budou použity k výpočtu bodů mnohoúhelníku a vytvořením pole pro uložení pozic.

### <a name="to-modify-the-header-file"></a>Úprava hlavičkového souboru

1. Přidá řádek `#include <math.h>` do horní části PolyCtl. h. Horní část souboru by měla vypadat takto:

    [!code-cpp[NVC_ATL_Windowing#47](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_1.cpp)]

1. Implementujte `IProvideClassInfo` rozhraní k poskytnutí informací o metodě pro ovládací prvek přidáním následujícího kódu do PolyCtl. h. Ve `CPolyCtl` třídě nahraďte řádek:

    ```cpp
    public CComControl<CPolyCtl>
    ```

    with

    ```cpp
    public CComControl<CPolyCtl>,
    public IProvideClassInfo2Impl<&CLSID_PolyCtl, &DIID__IPolyCtlEvents, &LIBID_PolygonLib>
    ```

    a do `BEGIN_COM_MAP(CPolyCtl)`přidejte řádky:

    ```cpp
    COM_INTERFACE_ENTRY(IProvideClassInfo)
    COM_INTERFACE_ENTRY(IProvideClassInfo2)
    ```

1. Po výpočtu bodů mnohoúhelníku budou uloženy v poli typu `POINT`, takže přidejte pole za příkaz `short m_nSides;` definice v PolyCtl. h:

    [!code-cpp[NVC_ATL_Windowing#48](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_2.h)]

## <a name="modifying-the-ondraw-method"></a>Změna metody nakreslení

Nyní byste měli upravit `OnDraw` metodu v PolyCtl. h. Kód, který přidáte, vytvoří nové pero a štětce, pomocí kterého se má nakreslit mnohoúhelník, a potom `Ellipse` zavolá funkce a `Polygon` Win32 API, aby se provedl skutečný výkres.

### <a name="to-modify-the-ondraw-function"></a>Úprava funkce nakreslit

1. Existující `OnDraw` metodu v PolyCtl. h nahraďte následujícím kódem:

    [!code-cpp[NVC_ATL_Windowing#49](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_3.cpp)]

## <a name="adding-a-method-to-calculate-the-polygon-points"></a>Přidání metody pro výpočet bodů mnohoúhelníku

Přidejte metodu s názvem `CalcPoints`, která bude počítat souřadnice bodů, které tvoří obvodu mnohoúhelníku. Tyto výpočty budou založené na proměnné RECT, která je předána do funkce.

### <a name="to-add-the-calcpoints-method"></a>Přidání metody CalcPoints

1. Přidejte deklaraci `CalcPoints` do `IPolyCtl` veřejné části `CPolyCtl` třídy v PolyCtl. h:

    [!code-cpp[NVC_ATL_Windowing#50](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_4.h)]

    Poslední část veřejné části `CPolyCtl` třídy bude vypadat takto:

    [!code-cpp[NVC_ATL_Windowing#51](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_5.h)]

1. Přidejte tuto implementaci `CalcPoints` funkce na konec PolyCtl. cpp:

    [!code-cpp[NVC_ATL_Windowing#52](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_6.cpp)]

## <a name="initializing-the-fill-color"></a>Inicializuje se barva výplně.

Inicializovat `m_clrFillColor` s výchozí barvou.

### <a name="to-initialize-the-fill-color"></a>Inicializace barvy výplně

1. Použijte zelenou jako výchozí barvu přidáním tohoto řádku do `CPolyCtl` konstruktoru v PolyCtl. h:

    [!code-cpp[NVC_ATL_Windowing#53](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_7.h)]

Konstruktor teď vypadá takto:

[!code-cpp[NVC_ATL_Windowing#54](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_8.h)]

## <a name="building-and-testing-the-control"></a>Sestavování a testování ovládacího prvku

Znovu Sestavte ovládací prvek. Ujistěte se, že je soubor PolyCtl. htm zavřený, pokud je stále otevřený, a potom v nabídce **sestavení** klikněte na **sestavit mnohoúhelník** . Tuto kontrolu můžete znovu zobrazit na stránce PolyCtl. htm, ale tentokrát použijte kontejner testu ovládacího prvku ActiveX.

### <a name="to-use-the-activex-control-test-container"></a>Použití kontejneru testů ovládacího prvku ActiveX

1. Sestavte a spusťte kontejner testu ovládacího prvku ActiveX. [Ukázka TSTCON: kontejner testu ovládacího prvku ActiveX](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole/TstCon) najdete na GitHubu.

    > [!NOTE]
    > V případě chyb `ATL::CW2AEX`týkajících se, ve skriptu. cpp `TRACE( "XActiveScriptSite::GetItemInfo( %s )\n", pszNameT );` , `TRACE( "XActiveScriptSite::GetItemInfo( %s )\n", pszNameT.m_psz );`nahraďte řádek `TRACE( "Source Text: %s\n", COLE2CT( bstrSourceLineText ) );` řetězcem a řádkem `TRACE( "Source Text: %s\n", bstrSourceLineText );`.<br/>
    > V případě chyb `HMONITOR`týkajících se otevření souboru stdafx. `TCProps` h v projektu a nahrazení:
    >
    > ```cpp
    > #ifndef WINVER
    > #define WINVER 0x0400
    > #endif
    > ```
    >
    > with
    >
    > ```cpp
    > #ifndef WINVER
    > #define WINVER 0x0500
    > #define _WIN32_WINNT 0x0500
    > #endif
    > ```

1. V části **kontejner testu**klikněte v nabídce **Úpravy** na možnost **Vložit nový ovládací prvek**.

1. Vyhledejte ovládací prvek, který bude zavolán `PolyCtl class`, a klikněte na tlačítko **OK**. V kruhu se zobrazí zelený trojúhelník.

Zkuste změnit počet stran podle následujícího postupu. Chcete-li upravit vlastnosti pro duální rozhraní v rámci **kontejneru testů**, použijte **metody Invoke**.

### <a name="to-modify-a-controls-property-from-within-the-test-container"></a>Úprava vlastnosti ovládacího prvku v rámci kontejneru testů

1. V části **kontejner testu**klikněte v nabídce **ovládacího prvku** na **vyvolat metody** .

    Zobrazí se dialogové okno **vyvolání metody** .

1. V rozevíracím seznamu **název metody** vyberte verzi **propput** vlastnosti **strany** .

1. Do `5` pole **hodnota parametru** zadejte, klikněte na **nastavit hodnotu**a klikněte na **vyvolat**.

Všimněte si, že se ovládací prvek nemění. I když jste změnili počet stran interně tím, `m_nSides` že nastavíte proměnnou, to nezpůsobí překreslení ovládacího prvku. Pokud přepnete do jiné aplikace a poté přepnete zpět do **testovacího kontejneru**, zjistíte, že ovládací prvek byl překreslen a má správný počet stran.

Chcete-li tento problém vyřešit, přidejte po nastavení `FireViewChange` počtu stran volání funkce `IViewObjectExImpl`definované v. Pokud je ovládací prvek spuštěn v samostatném okně, `FireViewChange` bude volat `InvalidateRect` metodu přímo. Pokud ovládací prvek používá bez okna, `InvalidateRect` metoda bude volána v rozhraní lokality kontejneru. To vynutí, aby ovládací prvek překreslit sám sebe.

### <a name="to-add-a-call-to-fireviewchange"></a>Přidání volání do FireViewChange

1. Aktualizujte PolyCtl. cpp přidáním volání `FireViewChange` do `put_Sides` metody. Po dokončení by `put_Sides` metoda měla vypadat takto:

    [!code-cpp[NVC_ATL_Windowing#55](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_9.cpp)]

Po přidání `FireViewChange`, znovu sestavte a zkuste ovládací prvek znovu v kontejneru testu ovládacího prvku ActiveX. Tentokrát když změníte počet stran a kliknete na `Invoke`, měli byste vidět změnu ovládacího prvku hned.

V dalším kroku přidáte událost.

[Vraťte se ke kroku 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md) &#124; [ke kroku 5](../atl/adding-an-event-atl-tutorial-part-5.md) .

## <a name="see-also"></a>Viz také

[Tutoriál](../atl/active-template-library-atl-tutorial.md)<br/>
[Testování vlastností a událostí pomocí testovacího kontejneru](../mfc/testing-properties-and-events-with-test-container.md)
