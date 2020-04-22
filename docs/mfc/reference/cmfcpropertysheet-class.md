---
title: Třída cmfcpropertysheet
ms.date: 11/19/2018
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
ms.openlocfilehash: 9b1bb2ce9a957b9cd9f7add983b4da7a228d7a1d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750057"
---
# <a name="cmfcpropertysheet-class"></a>Třída cmfcpropertysheet

Třída `CMFCPropertySheet` podporuje seznam vlastností, kde je každá stránka vlastností označena kartou stránky, tlačítkem panelu nástrojů, uzlem ovládacího prvku stromu nebo položkou seznamu.

## <a name="syntax"></a>Syntaxe

```
class CMFCPropertySheet : public CPropertySheet
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCPropertySheet::CMFCPropertySheet](#cmfcpropertysheet)|Vytvoří `CMFCPropertySheet` objekt.|
|`CMFCPropertySheet::~CMFCPropertySheet`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCPropertySheet::Přidat stránku](#addpage)|Přidá stránku do seznamu vlastností.|
|[CMFCPropertySheet::AddPageToTree](#addpagetotree)|Přidá novou stránku vlastností do ovládacího prvku stromu.|
|[CMFCPropertySheet::Kategorie AddTree](#addtreecategory)|Přidá nový uzel do stromového ovládacího prvku.|
|[CMFCPropertySheet::EnablePageHeader](#enablepageheader)|Rezervuje místo v horní části každé stránky a nakreslí vlastní záhlaví.|
|[CMFCPropertySheet::GetHeaderHeight](#getheaderheight)|Načte výšku aktuální hlavičky.|
|[CMFCPropertySheet::GetLook](#getlook)|Načte hodnotu výčtu, která určuje vzhled aktuálního seznamu vlastností.|
|[CMFCPropertySheet::GetNavBarWidth](#getnavbarwidth)|Opakuje šířku navigačního panelu v pixelech.|
|[CMFCPropertySheet::GetTab](#gettab)|Načte objekt ovládacího prvku vnitřní tabulátor, který podporuje aktuální ovládací prvek listu vlastností.|
|`CMFCPropertySheet::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objektu, který je přidružen k tomuto typu třídy.|
|[CMFCPropertySheet::InitNavigationControl](#initnavigationcontrol)|Inicializuje vzhled aktuálního ovládacího prvku listu vlastností.|
|[CMFCPropertySheet::OnActivatePage](#onactivatepage)|Volat rámci při je povolena stránka vlastností.|
|[CMFCPropertySheet::OnDrawPageHeader](#ondrawpageheader)|Volat rámci nakreslit záhlaví vlastní stránky vlastností.|
|`CMFCPropertySheet::OnInitDialog`|Zpracovává [zprávu WM_INITDIALOG.](/windows/win32/dlgbox/wm-initdialog) (Přepíše [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog).)|
|[CMFCPropertySheet::OnRemoveTreePage](#onremovetreepage)|Volat rámci odebrat stránku vlastností ze stromu ovládacího prvku.|
|`CMFCPropertySheet::PreTranslateMessage`|Přeloží zprávy okna před jejich odesláním do funkcí [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) systému Windows. (Přepíše `CPropertySheet::PreTranslateMessage`.)|
|[CMFCPropertySheet::Odebratkategorie](#removecategory)|Odebere uzel z ovládacího prvku stromu.|
|[CMFCPropertySheet::RemovePage](#removepage)|Odebere stránku vlastností ze seznamu vlastností.|
|[CMFCPropertySheet:SetIconsList](#seticonslist)|Určuje seznam obrázků, které se používají v navigačním ovládacím prvku podokna aplikace Outlook.|
|[CMFCPropertySheet::SetLook](#setlook)|Určuje vzhled seznamu vlastností.|

## <a name="remarks"></a>Poznámky

Třída `CMFCPropertySheet` představuje seznamy vlastností, označované také jako dialogová okna karet. Třída `CMFCPropertySheet` může zobrazit stránku vlastností různými způsoby.

Chcete-li třídu `CMFCPropertySheet` použít v aplikaci, postupujte takto:

1. Odvodit `CMFCPropertySheet` třídu z třídy a pojmenovat třídu, například CMyPropertySheet.

1. Vytvořte objekt [CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md) pro každou stránku vlastností.

1. Volání [CMFCPropertySheet::SetLook](#setlook) metoda v konstruktoru CMyPropertySheet. Parametr této metody určuje, že stránky vlastností se zobrazí buď jako karty v horní nebo levé části seznamu vlastností; karty ve stylu seznamu vlastností Microsoft OneNote; tlačítka na ovládacím prvku panelu nástrojů aplikace Microsoft Outlook; uzly na stromovládací prvek; nebo jako seznam položek na levé straně seznamu vlastností.

1. Pokud vytvoříte seznam vlastností ve stylu panelu nástrojů aplikace Microsoft Outlook, zavolejte metodu [CMFCPropertySheet::SetIconsList](#seticonslist) a přidružte seznam obrázků ke stránkám vlastností.

1. Volání [metody CMFCPropertySheet::AddPage](#addpage) pro každou stránku vlastností.

1. Vytvořte `CMFCPropertySheet` ovládací prvek `DoModal` a volání jeho metody.

## <a name="illustrations"></a>Ilustrace

Následující obrázek znázorňuje seznam vlastností, který je ve stylu vloženého panelu nástrojů aplikace Microsoft Outlook. Panel nástrojů aplikace Outlook se zobrazí na levé straně seznamu vlastností.

![Ovládací prvky barev CMFCPropertySheet](../../mfc/reference/media/cmfcpropertysheet_color.png "Ovládací prvky barev CMFCPropertySheet")

Následující obrázek znázorňuje seznam vlastností, který obsahuje objekt [třídy CMFCPropertyGridCtrl.](../../mfc/reference/cmfcpropertygridctrl-class.md) Tento objekt je seznam vlastností ve stylu standardního společného seznamu vlastností ovládacích prvků.

![Ovládací prvky seznamu a vlastností cmfcpropertysheet](../../mfc/reference/media/cmfcpropertysheet_list.png "Ovládací prvky seznamu a vlastností cmfcpropertysheet")

Následující obrázek znázorňuje seznam vlastností, který je ve stylu stromového ovládacího prvku.

![Strom vlastností](../../mfc/reference/media/proptree.png "Strom vlastností")

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

[CmFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxpropertysheet.h

## <a name="cmfcpropertysheetaddpage"></a><a name="addpage"></a>CMFCPropertySheet::Přidat stránku

Přidá stránku do seznamu vlastností.

```cpp
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parametry

*pStránka*<br/>
[v] Ukazatel na objekt stránky. Tento parametr nemůže mít hodnotu NULL.

### <a name="remarks"></a>Poznámky

Tato metoda přidá zadanou stránku vlastností jako kartu zcela vpravo v seznamu vlastností. Proto použijte tuto metodu k přidání stránek v pořadí zleva doprava.

Pokud je seznam vlastností ve stylu aplikace Microsoft Outlook, zobrazí se v rámci seznam navigačních tlačítek v levé části seznamu vlastností. Poté, co tato metoda přidá stránku vlastností, přidá odpovídající tlačítko do seznamu. Chcete-li zobrazit stránku vlastností, klepněte na odpovídající tlačítko. Další informace o stylech seznamů vlastností naleznete v tématu [CMFCPropertySheet::SetLook](#setlook).

## <a name="cmfcpropertysheetaddpagetotree"></a><a name="addpagetotree"></a>CMFCPropertySheet::AddPageToTree

Přidá novou stránku vlastností do ovládacího prvku stromu.

```cpp
void AddPageToTree(
    CMFCPropertySheetCategoryInfo* pCategory,
    CMFCPropertyPage* pPage,
    int nIconNum=-1,
    int nSelIconNum=-1);
```

### <a name="parameters"></a>Parametry

*pKategorie*<br/>
[v] Ukazatel na uzel nadřazeného stromu nebo NULL přidružit zadanou stránku k uzlu nejvyšší úrovně. Volání [CMFCPropertySheet::AddTreeCategory](#addtreecategory) metoda získat tento ukazatel.

*pStránka*<br/>
[v] Ukazatel na objekt stránky vlastností.

*nIconNum*<br/>
[v] Nulový index ikony nebo -1, pokud není použita žádná ikona. Ikona se zobrazí vedle stránky vlastností ovládacího prvku stromu, pokud stránka není vybrána. Výchozí hodnota je -1.

*nSelIconNum*<br/>
[v] Nulový index ikony nebo -1, pokud není použita žádná ikona. Ikona se zobrazí vedle stránky vlastností ovládacího prvku stromu, když je stránka vybraná. Výchozí hodnota je -1.

### <a name="remarks"></a>Poznámky

Tato metoda přidá stránku vlastností jako list stromového ovládacího prvku. Chcete-li přidat stránku `CMFCPropertySheet` vlastností, vytvořte objekt, zavolejte metodu [CMFCPropertySheet::SetLook](#setlook) s parametrem *look* nastaveným na `CMFCPropertySheet::PropSheetLook_Tree`a pak použijte tuto metodu k přidání stránky vlastností.

## <a name="cmfcpropertysheetaddtreecategory"></a><a name="addtreecategory"></a>CMFCPropertySheet::Kategorie AddTree

Přidá nový uzel do stromového ovládacího prvku.

```
CMFCPropertySheetCategoryInfo* AddTreeCategory(
    LPCTSTR lpszLabel,
    int nIconNum=-1,
    int nSelectedIconNum=-1,
    const CMFCPropertySheetCategoryInfo* pParentCategory=NULL);
```

### <a name="parameters"></a>Parametry

*popisek lpsz*<br/>
[v] Název uzlu.

*nIconNum*<br/>
[v] Nulový index ikony nebo -1, pokud není použita žádná ikona. Ikona se zobrazí vedle stránky vlastností ovládacího prvku stromu, pokud stránka není vybrána. Výchozí hodnota je -1.

*nSelectedIconNum*<br/>
[v] Nulový index ikony nebo -1, pokud není použita žádná ikona. Ikona se zobrazí vedle stránky vlastností ovládacího prvku stromu, když je stránka vybraná. Výchozí hodnota je -1.

*kategorie pParentCategory*<br/>
[v] Ukazatel na uzel nadřazeného stromu nebo NULL přidružit zadanou stránku k uzlu nejvyšší úrovně. Nastavte tento parametr pomocí metody [CMFCPropertySheet::AddTreeCategory.](#addtreecategory)

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nový uzel v ovládacím prvku stromu.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete do stromového ovládacího prvku přidat nový uzel, který je také označován jako kategorie. Chcete-li přidat uzel, `CMFCPropertySheet` vytvořte objekt, zavolejte metodu [CMFCPropertySheet::SetLook](#setlook) s parametrem *look* nastaveným na `CMFCPropertySheet::PropSheetLook_Tree`. a pak pomocí této metody přidejte uzel.

Návratovou hodnotu této metody použijte při následných voláních [cmfcpropertysheet::AddPageToTree](#addpagetotree) a [CMFCPropertySheet::AddTreeCategory](#addtreecategory).

## <a name="cmfcpropertysheetcmfcpropertysheet"></a><a name="cmfcpropertysheet"></a>CMFCPropertySheet::CMFCPropertySheet

Vytvoří `CMFCPropertySheet` objekt.

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

*pszCaption pszCaption pszCaption psz*<br/>
[v] Řetězec, který obsahuje titulek seznamu vlastností. Nemůže být null.

*nIDTitulek*<br/>
[v] ID prostředku, které obsahuje titulek seznamu vlastností.

*pParentWnd*<br/>
[v] Ukazatel na nadřazené okno seznamu vlastností nebo NULL, pokud je nadřazené okno hlavním oknem aplikace. Výchozí hodnota je NULL.

*iSelectPage*<br/>
[v] Index na základě nuly na stránce nejvyšší vlastnosti. Výchozí hodnota je 0.

### <a name="remarks"></a>Poznámky

Další informace naleznete v parametrech konstruktoru [CPropertySheet::CPropertySheet.](../../mfc/reference/cpropertysheet-class.md#cpropertysheet)

## <a name="cmfcpropertysheetenablepageheader"></a><a name="enablepageheader"></a>CMFCPropertySheet::EnablePageHeader

Rezervuje místo v horní části každé stránky a nakreslí vlastní záhlaví.

```cpp
void EnablePageHeader(int nHeaderHeight);
```

### <a name="parameters"></a>Parametry

*nVýška záhlaví*<br/>
[v] Výška záhlaví v pixelech.

### <a name="remarks"></a>Poznámky

Chcete-li použít hodnotu parametru *nHeaderHeight* k nakreslení vlastního záhlaví, přepište metodu [CMFCPropertySheet::OnDrawPageHeader.](#ondrawpageheader)

## <a name="cmfcpropertysheetgetheaderheight"></a><a name="getheaderheight"></a>CMFCPropertySheet::GetHeaderHeight

Načte výšku aktuální hlavičky.

```
int GetHeaderHeight() const;
```

### <a name="return-value"></a>Návratová hodnota

Výška záhlaví v pixelech.

### <a name="remarks"></a>Poznámky

Před voláním této metody zavolejte metodu [CMFCPropertySheet::EnablePageHeader.](#enablepageheader)

## <a name="cmfcpropertysheetgetlook"></a><a name="getlook"></a>CMFCPropertySheet::GetLook

Načte hodnotu výčtu, která určuje vzhled aktuálního seznamu vlastností.

```
PropSheetLook GetLook() const;
```

### <a name="return-value"></a>Návratová hodnota

Jedna z hodnot výčtu, která určuje vzhled seznamu vlastností. Seznam možných hodnot naleznete v tabulce výčtu v části Poznámky [na CMFCPropertySheet::SetLook](#setlook).

## <a name="cmfcpropertysheetgetnavbarwidth"></a><a name="getnavbarwidth"></a>CMFCPropertySheet::GetNavBarWidth

Získá šířku navigačního panelu.

```
int GetNavBarWidth() const;
```

### <a name="return-value"></a>Návratová hodnota

Šířka navigačního panelu v pixelech.

## <a name="cmfcpropertysheetgettab"></a><a name="gettab"></a>CMFCPropertySheet::GetTab

Načte objekt ovládacího prvku vnitřní tabulátor, který podporuje aktuální ovládací prvek listu vlastností.

```
CMFCTabCtrl& GetTab() const;
```

### <a name="return-value"></a>Návratová hodnota

Objekt ovládacího prvku vnitřní tabulátor.

### <a name="remarks"></a>Poznámky

Seznam vlastností můžete nastavit tak, aby se zobrazil v různých stylech, například v ovládacím prvku stromu, v seznamu navigačních tlačítek nebo v sadě stránek s kartami.

Před voláním této metody zavolejte metodu [CMFCPropertySheet::SetLook](#setlook) a nastavte vzhled ovládacího prvku listu vlastností. Potom zavolejte metodu [CMFCPropertySheet::InitNavigationControl](#initnavigationcontrol) a inicializujte objekt ovládacího prvku vnitřní karty. Pomocí této metody můžete načíst objekt ovládacího prvku tabulátoru a potom použít tento objekt k práci s kartami na seznamu vlastností.

Tato metoda uplatňuje v režimu ladění, pokud ovládací prvek listu vlastností není nastavena na zobrazení ve stylu Microsoft OneNote.

## <a name="cmfcpropertysheetinitnavigationcontrol"></a><a name="initnavigationcontrol"></a>CMFCPropertySheet::InitNavigationControl

Inicializuje vzhled aktuálního ovládacího prvku listu vlastností.

```
virtual CWnd* InitNavigationControl();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na okno ovládacího prvku listu vlastností.

### <a name="remarks"></a>Poznámky

Ovládací prvek listu vlastností se může zobrazit v několika různých formách, například v sadě stránek s kartami, stromové masce nebo v seznamu navigačních tlačítek. Pomocí metody [CMFCPropertySheet::SetLook](#setlook) určete vzhled ovládacího prvku listu vlastností.

## <a name="cmfcpropertysheetonactivatepage"></a><a name="onactivatepage"></a>CMFCPropertySheet::OnActivatePage

Volat rámci při je povolena stránka vlastností.

```
virtual void OnActivatePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parametry

*pStránka*<br/>
[v] Ukazatel na objekt stránky vlastností, který představuje stránku vlastností povolenou.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda zajišťuje, že stránka vlastností povolena je posunuta do zobrazení. Pokud styl aktuálního seznamu vlastností obsahuje podokno aplikace Microsoft Outlook, tato metoda nastaví odpovídající tlačítko aplikace Outlook do kontrolovaného stavu.

## <a name="cmfcpropertysheetondrawpageheader"></a><a name="ondrawpageheader"></a>CMFCPropertySheet::OnDrawPageHeader

Volat rámci nakreslit záhlaví pro vlastní stránku vlastností.

```
virtual void OnDrawPageHeader(
    CDC* pDC,
    int nPage,
    CRect rectHeader);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení.

*nStránka*<br/>
[v] Číslo stránky vlastnosti založené na nule.

*rectHeader*<br/>
[v] Ohraničující obdélník, který určuje, kde chcete nakreslit záhlaví.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda neprovede žádnou akci. Pokud tuto metodu přepíšete, zavolejte metodu [CMFCPropertySheet::EnablePageHeader](#enablepageheader) před tím, než framework tuto metodu zavolá.

## <a name="cmfcpropertysheetonremovetreepage"></a><a name="onremovetreepage"></a>CMFCPropertySheet::OnRemoveTreePage

Volat rámci odebrat stránku vlastností ze stromu ovládacího prvku.

```
virtual BOOL OnRemoveTreePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parametry

*pStránka*<br/>
[v] Ukazatel na objekt stránky vlastností, který představuje stránku vlastnosti odebrat.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

## <a name="cmfcpropertysheetremovecategory"></a><a name="removecategory"></a>CMFCPropertySheet::Odebratkategorie

Odebere uzel z ovládacího prvku stromu.

```cpp
void RemoveCategory(CMFCPropertySheetCategoryInfo* pCategory);
```

### <a name="parameters"></a>Parametry

*pKategorie*<br/>
[v] Ukazatel na kategorii (uzel), který chcete odebrat.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete odebrat uzel, který je také označován jako kategorie, z ovládacího prvku stromu. Pomocí metody [CMFCPropertySheet::AddTreeCategory](#addtreecategory) přidejte uzel do stromového ovládacího prvku.

## <a name="cmfcpropertysheetremovepage"></a><a name="removepage"></a>CMFCPropertySheet::RemovePage

Odebere stránku vlastností ze seznamu vlastností.

```cpp
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>Parametry

*pStránka*<br/>
[v] Ukazatel na objekt stránky vlastností, který představuje stránku vlastnosti odebrat. Nemůže být null.

*nStránka*<br/>
[v] Nulový index stránky odebrat.

### <a name="remarks"></a>Poznámky

Tato metoda odebere stránku zadané vlastnosti a zničí její přidružené okno. Objekt stránky vlastností, který určuje parametr *pPage,* není zničen, dokud nebude okno [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md) zavřeno.

## <a name="cmfcpropertysheetseticonslist"></a><a name="seticonslist"></a>CMFCPropertySheet:SetIconsList

Určuje seznam obrázků, které se používají v navigačním ovládacím prvku podokna aplikace Outlook.

```
BOOL SetIconsList(
    UINT uiImageListResID,
    int cx,
    COLORREF clrTransparent=RGB(255, 0, 255));
void SetIconsList(HIMAGELIST hIcons);
```

### <a name="parameters"></a>Parametry

*uiImageListResID*<br/>
[v] ID prostředku seznamu obrázků.

*Cx*<br/>
[v] Šířka ikon v obrazových bodech v seznamu obrázků.

*clrTransparent*<br/>
[v] Průhledná barva obrazu. Části obrazu, které jsou tato barva bude transparentní. Výchozí hodnota je barva purpurová, RGB (255,0,255).

*hIkony*<br/>
[v] Úchyt k existujícímu seznamu obrázků.

### <a name="return-value"></a>Návratová hodnota

V syntaxi přetížení první metody TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Pokud je seznam vlastností ve stylu aplikace Microsoft Outlook, zobrazí se v rámci v levé části seznamu vlastností seznam navigačních tlačítek nazývaných ovládací prvek podokna aplikace Outlook. Tato metoda slouží k nastavení seznamu obrázků, který má být používán ovládacím prvkem podokna aplikace Outlook.

Další informace o metodách, které podporují tuto metodu, naleznete v [tématu CImageList::Create](../../mfc/reference/cimagelist-class.md#create) a [CImageList::Add](../../mfc/reference/cimagelist-class.md#add). Další informace o nastavení stylu seznamu vlastností naleznete v tématu [CMFCPropertySheet::SetLook](#setlook).

## <a name="cmfcpropertysheetsetlook"></a><a name="setlook"></a>CMFCPropertySheet::SetLook

Určuje vzhled seznamu vlastností.

```cpp
void SetLook(
    PropSheetLook look,
    int nNavControlWidth=100);
```

### <a name="parameters"></a>Parametry

*Podívej*<br/>
[v] Jedna z hodnot výčtu, která určuje vzhled seznamu vlastností. Výchozí styl seznamu vlastností `CMFCPropertySheet::PropSheetLook_Tabs`je . Další informace naleznete v tabulce v části Poznámky v tomto tématu.

*nNavControlWidth*<br/>
[v] Šířka ovládacího prvku navigace v pixelech. Výchozí hodnota je 100.

### <a name="remarks"></a>Poznámky

Chcete-li zobrazit seznam vlastností v jiném než výchozím stylu, zavolejte tuto metodu před vytvořením okna seznamu vlastností.

V následující tabulce jsou uvedeny hodnoty výčtu, které lze zadat v parametru *look.*

|Hodnota|Popis|
|-----------|-----------------|
|`CMFCPropertySheet::PropSheetLook_Tabs`|(Výchozí) Zobrazí kartu pro každou stránku vlastností. Karty jsou zobrazeny v horní části seznamu vlastností a jsou skládané, pokud existuje více karet, než se vejde do jednoho řádku.|
|`CMFCPropertySheet::PropSheetLook_OutlookBar`|Zobrazí seznam navigačních tlačítek ve stylu panelu aplikace Microsoft Outlook na levé straně seznamu vlastností. Každé tlačítko v seznamu odpovídá stránce vlastností. Rámec zobrazí šipky posuvníku, pokud existuje více tlačítek, než se vejde do viditelné oblasti seznamu.|
|`CMFCPropertySheet::PropSheetLook_Tree`|Zobrazí ovládací prvek stromu na levé straně seznamu vlastností. Každý nadřazený nebo podřízený uzel stromového ovládacího prvku odpovídá stránce vlastností. Rámec zobrazí šipky posouvání, pokud existuje více uzlů, než se vejde do viditelné oblasti ovládacího prvku stromu.|
|`CMFCPropertySheet::PropSheetLook_OneNoteTabs`|Zobrazí kartu ve stylu Microsoft OneNotu pro každou stránku vlastností. Rámec zobrazí karty v horní části seznamu vlastností a šipky posouvání, pokud existuje více karet, než se vejde do jednoho řádku.|
|`CMFCPropertySheet::PropSheetLook_List`|Zobrazí seznam na levé straně seznamu vlastností. Každá položka seznamu odpovídá stránce vlastností. Rámec zobrazí šipky posuvníku, pokud existuje více položek seznamu, než se vejde do viditelné oblasti seznamu.|

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)<br/>
[CMFCOutlookBar – třída](../../mfc/reference/cmfcoutlookbar-class.md)
