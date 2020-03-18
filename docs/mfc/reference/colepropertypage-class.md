---
title: COlePropertyPage – – třída
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
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421091"
---
# <a name="colepropertypage-class"></a>COlePropertyPage – – třída

Slouží k zobrazení vlastností vlastního ovládacího prvku v grafickém rozhraní, podobně jako v dialogovém okně.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE COlePropertyPage : public CDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[COlePropertyPage –:: COlePropertyPage –](#colepropertypage)|Vytvoří objekt `COlePropertyPage`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COlePropertyPage –:: GetControlStatus](#getcontrolstatus)|Určuje, zda uživatel změnil hodnotu v ovládacím prvku.|
|[COlePropertyPage –:: GetObjectArray](#getobjectarray)|Vrátí pole objektů, které jsou upravovány na stránce vlastností.|
|[COlePropertyPage –:: GetPageSite](#getpagesite)|Vrátí ukazatel na `IPropertyPageSite` rozhraní stránky vlastností.|
|[COlePropertyPage –:: IgnoreApply](#ignoreapply)|Určuje, které ovládací prvky nepovolují tlačítko použít.|
|[COlePropertyPage –::-Modified](#ismodified)|Určuje, zda uživatel změnil stránku vlastností.|
|[COlePropertyPage –:: OnEditProperty](#oneditproperty)|Volá se rozhraním, když uživatel upravuje vlastnost.|
|[COlePropertyPage –:: help](#onhelp)|Volá se rozhraním, když uživatel vyvolá pomocníka.|
|[COlePropertyPage –:: OnInitDialog](#oninitdialog)|Volá se rozhraním, když se inicializuje stránka vlastností.|
|[COlePropertyPage –:: OnObjectsChanged](#onobjectschanged)|Volá se rozhraním, když se vybere jiný ovládací prvek OLE, s novými vlastnostmi.|
|[COlePropertyPage –:: OnSetPageSite](#onsetpagesite)|Volá se rozhraním, když rámec vlastnosti poskytuje web stránky.|
|[COlePropertyPage –:: SetControlStatus](#setcontrolstatus)|Nastaví příznak označující, zda uživatel změnil hodnotu v ovládacím prvku.|
|[COlePropertyPage –:: SetDialogResource](#setdialogresource)|Nastaví prostředek dialogového okna stránky vlastností.|
|[COlePropertyPage –:: SetHelpInfo](#sethelpinfo)|Nastaví stručný text v nápovědě stránky vlastností, název jeho souboru s jeho pomocí a kontext jeho kontextu.|
|[COlePropertyPage –:: SetModifiedFlag](#setmodifiedflag)|Nastaví příznak označující, zda uživatel změnil stránku vlastností.|
|[COlePropertyPage –:: SetPageName](#setpagename)|Nastaví název stránky vlastností (titulek).|

## <a name="remarks"></a>Poznámky

Například stránka vlastností může obsahovat ovládací prvek pro úpravy, který uživateli umožňuje zobrazit a změnit vlastnost popisek ovládacího prvku.

Každá vlastní nebo stavová vlastnost ovládacího prvku může mít ovládací prvek dialog, který umožňuje uživateli ovládacího prvku zobrazit aktuální hodnotu vlastnosti a v případě potřeby tuto hodnotu upravit.

Další informace o použití `COlePropertyPage`naleznete v článku [ovládací prvky ActiveX: stránky vlastností](../../mfc/mfc-activex-controls-property-pages.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`COlePropertyPage`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AFXCTL. h

##  <a name="colepropertypage"></a>COlePropertyPage –:: COlePropertyPage –

Vytvoří objekt `COlePropertyPage`.

```
COlePropertyPage(
    UINT idDlg,
    UINT idCaption);
```

### <a name="parameters"></a>Parametry

*idDlg*<br/>
ID prostředku šablony dialogového okna

*idCaption*<br/>
ID prostředku popisku stránky vlastností

### <a name="remarks"></a>Poznámky

Při implementaci podtřídy `COlePropertyPage`by měl konstruktor podtřídy použít konstruktor `COlePropertyPage` k identifikaci prostředku šablony dialogového okna, na kterém je založena stránka vlastností, a prostředku řetězce obsahujícího titulek.

##  <a name="getcontrolstatus"></a>COlePropertyPage –:: GetControlStatus

Určuje, zda uživatel změnil hodnotu ovládacího prvku stránka vlastností se zadaným ID prostředku.

```
BOOL GetControlStatus(UINT nID);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
ID prostředku ovládacího prvku stránky vlastností

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byla změněna hodnota ovládacího prvku; v opačném případě FALSE.

##  <a name="getobjectarray"></a>COlePropertyPage –:: GetObjectArray

Vrátí pole objektů, které jsou upravovány na stránce vlastností.

```
LPDISPATCH* GetObjectArray(ULONG* pnObjects);
```

### <a name="parameters"></a>Parametry

*pnObjects*<br/>
Ukazatel na dlouhé celé číslo bez znaménka, které obdrží počet objektů upravovaných stránkou.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na pole ukazatelů `IDispatch`, které slouží pro přístup k vlastnostem každého ovládacího prvku na stránce vlastností. Volající nesmí tyto ukazatele rozhraní uvolnit.

### <a name="remarks"></a>Poznámky

Každý objekt stránky vlastností udržuje pole ukazatelů na `IDispatch` rozhraní objektů upravovaných stránkou. Tato funkce nastaví svůj argument *pnObjects* na počet prvků v tomto poli a vrátí ukazatel na první prvek pole.

##  <a name="getpagesite"></a>COlePropertyPage –:: GetPageSite

Získá ukazatel na `IPropertyPageSite` rozhraní stránky vlastností.

```
LPPROPERTYPAGESITE GetPageSite();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `IPropertyPageSite` rozhraní stránky vlastností.

### <a name="remarks"></a>Poznámky

Ovládací prvky a kontejnery spolupracují, aby uživatelé mohli procházet a upravovat vlastnosti ovládacích prvků. Ovládací prvek poskytuje stránky vlastností, z nichž každý je objekt OLE, který umožňuje uživateli upravit související sadu vlastností. Kontejner poskytuje rámec vlastností, který zobrazí stránky vlastností. Pro každou stránku nabízí rámec vlastností stránku webu, která podporuje rozhraní `IPropertyPageSite`.

##  <a name="ignoreapply"></a>COlePropertyPage –:: IgnoreApply

Určuje, které ovládací prvky nepovolují tlačítko použít.

```
void IgnoreApply(UINT nID);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
ID ovládacího prvku, který se má ignorovat

### <a name="remarks"></a>Poznámky

Tlačítko použít na stránce vlastností je povoleno pouze v případě, že byly změněny hodnoty ovládacích prvků stránky vlastností. Pomocí této funkce lze zadat ovládací prvky, které nezpůsobí, že bude povoleno tlačítko použít, když se změní jejich hodnoty.

##  <a name="ismodified"></a>COlePropertyPage –::-Modified

Určuje, zda uživatel změnil jakékoli hodnoty na stránce vlastností.

```
BOOL IsModified();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud byla změněna stránka vlastností.

##  <a name="oneditproperty"></a>COlePropertyPage –:: OnEditProperty

Rozhraní volá tuto funkci, když se upraví konkrétní vlastnost.

```
virtual BOOL OnEditProperty(DISPID dispid);
```

### <a name="parameters"></a>Parametry

*DISPID*<br/>
ID odeslání upravované vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrátí hodnotu FALSE. Přepsání této funkce by mělo vrátit hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Můžete ji přepsat a nastavit tak fokus na příslušný ovládací prvek na stránce. Výchozí implementace neprovede žádnou akci a vrátí hodnotu FALSE.

##  <a name="onhelp"></a>COlePropertyPage –:: help

Rozhraní volá tuto funkci, když uživatel požádá o online podporu.

```
virtual BOOL OnHelp(LPCTSTR lpszHelpDir);
```

### <a name="parameters"></a>Parametry

*lpszHelpDir*<br/>
Adresář obsahující soubor Help stránky vlastností

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrátí hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Přepsat, pokud stránka vlastností musí při přístupu uživatele k nápovědě provést jakoukoli zvláštní akci. Výchozí implementace neprovede žádnou akci a vrátí hodnotu FALSE, která instruuje rozhraní, aby volalo funkci WinHelp.

##  <a name="oninitdialog"></a>COlePropertyPage –:: OnInitDialog

Rozhraní volá tuto funkci při inicializaci dialogového okna stránky vlastností.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrátí hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Přepsat, pokud se při inicializaci dialogového okna vyžaduje nějaká zvláštní akce. Výchozí implementace volá `CDialog::OnInitDialog` a vrátí hodnotu FALSE.

##  <a name="onobjectschanged"></a>COlePropertyPage –:: OnObjectsChanged

Volá se rozhraním, když se vybere jiný ovládací prvek OLE, s novými vlastnostmi.

```
virtual void OnObjectsChanged();
```

### <a name="remarks"></a>Poznámky

Při prohlížení vlastností ovládacího prvku OLE ve vývojovém prostředí se k zobrazení svých stránek vlastností používá nemodální dialogové okno. Pokud je vybraný jiný ovládací prvek, pro novou sadu vlastností se musí zobrazit jiná sada stránek vlastností. Rozhraní volá tuto funkci, aby upozornila stránku vlastností na změnu.

Přepište tuto funkci, pokud chcete dostávat oznámení o této akci a provést všechny zvláštní akce.

##  <a name="onsetpagesite"></a>COlePropertyPage –:: OnSetPageSite

Rozhraní volá tuto funkci, když rámec vlastnosti poskytuje stránku vlastností stránky.

```
virtual void OnSetPageSite();
```

### <a name="remarks"></a>Poznámky

Výchozí implementace načte titulek stránky a pokusí se určit velikost stránky z prostředku dialogového okna. Tuto funkci přepište, pokud vaše stránka vlastností vyžaduje jakoukoli další akci. vaše přepsání by mělo zavolat implementaci základní třídy.

##  <a name="setcontrolstatus"></a>COlePropertyPage –:: SetControlStatus

Změní stav ovládacího prvku stránka vlastností.

```
BOOL SetControlStatus(
    UINT nID,
    BOOL bDirty);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Obsahuje ID ovládacího prvku stránky vlastností.

*bDirty*<br/>
Určuje, zda bylo upraveno pole stránky vlastností. Nastavte na hodnotu TRUE, pokud bylo pole změněno, FALSE, pokud nebylo upraveno.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud zadaný ovládací prvek byl nastaven; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Pokud je stav ovládacího prvku stránka vlastností při zavření stránky vlastností nečistý nebo je vybráno tlačítko použít, bude vlastnost ovládacího prvku aktualizována odpovídající hodnotou.

##  <a name="setdialogresource"></a>COlePropertyPage –:: SetDialogResource

Nastaví prostředek dialogového okna stránky vlastností.

```
void SetDialogResource(HGLOBAL hDialog);
```

### <a name="parameters"></a>Parametry

*hDialog*<br/>
Pořídí prostředek dialogového okna stránky vlastností.

##  <a name="sethelpinfo"></a>COlePropertyPage –:: SetHelpInfo

Určuje informace o popisku, název souboru nápovědy a kontext nápovědy pro vaši stránku vlastností.

```
void SetHelpInfo(
    LPCTSTR lpszDocString,
    LPCTSTR lpszHelpFile = NULL,
    DWORD dwHelpContext = 0);
```

### <a name="parameters"></a>Parametry

*lpszDocString*<br/>
Řetězec obsahující stručné informace o nápovědě pro zobrazení ve stavovém řádku nebo jiném umístění.

*lpszHelpFile*<br/>
Název souboru Help stránky vlastností

*dwHelpContext*<br/>
Kontext kontextové nápovědu pro stránku vlastností

##  <a name="setmodifiedflag"></a>COlePropertyPage –:: SetModifiedFlag

Určuje, zda uživatel změnil stránku vlastností.

```
void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Parametry

*bModified*<br/>
Určuje novou hodnotu příznaku pro úpravu stránky vlastností.

##  <a name="setpagename"></a>COlePropertyPage –:: SetPageName

Nastaví název stránky vlastností, který se bude na kartě stránky obvykle zobrazovat jako rámeček vlastnosti.

```
void SetPageName(LPCTSTR lpszPageName);
```

### <a name="parameters"></a>Parametry

*lpszPageName*<br/>
Ukazatel na řetězec obsahující název stránky vlastností.

## <a name="see-also"></a>Viz také

[CIRC3 Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[TESTHELP Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CDialog – třída](../../mfc/reference/cdialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDialog – třída](../../mfc/reference/cdialog-class.md)
