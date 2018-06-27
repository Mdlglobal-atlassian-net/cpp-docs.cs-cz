---
title: 'Návod: Aktualizace aplikace MFC Scribble (část 1) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: cfe91812d178618b1707f99aa10d6bd492109069
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956792"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-1"></a>Návod: Aktualizace aplikace MFC Scribble (část 1)
Tento návod ukazuje, jak upravit existující aplikaci MFC použít uživatelské rozhraní pásu karet. Visual Studio podporuje na pásu karet Office 2007 a pásu karet Scenic Windows 7. Další informace o uživatelském rozhraní pásu karet najdete v tématu [pásů karet](http://go.microsoft.com/fwlink/p/?linkid=129233) na webu MSDN.  
  
 Tento názorný postup upravuje classic Klikyháky MFC 1.0 vzorku, který vám umožní používat myš k vytvoření kresby na řádek. Tato část průvodce ukazuje, jak upravit vzorovou Scribble tak, aby se zobrazí panel pásu karet. [Část 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md) přidá další tlačítka na panel pásu karet.  
  
## <a name="prerequisites"></a>Požadavky  
 [Visual C++ – ukázky](../visual-cpp-samples.md)  
  
 [Visual C++ – ukázky](../visual-cpp-samples.md)  
  
##  <a name="top"></a> Oddíly  
 Tato část průvodce obsahuje následující části:  
  
- [Nahraďte základní třídy](#replaceclass)  
  
- [Přidávání bitmap do projektu](#addbitmap)  
  
- [Přidání prostředek pásu karet do projektu](#addribbon)  
  
- [Vytvoření Instance panelu pásu karet](#createinstance)  
  
- [Přidávání pásu karet kategorie](#addcategory)  
  
- [Nastavení vzhledu aplikace](#setlook)  
  
##  <a name="replaceclass"></a> Nahraďte základní třídy  
 Převést aplikaci, která podporuje nabídky k aplikaci, která podporuje pásu karet, musí být odvozený od aktualizované základní třídy aplikace, oken s rámečkem a třídy panelu nástrojů. (Doporučujeme je, že nemáte upravit původní vzorovou Scribble; místo toho vyčistěte projekt Scribble, zkopírujte ho do jiného adresáře a upravte kopii.)  
  
#### <a name="to-replace-the-base-classes-in-the-scribble-application"></a>Chcete-li nahradit základní třídy v aplikaci Scribble  
  
1.  V scribble.cpp, ověřte, že `CScribbleApp::InitInstance` obsahuje volání [AfxOLEInit –](../mfc/reference/ole-initialization.md#afxoleinit).  
  
2.  Přidejte následující kód do souboru stdafx.h.  
  
 ```  
    #include <afxcontrolbars.h>  
 ```  
  
3.  V scribble.h, upravte definici `CScribbleApp` třídy tak, aby je odvozený od [CWinAppEx Class](../mfc/reference/cwinappex-class.md).  
  
 ```  
    class CScribbleApp: public CWinAppEx  
 ```  
  
4.  Pokud aplikace systému Windows používá soubor inicializace (.ini) pro uložení uživatelských předvoleb dat, byla zapsána Scribble 1.0. Místo inicializačního souboru upravte Scribble k ukládání přes uživatelské předvolby v registru. Pokud chcete nastavit klíč registru a základní, zadejte následující kód v `CScribbleApp::InitInstance` po `LoadStdProfileSettings()` příkaz.  
  
 ```  
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));

 SetRegistryBase(_T("Settings"));

 ```  
  
5.  Hlavního rámce pro více rozhraní (MDI) aplikaci dokument už je odvozený od `CMDIFrameWnd` třídy. Místo toho je odvozený od [CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md) třídy.  
  
     V souborech mainfrm.h a mainfrm.cpp nahradit všechny odkazy na `CMDIFrameWnd` s `CMDIFrameWndEx`.  
  
6.  Nahradit v souborech childfrm.h a childfrm.cpp `CMDIChildWnd` s `CMDIChildWndEx`.  
  
     V childfrm. h souboru, nahraďte `CSplitterWnd` s `CSplitterWndEx`.  
  
7.  Upravte panely nástrojů a stavové řádky použít nové třídy MFC.  
  
     V souboru mainfrm.h:  
  
    1.  Nahraďte `CToolBar` s `CMFCToolBar`.  
  
    2.  Nahraďte `CStatusBar` s `CMFCStatusBar`.  
  
8.  V souboru mainfrm.cpp:  
  
    1.  Nahraďte `m_wndToolBar.SetBarStyle` s `m_wndToolBar.SetPaneStyle`  
  
    2.  Nahraďte `m_wndToolBar.GetBarStyle` s `m_wndToolBar.GetPaneStyle`  
  
    3.  Nahraďte `DockControlBar(&m_wndToolBar)` s `DockPane(&m_wndToolBar)`  
  
9. V souboru ipframe.cpp komentář následující tři řádky kódu.  
  
 ```  
    m_wndToolBar.EnableDocking(CBRS_ALIGN_ANY);

 pWndFrame->EnableDocking(CBRS_ALIGN_ANY);

    pWndFrame->DockPane(&m_wndToolBar);

 ```  
  
10. Pokud chcete staticky propojte aplikaci, přidejte následující kód na začátek souboru projektu prostředků (RC).  
  
 ```  
    #include "afxribbon.rc"  
 ```  
  
     Soubor afxribbon.rc obsahuje prostředky, které jsou požadovány v době běhu. [Průvodce aplikací knihovny MFC](../mfc/reference/mfc-application-wizard.md) zahrnuje tento soubor automaticky při vytvoření aplikace.  
  
11. Uložte změny a sestavte a spusťte aplikaci.  
  
 [[Části](#top)]  
  
##  <a name="addbitmap"></a> Přidávání bitmap do projektu  
 Další čtyři kroky tohoto názorného postupu vyžadovat prostředky rastrového obrázku. Můžete získat odpovídající bitmap různými způsoby:  
  
-   Použití [editory prostředků](../windows/resource-editors.md) k skladová vlastní rastrové obrázky. Nebo použijte editory prostředků ke kompilaci rastrové obrázky z bitové kopie PNG grafiky (.png), které jsou součástí [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]. Tyto Image jsou v `VS2008ImageLibrary` adresáře.  
  
     Uživatelské rozhraní pásu karet však vyžaduje, aby podporoval určité bitmap průhledné obrázky. Transparentní bitmap použijte 32bitový pixelů, kde 24 bits komponenty červené, zelené a modré barvy a určete 8 bitů *alfa kanálu* , který určuje průhlednost barvy. Aktuální editory prostředků můžete zobrazit, ale ne upravovat bitmap s 32-bit pixelů. V důsledku toho použijte editor externí image místo editory prostředků k manipulaci s transparentní bitmapy.  
  
-   Zkopírujte soubor odpovídající prostředek z jiné aplikace do projektu a pak importovat rastrové obrázky z tohoto souboru.  
  
 Tento názorný postup zkopíruje soubory prostředků z aplikace v adresáři ukázky.  
  
#### <a name="to-add-bitmaps-to-the-project"></a>Chcete-li do projektu přidejte rastrové obrázky  
  
1.  Zkopírujte následující soubory .bmp z adresáře prostředků pomocí Průzkumníka souborů (`res`) RibbonGadgets vzorku:  
  
    1.  Main.bmp zkopírujte do projektu Scribble.  
  
    2.  Zkopírovat do projektu Scribble filesmall.bmp a filelarge.bmp.  
  
    3.  Vytvořit nové kopie filelarge.bmp a filesmall.bmp souborů, ale v ukázce RibbonGadgets uložení kopie. Přejmenujte kopie homesmall.bmp a homelarge.bmp a poté přesuňte do projektu Scribble kopie.  
  
    4.  Vytvořit kopii souboru Toolbar.bmp s tím, ale v ukázce RibbonGadgets uložit kopii. Přejmenujte panelicons.bmp kopie a poté přesuňte kopie do projektu Scribble.  
  
2.  Importujte rastrový obrázek pro aplikace MFC. V **zobrazení prostředků**, dvakrát klikněte na **scribble.rc** uzlu, dvakrát klikněte na **rastrový obrázek** uzel a pak klikněte na tlačítko **přidat prostředek**. V dialogovém okně, které se zobrazí, klikněte na tlačítko **Import**. Vyhledejte `res` adresář, vyberte soubor main.bmp a pak klikněte na tlačítko **otevřete**.  
  
     Rastrový obrázek main.bmp obsahuje bitovou kopii 26 x 26. Změňte ID bitové mapy na IDB_RIBBON_MAIN.  
  
3.  Importujte bitmap pro nabídky soubor, který je připojen k tlačítka aplikace.  
  
    1.  Importujte soubor filesmall.bmp, který obsahuje deset velikosti 16 x 16 (16 x 160) bitové kopie. Protože potřebujeme pouze osm velikosti 16 x 16 bitové kopie (16 × 128), použijte **zobrazení prostředků** změnit šířku bitovou mapu z 160 na 128 znaků. Změňte ID bitové mapy na IDB_RIBBON_FILESMALL.  
  
    2.  Import filelarge.bmp, který obsahuje osm 32 x 32 (32 x 256) bitové kopie. Změňte ID bitové mapy na IDB_RIBBON_FILELARGE.  
  
4.  Importujte bitmap kategorií pásu karet a panelů. Každé kartě na panelu pásu karet kategorii a skládá se z textový popisek a volitelné bitovou kopii.  
  
    1.  Importujte homesmall.bmp rastrový obrázek, který obsahuje osm 16 x 16 bitových kopií pro malé tlačítko bitmapy. Změňte ID bitové mapy na IDB_RIBBON_HOMESMALL.  
  
    2.  Importujte homelarge.bmp rastrový obrázek, který obsahuje osm 32 x 32 bitových kopií pro velké tlačítko bitmapy. Změňte ID bitové mapy na IDB_RIBBON_HOMELARGE.  
  
5.  Importovat bitmap pro panely změněnou pásu karet. Tyto Bitmap nebo panel ikon, se použijí po operace změny velikosti, pokud je příliš malá zobrazíte panel celý pásu karet.  
  
    1.  Importujte panelicons.bmp rastrový obrázek, který obsahuje osm 16 x 16 bitové kopie. V **vlastnosti** okno **rastrový obrázek Editor**, umožňuje upravit šířku rastrového obrázku na 64 (16 x 64). Změňte ID bitové mapy na IDB_PANEL_ICONS.  
  
 [[Části](#top)]  
  
##  <a name="addribbon"></a> Přidání prostředek pásu karet do projektu  
 Při převodu aplikaci, která používá nabídky k aplikaci, která používá pásu karet, nemáte odebrat nebo zakázat stávající nabídky. Místo toho můžete vytvořit prostředek pásu karet, přidání tlačítek pásu karet a pak přidružit nová tlačítka existující položky nabídky. I když již nejsou viditelné v nabídkách, jsou směrovány zprávy z panelu pásu karet v nabídkách. Kromě toho nabídky zástupců pokračovat v práci.  
  
 Pásu karet se skládá z tlačítka aplikace, což je velký tlačítko na levém okraji pásu karet, a jeden nebo více kategorií karty. Každé kartě kategorie obsahuje jednu nebo více panely, které fungují jako kontejnery tlačítek pásu karet a ovládacích prvků. Následující postup ukazuje, jak vytvořit prostředek pásu karet a pak přizpůsobení tlačítka aplikace.  
  
#### <a name="to-add-a-ribbon-resource-to-the-project"></a>Chcete-li přidat prostředek pásu karet do projektu  
  
1.  Na **projektu** nabídky, klikněte na tlačítko **přidat prostředek**.  
  
2.  V **přidat prostředek** dialogové okno, vyberte **pásu karet** a pak klikněte na **nový**.  
  
     Visual Studio vytvoří prostředek pásu karet a otevře v zobrazení návrhu. ID prostředku pásu karet je IDR_RIBBON1, který se zobrazí v **zobrazení prostředků**. Na pásu karet obsahuje jednu kategorii a jednoho panelu.  
  
3.  Tlačítko aplikace můžete přizpůsobit úpravou jeho vlastnosti. ID zprávy, které se používají v tomto kódu jsou již definováni v nabídce Klikyháky 1.0.  
  
4.  V návrhovém zobrazení klikněte na tlačítko aplikace zobrazíte její vlastnosti. Změnit hodnoty vlastností následujícím způsobem: **bitové kopie** k *IDB_RIBBON_MAIN*, **výzva** k *soubor*, **klíče** k *f*, **velkých obrázků** k *IDB_RIBBON_FILELARGE*, a **malých obrázků** k *IDB_RIBBON_ FILESMALL*.  
  
5.  Následující úpravy vytvořit v nabídce, která se zobrazí, když uživatel klikne na tlačítko aplikace. Klikněte na tlačítko se třemi tečkami (**...** ) vedle **položky hlavní** otevřete **položky Editor**.  
  
    1.  Klikněte na tlačítko **přidat** přidání tlačítka. Změna **popisek** k *& Nový*, **ID** k *id_file_new –*, **bitové kopie** k *0*, **Velký obrázek** k *0*.  
  
    2.  Klikněte na tlačítko **přidat** pro přidání druhé tlačítko. Změna **popisek** k *& Uložit*, **ID** k *id_file_save –*, **bitové kopie** k *2* , a **velký obrázek** k *2*.  
  
    3.  Klikněte na tlačítko **přidat** třetí tlačítko Přidat. Změna **popisek** k *& Uložit jako*, **ID** k *id_file_save_as –*, **bitové kopie** k *3*, a **velký obrázek** k *3*.  
  
    4.  Klikněte na tlačítko **přidat** čtvrté tlačítko Přidat. Změna **popisek** k *& Tisk*, **ID** k *id_file_print –*, **bitové kopie** k *4* , a **velký obrázek** k *4*.  
  
    5.  Změna **položky** typ **oddělovače** a pak klikněte na **přidat**.  
  
    6.  Změna **položky** typ **tlačítko**. Klikněte na tlačítko **přidat** páté tlačítko Přidat. Změna **popisek** k *& Zavřít*, **ID** k *id_file_close –*, **bitové kopie** k *5* , a **velký obrázek** k *5*.  
  
6.  Následující úpravy Vytvoření podnabídky pod na tlačítko Tisk, kterou jste vytvořili v předchozím kroku.  
  
    1.  Klikněte na tlačítko **tiskových** tlačítko, změňte **položky** typ **popisek**a potom klikněte na **vložit**. Změna **popisek** k *náhled a tisk dokumentu*.  
  
    2.  Klikněte na tlačítko **tiskových** tlačítko, změňte **položky** typ **tlačítko**a klikněte na tlačítko **vložit**. Změna **popisek** k *& Tisk*, **ID** k *id_file_print –*, **bitové kopie** k *4* , a **velký obrázek** k *4*.  
  
    3.  Klikněte **tiskových** tlačítko a pak klikněte na **vložit** přidání tlačítka. Změna **popisek** k *& Rychlý tiskových*, **ID** k *ID_FILE_PRINT_DIRECT*, **bitové kopie** k *7*, a **velký obrázek** k *7*.  
  
    4.  Klikněte na tlačítko **tiskových** tlačítko a pak klikněte na **vložit** na jiné tlačítko Přidat. Změna **popisek** k *& Náhled tisku*, **ID** k *id_file_print_preview –*, **bitové kopie** na *6*, a **velký obrázek** k *6*.  
  
    5.  Nyní jste změnili **položky hlavní**. Klikněte na tlačítko **Zavřít** ukončíte **položky Editor**.  
  
7.  Následující úpravy vytvoří ukončení tlačítko, které se zobrazí v dolní části nabídky tlačítko aplikace.  
  
    1.  V **vlastnosti** okně klikněte na tlačítko se třemi tečkami (**...** ) vedle **tlačítko** otevřete **položky Editor**.  
  
    2.  Klikněte na tlačítko **přidat** přidání tlačítka. Změna **popisek** k *vý &*, **ID** k *id_app_exit –*, **bitové kopie** k *8* .  
  
 [[Části](#top)]  
  
##  <a name="createinstance"></a> Vytvoření Instance panelu pásu karet  
 Následující kroky ukazují, jak vytvořit instanci na pásu karet panelu při spuštění aplikace. Chcete-li přidat panel pásu karet k aplikaci, deklarujte panelu pásu karet v souboru mainfrm.h. Potom v souboru mainfrm.cpp napište kód pro načtení prostředku pásu karet.  
  
#### <a name="to-create-an-instance-of-the-ribbon-bar"></a>K vytvoření instance panelu pásu karet  
  
1.  V souboru mainfrm.h přidat člena dat v chráněném sekci `CMainFrame`, definici třídy hlavního rámce. Tento člen představuje panelu pásu karet.  
  
 "' * / / Pásu karet panelu pro aplikaci  
    CMFCRibbonBar m_wndRibbonBar;  
 ```  
  
2.  In the mainfrm.cpp file, add the following code before the final **return** statement at the end of the `CMainFrame::OnCreate` function. This creates an instance of the ribbon bar.  
  
 ``` *// Create the ribbon bar  
    if (!m_wndRibbonBar.Create(this))  
 {  
    return -1;   //Failed to create ribbon bar  
 }  
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);

 ```  
  
 [[Části](#top)]  
  
##  <a name="addcategory"></a> Přizpůsobení prostředek pásu karet  
 Teď, když jste vytvořili tlačítka aplikace, můžete přidat prvky na pásu karet.  
  
> [!NOTE]
>  Tento návod používá ikonu panelu stejné pro všechny panely. Však můžete další indexy seznamu bitovou kopii k zobrazení dalších ikon.  
  
#### <a name="to-add-a-home-category-and-edit-panel"></a>Přidat kategorii domovské a upravit panely  
  
1.  Scribble program vyžaduje pouze jednu kategorii. V návrhovém zobrazení, klikněte na tlačítko **kategorie** zobrazíte její vlastnosti. Změňte hodnoty vlastností následujícím způsobem: **popisek** k *& Domů*, **velkých obrázků** k *IDB_RIBBON_HOMELARGE*,  **Malé obrázky** k *IDB_RIBBON_HOMESMALL*.  
  
2.  Každá kategorie pásu karet je uspořádán do pojmenované panelů. Jednotlivé panely obsahuje sadu ovládacích prvků, které provádějí související operace. Tato kategorie má jednoho panelu. Klikněte na tlačítko **Panel**a poté změňte **popisek** k *upravit* a **Index bitové kopie** k *0*.  
  
3.  Na **upravit** panelu, přidání tlačítka, která je odpovědná za vymazání obsah dokumentu. ID zprávy pro toto tlačítko již byl definován v rámci IDR_SCRIBBTYPE nabídky prostředku. Zadejte *Vymazat vše* jako text tlačítka a index rastrového obrázku, která upraví tlačítko. Otevřete **sada nástrojů**a poté přetáhněte **tlačítko** k **upravit** panelu. Klikněte na tlačítko a poté změňte **popisek** k *Vymazat vše*, **ID** k *id_edit_clear_all –*, **Index bitové kopie** k *0*, **velký obrázek indexu** k *0*.  
  
4.  Uložte změny a sestavte a spusťte aplikaci. Aplikace Scribble mají být zobrazeny, a měl by mít panelu pásu karet v horní části okna místo řádku nabídek. Na pásu karet panelu musí mít jednu kategorii **Domů**, a **Domů** by měl mít jeden panel **upravit**. Tlačítka pásu karet, které jste přidali by měly být přidružené stávající obslužné rutiny událostí a **otevřete**, **Zavřít**, **Uložit**, **tiskových**, a **Vymazat vše** tlačítka by měla fungovat podle očekávání.  
  
 [[Části](#top)]  
  
##  <a name="setlook"></a> Nastavení vzhledu aplikace  
 A *visual manager* je globální objekt, který řídí všechny vykreslování pro aplikaci. Vzhledem k původní Scribble aplikace využívá styl Office 2000 uživatelské rozhraní (UI), aplikace bude vypadat stejné. Můžete resetovat aplikaci pomocí visual správce Office 2007, tak, aby vypadal aplikace Office 2007.  
  
#### <a name="to-set-the-look-of-the-application"></a>K nastavení vzhledu aplikace  
  
1.  V `CMainFrame::OnCreate` fungovat, zadejte následující kód pro změnu výchozího visual správce a stylu.  
  
 "' * / / Nastavena výchozího správce na Office 2007   
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));

 CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);

 ```  
  
2.  Save the changes, and then build and run the application. The application UI should resemble the Office 2007 UI.  
  
 [[Sections](#top)]  
  
## Next Steps  
 You have modified the classic Scribble 1.0 MFC sample to use the Ribbon Designer. Now go to [Part 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md).  
  
## See Also  
 [Walkthroughs](../mfc/walkthroughs-mfc.md)   
 [Walkthrough: Updating the MFC Scribble Application (Part 2)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)

