---
title: CMFCPropertySheet – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 45624c094d7ae656c50b55cc932762b7f9aa6476
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37854067"
---
# <a name="cmfcpropertysheet-class"></a>CMFCPropertySheet – třída
`CMFCPropertySheet` Třída podporuje seznam vlastností, kde každou stránku vlastností označuje symbolem karty stránky, tlačítka panelu nástrojů, řídicí uzel stromu nebo položka seznamu.  
  
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
|[CMFCPropertySheet::AddPageToTree](#addpagetotree)|Přidá nové stránky vlastností do ovládacího prvku stromu.|  
|[CMFCPropertySheet::AddTreeCategory](#addtreecategory)|Přidá nový uzel stromové struktury.|  
|[CMFCPropertySheet::EnablePageHeader](#enablepageheader)|Rezervuje prostor v horní části každé stránky k vykreslení vlastní hlavičku.|  
|[CMFCPropertySheet::GetHeaderHeight](#getheaderheight)|Získá výšku aktuální záhlaví.|  
|[CMFCPropertySheet::GetLook](#getlook)|Načte hodnotu výčtu, která určuje vzhled aktuální seznam vlastností.|  
|[CMFCPropertySheet::GetNavBarWidth](#getnavbarwidth)|Počet opakování šířka navigační panel v pixelech.|  
|[CMFCPropertySheet::GetTab](#gettab)|Načte objekt interní kartu ovládacího prvku, který podporuje aktuální ovládacího prvku seznam vlastností.|  
|`CMFCPropertySheet::GetThisClass`|Používá k získání ukazatele na rámec [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený k typu třídy.|  
|[CMFCPropertySheet::InitNavigationControl](#initnavigationcontrol)|Inicializuje vzhled ovládacího prvku aktuální seznam vlastností.|  
|[CMFCPropertySheet::OnActivatePage](#onactivatepage)|Volá se rozhraním, když je povolena stránka vlastností.|  
|[CMFCPropertySheet::OnDrawPageHeader](#ondrawpageheader)|Volá se rozhraním, chcete-li nakreslit vlastní vlastnosti záhlaví stránky.|  
|`CMFCPropertySheet::OnInitDialog`|Zpracovává [nezavěsíte](http://msdn.microsoft.com/library/windows/desktop/ms645428) zprávy. (Přepíše [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog).)|  
|[CMFCPropertySheet::OnRemoveTreePage](#onremovetreepage)|Volá se rozhraním odebrání ovládacím prvkem strom stránky vlastností.|  
|`CMFCPropertySheet::PreTranslateMessage`|Přeloží okno zprávy před odesláním do [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) a [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funkce Windows. (Přepíše `CPropertySheet::PreTranslateMessage`.)|  
|[CMFCPropertySheet::RemoveCategory](#removecategory)|Odebrání uzlu z ovládacího prvku stromu.|  
|[CMFCPropertySheet::RemovePage](#removepage)|Stránky vlastností se odebere ze seznamu vlastností.|  
|[CMFCPropertySheet::SetIconsList](#seticonslist)|Určuje seznam imagí, které se používají v ovládacím prvku navigačního podokna aplikace Outlook.|  
|[CMFCPropertySheet::SetLook](#setlook)|Určuje vzhled seznamu vlastností.|  
  
## <a name="remarks"></a>Poznámky  
 `CMFCPropertySheet` Třída reprezentuje seznam vlastností, označovaný také jako dialogová okna Karta. `CMFCPropertySheet` Třídy můžete zobrazit stránku vlastností v mnoha různými způsoby.  
  
 Proveďte následující kroky a použít `CMFCPropertySheet` ve vaší aplikaci:  
  
1.  Odvodit třídu z `CMFCPropertySheet` třídy a název třídy, například CMyPropertySheet.  
  
2.  Vytvoření [cmfcpropertypage –](../../mfc/reference/cmfcpropertypage-class.md) objekt pro každou stránku vlastností.  
  
3.  Volání [CMFCPropertySheet::SetLook](#setlook) metoda v konstruktoru CMyPropertySheet. Parametr této metody Určuje, že stránky vlastností se zobrazí jako karty podél horní nebo nalevo od vlastnosti. karty ve stylu seznamu vlastností Microsoft OneNote; tlačítka v ovládacím prvku panel nástrojů aplikace Microsoft Outlook; uzly na ovládací prvek stromu; nebo jako seznam položek na levé straně okna vlastností.  
  
4.  Pokud vytvoříte seznam vlastností ve stylu panel nástrojů aplikace Microsoft Outlook, zavolejte [CMFCPropertySheet::SetIconsList](#seticonslist) metody pro přidružení seznamu obrázků spolu s stránky vlastností.  
  
5.  Volání [CMFCPropertySheet::AddPage](#addpage) metoda pro každou stránku vlastností.  
  
6.  Vytvoření `CMFCPropertySheet` řídit a volat jeho `DoModal` metoda.  
  
## <a name="illustrations"></a>Obrázky  
 Následující obrázek znázorňuje seznam vlastností, která je ve stylu integrovaném panelu nástrojů aplikace Microsoft Outlook. Panel nástrojů aplikace Outlook se zobrazí na levé straně seznam vlastností.  
  
 ![Barva CMFCPropertySheet – ovládací prvky](../../mfc/reference/media/cmfcpropertysheet_color.png "cmfcpropertysheet_color")  
  
 Následující obrázek znázorňuje seznam vlastností, která obsahuje [cmfcpropertygridctrl – třída](../../mfc/reference/cmfcpropertygridctrl-class.md) objektu. Tento objekt je seznam vlastností ve stylu standardní společný seznam vlastností ovládacích prvků.  
  
 ![CMFCPropertySheet – seznam a vlastnosti ovládacích prvků](../../mfc/reference/media/cmfcpropertysheet_list.png "cmfcpropertysheet_list")  
  
 Následující obrázek znázorňuje seznam vlastností, která je ve stylu ovládacího prvku stromu.  
  
 ![Strom](../../mfc/reference/media/proptree.png "proptree")  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CPropertySheet](../../mfc/reference/cpropertysheet-class.md)  
  
 [CMFCPropertySheet –](../../mfc/reference/cmfcpropertysheet-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxpropertysheet.h  
  
##  <a name="addpage"></a>  CMFCPropertySheet::AddPage  
 Na stránce se přidá do seznamu vlastností.  
  
```  
void AddPage(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *Fyzická_stránka*  
 Ukazatel na objekt stránky. Tento parametr nemůže mít hodnotu NULL.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda přidá zadanou vlastnost stránku kartě úplně vpravo v seznamu vlastností. Proto tuto metodu použijte pro přidání stránek v pořadí zleva doprava.  
  
 Pokud je seznam vlastností ve stylu Microsoft Outlook, zobrazí rozhraní seznam navigačních tlačítek v levé části seznamu vlastností. Až tato metoda přidá stránky vlastností, přidá do seznamu odpovídajících tlačítko. Pro zobrazení stránky vlastností, klikněte na jeho odpovídající tlačítko. Další informace o stylech seznamů vlastností najdete v tématu [CMFCPropertySheet::SetLook](#setlook).  
  
##  <a name="addpagetotree"></a>  CMFCPropertySheet::AddPageToTree  
 Přidá nové stránky vlastností do ovládacího prvku stromu.  
  
```  
void AddPageToTree(
    CMFCPropertySheetCategoryInfo* pCategory,  
    CMFCPropertyPage* pPage,  
    int nIconNum=-1,  
    int nSelIconNum=-1);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pCategory*  
 Ukazatel na nadřazený uzel stromu, nebo hodnota NULL pro zadanou stránku přidružit uzel nejvyšší úrovně. Volání [CMFCPropertySheet::AddTreeCategory](#addtreecategory) metodu k získání tohoto ukazatele.  
  
 [in] *Fyzická_stránka*  
 Ukazatel na objekt stránky vlastností.  
  
 [in] *nIconNum*  
 Index založený na nule ikony nebo -1, pokud je použita žádná ikona. Pokud není vybrána na stránce, zobrazí se na ikonu vedle na stránce vlastností ovládacího prvku stromu. Výchozí hodnota je -1.  
  
 [in] *nSelIconNum*  
 Index založený na nule ikony nebo -1, pokud je použita žádná ikona. Pokud je vybrána na stránce, zobrazí se na ikonu vedle na stránce vlastností ovládacího prvku stromu. Výchozí hodnota je -1.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda přidá jako listový ovládacím prvkem strom stránky vlastností. Přidání stránky vlastností, vytvořit `CMFCPropertySheet` objektů, zavolejte [CMFCPropertySheet::SetLook](#setlook) metodu s *vypadat* parametr nastaven na `CMFCPropertySheet::PropSheetLook_Tree`a potom tuto metodu použijte k přidání stránky vlastností .  
  
##  <a name="addtreecategory"></a>  CMFCPropertySheet::AddTreeCategory  
 Přidá nový uzel stromové struktury.  
  
```  
CMFCPropertySheetCategoryInfo* AddTreeCategory(
    LPCTSTR lpszLabel,  
    int nIconNum=-1,  
    int nSelectedIconNum=-1,  
    const CMFCPropertySheetCategoryInfo* pParentCategory=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *lpszLabel*  
 Název uzlu.  
  
 [in] *nIconNum*  
 Index založený na nule ikony nebo -1, pokud je použita žádná ikona. Pokud není vybrána na stránce, zobrazí se na ikonu vedle na stránce vlastností ovládacího prvku stromu. Výchozí hodnota je -1.  
  
 [in] *nSelectedIconNum*  
 Index založený na nule ikony nebo -1, pokud je použita žádná ikona. Pokud je vybrána na stránce, zobrazí se na ikonu vedle na stránce vlastností ovládacího prvku stromu. Výchozí hodnota je -1.  
  
 [in] *pParentCategory*  
 Ukazatel na nadřazený uzel stromu, nebo hodnota NULL pro zadanou stránku přidružit uzel nejvyšší úrovně. Nastavte tento parametr se [CMFCPropertySheet::AddTreeCategory](#addtreecategory) metody.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na novém uzlu ve stromovém zobrazení.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte, chcete-li přidat nový uzel, který se také označuje jako kategorie, do ovládacího prvku stromu. Přidat uzel, vytvořit `CMFCPropertySheet` objektů, zavolejte [CMFCPropertySheet::SetLook](#setlook) metodu s *vypadat* parametr nastaven na `CMFCPropertySheet::PropSheetLook_Tree`a potom tuto metodu použijte k přidání uzlu.  
  
 Používat návratovou hodnotu této metody v následných voláních [CMFCPropertySheet::AddPageToTree](#addpagetotree) a [CMFCPropertySheet::AddTreeCategory](#addtreecategory).  
  
##  <a name="cmfcpropertysheet"></a>  CMFCPropertySheet::CMFCPropertySheet  
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
 [in] *pszCaption*  
 Řetězec, který obsahuje titulek list vlastností. Nemůže mít hodnotu NULL.  
  
 [in] *nIDCaption*  
 ID prostředku, který obsahuje titulek list vlastností.  
  
 [in] *pParentWnd*  
 Ukazatel do nadřazeného okna vlastností nebo hodnota NULL, pokud je okno nadřazeného hlavního okna aplikace. Výchozí hodnota je NULL.  
  
 [in] *iSelectPage*  
 Index založený na nule hlavní vlastnosti stránky. Výchozí hodnota je 0.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu parametry [CPropertySheet::CPropertySheet](../../mfc/reference/cpropertysheet-class.md#cpropertysheet) konstruktoru.  
  
##  <a name="enablepageheader"></a>  CMFCPropertySheet::EnablePageHeader  
 Rezervuje prostor v horní části každé stránky k vykreslení vlastní hlavičku.  
  
```  
void EnablePageHeader(int nHeaderHeight);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nHeaderHeight*  
 Výška záhlaví v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Použít hodnotu *nHeaderHeight* přepište parametr kreslení vlastní hlavičky, [CMFCPropertySheet::OnDrawPageHeader](#ondrawpageheader) metody.  
  
##  <a name="getheaderheight"></a>  CMFCPropertySheet::GetHeaderHeight  
 Získá výšku aktuální záhlaví.  
  
```  
int GetHeaderHeight() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výška záhlaví v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Volání [CMFCPropertySheet::EnablePageHeader](#enablepageheader) metoda před voláním této metody.  
  
##  <a name="getlook"></a>  CMFCPropertySheet::GetLook  
 Načte hodnotu výčtu, která určuje vzhled aktuální seznam vlastností.  
  
```  
PropSheetLook GetLook() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Jedna z hodnot výčtu, které určují vzhled seznamu vlastností. Seznam možných hodnot, najdete v tabulce výčtu v části poznámky [CMFCPropertySheet::SetLook](#setlook).  
  
##  <a name="getnavbarwidth"></a>  CMFCPropertySheet::GetNavBarWidth  
 Získává šířku objektu na navigačním panelu.  
  
```  
int GetNavBarWidth() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Šířka panelu navigace v pixelech.  
  
##  <a name="gettab"></a>  CMFCPropertySheet::GetTab  
 Načte objekt interní kartu ovládacího prvku, který podporuje aktuální ovládacího prvku seznam vlastností.  
  
```  
CMFCTabCtrl& GetTab() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Objekt interní kartu ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
 Seznam vlastností můžete nastavit, aby se zobrazovala v různých stylů, jako je například ovládací prvek stromu seznam navigačních tlačítek nebo sadu s kartami stránek.  
  
 Před voláním této metody zavolejte [CMFCPropertySheet::SetLook](#setlook) metody nastavte vzhled ovládacího prvku seznam vlastností. Zavolejte [CMFCPropertySheet::InitNavigationControl](#initnavigationcontrol) metody k inicializaci objektu interní kartu ovládacího prvku. Pomocí této metody můžete načíst objekt ovládacího prvku karty a pak použít tento objekt pro práci se karty v seznamu vlastností.  
  
 Tato metoda nepodmíněné výrazy v režimu ladění, pokud není nastavena ovládacího prvku seznam vlastností zobrazí ve stylu Microsoft OneNote.  
  
##  <a name="initnavigationcontrol"></a>  CMFCPropertySheet::InitNavigationControl  
 Inicializuje vzhled ovládacího prvku aktuální seznam vlastností.  
  
```  
virtual CWnd* InitNavigationControl();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na okno ovládacího prvku seznam vlastností.  
  
### <a name="remarks"></a>Poznámky  
 Prvku seznamu vlastností se mohou objevit v několika různých formách, jako je například sada stránky se záložkami, ovládací prvek stromu nebo seznamu navigačních tlačítek. Použití [CMFCPropertySheet::SetLook](#setlook) metodu k určení vzhledu ovládacího prvku seznam vlastností.  
  
##  <a name="onactivatepage"></a>  CMFCPropertySheet::OnActivatePage  
 Volá se rozhraním, když je povolena stránka vlastností.  
  
```  
virtual void OnActivatePage(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *Fyzická_stránka*  
 Ukazatel na objekt stránky vlastností, který představuje stránku vlastnost enabled.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení tato metoda zajišťuje, že vlastnost enabled stránky je přesunut do oblasti zobrazení. Pokud styl aktuální seznam vlastností obsahuje podokno Microsoft Outlook, tato metoda nastaví na odpovídající tlačítko Outlook na zaškrtnutém stavu.  
  
##  <a name="ondrawpageheader"></a>  CMFCPropertySheet::OnDrawPageHeader  
 Volá se rozhraním, chcete-li nakreslit záhlaví stránky přizpůsobených vlastností.  
  
```  
virtual void OnDrawPageHeader(
    CDC* pDC,  
    int nPage,  
    CRect rectHeader);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *primárního řadiče domény*  
 Ukazatel na kontext zařízení.  
  
 [in] *nPage*  
 Číslo stránky vlastností založený na nule.  
  
 [in] *rectHeader*  
 Ohraničující obdélník, který určuje, kde chcete-li nakreslit záhlaví.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení tato metoda nemá žádný účinek. Pokud tuto metodu přepíšete, zavolejte [CMFCPropertySheet::EnablePageHeader](#enablepageheader) metoda před rozhraní volá tuto metodu.  
  
##  <a name="onremovetreepage"></a>  CMFCPropertySheet::OnRemoveTreePage  
 Volá se rozhraním odebrání ovládacím prvkem strom stránky vlastností.  
  
```  
virtual BOOL OnRemoveTreePage(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *Fyzická_stránka*  
 Ukazatel na objekt stránky vlastností, který představuje stránky vlastností k odebrání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.  
  
##  <a name="removecategory"></a>  CMFCPropertySheet::RemoveCategory  
 Odebrání uzlu z ovládacího prvku stromu.  
  
```  
void RemoveCategory(CMFCPropertySheetCategoryInfo* pCategory);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pCategory*  
 Ukazatel na kategorii (uzly) Chcete-li odebrat.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k odebrání uzlu, který se také označuje jako kategorie, z ovládacího prvku stromu. Použití [CMFCPropertySheet::AddTreeCategory](#addtreecategory) metody přidat uzel do ovládacího prvku stromu.  
  
##  <a name="removepage"></a>  CMFCPropertySheet::RemovePage  
 Stránky vlastností se odebere ze seznamu vlastností.  
  
```  
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *Fyzická_stránka*  
 Ukazatel na objekt stránky vlastností, představující stránky vlastností k odebrání. Nemůže mít hodnotu NULL.  
  
 [in] *nPage*  
 Z nuly vycházející index stránky k odebrání.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odebere zadané vlastnosti stránky a odstraní přidružené okna. Na stránce vlastností objektu, který *Fyzická_stránka* parametr určuje není zničen, dokud [CMFCPropertySheet –](../../mfc/reference/cmfcpropertysheet-class.md) zavření časového intervalu.  
  
##  <a name="seticonslist"></a>  CMFCPropertySheet::SetIconsList  
 Určuje seznam imagí, které se používají v ovládacím prvku navigačního podokna aplikace Outlook.  
  
```  
BOOL SetIconsList(
    UINT uiImageListResID,  
    int cx,  
    COLORREF clrTransparent=RGB(255, 0, 255));
void SetIconsList(HIMAGELIST hIcons);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *uiImageListResID*  
 ID prostředku ze seznamu obrázků.  
  
 [in] *cx*  
 Šířka v pixelech ikony v seznamu obrázků.  
  
 [in] *clrTransparent*  
 Barva průhledný obrázek. Součástí image, které jsou tato barva bude průhledný. Výchozí hodnota je barva purpurová, RGB(255,0,255).  
  
 [in] *hIcons*  
 Popisovač pro existující seznam obrázků.  
  
### <a name="return-value"></a>Návratová hodnota  
 V první metodě přetížení syntaxe, nastavena hodnota TRUE v případě, že tato metoda je úspěšná. v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je seznam vlastností ve stylu Microsoft Outlook, zobrazí rozhraní seznam navigačních tlačítek, volá ovládacího prvku podokno Outlooku, v levé části seznamu vlastností. Tuto metodu použijte k nastavení seznamu image používané ovládací prvek podokna aplikace Outlook.  
  
 Další informace o metodách, které podporují tuto metodu, najdete v části [CImageList::Create](../../mfc/reference/cimagelist-class.md#create) a [CImageList::Add](../../mfc/reference/cimagelist-class.md#add). Další informace o tom, jak nastavit styl seznamu vlastností najdete v tématu [CMFCPropertySheet::SetLook](#setlook).  
  
##  <a name="setlook"></a>  CMFCPropertySheet::SetLook  
 Určuje vzhled seznamu vlastností.  
  
```  
void SetLook(
    PropSheetLook look,  
    int nNavControlWidth=100);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *vypadat*  
 Jedna z hodnot výčtu, které určují vzhled seznamu vlastností. Výchozí styl seznamu vlastností je `CMFCPropertySheet::PropSheetLook_Tabs`. Další informace najdete v tabulce v části poznámky v tomto tématu.  
  
 [in] *nNavControlWidth*  
 Šířka navigaci ovládacího prvku v pixelech. Výchozí hodnota je 100.  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li zobrazit seznam vlastností ve stylu jiné než výchozí, volejte tuto metodu, před vytvořením okna List vlastností.  
  
 V následující tabulce jsou uvedeny hodnoty výčtu, které lze zadat v *vypadat* parametru.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`CMFCPropertySheet::PropSheetLook_Tabs`|(Výchozí) Zobrazuje kartu pro každou stránku vlastností. Karty se zobrazí v horní části stránky vlastností a jsou uspořádány vedle, pokud existují další záložky, než se vejde do jednoho řádku.|  
|`CMFCPropertySheet::PropSheetLook_OutlookBar`|Zobrazí seznam navigačních tlačítek ve stylu na panelu aplikace Microsoft Outlook, v levé části seznamu vlastností. Stránka vlastností odpovídá každé tlačítko v seznamu. Pokud existují další tlačítka, než pojme viditelná oblast v seznamu zobrazí rozhraní šipky.|  
|`CMFCPropertySheet::PropSheetLook_Tree`|Ovládací prvek stromu se zobrazí na levé straně seznam vlastností. Každý uzel nadřazené nebo podřízené ovládacího prvku strom odpovídá stránky vlastností. Pokud existuje více uzlů, než pojme viditelná oblast ovládacího prvku strom, zobrazí rozhraní šipky.|  
|`CMFCPropertySheet::PropSheetLook_OneNoteTabs`|Na kartě se zobrazí ve stylu Microsoft OneNote pro každou stránku vlastností. Rozhraní zobrazí karty v horní části stránky vlastností a šipky posuvníku Pokud existují další záložky, než se vejde na jednom řádku.|  
|`CMFCPropertySheet::PropSheetLook_List`|Zobrazí seznam v levé části seznamu vlastností. Každá položka seznamu odpovídá stránky vlastností. Pokud existují další položky seznamu, než pojme viditelná oblast v seznamu zobrazí rozhraní šipky.|  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [Cmfcpropertypage – třída](../../mfc/reference/cmfcpropertypage-class.md)   
 [CMFCOutlookBar – třída](../../mfc/reference/cmfcoutlookbar-class.md)
