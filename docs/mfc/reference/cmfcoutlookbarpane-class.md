---
title: CMFCOutlookBarPane – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCOutlookBarPane
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::AddButton
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::CanBeAttached
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::ClearAll
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::Create
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::EnablePageScrollMode
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::GetRegularColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::IsBackgroundTexture
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::IsDrawShadedHighlight
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::RemoveButton
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetBackColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetBackImage
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetDefaultState
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetExtraSpace
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetTextColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetTransparentColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::EnableContextMenuItems
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::RemoveAllButtons
helpviewer_keywords:
- CMFCOutlookBarPane [MFC], AddButton
- CMFCOutlookBarPane [MFC], CanBeAttached
- CMFCOutlookBarPane [MFC], ClearAll
- CMFCOutlookBarPane [MFC], Create
- CMFCOutlookBarPane [MFC], EnablePageScrollMode
- CMFCOutlookBarPane [MFC], GetRegularColor
- CMFCOutlookBarPane [MFC], IsBackgroundTexture
- CMFCOutlookBarPane [MFC], IsDrawShadedHighlight
- CMFCOutlookBarPane [MFC], RemoveButton
- CMFCOutlookBarPane [MFC], SetBackColor
- CMFCOutlookBarPane [MFC], SetBackImage
- CMFCOutlookBarPane [MFC], SetDefaultState
- CMFCOutlookBarPane [MFC], SetExtraSpace
- CMFCOutlookBarPane [MFC], SetTextColor
- CMFCOutlookBarPane [MFC], SetTransparentColor
- CMFCOutlookBarPane [MFC], EnableContextMenuItems
- CMFCOutlookBarPane [MFC], RemoveAllButtons
ms.assetid: 094e2ef3-a118-487e-a4cc-27626108fe08
ms.openlocfilehash: 9ef6a06a4889119e39e72a9e495e5d4f9e17cf56
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505155"
---
# <a name="cmfcoutlookbarpane-class"></a>CMFCOutlookBarPane – třída

Další podrobnosti najdete ve zdrojovém kódu ve složce **VC\\atlmfc\\src\\MFC** v instalaci sady Visual Studio.

Ovládací prvek odvozený z [třídy CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md) , který může být vložen do panelu aplikace Outlook ( [Třída CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)). Podokno panelu aplikace Outlook obsahuje sloupec velkých tlačítek. Uživatel může přejít nahoru a dolů seznam tlačítek, pokud je větší než podokno. Když uživatel odpojí podokno panelu Outlook z panelu aplikace Outlook, může v hlavním okně rámce zůstat nebo Dock.

## <a name="syntax"></a>Syntaxe

