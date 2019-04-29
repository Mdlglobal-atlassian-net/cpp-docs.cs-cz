---
title: Cmfcoutlookbarpane – třída
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
ms.openlocfilehash: b23aa9e30c130cea8c84290b62cc19794376d4c1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374100"
---
# <a name="cmfcoutlookbarpane-class"></a>Cmfcoutlookbarpane – třída

Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.

Ovládací prvek odvozený z [cmfctoolbar – třída](../../mfc/reference/cmfctoolbar-class.md) lze vložit do panel aplikace Outlook ( [CMFCOutlookBar – třída](../../mfc/reference/cmfcoutlookbar-class.md)). Podokno panelu aplikace Outlook obsahuje sloupec velkých tlačítek. Uživatel může posunout nahoru nebo dolů seznam tlačítek, pokud je větší než podokno. Když uživatel odpojí podokno panelu Outlook z panelu aplikace Outlook, může uvolnit nebo ukotvit v hlavním okně rámce.

## <a name="syntax"></a>Syntaxe

```
class CMFCOutlookBarPane : public CMFCToolBar
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|`CMFCOutlookBarPane::CMFCOutlookBarPane`|Výchozí konstruktor.|
|`CMFCOutlookBarPane::~CMFCOutlookBarPane`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCOutlookBarPane::AddButton](#addbutton)|Přidá tlačítko do podokno panelu aplikace Outlook.|
|[CMFCOutlookBarPane::CanBeAttached](#canbeattached)|Určuje, zda lze ukotvit podokna Další podokno nebo rámec okna. (Přepíše [CBasePane::CanBeAttached](../../mfc/reference/cbasepane-class.md#canbeattached).)|
|`CMFCOutlookBarPane::CanBeRestored`|Určuje, zda systém může panel nástrojů – obnovit do původního stavu po přizpůsobení. (Přepíše [CMFCToolBar::CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored).)|
|[CMFCOutlookBarPane::ClearAll](#clearall)|Uvolní prostředky využívané třídou imagí v podokno panelu aplikace Outlook.|
|[CMFCOutlookBarPane::Create](#create)|Vytvoří podokno panelu aplikace Outlook.|
|`CMFCOutlookBarPane::CreateObject`|Rozhraní používá k vytvoření dynamické instance tohoto typu třídy.|
|`CMFCOutlookBarPane::Dock`|Volá se rozhraním, které chcete ukotvit podokno panelu aplikace Outlook. (Přepíše `CPane::Dock`.)|
|[CMFCOutlookBarPane::EnablePageScrollMode](#enablepagescrollmode)|Určuje, zda šipky na podokno panelu Outlook předem seznam tlačítek, stránky, nebo tlačítko.|
|[CMFCOutlookBarPane::GetRegularColor](#getregularcolor)|Vrátí barvu běžný text (nevybraných) podokno panelu aplikace Outlook.|
|`CMFCOutlookBarPane::GetThisClass`|Používá k získání ukazatele na rámec [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený k typu třídy.|
|[CMFCOutlookBarPane::IsBackgroundTexture](#isbackgroundtexture)|Určuje, jestli je obrázek pozadí pro podokno panelu aplikace Outlook se nenačetly.|
|`CMFCOutlookBarPane::IsChangeState`|Určuje, zda může být ukotven plovoucího podokna. (Přepíše `CPane::IsChangeState`.)|
|[CMFCOutlookBarPane::IsDrawShadedHighlight](#isdrawshadedhighlight)|Určuje, zda je tlačítko ohraničení označeno šedou barvou při tlačítka se zvýrazní a zobrazí se obrázek na pozadí.|
|`CMFCOutlookBarPane::OnBeforeFloat`|Volá se rozhraním, když na stavového řádku o plovoucí desetinnou čárkou. (Přepíše [CPane::OnBeforeFloat](../../mfc/reference/cpane-class.md#onbeforefloat).)|
|[CMFCOutlookBarPane::RemoveButton](#removebutton)|Odebere tlačítko, která má ID zadaného příkazu.|
|`CMFCOutlookBarPane::RestoreOriginalstate`|Obnoví původní stav panelu nástrojů. (Přepíše [CMFCToolBar::RestoreOriginalState](../../mfc/reference/cmfctoolbar-class.md#restoreoriginalstate).)|
|[CMFCOutlookBarPane::SetBackColor](#setbackcolor)|Nastaví barvu pozadí.|
|[CMFCOutlookBarPane::SetBackImage](#setbackimage)|Nastaví obrázek na pozadí.|
|[CMFCOutlookBarPane::SetDefaultState](#setdefaultstate)|Podokno panelu Outlook obnovíte původní sadu tlačítek.|
|[CMFCOutlookBarPane::SetExtraSpace](#setextraspace)|Nastaví počet pixelů odsazení použité kolem tlačítka v podokno panelu aplikace Outlook.|
|[CMFCOutlookBarPane::SetTextColor](#settextcolor)|Nastaví barvy textu pravidelné a zvýrazněné v podokno panelu aplikace Outlook.|
|[CMFCOutlookBarPane::SetTransparentColor](#settransparentcolor)|Nastaví průhlednou barvu podokno panelu aplikace Outlook.|
|`CMFCOutlookBarPane::SmartUpdate`|Interně používá k aktualizaci panel aplikace Outlook. (Přepíše `CMFCToolBar::SmartUpdate`.)|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CMFCOutlookBarPane::EnableContextMenuItems](#enablecontextmenuitems)|Určuje, které položky místní nabídky se zobrazí v režimu úprav.|
|[CMFCOutlookBarPane::RemoveAllButtons](#removeallbuttons)|Odebere všechna tlačítka z podokno panelu aplikace Outlook. (Přepíše [CMFCToolBar::RemoveAllButtons](../../mfc/reference/cmfctoolbar-class.md#removeallbuttons).)|

## <a name="remarks"></a>Poznámky

Informace o tom, jak implementovat panel aplikace Outlook, naleznete v tématu [CMFCOutlookBar – třída](../../mfc/reference/cmfcoutlookbar-class.md).

Příklad panel aplikace Outlook naleznete v tématu OutlookDemo ukázkového projektu.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít různé metody `CMFCOutlookBarPane` třídy. Tento příklad ukazuje, jak vytvořit podokno panelu Outlook, povolit rolovací režim stránky, povolit ukotvení a nastavit barvu pozadí panelu aplikace Outlook. Tento fragment kódu je součástí [ukázkové aplikace Outlook s více zobrazení](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_OutlookMultiViews#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_1.h)]
[!code-cpp[NVC_MFC_OutlookMultiViews#4](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxoutlookbarpane.h

##  <a name="addbutton"></a>  CMFCOutlookBarPane::AddButton

Přidá tlačítko do podokno panelu aplikace Outlook.

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
[in] Určuje identifikátor prostředku rastrového obrázku.

*lpszLabel*<br/>
[in] Určuje text tlačítka.

*iIdCommand*<br/>
[in] Určuje ID ovládacího prvku button.

*iInsertAt*<br/>
[in] Určuje index založený na nule, na stránce panelu aplikace outlook, ve kterém se má vložit tlačítka.

*uiLabel*<br/>
[in] Řetězec prostředku.

*szBmpFileName*<br/>
[in] Určuje název souboru bitové kopie disku pro načtení.

*szLabel*<br/>
[in] Určuje text tlačítka.

*hBmp*<br/>
[in] Popisovač rastrového obrázku tlačítka.

*hIcon*<br/>
[in] Popisovač ikony tlačítka.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud byla tlačítka přidána úspěšně; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete vložit nové tlačítko na panelu aplikace Outlook stránku. Obrázek na tlačítko můžete načíst ze zdrojů aplikace nebo ze souboru na disku.

Pokud ID stránky určené *uiPageID* se -1, na tlačítko se vloží do první stránky.

Pokud index zadaný *iInsertAt* se -1, na tlačítko se přidá na konec stránky.

##  <a name="canbeattached"></a>  CMFCOutlookBarPane::CanBeAttached

Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="clearall"></a>  CMFCOutlookBarPane::ClearAll

Uvolní prostředky využívané třídou obrázků na podokno panelu aplikace Outlook.

```
void ClearAll();
```

### <a name="remarks"></a>Poznámky

Tato metoda volá přímo [CMFCToolBarImages::Clear](../../mfc/reference/cmfctoolbarimages-class.md#clear), která je volána v imagích, které jsou používány podokno panelu aplikace Outlook.

##  <a name="create"></a>  CMFCOutlookBarPane::Create

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
[in] Určuje nadřazené okno ovládacího prvku podokno panelu aplikace Outlook. Nesmí mít hodnotu NULL.

*dwStyle*<br/>
[in] Styl okna.  Seznam styly oken najdete v tématu [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*uiID*<br/>
[in] ID ovládacího prvku. Musí být jedinečné pro povolení ukládání stavu ovládacího prvku.

*dwControlBarStyle*<br/>
[in] Určuje zvláštní styly, které definují chování ovládacího prvku podokno panelu Outlook, kdy je odpojena od panel aplikace Outlook.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud metoda byla úspěšná. v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

K vytvoření `CMFCOutlookBarPane` objektu, nejprve volat konstruktor a následně zavolat `Create`, aplikace Outlook panelu ovládacího prvku podokna vytvoří a připojí ho k `CMFCOutlookBarPane` objektu.

Další informace o `dwControlBarStyle` naleznete v tématu [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).

##  <a name="enablecontextmenuitems"></a>  CMFCOutlookBarPane::EnableContextMenuItems

Určuje, které položky místní nabídky se zobrazí v režimu úprav.

```
virtual BOOL EnableContextMenuItems(
    CMFCToolBarButton* pButton,
    CMenu* pPopup);
