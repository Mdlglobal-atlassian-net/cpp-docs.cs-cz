---
title: "Cpropertysheet – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPropertySheet
- AFXDLGS/CPropertySheet
- AFXDLGS/CPropertySheet::CPropertySheet
- AFXDLGS/CPropertySheet::AddPage
- AFXDLGS/CPropertySheet::Construct
- AFXDLGS/CPropertySheet::Create
- AFXDLGS/CPropertySheet::DoModal
- AFXDLGS/CPropertySheet::EnableStackedTabs
- AFXDLGS/CPropertySheet::EndDialog
- AFXDLGS/CPropertySheet::GetActiveIndex
- AFXDLGS/CPropertySheet::GetActivePage
- AFXDLGS/CPropertySheet::GetPage
- AFXDLGS/CPropertySheet::GetPageCount
- AFXDLGS/CPropertySheet::GetPageIndex
- AFXDLGS/CPropertySheet::GetTabControl
- AFXDLGS/CPropertySheet::MapDialogRect
- AFXDLGS/CPropertySheet::OnInitDialog
- AFXDLGS/CPropertySheet::PressButton
- AFXDLGS/CPropertySheet::RemovePage
- AFXDLGS/CPropertySheet::SetActivePage
- AFXDLGS/CPropertySheet::SetFinishText
- AFXDLGS/CPropertySheet::SetTitle
- AFXDLGS/CPropertySheet::SetWizardButtons
- AFXDLGS/CPropertySheet::SetWizardMode
- AFXDLGS/CPropertySheet::m_psh
dev_langs: C++
helpviewer_keywords:
- CPropertySheet [MFC], CPropertySheet
- CPropertySheet [MFC], AddPage
- CPropertySheet [MFC], Construct
- CPropertySheet [MFC], Create
- CPropertySheet [MFC], DoModal
- CPropertySheet [MFC], EnableStackedTabs
- CPropertySheet [MFC], EndDialog
- CPropertySheet [MFC], GetActiveIndex
- CPropertySheet [MFC], GetActivePage
- CPropertySheet [MFC], GetPage
- CPropertySheet [MFC], GetPageCount
- CPropertySheet [MFC], GetPageIndex
- CPropertySheet [MFC], GetTabControl
- CPropertySheet [MFC], MapDialogRect
- CPropertySheet [MFC], OnInitDialog
- CPropertySheet [MFC], PressButton
- CPropertySheet [MFC], RemovePage
- CPropertySheet [MFC], SetActivePage
- CPropertySheet [MFC], SetFinishText
- CPropertySheet [MFC], SetTitle
- CPropertySheet [MFC], SetWizardButtons
- CPropertySheet [MFC], SetWizardMode
- CPropertySheet [MFC], m_psh
ms.assetid: 8461ccff-d14f-46e0-a746-42ad642ef94e
caps.latest.revision: "30"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 52c5d167390826578c4e3a2380c885bf1d507d19
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cpropertysheet-class"></a>Cpropertysheet – třída
Představuje seznam vlastností, také známé jako dialogová okna karet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CPropertySheet : public CWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CPropertySheet::CPropertySheet](#cpropertysheet)|Vytvoří `CPropertySheet` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CPropertySheet::AddPage](#addpage)|Na stránce se přidá do seznamu vlastností.|  
|[CPropertySheet::Construct](#construct)|Vytvoří `CPropertySheet` objektu.|  
|[CPropertySheet::Create](#create)|Zobrazí nemodálního seznamu vlastností.|  
|[CPropertySheet::DoModal](#domodal)|Zobrazí modální vlastností.|  
|[CPropertySheet::EnableStackedTabs](#enablestackedtabs)|Označuje, zda seznam vlastností používá skládaný nebo posouvání karty.|  
|[CPropertySheet::EndDialog](#enddialog)|Ukončí seznamu vlastností.|  
|[CPropertySheet::GetActiveIndex](#getactiveindex)|Načte index active stránky seznamu vlastností.|  
|[CPropertySheet::GetActivePage](#getactivepage)|Vrací objekt aktivní stránku.|  
|[CPropertySheet::GetPage](#getpage)|Načte ukazatel na určenou stránku.|  
|[CPropertySheet::GetPageCount](#getpagecount)|Načte počet stránek v seznamu vlastností.|  
|[CPropertySheet::GetPageIndex](#getpageindex)|Načte index zadaný stránky seznamu vlastností.|  
|[CPropertySheet::GetTabControl](#gettabcontrol)|Načte ukazatel do ovládacího prvku karta.|  
|[CPropertySheet::MapDialogRect](#mapdialogrect)|Dialogové okno-jednotky obdélníku převede na obrazovce jednotky.|  
|[CPropertySheet::OnInitDialog](#oninitdialog)|Přepsání nastavení za účelem posílení inicializace list vlastností.|  
|[CPropertySheet::PressButton](#pressbutton)|Simuluje volba tlačítko zadané v seznamu vlastností.|  
|[CPropertySheet::RemovePage](#removepage)|Na stránce se odebere ze seznamu vlastností.|  
|[CPropertySheet::SetActivePage](#setactivepage)|Nastaví prostřednictvím kódu programu objektu active stránky.|  
|[CPropertySheet::SetFinishText](#setfinishtext)|Nastaví text pro tlačítko Dokončit.|  
|[CPropertySheet::SetTitle](#settitle)|Nastaví titulek seznamu vlastností.|  
|[CPropertySheet::SetWizardButtons](#setwizardbuttons)|Umožňuje tlačítka průvodce.|  
|[CPropertySheet::SetWizardMode](#setwizardmode)|Umožňuje režimu průvodce.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CPropertySheet::m_psh](#m_psh)|Windows [PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546) struktury. Poskytuje přístup k základní vlastnost list parametry.|  
  
## <a name="remarks"></a>Poznámky  
 Seznam vlastností se skládá z `CPropertySheet` objektů a jeden nebo více [CPropertyPage](../../mfc/reference/cpropertypage-class.md) objekty. Rozhraní zobrazuje jako okno s sadu karta indexy a oblast, která obsahuje aktuálně vybrané stránky vlastností. Uživatel přejde na konkrétní stránku pomocí příslušnou kartu.  
  
 `CPropertySheet`poskytuje podporu pro rozšířená [PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546) struktura byla zavedená v [!INCLUDE[Win98](../../mfc/reference/includes/win98_md.md)] a systému Windows NT 2000. Struktura obsahuje další příznaky a členy, které podporují použití rastrový obrázek pozadí "vodoznak".  
  
 V seznamu vlastností objektu vlastnost zobrazit tyto nové bitové kopie automaticky, předejte platné hodnoty pro Image rastrového obrázku a palety volání [CPropertySheet::Construct](#construct) nebo [CPropertySheet::CPropertySheet](#cpropertysheet).  
  
 I když `CPropertySheet` není odvozen od [CDialog](../../mfc/reference/cdialog-class.md), správu `CPropertySheet` objektu je třeba Správa `CDialog` objektu. Například vytvoření vlastností vyžaduje dvě části vytváření: volat konstruktor a pak zavolají [DoModal](#domodal) pro modální vlastností nebo [vytvořit](#create) pro nemodálního seznamu vlastností. `CPropertySheet`má dva typy konstruktory: [CPropertySheet::Construct](#construct) a [CPropertySheet::CPropertySheet](#cpropertysheet).  
  
 Když vytvoříte `CPropertySheet` objektu některé [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) může způsobit, že první odpovídající výjimce proběhnout. Výsledkem systému pokusu změnit styl seznamu vlastností, před vytvořením list. Abyste se vyhnuli výjimku, zajistěte, aby při vytváření nastavte následující styly vaší `CPropertySheet`:  
  
-   DS_3DLOOK  
  
-   DS_CONTROL  
  
-   WS_CHILD –  
  
-   WS_TABSTOP –  
  
 Následující styly jsou volitelné a nezpůsobí první odpovídající výjimce:  
  
-   DS_SHELLFONT  
  
-   DS_LOCALEDIT  
  
-   WS_CLIPCHILDREN –  
  
 Žádné jiné `Window Styles` jsou zakázané a je neměli povolit.  
  
 Výměna dat mezi `CPropertySheet` objekt a externího objektu je podobná výměna dat s `CDialog` objektu. Důležitý rozdíl je, že jsou nastavení vlastností obvykle členské proměnné `CPropertyPage` objekty spíše než z `CPropertySheet` samotného objektu.  
  
 Můžete vytvořit typ dialogového okna Karta nazývá průvodce, který se skládá z vlastností s posloupností stránky vlastností, které průvodce provede kroky pro operace, jako je například nastavení zařízení nebo vytváření bulletinu uživatele. V dialogovém okně Karta Průvodce type stránek vlastností nemají karty a současně je viditelná pouze jednu vlastnost stránky. Navíc místo nutnosti **OK** a **použít nyní** tlačítka, dialogové okno Průvodce typu karta má **zpět** tlačítko **Další** nebo  **Dokončit** tlačítko **zrušit** tlačítko a **pomoci** tlačítko.  
  
 Pokud chcete vytvořit dialogové okno Průvodce type, postupujte podle stejných kroků, které byste použili k vytvoření standardní vlastností, ale volání [SetWizardMode](#setwizardmode) před voláním [DoModal](#domodal). Chcete-li povolit tlačítka průvodce, volejte [SetWizardButtons](#setwizardbuttons), přizpůsobení jejich funkce a vzhled pomocí příznaky. Chcete-li povolit **Dokončit** tlačítko, volání [SetFinishText](#setfinishtext) poté, co uživatel má akce prováděné na poslední stránce průvodce.  
  
 Další informace o tom, jak používat `CPropertySheet` objekty, najdete v článku [vlastností a stránky vlastností](../../mfc/property-sheets-and-property-pages-in-mfc.md). Navíc najdete v článku znalostní báze Knowledge Base Q146916: postupy: vytvoření cpropertysheet – nemodální pomocí standardní tlačítka a článek Q300606: postupy: návrh s možností změny velikosti MFC vlastností.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CPropertySheet`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdlgs.h  
  
##  <a name="addpage"></a>CPropertySheet::AddPage  
 Přidá zadaný stránka s kartě úplně vpravo v seznamu vlastností.  
  
```  
void AddPage(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>Parametry  
 `pPage`  
 Bodů na stránku, který se má přidat do seznamu vlastností. Nemůže být **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Přidejte do seznamu vlastností v pořadí zleva doprava, že chcete, aby se objevily stránky.  
  
 `AddPage`Přidá [CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage) do objektu `CPropertySheet` objektu je seznam stránek, ale ve skutečnosti nevytvoří okna pro stránku. Rozhraní framework odloží vytváření okna pro stránku, dokud uživatel vybere této stránce.  
  
 Když přidáte pomocí stránky vlastností `AddPage`, `CPropertySheet` nadřazeným objektem `CPropertyPage`. Chcete-li získat přístup k seznamu vlastností na stránce vlastností, zavolejte [CWnd::GetParent](../../mfc/reference/cwnd-class.md#getparent).  
  
 Není nutné počkejte na vytvoření v okně Vlastnosti list volat `AddPage`. Obvykle bude volat `AddPage` před voláním [DoModal](#domodal) nebo [vytvořit](#create).  
  
 Když zavoláte `AddPage` po zobrazení stránky vlastností, se projeví na kartě řádek nově přidané stránky.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#129](../../mfc/codesnippet/cpp/cpropertysheet-class_1.cpp)]  
  
##  <a name="construct"></a>CPropertySheet::Construct  
 Vytvoří `CPropertySheet` objektu.  
  
```  
void Construct(
    UINT nIDCaption,  
    CWnd* pParentWnd = NULL,  
    UINT iSelectPage = 0);

 
void Construct(
    LPCTSTR pszCaption,  
    CWnd* pParentWnd = NULL,  
    UINT iSelectPage = 0);

 
void Construct(
    UINT nIDCaption,  
    CWnd* pParentWnd,  
    UINT iSelectPage,  
    HBITMAP hbmWatermark,  
    HPALETTE hpalWatermark = NULL,  
    HBITMAP hbmHeader = NULL);

 
void Construct(
    LPCTSTR pszCaption,  
    CWnd* pParentWnd,  
    UINT iSelectPage,  
    HBITMAP hbmWatermark,  
    HPALETTE hpalWatermark = NULL,  
    HBITMAP hbmHeader = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDCaption`  
 ID titulek má být použit pro seznam vlastností.  
  
 `pParentWnd`  
 Ukazatel do nadřazeného okna seznamu vlastností. Pokud **NULL**, nadřazené okno bude hlavní okno aplikace.  
  
 `iSelectPage`  
 Index stránky, která bude zpočátku nahoře. Výchozí hodnota je na první stránku přidat do seznamu.  
  
 `pszCaption`  
 Ukazatel na řetězec, který obsahuje titulek, který se má použít pro seznam vlastností. Nemůže být **NULL**.  
  
 `hbmWatermark`  
 Popisovač vodoznak bitové mapy ze stránky vlastností.  
  
 `hpalWatermark`  
 Popisovač paletu vodoznak rastrový obrázek nebo rastrový obrázek hlavičky.  
  
 `hbmHeader`  
 Popisovač rastrového obrázku záhlaví stránky vlastností.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce člen, pokud jeden z konstruktorů třídy již nebyla volána. Například volání `Construct` při deklarovat nebo přidělit pole `CPropertySheet` objekty. V případě pole, je třeba volat `Construct` pro každého člena v poli.  
  
 Chcete-li zobrazit seznam vlastností, zavolejte [DoModal](#domodal) nebo [vytvořit](#create). Řetězec obsažené v první parametr bude uložena v umístění panelu popisek pro seznam vlastností.  
  
 Můžete zobrazit obrázky vodoznak nebo záhlaví automaticky Pokud používáte třetí nebo čtvrtý prototypů `Construct`uvedené výše a předat platné hodnoty pro `hbmWatermark`, `hpalWatermark`, nebo `hbmHeader` parametry.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, v části co jste okolností by volání `Construct`.  
  
 [!code-cpp[NVC_MFCDocView#130](../../mfc/codesnippet/cpp/cpropertysheet-class_2.cpp)]  
  
##  <a name="cpropertysheet"></a>CPropertySheet::CPropertySheet  
 Vytvoří `CPropertySheet` objektu.  
  
```  
CPropertySheet();

 
explicit CPropertySheet(
    UINT nIDCaption,  
    CWnd* pParentWnd = NULL,  
    UINT iSelectPage = 0);

 
explicit CPropertySheet(
    LPCTSTR pszCaption,  
    CWnd* pParentWnd = NULL,  
    UINT iSelectPage = 0);

 
CPropertySheet(
    UINT nIDCaption,  
    CWnd* pParentWnd,  
    UINT iSelectPage,  
    HBITMAP hbmWatermark,  
    HPALETTE hpalWatermark = NULL,  
    HBITMAP hbmHeader = NULL);

 
CPropertySheet(
    LPCTSTR pszCaption,  
    CWnd* pParentWnd,  
    UINT iSelectPage,  
    HBITMAP hbmWatermark,  
    HPALETTE hpalWatermark = NULL,  
    HBITMAP hbmHeader = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDCaption`  
 ID titulek má být použit pro seznam vlastností.  
  
 `pParentWnd`  
 Body do nadřazeného okna seznamu vlastností. Pokud **NULL**, nadřazené okno bude hlavní okno aplikace.  
  
 `iSelectPage`  
 Index stránky, která bude zpočátku nahoře. Výchozí hodnota je na první stránku přidat do seznamu.  
  
 `pszCaption`  
 Odkazuje na řetězec, který obsahuje titulek, který se má použít pro seznam vlastností. Nemůže být **NULL**.  
  
 `hbmWatermark`  
 Popisovač pro rastrový obrázek pozadí seznamu vlastností.  
  
 `hpalWatermark`  
 Popisovač pro paletu vodoznak rastrový obrázek nebo rastrový obrázek hlavičky.  
  
 `hbmHeader`  
 Popisovač pro bitovou mapu záhlaví stránky vlastností.  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li zobrazit seznam vlastností, zavolejte [DoModal](#domodal) nebo [vytvořit](#create). Řetězec obsažené v první parametr bude uložena v umístění panelu popisek pro seznam vlastností.  
  
 Pokud máte několik parametrů (například pokud používáte pole), použijte [vytvořit](#construct) místo `CPropertySheet`.  
  
 Můžete zobrazit obrázky vodoznak nebo záhlaví automaticky Pokud používáte třetí nebo čtvrtý prototypů `CPropertySheet`výše, a předat platné hodnoty pro `hbmWatermark`, `hpalWatermark`, nebo `hbmHeader` parametry.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#131](../../mfc/codesnippet/cpp/cpropertysheet-class_3.cpp)]  
  
##  <a name="create"></a>CPropertySheet::Create  
 Zobrazí nemodálního seznamu vlastností.  
  
```  
virtual BOOL Create(CWnd* pParentWnd = NULL,
    DWORD dwStyle = (DWORD)-1,
    DWORD dwExStyle = 0);  
```  
  
### <a name="parameters"></a>Parametry  
 `pParentWnd`  
 Body do nadřazeného okna. Pokud **NULL**, nadřazená položka plochy.  
  
 `dwStyle`  
 Styly oken pro seznam vlastností. Úplný seznam dostupných stylů, najdete v části [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 `dwExStyle`  
 Rozšířené styly oken pro seznam vlastností. Úplný seznam dostupných stylů, najdete v části [rozšířené styly oken](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je úspěšně; vytvořil seznam vlastností jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Volání **vytvořit** lze v konstruktoru, nebo můžete volat, po vyvolání konstruktoru.  
  
 Výchozí styl, vyjádřené předáním -1 jako `dwStyle`, je ve skutečnosti **ws_sysmenu – &#124;** `WS_POPUP` **&#124; Ws_caption – &#124; DS_MODALFRAME &#124; DS_CONTEXTHELP &#124; Ws_visible –**. Výchozí hodnota rozšířený styl oken, vyjádřené jako 0 předáním `dwExStyle`, je ve skutečnosti **ws_ex_dlgmodalframe –**.  
  
 **Vytvořit** – členská funkce vrátí ihned po vytvoření seznamu vlastností. Chcete-li odstranit seznamu vlastností, zavolejte [CWnd::DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow).  
  
 Nemodální vlastností, zobrazí se volání **vytvořit** nemají, zrušit, použít nyní tlačítka OK a nápovědy, stejně jako modální dialogové okno vlastností. Požadované tlačítka musí být vytvořený uživatelem.  
  
 Chcete-li zobrazit modální vlastností, zavolejte [DoModal](#domodal) místo.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#132](../../mfc/codesnippet/cpp/cpropertysheet-class_4.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#133](../../mfc/codesnippet/cpp/cpropertysheet-class_5.cpp)]  
  
##  <a name="domodal"></a>CPropertySheet::DoModal  
 Zobrazí modální vlastností.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `IDOK`nebo `IDCANCEL` Pokud funkci bylo úspěšné; jinak hodnota 0 nebo -1. Pokud jako průvodce bylo úspěšně navázáno seznamu vlastností (viz [SetWizardMode](#setwizardmode)), `DoModal` vrací buď `ID_WIZFINISH` nebo `IDCANCEL`.  
  
### <a name="remarks"></a>Poznámky  
 Návratová hodnota odpovídá ID ovládacího prvku, který uzavřel seznamu vlastností. Po návratu tato funkce windows odpovídající seznam vlastností a všechny stránky budou mít byl zničen. Bude stále existují objekty sami. Obvykle se budou načítat data z [CPropertyPage](../../mfc/reference/cpropertypage-class.md) objekty po `DoModal` vrátí `IDOK`.  
  
 Chcete-li zobrazit nemodálního seznamu vlastností, zavolejte [vytvořit](#create) místo.  
  
 Při stránky vlastností z jeho odpovídající prostředku dialogového okna, může to způsobit první odpovídající výjimce. To vyplývá z jeho stránku vlastností změna styl prostředku dialogového okna na požadovaný styl, před vytvořením stránky. Protože prostředky jsou obecně jen pro čtení, to způsobí výjimku. Systém ošetří výjimku a vytvoří kopii upravené prostředků. První odpovídající výjimce můžete proto ignorována.  
  
> [!NOTE]
>  Tato výjimka musí být zpracován podle operačního systému, pokud jsou kompilování s modelem asynchronní zpracování výjimek. Další informace o zpracování modely výjimek najdete v tématu [/EH (Model zpracování výjimek)](../../build/reference/eh-exception-handling-model.md). V takovém případě není zalomen volání `CPropertySheet::DoModal` pomocí bloku try-catch C++ ve kterém catch zpracuje všechny výjimky, například `catch (...)`. Tento blok by ošetření výjimky určen pro operační systém a příčina nepředvídatelné chování. Však můžete bez obav použít C++ zpracování výjimek s typy konkrétní výjimek nebo strukturované zpracování výjimek kde výjimka narušení přístupu předána do operačního systému.  
  
 Aby nedošlo ke generování tento první odpovídající výjimce, můžete ručně zaručit, že seznam vlastností má správný [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles). Je nutné nastavit následující styly pro seznam vlastností:  
  
-   DS_3DLOOK  
  
-   DS_CONTROL  
  
-   WS_CHILD –  
  
-   WS_TABSTOP –  
  
 Můžete použít následující volitelné styly aniž by to způsobilo první odpovídající výjimce:  
  
-   DS_SHELLFONT  
  
-   DS_LOCALEDIT  
  
-   WS_CLIPCHILDREN –  
  
 Všechny ostatní styly Windows zakážete, protože nejsou kompatibilní s vlastností. Toto doporučení se nevztahuje na rozšířené styly. Nastavení těchto standardní stylů správně bude zaručit, že seznam vlastností není potřeba upravovat a bude nedošlo ke generování první odpovídající výjimce.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPropertySheet::AddPage](#addpage).  
  
##  <a name="enablestackedtabs"></a>CPropertySheet::EnableStackedTabs  
 Označuje, zda zásobníku řádky karty v seznamu vlastností.  
  
```  
void EnableStackedTabs(BOOL bStacked);
```  
  
### <a name="parameters"></a>Parametry  
 `bStacked`  
 Určuje, zda jsou povolena skládaný karty v seznamu vlastností. Zakažte skládaný řádky značky nastavením `bStacked` k **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení Pokud má seznam vlastností další karty, než se vejde na šířku jednoho řádku seznamu vlastností, bude karty zásobníku v více řádků. Použití posouvání karet místo Skládání karty, volání `EnableStackedTabs` s `bStacked` nastavena na **FALSE** před voláním [DoModal](#domodal) nebo [vytvořit](#create).  
  
 Je třeba volat `EnableStackedTabs` při vytváření modální nebo nemodálního seznamu vlastností. Chcete-li zahrnout tento styl v `CPropertySheet`-odvozené třídy, zápis obslužné rutiny zpráv pro `WM_CREATE`. V přepsané verzi [CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate), volání **EnableStackedTabs (FALSE)** před voláním implementaci základní třídy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#134](../../mfc/codesnippet/cpp/cpropertysheet-class_6.cpp)]  
  
##  <a name="enddialog"></a>CPropertySheet::EndDialog  
 Ukončí seznamu vlastností.  
  
```  
void EndDialog(int nEndID);
```  
  
### <a name="parameters"></a>Parametry  
 *nEndID*  
 Identifikátor má být použit jako návratová hodnota seznamu vlastností.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen je voláno rámcem při stisknutí tlačítka OK, zrušit nebo tlačítko Zavřít. Volání, že tato funkce člen, pokud dojde k události, který by měl zavřete okno vlastností.  
  
 Tato funkce člen se používá pouze pro modální dialogové okno.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPropertySheet::PressButton](#pressbutton).  
  
##  <a name="getactiveindex"></a>CPropertySheet::GetActiveIndex  
 Získá index počet aktivní stránku v okně List vlastnosti a pak používá vrácené číslo indexu jako parametr pro `GetPage`.  
  
```  
int GetActiveIndex() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Číslo indexu aktivní stránky.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPropertySheet::GetActivePage](#getactivepage).  
  
##  <a name="getactivepage"></a>CPropertySheet::GetActivePage  
 Načte stránka aktivní okno List vlastností.  
  
```  
CPropertyPage* GetActivePage() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na stránce aktivní.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce člen můžete provést některé akce na stránce aktivní.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#135](../../mfc/codesnippet/cpp/cpropertysheet-class_7.cpp)]  
  
##  <a name="getpage"></a>CPropertySheet::GetPage  
 Vrátí ukazatel na určenou stránku v tohoto seznamu vlastností.  
  
```  
CPropertyPage* GetPage(int nPage) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nPage`  
 Index na požadovanou stránku začínajícím hodnotou 0. Musí být mezi 0 a jeden menší než počet stránek v seznamu vlastností (včetně).  
  
### <a name="return-value"></a>Návratová hodnota  
 Má ukazatel na odpovídající stránky k `nPage` parametr.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPropertyPage::OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish).  
  
##  <a name="getpagecount"></a>CPropertySheet::GetPageCount  
 Určuje, kolik stránek se aktuálně v seznamu vlastností.  
  
```  
int GetPageCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet stránek v seznamu vlastností.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPropertyPage::OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish).  
  
##  <a name="getpageindex"></a>CPropertySheet::GetPageIndex  
 Načte indexové číslo zadané stránky v seznamu vlastností.  
  
```  
int GetPageIndex(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>Parametry  
 `pPage`  
 Bodů na stránku s indexem, která se má najít. Nemůže být **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Indexové číslo stránky.  
  
### <a name="remarks"></a>Poznámky  
 Například byste použili `GetPageIndex` získat index stránky, aby bylo možné používat [SetActivePage](#setactivepage) nebo [GetPage](#getpage).  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPropertySheet::GetActivePage](#getactivepage).  
  
##  <a name="gettabcontrol"></a>CPropertySheet::GetTabControl  
 Načte ukazatel ovládacího prvku karta udělat něco specifické pro ovládacího prvku karta (to znamená, že k používání některé z rozhraní API v [CTabCtrl](../../mfc/reference/ctabctrl-class.md)).  
  
```  
CTabCtrl* GetTabControl() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na ovládacího prvku karta.  
  
### <a name="remarks"></a>Poznámky  
 Například volání této funkce člen, pokud chcete přidat bitmap na každé kartě během inicializace.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#136](../../mfc/codesnippet/cpp/cpropertysheet-class_8.cpp)]  
  
##  <a name="m_psh"></a>CPropertySheet::m_psh  
 Struktura, jejíž členové uložení charakteristika [PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546).  
  
### <a name="remarks"></a>Poznámky  
 Použijte tuto strukturu k chybě při inicializaci vzhled vlastností po je vytvořený, ale předtím, než se zobrazí se [DoModal](#domodal) – členská funkce. Například nastavit `dwSize` členem `m_psh` velikosti chcete vlastností tak, aby měl.  
  
 Další informace o tuto strukturu, včetně seznamu svých členů, najdete v části **PROPSHEETHEADER** ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#143](../../mfc/codesnippet/cpp/cpropertysheet-class_9.cpp)]  
  
##  <a name="mapdialogrect"></a>CPropertySheet::MapDialogRect  
 Dialogové okno-jednotky obdélníku převede na obrazovce jednotky.  
  
```  
void MapDialogRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `lpRect`  
 Odkazuje na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura nebo [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt, který obsahuje – dialogové okno koordinuje má být převeden.  
  
### <a name="remarks"></a>Poznámky  
 Dialogové okno-jednotky jsou vyjádřený jako aktuální základní jednotku – dialogové okno odvozené od průměrná šířka a výška znaků písmo použité pro – dialogové okno text. Jednu jednotku vodorovné je jeden čtvrtý jednotky základní šířkou – dialogové okno a jednu jednotku svislé osmina jednotky základní výška – dialogové okno.  
  
 [GetDialogBaseUnits](http://msdn.microsoft.com/library/windows/desktop/ms645475) funkce Windows vrací informace o velikosti písma systému, ale jiné písmo pro každý vlastností můžete zadat, pokud použijete **DS_SETFONT** styl v Soubor definice prostředků. [MapDialogRect](http://msdn.microsoft.com/library/windows/desktop/ms645502) funkce systému Windows, popsané v sadě Windows SDK používá příslušného písma pro tohoto dialogového okna.  
  
 `MapDialogRect` – Členská funkce nahrazuje dialogového jednotky v `lpRect` s obrazovky jednotek (v pixelech) tak, aby rámeček umožňuje vytvoření dialogového nebo umístit ovládacího prvku v rámci pole.  
  
##  <a name="oninitdialog"></a>CPropertySheet::OnInitDialog  
 Přepsání posílení inicializace list vlastností.  
  
```  
virtual BOOL OnInitDialog();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Určuje, zda má aplikace nastavena zaměření pro vstup na jednu z ovládacích prvků v seznamu vlastností. Pokud **OnInitDialog** vrátí nenulovou, Windows nastaví zaměření pro vstup na první ovládací prvek v seznamu vlastností. Aplikace může vrátit 0, pouze v případě, že se má zaměření pro vstup explicitně nastavit na jednu z ovládacích prvků v seznamu vlastností.  
  
### <a name="remarks"></a>Poznámky  
 Tato členské funkce je volána v reakci **WM_INITDIALOG** zprávy. Tato zpráva je odeslána do seznamu vlastností během [vytvořit](#create) nebo [DoModal](#domodal) volání, které nastat bezprostředně před zobrazením seznamu vlastností je.  
  
 Funkci člena přepište, pokud je třeba provést zvláštní zpracování při inicializaci seznamu vlastností. V přepsané verze, nejprve volat základní třídy `OnInitDialog` ale Ignorovat hodnoty. Obvykle bude vracet **TRUE** z přepsaného – členská funkce.  
  
 Není nutné položku mapy zpráv pro tuto funkci člen.  
  
##  <a name="pressbutton"></a>CPropertySheet::PressButton  
 Simuluje volba tlačítko zadané v seznamu vlastností.  
  
```  
void PressButton(int nButton);
```  
  
### <a name="parameters"></a>Parametry  
 `nButton`  
 nButton: identifikuje být stisknutí tlačítka. Tento parametr může být jedna z následujících hodnot:  
  
- **PSBTN_BACK** rozhodne na tlačítko Zpět.  
  
- **PSBTN_NEXT** rozhodne na tlačítko Další.  
  
- **PSBTN_FINISH** rozhodne na tlačítko Dokončit.  
  
- **PSBTN_OK** rozhodne na tlačítko OK.  
  
- **PSBTN_APPLYNOW** vybere tlačítko použít.  
  
- **PSBTN_CANCEL** rozhodne na tlačítko Storno.  
  
- **PSBTN_HELP** rozhodne na tlačítko Nápověda.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [PSM_PRESSBUTTON](http://msdn.microsoft.com/library/windows/desktop/bb774597) Další informace o zprávě, Windows SDK Pressbutton.  
  
 Volání `PressButton` nebudou odesílat [PSN_APPLY](http://msdn.microsoft.com/library/windows/desktop/bb774552) oznámení na stránce vlastností do rozhraní. Chcete-li odeslat toto oznámení, volejte [CPropertyPage::OnOK](../../mfc/reference/cpropertypage-class.md#onok).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#137](../../mfc/codesnippet/cpp/cpropertysheet-class_10.cpp)]  
  
##  <a name="removepage"></a>CPropertySheet::RemovePage  
 Odebere ze seznamu vlastností stránky a zničí okna přidružené.  
  
```  
void RemovePage(CPropertyPage* pPage);  
void RemovePage(int nPage);
```  
  
### <a name="parameters"></a>Parametry  
 `pPage`  
 Bodů na stránku a odebrat ze seznamu vlastností. Nemůže být `NULL`.  
  
 `nPage`  
 Index stránky odeberou. Musí být mezi 0 a jeden menší než počet stránek v seznamu vlastností (včetně).  
  
### <a name="remarks"></a>Poznámky  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md) samotného objektu nebude odstraněn, až vlastník `CPropertySheet` zavření časového intervalu.  
  
##  <a name="setactivepage"></a>CPropertySheet::SetActivePage  
 Změní na aktivní stránce.  
  
```  
BOOL SetActivePage(int nPage);  
BOOL SetActivePage(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>Parametry  
 `nPage`  
 Index stránky lze nastavit. Musí být mezi 0 a jeden menší než počet stránek v seznamu vlastností (včetně).  
  
 `pPage`  
 Bodů na stránku nastavení v seznamu vlastností. Nemůže být **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v seznamu vlastností po aktivaci úspěšně; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Například použít `SetActivePage` Pokud akce uživatele na jedné stránce by nemělo způsobit jinou stránku stane aktivní stránky.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPropertySheet::GetActivePage](#getactivepage).  
  
##  <a name="setfinishtext"></a>CPropertySheet::SetFinishText  
 Nastaví text, v příkazovém tlačítku dokončit.  
  
```  
void SetFinishText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszText`  
 Odkazuje na text, který se zobrazí na tlačítko Dokončit příkaz.  
  
### <a name="remarks"></a>Poznámky  
 Volání `SetFinishText` zobrazit text na tlačítko Dokončit příkaz a poté, co uživatel vykoná akce na poslední stránce průvodce skrýt tlačítka Další a zpět.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]  
  
##  <a name="settitle"></a>CPropertySheet::SetTitle  
 Určuje titulek seznamu vlastností (text zobrazovaný v záhlaví okna rámečkem).  
  
```  
void SetTitle(
    LPCTSTR lpszText,  
    UINT nStyle = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `nStyle`  
 Určuje styl název. Styl musí být určený na 0 nebo **PSH_PROPTITLE**. Pokud je styl nastavená jako **PSH_PROPTITLE**, slova "Vlastnosti" se zobrazí po bude text zadaný jako popisek. Například volání `SetTitle`("Jednoduché", **PSH_PROPTITLE**) bude mít za následek popisek list vlastnost "Jednoduché vlastností."  
  
 `lpszText`  
 Odkazuje na text, který se použije jako popisek v záhlaví okna seznamu vlastností.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení používá vlastností parametr titulek v konstruktoru list vlastností.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#139](../../mfc/codesnippet/cpp/cpropertysheet-class_12.cpp)]  
  
##  <a name="setwizardbuttons"></a>CPropertySheet::SetWizardButtons  
 Povolí nebo zakáže na tlačítko Zpět a další, dokončit v seznamu vlastností průvodce.  
  
```  
void SetWizardButtons(DWORD dwFlags);
```  
  
### <a name="parameters"></a>Parametry  
 `dwFlags`  
 Sada příznaky, které přizpůsobit funkce a vzhled tlačítka průvodce. Tento parametr může být kombinací následujícího:  
  
- **PSWIZB_BACK** tlačítko Zpět  
  
- **PSWIZB_NEXT** vedle tlačítka  
  
- **PSWIZB_FINISH** tlačítko Dokončit  
  
- **PSWIZB_DISABLEDFINISH** zakázané dokončit tlačítko  
  
### <a name="remarks"></a>Poznámky  
 Volání `SetWizardButtons` pouze po otevření; dialogové okno nelze volat `SetWizardButtons` před voláním [DoModal](#domodal). Obvykle, by měly volat `SetWizardButtons` z [CPropertyPage::OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive).  
  
 Pokud chcete změnit text na tlačítko Dokončit nebo skrýt další a zpět tlačítka jednou uživatele byla dokončena v Průvodci volání [SetFinishText](#setfinishtext). Všimněte si, že je tlačítko stejné sdílené pro dokončit a další. Můžete zobrazit dokončit nebo tlačítko Další najednou, ale ne obojí.  
  
### <a name="example"></a>Příklad  
 A `CPropertySheet` má tři průvodce stránky vlastností: `CStylePage`, `CColorPage`, a `CShapePage`.  Následující fragment kódu ukazuje, jak povolit a zakázat **zpět** a **Další** tlačítka na stránce průvodce.  
  
 [!code-cpp[NVC_MFCDocView#140](../../mfc/codesnippet/cpp/cpropertysheet-class_13.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#141](../../mfc/codesnippet/cpp/cpropertysheet-class_14.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]  
  
##  <a name="setwizardmode"></a>CPropertySheet::SetWizardMode  
 Stránky vlastností vytvoří jako průvodce.  
  
```  
void SetWizardMode();
```  
  
### <a name="remarks"></a>Poznámky  
 Klíčové vlastnosti stránky vlastností Průvodce je, že uživatel přejde pomocí další nebo dokončit, zálohování a stornovací tlačítka místo karty.  
  
 Volání `SetWizardMode` před voláním [DoModal](#domodal). Po zavolání metody `SetWizardMode`, `DoModal` buď vrátí **ID_WIZFINISH** (Pokud je uživatel nezavře s na tlačítko Dokončit) nebo **IDCANCEL**.  
  
 `SetWizardMode`Nastaví příznak PSH_WIZARD.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#142](../../mfc/codesnippet/cpp/cpropertysheet-class_15.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka CMNCTRL1 MFC](../../visual-cpp-samples.md)   
 [Ukázka CMNCTRL2 MFC](../../visual-cpp-samples.md)   
 [Ukázka MFC PROPDLG](../../visual-cpp-samples.md)   
 [Ukázka MFC SNAPVW](../../visual-cpp-samples.md)   
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