```
class CMFCOutlookBarPane : public CMFCToolBar
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|`CMFCOutlookBarPane::CMFCOutlookBarPane`|Výchozí konstruktor|
|`CMFCOutlookBarPane::~CMFCOutlookBarPane`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMFCOutlookBarPane::AddButton](#addbutton)|Přidá tlačítko do podokna panelu aplikace Outlook.|
|[CMFCOutlookBarPane::CanBeAttached](#canbeattached)|Určuje, zda lze podokno ukotvit do jiného podokna nebo okna rámce. (Overrides [CBasePane:: CanBeAttached](../../mfc/reference/cbasepane-class.md#canbeattached).)|
|`CMFCOutlookBarPane::CanBeRestored`|Určuje, zda systém může po přizpůsobení obnovit původní stav panelu nástrojů. (Overrides [CMFCToolBar:: CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored).)|
|[CMFCOutlookBarPane:: ClearAll](#clearall)|Uvolní prostředky používané obrázky v podokně panelu aplikace Outlook.|
|[CMFCOutlookBarPane:: Create](#create)|Vytvoří podokno panelu aplikace Outlook.|
|`CMFCOutlookBarPane::CreateObject`|Používá se rozhraním k vytvoření dynamické instance tohoto typu třídy.|
|`CMFCOutlookBarPane::Dock`|Volá se rozhraním, aby se mohlo ukotvit podokno panelu Outlooku. (Overrides `CPane::Dock`.)|
|[CMFCOutlookBarPane::EnablePageScrollMode](#enablepagescrollmode)|Určuje, zda se šipky posuvníku v podokně panelu aplikace Outlook budou nacházet v seznamu tlačítek podle stránky nebo tlačítkem.|
|[CMFCOutlookBarPane::GetRegularColor](#getregularcolor)|Vrátí běžnou (nevybranou) barvu textu podokna panelu aplikace Outlook.|
|`CMFCOutlookBarPane::GetThisClass`|Používá se rozhraním, aby se získal ukazatel na objekt [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , který je přidružený k tomuto typu třídy.|
|[CMFCOutlookBarPane::IsBackgroundTexture](#isbackgroundtexture)|Určuje, zda je pro podokno panelu aplikace Outlook načten obrázek pozadí.|
|`CMFCOutlookBarPane::IsChangeState`|Určuje, zda může být plovoucí podokno ukotveno. (Overrides `CPane::IsChangeState`.)|
|[CMFCOutlookBarPane::IsDrawShadedHighlight](#isdrawshadedhighlight)|Určuje, zda je ohraničení tlačítka zobrazeno při zvýraznění tlačítka a zobrazení obrázku pozadí.|
|`CMFCOutlookBarPane::OnBeforeFloat`|Volá se rozhraním, když má podokno hodnotu float. (Overrides [CPane:: OnBeforeFloat](../../mfc/reference/cpane-class.md#onbeforefloat).)|
|[CMFCOutlookBarPane::RemoveButton](#removebutton)|Odebere tlačítko, které má zadané ID příkazu.|
|`CMFCOutlookBarPane::RestoreOriginalstate`|Obnoví původní stav panelu nástrojů. (Overrides [CMFCToolBar:: RestoreOriginalState](../../mfc/reference/cmfctoolbar-class.md#restoreoriginalstate).)|
|[CMFCOutlookBarPane::SetBackColor](#setbackcolor)|Nastaví barvu pozadí.|
|[CMFCOutlookBarPane::SetBackImage](#setbackimage)|Nastaví obrázek pozadí.|
|[CMFCOutlookBarPane::SetDefaultState](#setdefaultstate)|Obnoví podokno panelu aplikace Outlook na původní sadu tlačítek.|
|[CMFCOutlookBarPane::SetExtraSpace](#setextraspace)|Nastaví počet pixelů odsazení, který se používá kolem tlačítek v podokně panelu aplikace Outlook.|
|[CMFCOutlookBarPane::SetTextColor](#settextcolor)|Nastaví barvy regulárního a zvýrazněného textu v podokně panelu aplikace Outlook.|
|[CMFCOutlookBarPane::SetTransparentColor](#settransparentcolor)|Nastaví průhlednou barvu podokna panelu aplikace Outlook.|
|`CMFCOutlookBarPane::SmartUpdate`|Používá se interně k aktualizaci panelu Outlooku. (Overrides `CMFCToolBar::SmartUpdate`.)|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[CMFCOutlookBarPane::EnableContextMenuItems](#enablecontextmenuitems)|Určuje, které položky místní nabídky se mají zobrazit v režimu přizpůsobení.|
|[CMFCOutlookBarPane::RemoveAllButtons](#removeallbuttons)|Odebere všechna tlačítka z podokna panelu aplikace Outlook. (Overrides [CMFCToolBar:: RemoveAllButtons](../../mfc/reference/cmfctoolbar-class.md#removeallbuttons).)|

## <a name="remarks"></a>Poznámky

Informace o tom, jak implementovat panel aplikace Outlook, naleznete v tématu [Třída CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md).

Příklad panelu aplikace Outlook naleznete v ukázkovém projektu OutlookDemo.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít různé metody `CMFCOutlookBarPane` třídy. Tento příklad ukazuje, jak vytvořit podokno panelu aplikace Outlook, povolit režim posouvání stránky, Povolit ukotvení a nastavit barvu pozadí panelu aplikace Outlook. Tento fragment kódu je součástí ukázky pro [Outlook multi views](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_OutlookMultiViews#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_1.h)]
[!code-cpp[NVC_MFC_OutlookMultiViews#4](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxoutlookbarpane. h

##  <a name="addbutton"></a>CMFCOutlookBarPane::AddButton

Přidá tlačítko do podokna panelu aplikace Outlook.

```
BOOL AddButton(
    UINT uiImage,
    LPCTSTR lpszLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    UINT uiImage,
    UINT uiLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    LPCTSTR szBmpFileName,
    LPCTSTR szLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    HBITMAP hBmp,
    LPCTSTR lpszLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    HICON hIcon,
    LPCTSTR lpszLabel,
    UINT iIdCommand,
    int iInsertAt=-1,
    BOOL bAlphaBlend=FALSE);