```

### <a name="parameters"></a>Parametry

*pButton*<br/>
[in] Ukazatel, který uživatel ke kliknutí na tlačítko panelu nástrojů.

*pPopup*<br/>
[in] Ukazatel na místní nabídku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud má být zobrazena v místní nabídce; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu za účelem framework standardní nabídku, která zobrazí rozhraní v režim úprav změnit.

Výchozí implementace kontroluje do režimu úprav ( [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)) a pokud je hodnota TRUE, zakáže všechny místní položky nabídky s výjimkou **odstranit**. Potom stačí předá vstupní parametry `CMFCToolBar::EnableContextMenuItems`.

> [!NOTE]
> *Místní nabídka* je synonymum pro místní nabídky.

##  <a name="enablepagescrollmode"></a>  CMFCOutlookBarPane::EnablePageScrollMode

Určuje, zda šipky na podokno panelu Outlook předem seznam tlačítek stránku po stránce nebo podle tlačítko.

```
void EnablePageScrollMode(BOOL bPageScroll=TRUE);
```

### <a name="parameters"></a>Parametry

*bPageScroll*<br/>
[in] Při hodnotě TRUE povolte rolovací režim stránky. Pokud má hodnotu FALSE, zakažte rolovací režim stránky.

##  <a name="getregularcolor"></a>  CMFCOutlookBarPane::GetRegularColor

Vrací standardní (to znamená, nevybrané) textového barvu podokno panelu aplikace Outlook.

```
DECLARE_MESSAGE_MAPCOLORREF GetRegularColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální barva textu jako hodnota barvy RGB.

