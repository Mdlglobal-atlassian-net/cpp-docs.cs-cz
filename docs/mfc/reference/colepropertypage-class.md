---
title: COlePropertyPage – třída
ms.date: 11/04/2016
f1_keywords:
- COlePropertyPage
- AFXCTL/COlePropertyPage
- AFXCTL/COlePropertyPage::COlePropertyPage
- AFXCTL/COlePropertyPage::GetControlStatus
- AFXCTL/COlePropertyPage::GetObjectArray
- AFXCTL/COlePropertyPage::GetPageSite
- AFXCTL/COlePropertyPage::OVERWRITEApply
- AFXCTL/COlePropertyPage::IsModified
- AFXCTL/COlePropertyPage::OnEditProperty
- AFXCTL/COlePropertyPage::OnHelp
- AFXCTL/COlePropertyPage::OnInitDialog
- AFXCTL/COlePropertyPage::OnObjectsChanged
- AFXCTL/COlePropertyPage::OnSetPageSite
- AFXCTL/COlePropertyPage::SetControlStatus
- AFXCTL/COlePropertyPage::SetDialogResource
- AFXCTL/COlePropertyPage::SetHelpInfo
- AFXCTL/COlePropertyPage::SetModifiedFlag
- AFXCTL/COlePropertyPage::SetPageName
helpviewer_keywords:
- COlePropertyPage [MFC], COlePropertyPage
- COlePropertyPage [MFC], GetControlStatus
- COlePropertyPage [MFC], GetObjectArray
- COlePropertyPage [MFC], GetPageSite
- COlePropertyPage [MFC], IgnoreApply
- COlePropertyPage [MFC], IsModified
- COlePropertyPage [MFC], OnEditProperty
- COlePropertyPage [MFC], OnHelp
- COlePropertyPage [MFC], OnInitDialog
- COlePropertyPage [MFC], OnObjectsChanged
- COlePropertyPage [MFC], OnSetPageSite
- COlePropertyPage [MFC], SetControlStatus
- COlePropertyPage [MFC], SetDialogResource
- COlePropertyPage [MFC], SetHelpInfo
- COlePropertyPage [MFC], SetModifiedFlag
- COlePropertyPage [MFC], SetPageName
ms.assetid: e9972872-8e6b-4550-905e-d36a274d64dc
ms.openlocfilehash: 8253b2c2fa6b93ec51c7ede983ef710eed039970
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58776983"
---
# <a name="colepropertypage-class"></a>COlePropertyPage – třída

