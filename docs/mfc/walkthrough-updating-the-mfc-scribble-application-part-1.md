---
title: 'Návod: Aktualizace aplikace MFC Klikyháky (část 1)'
ms.date: 04/25/2019
helpviewer_keywords:
- examples [MFC], update existing application
- ribbon UI, porting to
- Office Fluent UI, porting to
- samples [MFC], update existing application
- MFC Feature Pack, update existing application
- walkthroughs [MFC], update existing application
ms.assetid: aa6330d3-6cfc-4c79-8fcb-0282263025f7
ms.openlocfilehash: 8211111e3f9e6fff2377a62689e6f8b1e0e40990
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630401"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-1"></a>Návod: Aktualizace aplikace MFC Klikyháky (část 1)

Tento návod ukazuje, jak upravit existující aplikaci knihovny MFC pro použití uživatelského rozhraní pásu karet. Sada Visual Studio podporuje pás karet Office 2007 i pás karet Windows 7 Scenic. Další informace o uživatelském rozhraní pásu karet najdete v tématu [pásy karet](/windows/win32/uxguide/cmd-ribbons).

Tento návod upraví klasickou ukázku 1,0 MFC, která vám umožní pomocí myši vytvořit čárové kresby. Tato část návodu ukazuje, jak upravit ukázku Klikyháky tak, aby se zobrazil panel pásu karet. [Část 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md) přidá na pás karet více tlačítek.

## <a name="prerequisites"></a>Požadavky