### <a name="remarks"></a>Poznámky

Použití [CMFCOutlookBarPane::SetTextColor](#settextcolor) nastavit aktuální barva textu (pravidelné a vybrané) panel aplikace Outlook. Výchozí barva textu lze získat voláním [GetSysColor](/windows/desktop/api/winuser/nf-winuser-getsyscolor) funkce s indexem COLOR_WINDOW.

##  <a name="isbackgroundtexture"></a>  CMFCOutlookBarPane::IsBackgroundTexture

Určuje, jestli je obrázek pozadí pro podokno panelu aplikace Outlook se nenačetly.

```
BOOL IsBackgroundTexture() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je obrázek na pozadí se zobrazí; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Můžete přidat obrázek pozadí voláním [CMFCOutlookBarPane::SetBackImage](#setbackimage) funkce.

Pokud neexistuje žádný obrázek na pozadí, na pozadí vymalovávání barvou určené vlastností [CMFCOutlookBarPane::SetBackColor](#setbackcolor).

##  <a name="isdrawshadedhighlight"></a>  CMFCOutlookBarPane::IsDrawShadedHighlight

Určuje, zda je tlačítko ohraničení označeno šedou barvou při tlačítka se zvýrazní a zobrazí se obrázek na pozadí.

```
BOOL IsDrawShadedHighlight() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud jsou zobrazena šedě; ohraničení tlačítka v opačném případě FALSE.

##  <a name="removeallbuttons"></a>  CMFCOutlookBarPane::RemoveAllButtons

Odebere všechna tlačítka z podokno panelu aplikace Outlook.

```
virtual void RemoveAllButtons();
```

##  <a name="removebutton"></a>  CMFCOutlookBarPane::RemoveButton

Odebere tlačítko, která má ID zadaného příkazu.

```
BOOL RemoveButton(UINT iIdCommand);
```

### <a name="parameters"></a>Parametry

*iIdCommand*<br/>
[in] Určuje Identifikátor příkazu tlačítka odebrat.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud bylo úspěšně odebráno tlačítko; FALSE, pokud zadaný příkaz ID je neplatné.

##  <a name="setbackcolor"></a>  CMFCOutlookBarPane::SetBackColor

Nastaví barvu pozadí panelu aplikace Outlook.

```
void SetBackColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
[in] Určuje novou barvou pozadí.

### <a name="remarks"></a>Poznámky

Voláním této funkce nastavit aktuální barvu pozadí panelu aplikace Outlook. Barva pozadí se používá pouze v případě, že neexistuje žádný obrázek na pozadí.

##  <a name="setbackimage"></a>  CMFCOutlookBarPane::SetBackImage

Nastaví obrázek na pozadí.

```
void SetBackImage(UINT uiImageID);
```

### <a name="parameters"></a>Parametry

*uiImageID*<br/>
[in] Určuje ID bitové kopie prostředku.

### <a name="remarks"></a>Poznámky

Voláním této metody lze nastavit v Outlooku obrázek pozadí panelu. Seznam obrázků na pozadí se spravuje pomocí vložený [cmfctoolbarimages – třída](../../mfc/reference/cmfctoolbarimages-class.md) objektu.

##  <a name="setdefaultstate"></a>  CMFCOutlookBarPane::SetDefaultState

Podokno panelu Outlook obnovíte původní sadu tlačítek.

```
void SetDefaultState();
```

### <a name="remarks"></a>Poznámky

Tato metoda obnoví původní sadu tlačítek na panelu aplikace Outlook. Tato metoda je jako `CMFCOutlookBarPane::RestoreOriginalstate`, s tím rozdílem, že neaktivuje překreslování podokno panelu aplikace Outlook.

##  <a name="setextraspace"></a>  CMFCOutlookBarPane::SetExtraSpace

Nastaví počet pixelů odsazení použité kolem tlačítka v podokno panelu aplikace Outlook.

```
void SetExtraSpace()
```

##  <a name="settextcolor"></a>  CMFCOutlookBarPane::SetTextColor

Nastaví barvy textu pravidelné a zvýrazněné v podokno panelu aplikace Outlook.

```
void SetTextColor(
    COLORREF clrRegText,
    COLORREF clrSelText=0);
```

### <a name="parameters"></a>Parametry

*clrRegText*<br/>
[in] Určuje barvu nové-vybraný text.

*clrSelText*<br/>
[in] Určuje novou barvu pro vybraný text.

##  <a name="settransparentcolor"></a>  CMFCOutlookBarPane::SetTransparentColor

Nastaví průhlednou barvu podokno panelu aplikace Outlook.

```
void SetTransparentColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
Určuje průhlednou barvu nové.

### <a name="remarks"></a>Poznámky

Průhledná barva je vyžadována k zobrazení průhledné obrázky. Jakýmkoli výskytem tuto barvu v obrázku se barvou pozadí vymalovávání místo.  Neexistuje žádné prolnutí imagí na pozadí a popředí.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCOutlookBar – třída](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CMFCOutlookBarTabCtrl – třída](../../mfc/reference/cmfcoutlookbartabctrl-class.md)
