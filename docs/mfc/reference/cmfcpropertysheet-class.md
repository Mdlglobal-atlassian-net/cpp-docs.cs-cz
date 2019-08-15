---
title: CMFCPropertySheet – třída
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
ms.openlocfilehash: f7c9d2b472a443d8bf556d0b12dfe202ea8607a1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505055"
---
# <a name="cmfcpropertysheet-class"></a>CMFCPropertySheet – třída

`CMFCPropertySheet` Třída podporuje seznam vlastností, kde každá stránka vlastností je označena tabulátorem stránky, tlačítkem panelu nástrojů, uzlem ovládacího prvku stromové struktury nebo položkou seznamu.

## <a name="syntax"></a>Syntaxe

```
class CMFCPropertySheet : public CPropertySheet
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMFCPropertySheet::CMFCPropertySheet](#cmfcpropertysheet)|`CMFCPropertySheet` Vytvoří objekt.|
|`CMFCPropertySheet::~CMFCPropertySheet`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMFCPropertySheet::AddPage](#addpage)|Přidá stránku do seznamu vlastností.|
|[CMFCPropertySheet::AddPageToTree](#addpagetotree)|Přidá do ovládacího prvku stromové struktury novou stránku vlastností.|
|[CMFCPropertySheet::AddTreeCategory](#addtreecategory)|Přidá nový uzel do ovládacího prvku strom.|
|[CMFCPropertySheet::EnablePageHeader](#enablepageheader)|Rezervuje prostor v horní části každé stránky, aby se nakreslila vlastní hlavička.|
|[CMFCPropertySheet::GetHeaderHeight](#getheaderheight)|Načte výšku aktuálního záhlaví.|
|[CMFCPropertySheet::GetLook](#getlook)|Načte hodnotu výčtu, která určuje vzhled aktuálního seznamu vlastností.|
|[CMFCPropertySheet::GetNavBarWidth](#getnavbarwidth)|Opakuje pokus o šířku navigačního panelu v pixelech.|
|[CMFCPropertySheet::GetTab](#gettab)|Načte vnitřní objekt ovládacího prvku karta, který podporuje aktuální ovládací prvek seznamu vlastností.|
|`CMFCPropertySheet::GetThisClass`|Používá se rozhraním, aby se získal ukazatel na objekt [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , který je přidružený k tomuto typu třídy.|
|[CMFCPropertySheet::InitNavigationControl](#initnavigationcontrol)|Inicializuje vzhled aktuálního ovládacího prvku seznamu vlastností.|
|[CMFCPropertySheet::OnActivatePage](#onactivatepage)|Volá se rozhraním, když je povolená stránka vlastností.|
|[CMFCPropertySheet::OnDrawPageHeader](#ondrawpageheader)|Volá se rozhraním, aby se nakreslila hlavička stránky vlastní vlastnosti.|
|`CMFCPropertySheet::OnInitDialog`|Zpracovává zprávu [WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog) . (Overrides [CPropertySheet –:: OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog).)|
|[CMFCPropertySheet::OnRemoveTreePage](#onremovetreepage)|Volá se rozhraním, aby se odebrala stránka vlastností z ovládacího prvku stromu.|
|`CMFCPropertySheet::PreTranslateMessage`|Přeloží zprávy oken před odesláním do funkcí Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . (Overrides `CPropertySheet::PreTranslateMessage`.)|
|[CMFCPropertySheet::RemoveCategory](#removecategory)|Odebere uzel z ovládacího prvku stromu.|
|[CMFCPropertySheet:: volat RemovePage](#removepage)|Odebere ze seznamu vlastností stránku vlastností.|
|[CMFCPropertySheet::SetIconsList](#seticonslist)|Určuje seznam obrázků, které se používají v ovládacím prvku navigace v podokně Outlook.|
|[CMFCPropertySheet::SetLook](#setlook)|Určuje vzhled seznamu vlastností.|

## <a name="remarks"></a>Poznámky

`CMFCPropertySheet` Třída představuje seznamy vlastností, označované také jako dialogová okna karty. `CMFCPropertySheet` Třída může zobrazit stránku vlastností různými způsoby.

Chcete-li použít `CMFCPropertySheet` třídu ve vaší aplikaci, proveďte následující kroky:

1. Odvozuje třídu od `CMFCPropertySheet` třídy a pojmenujte třídu, například CMyPropertySheet.

1. Vytvořte objekt [CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md) pro každou stránku vlastností.

1. V konstruktoru CMyPropertySheet volejte metodu [CMFCPropertySheet:: SetLook](#setlook) . Parametr této metody určuje, že stránky vlastností musí být zobrazeny buď jako tabulátory podél horního nebo levého okraje seznamu vlastností; karty ve stylu seznamu vlastností Microsoft OneNotu; tlačítka na ovládacím prvku panelu nástrojů aplikace Microsoft Outlook; uzly na ovládacím prvku strom; nebo jako seznam položek na levé straně seznamu vlastností.

1. Pokud vytvoříte seznam vlastností ve stylu panelu nástrojů aplikace Microsoft Outlook, zavolejte metodu [CMFCPropertySheet:: SetIconsList](#seticonslist) a přidružte seznam obrázků společně se stránkami vlastností.

1. Pro každou stránku vlastností zavolejte metodu [CMFCPropertySheet:: addPage](#addpage) .

1. Vytvořte ovládací prvek a zavolejte jeho `DoModal` metodu. `CMFCPropertySheet`

## <a name="illustrations"></a>Obrázky

Následující ilustrace znázorňuje seznam vlastností, který je ve stylu vloženého panelu nástrojů aplikace Microsoft Outlook. Na levé straně seznamu vlastností se zobrazí panel nástrojů Outlook.

![Ovládací prvky barev CMFCPropertySheet](../../mfc/reference/media/cmfcpropertysheet_color.png "Ovládací prvky barev CMFCPropertySheet")

Následující ilustrace znázorňuje seznam vlastností, který obsahuje objekt [třídy CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md) . Tento objekt je seznam vlastností ve stylu standardního obecného ovládacího prvku seznam vlastností.

![Seznam CMFCPropertySheet a ovládací prvky vlastností](../../mfc/reference/media/cmfcpropertysheet_list.png "Seznam CMFCPropertySheet a ovládací prvky vlastností")

Následující ilustrace znázorňuje seznam vlastností, který je ve stylu ovládacího prvku strom.

![Strom vlastností](../../mfc/reference/media/proptree.png "Strom vlastností")

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxpropertysheet. h

##  <a name="addpage"></a>CMFCPropertySheet:: AddPage

Přidá stránku do seznamu vlastností.

```
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parametry