[Ukázka knihovny MFC klikyháky 1,0](https://download.microsoft.com/download/4/0/9/40946FEC-EE5C-48C2-8750-B0F8DA1C99A8/MFC/general/Scribble.zip.exe). Nápovědu k převodu do sady Visual Studio 2017 nebo novější najdete v [tématu Průvodce přenosem: Prostředí MFC –](../porting/porting-guide-mfc-scribble.md)Klikyháky

##  <a name="top"></a>Řezů

Tato část návodu obsahuje následující oddíly:

- [Nahrazení základních tříd](#replaceclass)

- [Přidání rastrových obrázků do projektu](#addbitmap)

- [Přidání prostředku pásu karet do projektu](#addribbon)

- [Vytvoření instance panelu pásu karet](#createinstance)

- [Přidání kategorie pásu karet](#addcategory)

- [Nastavení vzhledu aplikace](#setlook)

##  <a name="replaceclass"></a>Nahrazení základních tříd

Chcete-li převést aplikaci, která podporuje nabídku na aplikaci, která podporuje pás karet, je nutné z aktualizovaných základních tříd odvodit třídy aplikace, okna rámce a panely nástrojů. (Doporučujeme, abyste původní vzorek Klikyháky nezměnili. Místo toho vyčistěte projekt Klikyháky, zkopírujte ho do jiného adresáře a pak upravte kopii.)

### <a name="to-replace-the-base-classes-in-the-scribble-application"></a>Nahrazení základních tříd v aplikaci Klikyháky

1. V Klikyháky. cpp ověřte, že `CScribbleApp::InitInstance` obsahuje volání [AfxOleInit](../mfc/reference/ole-initialization.md#afxoleinit).

1. Přidejte následující kód do souboru *PCH. h* (*stdafx. h* v aplikaci Visual Studio 2017 a starší):

    ```cpp
    #include <afxcontrolbars.h>
    ```

1. V Klikyháky. h upravte definici pro `CScribbleApp` třídu tak, aby byla odvozena od [třídy CWinAppEx](../mfc/reference/cwinappex-class.md).

    ```cpp
    class CScribbleApp: public CWinAppEx
    ```

1. Klikyháky 1,0 byl napsán, když aplikace systému Windows použily soubor inicializace (. ini) k uložení dat předvoleb uživatele. Místo inicializačního souboru upravte Klikyháky a uložte předvolby uživatele v registru. Chcete-li nastavit klíč registru a základ, zadejte za `CScribbleApp::InitInstance` `LoadStdProfileSettings()` příkaz následující kód.

    ```cpp
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));
    SetRegistryBase(_T("Settings"));
    ```

1. Hlavní rámec aplikace MDI (Multiple Document Interface) již není odvozen od `CMDIFrameWnd` třídy. Místo toho je odvozen od třídy [CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md) .

    V souborech mainfrm. h a mainfrm. cpp nahraďte všechny odkazy na `CMDIFrameWnd`. `CMDIFrameWndEx`

1. V souborech childfrm. h a childfrm. cpp nahraďte `CMDIChildWnd` parametrem `CMDIChildWndEx`.

    V childfrm. soubor h, `CSplitterWnd` nahraďte `CSplitterWndEx`parametrem.

1. Upravte panely nástrojů a stavové řádky tak, aby používaly nové třídy MFC.

    V souboru mainfrm. h:

    1. Nahraďte `CToolBar` za `CMFCToolBar` (Jak velká může být moje znalostní báze?).

    1. Nahraďte `CStatusBar` za `CMFCStatusBar` (Jak velká může být moje znalostní báze?).

1. V souboru mainfrm. cpp:

    1. Nahradit `m_wndToolBar.SetBarStyle``m_wndToolBar.SetPaneStyle`

    1. Nahradit `m_wndToolBar.GetBarStyle``m_wndToolBar.GetPaneStyle`

    1. Nahradit `DockControlBar(&m_wndToolBar)``DockPane(&m_wndToolBar)`

1. V souboru ipframe. cpp přidejte následující tři řádky kódu.

    ```cpp
    m_wndToolBar.EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->DockPane(&m_wndToolBar);
    ```

1. Uložte změny a pak Sestavte a spusťte aplikaci.

##  <a name="addbitmap"></a>Přidání rastrových obrázků do projektu

Další čtyři kroky tohoto návodu vyžadují prostředky rastrového obrázku. Příslušné rastrové obrázky můžete získat různými způsoby:

- Editory [prostředků](../windows/resource-editors.md) použijte k zásobování vlastních rastrových obrázků. Případně můžete pomocí editorů prostředků sestavovat bitmapy z obrázků PNG (Portable Network Graphics), které jsou součástí sady Visual Studio, a lze je stáhnout z [knihovny imagí sady Visual Studio](https://docs.microsoft.com/visualstudio/designers/the-visual-studio-image-library).

    Uživatelské rozhraní **pásu karet** ale vyžaduje, aby některé bitmapy podporovaly průhledné obrázky. Transparentní rastrové obrázky používají 32 pixelů, kde 24 bitů určují červenou, zelenou a modrou komponentu barvy a 8 bitů definují *alfa kanál* , který určuje průhlednost barvy. Aktuální editory prostředků můžete zobrazit, ale Neupravovat rastry s 32 pixely. V důsledku toho použijte externí editor obrázků namísto editorů prostředků k manipulaci s průhlednými bitmapami.

- Zkopírujte příslušný soubor prostředků z jiné aplikace do projektu a pak importujte bitmapy z tohoto souboru.

Tento návod kopíruje soubory prostředků z příkladu vytvořeného [v návodu: Vytvoření aplikace pásu karet pomocí knihovny MFC](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md).

### <a name="to-add-bitmaps-to-the-project"></a>Přidání rastrových obrázků do projektu

1. Pomocí Průzkumníka souborů zkopírujte následující soubory. bmp z adresáře prostředků (`res`) příkladu pásu karet do adresáře prostředků (`res`) v rámci projektu Klikyháky:

   1. Zkopírujte Main. bmp do projektu Klikyháky.

   1. Zkopírujte do svého projektu Klikyháky malý. bmp a Large. bmp.

   1. Vytvořte nové kopie velkých a malých souborů. bmp a v příkladu na pásu karet uložte kopie. Přejmenujte kopie homesmall. bmp a homelarge. bmp a potom přesuňte kopie do projektu Klikyháky.

   1. Vytvořte kopii souboru Toolbar. bmp, ale kopii uložte v příkladu pásu karet. Přejmenujte kopii panelicons. bmp a pak ji přesuňte do svého projektu Klikyháky.

1. Importujte rastrový obrázek pro aplikaci knihovny MFC. V **prostředky**poklikejte na uzel **Klikyháky. RC** , dvakrát klikněte na uzel **rastrový obrázek** a potom klikněte na **Přidat prostředek**. V dialogovém okně, které se zobrazí, klikněte na **importovat**. Přejděte do `res` adresáře, vyberte soubor Main. bmp a potom klikněte na tlačítko **otevřít**.

   Hlavní rastrová obrázek. bmp obsahuje obrázek 26x26. Změňte ID rastrového obrázku na `IDB_RIBBON_MAIN`.

1. Importujte rastrové obrázky pro nabídku soubor, která je připojena k tlačítku **aplikace** .

   1. Importujte soubor Small. bmp, který obsahuje asi 16 16x16 (16x176) obrázků. Změňte ID rastrového obrázku na `IDB_RIBBON_FILESMALL`.

   > [!NOTE]
   > Vzhledem k tomu, že potřebujeme jenom prvních osm imagí (16x128), můžete volitelně oříznout šířku této bitmapy na pravé straně od 176 do 128.

   1. Naimportujte velký. bmp obsahující devět imagí 32x32 (32x288). Změňte ID rastrového obrázku na `IDB_RIBBON_FILELARGE`.

1. Importujte rastrové obrázky pro kategorie a panely pásu karet. Každá karta na panelu pásu karet je kategorie a skládá se z textového popisku a volitelného obrázku.

   1. Importujte rastrový obrázek homesmall. bmp, který obsahuje jedenáct obrázků pro rastry malých tlačítek. Změňte ID rastrového obrázku na `IDB_RIBBON_HOMESMALL`.

   1. Importujte rastr homelarge. bmp obsahující devět imagí 32x32 pro rastry velkých tlačítek. Změňte ID rastrového obrázku na `IDB_RIBBON_HOMELARGE`.

1. Import rastrových obrázků pro panely pásu karet se změněnou velikostí Tyto rastrové obrázky nebo ikony panelu se používají po operaci změny velikosti, pokud je pás karet příliš malý pro zobrazení celého panelu.

   1. Importujte rastrový obrázek panelicons. bmp, který obsahuje 8 × 16 obrázků. V okně **vlastnosti** **editoru rastrového obrázku**nastavte šířku rastrového obrázku na 64 (16x64). Změňte ID rastrového obrázku na `IDB_PANEL_ICONS`.

   > [!NOTE]
   > Vzhledem k tomu, že potřebujeme jenom první čtyři obrázky 16x16 (16x64), můžete volitelně oříznout šířku této bitmapy na pravé straně od 128 do 64.

##  <a name="addribbon"></a>Přidání prostředku pásu karet do projektu

Když převedete aplikaci, která používá nabídky, na aplikaci, která používá pás karet, nemusíte odebírat ani zakázat existující nabídky. Stačí vytvořit prostředek pásu karet, přidat tlačítka pásu karet a potom přidružit nová tlačítka k existujícím položkám nabídky. I když již nejsou nabídky viditelné, zprávy z panelu pásu karet jsou směrovány pomocí klávesových zkratek nabídek a nabídek, které fungují i nadále.

Pás karet se skládá z tlačítka **aplikace** , což je velké tlačítko v levé horní části pásu karet a jedna nebo více karet kategorií. Každá karta kategorie obsahuje jeden nebo více panelů, které fungují jako kontejnery pro tlačítka a ovládací prvky pásu karet. Následující postup ukazuje, jak vytvořit prostředek pásu karet a pak přizpůsobit tlačítko **aplikace** .

### <a name="to-add-a-ribbon-resource-to-the-project"></a>Přidání prostředku pásu karet do projektu

1. Když máte projekt Klikyháky vybraný v **Průzkumník řešení**, v nabídce **projekt** klikněte na **Přidat prostředek**.

1. V dialogovém okně **Přidat prostředek** vyberte možnost **pás karet** a pak klikněte na tlačítko **Nový**.

   Visual Studio vytvoří prostředek pásu karet a otevře ho v zobrazení Návrh. ID prostředku pásu karet je `IDR_RIBBON1`, které se zobrazí v **prostředky**. Pás karet obsahuje jednu kategorii a jeden panel.

1. Tlačítko **aplikace** můžete přizpůsobit úpravou jeho vlastností. ID zpráv, která jsou použita v tomto kódu, jsou již definována v nabídce pro Klikyháky 1,0.

1. V zobrazení Návrh klikněte na tlačítko **aplikace** a zobrazte jeho vlastnosti. Změňte hodnoty vlastností následujícím způsobem: **Obrázek** na `IDB_RIBBON_MAIN`, **Dotázat** se `File`na **klíče** na `f`, **velké obrázky** na `IDB_RIBBON_FILELARGE`a **malé obrázky** na `IDB_RIBBON_FILESMALL`.

1. Následující úpravy vytvoří nabídku, která se zobrazí, když uživatel klikne na tlačítko **aplikace** . Kliknutím na tlačítko se třemi tečkami ( **...** ) vedle **položky hlavní položky** otevřete **Editor položek**.

   1. Když je vybrané **tlačítko** typ **položky** , klikněte na **Přidat** a přidejte tlačítko. Změňte **Titulek** na `&New`, **ID** na `ID_FILE_NEW`, **Obrázek** na `0`, **Obrázek velký** na `0`.

   1. Kliknutím na tlačítko **Přidat** přidejte tlačítko. Změňte **Titulek** na `&Save`, **ID** na `ID_FILE_SAVE`, **Obrázek** na `2`a **Obrázek velký** na `2`.

   1. Kliknutím na tlačítko **Přidat** přidejte tlačítko. Změňte **Titulek** na `Save &As`, **ID** na `ID_FILE_SAVE_AS`, **Obrázek** na `3`a **Obrázek velký** na `3`.

   1. Kliknutím na tlačítko **Přidat** přidejte tlačítko. Změňte **Titulek** na `&Print`, **ID** na `ID_FILE_PRINT`, **Obrázek** na `4`a **Obrázek velký** na `4`.

   1. Změňte typ **položky** na **oddělovač** a potom klikněte na tlačítko **Přidat**.

   1. Změňte typ **položky** na **tlačítko**. Kliknutím na tlačítko **Přidat** přidejte páté tlačítko. Změňte **Titulek** na `&Close`, **ID** na `ID_FILE_CLOSE`, **Obrázek** na `5`a **Obrázek velký** na `5`.

1. Následující úpravy vytvoří podnabídku pod tlačítkem **Tisk** , kterou jste vytvořili v předchozím kroku.

   1. Klikněte na tlačítko **Tisk** , změňte typ **položky** na **popisek**a pak klikněte na tlačítko **Vložit**. Změňte **Titulek** na `Preview and print the document`.

   1. Klikněte na tlačítko **Tisk** , změňte typ **položky** na **tlačítko**a klikněte na tlačítko **Vložit**. Změňte **Titulek** na `&Print`, **ID** na `ID_FILE_PRINT`, **Obrázek** na `4`a **Obrázek velký** na `4`.

   1. Klikněte na tlačítko **Tisk** a potom kliknutím na tlačítko **Vložit** přidejte tlačítko. Změňte **Titulek** na `&Quick Print`, **ID** na `ID_FILE_PRINT_DIRECT`, **Obrázek** na `7`a **Obrázek velký** na `7`.

   1. Klikněte na tlačítko **Tisk** a potom kliknutím na tlačítko **Vložit** přidejte další tlačítko. Změňte **Titulek** na `Print Pre&view`, **ID** na `ID_FILE_PRINT_PREVIEW`, **Obrázek** na `6`a **Obrázek velký** na `6`.

   1. Nyní jste změnili **hlavní položky**. Kliknutím na **Zavřít** ukončete **Editor položek**.

1. Následující změna vytvoří tlačítko ukončit, které se zobrazí v dolní části nabídky tlačítka **aplikace** .

   1. V okně **vlastnosti** kliknutím na tlačítko se třemi tečkami ( **...** ) vedle **tlačítka** otevřete **Editor položek**.

   1. Když je vybrané **tlačítko** typ **položky** , klikněte na **Přidat** a přidejte tlačítko. Změňte **Titulek** na `E&xit`, **ID** na `ID_APP_EXIT`, **Obrázek** na `8`.

   1. Změnili jste **tlačítka**. Kliknutím na **Zavřít** ukončete **Editor položek**.

##  <a name="createinstance"></a>Vytvoření instance panelu pásu karet

Následující kroky ukazují, jak vytvořit instanci panelu pásu karet při spuštění aplikace. Chcete-li přidat panel pásu karet do aplikace, deklarujte pás karet v souboru mainfrm. h. Poté v souboru mainfrm. cpp zadejte kód pro načtení prostředku pásu karet.

### <a name="to-create-an-instance-of-the-ribbon-bar"></a>Vytvoření instance panelu pásu karet

1. V souboru mainfrm. h přidejte datový člen do oddílu `CMainFrame`Protected, definice třídy pro hlavní rámec. Tento člen je pro panel pásu karet.

    ```cpp
    // Ribbon bar for the application
    CMFCRibbonBar m_wndRibbonBar;
    ```

2. V souboru mainfrm. cpp přidejte následující kód před poslední `return` příkaz na konci `CMainFrame::OnCreate` funkce. Vytvoří instanci panelu pásu karet.

    ```cpp
    // Create the ribbon bar
    if (!m_wndRibbonBar.Create(this))
    {
        return -1;   //Failed to create ribbon bar
    }
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
    ```

##  <a name="addcategory"></a>Přizpůsobení prostředku pásu karet

Nyní, když jste vytvořili tlačítko **aplikace** , můžete přidat prvky na pás karet.

> [!NOTE]
> Tento návod používá stejnou ikonu panelu pro všechny panely. Můžete však použít další indexy seznamu obrázků k zobrazení dalších ikon.

### <a name="to-add-a-home-category-and-edit-panel"></a>Přidání kategorie domů a panelu úprav

1. Program Klikyháky vyžaduje jenom jednu kategorii. V zobrazení Návrh klikněte v **panelu nástrojů**dvakrát na **kategorie** a přidejte jednu a zobrazte její vlastnosti. Změňte hodnoty vlastností následujícím způsobem: **Titulky do** **malých** obrázků ajejich`IDB_RIBBON_HOMESMALL`obrázky `&Home` `IDB_RIBBON_HOMELARGE`

1. Každá kategorie pásu karet je uspořádána do pojmenovaných panelů. Každý panel obsahuje sadu ovládacích prvků, které dokončí související operace. Tato kategorie má jeden panel. Klikněte na **panel**a pak změňte **Titulek** na `Edit`.

1. Do panelu **úprav** přidejte tlačítko zodpovědné za vymazání obsahu dokumentu. ID zprávy pro toto tlačítko již bylo definováno v `IDR_SCRIBBTYPE` prostředku nabídky. Zadejte `Clear All` jako text tlačítka a index rastrového obrázku, který tlačítko upraví. Otevřete **panel nástrojů**a přetáhněte **tlačítko** na panel **úprav** . Klikněte na tlačítko a pak změňte **Titulek** na `Clear All`, **ID** na `ID_EDIT_CLEAR_ALL`, **index obrázku** na `0`, **velký index obrázku** na `0`.

1. Uložte změny a pak Sestavte a spusťte aplikaci. Aplikace Klikyháky by měla být zobrazena a měla by obsahovat pás karet v horní části okna, nikoli na řádku nabídek. Pás karet by měl mít jednu kategorii, **domovskou stránku**a **Home** by měl mít jeden panel, **Upravit**. Tlačítka pásu karet, která jste přidali, by měla být přidružena k existujícím obslužným rutinám událostí a tlačítka **otevřít**, **Zavřít**, **Uložit**, **Tisk**a **Vymazat** by měla fungovat podle očekávání.

##  <a name="setlook"></a>Nastavení vzhledu aplikace

*Vizuální správce* je globální objekt, který ovládá všechny kresby pro aplikaci. Vzhledem k tomu, že původní aplikace Klikyháky používá styl uživatelského rozhraní Office 2000, může aplikace vypadat jako staré. Aplikaci můžete obnovit tak, aby používala aplikaci Office 2007 Visual Manager, aby vypadala jako aplikace Office 2007.

### <a name="to-set-the-look-of-the-application"></a>Nastavení vzhledu aplikace

1. Ve funkci zadejte následující kód `return 0;` před příkazem pro změnu výchozího vizuálního manažera a stylu. `CMainFrame::OnCreate`

    ```cpp
    // Set the default manager to Office 2007
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));
    CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);
    ```

1. Uložte změny a pak Sestavte a spusťte aplikaci. Uživatelské rozhraní aplikace by mělo vypadat jako uživatelské rozhraní sady Office 2007.

## <a name="next-steps"></a>Další kroky

Upravili jste klasickou ukázku 1,0 knihovny MFC pro použití **Návrháře pásu karet**. Teď přejdete na [část 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md).

## <a name="see-also"></a>Viz také:

[Návody](../mfc/walkthroughs-mfc.md)<br/>
[Návod: Aktualizace aplikace MFC Scribble (část 2)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)
