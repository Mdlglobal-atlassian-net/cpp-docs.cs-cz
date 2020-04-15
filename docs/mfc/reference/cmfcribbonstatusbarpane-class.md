---
title: Třída CMFCRibbonStatusBarPane
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
ms.openlocfilehash: 554b9fe364c6a213e038416a605c17cdd4f8e7d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368799"
---
# <a name="cmfcribbonstatusbarpane-class"></a>Třída CMFCRibbonStatusBarPane

Třída `CMFCRibbonStatusBarPane` implementuje prvek pásu karet, který můžete přidat na stavový řádek pásu karet.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonStatusBarPane : public CMFCRibbonButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCRibbonRibbonStatusBarPane::CMFCRibbonStatusBarPane](#cmfcribbonstatusbarpane)|Vytvoří a inicializuje `CMFCRibbonStatusBarPane` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCRibbonRibbonStatusBarPane::GetAlmostLargeText](#getalmostlargetext)|Vrátí řetězec, který definuje nejdelší textový řetězec, který lze zobrazit v podokně bez zkrácení.|
|[CMFCRibbonStatusBarPane::GetTextAlign](#gettextalign)|Vrátí aktuální nastavení zarovnání textu.|
|[CMFCRibbonRibbonStatusBarPane::IsAnimation](#isanimation)|Určuje, zda animace probíhá.|
|[CMFCRibbonRibbonStatusBarPane::IsExtended](#isextended)|Určuje, zda je podokno umístěno v rozšířené oblasti stavového řádku pásu karet.|
|[CMFCRibbonStatusBarPane::OnDrawBorder](#ondrawborder)|(Přepíše [CMFCRibbonButton::OnDrawBorder](../../mfc/reference/cmfcribbonbutton-class.md#ondrawborder).)|
|[CMFCRibbonRibbonStatusBarPane::OnFillBackground](#onfillbackground)|(Přepíše [CMFCRibbonButton::OnFillBackground](../../mfc/reference/cmfcribbonbutton-class.md#onfillbackground).)|
|[CMFCRibbonRibbonStatusBarPane::SetAlmostLargeText](#setalmostlargetext)|Definuje nejdelší textový řetězec, který lze zobrazit v podokně bez zkrácení.|
|[CMFCRibbonRibbonStatusBarPane::SetanimationList](#setanimationlist)|Přiřadí podokně seznam obrázků, který lze použít pro animaci.|
|[CMFCRibbonStatusBarPane::SetTextAlign](#settextalign)|Nastaví zarovnání textu.|
|[CMFCRibbonStatusBarPane::StartAnimation](#startanimation)|Spustí animaci přiřazenou podoknu.|
|[CMFCRibbonRibbonStatusBarPane::StopAnimation](#stopanimation)|Zastaví animaci přiřazenou podoknu. .|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCRibbonRibbonStatusBarPane::OnFinishAnimation](#onfinishanimation)|Volat rámci při zastaví animace, která je přiřazena k podokně.|

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat různé `CMFCRibbonStatusBarPane` metody ve třídě. Příklad ukazuje, jak `CMFCRibbonStatusBarPane` vytvořit objekt, nastavit zarovnání textu popisku podokna stavového řádku, definovat nejdelší text, který lze zobrazit v podokně stavového řádku bez zkrácení, připojit k podokně stavového řádku seznam obrázků, který lze použít pro animaci, a spustit animaci.

[!code-cpp[NVC_MFC_RibbonApp#2](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbarpane-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CMFC4RibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CmFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonPanelpanel](../../mfc/reference/cmfcribbonstatusbarpane-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxribbonstatusbarpane.h

## <a name="cmfcribbonstatusbarpanecmfcribbonstatusbarpane"></a><a name="cmfcribbonstatusbarpane"></a>CMFCRibbonRibbonStatusBarPane::CMFCRibbonStatusBarPane

Vytvořte objekt podokna na stavovém řádku.

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
[v] Určuje ID příkazu podokna.

*lpszText*<br/>
[v] Určuje textový řetězec, který se má zobrazit v podokně.

*bIsStatic*<br/>
[v] Pokud je hodnota PRAVDA, nelze podokno stavu zvýraznit nebo vybrat klepnutím na něj.

*hIkona*<br/>
[v] Určuje úchyt k ikoně, která má být zobrazena v podokně.

*lpszTéměřLargeText*<br/>
[v] Určuje nejdelší textový řetězec, který může podokno zobrazit.

*hBmpAnimationList*<br/>
[v] Určuje popisovač seznamu obrázků, který se používá pro animaci.

*cxAnimace*<br/>
[v] Určuje šířku ikony v seznamu obrázků, která se používá pro animaci, v obrazových bodech.

*clrTrnsp*<br/>
[v] Určuje průhlednou barvu obrazů v seznamu obrázků, které se používají pro animaci.

*uiAnimationListResID*<br/>
[v] Určuje ID prostředku seznamu obrázků, který se používá pro animaci.

## <a name="cmfcribbonstatusbarpanegetalmostlargetext"></a><a name="getalmostlargetext"></a>CMFCRibbonRibbonStatusBarPane::GetAlmostLargeText

Získá nejdelší textový řetězec, který může zobrazit podokno stavového řádku.

```
LPCTSTR GetAlmostLargeText() const;
```

### <a name="return-value"></a>Návratová hodnota

Nejdelší textový řetězec, který může podokno stavového řádku zobrazit.

## <a name="cmfcribbonstatusbarpanegettextalign"></a><a name="gettextalign"></a>CMFCRibbonStatusBarPane::GetTextAlign

Získá aktuální nastavení zarovnání textu popisku podokna stavového řádku.

```
int GetTextAlign() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální zarovnání textu, které může být jedním z následujících:

- TA_LEFT

- TA_CENTER

- TA_RIGHT.

## <a name="cmfcribbonstatusbarpaneisanimation"></a><a name="isanimation"></a>CMFCRibbonRibbonStatusBarPane::IsAnimation

Určuje, zda animace probíhá.

```
BOOL IsAnimation() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud probíhá animace; FALSE jinak.

## <a name="cmfcribbonstatusbarpaneisextended"></a><a name="isextended"></a>CMFCRibbonRibbonStatusBarPane::IsExtended

Určete, zda je podokno umístěno v rozšířené oblasti stavového řádku pásu karet.

```
BOOL IsExtended() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je podokno na rozšířené oblasti stavového řádku. FALSE jinak.

## <a name="cmfcribbonstatusbarpaneondrawborder"></a><a name="ondrawborder"></a>CMFCRibbonStatusBarPane::OnDrawBorder

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

```
virtual void OnDrawBorder(CDC*);
```

### <a name="parameters"></a>Parametry

[v] *CDC&#42;*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonstatusbarpaneonfillbackground"></a><a name="onfillbackground"></a>CMFCRibbonRibbonStatusBarPane::OnFillBackground

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

```
virtual COLORREF OnFillBackground(CDC* pDC);
```

### <a name="parameters"></a>Parametry

[v] *pDC*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonstatusbarpaneonfinishanimation"></a><a name="onfinishanimation"></a>CMFCRibbonRibbonStatusBarPane::OnFinishAnimation

Framework volá tuto metodu, když končí animace přiřazená podoknu.

```
virtual void OnFinishAnimation();
```

### <a name="remarks"></a>Poznámky

`StopAnimation`metoda volá `OnFinishAnimation` metodu, kterou můžete použít k vyčištění dat po ukončení animace.

## <a name="cmfcribbonstatusbarpanesetalmostlargetext"></a><a name="setalmostlargetext"></a>CMFCRibbonRibbonStatusBarPane::SetAlmostLargeText

Definujte nejdelší text, který lze zobrazit v podokně stavového řádku bez zkrácení.

```
void SetAlmostLargeText(LPCTSTR lpszAlmostLargeText);
```

### <a name="parameters"></a>Parametry

*lpszTéměřLargeText*<br/>
[v] Určuje nejdelší řetězec, který lze zobrazit v podokně stavového řádku bez zkrácení.

### <a name="remarks"></a>Poznámky

Knihovna vypočítá velikost textu, který *lpszAlmostLargeText* určuje a odpovídajícím způsobem změní velikost podokna. Text bude zkrácen, pokud se stále nevejde do podokna.

## <a name="cmfcribbonstatusbarpanesetanimationlist"></a><a name="setanimationlist"></a>CMFCRibbonRibbonStatusBarPane::SetanimationList

Připojí k podokně stavového řádku seznam obrázků, který lze použít pro animaci.

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
[v] Určuje úchyt do seznamu obrázků.

*cxAnimace*<br/>
[v] Určuje šířku rámečku v obrazových bodech v seznamu obrázků.

*clrTransp*<br/>
[v] Určuje průhlednou barvu seznamu obrázků.

*uiAnimationListResID*<br/>
[v] Určuje ID prostředku seznamu obrázků.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je seznam obrázků úspěšně připojen k podokně stavového řádku; FALSE jinak.

## <a name="cmfcribbonstatusbarpanesettextalign"></a><a name="settextalign"></a>CMFCRibbonStatusBarPane::SetTextAlign

Nastaví zarovnání textu popisku podokna stavového řádku.

```
void SetTextAlign(int nAlign);
```

### <a name="parameters"></a>Parametry

*nZarovnat*<br/>
[v] Určuje zarovnání textu.

### <a name="remarks"></a>Poznámky

*nAlign* může mít jednu z následujících hodnot:

- TA_LEFT: zarovnání doleva

- TA_CENTER: zarovnání na střed

- TA_RIGHT: zarovnání vpravo

## <a name="cmfcribbonstatusbarpanestartanimation"></a><a name="startanimation"></a>CMFCRibbonStatusBarPane::StartAnimation

Spustí animaci, kterou přiřadíte k podokně.

```
void StartAnimation(
    UINT nFrameDelay=500,
    UINT nDuration=-1);
```

### <a name="parameters"></a>Parametry

*nZpoždění rámce*<br/>
[v] Určuje kmitočet snímků animace v milisekundách.

*nDoba trvání*<br/>
[v] Určuje, jak dlouho se má animace přehrávat v milisekundách. Použijte -1 pro nekonečnou smyčku.

### <a name="remarks"></a>Poznámky

Před voláním pomocí aplikace `StartAnimation` `SetAnimationList`je nutné zadat popisovač seznamu obrázků.

## <a name="cmfcribbonstatusbarpanestopanimation"></a><a name="stopanimation"></a>CMFCRibbonRibbonStatusBarPane::StopAnimation

Zastaví animaci přiřazenou podoknu stavového řádku.

```
void StopAnimation();
```

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton – třída](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[Třída cmfcpásového pruhu](../../mfc/reference/cmfcribbonstatusbar-class.md)