```

### <a name="parameters"></a>Parametry

*uiImage*<br/>
pro Určuje identifikátor prostředku rastrového obrázku.

*lpszLabel*<br/>
pro Určuje text tlačítka.

*iIdCommand*<br/>
pro Určuje ID ovládacího prvku tlačítko.

*iInsertAt*<br/>
pro Určuje index založený na nule na stránce panelu aplikace Outlook, na kterou má být tlačítko vloženo.

*uiLabel*<br/>
pro ID prostředku řetězce.

*szBmpFileName*<br/>
pro Určuje název souboru bitové kopie disku, který se má načíst.

*szLabel*<br/>
pro Určuje text tlačítka.

*hBmp*<br/>
pro Popisovač rastrového obrázku tlačítka.

*hIcon*<br/>
pro Popisovač ikony tlačítek

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud bylo tlačítko úspěšně přidáno; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte, chcete-li vložit nové tlačítko na stránku na panelu aplikace Outlook. Obrázek tlačítka lze načíst buď z prostředků aplikace, nebo ze souboru na disku.

Pokud je ID stránky určené parametrem *uiPageID* -1, tlačítko je vloženo do první stránky.

Pokud je index určený parametrem *iInsertAt* -1, tlačítko je přidáno na konci stránky.

##  <a name="canbeattached"></a>CMFCOutlookBarPane::CanBeAttached

Další podrobnosti najdete ve zdrojovém kódu ve složce **VC\\atlmfc\\src\\MFC** v instalaci sady Visual Studio.

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="clearall"></a>CMFCOutlookBarPane:: ClearAll

Uvolní prostředky používané obrázky v podokně panelu aplikace Outlook.

```
void ClearAll();
```

### <a name="remarks"></a>Poznámky

Tato metoda přímo volá metodu [CMFCToolBarImages:: Clear](../../mfc/reference/cmfctoolbarimages-class.md#clear), která je volána na obrázcích používaných podoknem panelu aplikace Outlook.

##  <a name="create"></a>CMFCOutlookBarPane:: Create

Vytvoří podokno panelu aplikace Outlook.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle=AFX_DEFAULT_TOOLBAR_STYLE,
    UINT uiID=(UINT)-1,
    DWORD dwControlBarStyle=0);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
pro Určuje nadřazené okno ovládacího prvku podokna panelu aplikace Outlook. Nesmí mít hodnotu NULL.

*dwStyle*<br/>
pro Styl okna  Seznam stylů oken naleznete v tématu [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*uiID*<br/>
pro ID ovládacího prvku Musí být jedinečný, aby bylo možné uložit stav ovládacího prvku.

*dwControlBarStyle*<br/>
pro Určuje speciální styly, které definují chování ovládacího prvku podokna panelu aplikace Outlook, když je odpojen z panelu aplikace Outlook.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byla metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Chcete-li `CMFCOutlookBarPane` vytvořit objekt, nejprve volejte konstruktor a potom zavolejte `Create`, čímž se vytvoří ovládací prvek podokno panelu aplikace Outlook a `CMFCOutlookBarPane` připojí ho k objektu.

Další informace `dwControlBarStyle` najdete v tématu [CBasePane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex).

##  <a name="enablecontextmenuitems"></a>CMFCOutlookBarPane::EnableContextMenuItems

Určuje, které položky místní nabídky se mají zobrazit v režimu přizpůsobení.

```
virtual BOOL EnableContextMenuItems(
    CMFCToolBarButton* pButton,
    CMenu* pPopup);
```

### <a name="parameters"></a>Parametry

*pButton*<br/>
pro Ukazatel na tlačítko panelu nástrojů, na které uživatel kliknul

*pPopup*<br/>
pro Ukazatel na místní nabídku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud se má místní nabídka Zobrazit. v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tuto metodu přepište pro úpravu standardní místní nabídky rozhraní, kterou rozhraní zobrazuje v režimu přizpůsobení.

Výchozí implementace kontroluje režim přizpůsobení ( [CMFCToolBar:: IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)) a pokud je nastavená na hodnotu true, zakáže všechny položky místní nabídky s výjimkou **Delete**. Poté pouze předává vstupní parametry do `CMFCToolBar::EnableContextMenuItems`.

> [!NOTE]
> *Místní* nabídka je synonymem pro místní nabídku.

##  <a name="enablepagescrollmode"></a>CMFCOutlookBarPane::EnablePageScrollMode

Určuje, zda se šipky posuvníku v podokně panelu aplikace Outlook posouvají na seznam tlačítek na stránce nebo tlačítko podle tlačítka.

```
void EnablePageScrollMode(BOOL bPageScroll=TRUE);
```

### <a name="parameters"></a>Parametry

*bPageScroll*<br/>
pro Je-li nastavena hodnota TRUE, Povolte režim posouvání stránky. Pokud je hodnota FALSE, zakažte režim posouvání stránky.

##  <a name="getregularcolor"></a>CMFCOutlookBarPane::GetRegularColor

Vrátí normální barvu textu (tj. není vybraná) podokna panelu aplikace Outlook.

```
DECLARE_MESSAGE_MAPCOLORREF GetRegularColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální barva textu jako hodnota barvy RGB.

### <a name="remarks"></a>Poznámky

