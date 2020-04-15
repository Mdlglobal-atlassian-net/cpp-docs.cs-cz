---
title: 'Návod: Aktualizace aplikace MFC Scribble (část 1)'
ms.date: 09/09/2019
helpviewer_keywords:
- examples [MFC], update existing application
- ribbon UI, porting to
- Office Fluent UI, porting to
- samples [MFC], update existing application
- MFC Feature Pack, update existing application
- walkthroughs [MFC], update existing application
ms.assetid: aa6330d3-6cfc-4c79-8fcb-0282263025f7
ms.openlocfilehash: 18803d2222c80b80ac2b1fde75b442ea1e9a89bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360248"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-1"></a>Návod: Aktualizace aplikace MFC Scribble (část 1)

Tento návod ukazuje, jak upravit existující aplikaci knihovny MFC pro použití uživatelského rozhraní pásu karet. Visual Studio podporuje pás karet office 2007 i scénický pás karet systému Windows 7. Další informace o uživatelském rozhraní pásu karet naleznete v [tématu Pásové pásy](/windows/win32/uxguide/cmd-ribbons).

Tento návod upravuje klasický ukázku knihovny MFC s čmáranice1,0, která umožňuje pomocí myši vytvářet čárové výkresy. Tato část návodu ukazuje, jak upravit ukázku klikyháky tak, aby se zoíral pruh pásu karet. [Část 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md) přidá další tlačítka na panel u pásu karet.

## <a name="prerequisites"></a>Požadavky