*pPage*<br/>
pro Ukazatel na objekt Page. Tento parametr nemůže mít hodnotu NULL.

### <a name="remarks"></a>Poznámky

Tato metoda přidá zadanou stránku vlastností jako kartu vpravo v seznamu vlastností. Proto tuto metodu použijte, chcete-li přidat stránky v pořadí zleva doprava.

Pokud je seznam vlastností ve stylu aplikace Microsoft Outlook, rozhraní zobrazí seznam navigačních tlačítek nalevo od seznamu vlastností. Poté, co tato metoda přidá stránku vlastností, přidá do seznamu odpovídající tlačítko. Chcete-li zobrazit stránku vlastností, klikněte na příslušné tlačítko. Další informace o stylech seznamů vlastností naleznete v tématu [CMFCPropertySheet:: SetLook](#setlook).

##  <a name="addpagetotree"></a>CMFCPropertySheet::AddPageToTree

Přidá do ovládacího prvku stromové struktury novou stránku vlastností.

```
void AddPageToTree(
    CMFCPropertySheetCategoryInfo* pCategory,
    CMFCPropertyPage* pPage,
    int nIconNum=-1,
    int nSelIconNum=-1);
```

### <a name="parameters"></a>Parametry

*pCategory*<br/>
pro Ukazatel na uzel nadřazeného stromu nebo hodnotu NULL, chcete-li přidružit určenou stránku k uzlu nejvyšší úrovně. Pro získání tohoto ukazatele volejte metodu [CMFCPropertySheet:: AddTreeCategory](#addtreecategory) .

*pPage*<br/>
pro Ukazatel na objekt stránky vlastností.

*nIconNum*<br/>
pro Index ikony založený na nule, nebo hodnota-1, pokud se nepoužívá žádná ikona Ikona se zobrazí vedle stránky vlastností ovládacího prvku strom, pokud není vybrána stránka. Výchozí hodnota je-1.

*nSelIconNum*<br/>
pro Index ikony založený na nule, nebo hodnota-1, pokud se nepoužívá žádná ikona Ikona se zobrazí vedle stránky vlastností ovládacího prvku strom, když je vybrána stránka. Výchozí hodnota je-1.

### <a name="remarks"></a>Poznámky

Tato metoda přidá stránku vlastností jako list ovládacího prvku stromu. Chcete-li přidat stránku vlastností, vytvořte `CMFCPropertySheet` objekt, zavolejte metodu [CMFCPropertySheet:: SetLook](#setlook) s parametrem nastaveným na `CMFCPropertySheet::PropSheetLook_Tree`hodnotu a poté pomocí této metody přidejte stránku vlastností.

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

*lpszLabel*<br/>
pro Název uzlu.

*nIconNum*<br/>
pro Index ikony založený na nule, nebo hodnota-1, pokud se nepoužívá žádná ikona Ikona se zobrazí vedle stránky vlastností ovládacího prvku strom, pokud není vybrána stránka. Výchozí hodnota je-1.

*nSelectedIconNum*<br/>
pro Index ikony založený na nule, nebo hodnota-1, pokud se nepoužívá žádná ikona Ikona se zobrazí vedle stránky vlastností ovládacího prvku strom, když je vybrána stránka. Výchozí hodnota je-1.

*pParentCategory*<br/>
pro Ukazatel na uzel nadřazeného stromu nebo hodnotu NULL, chcete-li přidružit určenou stránku k uzlu nejvyšší úrovně. Nastavte tento parametr pomocí metody [CMFCPropertySheet:: AddTreeCategory](#addtreecategory) .

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nový uzel v ovládacím prvku strom.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte, chcete-li přidat nový uzel, který je také označován jako kategorie, do ovládacího prvku stromu. Chcete-li přidat uzel, vytvořte `CMFCPropertySheet` objekt, zavolejte metodu [CMFCPropertySheet:: SetLook](#setlook) s parametrem nastaveným na `CMFCPropertySheet::PropSheetLook_Tree`hodnotu a poté pomocí této metody přidejte uzel.

Použijte návratovou hodnotu této metody v následných voláních do [CMFCPropertySheet:: AddPageToTree](#addpagetotree) a [CMFCPropertySheet:: AddTreeCategory](#addtreecategory).

##  <a name="cmfcpropertysheet"></a>CMFCPropertySheet::CMFCPropertySheet

`CMFCPropertySheet` Vytvoří objekt.

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

*pszCaption*<br/>
pro Řetězec, který obsahuje titulek seznamu vlastností. Nemůže mít hodnotu NULL.

*nIDCaption*<br/>
pro ID prostředku, které obsahuje titulek seznamu vlastností.

*pParentWnd*<br/>
pro Ukazatel na nadřazené okno seznamu vlastností nebo hodnotu NULL, pokud je nadřazené okno hlavním oknem aplikace. Výchozí hodnota je NULL.

*iSelectPage*<br/>
pro Index vycházející ze stránky horních vlastností na základě nuly Výchozí hodnota je 0.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu parametry pro konstruktor [CPropertySheet –:: CPropertySheet –](../../mfc/reference/cpropertysheet-class.md#cpropertysheet) .

##  <a name="enablepageheader"></a>CMFCPropertySheet::EnablePageHeader

Rezervuje prostor v horní části každé stránky, aby se nakreslila vlastní hlavička.

```
void EnablePageHeader(int nHeaderHeight);
```

### <a name="parameters"></a>Parametry

*nHeaderHeight*<br/>
pro Výška hlavičky v pixelech

### <a name="remarks"></a>Poznámky

Chcete-li použít hodnotu parametru *nHeaderHeight* k nakreslení vlastní hlavičky, přepište metodu [CMFCPropertySheet:: OnDrawPageHeader](#ondrawpageheader) .

##  <a name="getheaderheight"></a>CMFCPropertySheet::GetHeaderHeight

Načte výšku aktuálního záhlaví.

```
int GetHeaderHeight() const;
```

### <a name="return-value"></a>Návratová hodnota

Výška hlavičky v pixelech

### <a name="remarks"></a>Poznámky

Před voláním této metody volejte metodu [CMFCPropertySheet:: EnablePageHeader](#enablepageheader) .

##  <a name="getlook"></a>CMFCPropertySheet:: getvzhled

Načte hodnotu výčtu, která určuje vzhled aktuálního seznamu vlastností.

```
PropSheetLook GetLook() const;
```

### <a name="return-value"></a>Návratová hodnota

Jedna z hodnot výčtu, která určuje vzhled seznamu vlastností. Seznam možných hodnot naleznete v tabulce výčtu v části poznámky v tématu [CMFCPropertySheet:: SetLook](#setlook).

##  <a name="getnavbarwidth"></a>CMFCPropertySheet::GetNavBarWidth

Získá šířku navigačního panelu.

```
int GetNavBarWidth() const;
```

### <a name="return-value"></a>Návratová hodnota

Šířka navigačního panelu v pixelech

##  <a name="gettab"></a>CMFCPropertySheet::GetTab

Načte vnitřní objekt ovládacího prvku karta, který podporuje aktuální ovládací prvek seznamu vlastností.

```
CMFCTabCtrl& GetTab() const;
```

### <a name="return-value"></a>Návratová hodnota

Vnitřní objekt ovládacího prvku karta.

### <a name="remarks"></a>Poznámky

Seznam vlastností můžete nastavit tak, aby se zobrazil v různých stylech, jako je například ovládací prvek stromu, seznam navigačních tlačítek nebo sada stránek s kartami.

Před voláním této metody zavolejte metodu [CMFCPropertySheet:: SetLook](#setlook) , abyste nastavili vzhled ovládacího prvku seznamu vlastností. Pak zavolejte metodu [CMFCPropertySheet:: InitNavigationControl](#initnavigationcontrol) pro inicializaci interního objektu ovládacího prvku karta. Tuto metodu použijte, chcete-li načíst objekt ovládacího prvku karta a potom použít tento objekt pro práci s kartami na seznamu vlastností.

Tato metoda vyhodnotí v režimu ladění, pokud ovládací prvek seznam vlastností není nastaven jako zobrazený ve stylu aplikace Microsoft OneNote.

##  <a name="initnavigationcontrol"></a>CMFCPropertySheet::InitNavigationControl

Inicializuje vzhled aktuálního ovládacího prvku seznamu vlastností.

```
virtual CWnd* InitNavigationControl();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na okno ovládacího prvku seznamu vlastností.

### <a name="remarks"></a>Poznámky

Ovládací prvek seznamu vlastností se může objevit v několika různých formách, jako je například sada stránek s kartami, stromové řízení nebo seznam navigačních tlačítek. Pomocí metody [CMFCPropertySheet:: SetLook](#setlook) určete vzhled ovládacího prvku seznamu vlastností.

##  <a name="onactivatepage"></a>CMFCPropertySheet::OnActivatePage

Volá se rozhraním, když je povolená stránka vlastností.

```
virtual void OnActivatePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parametry

*pPage*<br/>
pro Ukazatel na objekt stránky vlastností, který představuje stránku vlastností Enabled.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda zajišťuje, že se stránka vlastností Enabled posouvá do zobrazení. Pokud styl aktuálního seznamu vlastností obsahuje podokno Microsoft Outlook, tato metoda nastaví odpovídající tlačítko aplikace Outlook na stav zaškrtnutí.

##  <a name="ondrawpageheader"></a>CMFCPropertySheet::OnDrawPageHeader

Volá se rozhraním, aby se nakreslila hlavička pro stránku vlastní vlastnosti.

```
virtual void OnDrawPageHeader(
    CDC* pDC,
    int nPage,
    CRect rectHeader);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
pro Ukazatel na kontext zařízení.

*nPage*<br/>
pro Číslo stránky vlastnosti založené na nule.

*rectHeader*<br/>
pro Ohraničující obdélník, který určuje, kde se má záhlaví nakreslit.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato metoda neprovede žádnou akci. Pokud přepíšete tuto metodu, zavolejte metodu [CMFCPropertySheet:: EnablePageHeader](#enablepageheader) předtím, než rozhraní zavolá tuto metodu.

##  <a name="onremovetreepage"></a>CMFCPropertySheet::OnRemoveTreePage

Volá se rozhraním, aby se odebrala stránka vlastností z ovládacího prvku stromu.

```
virtual BOOL OnRemoveTreePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parametry

*pPage*<br/>
pro Ukazatel na objekt stránky vlastností, který představuje stránku vlastností, která se má odebrat.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

##  <a name="removecategory"></a>CMFCPropertySheet::RemoveCategory

Odebere uzel z ovládacího prvku stromu.

```
void RemoveCategory(CMFCPropertySheetCategoryInfo* pCategory);
```

### <a name="parameters"></a>Parametry

*pCategory*<br/>
pro Ukazatel na kategorii (uzel), který se má odebrat

### <a name="remarks"></a>Poznámky

Tuto metodu použijte, chcete-li z ovládacího prvku stromu odebrat uzel, který je také označován jako kategorie. K přidání uzlu do ovládacího prvku stromu použijte metodu [CMFCPropertySheet:: AddTreeCategory](#addtreecategory) .

##  <a name="removepage"></a>CMFCPropertySheet:: volat RemovePage

Odebere ze seznamu vlastností stránku vlastností.

```
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>Parametry

*pPage*<br/>
pro Ukazatel na objekt stránky vlastností, který představuje stránku vlastností, která se má odebrat. Nemůže mít hodnotu NULL.

*nPage*<br/>
pro Index vycházející ze stránky, která má být odebrána od nuly

### <a name="remarks"></a>Poznámky

Tato metoda odebere zadanou stránku vlastností a odstraní její přidružené okno. Objekt stránky vlastností, který je určen parametrem *ppage* , nebude zničen, dokud okno [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md) nebude zavřeno.

##  <a name="seticonslist"></a>CMFCPropertySheet::SetIconsList

Určuje seznam obrázků, které se používají v ovládacím prvku navigace v podokně Outlook.

```
BOOL SetIconsList(
    UINT uiImageListResID,
    int cx,
    COLORREF clrTransparent=RGB(255, 0, 255));
void SetIconsList(HIMAGELIST hIcons);
```

### <a name="parameters"></a>Parametry

*uiImageListResID*<br/>
pro ID prostředku seznamu obrázků.

*cx*<br/>
pro Šířka ikon v seznamu obrázků (v pixelech).

*clrTransparent*<br/>
pro Průhledná barva obrázku. Části obrázku, které mají tuto barvu, budou transparentní. Výchozí hodnota je purpurová barvy, RGB (255, 0255).

*hIcons*<br/>
pro Popisovač existujícího seznamu obrázků.

### <a name="return-value"></a>Návratová hodnota

V první metodě přetížení syntaxe TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Pokud je seznam vlastností ve stylu aplikace Microsoft Outlook, rozhraní zobrazí seznam navigačních tlačítek označovaných jako ovládací prvek podokno aplikace Outlook, nalevo od seznamu vlastností. Tuto metodu použijte, chcete-li nastavit seznam obrázků, který bude použit ovládacím prvkem podokna aplikace Outlook.

Další informace o metodách, které podporují tuto metodu, naleznete v tématu [atributu CImageList:: Create](../../mfc/reference/cimagelist-class.md#create) a [atributu CImageList:: Add](../../mfc/reference/cimagelist-class.md#add). Další informace o nastavení stylu seznamu vlastností naleznete v tématu [CMFCPropertySheet:: SetLook](#setlook).

##  <a name="setlook"></a>CMFCPropertySheet::SetLook

Určuje vzhled seznamu vlastností.

```
void SetLook(
    PropSheetLook look,
    int nNavControlWidth=100);
```

### <a name="parameters"></a>Parametry

*Podívej*<br/>
pro Jedna z hodnot výčtu, která určuje vzhled seznamu vlastností. Výchozí styl seznamu vlastností je `CMFCPropertySheet::PropSheetLook_Tabs`. Další informace najdete v tabulce v tomto tématu v části poznámky.

*nNavControlWidth*<br/>
pro Šířka ovládacího prvku navigace (v pixelech) Výchozí hodnota je 100.

### <a name="remarks"></a>Poznámky

Chcete-li zobrazit seznam vlastností ve stylu jiném než výchozí, zavolejte tuto metodu před vytvořením okna seznamu vlastností.

V následující tabulce jsou uvedeny hodnoty výčtu, které lze zadat v parametru *Vyhledat* .

|Value|Popis|
|-----------|-----------------|
|`CMFCPropertySheet::PropSheetLook_Tabs`|Výchozí Zobrazí kartu pro každou stránku vlastností. Karty se zobrazí v horní části seznamu vlastností a jsou skládané, pokud existuje více karet, než se vejde do jednoho řádku.|
|`CMFCPropertySheet::PropSheetLook_OutlookBar`|Zobrazí seznam navigačních tlačítek ve stylu panelu aplikace Microsoft Outlook na levé straně seznamu vlastností. Každé tlačítko v seznamu odpovídá stránce vlastností. Rozhraní zobrazí šipky posuvníku, pokud existuje více tlačítek, než se vejde do viditelné oblasti seznamu.|
|`CMFCPropertySheet::PropSheetLook_Tree`|Zobrazí ovládací prvek stromu na levé straně seznamu vlastností. Každý nadřazený nebo podřízený uzel ovládacího prvku stromu odpovídá stránce vlastností. Rozhraní zobrazí šipky posuvníku, pokud existuje více uzlů, než se vejde do viditelné oblasti ovládacího prvku stromu.|
|`CMFCPropertySheet::PropSheetLook_OneNoteTabs`|Zobrazí kartu ve stylu Microsoft OneNotu pro každou stránku vlastností. Rozhraní zobrazí karty v horní části seznamu vlastností a šipky posuvníku, pokud existuje více karet, než se vejde do jednoho řádku.|
|`CMFCPropertySheet::PropSheetLook_List`|Zobrazí seznam na levé straně seznamu vlastností. Každá položka seznamu odpovídá stránce vlastností. Rozhraní zobrazí šipky posuvníku, pokud existuje více položek seznamu, než se vejde do viditelné oblasti seznamu.|

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyPage – třída](../../mfc/reference/cmfcpropertypage-class.md)<br/>
[CMFCOutlookBar – třída](../../mfc/reference/cmfcoutlookbar-class.md)
