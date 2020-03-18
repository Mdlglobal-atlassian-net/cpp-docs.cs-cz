---
title: Změna kódu kreslení (ATL – tutoriál, část 4)
ms.custom: get-started-article
ms.date: 09/26/2018
helpviewer_keywords:
- _ATL_MIN_CRT macro
ms.assetid: 08ff14e8-aa49-4139-a110-5d071939cf1e
ms.openlocfilehash: 4244dae532f467f28a5ca53e15ee601344999233
ms.sourcegitcommit: 44eeb065c3148d0484de791080a3f963109744fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79509371"
---
# <a name="changing-the-drawing-code-atl-tutorial-part-4"></a>Změna kódu kreslení (ATL – tutoriál, část 4)

Ve výchozím nastavení zobrazí kód pro kreslení ovládacího prvku čtverc a text **PolyCtl**. V tomto kroku změníte kód tak, aby zobrazoval něco zajímavějšího. Jsou zapojeny následující úlohy:

- Úprava hlavičkového souboru

- Úprava funkce `OnDraw`

- Přidání metody pro výpočet bodů mnohoúhelníku

- Inicializuje se barva výplně.

## <a name="modifying-the-header-file"></a>Úprava hlavičkového souboru

Začněte přidáním podpory pro matematické funkce `sin` a `cos`, které budou použity k výpočtu bodů mnohoúhelníku a vytvořením pole pro uložení pozic.

### <a name="to-modify-the-header-file"></a>Úprava hlavičkového souboru