K nastavení aktuální (běžné a vybrané) barvy textu na panelu aplikace Outlook použijte [CMFCOutlookBarPane:: SetTextColor](#settextcolor) . Výchozí barvu textu můžete získat voláním funkce [GetSysColor](/windows/win32/api/winuser/nf-winuser-getsyscolor) s indexem COLOR_WINDOW.

##  <a name="isbackgroundtexture"></a>CMFCOutlookBarPane::IsBackgroundTexture

Určuje, zda je pro podokno panelu aplikace Outlook načten obrázek pozadí.

```
BOOL IsBackgroundTexture() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je k zobrazení k dispozici obrázek pozadí; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Můžete přidat obrázek pozadí voláním funkce [CMFCOutlookBarPane:: SetBackImage](#setbackimage) .

Pokud není k dispozici žádný obrázek pozadí, pozadí je vykresleno barvou určenou pomocí [CMFCOutlookBarPane:: SetBackColor](#setbackcolor).

##  <a name="isdrawshadedhighlight"></a>CMFCOutlookBarPane::IsDrawShadedHighlight

Určuje, zda je ohraničení tlačítka zobrazeno při zvýraznění tlačítka a zobrazení obrázku pozadí.

```
BOOL IsDrawShadedHighlight() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud jsou ohraničení tlačítka šedá; v opačném případě FALSE.

##  <a name="removeallbuttons"></a>CMFCOutlookBarPane::RemoveAllButtons

Odebere všechna tlačítka z podokna panelu aplikace Outlook.

```
virtual void RemoveAllButtons();
```

##  <a name="removebutton"></a>CMFCOutlookBarPane::RemoveButton

Odebere tlačítko, které má zadané ID příkazu.

```
BOOL RemoveButton(UINT iIdCommand);
```

### <a name="parameters"></a>Parametry

*iIdCommand*<br/>
pro Určuje ID příkazu pro odebrání tlačítka.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud bylo tlačítko úspěšně odebráno; FALSE, pokud zadané ID příkazu není platné.

##  <a name="setbackcolor"></a>CMFCOutlookBarPane::SetBackColor

Nastaví barvu pozadí panelu aplikace Outlook.

```
void SetBackColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*barevných*<br/>
pro Určuje novou barvu pozadí.

### <a name="remarks"></a>Poznámky

Voláním této funkce nastavíte aktuální barvu pozadí panelu aplikace Outlook. Barva pozadí se používá pouze v případě, že není k dispozici žádný obrázek na pozadí.

##  <a name="setbackimage"></a>CMFCOutlookBarPane::SetBackImage

Nastaví obrázek pozadí.

```
void SetBackImage(UINT uiImageID);
```

### <a name="parameters"></a>Parametry

*uiImageID*<br/>
pro Určuje ID prostředku obrázku.

### <a name="remarks"></a>Poznámky

Voláním této metody nastavíte obrázek pozadí panelu aplikace Outlook. Seznam imagí pozadí je spravovaný objektem vložené [třídy CMFCToolBarImages](../../mfc/reference/cmfctoolbarimages-class.md) .

##  <a name="setdefaultstate"></a>CMFCOutlookBarPane::SetDefaultState

Obnoví podokno panelu aplikace Outlook na původní sadu tlačítek.

```
void SetDefaultState();
```

### <a name="remarks"></a>Poznámky

Tato metoda obnoví tlačítka panelu aplikace Outlook na původní sadu. Tato metoda je podobná `CMFCOutlookBarPane::RestoreOriginalstate`, s tím rozdílem, že neaktivuje překreslování podokna panelu aplikace Outlook.

##  <a name="setextraspace"></a>CMFCOutlookBarPane::SetExtraSpace

Nastaví počet pixelů odsazení, který se používá kolem tlačítek v podokně panelu aplikace Outlook.

```
void SetExtraSpace()
```

##  <a name="settextcolor"></a>CMFCOutlookBarPane::SetTextColor

Nastaví barvy regulárního a zvýrazněného textu v podokně panelu aplikace Outlook.

```
void SetTextColor(
    COLORREF clrRegText,
    COLORREF clrSelText=0);
```

### <a name="parameters"></a>Parametry

*clrRegText*<br/>
pro Určuje novou barvu pro nevybraný text.

*clrSelText*<br/>
pro Určuje novou barvu pro vybraný text.

##  <a name="settransparentcolor"></a>CMFCOutlookBarPane::SetTransparentColor

Nastaví průhlednou barvu podokna panelu aplikace Outlook.

```
void SetTransparentColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*barevných*<br/>
Určuje novou průhlednou barvu.

### <a name="remarks"></a>Poznámky

Průhledná barva je nutná k zobrazení průhledných obrázků. Všechny výskyty této barvy v obrázku jsou místo toho vykresleny barvou pozadí.  Neexistují žádné prolnutí obrázků pozadí a popředí.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCOutlookBar – třída](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CMFCOutlookBarTabCtrl – třída](../../mfc/reference/cmfcoutlookbartabctrl-class.md)