[Klikatý 1,0 MFC vzorek](https://download.microsoft.com/download/4/0/9/40946FEC-EE5C-48C2-8750-B0F8DA1C99A8/MFC/general/Scribble.zip.exe). Nápovědu k převodu na Visual Studio 2017 nebo novější najdete v [tématu Průvodce portováním: Klikyháky knihovny MFC](../porting/porting-guide-mfc-scribble.md).

## <a name="sections"></a><a name="top"></a>Oddíly

Tato část návodu má následující části:

- [Nahrazení základních tříd](#replaceclass)

- [Přidání bitmap do projektu](#addbitmap)

- [Přidání zdroje pásu karet do projektu](#addribbon)

- [Vytvoření instance panelu pásu karet](#createinstance)

- [Přidání kategorie pásu karet](#addcategory)

- [Nastavení vzhledu aplikace](#setlook)

## <a name="replacing-the-base-classes"></a><a name="replaceclass"></a>Nahrazení základních tříd

Chcete-li převést aplikaci, která podporuje nabídku na aplikaci, která podporuje pás karet, je nutné odvodit třídy aplikace, okna rámce a panelu nástrojů z aktualizovaných základních tříd. (Doporučujeme, abyste původní ukázku klikací položky neupravovali. Místo toho vyčistěte projekt Klikyháky, zkopírujte jej do jiného adresáře a upravte kopii.)

### <a name="to-replace-the-base-classes-in-the-scribble-application"></a>Nahrazení základních tříd v aplikaci Klikyháky

1. V scribble.cpp, `CScribbleApp::InitInstance` ověřte, že zahrnuje volání [AfxOleInit](../mfc/reference/ole-initialization.md#afxoleinit).

1. Přidejte do souboru *pch.h* následující kód (*stdafx.h* v sadě Visual Studio 2017 a starší):

    ```cpp
    #include <afxcontrolbars.h>
    ```

1. V scribble.h upravte definici třídy `CScribbleApp` tak, aby byla odvozena z [třídy CWinAppEx](../mfc/reference/cwinappex-class.md).

    ```cpp
    class CScribbleApp: public CWinAppEx
    ```

1. Klikyháky 1.0 byly napsány, když aplikace systému Windows používaly k uložení dat uživatelských předvoleb soubor inicializace (.ini). Místo inicializačního souboru upravte klikyháky tak, aby ukládaly uživatelské předvolby do registru. Chcete-li nastavit klíč registru a základní, zadejte následující kód za `CScribbleApp::InitInstance` `LoadStdProfileSettings()` příkaz.

    ```cpp
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));
    SetRegistryBase(_T("Settings"));
    ```

1. Hlavní rámec pro více dokumentů rozhraní (MDI) aplikace již `CMDIFrameWnd` není odvozen z třídy. Místo toho je odvozen z [TŘÍDY CMDIFrameWndEx.](../mfc/reference/cmdiframewndex-class.md)

    V souborech mainfrm.h a mainfrm.cpp nahraďte všechny odkazy `CMDIFrameWnd` na . `CMDIFrameWndEx`

1. V souborech childfrm.h a childfrm.cpp nahraďte souborem `CMDIChildWnd` `CMDIChildWndEx`.

    V dětské mašli. h, nahraďte soubor `CSplitterWnd` `CSplitterWndEx`.

1. Upravte panely nástrojů a stavové panely tak, aby používaly nové třídy knihovny MFC.

    V souboru mainfrm.h:

    1. Nahraďte `CToolBar` za `CMFCToolBar` (Jak velká může být moje znalostní báze?).

    1. Nahraďte `CStatusBar` za `CMFCStatusBar` (Jak velká může být moje znalostní báze?).

1. V souboru mainfrm.cpp:

    1. Nahradit `m_wndToolBar.SetBarStyle``m_wndToolBar.SetPaneStyle`

    1. Nahradit `m_wndToolBar.GetBarStyle``m_wndToolBar.GetPaneStyle`

    1. Nahradit `DockControlBar(&m_wndToolBar)``DockPane(&m_wndToolBar)`

1. V souboru ipframe.cpp zakomentujte následující tři řádky kódu.

    ```cpp
    m_wndToolBar.EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->DockPane(&m_wndToolBar);
    ```

1. Uložte změny a potom vytvořte a spusťte aplikaci.

## <a name="adding-bitmaps-to-the-project"></a><a name="addbitmap"></a>Přidání bitmap do projektu

Další čtyři kroky tohoto návodu vyžadují bitmapové prostředky. Příslušné rastrové obrázky můžete získat různými způsoby:

- Pomocí [editorů prostředků](../windows/resource-editors.md) vymýšlíte vlastní rastrové obrázky. Nebo použijte editory prostředků k sestavení bitmap z přenosných síťových grafických obrázků (.png), které jsou součástí sady Visual Studio a lze je stáhnout z [knihovny obrázků sady Visual Studio](https://docs.microsoft.com/visualstudio/designers/the-visual-studio-image-library).

    Uživatelské rozhraní **pásu karet** však vyžaduje, aby určité bitmapy podporovaly průhledné obrázky. Průhledné bitmapy používají 32bitové obrazové body, kde 24 bitů určuje červenou, zelenou a modrou složku barvy a 8 bitů definuje *alfa kanál,* který určuje průhlednost barvy. Aktuální editory prostředků mohou zobrazit bitmapy s 32bitovými obrazovými body, ale neupravovat je. V důsledku toho použijte externí editor obrázků namísto editorů prostředků k manipulaci s průhlednými bitmapami.

- Zkopírujte příslušný soubor prostředků z jiné aplikace do projektu a pak importujte bitmapy z tohoto souboru.

Tento návod zkopíruje soubory prostředků z příkladu vytvořeného v [návodu: Vytvoření aplikace pásu karet pomocí knihovny MFC](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md).

### <a name="to-add-bitmaps-to-the-project"></a>Přidání bitmap do projektu

1. Pomocí Průzkumníka souborů zkopírujte následující soubory BMP`res`z adresáře zdrojů (`res`) příkladu pásu karet do adresáře zdrojů ( ) projektu Klikyháky:

   1. Zkopírujte main.bmp do projektu Klikyháky.

   1. Zkopírujte souborsmall.bmp a filelarge.bmp do projektu Klikyháky.

   1. Vytvořte nové kopie souborů filelarge.bmp a filesmall.bmp, ale uložte je v příkladu pásu karet. Přejmenujte kopie homesmall.bmp a homelarge.bmp a potom je přesuňte do projektu Klikyháky.

   1. Vytvořte kopii souboru panelu nástrojů.bmp, ale uložte kopii v příkladu pásu karet. Přejmenujte copy panelicons.bmp a potom ji přesuňte do projektu Klikyháky.

1. Importujte bitmapu pro aplikaci knihovny MFC. V **zobrazení zdrojů**poklepejte na uzel **scribble.rc,** poklepejte na uzel **Bitová mapa** a potom klepněte na tlačítko Přidat **prostředek**. V zobrazeném dialogovém okně klepněte na **tlačítko Importovat**. Přejděte `res` do adresáře, vyberte soubor main.bmp a klepněte na tlačítko **Otevřít**.

   Bitmapa main.bmp obsahuje obraz 26x26. Změňte ID bitmapy `IDB_RIBBON_MAIN`na .

1. Importujte bitmapy pro nabídku souboru připojenou k tlačítku **Aplikace.**

   1. Importujte soubor filesmall.bmp, který obsahuje jedenáct obrázků 16x16 (16x176). Změňte ID bitmapy `IDB_RIBBON_FILESMALL`na .

   > [!NOTE]
   > Protože potřebujeme pouze prvních osm obrázků 16x16 (16x128), můžete volitelně oříznout šířku pravé strany této bitmapy od 176 do 128.

   1. Importujte filelarge.bmp, který obsahuje devět obrázků 32x32 (32x288). Změňte ID bitmapy `IDB_RIBBON_FILELARGE`na .

1. Importujte bitmapy pro kategorie a panely pásu karet. Každá karta na panelu pásu karet je kategorie a skládá se z textového popisku a volitelného obrázku.

   1. Importujte bitmapu homesmall.bmp, která obsahuje jedenáct obrázků 16x16 pro malé bitmapy tlačítek. Změňte ID bitmapy `IDB_RIBBON_HOMESMALL`na .

   1. Importujte bitmapu homelarge.bmp, která obsahuje devět obrazů 32x32 pro velké bitmapy tlačítek. Změňte ID bitmapy `IDB_RIBBON_HOMELARGE`na .

1. Importujte bitmapy pro panely pásu karet se velikostí. Tyto rastrové obrázky nebo ikony panelu se používají po operaci změny velikosti, pokud je pás karet příliš malý na zobrazení celého panelu.

   1. Importujte bitmapu panelicons.bmp, která obsahuje osm obrazů 16x16. V okně **Vlastnosti** **editoru bitmap**upravte šířku bitmapy na 64 (16x64). Změňte ID bitmapy `IDB_PANEL_ICONS`na .

   > [!NOTE]
   > Protože potřebujeme pouze první čtyři obrazy 16x16 (16x64), můžete volitelně oříznout šířku pravé strany této bitmapy od 128 do 64.

## <a name="adding-a-ribbon-resource-to-the-project"></a><a name="addribbon"></a>Přidání zdroje pásu karet do projektu

Při převodu aplikace, která používá nabídky na aplikaci, která používá pás karet, není třeba stávající nabídky odebrat ani zakázat. Stačí vytvořit zdroj pásu karet, přidat tlačítka pásu karet a potom přidružit nová tlačítka k existujícím položkám nabídky. Přestože nabídky již nejsou viditelné, zprávy z pruhu pásu karet jsou směrovány přes nabídky a zástupci nabídek nadále fungují.

Pás karet se skládá z tlačítka **Aplikace,** což je velké tlačítko na levé horní straně pásu karet a jedné nebo více karet kategorií. Každá karta kategorie obsahuje jeden nebo více panelů, které fungují jako kontejnery pro tlačítka a ovládací prvky pásu karet. Následující postup ukazuje, jak vytvořit prostředek pásu karet a potom přizpůsobit tlačítko **Aplikace.**

### <a name="to-add-a-ribbon-resource-to-the-project"></a>Přidání zdroje pásu karet do projektu

1. S vybraným projektem Klikyháky v **Průzkumníku řešení**klikněte v nabídce **Projekt** na **Přidat zdroj**.

1. V dialogovém okně **Přidat zdroj** vyberte **pás karet** a klepněte na tlačítko **Nový**.

   Visual Studio vytvoří prostředek pásu karet a otevře jej v návrhovém zobrazení. ID prostředku pásu karet je `IDR_RIBBON1`, které je zobrazeno v zobrazení **zdrojů**. Pás karet obsahuje jednu kategorii a jeden panel.

1. Tlačítko **Aplikace** můžete přizpůsobit úpravou jeho vlastností. ID zprávy, které se používají v tomto kódu jsou již definovány v nabídce klikyháky 1.0.

1. V návrhovém zobrazení zobrazte jeho vlastnosti klepnutím na tlačítko **Aplikace.** Změňte hodnoty vlastností takto: Příkaz : `f`Příkaz K příkazu **,** `IDB_RIBBON_MAIN`Příkaz k **příkazu** `File`, **Klávesy** na , **Velké obrázky** do `IDB_RIBBON_FILELARGE`a Malé **obrázky** do `IDB_RIBBON_FILESMALL`.

1. Následující změny vytvoří nabídku, která se zobrazí, když uživatel klepne na tlačítko **Aplikace.** Kliknutím na tři tečky (**...**) vedle **položky Hlavní položky** otevřete **Editor položek**.

   1. Když je vybrané **tlačítko** **Typu položky,** kliknutím na **Přidat** přidáte tlačítko. Změňte `&New` **titulek** na `ID_FILE_NEW`, **ID** na , **Obrázek** na `0`, **Obrázek velký** na `0`.

   1. Kliknutím na **Přidat** přidáte tlačítko. Změňte `&Save` **titulek** na `ID_FILE_SAVE`, `2` **ID** na , **Obrázek** na a **Velký obrázek** na `2`.

   1. Kliknutím na **Přidat** přidáte tlačítko. Změňte `Save &As` **titulek** na `ID_FILE_SAVE_AS`, `3` **ID** na , **Obrázek** na a **Velký obrázek** na `3`.

   1. Kliknutím na **Přidat** přidáte tlačítko. Změňte `&Print` **titulek** na `ID_FILE_PRINT`, `4` **ID** na , **Obrázek** na a **Velký obrázek** na `4`.

   1. Změňte typ **položky** na **Oddělovač** a klepněte na tlačítko **Přidat**.

   1. Změňte typ **položky** na **Tlačítko**. Kliknutím na **Přidat** přidáte páté tlačítko. Změňte `&Close` **titulek** na `ID_FILE_CLOSE`, `5` **ID** na , **Obrázek** na a **Velký obrázek** na `5`.

1. Následující změny vytvoří podnabídku pod tlačítkem **Tisk,** které jste vytvořili v předchozím kroku.

   1. Klepněte na tlačítko **Tisk,** změňte typ **položky** na **Popisek**a potom klepněte na **tlačítko Vložit**. Změnit **titulek** na `Preview and print the document`.

   1. Klepněte na tlačítko **Tisk,** změňte typ **položky** na **Tlačítko**a klepněte na **tlačítko Vložit**. Změňte `&Print` **titulek** na `ID_FILE_PRINT`, `4` **ID** na , **Obrázek** na a **Velký obrázek** na `4`.

   1. Klikněte na tlačítko **Tisk** a potom kliknutím na **Vložit** přidejte tlačítko. Změňte `&Quick Print` **titulek** na `ID_FILE_PRINT_DIRECT`, `7` **ID** na , **Obrázek** na a **Velký obrázek** na `7`.

   1. Klikněte na tlačítko **Tisk** a potom kliknutím na **Vložit** přidejte další tlačítko. Změňte `Print Pre&view` **titulek** na `ID_FILE_PRINT_PREVIEW`, `6` **ID** na , **Obrázek** na a **Velký obrázek** na `6`.

   1. Nyní jste upravili **hlavní položky**. Klepnutím na **tlačítko Zavřít** ukončete **Editor položek**.

1. Následující úprava vytvoří tlačítko ukončení, které se zobrazí v dolní části nabídky tlačítka **Aplikace.**

   1. V **Průzkumníku řešení**zvolte kartu **Zobrazení prostředků** .
   1. V okně **Vlastnosti** otevřete **Editor položek**klepnutím na tři tečky**vedle** **tlačítka** .

   1. Když je vybrané **tlačítko** **Typu položky,** kliknutím na **Přidat** přidáte tlačítko. Změňte `E&xit` **titulek** na `ID_APP_EXIT`, `8` **ID** na , **Obrázek** na .

   1. Upravili jste **tlačítka**. Klepnutím na **tlačítko Zavřít** ukončete **Editor položek**.

## <a name="creating-an-instance-of-the-ribbon-bar"></a><a name="createinstance"></a>Vytvoření instance panelu pásu karet

Následující kroky ukazují, jak vytvořit instanci panelu pásu karet při spuštění aplikace. Pokud chcete do aplikace přidat pruh pásu karet, deklarujte pruh pásu karet v souboru mainfrm.h. Potom v souboru mainfrm.cpp napište kód pro načtení prostředku pásu karet.

### <a name="to-create-an-instance-of-the-ribbon-bar"></a>Vytvoření instance pruhu pásu karet

1. V souboru mainfrm.h přidejte datový člen `CMainFrame`do chráněné části , definice třídy pro hlavní rámec. Tento člen je pro pás karet.

    ```cpp
    // Ribbon bar for the application
    CMFCRibbonBar m_wndRibbonBar;
    ```

2. Do souboru mainfrm.cpp přidejte následující `return` kód před konečný `CMainFrame::OnCreate` příkaz na konci funkce. Vytvoří instanci pruhu pásu karet.

    ```cpp
    // Create the ribbon bar
    if (!m_wndRibbonBar.Create(this))
    {
        return -1;   //Failed to create ribbon bar
    }
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
    ```

## <a name="customizing-the-ribbon-resource"></a><a name="addcategory"></a>Přizpůsobení zdroje pásu karet

Teď, když jste vytvořili tlačítko **Aplikace,** můžete na pás karet přidat prvky.

> [!NOTE]
> Tento návod používá stejnou ikonu panelu pro všechny panely. K zobrazení dalších ikon však můžete použít jiné indexy seznamu obrázků.

### <a name="to-add-a-home-category-and-edit-panel"></a>Přidání kategorie Domů a panel Úpravy

1. Program Klikyháky vyžaduje pouze jednu kategorii. V návrhovém zobrazení v **panelu nástrojů**poklepejte na **kategorii,** chcete-li přidat jednu a zobrazit její vlastnosti. Změňte hodnoty vlastností takto: **Titulek** `&Home`do `IDB_RIBBON_HOMESMALL`, Velké **obrázky** na `IDB_RIBBON_HOMELARGE`, Malé **obrázky** na .

1. Každá kategorie pásu karet je uspořádána do pojmenovaných panelů. Každý panel obsahuje sadu ovládacích prvků, které dokončí související operace. Tato kategorie má jeden panel. Klepněte na **panel**a `Edit`změňte **možnost Titulek** na .

1. Do panelu **Úpravy** přidejte tlačítko odpovědné za vymazání obsahu dokumentu. ID zprávy pro toto tlačítko již `IDR_SCRIBBTYPE` bylo definováno v prostředku nabídky. Určete `Clear All` jako text tlačítka a index bitmapy, která zdobí tlačítko. Otevřete **panel nástrojů**a přetáhněte **tlačítko** do panelu **Úpravy.** Klepněte na tlačítko a `Clear All`změňte **položku Titulek** na , `0` **ID** na `ID_EDIT_CLEAR_ALL`, Index **obrázků** na `0`, Index velkých **obrázků** na .

1. Uložte změny a potom vytvořte a spusťte aplikaci. Aplikace Klikyháky by měla být zobrazena a měla by mít pruh pásu karet v horní části okna namísto panelu nabídek. Pruh pásu karet by měl mít jednu kategorii, **domovská**stránka a **domovská stránka** by měla mít jeden panel **Úpravy**. Přidaná tlačítka pásu karet by měla být přidružena k existujícím obslužným rutinám událostí a tlačítka **Otevřít**, **Zavřít**, **Uložit**, **Tisk**a **Vymazat vše** by měla fungovat podle očekávání.

## <a name="setting-the-look-of-the-application"></a><a name="setlook"></a>Nastavení vzhledu aplikace

*Vizuální manažer* je globální objekt, který řídí veškerý výkres pro aplikaci. Vzhledem k tomu, že původní aplikace Klikyháky používá styl uživatelského rozhraní sady Office 2000 ( UI), může aplikace vypadat staromódní. Aplikaci můžete obnovit tak, aby používala vizuální správce sady Office 2007 tak, aby se podobala aplikaci sady Office 2007.

### <a name="to-set-the-look-of-the-application"></a>Nastavení vzhledu aplikace

1. Do `CMainFrame::OnCreate` funkce zadejte před `return 0;` příkaz následující kód, který chcete změnit výchozí vizuální manažer a styl.

    ```cpp
    // Set the default manager to Office 2007
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));
    CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);
    ```

1. Uložte změny a potom vytvořte a spusťte aplikaci. Použití aplikace by se mělo podobat uj.u.

## <a name="next-steps"></a>Další kroky

Upravili jste klasickou ukázku knihovny MFC 1.0 tak, aby používala **Návrhář pásu karet**. Nyní přejděte k [části 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md).

## <a name="see-also"></a>Viz také

[Postupy](../mfc/walkthroughs-mfc.md)<br/>
[Návod: Aktualizace aplikace MFC Scribble (část 2)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)