Slouží k zobrazení vlastností vlastního ovládacího prvku v grafickém rozhraní, podobnému dialogovému oknu.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE COlePropertyPage : public CDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[COlePropertyPage::COlePropertyPage](#colepropertypage)|Vytvoří `COlePropertyPage` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[COlePropertyPage::GetControlStatus](#getcontrolstatus)|Určuje, zda má uživatel změnil hodnotu v ovládacím prvku.|
|[COlePropertyPage::GetObjectArray](#getobjectarray)|Vrátí pole objektů editován stránky vlastností.|
|[COlePropertyPage::GetPageSite](#getpagesite)|Vrací ukazatel na stránku vlastností `IPropertyPageSite` rozhraní.|
|[COlePropertyPage::IgnoreApply](#ignoreapply)|Určuje, jaké ovládací prvky nepovolujte tlačítko použít.|
|[COlePropertyPage::IsModified](#ismodified)|Určuje, zda má uživatel změnil na stránce vlastností.|
|[COlePropertyPage::OnEditProperty](#oneditproperty)|Volá se rozhraním, když uživatel upravuje vlastnost.|
|[COlePropertyPage::OnHelp](#onhelp)|Volá se rozhraním, když uživatel vyvolá nápovědu.|
|[COlePropertyPage::OnInitDialog](#oninitdialog)|Volá se rozhraním, když je inicializován na stránce vlastností.|
|[COlePropertyPage::OnObjectsChanged](#onobjectschanged)|Volá se rozhraním, když se zvolí jiný ovládací prvek OLE, novými vlastnostmi.|
|[COlePropertyPage::OnSetPageSite](#onsetpagesite)|Volá se rozhraním, když rámec vlastnosti nabízí web stránky.|
|[COlePropertyPage::SetControlStatus](#setcontrolstatus)|Nastaví příznak označující, zda má uživatel změnil hodnotu v ovládacím prvku.|
|[COlePropertyPage::SetDialogResource](#setdialogresource)|Nastaví prostředku dialogového okna stránky vlastností.|
|[COlePropertyPage::SetHelpInfo](#sethelpinfo)|Nastaví text na stránce vlastností stručnou nápovědu, název jeho soubor nápovědy a její kontextové nápovědy.|
|[COlePropertyPage::SetModifiedFlag](#setmodifiedflag)|Nastaví příznak označující, zda má uživatel změnil na stránce vlastností.|
|[COlePropertyPage::SetPageName](#setpagename)|Nastaví název stránky vlastností (popisek).|

## <a name="remarks"></a>Poznámky

Stránky vlastností pro instanci může obsahovat prvek pro úpravy, který umožňuje uživateli zobrazit a upravit vlastnosti titulku ovládacího prvku.

Každá vlastnost základní nebo vlastní ovládací prvek může mít ovládací prvek dialogového okna, který umožňuje uživateli zobrazit aktuální hodnota vlastnosti a v případě potřeby změňte tuto hodnotu ovládacího prvku.

Další informace o používání `COlePropertyPage`, najdete v článku [ovládací prvky ActiveX: Stránky vlastností](../../mfc/mfc-activex-controls-property-pages.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`COlePropertyPage`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxctl.h

##  <a name="colepropertypage"></a>  COlePropertyPage::COlePropertyPage

Vytvoří `COlePropertyPage` objektu.

```
COlePropertyPage(
    UINT idDlg,
    UINT idCaption);
```

### <a name="parameters"></a>Parametry

*idDlg*<br/>
ID prostředku šablony dialogového okna.

*idCaption*<br/>
ID prostředku titulek stránky vlastností.

### <a name="remarks"></a>Poznámky

Při implementaci podtřída `COlePropertyPage`, konstruktor vaší podtřídy by měly použít `COlePropertyPage` konstruktor k identifikaci prostředku šablony dialogového okna na která je založena na stránce vlastností a prostředku řetězců obsahující titulek.

##  <a name="getcontrolstatus"></a>  COlePropertyPage::GetControlStatus

Určuje, zda má uživatel změnil hodnotu ovládacího prvku stránku vlastností s ID zadaného prostředku.

```
BOOL GetControlStatus(UINT nID);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
ID prostředku ovládací prvek stránky vlastností.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud byla změněna hodnota ovládacího prvku; v opačném případě FALSE.

##  <a name="getobjectarray"></a>  COlePropertyPage::GetObjectArray

Vrátí pole objektů editován stránky vlastností.

```
LPDISPATCH* GetObjectArray(ULONG* pnObjects);
```

### <a name="parameters"></a>Parametry

*pnObjects*<br/>
Ukazatel na dlouhé celé číslo bez znaménka, která bude dostávat počet objektů editován stránky.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na pole `IDispatch` ukazatele, které se používají pro přístup k vlastnostem na stránce vlastností každého ovládacího prvku. Volající nemůže uvolnit tyto ukazatele rozhraní.

### <a name="remarks"></a>Poznámky

Každou vlastnost objektu page udržuje pole ukazatelů na `IDispatch` rozhraní objektů editován stránky. Tato funkce nastaví jeho *pnObjects* argument pro počet prvků v dané pole a vrátí ukazatel na první prvek pole.

##  <a name="getpagesite"></a>  COlePropertyPage::GetPageSite

Získá ukazatel na stránku vlastností `IPropertyPageSite` rozhraní.

```
LPPROPERTYPAGESITE GetPageSite();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na stránce vlastností `IPropertyPageSite` rozhraní.

### <a name="remarks"></a>Poznámky

Ovládací prvky a kontejnery spolupracují, aby uživatelé mohou procházet a upravovat vlastnosti ovládacího prvku. Ovládací prvek poskytuje stránky vlastností, z nichž každý je objekt OLE, který umožňuje uživateli upravit související sadu vlastností. Kontejner obsahuje vlastnost rámce, který se zobrazí na stránkách vlastností. Pro každou stránku rámec vlastnosti nabízí stránku webu, který podporuje `IPropertyPageSite` rozhraní.

##  <a name="ignoreapply"></a>  COlePropertyPage::IgnoreApply

Určuje, jaké ovládací prvky nepovolujte tlačítko použít.

```
void IgnoreApply(UINT nID);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
ID ovládacího prvku se má ignorovat.

### <a name="remarks"></a>Poznámky

Na stránce vlastností použít tlačítko je povoleno pouze v případě, že se změnily hodnoty vlastností ovládacích prvků stránky. Tuto funkci použijte k určení ovládacích prvků, které nezpůsobí tlačítko použít, aby byla povolena při změně jejich hodnoty.

##  <a name="ismodified"></a>  COlePropertyPage::IsModified

Určuje, zda má uživatel změnil všechny hodnoty na stránce vlastností.

```
BOOL IsModified();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byl změněn na stránce vlastností.

##  <a name="oneditproperty"></a>  COlePropertyPage::OnEditProperty

Rozhraní volá tuto funkci se upravit určitou vlastnost.

```
virtual BOOL OnEditProperty(DISPID dispid);
```

### <a name="parameters"></a>Parametry

*dispid*<br/>
Hodnotu Dispatch ID vlastnosti, který právě upravujete.

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrací hodnotu FALSE. Přepsání této funkce by měla vrátit hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Můžete přepsat tak zaměřit na odpovídající ovládací prvek na stránce. Výchozí implementace neprovede žádnou akci a vrátí hodnotu FALSE.

##  <a name="onhelp"></a>  COlePropertyPage::OnHelp

Rozhraní volá tuto funkci, pokud si uživatel vyžádá nápovědu online.

```
virtual BOOL OnHelp(LPCTSTR lpszHelpDir);
```

### <a name="parameters"></a>Parametry

*lpszHelpDir*<br/>
Adresář obsahující soubor nápovědy na stránce vlastností.

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrací hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Přepište stránky vlastností musí provést žádnou zvláštní akci, když uživatel přistupuje k nápovědy. Výchozí implementace neprovede žádnou akci a vrátí hodnotu FALSE, která nastaví rozhraní pro volání WinHelp.

##  <a name="oninitdialog"></a>  COlePropertyPage::OnInitDialog

Rozhraní volá tuto funkci při inicializaci dialogového okna stránky vlastností.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrací hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Pokud žádnou zvláštní akci je potřeba při inicializaci dialogového okna, přepište ji. Výchozí implementace volá `CDialog::OnInitDialog` a vrátí hodnotu FALSE.

##  <a name="onobjectschanged"></a>  COlePropertyPage::OnObjectsChanged

Volá se rozhraním, když se zvolí jiný ovládací prvek OLE, novými vlastnostmi.

```
virtual void OnObjectsChanged();
```

### <a name="remarks"></a>Poznámky

Při zobrazení vlastností ovládacího prvku OLE vývojářského prostředí, dialogové okno nemodální slouží k zobrazení stránky s jejími vlastnostmi. Pokud jiný ovládací prvek je vybrán, musí být aktivní jinou sadu stránky vlastností pro novou sadu vlastností. Rozhraní volá tuto funkci upozornit na stránce vlastností změnu.

Potlačí tuto funkci pro příjem oznámení pro tuto akci a provádět žádné zvláštní akce.

##  <a name="onsetpagesite"></a>  COlePropertyPage::OnSetPageSite

Rozhraní volá tuto funkci, když rámec vlastnosti nabízí stránku vlastností stránky webu.

```
virtual void OnSetPageSite();
```

### <a name="remarks"></a>Poznámky

Výchozí implementace načte titulek stránky a pokusí se zjistit velikost stránky z prostředku dialogového okna. Potlačí tuto funkci v případě, že žádné další akce; vyžaduje stránky vlastností přepsání by měly volat implementaci základní třídy.

##  <a name="setcontrolstatus"></a>  COlePropertyPage::SetControlStatus

Změní stav ovládacího prvku vlastnosti stránky.

```
BOOL SetControlStatus(
    UINT nID,
    BOOL bDirty);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Obsahuje ID ovládacího prvku vlastnosti stránky.

*bDirty*<br/>
Určuje, pokud byl změněn na pole na stránce vlastností. Nastavte na hodnotu TRUE, pokud pole byl změněn, FALSE v případě, že byl změněn.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud zadaný ovládací prvek byl nastaven; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Pokud je stav ovládací prvek na stránce Vlastnosti dirty při na stránce vlastností je uzavřený nebo kliknutí na toto tlačítko použít, vlastnost ovládacího prvku bude aktualizován na odpovídající hodnotu.

##  <a name="setdialogresource"></a>  COlePropertyPage::SetDialogResource

Nastaví prostředku dialogového okna stránky vlastností.

```
void SetDialogResource(HGLOBAL hDialog);
```

### <a name="parameters"></a>Parametry

*hDialog*<br/>
Popisovač prostředku dialogového okna stránky vlastností.

##  <a name="sethelpinfo"></a>  COlePropertyPage::SetHelpInfo

Určuje informace popisu tlačítka, název souboru nápovědy a kontextové nápovědy pro stránky vlastností.

```
void SetHelpInfo(
    LPCTSTR lpszDocString,
    LPCTSTR lpszHelpFile = NULL,
    DWORD dwHelpContext = 0);
```

### <a name="parameters"></a>Parametry

*lpszDocString*<br/>
Řetězec obsahující informace o stručnou nápovědu pro zobrazení ve stavovém řádku nebo v jiném umístění.

*lpszHelpFile*<br/>
Název souboru nápovědy na stránce vlastností.

*dwHelpContext*<br/>
Kontextové nápovědy pro stránku vlastností.

##  <a name="setmodifiedflag"></a>  COlePropertyPage::SetModifiedFlag

Určuje, zda má uživatel změnil na stránce vlastností.

```
void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Parametry

*bModified*<br/>
Určuje novou hodnotu pro příznak upravené stránky vlastností.

##  <a name="setpagename"></a>  COlePropertyPage::SetPageName

Nastaví název stránky vlastností, které rámec vlastnosti se obvykle zobrazí na kartě stránky.

```
void SetPageName(LPCTSTR lpszPageName);
```

### <a name="parameters"></a>Parametry

*lpszPageName*<br/>
Ukazatel na řetězec obsahující název vlastnosti stránky.

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC Circ3 –](../../overview/visual-cpp-samples.md)<br/>
[Ukázky knihovny MFC TESTHELP](../../overview/visual-cpp-samples.md)<br/>
[CDialog – třída](../../mfc/reference/cdialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDialog – třída](../../mfc/reference/cdialog-class.md)
