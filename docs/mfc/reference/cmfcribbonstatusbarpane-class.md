---
title: CMFCRibbonStatusBarPane Class
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::GetAlmostLargeText
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::GetTextAlign
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::IsAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::IsExtended
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnDrawBorder
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnFillBackground
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetAlmostLargeText
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetAnimationList
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetTextAlign
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::StartAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::StopAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnFinishAnimation
helpviewer_keywords:
- CMFCRibbonStatusBarPane [MFC], CMFCRibbonStatusBarPane
- CMFCRibbonStatusBarPane [MFC], GetAlmostLargeText
- CMFCRibbonStatusBarPane [MFC], GetTextAlign
- CMFCRibbonStatusBarPane [MFC], IsAnimation
- CMFCRibbonStatusBarPane [MFC], IsExtended
- CMFCRibbonStatusBarPane [MFC], OnDrawBorder
- CMFCRibbonStatusBarPane [MFC], OnFillBackground
- CMFCRibbonStatusBarPane [MFC], SetAlmostLargeText
- CMFCRibbonStatusBarPane [MFC], SetAnimationList
- CMFCRibbonStatusBarPane [MFC], SetTextAlign
- CMFCRibbonStatusBarPane [MFC], StartAnimation
- CMFCRibbonStatusBarPane [MFC], StopAnimation
- CMFCRibbonStatusBarPane [MFC], OnFinishAnimation
ms.assetid: 5d034c3c-ecca-4267-b88c-0f55a2884dd0
ms.openlocfilehash: 9911672ec139ab1598db8005e9b7b909e85dd33d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265727"
---
# <a name="cmfcribbonstatusbarpane-class"></a>CMFCRibbonStatusBarPane Class

