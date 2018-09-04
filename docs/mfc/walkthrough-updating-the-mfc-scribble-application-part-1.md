---
title: 'Návod: Aktualizace aplikace MFC Scribble (část 1) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- examples [MFC], update existing application
- ribbon UI, porting to
- Office Fluent UI, porting to
- samples [MFC], update existing application
- MFC Feature Pack, update existing application
- walkthroughs [MFC], update existing application
ms.assetid: aa6330d3-6cfc-4c79-8fcb-0282263025f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ce50d2c70107b4c88f223e32fdd8cc083df38840
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43685542"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-1"></a>Návod: Aktualizace aplikace MFC Scribble (část 1)

Tento návod ukazuje, jak změnit existující aplikaci MFC použít uživatelské rozhraní pásu karet. Visual Studio podporuje pásu karet Office 2007 a na Windows 7 Scenic pásu karet. Další informace o uživatelském rozhraní pásu karet najdete v tématu [pásů karet](/windows/desktop/uxguide/cmd-ribbons).

Tento názorný postup upravuje classic vzorek Scribble 1.0 MFC, který vám umožní používat myš kreslit čáry. Tato část návodu ukazuje, jak upravit ukázky Scribble tak, aby zobrazil panel pásu karet. [Část 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md) přidá další tlačítka na panel pásu karet.

## <a name="prerequisites"></a>Požadavky

[Visual C++ – ukázky](../visual-cpp-samples.md)

[Visual C++ – ukázky](../visual-cpp-samples.md)

##  <a name="top"></a> Oddíly

Tato část návodu obsahuje následující oddíly:

- [Nahrazení základní třídy](#replaceclass)

- [Přidávání bitmap do projektu](#addbitmap)

- [Přidání prostředku pásu karet do projektu](#addribbon)

- [Vytvoření Instance na pásu karet](#createinstance)

- [Přidáním kategorie pásu karet](#addcategory)

- [Nastavení vzhledu aplikace](#setlook)

##  <a name="replaceclass"></a> Nahrazení základní třídy

Převést aplikaci, která podporuje nabídky k aplikaci, která podporuje pás karet, musí aplikace, okno rámce a nástrojů třídy odvozeny od aktualizace základní třídy. (Doporučujeme, že jste není upravit původní ukázky Scribble; místo toho, vyčistěte projekt Scribble, zkopírujte ho do jiného adresáře a upravte kopii.)

### <a name="to-replace-the-base-classes-in-the-scribble-application"></a>Chcete-li nahradit základní třídy v aplikaci Scribble

1. V scribble.cpp, ověřte, zda `CScribbleApp::InitInstance` obsahuje volání [AfxOleInit](../mfc/reference/ole-initialization.md#afxoleinit).

2. Přidejte následující kód do souboru stdafx.h.

    ```cpp
    #include <afxcontrolbars.h>
    ```

3. V scribble.h, změňte definici pro `CScribbleApp` třídy, takže je odvozena z [CWinAppEx – třída](../mfc/reference/cwinappex-class.md).

    ```cpp
    class CScribbleApp: public CWinAppEx
    ```

4. Scribble 1.0 byla zapsána, pokud aplikace Windows použít soubor inicializace (.ini) k uložení dat předvoleb uživatele. Místo inicializačního souboru upravte Scribble k ukládání uživatelských předvoleb v registru. Pokud chcete nastavit klíč registru a základní, zadejte následující kód v `CScribbleApp::InitInstance` po `LoadStdProfileSettings()` příkazu.

    ```cpp
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));
    SetRegistryBase(_T("Settings"));
    ```

5. Hlavního rámce pro aplikace (MDI interface) více dokumentů už pochází z `CMDIFrameWnd` třídy. Místo toho je odvozen z [CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md) třídy.

     V souborech mainfrm.h a mainfrm.cpp nahradit všechny odkazy na `CMDIFrameWnd` s `CMDIFrameWndEx`.

6. Nahradit v souborech childfrm.h a childfrm.cpp `CMDIChildWnd` s `CMDIChildWndEx`.

     V childfrm. h souboru nahraďte `CSplitterWnd` s `CSplitterWndEx`.

7. Upravte panelů nástrojů a stavové řádky používat nové třídy knihovny MFC.

     V souboru mainfrm.h:

    1. Nahraďte `CToolBar` s `CMFCToolBar`.

    2. Nahraďte `CStatusBar` s `CMFCStatusBar`.

8. V souboru mainfrm.cpp:

    1. Nahraďte `m_wndToolBar.SetBarStyle` s `m_wndToolBar.SetPaneStyle`

    2. Nahraďte `m_wndToolBar.GetBarStyle` s `m_wndToolBar.GetPaneStyle`

    3. Nahraďte `DockControlBar(&m_wndToolBar)` s `DockPane(&m_wndToolBar)`

9. V souboru ipframe.cpp okomentujte následující tři řádky kódu.

    ```cpp
    m_wndToolBar.EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->DockPane(&m_wndToolBar);
    ```

10. Pokud chcete staticky propojit aplikace, přidejte následující kód na začátek souboru prostředků (.rc) projektu.

    ```cpp
    #include "afxribbon.rc"
    ```

     Soubor afxribbon.rc obsahuje prostředky, které jsou požadovány v době běhu. [Průvodce aplikací knihovny MFC](../mfc/reference/mfc-application-wizard.md) zahrnuje tento soubor automaticky při vytvoření aplikace.

11. Uložte změny a potom sestavíte a spustíte aplikaci.

[[Oddíly](#top)]

##  <a name="addbitmap"></a> Přidávání bitmap do projektu

Další čtyři kroky tohoto názorného postupu vyžadovat prostředky rastrového obrázku. Můžete získat příslušné rastrové obrázky různými způsoby:

- Použití [editory prostředků](../windows/resource-editors.md) vytvářet vlastní rastrových obrázků. Nebo použijte editory prostředků sestavení rastrové obrázky z imagí portable network graphics (.png), které jsou součástí sady Visual Studio. Tyto Image jsou v `VS2008ImageLibrary` adresáře.

     Uživatelské rozhraní pásu karet, ale vyžaduje, aby podporoval určité rastrové obrázky průhledné obrázky. Transparentní rastrové obrázky použijte 32bitový pixelů, kde 24 bitů komponenty červené, zelené a modré barvy a určete 8 bitů *alfa kanál* , který určuje průhlednost barvy. Aktuální editory prostředků můžete zobrazit, ale nemohou měnit rastrové obrázky s 32-bit pixelů. V důsledku toho pomocí editoru obrázků externí místo editory prostředků pro manipulaci s transparentní rastrové obrázky.

- Zkopírujte si soubor odpovídající prostředek z jiné aplikace do projektu a poté importovat bitmapy z tohoto souboru.

Tento podrobný postup kopíruje soubory prostředků z aplikace v adresáři ukázky.

### <a name="to-add-bitmaps-to-the-project"></a>Chcete-li přidat rastrové obrázky do projektu

1. Zkopírujte následující soubory .bmp z adresáře prostředků pomocí Průzkumníka souborů (`res`) z vzorek RibbonGadgets:

   1. Zkopírujte main.bmp Scribble projektu.

   2. Zkopírujte filesmall.bmp a filelarge.bmp Scribble projektu.

   3. Vytvořte nové kopie souborů filelarge.bmp a filesmall.bmp, ale v vzorek RibbonGadgets ukládat kopie. Přejmenovat homesmall.bmp kopie a homelarge.bmp a poté přesuňte do projektu Scribble kopie.

   4. Vytvořte kopii souboru Toolbar.bmp s tím, ale uložit kopii vzorek RibbonGadgets. Přejmenovat panelicons.bmp kopie a poté přesuňte kopii do svého projektu Scribble.

2. Importujte rastrového obrázku pro aplikaci knihovny MFC. V **zobrazení prostředků**, dvakrát klikněte **scribble.rc** uzlu, dvakrát klikněte na **rastrový obrázek** uzel a potom klikněte na **přidat prostředek**. V dialogovém okně, které se zobrazí, klikněte na tlačítko **Import**. Přejděte `res` adresář, vyberte soubor main.bmp a potom klikněte na tlačítko **otevřít**.

   Rastrový obrázek main.bmp obsahuje bitovou kopii 26 × 26. Změňte ID rastrového obrázku nastaven na IDB_RIBBON_MAIN.

3. Importujte bitmapy pro nabídky soubor, který je připojen k tlačítku aplikace.

   1. Importovat soubor filesmall.bmp, který obsahuje deset 16 x 16 (16 × 160) bitové kopie. Protože potřebujeme imagí pouze osm 16 x 16 (16 × 128), použijte **zobrazení prostředků** změnit šířku tento rastrový obrázek z 160 na 128. Změňte ID rastrového obrázku nastaven na IDB_RIBBON_FILESMALL.

   2. Importovat filelarge.bmp, který obsahuje osm 32 x 32 (32 x 256) bitové kopie. Změňte ID rastrového obrázku nastaven na IDB_RIBBON_FILELARGE.

4. Importujte bitmapy pro kategorie pásu karet a panelů. Každou kartu na panelu pásu karet je kategorie a se skládá z textový popisek a volitelné bitovou kopii.

   1. Importujte homesmall.bmp rastrový obrázek, který obsahuje osm 16 x 16 bitových kopií pro malé tlačítko rastrových obrázků. Změňte ID rastrového obrázku nastaven na IDB_RIBBON_HOMESMALL.

   2. Importujte homelarge.bmp rastrový obrázek, který obsahuje osm 32 x 32 bitové kopie pro velké tlačítko bitmapy. Změňte ID rastrového obrázku nastaven na IDB_RIBBON_HOMELARGE.

5. Importovat bitmapy pro panely změněnou pásu karet. Tyto rastrové obrázky nebo panel ikon, se použijí po operaci změny velikosti, pokud je příliš malá pro zobrazení na celou panelu pásu karet.

   1. Importujte panelicons.bmp rastrový obrázek, který obsahuje osm 16 x 16 imagí. V **vlastnosti** okno **editoru rastrových obrázků**, umožňuje upravit šířku rastrového obrázku na 64 (16 x 64). Změňte ID rastrového obrázku nastaven na IDB_PANEL_ICONS.

[[Oddíly](#top)]

##  <a name="addribbon"></a> Přidání prostředku pásu karet do projektu

Při převodu aplikaci, která používá nabídky k aplikaci, která používá pás karet, není nutné odebrat nebo zakázat stávající nabídky. Místo toho vytvořte prostředek pásu karet, přidejte tlačítek na pásu karet a nová tlačítka přidružit existující položky nabídky. I když již nejsou viditelné v nabídkách, zprávy z pásu karet jsou směrovány v nabídkách. Kromě toho zástupci v nabídce pokračovat v práci.

Pásu karet se skládá z tlačítko aplikace, který je velké tlačítko v levé horní části pásu karet, a jednu nebo více karet kategorie. Každá karta kategorie obsahuje jednu nebo více panelů, které fungují jako kontejnery pro tlačítek na pásu karet a ovládacích prvků. Následující postup ukazuje, jak vytvořit prostředek pásu karet a potom přizpůsobení tlačítka aplikace.

### <a name="to-add-a-ribbon-resource-to-the-project"></a>Chcete-li přidat prostředek pásu karet do projektu

1. Na **projektu** nabídky, klikněte na tlačítko **přidat prostředek**.

2. V **přidat prostředek** dialogu **pásu karet** a potom klikněte na tlačítko **nový**.

   Visual Studio vytvoří prostředek pásu karet a otevře v zobrazení Návrh. ID prostředku pásu karet je IDR_RIBBON1, který se zobrazí v **zobrazení prostředků**. Na pásu karet obsahuje jednu kategorii a jeden panel.

3. Tlačítko aplikace lze přizpůsobit úpravou jeho vlastností. ID zprávy, které se používají v tomto kódu jsou již definovány v nabídce Scribble 1.0.

4. V návrhovém zobrazení klikněte na tlačítko aplikací zobrazíte její vlastnosti. Změňte hodnoty vlastností následujícím způsobem: **Image** k `IDB_RIBBON_MAIN`, **výzvy** k `File`, **klíče** k `f`, **Large Images** k `IDB_RIBBON_FILELARGE`, a **Small Images** k `IDB_RIBBON_FILESMALL`.

5. Následující změny vytvoření nabídky, která se zobrazí, když uživatel klikne na tlačítko aplikace. Klikněte na tlačítko se třemi tečkami (**...** ) vedle položky **položky hlavní** otevřít **Editor položek**.

   1. Klikněte na tlačítko **přidat** přidáte tlačítko. Změna **titulek** k `&New`, **ID** k `ID_FILE_NEW`, **Image** k `0`, **velký obrázek** k `0`.

   2. Klikněte na tlačítko **přidat** přidání druhého tlačítka. Změna **titulek** k `&Save`, **ID** k `ID_FILE_SAVE`, **Image** k `2`, a **velký obrázek** k `2`.

   3. Klikněte na tlačítko **přidat** na třetí tlačítko Přidat. Změna **titulek** k `Save &As`, **ID** k `ID_FILE_SAVE_AS`, **Image** k `3`, a **velký obrázek** k `3`.

   4. Klikněte na tlačítko **přidat** čtvrté tlačítko Přidat. Změna **titulek** k `&Print`, **ID** k `ID_FILE_PRINT`, **Image** k `4`, a **velký obrázek** k `4`.

   5. Změnit **položky** typ, který **oddělovač** a potom klikněte na tlačítko **přidat**.

   6. Změnit **položky** typ, který **tlačítko**. Klikněte na tlačítko **přidat** páté tlačítko Přidat. Změna **titulek** k `&Close`, **ID** k `ID_FILE_CLOSE`, **Image** k `5`, a **velký obrázek** k `5`.

6. Následující změny Vytvoření podnabídky pod tlačítko Tisk, který jste vytvořili v předchozím kroku.

   1. Klikněte na tlačítko **tisk** tlačítko, změňte **položky** typ, který **popisek**a potom klikněte na tlačítko **vložit**. Změna **titulek** k `Preview and print the document`.

   2. Klikněte na tlačítko **tisk** tlačítko, změňte **položky** typ, který **tlačítko**a klikněte na tlačítko **vložit**. Změna **titulek** k `&Print`, **ID** k `ID_FILE_PRINT`, **Image** k `4`, a **velký obrázek** k `4`.

   3. Klikněte na tlačítko **tisk** tlačítko a pak klikněte na tlačítko **vložit** přidáte tlačítko. Změna **titulek** k `&Quick Print`, **ID** k `ID_FILE_PRINT_DIRECT`, **Image** k `7`, a **velký obrázek** k `7`.

   4. Klikněte na tlačítko **tisk** tlačítko a pak klikněte na tlačítko **vložit** k přidání dalšího tlačítka. Změna **titulek** k `Print Pre&view`, **ID** k `ID_FILE_PRINT_PREVIEW`, **Image** k `6`, a **velký obrázek** k `6`.

   5. Nyní jste změnili **položky hlavní**. Klikněte na tlačítko **Zavřít** ukončíte **Editor položek**.

7. Následující změny vytvoří ukončení tlačítko, které se zobrazí v dolní části nabídky tlačítko aplikace.

   1. V **vlastnosti** okna, klikněte na tlačítko se třemi tečkami (**...** ) vedle položky **tlačítko** otevřít **Editor položek**.

   2. Klikněte na tlačítko **přidat** přidáte tlačítko. Změna **titulek** k `E&xit`, **ID** k `ID_APP_EXIT`, **Image** k `8`.

[[Oddíly](#top)]

##  <a name="createinstance"></a> Vytvoření Instance na pásu karet

Následující kroky ukazují, jak vytvořit instance na pásu karet při spuštění aplikace. Chcete-li přidat panel pásu karet do aplikace, deklarujte na pásu karet v souboru mainfrm.h. V souboru mainfrm.cpp napište kód pro načtení prostředku pásu karet.

### <a name="to-create-an-instance-of-the-ribbon-bar"></a>K vytvoření instance na pásu karet

1. V souboru mainfrm.h přidat datový člen chráněné části `CMainFrame`, definice třídy pro hlavního rámce. Tento člen představuje na pásu karet.

    ```cpp
    // Ribbon bar for the application
    CMFCRibbonBar m_wndRibbonBar;
    ```

2. V souboru mainfrm.cpp, přidejte následující kód před finální `return` příkaz na konci `CMainFrame::OnCreate` funkce. Tím se vytvoří instance na pásu karet.

    ```cpp
    // Create the ribbon bar
    if (!m_wndRibbonBar.Create(this))
    {
        return -1;   //Failed to create ribbon bar
    }
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
    ```

[[Oddíly](#top)]

##  <a name="addcategory"></a> Přizpůsobení prostředek pásu karet

Teď, když vytvoříte tlačítko aplikace, můžete přidat prvky na pás karet.

> [!NOTE]
> Tento návod používá stejné panelu ikonu pro všechny panely. Ale můžete použít jiných indexů obrázek seznamu zobrazíte další ikony.

### <a name="to-add-a-home-category-and-edit-panel"></a>Přidat kategorii domovské a upravit panel

1. Scribble program vyžaduje pouze jednu kategorii. V návrhovém zobrazení, klikněte na tlačítko **kategorie** zobrazíte jeho vlastnosti. Změňte hodnoty vlastností následujícím způsobem: **titulek** k `&Home`, **Large Images** k `IDB_RIBBON_HOMELARGE`, **Small Images** k `IDB_RIBBON_HOMESMALL`.

2. Každá kategorie pásu karet je uspořádaný do pojmenované panelů. Každý panel obsahuje sadu ovládacích prvků, které provádějí souvisejících operací. Tato kategorie obsahuje jeden panel. Klikněte na tlačítko **Panel**a potom změňte **titulek** k `Edit` a **Index bitové kopie** k `0`.

3. Chcete **upravit** panelu, přidejte tlačítko, které je zodpovědný za vymazat obsah dokumentu. ID zprávy pro toto tlačítko je již definována v prostředku nabídky IDR_SCRIBBTYPE. Zadejte `Clear All` jako text tlačítka a index rastrový obrázek, který upraví na tlačítko. Otevřít **nástrojů**a pak přetáhněte **tlačítko** k **upravit** panelu. Klikněte na tlačítko a pak změňte **titulek** k `Clear All`, **ID** k `ID_EDIT_CLEAR_ALL`, **Index bitové kopie** k `0`, **Large Image Index**  k `0`.

4. Uložte změny a potom sestavíte a spustíte aplikaci. Scribble aplikace má být zobrazena, a měl by mít panel pásu karet v horní části okna namísto řádku nabídek. Na pásu karet by měl mít jednu kategorii **Domů**, a **Domů** by měl mít jeden panel **upravit**. Tlačítka pásu karet, který jste přidali by měly být přidruženy s existující obslužné rutiny událostí a **otevřít**, **Zavřít**, **Uložit**, **tisk**, a **Vymazat vše** tlačítka by měla fungovat podle očekávání.

[[Oddíly](#top)]

##  <a name="setlook"></a> Nastavení vzhledu aplikace

A *správce vzhledu* je globální objekt, který určuje všechny vykreslování pro aplikaci. Protože původní aplikace Scribble používá styl uživatelského rozhraní (UI) Office 2000, aplikace může vypadat zastaralý. Můžete obnovit aplikaci, aby používala správce vzhledu Office 2007, tak, aby se podobá aplikaci sady Office 2007.

### <a name="to-set-the-look-of-the-application"></a>K nastavení vzhledu aplikace

1. V `CMainFrame::OnCreate` funkci, zadejte následující kód, chcete-li změnit výchozí správce vzhledu a vizuální styl.

    ```cpp
    // Set the default manager to Office 2007
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));
    CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);
    ```

2. Uložte změny a potom sestavíte a spustíte aplikaci. V uživatelském rozhraní aplikace by měla vypadat podobně jako uživatelského rozhraní sady Office 2007.

[[Oddíly](#top)]

## <a name="next-steps"></a>Další kroky

Změnili jste classic vzorek Scribble 1.0 MFC použití Návrháře pásu karet. Teď přejděte na [2. část](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md).

## <a name="see-also"></a>Viz také:

[Návody](../mfc/walkthroughs-mfc.md)  
[Návod: aktualizace aplikace MFC Scribble (část 2)] (.. / mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)  
