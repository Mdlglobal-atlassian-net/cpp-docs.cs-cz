---
title: 'Návod: Aktualizace aplikace MFC Scribble (část 1)'
ms.date: 04/25/2019
helpviewer_keywords:
- examples [MFC], update existing application
- ribbon UI, porting to
- Office Fluent UI, porting to
- samples [MFC], update existing application
- MFC Feature Pack, update existing application
- walkthroughs [MFC], update existing application
ms.assetid: aa6330d3-6cfc-4c79-8fcb-0282263025f7
ms.openlocfilehash: a12c2bd2c1c1963630a1bd74b56f2c832573cc94
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450511"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-1"></a>Návod: Aktualizace aplikace MFC Scribble (část 1)

Tento návod ukazuje, jak změnit existující aplikaci MFC použít uživatelské rozhraní pásu karet. Visual Studio podporuje pásu karet Office 2007 a na Windows 7 Scenic pásu karet. Další informace o uživatelském rozhraní pásu karet najdete v tématu [pásů karet](/windows/desktop/uxguide/cmd-ribbons).

Tento názorný postup upravuje classic vzorek Scribble 1.0 MFC, který vám umožní používat myš kreslit čáry. Tato část návodu ukazuje, jak upravit ukázky Scribble tak, aby zobrazil panel pásu karet. [Část 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md) přidá další tlačítka na panel pásu karet.

## <a name="prerequisites"></a>Požadavky

