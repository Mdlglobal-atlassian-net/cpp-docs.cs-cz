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
ms.openlocfilehash: 97c7edde26bdf13e899d823dcf88d143068d86a4
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749605"
---
# <a name="cmfcoutlookbarpane-class"></a>CMFCOutlookBarPane – třída

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

Ovládací prvek odvozený z [třídy CMFCToolBar,](../../mfc/reference/cmfctoolbar-class.md) který lze vložit do panelu aplikace Outlook [(třída CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)). Podokno panelu aplikace Outlook obsahuje sloupec velkých tlačítek. Uživatel může posouvat nahoru a dolů seznam tlačítek, pokud je větší než podokno. Když uživatel odpojí podokno panelu aplikace Outlook od panelu aplikace Outlook, může se uvolnit nebo ukotvit v okně hlavního rámce.

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
|[CMFCOutlookBarpane::Tlačítko AddButton](#addbutton)|Přidá tlačítko do podokna panelu aplikace Outlook.|
|[CMFCOutlookBarPane::CanBeAttached](#canbeattached)|Určuje, zda lze podokno ukotvit do jiného podokna nebo okna rámce. (Přepíše [CBasePane::CanBeAttached](../../mfc/reference/cbasepane-class.md#canbeattached).)|
|`CMFCOutlookBarPane::CanBeRestored`|Určuje, zda může systém po vlastním nastavení obnovit původní stav panelu nástrojů. (Přepíše [CMFCToolBar::CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored).)|
|[CMFCOutlookBarPane::Clearall](#clearall)|Uvolní prostředky používané obrázky v podokně panelu aplikace Outlook.|
|[CMFCOutlookBarPane::Vytvořit](#create)|Vytvoří podokno panelu panelu aplikace Outlook.|
|`CMFCOutlookBarPane::CreateObject`|Používá rámci k vytvoření dynamické instance tohoto typu třídy.|
|`CMFCOutlookBarPane::Dock`|Volat rámci ukotvit podokno panelu aplikace Outlook. (Přepíše `CPane::Dock`.)|
|[CMFCOutlookBarPane::EnablePageScrollMode](#enablepagescrollmode)|Určuje, zda šipky posuvníku v podokně panelu aplikace Outlook posunují seznam tlačítek podle stránky nebo tlačítka.|
|[CMFCOutlookBarpane::GetRegularColor](#getregularcolor)|Vrátí normální (nevybranou) barvu textu podokna panelu panelu aplikace Outlook.|
|`CMFCOutlookBarPane::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objektu, který je přidružen k tomuto typu třídy.|
|[CMFCOutlookBarPane::isBackgroundTexture](#isbackgroundtexture)|Určuje, zda je pro podokno panelu panelu aplikace Outlook načten obrázek pozadí.|
|`CMFCOutlookBarPane::IsChangeState`|Určuje, zda plovoucí podokno může být ukotven. (Přepíše `CPane::IsChangeState`.)|
|[CMFCOutlookBarPane::IsDrawShadedHighlight](#isdrawshadedhighlight)|Určuje, zda je ohraničení tlačítka stínované, když je tlačítko zvýrazněno a zobrazí se obrázek pozadí.|
|`CMFCOutlookBarPane::OnBeforeFloat`|Volat rámci při podokně se chystá float. (Přepíše [CPane::OnBeforeFloat](../../mfc/reference/cpane-class.md#onbeforefloat).)|
|[CMFCOutlookBarPane::tlačítko RemoveButton](#removebutton)|Odebere tlačítko, které má zadané ID příkazu.|
|`CMFCOutlookBarPane::RestoreOriginalstate`|Obnoví původní stav panelu nástrojů. (Přepíše [CMFCToolBar::RestoreOriginalState](../../mfc/reference/cmfctoolbar-class.md#restoreoriginalstate).)|
|[CMFCOutlookBarpane::Setbackcolor](#setbackcolor)|Nastaví barvu pozadí.|
|[CMFCOutlookBarpane::SetbackImage](#setbackimage)|Nastaví obrázek pozadí.|
|[CMFCOutlookBarPane::Nastavit výchozí stav](#setdefaultstate)|Obnoví podokno panelu panelu aplikace Outlook na původní sadu tlačítek.|
|[CMFCOutlookBarpane::SetExtraSpace](#setextraspace)|Nastaví počet obrazových bodů odsazení použitých kolem tlačítek v podokně panelu aplikace Outlook.|
|[CMFCOutlookBarpane::SetTextColor](#settextcolor)|Nastaví barvy běžného a zvýrazněného textu v podokně panelu aplikace Outlook.|
|[CMFCOutlookBarpane::SetTransparentColor](#settransparentcolor)|Nastaví průhlednou barvu panelového podokna aplikace Outlook.|
|`CMFCOutlookBarPane::SmartUpdate`|Interně se používá k aktualizaci panelu aplikace Outlook. (Přepíše `CMFCToolBar::SmartUpdate`.)|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CMFCOutlookBarPane::EnableContextMenuItems](#enablecontextmenuitems)|Určuje, které položky místní nabídky budou zobrazeny v režimu vlastního nastavení.|
|[CMFCOutlookBarPane::RemoveAllButtons](#removeallbuttons)|Odebere všechna tlačítka z podokna panelu aplikace Outlook. (Přepíše [CMFCToolBar::RemoveAllButtons](../../mfc/reference/cmfctoolbar-class.md#removeallbuttons).)|

## <a name="remarks"></a>Poznámky

Informace o implementaci panelu aplikace Outlook naleznete v [tématu CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md).

Příklad panelu aplikace Outlook naleznete v ukázkovém projektu Aplikace OutlookDemo.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat různé `CMFCOutlookBarPane` metody třídy. Příklad ukazuje, jak vytvořit podokno panelu panelu aplikace Outlook, povolit režim posouvání stránky, povolit ukotvení a nastavit barvu pozadí panelu aplikace Outlook. Tento fragment kódu je součástí [ukázky více zobrazení aplikace Outlook](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_OutlookMultiViews#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_1.h)]
[!code-cpp[NVC_MFC_OutlookMultiViews#4](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCPanel](../../mfc/reference/cmfctoolbar-class.md)

[CMFCOutlookBarpane](../../mfc/reference/cmfcoutlookbarpane-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxoutlookbarpane.h

## <a name="cmfcoutlookbarpaneaddbutton"></a><a name="addbutton"></a>CMFCOutlookBarpane::Tlačítko AddButton

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
[v] Určuje identifikátor prostředku bitmapy.

*popisek lpsz*<br/>
[v] Určuje text tlačítka.

*iIdCommand*<br/>
[v] Určuje ID ovládacího prvku tlačítka.

*iInsertAt*<br/>
[v] Určuje nulový index na stránce panelu aplikace Outlook, na kterou chcete tlačítko vložit.

*uiLabel*<br/>
[v] ID řetězce prostředku.

*szBmpNázev souboru*<br/>
[v] Určuje název načtení souboru bitové kopie disku.

*szLabel*<br/>
[v] Určuje text tlačítka.

*hBmp*<br/>
[v] Úchyt k bitmapě tlačítka.

*hIkona*<br/>
[v] Úchyt k ikoně tlačítek.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud bylo tlačítko přidáno úspěšně; jinak FALSE.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete vložit nové tlačítko na stránku panelu aplikace Outlook. Bitovou kopii tlačítka lze načíst buď z prostředků aplikace, nebo ze souboru disku.

Pokud je ID stránky určené *uiPageID* -1, tlačítko se vloží na první stránku.

Pokud je index určený *iInsertAt* -1, tlačítko je přidán na konec stránky.

## <a name="cmfcoutlookbarpanecanbeattached"></a><a name="canbeattached"></a>CMFCOutlookBarPane::CanBeAttached

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcoutlookbarpaneclearall"></a><a name="clearall"></a>CMFCOutlookBarPane::Clearall

Uvolní prostředky používané obrázky v podokně panelu aplikace Outlook.

```cpp
void ClearAll();
```

### <a name="remarks"></a>Poznámky

Tato metoda přímo volá [CMFCToolBarImages::Clear](../../mfc/reference/cmfctoolbarimages-class.md#clear), který je volán na obrázky, které jsou používány podokno panelu aplikace Outlook.

## <a name="cmfcoutlookbarpanecreate"></a><a name="create"></a>CMFCOutlookBarPane::Vytvořit

Vytvoří podokno panelu panelu aplikace Outlook.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle=AFX_DEFAULT_TOOLBAR_STYLE,
    UINT uiID=(UINT)-1,
    DWORD dwControlBarStyle=0);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
[v] Určuje nadřazené okno ovládacího prvku panelu panelu aplikace Outlook. Nesmí být null.

*dwStyl*<br/>
[v] Styl okna.  Seznam stylů oken naleznete v tématu [Styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*uiID*<br/>
[v] ID ovládacího prvku. Musí být jedinečný, aby bylo možné uložit stav ovládacího prvku.

*dwControlBarStyle*<br/>
[v] Určuje speciální styly, které definují chování ovládacího prvku panelu panelu aplikace Outlook, když je odpojen od panelu aplikace Outlook.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byla metoda úspěšná; jinak FALSE.

### <a name="remarks"></a>Poznámky

Chcete-li `CMFCOutlookBarPane` vytvořit objekt, nejprve zavolejte `Create`konstruktor a potom volání , který `CMFCOutlookBarPane` vytvoří ovládací prvek panelového podokna aplikace Outlook a připojí jej k objektu.

Další informace `dwControlBarStyle` o [cbasepane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).

## <a name="cmfcoutlookbarpaneenablecontextmenuitems"></a><a name="enablecontextmenuitems"></a>CMFCOutlookBarPane::EnableContextMenuItems

Určuje, které položky místní nabídky budou zobrazeny v režimu vlastního nastavení.

```
virtual BOOL EnableContextMenuItems(
    CMFCToolBarButton* pButton,
    CMenu* pPopup);
```

### <a name="parameters"></a>Parametry

*pTlačítko*<br/>
[v] Ukazatel na tlačítko panelu nástrojů, na které uživatel klepnul.

*pPopup*<br/>
[v] Ukazatel na místní nabídku.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud má být zobrazena místní nabídka; jinak FALSE.

### <a name="remarks"></a>Poznámky

Přepište tuto metodu a upravte standardní místní nabídku architektury, která se v režimu vlastního nastavení zobrazí v rámci.

Výchozí implementace zkontroluje režim přizpůsobení [(CMFCToolBar::IsCustomizeMode)](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)a pokud je nastavena na hodnotu TRUE, zakáže všechny položky místní nabídky kromě **odstranění**. Pak to jen předá vstupní `CMFCToolBar::EnableContextMenuItems`parametry .

> [!NOTE]
> *Místní nabídka* je synonymem pro místní nabídku.

## <a name="cmfcoutlookbarpaneenablepagescrollmode"></a><a name="enablepagescrollmode"></a>CMFCOutlookBarPane::EnablePageScrollMode

Určuje, zda šipky posuvníku v podokně panelu aplikace Outlook posunují seznam tlačítek po stránce nebo tlačítka po tlačítku.

```cpp
void EnablePageScrollMode(BOOL bPageScroll=TRUE);
```

### <a name="parameters"></a>Parametry

*bPageScroll*<br/>
[v] Pokud je true, povolte režim posouvání stránky. Pokud se nezobrazuje, zakažte režim posouvání stránky.

## <a name="cmfcoutlookbarpanegetregularcolor"></a><a name="getregularcolor"></a>CMFCOutlookBarpane::GetRegularColor

Vrátí normální (tj. nevybranou) barvu textu podokna panelu panelu aplikace Outlook.

```
DECLARE_MESSAGE_MAPCOLORREF GetRegularColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální barva textu jako hodnota barvy RGB.

### <a name="remarks"></a>Poznámky

Použití [CMFCOutlookBarPane::SetTextColor](#settextcolor) k nastavení aktuální (normální a vybrané) barvy textu panelu aplikace Outlook. Výchozí barvu textu můžete získat voláním funkce [GetSysColor](/windows/win32/api/winuser/nf-winuser-getsyscolor) s COLOR_WINDOW indexem.

## <a name="cmfcoutlookbarpaneisbackgroundtexture"></a><a name="isbackgroundtexture"></a>CMFCOutlookBarPane::isBackgroundTexture

Určuje, zda je pro podokno panelu panelu aplikace Outlook načten obrázek pozadí.

```
BOOL IsBackgroundTexture() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je obrázek na pozadí k zobrazení; jinak FALSE.

### <a name="remarks"></a>Poznámky

Obrázek pozadí můžete přidat voláním funkce [CMFCOutlookBarPane::SetBackImage.](#setbackimage)

Pokud není k dispozici žádný obrázek pozadí, je pozadí vybarveno barvou určenou pomocí [cmfcoutlookbarpane::SetBackColor](#setbackcolor).

## <a name="cmfcoutlookbarpaneisdrawshadedhighlight"></a><a name="isdrawshadedhighlight"></a>CMFCOutlookBarPane::IsDrawShadedHighlight

Určuje, zda je ohraničení tlačítka stínované, když je tlačítko zvýrazněno a zobrazí se obrázek pozadí.

```
BOOL IsDrawShadedHighlight() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud jsou ohraničení tlačítka stínována; jinak FALSE.

## <a name="cmfcoutlookbarpaneremoveallbuttons"></a><a name="removeallbuttons"></a>CMFCOutlookBarPane::RemoveAllButtons

Odebere všechna tlačítka z podokna panelu aplikace Outlook.

```
virtual void RemoveAllButtons();
```

## <a name="cmfcoutlookbarpaneremovebutton"></a><a name="removebutton"></a>CMFCOutlookBarPane::tlačítko RemoveButton

Odebere tlačítko, které má zadané ID příkazu.

```
BOOL RemoveButton(UINT iIdCommand);
```

### <a name="parameters"></a>Parametry

*iIdCommand*<br/>
[v] Určuje ID příkazu tlačítka, které chcete odebrat.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud bylo tlačítko úspěšně odebráno; FALSE, pokud zadané ID příkazu není platné.

## <a name="cmfcoutlookbarpanesetbackcolor"></a><a name="setbackcolor"></a>CMFCOutlookBarpane::Setbackcolor

Nastaví barvu pozadí panelu aplikace Outlook.

```cpp
void SetBackColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
[v] Určuje novou barvu pozadí.

### <a name="remarks"></a>Poznámky

Voláním této funkce nastavte aktuální barvu pozadí pro panel aplikace Outlook. Barva pozadí se používá pouze v případě, že není k dispozici žádný obrázek pozadí.

## <a name="cmfcoutlookbarpanesetbackimage"></a><a name="setbackimage"></a>CMFCOutlookBarpane::SetbackImage

Nastaví obrázek pozadí.

```cpp
void SetBackImage(UINT uiImageID);
```

### <a name="parameters"></a>Parametry

*uiImageID*<br/>
[v] Určuje ID prostředku obrázku.

### <a name="remarks"></a>Poznámky

Voláním této metody nastavte obrázek pozadí panelu aplikace Outlook. Seznam obrázků na pozadí je spravován vloženým objektem [třídy CMFCToolBarImages.](../../mfc/reference/cmfctoolbarimages-class.md)

## <a name="cmfcoutlookbarpanesetdefaultstate"></a><a name="setdefaultstate"></a>CMFCOutlookBarPane::Nastavit výchozí stav

Obnoví podokno panelu panelu aplikace Outlook na původní sadu tlačítek.

```cpp
void SetDefaultState();
```

### <a name="remarks"></a>Poznámky

Tato metoda obnoví tlačítka panelu aplikace Outlook na původní sadu. Tato metoda `CMFCOutlookBarPane::RestoreOriginalstate`je jako , s tím rozdílem, že neaktivuje překreslení podokna panelu aplikace Outlook.

## <a name="cmfcoutlookbarpanesetextraspace"></a><a name="setextraspace"></a>CMFCOutlookBarpane::SetExtraSpace

Nastaví počet obrazových bodů odsazení použitých kolem tlačítek v podokně panelu aplikace Outlook.

```cpp
void SetExtraSpace()
```

## <a name="cmfcoutlookbarpanesettextcolor"></a><a name="settextcolor"></a>CMFCOutlookBarpane::SetTextColor

Nastaví barvy běžného a zvýrazněného textu v podokně panelu aplikace Outlook.

```cpp
void SetTextColor(
    COLORREF clrRegText,
    COLORREF clrSelText=0);
```

### <a name="parameters"></a>Parametry

*clrRegText*<br/>
[v] Určuje novou barvu pro nevybraný text.

*clrSelText*<br/>
[v] Určuje novou barvu pro vybraný text.

## <a name="cmfcoutlookbarpanesettransparentcolor"></a><a name="settransparentcolor"></a>CMFCOutlookBarpane::SetTransparentColor

Nastaví průhlednou barvu panelového podokna aplikace Outlook.

```cpp
void SetTransparentColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
Určuje novou průhlednou barvu.

### <a name="remarks"></a>Poznámky

Průhledná barva je vyžadována pro zobrazení průhledných obrazů. Jakýkoli výskyt této barvy v obraze je namalován barvou pozadí.  Neexistuje žádné prolnutí obrázků pozadí a popředí.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCOutlookBar – třída](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[Třída CMFCOutlookBarTabctrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md)
