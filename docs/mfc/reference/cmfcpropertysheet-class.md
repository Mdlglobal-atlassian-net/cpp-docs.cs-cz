---
title: "Třída CMFCPropertySheet | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCPropertySheet
- AFXPROPERTYSHEET/CMFCPropertySheet
- AFXPROPERTYSHEET/CMFCPropertySheet::CMFCPropertySheet
- AFXPROPERTYSHEET/CMFCPropertySheet::AddPage
- AFXPROPERTYSHEET/CMFCPropertySheet::AddPageToTree
- AFXPROPERTYSHEET/CMFCPropertySheet::AddTreeCategory
- AFXPROPERTYSHEET/CMFCPropertySheet::EnablePageHeader
- AFXPROPERTYSHEET/CMFCPropertySheet::GetHeaderHeight
- AFXPROPERTYSHEET/CMFCPropertySheet::GetLook
- AFXPROPERTYSHEET/CMFCPropertySheet::GetNavBarWidth
- AFXPROPERTYSHEET/CMFCPropertySheet::GetTab
- AFXPROPERTYSHEET/CMFCPropertySheet::InitNavigationControl
- AFXPROPERTYSHEET/CMFCPropertySheet::OnActivatePage
- AFXPROPERTYSHEET/CMFCPropertySheet::OnDrawPageHeader
- AFXPROPERTYSHEET/CMFCPropertySheet::OnRemoveTreePage
- AFXPROPERTYSHEET/CMFCPropertySheet::RemoveCategory
- AFXPROPERTYSHEET/CMFCPropertySheet::RemovePage
- AFXPROPERTYSHEET/CMFCPropertySheet::SetIconsList
- AFXPROPERTYSHEET/CMFCPropertySheet::SetLook
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertySheet [MFC], CMFCPropertySheet
- CMFCPropertySheet [MFC], AddPage
- CMFCPropertySheet [MFC], AddPageToTree
- CMFCPropertySheet [MFC], AddTreeCategory
- CMFCPropertySheet [MFC], EnablePageHeader
- CMFCPropertySheet [MFC], GetHeaderHeight
- CMFCPropertySheet [MFC], GetLook
- CMFCPropertySheet [MFC], GetNavBarWidth
- CMFCPropertySheet [MFC], GetTab
- CMFCPropertySheet [MFC], InitNavigationControl
- CMFCPropertySheet [MFC], OnActivatePage
- CMFCPropertySheet [MFC], OnDrawPageHeader
- CMFCPropertySheet [MFC], OnRemoveTreePage
- CMFCPropertySheet [MFC], RemoveCategory
- CMFCPropertySheet [MFC], RemovePage
- CMFCPropertySheet [MFC], SetIconsList
- CMFCPropertySheet [MFC], SetLook
ms.assetid: 01d93573-9698-440f-a6a4-5bebbee879dc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e2684de5c72dcc755c2a75e2553eed509ce76533
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcpropertysheet-class"></a>CMFCPropertySheet – třída
`CMFCPropertySheet` Třída podporuje seznam vlastností, kde každé stránce vlastnost je označený jako kartu stránky, tlačítka panelu nástrojů, řídicí uzel stromu nebo položku seznamu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCPropertySheet : public CPropertySheet  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCPropertySheet::CMFCPropertySheet](#cmfcpropertysheet)|Vytvoří `CMFCPropertySheet` objektu.|  
|`CMFCPropertySheet::~CMFCPropertySheet`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCPropertySheet::AddPage](#addpage)|Na stránce se přidá do seznamu vlastností.|  
|[CMFCPropertySheet::AddPageToTree](#addpagetotree)|Přidá novou stránku vlastnosti do ovládacího prvku strom.|  
|[CMFCPropertySheet::AddTreeCategory](#addtreecategory)|Přidá nový uzel do ovládacího prvku strom.|  
|[CMFCPropertySheet::EnablePageHeader](#enablepageheader)|Rezervy místa v horní části každé stránce kreslení vlastní hlavičky.|  
|[CMFCPropertySheet::GetHeaderHeight](#getheaderheight)|Načte výšku aktuální záhlaví.|  
|[CMFCPropertySheet::GetLook](#getlook)|Načte hodnotu výčtu, která určuje vzhled aktuální seznam vlastností.|  
|[CMFCPropertySheet::GetNavBarWidth](#getnavbarwidth)|Opakuje šířku navigačního panelu v pixelech.|  
|[CMFCPropertySheet::GetTab](#gettab)|Načte objekt interní karta ovládací prvek, který podporuje aktuální vlastnost stylů ovládacího prvku.|  
|`CMFCPropertySheet::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený tento typ třídy.|  
|[CMFCPropertySheet::InitNavigationControl](#initnavigationcontrol)|Inicializuje vzhled aktuální vlastnost stylů ovládacího prvku.|  
|[CMFCPropertySheet::OnActivatePage](#onactivatepage)|Voláno rámcem, pokud je povoleno stránky vlastností.|  
|[CMFCPropertySheet::OnDrawPageHeader](#ondrawpageheader)|Voláno rámcem kreslení vlastní vlastnosti záhlaví stránky.|  
|`CMFCPropertySheet::OnInitDialog`|Zpracovává [WM_INITDIALOG](http://msdn.microsoft.com/library/windows/desktop/ms645428) zprávy. (Přepisuje [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog).)|  
|[CMFCPropertySheet::OnRemoveTreePage](#onremovetreepage)|Voláno rámcem odebrání ovládacím prvkem strom stránky vlastností.|  
|`CMFCPropertySheet::PreTranslateMessage`|Přeloží zprávy oken, než jsou odeslány do [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) a [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funkce systému Windows. (Přepisuje `CPropertySheet::PreTranslateMessage`.)|  
|[CMFCPropertySheet::RemoveCategory](#removecategory)|Odebrání uzlu z ovládacího prvku strom.|  
|[CMFCPropertySheet::RemovePage](#removepage)|Stránky vlastností odebere ze seznamu vlastností.|  
|[CMFCPropertySheet::SetIconsList](#seticonslist)|Určuje seznam bitové kopie, které se používají v ovládacím prvku navigačním podokně aplikace Outlook.|  
|[CMFCPropertySheet::SetLook](#setlook)|Určuje vzhled seznamu vlastností.|  
  
## <a name="remarks"></a>Poznámky  
 `CMFCPropertySheet` Třída reprezentuje seznam vlastností, také známé jako dialogová okna karet. `CMFCPropertySheet` Třídy můžete zobrazit stránce vlastností v mnoha různými způsoby.  
  
 Proveďte následující kroky a použít `CMFCPropertySheet` ve vaší aplikaci:  
  
1.  Odvození třídy z `CMFCPropertySheet` třídy a název třídy, například CMyPropertySheet.  
  
2.  Vytvořit [CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md) objekt pro každou stránku vlastností.  
  
3.  Volání [CMFCPropertySheet::SetLook](#setlook) metoda v konstruktoru CMyPropertySheet. Parametr této metody Určuje, že vlastnost stránky se zobrazí jako karty na nejvyšší nebo nalevo od poli vlastnosti. karty ve stylu Microsoft OneNote vlastností; tlačítka v ovládacím prvku panel nástrojů Microsoft Outlook; uzly na ovládacím prvkem strom; nebo seznam položek na levé straně seznamu vlastností.  
  
4.  Pokud vytvoříte seznam vlastností ve stylu panel nástrojů Microsoft Outlook, zavolejte [CMFCPropertySheet::SetIconsList](#seticonslist) metoda, jak přidružit seznamu obrázků společně s stránky vlastností.  
  
5.  Volání [CMFCPropertySheet::AddPage](#addpage) metoda pro každou stránku vlastností.  
  
6.  Vytvoření `CMFCPropertySheet` řízení a volat jeho `DoModal` metoda.  
  
## <a name="illustrations"></a>Obrázky  
 Následující obrázek znázorňuje vlastností, který je ve stylu embedded nástrojů Microsoft Outlook. Na levé straně listu vlastností se zobrazí panel nástrojů aplikace Outlook.  
  
 ![Ovládací prvky Barva CMFCPropertySheet](../../mfc/reference/media/cmfcpropertysheet_color.png "cmfcpropertysheet_color")  
  
 Následující obrázek znázorňuje seznam vlastností, která obsahuje [CMFCPropertyGridCtrl třída](../../mfc/reference/cmfcpropertygridctrl-class.md) objektu. Tento objekt je seznam vlastností ve stylu standardní běžné ovládací prvky vlastností.  
  
 ![Ovládací prvky seznamu a vlastnost CMFCPropertySheet](../../mfc/reference/media/cmfcpropertysheet_list.png "cmfcpropertysheet_list")  
  
 Následující obrázek znázorňuje vlastností, který je ve stylu ovládacím prvkem strom.  
  
 ![Strom vlastností](../../mfc/reference/media/proptree.png "proptree")  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cpropertysheet –](../../mfc/reference/cpropertysheet-class.md)  
  
 [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxpropertysheet.h  
  
##  <a name="addpage"></a>CMFCPropertySheet::AddPage  
 Na stránce se přidá do seznamu vlastností.  
  
```  
void AddPage(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pPage`  
 Ukazatel na objekt stránky. Tento parametr nemůže být `NULL`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda přidá stránku zadanou vlastnost kartě úplně vpravo v seznamu vlastností. Proto tuto metodu použijte k přidání stránky v pořadí zleva doprava.  
  
 Pokud seznam vlastností ve stylu aplikace Microsoft Outlook, rozhraní zobrazí seznam navigačních tlačítek v levé části seznamu vlastností. Po této metody přidá stránky vlastností, přidá do seznamu odpovídající tlačítko. Stránky vlastností zobrazíte kliknutím na jeho odpovídající tlačítko. Další informace o styly vlastností najdete v tématu [CMFCPropertySheet::SetLook](#setlook).  
  
##  <a name="addpagetotree"></a>CMFCPropertySheet::AddPageToTree  
 Přidá novou stránku vlastnosti do ovládacího prvku strom.  
  
```  
void AddPageToTree(
    CMFCPropertySheetCategoryInfo* pCategory,  
    CMFCPropertyPage* pPage,  
    int nIconNum=-1,  
    int nSelIconNum=-1);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pCategory`  
 Ukazatel na nadřazeného uzlu stromu, nebo `NULL` pro přidružení na určenou stránku nejvyšší úrovně uzlu. Volání [CMFCPropertySheet::AddTreeCategory](#addtreecategory) metoda získat tento ukazatel.  
  
 [v]`pPage`  
 Ukazatel na objekt vlastnosti stránky.  
  
 [v]`nIconNum`  
 Indexem ikony nebo -1, pokud žádné ikona je použita. Pokud není vybrána stránce, zobrazí se ikona vedle jeho stránku vlastností ovládacího prvku strom. Výchozí hodnota je -1.  
  
 [v]`nSelIconNum`  
 Indexem ikony nebo -1, pokud žádné ikona je použita. Pokud je vybrána stránce, zobrazí se ikona vedle jeho stránku vlastností ovládacího prvku strom. Výchozí hodnota je -1.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda přidá stránky vlastností jako na základní úrovni ovládacím prvkem strom. Přidání stránky vlastností, vytvoření `CMFCPropertySheet` objektu, volání [CMFCPropertySheet::SetLook](#setlook) metoda s `look` parametr nastaven na `CMFCPropertySheet::PropSheetLook_Tree`a potom pomocí této metody přidat stránku vlastností.  
  
##  <a name="addtreecategory"></a>CMFCPropertySheet::AddTreeCategory  
 Přidá nový uzel do ovládacího prvku strom.  
  
```  
CMFCPropertySheetCategoryInfo* AddTreeCategory(
    LPCTSTR lpszLabel,  
    int nIconNum=-1,  
    int nSelectedIconNum=-1,  
    const CMFCPropertySheetCategoryInfo* pParentCategory=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszLabel`  
 Název uzlu.  
  
 [v]`nIconNum`  
 Indexem ikony nebo -1, pokud žádné ikona je použita. Pokud není vybrána stránce, zobrazí se ikona vedle jeho stránku vlastností ovládacího prvku strom. Výchozí hodnota je -1.  
  
 [v]`nSelectedIconNum`  
 Indexem ikony nebo -1, pokud žádné ikona je použita. Pokud je vybrána stránce, zobrazí se ikona vedle jeho stránku vlastností ovládacího prvku strom. Výchozí hodnota je -1.  
  
 [v]`pParentCategory`  
 Ukazatel na nadřazeného uzlu stromu, nebo `NULL` pro přidružení na určenou stránku nejvyšší úrovně uzlu. Nastavte tento parametr se [CMFCPropertySheet::AddTreeCategory](#addtreecategory) metoda.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nový uzel ve stromové struktuře.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte, chcete-li přidat nový uzel, který se také označuje jako kategorii, do ovládacího prvku strom. Přidat uzel, vytvoření `CMFCPropertySheet` objektu, volání [CMFCPropertySheet::SetLook](#setlook) metoda s `look` parametr nastaven na `CMFCPropertySheet::PropSheetLook_Tree`a potom pomocí této metody přidat uzel.  
  
 Návratová hodnota tuto metodu použijte v následující volání [CMFCPropertySheet::AddPageToTree](#addpagetotree) a [CMFCPropertySheet::AddTreeCategory](#addtreecategory).  
  
##  <a name="cmfcpropertysheet"></a>CMFCPropertySheet::CMFCPropertySheet  
 Vytvoří `CMFCPropertySheet` objektu.  
  
```  
CMFCPropertySheet(
    UINT nIDCaption,  
    CWnd* pParentWnd=NULL,  
    UINT iSelectPage=0);

CMFCPropertySheet(
    LPCTSTR pszCaption,  
    CWnd* pParentWnd=NULL,  
    UINT iSelectPage=0);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pszCaption`  
 Řetězec, který obsahuje titulek list vlastností. Nemůže být `NULL`.  
  
 [v]`nIDCaption`  
 ID prostředku, který obsahuje titulek list vlastností.  
  
 [v]`pParentWnd`  
 Ukazatel do nadřazeného okna vlastností, nebo `NULL` Pokud nadřazeného okna je hlavní okno aplikace. Výchozí hodnota je `NULL`.  
  
 [v]`iSelectPage`  
 Index založený na nule nejvyšší vlastnost stránky. Výchozí hodnota je 0.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu parametry [CPropertySheet::CPropertySheet](../../mfc/reference/cpropertysheet-class.md#cpropertysheet) konstruktor.  
  
##  <a name="enablepageheader"></a>CMFCPropertySheet::EnablePageHeader  
 Rezervy místa v horní části každé stránce kreslení vlastní hlavičky.  
  
```  
void EnablePageHeader(int nHeaderHeight);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nHeaderHeight`  
 Výška záhlaví má v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Použít hodnotu `nHeaderHeight` parametr kreslení vlastní hlavičky přepsat [CMFCPropertySheet::OnDrawPageHeader](#ondrawpageheader) metoda.  
  
##  <a name="getheaderheight"></a>CMFCPropertySheet::GetHeaderHeight  
 Načte výšku aktuální záhlaví.  
  
```  
int GetHeaderHeight() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výška záhlaví má v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Volání [CMFCPropertySheet::EnablePageHeader](#enablepageheader) metoda před voláním této metody.  
  
##  <a name="getlook"></a>CMFCPropertySheet::GetLook  
 Načte hodnotu výčtu, která určuje vzhled aktuální seznam vlastností.  
  
```  
PropSheetLook GetLook() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Jedna z hodnot výčtu, která určuje vzhled seznamu vlastností. Seznam možných hodnot najdete v tématu výčtu tabulce v části poznámky [CMFCPropertySheet::SetLook](#setlook).  
  
##  <a name="getnavbarwidth"></a>CMFCPropertySheet::GetNavBarWidth  
 Získá šířku navigačním panelu.  
  
```  
int GetNavBarWidth() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Šířka navigačního panelu v pixelech.  
  
##  <a name="gettab"></a>CMFCPropertySheet::GetTab  
 Načte objekt interní karta ovládací prvek, který podporuje aktuální vlastnost stylů ovládacího prvku.  
  
```  
CMFCTabCtrl& GetTab() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Objekt ovládacího prvku karta interní.  
  
### <a name="remarks"></a>Poznámky  
 Seznam vlastností můžete nastavit tak, aby se zobrazuje v různé styly, jako je například ovládacím prvkem strom, seznam navigačních tlačítek nebo sadu stránky s kartami.  
  
 Před voláním této metody volejte [CMFCPropertySheet::SetLook](#setlook) metoda k nastavení vzhledu ovládacího prvku list vlastností. Potom zavolejte [CMFCPropertySheet::InitNavigationControl](#initnavigationcontrol) metoda pro inicializaci objekt ovládacího prvku karta interní. Tuto metodu použijte načíst objekt ovládacího prvku karta a pak použijte tento objekt pro práci s kartami na seznamu vlastností.  
  
 Tato metoda se vyhodnotí v režimu ladění, pokud ovládací prvek seznamu vlastností vlastnost není nastavená na objeví ve stylu Microsoft OneNote.  
  
##  <a name="initnavigationcontrol"></a>CMFCPropertySheet::InitNavigationControl  
 Inicializuje vzhled aktuální vlastnost stylů ovládacího prvku.  
  
```  
virtual CWnd* InitNavigationControl();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na okno ovládacího prvku list vlastností.  
  
### <a name="remarks"></a>Poznámky  
 Ovládací prvek seznamu vlastností Vlastnosti mohou objevit v několika různých formulářů, například sadu stránky s kartami, ovládacím prvkem strom nebo seznam navigačních tlačítek. Použití [CMFCPropertySheet::SetLook](#setlook) metoda k určení vzhledu ovládacího prvku list vlastností.  
  
##  <a name="onactivatepage"></a>CMFCPropertySheet::OnActivatePage  
 Voláno rámcem, pokud je povoleno stránky vlastností.  
  
```  
virtual void OnActivatePage(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pPage`  
 Ukazatel na objekt vlastnosti stránky, který představuje stránku povolená vlastnost.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení tato metoda zajišťuje, že stránka povoleno vlastností přesunut do oblasti zobrazení. Obsahuje-li styl aktuální seznam vlastností podokně Microsoft Outlook, tato metoda nastaví na odpovídající tlačítko Outlook na zaškrtnutého stavu.  
  
##  <a name="ondrawpageheader"></a>CMFCPropertySheet::OnDrawPageHeader  
 Voláno rámcem k vykreslení hlavičku pro stránky přizpůsobených vlastností.  
  
```  
virtual void OnDrawPageHeader(
    CDC* pDC,  
    int nPage,  
    CRect rectHeader);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Ukazatel na kontextu zařízení.  
  
 [v]`nPage`  
 Číslo od nuly vlastnost stránky.  
  
 [v]`rectHeader`  
 Ohraničující obdélník, která určuje, kde k vykreslení záhlaví.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení tato metoda neprovede žádnou akci. Pokud tuto metodu přepíšete, zavolejte [CMFCPropertySheet::EnablePageHeader](#enablepageheader) metoda předtím, než tuto metodu volá framework.  
  
##  <a name="onremovetreepage"></a>CMFCPropertySheet::OnRemoveTreePage  
 Voláno rámcem odebrání ovládacím prvkem strom stránky vlastností.  
  
```  
virtual BOOL OnRemoveTreePage(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pPage`  
 Ukazatel na objekt vlastností stránky, který představuje stránku vlastností a odebrat.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud tato metoda je úspěšná. v opačném `FALSE`.  
  
##  <a name="removecategory"></a>CMFCPropertySheet::RemoveCategory  
 Odebrání uzlu z ovládacího prvku strom.  
  
```  
void RemoveCategory(CMFCPropertySheetCategoryInfo* pCategory);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pCategory`  
 Ukazatel na kategorii (uzel) Chcete-li odebrat.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k odebrání uzlu, který se také označuje jako kategorie, z ovládacího prvku strom. Použití [CMFCPropertySheet::AddTreeCategory](#addtreecategory) metody přidat uzel do ovládacího prvku strom.  
  
##  <a name="removepage"></a>CMFCPropertySheet::RemovePage  
 Stránky vlastností odebere ze seznamu vlastností.  
  
```  
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pPage`  
 Ukazatel na vlastnost stránky objekt, který reprezentuje stránku vlastností a odebrat. Nemůže být `NULL`.  
  
 [v]`nPage`  
 Index stránky, odeberte nule.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odstraní zadanou vlastnost stránku a zničí jeho přidružené okno. Stránka vlastností objektu, který `pPage` parametr určuje nebude odstraněn, až [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md) zavření časového intervalu.  
  
##  <a name="seticonslist"></a>CMFCPropertySheet::SetIconsList  
 Určuje seznam bitové kopie, které se používají v ovládacím prvku navigačním podokně aplikace Outlook.  
  
```  
BOOL SetIconsList(
    UINT uiImageListResID,  
    int cx,  
    COLORREF clrTransparent=RGB(255, 0, 255));
void SetIconsList(HIMAGELIST hIcons);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiImageListResID`  
 ID prostředku seznamu obrázků.  
  
 [v]`cx`  
 Šířka v pixelech ikony v seznamu obrázků.  
  
 [v]`clrTransparent`  
 Barva průhledný obrázek. Části bitové kopie, které jsou tato barva bude průhledná. Výchozí hodnota je purpurová barva, RGB(255,0,255).  
  
 [v]`hIcons`  
 Obslužná rutina do existujícího seznamu bitové kopie.  
  
### <a name="return-value"></a>Návratová hodnota  
 V metodě první přetížení syntaxe, `TRUE` Pokud tato metoda je úspěšné, jinak hodnota `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud seznam vlastností ve stylu aplikace Microsoft Outlook, rozhraní zobrazí seznam navigačních tlačítek, volá ovládací prvek podokně aplikace Outlook v levé části seznamu vlastností. Tuto metodu použijte k nastavení seznamu bitové kopie a použije se v podokně ovládacího prvku aplikace Outlook.  
  
 Další informace o metodách, které podporují tuto metodu, najdete v části [CImageList::Create](../../mfc/reference/cimagelist-class.md#create) a [CImageList::Add](../../mfc/reference/cimagelist-class.md#add). Další informace o tom, jak nastavit styl vlastností najdete v tématu [CMFCPropertySheet::SetLook](#setlook).  
  
##  <a name="setlook"></a>CMFCPropertySheet::SetLook  
 Určuje vzhled seznamu vlastností.  
  
```  
void SetLook(
    PropSheetLook look,  
    int nNavControlWidth=100);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`look`  
 Jedna z hodnot výčtu, která určuje vzhled seznamu vlastností. Výchozí styl pro seznam vlastností je `CMFCPropertySheet::PropSheetLook_Tabs`. Další informace najdete v tabulce v části poznámky v tomto tématu.  
  
 [v]`nNavControlWidth`  
 Šířka navigační ovládacího prvku v pixelech. Výchozí hodnota je 100.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete zobrazit seznam vlastností ve stylu jiné než výchozí, volejte tuto metodu, před vytvořením okna List vlastností.  
  
 Následující tabulka uvádí hodnot výčtu, která lze zadat v `look` parametr.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`CMFCPropertySheet::PropSheetLook_Tabs`|(Výchozí) Zobrazí kartu pro každou stránku vlastností. Karty se zobrazí v horní části seznamu vlastností a jsou skládaný, pokud existují další karty, než se vejde do jednoho řádku.|  
|`CMFCPropertySheet::PropSheetLook_OutlookBar`|Zobrazí seznam navigačních tlačítek v styl panelu Microsoft Outlook na levou stranu seznamu vlastností. Každé tlačítko v seznamu odpovídá stránky vlastností. Pokud existují další tlačítka, než se vejde v oblasti viditelné v seznamu, zobrazí rozhraní šipky posuvníku.|  
|`CMFCPropertySheet::PropSheetLook_Tree`|Zobrazí ovládacím prvkem strom v levé části seznamu vlastností. Jednotlivé nadřazené nebo podřízené uzly ovládacího prvku strom odpovídá stránky vlastností. Pokud existují další uzly, než se vejde v oblasti viditelné v ovládacím prvku stromu, zobrazí rozhraní šipky posuvníku.|  
|`CMFCPropertySheet::PropSheetLook_OneNoteTabs`|Zobrazí na kartě ve stylu Microsoft OneNote pro každou stránku vlastností. Rozhraní zobrazuje karty v horní části seznamu vlastností a šipky posuvníku Pokud existují další karty, než se vejde do jednoho řádku.|  
|`CMFCPropertySheet::PropSheetLook_List`|Zobrazí seznam v levé části seznamu vlastností. Každá položka seznamu odpovídá stránky vlastností. Pokud existují další položky seznamu, než se vejde v oblasti viditelné v seznamu, zobrazí rozhraní šipky posuvníku.|  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCPropertyPage – třída](../../mfc/reference/cmfcpropertypage-class.md)   
 [CMFCOutlookBar – třída](../../mfc/reference/cmfcoutlookbar-class.md)