[Vzorek Scribble 1.0 MFC](https://download.microsoft.com/download/4/0/9/40946FEC-EE5C-48C2-8750-B0F8DA1C99A8/MFC/general/Scribble.zip.exe). Nápovědu k převodu do sady Visual Studio 2017 nebo později, naleznete v tématu [portování průvodce: MFC Scribble](../porting/porting-guide-mfc-scribble.md).

##  <a name="top"></a> Oddíly

Tato část návodu obsahuje následující oddíly:

- [Nahrazení základní třídy](#replaceclass)

- [Přidávání bitmap do projektu](#addbitmap)

- [Přidání prostředku pásu karet do projektu](#addribbon)

- [Vytvoření Instance na pásu karet](#createinstance)

- [Přidáním kategorie pásu karet](#addcategory)

- [Nastavení vzhledu aplikace](#setlook)

##  <a name="replaceclass"></a> Nahrazení základní třídy

Převést aplikaci, která podporuje nabídky k aplikaci, která podporuje pás karet, musí aplikace, okno rámce a nástrojů třídy odvozeny od aktualizace základní třídy. (My Navrhujeme, že nebudete muset měnit původní ukázky Scribble pomocí. Místo toho vyčistěte projekt Scribble, zkopírujte ho do jiného adresáře a potom upravte kopii.)

### <a name="to-replace-the-base-classes-in-the-scribble-application"></a>Chcete-li nahradit základní třídy v aplikaci Scribble

1. V scribble.cpp, ověřte, zda `CScribbleApp::InitInstance` obsahuje volání [AfxOleInit](../mfc/reference/ole-initialization.md#afxoleinit).

1. Přidejte následující kód do souboru stdafx.h.

    ```cpp
    #include <afxcontrolbars.h>
    ```

1. V scribble.h, změňte definici pro `CScribbleApp` třídy, takže je odvozena z [CWinAppEx – třída](../mfc/reference/cwinappex-class.md).

    ```cpp
    class CScribbleApp: public CWinAppEx
    ```

1. Scribble 1.0 byla zapsána, pokud aplikace Windows použít soubor inicializace (.ini) k uložení dat předvoleb uživatele. Místo inicializačního souboru upravte Scribble k ukládání uživatelských předvoleb v registru. Pokud chcete nastavit klíč registru a základní, zadejte následující kód v `CScribbleApp::InitInstance` po `LoadStdProfileSettings()` příkazu.

    ```cpp
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));
    SetRegistryBase(_T("Settings"));
    ```

1. Hlavního rámce pro aplikace (MDI interface) více dokumentů už pochází z `CMDIFrameWnd` třídy. Místo toho je odvozen z [CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md) třídy.

    V souborech mainfrm.h a mainfrm.cpp nahradit všechny odkazy na `CMDIFrameWnd` s `CMDIFrameWndEx`.

1. Nahradit v souborech childfrm.h a childfrm.cpp `CMDIChildWnd` s `CMDIChildWndEx`.

    V childfrm. h souboru nahraďte `CSplitterWnd` s `CSplitterWndEx`.

1. Upravte panelů nástrojů a stavové řádky používat nové třídy knihovny MFC.

    V souboru mainfrm.h:

    1. Nahraďte `CToolBar` za `CMFCToolBar` (Jak velká může být moje znalostní báze?).

    1. Nahraďte `CStatusBar` za `CMFCStatusBar` (Jak velká může být moje znalostní báze?).

1. V souboru mainfrm.cpp:

    1. Nahraďte `m_wndToolBar.SetBarStyle` s `m_wndToolBar.SetPaneStyle`

    1. Nahraďte `m_wndToolBar.GetBarStyle` s `m_wndToolBar.GetPaneStyle`

    1. Nahraďte `DockControlBar(&m_wndToolBar)` s `DockPane(&m_wndToolBar)`

1. V souboru ipframe.cpp okomentujte následující tři řádky kódu.

    ```cpp
    m_wndToolBar.EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->DockPane(&m_wndToolBar);
    ```

1. Uložte změny a potom sestavíte a spustíte aplikaci.

##  <a name="addbitmap"></a> Přidávání bitmap do projektu

Další čtyři kroky tohoto názorného postupu vyžadovat prostředky rastrového obrázku. Získáte příslušné rastrové obrázky různými způsoby:

- Použití [editory prostředků](../windows/resource-editors.md) vytvářet vlastní rastrových obrázků. Nebo můžete sestavit rastrové obrázky z imagí portable network graphics (.png), které jsou součástí sady Visual Studio a můžete ho stáhnout z editory prostředků [knihovna obrázků sady Visual Studio](https://docs.microsoft.com/visualstudio/designers/the-visual-studio-image-library).

    Ale **pásu karet** uživatelského rozhraní vyžaduje, aby určité rastrové obrázky podporující průhledné obrázky. Transparentní rastrové obrázky použijte 32bitový pixelů, kde 24 bitů komponenty červené, zelené a modré barvy a určete 8 bitů *alfa kanál* , který určuje průhlednost barvy. Aktuální editory prostředků můžete zobrazit, ale nemohou měnit rastrové obrázky s 32-bit pixelů. V důsledku toho pomocí editoru obrázků externí místo editory prostředků pro manipulaci s transparentní rastrové obrázky.

- Zkopírujte si soubor odpovídající prostředek z jiné aplikace do projektu a poté importovat bitmapy z tohoto souboru.

Tento podrobný postup kopíruje soubory prostředků z příkladu, vytvoří v [názorný postup: Vytvoření jednoduché aplikace pásu karet pomocí knihovny MFC](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md).

### <a name="to-add-bitmaps-to-the-project"></a>Chcete-li přidat rastrové obrázky do projektu

1. Zkopírujte následující soubory .bmp z adresáře prostředků pomocí Průzkumníka souborů (`res`). Příklad pro adresář prostředků pásu karet (`res`) Scribble projektu:

   1. Zkopírujte main.bmp Scribble projektu.

   1. Zkopírujte filesmall.bmp a filelarge.bmp Scribble projektu.

   1. Vytvořte nové kopie souborů filelarge.bmp a filesmall.bmp, ale ukládat kopie v příkladu pásu karet. Přejmenovat homesmall.bmp kopie a homelarge.bmp a poté přesuňte do projektu Scribble kopie.

   1. Vytvořte kopii souboru Toolbar.bmp s tím, ale uložit kopii v příkladu pásu karet. Přejmenovat panelicons.bmp kopie a poté přesuňte kopii do svého projektu Scribble.

1. Importujte rastrového obrázku pro aplikaci knihovny MFC. V **zobrazení prostředků**, dvakrát klikněte **scribble.rc** uzlu, dvakrát klikněte na **rastrový obrázek** uzel a potom klikněte na **přidat prostředek**. V dialogovém okně, které se zobrazí, klikněte na tlačítko **Import**. Přejděte `res` adresář, vyberte soubor main.bmp a potom klikněte na tlačítko **otevřít**.

   Rastrový obrázek main.bmp obsahuje bitovou kopii 26 × 26. Změna ID rastrový obrázek pro `IDB_RIBBON_MAIN`.

1. Rastrové obrázky pro nabídky soubor, který je připojen k importu **aplikace** tlačítko.

   1. Importovat soubor filesmall.bmp, který obsahuje jedenáct 16 x 16 (16 × 176) bitové kopie. Změna ID rastrový obrázek pro `IDB_RIBBON_FILESMALL`.

   > [!NOTE]
   > Protože potřebujeme pouze prvních osm 16 x 16 imagí (16 × 128), může volitelně oříznout šířku na pravé straně tento rastrový obrázek z 176 do 128.

   1. Importovat filelarge.bmp, který obsahuje devět 32 x 32 (32 x 288) bitové kopie. Změna ID rastrový obrázek pro `IDB_RIBBON_FILELARGE`.

1. Importujte bitmapy pro kategorie pásu karet a panelů. Každou kartu na panelu pásu karet je kategorie a se skládá z textový popisek a volitelné bitovou kopii.

   1. Importujte homesmall.bmp rastrový obrázek, který obsahuje jedenáct 16 x 16 bitových kopií pro malé tlačítko rastrových obrázků. Změna ID rastrový obrázek pro `IDB_RIBBON_HOMESMALL`.

   1. Importujte homelarge.bmp rastrový obrázek, který obsahuje devět 32 x 32 bitové kopie pro velké tlačítko bitmapy. Změna ID rastrový obrázek pro `IDB_RIBBON_HOMELARGE`.

1. Importovat bitmapy pro panely změněnou pásu karet. Tyto rastrové obrázky nebo panel ikon, se použijí po operaci změny velikosti, pokud je příliš malá pro zobrazení na celou panelu pásu karet.

   1. Importujte panelicons.bmp rastrový obrázek, který obsahuje osm 16 x 16 imagí. V **vlastnosti** okno **editoru rastrových obrázků**, umožňuje upravit šířku rastrového obrázku na 64 (16 x 64). Změna ID rastrový obrázek pro `IDB_PANEL_ICONS`.

   > [!NOTE]
   > Protože potřebujeme jenom první čtyři 16 x 16 imagí (16 x 64), může volitelně oříznout šířku na pravé straně tento rastrový obrázek z 128 až 64.

##  <a name="addribbon"></a> Přidání prostředku pásu karet do projektu

Můžete převést aplikaci, která používá nabídky k aplikaci, která používá pás karet, není nutné odebrat nebo zakázat stávající nabídky. Stačí vytvořit prostředek pásu karet, přidejte tlačítek na pásu karet a nová tlačítka přidružit existující položky nabídky. I když již nejsou viditelné v nabídkách, zprávy z pásu karet jsou směrovány prostřednictvím nabídky a nabídky zástupců pokračovat v práci.

Se skládá z pásu karet **aplikace** tlačítko, které je velké tlačítko v levé horní části pásu karet a jednu nebo více karet kategorie. Každá karta kategorie obsahuje jednu nebo více panelů, které fungují jako kontejnery pro tlačítek na pásu karet a ovládacích prvků. Následující postup ukazuje, jak vytvořit prostředek pásu karet a potom přizpůsobit **aplikace** tlačítko.

### <a name="to-add-a-ribbon-resource-to-the-project"></a>Chcete-li přidat prostředek pásu karet do projektu

1. S Scribble projekt vybraný v **Průzkumníka řešení**v **projektu** nabídky, klikněte na tlačítko **přidat prostředek**.

1. V **přidat prostředek** dialogu **pásu karet** a potom klikněte na tlačítko **nový**.

   Visual Studio vytvoří prostředek pásu karet a otevře v zobrazení Návrh. ID prostředku pásu karet je `IDR_RIBBON1`, který se zobrazí v **zobrazení prostředků**. Na pásu karet obsahuje jednu kategorii a jeden panel.

1. Můžete přizpůsobit **aplikace** tlačítko úpravou jeho vlastností. ID zprávy, které se používají v tomto kódu jsou již definovány v nabídce Scribble 1.0.

1. V návrhovém zobrazení, klikněte na tlačítko **aplikace** tlačítko a zobrazte její vlastnosti. Změňte hodnoty vlastností následujícím způsobem: **Image** k `IDB_RIBBON_MAIN`, **výzvy** k `File`, **klíče** k `f`, **Large Images** k `IDB_RIBBON_FILELARGE`a **Small Images** k `IDB_RIBBON_FILESMALL`.

1. Vytvořit následující změny v nabídce, která se zobrazí, když uživatel klikne **aplikace** tlačítko. Klikněte na tlačítko se třemi tečkami ( **...** ) vedle položky **položky hlavní** otevřít **Editor položek**.

   1. S **položky** typ **tlačítko** vybraný, klikněte na tlačítko **přidat** přidáte tlačítko. Změna **titulek** k `&New`, **ID** k `ID_FILE_NEW`, **Image** k `0`, **velký obrázek** k `0`.

   1. Klikněte na tlačítko **přidat** přidáte tlačítko. Změna **titulek** k `&Save`, **ID** k `ID_FILE_SAVE`, **Image** k `2`, a **velký obrázek** k `2`.

   1. Klikněte na tlačítko **přidat** přidáte tlačítko. Změna **titulek** k `Save &As`, **ID** k `ID_FILE_SAVE_AS`, **Image** k `3`, a **velký obrázek** k `3`.

   1. Klikněte na tlačítko **přidat** přidáte tlačítko. Změna **titulek** k `&Print`, **ID** k `ID_FILE_PRINT`, **Image** k `4`, a **velký obrázek** k `4`.

   1. Změnit **položky** typ, který **oddělovač** a potom klikněte na tlačítko **přidat**.

   1. Změnit **položky** typ, který **tlačítko**. Klikněte na tlačítko **přidat** páté tlačítko Přidat. Změna **titulek** k `&Close`, **ID** k `ID_FILE_CLOSE`, **Image** k `5`, a **velký obrázek** k `5`.

1. Následující změny Vytvoření podnabídky pod **tisk** tlačítko, které jste vytvořili v předchozím kroku.

   1. Klikněte na tlačítko **tisk** tlačítko, změňte **položky** typ, který **popisek**a potom klikněte na tlačítko **vložit**. Změna **titulek** k `Preview and print the document`.

   1. Klikněte na tlačítko **tisk** tlačítko, změňte **položky** typ, který **tlačítko**a klikněte na tlačítko **vložit**. Změna **titulek** k `&Print`, **ID** k `ID_FILE_PRINT`, **Image** k `4`, a **velký obrázek** k `4`.

   1. Klikněte na tlačítko **tisk** tlačítko a pak klikněte na tlačítko **vložit** přidáte tlačítko. Změna **titulek** k `&Quick Print`, **ID** k `ID_FILE_PRINT_DIRECT`, **Image** k `7`, a **velký obrázek** k `7`.

   1. Klikněte na tlačítko **tisk** tlačítko a pak klikněte na tlačítko **vložit** k přidání dalšího tlačítka. Změna **titulek** k `Print Pre&view`, **ID** k `ID_FILE_PRINT_PREVIEW`, **Image** k `6`, a **velký obrázek** k `6`.

   1. Nyní jste upravili **položky hlavní**. Klikněte na tlačítko **Zavřít** ukončíte **Editor položek**.

1. Následující změny vytvoří ukončení tlačítko, které se zobrazí v dolní části **aplikace** tlačítka nabídky.

   1. V **vlastnosti** okna, klikněte na tlačítko se třemi tečkami ( **...** ) vedle položky **tlačítko** otevřít **Editor položek**.

   1. S **položky** typ **tlačítko** vybraný, klikněte na tlačítko **přidat** přidáte tlačítko. Změna **titulek** k `E&xit`, **ID** k `ID_APP_EXIT`, **Image** k `8`.

   1. Jsme změnili **tlačítka**. Klikněte na tlačítko **Zavřít** ukončíte **Editor položek**.

##  <a name="createinstance"></a> Vytvoření Instance na pásu karet

Následující kroky ukazují, jak vytvořit instance na pásu karet při spuštění aplikace. Chcete-li přidat panel pásu karet do aplikace, deklarujte na pásu karet v souboru mainfrm.h. V souboru mainfrm.cpp napište kód pro načtení prostředku pásu karet.

### <a name="to-create-an-instance-of-the-ribbon-bar"></a>K vytvoření instance na pásu karet

1. V souboru mainfrm.h přidat datový člen chráněné části `CMainFrame`, definice třídy pro hlavního rámce. Tento člen je panel pásu karet.

    ```cpp
    // Ribbon bar for the application
    CMFCRibbonBar m_wndRibbonBar;
    ```

2. V souboru mainfrm.cpp, přidejte následující kód před finální `return` příkaz na konci `CMainFrame::OnCreate` funkce. Vytvoří instanci na pásu karet.

    ```cpp
    // Create the ribbon bar
    if (!m_wndRibbonBar.Create(this))
    {
        return -1;   //Failed to create ribbon bar
    }
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
    ```

##  <a name="addcategory"></a> Přizpůsobení prostředek pásu karet

Teď, když jste vytvořili **aplikace** tlačítko, můžete přidat prvky na pás karet.

> [!NOTE]
> Tento návod používá stejné panelu ikonu pro všechny panely. Ale můžete použít jiných indexů obrázek seznamu zobrazíte další ikony.

### <a name="to-add-a-home-category-and-edit-panel"></a>Přidat kategorii domovské a upravit panel

1. Scribble program vyžaduje pouze jednu kategorii. V okně návrhu v **nástrojů**, dvakrát klikněte na panel **kategorie** ho přidejte a zobrazit její vlastnosti. Změňte hodnoty vlastností následujícím způsobem: **Titulek** k `&Home`, **Large Images** k `IDB_RIBBON_HOMELARGE`, **Small Images** k `IDB_RIBBON_HOMESMALL`.

1. Každá kategorie pásu karet je uspořádaný do pojmenované panelů. Každý panel obsahuje sadu ovládacích prvků tohoto dokončení souvisejících operací. Tato kategorie obsahuje jeden panel. Klikněte na tlačítko **Panel**a potom změňte **titulek** k `Edit`.

1. Chcete **upravit** panelu, přidejte tlačítko za vymazat obsah dokumentu. ID zprávy pro toto tlačítko je již definována v `IDR_SCRIBBTYPE` nabídce prostředků. Zadejte `Clear All` jako text tlačítka a index rastrový obrázek, který upraví na tlačítko. Otevřít **nástrojů**a pak přetáhněte **tlačítko** k **upravit** panelu. Klikněte na tlačítko a pak změňte **titulek** k `Clear All`, **ID** k `ID_EDIT_CLEAR_ALL`, **Index bitové kopie** k `0`, **Large Image Index**  k `0`.

1. Uložte změny a potom sestavíte a spustíte aplikaci. Scribble aplikace má být zobrazena, a měl by mít panel pásu karet v horní části okna namísto řádku nabídek. Na pásu karet by měl mít jednu kategorii **Domů**, a **Domů** by měl mít jeden panel **upravit**. Tlačítka pásu karet, který jste přidali by měly být přidruženy s existující obslužné rutiny událostí a **otevřít**, **Zavřít**, **Uložit**, **tisk**, a **Vymazat vše** tlačítka by měla fungovat podle očekávání.

##  <a name="setlook"></a> Nastavení vzhledu aplikace

A *správce vzhledu* je globální objekt, který určuje všechny vykreslování pro aplikaci. Protože původní aplikace Scribble používá styl uživatelského rozhraní (UI) Office 2000, aplikace může vypadat zastaralý. Můžete obnovit aplikaci, aby používala správce vzhledu Office 2007, tak, aby se podobá aplikaci sady Office 2007.

### <a name="to-set-the-look-of-the-application"></a>K nastavení vzhledu aplikace

1. V `CMainFrame::OnCreate` funkci, zadejte následující kód před `return 0;` prohlášení, chcete-li změnit výchozí správce vzhledu a vizuální styl.

    ```cpp
    // Set the default manager to Office 2007
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));
    CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);
    ```

1. Uložte změny a potom sestavíte a spustíte aplikaci. V uživatelském rozhraní aplikace by měla vypadat podobně jako uživatelského rozhraní sady Office 2007.

## <a name="next-steps"></a>Další kroky

Změnili jste classic vzorek Scribble 1.0 MFC používat **Návrháře pásu karet**. Teď přejděte na [2. část](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md).

## <a name="see-also"></a>Viz také:

[Návody](../mfc/walkthroughs-mfc.md)<br/>
[Návod: Aktualizace aplikace MFC Scribble (část 2)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)