1. Přidat řádek `#include <math.h>` k hornímu okraji PolyCtl. h. Horní část souboru by měla vypadat takto:

    [!code-cpp[NVC_ATL_Windowing#47](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_1.cpp)]

1. Implementujte rozhraní `IProvideClassInfo` k poskytnutí informací o metodě pro ovládací prvek přidáním následujícího kódu do PolyCtl. h. Ve třídě `CPolyCtl` nahraďte řádek:

    ```cpp
    public CComControl<CPolyCtl>
    ```

    následující adresou:

    ```cpp
    public CComControl<CPolyCtl>,
    public IProvideClassInfo2Impl<&CLSID_PolyCtl, &DIID__IPolyCtlEvents, &LIBID_PolygonLib>
    ```

    a v `BEGIN_COM_MAP(CPolyCtl)`přidejte řádky:

    ```cpp
    COM_INTERFACE_ENTRY(IProvideClassInfo)
    COM_INTERFACE_ENTRY(IProvideClassInfo2)
    ```

1. Po výpočtu bodů mnohoúhelníku budou uloženy v poli typu `POINT`, takže přidejte pole za příkaz definice `short m_nSides;` v PolyCtl. h:

    [!code-cpp[NVC_ATL_Windowing#48](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_2.h)]

## <a name="modifying-the-ondraw-method"></a>Změna metody nakreslení

Nyní byste měli upravit metodu `OnDraw` v PolyCtl. h. Kód, který budete přidávat, vytvoří nové pero a štětec, pomocí kterého se má nakreslit mnohoúhelník, a potom zavolá `Ellipse` a `Polygon` Win32 API funkce, aby se provedl skutečný výkres.

### <a name="to-modify-the-ondraw-function"></a>Úprava funkce nakreslit

1. Nahraďte existující metodu `OnDraw` v PolyCtl. h následujícím kódem:

    [!code-cpp[NVC_ATL_Windowing#49](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_3.cpp)]

## <a name="adding-a-method-to-calculate-the-polygon-points"></a>Přidání metody pro výpočet bodů mnohoúhelníku

Přidejte metodu s názvem `CalcPoints`, která bude počítat souřadnice bodů, které tvoří obvodu mnohoúhelníku. Tyto výpočty budou založené na proměnné RECT, která je předána do funkce.

### <a name="to-add-the-calcpoints-method"></a>Přidání metody CalcPoints

1. Přidejte deklaraci `CalcPoints` do části `IPolyCtl` Public třídy `CPolyCtl` v PolyCtl. h:

    [!code-cpp[NVC_ATL_Windowing#50](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_4.h)]

    Poslední část veřejného oddílu `CPolyCtl` třídy bude vypadat takto:

    [!code-cpp[NVC_ATL_Windowing#51](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_5.h)]

1. Přidejte tuto implementaci funkce `CalcPoints` na konec PolyCtl. cpp:

    [!code-cpp[NVC_ATL_Windowing#52](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_6.cpp)]

## <a name="initializing-the-fill-color"></a>Inicializuje se barva výplně.

Inicializujte `m_clrFillColor` s výchozí barvou.

### <a name="to-initialize-the-fill-color"></a>Inicializace barvy výplně

1. Použijte zelenou jako výchozí barvu přidáním tohoto řádku do konstruktoru `CPolyCtl` v PolyCtl. h:

    [!code-cpp[NVC_ATL_Windowing#53](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_7.h)]

Konstruktor teď vypadá takto:

[!code-cpp[NVC_ATL_Windowing#54](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_8.h)]

## <a name="building-and-testing-the-control"></a>Sestavování a testování ovládacího prvku

Znovu Sestavte ovládací prvek. Ujistěte se, že je soubor PolyCtl. htm zavřený, pokud je stále otevřený, a potom v nabídce **sestavení** klikněte na **sestavit mnohoúhelník** . Tuto kontrolu můžete znovu zobrazit na stránce PolyCtl. htm, ale tentokrát použijte kontejner testu ovládacího prvku ActiveX.

### <a name="to-use-the-activex-control-test-container"></a>Použití kontejneru testů ovládacího prvku ActiveX

1. Sestavte a spusťte kontejner testu ovládacího prvku ActiveX. [Ukázka TSTCON: kontejner testu ovládacího prvku ActiveX](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole/TstCon) najdete na GitHubu.

    > [!NOTE]
    > V případě chyb týkajících se `ATL::CW2AEX`v Script. cpp, nahraďte `TRACE( "XActiveScriptSite::GetItemInfo( %s )\n", pszNameT );` řádku `TRACE( "XActiveScriptSite::GetItemInfo( %s )\n", pszNameT.m_psz );`a `TRACE( "Source Text: %s\n", COLE2CT( bstrSourceLineText ) );` řádku s `TRACE( "Source Text: %s\n", bstrSourceLineText );`.<br/>
    > Pro chyby týkající se `HMONITOR`otevřete soubor StdAfx. h v projektu `TCProps` a nahraďte:
    >
    > ```
    > #ifndef WINVER
    > #define WINVER 0x0400
    > #endif
    > ```
    >
    > následující adresou:
    >
    > ```
    > #ifndef WINVER
    > #define WINVER 0x0500
    > #define _WIN32_WINNT 0x0500
    > #endif
    > ```

1. V části **kontejner testu**klikněte v nabídce **Úpravy** na možnost **Vložit nový ovládací prvek**.

1. Vyhledejte ovládací prvek, který bude nazýván `PolyCtl class`a klikněte na tlačítko **OK**. V kruhu se zobrazí zelený trojúhelník.

Zkuste změnit počet stran podle následujícího postupu. Chcete-li upravit vlastnosti pro duální rozhraní v rámci **kontejneru testů**, použijte **metody Invoke**.

### <a name="to-modify-a-controls-property-from-within-the-test-container"></a>Úprava vlastnosti ovládacího prvku v rámci kontejneru testů

1. V části **kontejner testu**klikněte v nabídce **ovládacího prvku** na **vyvolat metody** .

    Zobrazí se dialogové okno **vyvolání metody** .

1. V rozevíracím seznamu **název metody** vyberte verzi **propput** vlastnosti **strany** .

1. Zadejte `5` v poli **hodnota parametru** klikněte na **nastavit hodnotu**a klikněte na **vyvolat**.

Všimněte si, že se ovládací prvek nemění. I když jste změnili počet stran interně tím, že nastavíte `m_nSides` proměnnou, to nezpůsobí překreslení ovládacího prvku. Pokud přepnete do jiné aplikace a poté přepnete zpět do **testovacího kontejneru**, zjistíte, že ovládací prvek byl překreslen a má správný počet stran.

Chcete-li tento problém vyřešit, přidejte po nastavení počtu stran volání funkce `FireViewChange` definované v `IViewObjectExImpl`. Pokud je ovládací prvek spuštěn ve vlastním okně, `FireViewChange` volat metodu `InvalidateRect` přímo. Pokud ovládací prvek používá bez okna, bude metoda `InvalidateRect` volána v rozhraní lokality kontejneru. To vynutí, aby ovládací prvek překreslit sám sebe.

### <a name="to-add-a-call-to-fireviewchange"></a>Přidání volání do FireViewChange

1. Aktualizujte PolyCtl. cpp přidáním volání `FireViewChange` do metody `put_Sides`. Až skončíte, `put_Sides` metoda by měla vypadat takto:

    [!code-cpp[NVC_ATL_Windowing#55](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_9.cpp)]

Po přidání `FireViewChange`znovu sestavte a zkuste ovládací prvek znovu v kontejneru testu ovládacího prvku ActiveX. Tentokrát když změníte počet stran a kliknete na `Invoke`, měli byste vidět změnu ovládacího prvku hned.

V dalším kroku přidáte událost.

[Zpět ke kroku 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md) &#124; pro krok [5](../atl/adding-an-event-atl-tutorial-part-5.md)

## <a name="see-also"></a>Viz také

[Kurz](../atl/active-template-library-atl-tutorial.md)<br/>
[Testování vlastností a událostí pomocí testovacího kontejneru](../mfc/testing-properties-and-events-with-test-container.md)
