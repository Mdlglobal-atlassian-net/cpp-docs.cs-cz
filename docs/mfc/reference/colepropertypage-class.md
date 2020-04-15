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
ms.openlocfilehash: dbdc889e244b33365756bcbae5b37cf657a6d900
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374879"
---
# <a name="colepropertypage-class"></a>COlePropertyPage – třída

Slouží k zobrazení vlastností vlastního ovládacího prvku v grafickém rozhraní, podobně jako dialogové okno.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE COlePropertyPage : public CDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[COlePropertyPage::COlePropertyPage](#colepropertypage)|Vytvoří `COlePropertyPage` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[COlePropertyPage::GetControlStatus](#getcontrolstatus)|Označuje, zda uživatel změnil hodnotu v ovládacím prvku.|
|[COlePropertyPage::GetObjectArray](#getobjectarray)|Vrátí pole objektů upravovaných stránkou vlastností.|
|[COlePropertyPage::GetPageSite](#getpagesite)|Vrátí ukazatel na `IPropertyPageSite` rozhraní stránky vlastností.|
|[COlePropertyPage::IgnoreApply](#ignoreapply)|Určuje, které ovládací prvky nepovolují tlačítko Použít.|
|[COlePropertyPage::IsModified](#ismodified)|Označuje, zda uživatel změnil stránku vlastností.|
|[COlePropertyPage::OnEditProperty](#oneditproperty)|Volat rámci při uživatel im editace vlastnosti.|
|[COlePropertyPage::OnHelp](#onhelp)|Volat rámci při uživatel vyvolá pomoc.|
|[COlePropertyPage::OnInitDialog](#oninitdialog)|Volat rámci při inicializována stránka vlastností.|
|[COlePropertyPage::OnObjectsChanged](#onobjectschanged)|Volat rámci při jiné ho ole ovládací prvek s novými vlastnostmi, je vybrán.|
|[COlePropertyPage::onsetpagesite](#onsetpagesite)|Volat rámci, když rámec vlastností poskytuje webu stránky.|
|[COlePropertyPage::SetControlStatus](#setcontrolstatus)|Nastaví příznak označující, zda uživatel změnil hodnotu v ovládacím prvku.|
|[COlePropertyPage::SetDialogResource](#setdialogresource)|Nastaví prostředek dialogového okna stránky vlastností.|
|[COlePropertyPage::SetHelpInfo](#sethelpinfo)|Nastaví stručný text nápovědy stránky vlastností, název souboru nápovědy a kontext nápovědy.|
|[COlePropertyPage::SetModifiedFlag](#setmodifiedflag)|Nastaví příznak označující, zda uživatel změnil stránku vlastností.|
|[COlePropertyPage::SetPageName](#setpagename)|Nastaví název stránky vlastností (titulek).|

## <a name="remarks"></a>Poznámky

Například stránka vlastností může obsahovat ovládací prvek úprav, který umožňuje uživateli zobrazit a upravit vlastnost titulku ovládacího prvku.

Každá vlastnost vlastní nebo burzovní ovládací prvek může mít dialogové okno ovládací prvek, který umožňuje uživateli ovládacího prvku zobrazit aktuální hodnotu vlastnosti a upravit tuto hodnotu v případě potřeby.

Další informace o `COlePropertyPage`použití naleznete v článku [Ovládací prvky ActiveX: Stránky vlastností](../../mfc/mfc-activex-controls-property-pages.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

`COlePropertyPage`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxctl.h

## <a name="colepropertypagecolepropertypage"></a><a name="colepropertypage"></a>COlePropertyPage::COlePropertyPage

Vytvoří `COlePropertyPage` objekt.

```
COlePropertyPage(
    UINT idDlg,
    UINT idCaption);
```

### <a name="parameters"></a>Parametry

*idDlg*<br/>
ID prostředku šablony dialogu.

*idTitulek*<br/>
ID prostředku titulku stránky vlastností.

### <a name="remarks"></a>Poznámky

Při implementaci podtřídy `COlePropertyPage`, konstruktor u podtřídy `COlePropertyPage` by měl použít konstruktor k identifikaci prostředku šablony dialogu, na kterém je stránka vlastnosti založena, a řetězcového prostředku obsahujícího jeho titulek.

## <a name="colepropertypagegetcontrolstatus"></a><a name="getcontrolstatus"></a>COlePropertyPage::GetControlStatus

Určuje, zda uživatel změnil hodnotu ovládacího prvku stránky vlastností pomocí zadaného ID prostředku.

```
BOOL GetControlStatus(UINT nID);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
ID prostředku ovládacího prvku stránky vlastností.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byla změněna hodnota ovládacího prvku; jinak FALSE.

## <a name="colepropertypagegetobjectarray"></a><a name="getobjectarray"></a>COlePropertyPage::GetObjectArray

Vrátí pole objektů upravovaných stránkou vlastností.

```
LPDISPATCH* GetObjectArray(ULONG* pnObjects);
```

### <a name="parameters"></a>Parametry

*pnObjekty*<br/>
Ukazatel na nepodepsané dlouhé celé číslo, které obdrží počet objektů upravovaných stránkou.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na pole `IDispatch` ukazatelů, které se používají pro přístup k vlastnostem každého ovládacího prvku na stránce vlastností. Volající nesmí uvolnit tyto ukazatele rozhraní.

### <a name="remarks"></a>Poznámky

Každý objekt stránky vlastností udržuje pole `IDispatch` ukazatelů na rozhraní objektů upravovaných stránkou. Tato funkce nastaví jeho *pnObjects* argument na počet prvků v tomto poli a vrátí ukazatel na první prvek pole.

## <a name="colepropertypagegetpagesite"></a><a name="getpagesite"></a>COlePropertyPage::GetPageSite

Získá ukazatel na `IPropertyPageSite` rozhraní stránky vlastností.

```
LPPROPERTYPAGESITE GetPageSite();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `IPropertyPageSite` rozhraní stránky vlastností.

### <a name="remarks"></a>Poznámky

Ovládací prvky a kontejnery spolupracují tak, aby uživatelé mohli procházet a upravovat vlastnosti ovládacího prvku. Ovládací prvek poskytuje stránky vlastností, z nichž každá je objekt OLE, který umožňuje uživateli upravit související sadu vlastností. Kontejner poskytuje rámec vlastností, který zobrazuje stránky vlastností. Pro každou stránku obsahuje rámeček vlastností `IPropertyPageSite` web stránky, který podporuje rozhraní.

## <a name="colepropertypageignoreapply"></a><a name="ignoreapply"></a>COlePropertyPage::IgnoreApply

Určuje, které ovládací prvky nepovolují tlačítko Použít.

```
void IgnoreApply(UINT nID);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
ID ovládacího prvku, který má být ignorován.

### <a name="remarks"></a>Poznámky

Tlačítko Použít na stránce vlastností je povoleno pouze v případě, že byly změněny hodnoty ovládacích prvků stránky vlastností. Tato funkce slouží k určení ovládacích prvků, které nezpůsobí, že tlačítko Použít bude povoleno při změně jejich hodnot.

## <a name="colepropertypageismodified"></a><a name="ismodified"></a>COlePropertyPage::IsModified

Určuje, zda uživatel změnil všechny hodnoty na stránce vlastností.

```
BOOL IsModified();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byla stránka vlastností změněna.

## <a name="colepropertypageoneditproperty"></a><a name="oneditproperty"></a>COlePropertyPage::OnEditProperty

Framework volá tuto funkci, když má být upravena určitá vlastnost.

```
virtual BOOL OnEditProperty(DISPID dispid);
```

### <a name="parameters"></a>Parametry

*Dispid*<br/>
ID odeslání upravované vlastnosti.

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrátí hodnotu NEPRAVDA. Přepsání této funkce by měla vrátit hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Můžete přepsat a nastavit fokus na příslušný ovládací prvek na stránce. Výchozí implementace neprovede žádné funkce a vrátí hodnotu FALSE.

## <a name="colepropertypageonhelp"></a><a name="onhelp"></a>COlePropertyPage::OnHelp

Rozhraní Framework volá tuto funkci, když uživatel požádá o online nápovědu.

```
virtual BOOL OnHelp(LPCTSTR lpszHelpDir);
```

### <a name="parameters"></a>Parametry

*lpszHelpDir*<br/>
Adresář obsahující soubor nápovědy stránky vlastností.

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrátí hodnotu NEPRAVDA.

### <a name="remarks"></a>Poznámky

Přepište ji, pokud vaše stránka vlastností musí provést nějakou zvláštní akci, když uživatel přistupuje k nápovědě. Výchozí implementace neprovede žádné a vrátí false, který instruuje rozhraní pro volání WinHelp.

## <a name="colepropertypageoninitdialog"></a><a name="oninitdialog"></a>COlePropertyPage::OnInitDialog

Rozhraní Framework volá tuto funkci při inicializování dialogového okna stránky vlastností.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Návratová hodnota

Výchozí implementace vrátí hodnotu NEPRAVDA.

### <a name="remarks"></a>Poznámky

Přepište ji, pokud je při inicializování dialogového okna vyžadována nějaká speciální akce. Výchozí implementace `CDialog::OnInitDialog` volá a vrátí hodnotu NEPRAVDA.

## <a name="colepropertypageonobjectschanged"></a><a name="onobjectschanged"></a>COlePropertyPage::OnObjectsChanged

Volat rámci při jiné ho ole ovládací prvek s novými vlastnostmi, je vybrán.

```
virtual void OnObjectsChanged();
```

### <a name="remarks"></a>Poznámky

Při zobrazení vlastností ovládacího prvku OLE v prostředí pro vývojáře se k zobrazení stránek vlastností používá nemodální dialogové okno. Pokud je vybrán jiný ovládací prvek, musí být pro novou sadu vlastností zobrazena jiná sada stránek vlastností. Rozhraní Framework volá tuto funkci upozornit stránku vlastností změny.

Přepište tuto funkci, chcete-li přijímat oznámení o této akci a provádět jakékoli zvláštní akce.

## <a name="colepropertypageonsetpagesite"></a><a name="onsetpagesite"></a>COlePropertyPage::onsetpagesite

Framework volá tuto funkci, když rámec vlastností poskytuje stránku stránky stránky webu vlastností.

```
virtual void OnSetPageSite();
```

### <a name="remarks"></a>Poznámky

Výchozí implementace načte popisek stránky a pokusí se určit velikost stránky z prostředku dialogu. Přepsat tuto funkci, pokud vaše stránka vlastností vyžaduje další akci; přepsání by mělo volat implementaci základní třídy.

## <a name="colepropertypagesetcontrolstatus"></a><a name="setcontrolstatus"></a>COlePropertyPage::SetControlStatus

Změní stav ovládacího prvku stránky vlastností.

```
BOOL SetControlStatus(
    UINT nID,
    BOOL bDirty);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Obsahuje ID ovládacího prvku stránky vlastností.

*bDirty*<br/>
Určuje, zda bylo pole stránky vlastností změněno. Pokud bylo pole změněno, nepravda, nastavte hodnotu PRAVDA, neplatí, pokud nebylo změněno.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byl zadaný ovládací prvek nastaven; jinak FALSE.

### <a name="remarks"></a>Poznámky

Pokud je stav ovládacího prvku stránky vlastností nečistý, když je stránka vlastností zavřená nebo je vybráno tlačítko Použít, bude vlastnost ovládacího prvku aktualizována příslušnou hodnotou.

## <a name="colepropertypagesetdialogresource"></a><a name="setdialogresource"></a>COlePropertyPage::SetDialogResource

Nastaví prostředek dialogového okna stránky vlastností.

```
void SetDialogResource(HGLOBAL hDialog);
```

### <a name="parameters"></a>Parametry

*hDialog*<br/>
Zpracovat prostředek dialogového okna stránky vlastností.

## <a name="colepropertypagesethelpinfo"></a><a name="sethelpinfo"></a>COlePropertyPage::SetHelpInfo

Určuje informace popisku, název souboru nápovědy a kontext nápovědy pro stránku vlastností.

```
void SetHelpInfo(
    LPCTSTR lpszDocString,
    LPCTSTR lpszHelpFile = NULL,
    DWORD dwHelpContext = 0);
```

### <a name="parameters"></a>Parametry

*lpszDocString*<br/>
Řetězec obsahující stručné informace nápovědy pro zobrazení ve stavovém řádku nebo jiném umístění.

*soubor lpszHelpFile*<br/>
Název souboru nápovědy stránky vlastností.

*dwHelpKontext*<br/>
Kontext nápovědy pro stránku vlastností.

## <a name="colepropertypagesetmodifiedflag"></a><a name="setmodifiedflag"></a>COlePropertyPage::SetModifiedFlag

Označuje, zda uživatel změnil stránku vlastností.

```
void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Parametry

*bZměněno*<br/>
Určuje novou hodnotu upraveného příznaku stránky vlastností.

## <a name="colepropertypagesetpagename"></a><a name="setpagename"></a>COlePropertyPage::SetPageName

Nastaví název stránky vlastností, který se rámeček vlastností obvykle zobrazí na kartě stránky.

```
void SetPageName(LPCTSTR lpszPageName);
```

### <a name="parameters"></a>Parametry

*lpszPageName*<br/>
Ukazatel na řetězec obsahující název stránky vlastností.

## <a name="see-also"></a>Viz také

[Vzorek knihovny MFC CIRC3](../../overview/visual-cpp-samples.md)<br/>
[Testhelp vzorku knihovny MFC](../../overview/visual-cpp-samples.md)<br/>
[CDialog – třída](../../mfc/reference/cdialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDialog – třída](../../mfc/reference/cdialog-class.md)