`CMFCRibbonStatusBarPane` Třída implementuje prvek pásu karet, který lze přidat na stavový panel pásu karet.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonStatusBarPane : public CMFCRibbonButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane](#cmfcribbonstatusbarpane)|Vytvoří a inicializuje `CMFCRibbonStatusBarPane` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCRibbonStatusBarPane::GetAlmostLargeText](#getalmostlargetext)|Vrátí řetězec, který definuje nejdelší textový řetězec, který lze zobrazit v podokně bez zkrácení.|
|[CMFCRibbonStatusBarPane::GetTextAlign](#gettextalign)|Vrátí aktuální nastavení zarovnání textu.|
|[CMFCRibbonStatusBarPane::IsAnimation](#isanimation)|Určuje, zda je animace v průběhu.|
|[CMFCRibbonStatusBarPane::IsExtended](#isextended)|Určuje, zda v podokně se nachází v oblasti rozšířené stavový panel pásu karet.|
|[CMFCRibbonStatusBarPane::OnDrawBorder](#ondrawborder)|(Přepíše [CMFCRibbonButton::OnDrawBorder](../../mfc/reference/cmfcribbonbutton-class.md#ondrawborder).)|
|[CMFCRibbonStatusBarPane::OnFillBackground](#onfillbackground)|(Přepíše [CMFCRibbonButton::OnFillBackground](../../mfc/reference/cmfcribbonbutton-class.md#onfillbackground).)|
|[CMFCRibbonStatusBarPane::SetAlmostLargeText](#setalmostlargetext)|Definuje nejdelší textový řetězec, který lze zobrazit v podokně bez zkrácení.|
|[CMFCRibbonStatusBarPane::SetAnimationList](#setanimationlist)|Přiřadí v podokně seznamu obrázků, které lze použít pro animaci.|
|[CMFCRibbonStatusBarPane::SetTextAlign](#settextalign)|Nastaví zarovnání textu.|
|[CMFCRibbonStatusBarPane::StartAnimation](#startanimation)|Spuštění animace, který je přiřazen do podokna.|
|[CMFCRibbonStatusBarPane::StopAnimation](#stopanimation)|Zastaví animace, který je přiřazen do podokna. .|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CMFCRibbonStatusBarPane::OnFinishAnimation](#onfinishanimation)|Volá se rozhraním, když se zastaví animace, který je přiřazen do podokna.|

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít různé metody v `CMFCRibbonStatusBarPane` třídy. Tento příklad ukazuje, jak vytvořit `CMFCRibbonStatusBarPane` objektu, nastavení zarovnání textu popisku panelu stavového řádku stav, definujte nejdelší text, který lze zobrazit v podokně Stav panelu nezkrácený, připojit k podokno panelu Stav, který lze použít pro seznam obrázků nalizaci a spuštění animace.

[!code-cpp[NVC_MFC_RibbonApp#2](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbarpane-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cmfcribbonbaseelement –](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonStatusBarPane](../../mfc/reference/cmfcribbonstatusbarpane-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxribbonstatusbarpane.h

##  <a name="cmfcribbonstatusbarpane"></a>  CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane

Vytvoření objektu podokně ve stavovém řádku.

```
CMFCRibbonStatusBarPane(
    UINT nCmdID,
    LPCTSTR lpszText,
    BOOL bIsStatic=FALSE,
    HICON hIcon=NULL,
    LPCTSTR lpszAlmostLargeText=NULL);

CMFCRibbonStatusBarPane(
    UINT nCmdID,
    LPCTSTR lpszText,
    HBITMAP hBmpAnimationList,
    int cxAnimation=16,
    COLORREF clrTrnsp=RGB(192,192 1,192) 1,
    HICON hIcon=NULL,
    BOOL bIsStatic=FALSE);

CMFCRibbonStatusBarPane(
    UINT nCmdID,
    LPCTSTR lpszText,
    UINT uiAnimationListResID,
    int cxAnimation=16,
    COLORREF clrTrnsp=RGB(192, 192 1, 192) 1,
    HICON hIcon=NULL,
    BOOL bIsStatic=FALSE);
```

### <a name="parameters"></a>Parametry

*nCmdID*<br/>
[in] Určuje ID příkazového podokna.

*lpszText*<br/>
[in] Určuje textový řetězec, který se má zobrazit v podokně.

*bIsStatic*<br/>
[in] Při hodnotě TRUE nelze podokně Stav zvýrazněny nebo vybrat kliknutím ji.

*hIcon*<br/>
[in] Určuje ikonu, která se zobrazí v podokně popisovač.

*lpszAlmostLargeText*<br/>
[in] Určuje nejdelší textový řetězec, který lze zobrazit v podokně.

*hBmpAnimationList*<br/>
[in] Určuje popisovač, který se používá pro animaci seznamu obrázků.

*cxAnimation*<br/>
[in] Určuje šířku v pixelech, ikony v seznamu obrázků, který se používá pro animaci.

*clrTrnsp*<br/>
[in] Určuje průhlednou barvu imagí v seznamu obrázků, které se používají pro animaci.

*uiAnimationListResID*<br/>
[in] Určuje Identifikátor prostředku, který se používá pro animaci seznamu obrázků.

##  <a name="getalmostlargetext"></a>  CMFCRibbonStatusBarPane::GetAlmostLargeText

Načte nejdelší textový řetězec, který může zobrazit panelu stavového řádku stav.

```
LPCTSTR GetAlmostLargeText() const;
```

### <a name="return-value"></a>Návratová hodnota

Nejdelší textový řetězec, který lze zobrazit panelu stavového řádku stav.

##  <a name="gettextalign"></a>  CMFCRibbonStatusBarPane::GetTextAlign

Získá aktuální nastavení zarovnání textu popisku panelu stavového řádku stav.

```
int GetTextAlign() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální zarovnání textu, který může být jedna z následujících akcí:

- TA_LEFT

- TA_CENTER

- TA_RIGHT.

##  <a name="isanimation"></a>  CMFCRibbonStatusBarPane::IsAnimation

Určuje, zda je animace v průběhu.

```
BOOL IsAnimation() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je animace v průběhu; FALSE v opačném případě.

##  <a name="isextended"></a>  CMFCRibbonStatusBarPane::IsExtended

Určení, zda v podokně se nachází v oblasti rozšířené stavový panel pásu karet.

```
BOOL IsExtended() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je podokno na stavovém řádku rozšířené oblasti. FALSE v opačném případě.

##  <a name="ondrawborder"></a>  CMFCRibbonStatusBarPane::OnDrawBorder

Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.

```
virtual void OnDrawBorder(CDC*);
```

### <a name="parameters"></a>Parametry

[in] *CDC&#42;*<br/>

### <a name="remarks"></a>Poznámky

##  <a name="onfillbackground"></a>  CMFCRibbonStatusBarPane::OnFillBackground

Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.

```
virtual COLORREF OnFillBackground(CDC* pDC);
```

### <a name="parameters"></a>Parametry

[in] *pDC*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="onfinishanimation"></a>  CMFCRibbonStatusBarPane::OnFinishAnimation

Rozhraní volá tuto metodu při ukončení animace, který je přiřazen do podokna.

```
virtual void OnFinishAnimation();
```

### <a name="remarks"></a>Poznámky

`StopAnimation` volání metody `OnFinishAnimation` metodu, která slouží k vyčištění dat při ukončení animace.

##  <a name="setalmostlargetext"></a>  CMFCRibbonStatusBarPane::SetAlmostLargeText

Definujte nejdelší text, který lze zobrazit v podokně Stav panelu bez zkrácení.

```
void SetAlmostLargeText(LPCTSTR lpszAlmostLargeText);
```

### <a name="parameters"></a>Parametry

*lpszAlmostLargeText*<br/>
[in] Určuje nejdelší řetězec, který lze zobrazit na panelu stavového stav bez zkrácení.

### <a name="remarks"></a>Poznámky

Knihovny vypočítá velikost textu, který *lpszAlmostLargeText* určuje a změní velikost panelu odpovídajícím způsobem. Text bude zkrácen, pokud ho stále nevejde do podokna.

##  <a name="setanimationlist"></a>  CMFCRibbonStatusBarPane::SetAnimationList

Připojí se k podokno panelu Stav, který lze použít pro animaci seznamu obrázků.

```
void SetAnimationList(
    HBITMAP hBmpAnimationList,
    int cxAnimation=16,
    COLORREF clrTransp=RGB(192, 192 1, 192) 1);

BOOL SetAnimationList(
    UINT uiAnimationListResID,
    int cxAnimation=16,
    COLORREF clrTransp=RGB(192, 192 1, 192) 1);
```

### <a name="parameters"></a>Parametry

*hBmpAnimationList*<br/>
[in] Určuje popisovač seznamu obrázků.

*cxAnimation*<br/>
[in] Určuje šířku v pixelech, rámce v seznamu obrázků.

*clrTransp*<br/>
[in] Určuje průhlednou barvu ze seznamu obrázků.

*uiAnimationListResID*<br/>
[in] Určuje ID prostředku ze seznamu obrázků.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud seznam obrázků se úspěšně připojil k panelu stavového řádku stav; FALSE v opačném případě.

##  <a name="settextalign"></a>  CMFCRibbonStatusBarPane::SetTextAlign

Nastaví zarovnání textu popisku panelu stavového řádku stav.

```
void SetTextAlign(int nAlign);
```

### <a name="parameters"></a>Parametry

*nAlign*<br/>
[in] Určuje zarovnání textu.

### <a name="remarks"></a>Poznámky

*nAlign* může mít jednu z následujících hodnot:

- TA_LEFT: zarovnání doleva

- TA_CENTER: zarovnání na střed

- TA_RIGHT: zarovnání doprava

##  <a name="startanimation"></a>  CMFCRibbonStatusBarPane::StartAnimation

Spuštění animace, která přiřadíte do podokna.

```
void StartAnimation(
    UINT nFrameDelay=500,
    UINT nDuration=-1);
```

### <a name="parameters"></a>Parametry

*nFrameDelay*<br/>
[in] Určuje frekvenci snímků animace v milisekundách.

*nDuration*<br/>
[in] Určuje, jak dlouho přehrávání animace, v milisekundách. Použijte hodnotu -1 pro nekonečnou smyčku.

### <a name="remarks"></a>Poznámky

Před voláním, je nutné zadat popisovač seznamu obrázků `StartAnimation` pomocí `SetAnimationList`.

##  <a name="stopanimation"></a>  CMFCRibbonStatusBarPane::StopAnimation

Zastaví animace, který jste přiřadili do podokna stav řádku.

```
void StopAnimation();
```

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton – třída](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[CMFCRibbonStatusBar – třída](../../mfc/reference/cmfcribbonstatusbar-class.md)
