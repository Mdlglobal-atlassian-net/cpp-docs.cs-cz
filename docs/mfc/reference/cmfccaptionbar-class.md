---
title: CMFCCaptionBar – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCCaptionBar
- AFXCAPTIONBAR/CMFCCaptionBar
- AFXCAPTIONBAR/CMFCCaptionBar::Create
- AFXCAPTIONBAR/CMFCCaptionBar::DoesAllowDynInsertBefore
- AFXCAPTIONBAR/CMFCCaptionBar::EnableButton
- AFXCAPTIONBAR/CMFCCaptionBar::GetAlignment
- AFXCAPTIONBAR/CMFCCaptionBar::GetBorderSize
- AFXCAPTIONBAR/CMFCCaptionBar::GetButtonRect
- AFXCAPTIONBAR/CMFCCaptionBar::GetMargin
- AFXCAPTIONBAR/CMFCCaptionBar::IsMessageBarMode
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveBitmap
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveButton
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveIcon
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveText
- AFXCAPTIONBAR/CMFCCaptionBar::SetBitmap
- AFXCAPTIONBAR/CMFCCaptionBar::SetBorderSize
- AFXCAPTIONBAR/CMFCCaptionBar::SetButton
- AFXCAPTIONBAR/CMFCCaptionBar::SetButtonPressed
- AFXCAPTIONBAR/CMFCCaptionBar::SetButtonToolTip
- AFXCAPTIONBAR/CMFCCaptionBar::SetFlatBorder
- AFXCAPTIONBAR/CMFCCaptionBar::SetIcon
- AFXCAPTIONBAR/CMFCCaptionBar::SetImageToolTip
- AFXCAPTIONBAR/CMFCCaptionBar::SetMargin
- AFXCAPTIONBAR/CMFCCaptionBar::SetText
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawBackground
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawBorder
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawButton
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawImage
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawText
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarBackground
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarBorder
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarText
helpviewer_keywords:
- CMFCCaptionBar [MFC], Create
- CMFCCaptionBar [MFC], DoesAllowDynInsertBefore
- CMFCCaptionBar [MFC], EnableButton
- CMFCCaptionBar [MFC], GetAlignment
- CMFCCaptionBar [MFC], GetBorderSize
- CMFCCaptionBar [MFC], GetButtonRect
- CMFCCaptionBar [MFC], GetMargin
- CMFCCaptionBar [MFC], IsMessageBarMode
- CMFCCaptionBar [MFC], RemoveBitmap
- CMFCCaptionBar [MFC], RemoveButton
- CMFCCaptionBar [MFC], RemoveIcon
- CMFCCaptionBar [MFC], RemoveText
- CMFCCaptionBar [MFC], SetBitmap
- CMFCCaptionBar [MFC], SetBorderSize
- CMFCCaptionBar [MFC], SetButton
- CMFCCaptionBar [MFC], SetButtonPressed
- CMFCCaptionBar [MFC], SetButtonToolTip
- CMFCCaptionBar [MFC], SetFlatBorder
- CMFCCaptionBar [MFC], SetIcon
- CMFCCaptionBar [MFC], SetImageToolTip
- CMFCCaptionBar [MFC], SetMargin
- CMFCCaptionBar [MFC], SetText
- CMFCCaptionBar [MFC], OnDrawBackground
- CMFCCaptionBar [MFC], OnDrawBorder
- CMFCCaptionBar [MFC], OnDrawButton
- CMFCCaptionBar [MFC], OnDrawImage
- CMFCCaptionBar [MFC], OnDrawText
- CMFCCaptionBar [MFC], m_clrBarBackground
- CMFCCaptionBar [MFC], m_clrBarBorder
- CMFCCaptionBar [MFC], m_clrBarText
ms.assetid: acb54d5f-14ff-4c96-aeb3-7717cf566d9a
ms.openlocfilehash: 1a18e235c9f5875a977f740c26b917a3567a678d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57264986"
---
# <a name="cmfccaptionbar-class"></a>CMFCCaptionBar – třída

A `CMFCCaptionBar` objekt je ovládací panel, který může zobrazit tři prvky: tlačítko, textový popisek a rastrový obrázek. Současně může zobrazit pouze jeden prvek každého typu. Je možné zarovnat každý prvek do levého či pravého okraje ovládacího prvku nebo na střed. Můžete také použít styl ploché nebo 3D na horní a dolní ohraničení záhlaví.

## <a name="syntax"></a>Syntaxe

```
class CMFCCaptionBar : public CPane
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCCaptionBar::Create](#create)|Vytvoří ovládací prvek panel titulek a připojí ho k `CMFCCaptionBar` objektu.|
|[CMFCCaptionBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Určuje, zda jiný podokně můžete dynamicky vložen mezi záhlaví a jeho nadřazeného rámce. (Přepíše [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CMFCCaptionBar::EnableButton](#enablebutton)|Povolí nebo zakáže tlačítko v záhlaví.|
|[CMFCCaptionBar::GetAlignment](#getalignment)|Vrátí zadaný element zarovnání.|
|[CMFCCaptionBar::GetBorderSize](#getbordersize)|Vrátí velikost ohraničení záhlaví.|
|[CMFCCaptionBar::GetButtonRect](#getbuttonrect)|Načte ohraničující obdélník tlačítko v záhlaví.|
|[CMFCCaptionBar::GetMargin](#getmargin)|Vrací vzdálenost mezi hraniční prvky panelu titulek a okrajem ovládacího prvku panelu titulek.|
|[CMFCCaptionBar::IsMessageBarMode](#ismessagebarmode)|Určuje, zda záhlaví je v režimu panel zpráv.|
|[CMFCCaptionBar::RemoveBitmap](#removebitmap)|Odebere rastrový obrázek ze záhlaví.|
|[CMFCCaptionBar::RemoveButton](#removebutton)|Odebere tlačítko z záhlaví.|
|[CMFCCaptionBar::RemoveIcon](#removeicon)|Ikona se odebere ze záhlaví.|
|[CMFCCaptionBar::RemoveText](#removetext)|Textový popisek se odebere ze záhlaví.|
|[CMFCCaptionBar::SetBitmap](#setbitmap)|Nastavuje rastrový obrázek pro záhlaví.|
|[CMFCCaptionBar::SetBorderSize](#setbordersize)|Nastaví velikost ohraničení záhlaví.|
|[CMFCCaptionBar::SetButton](#setbutton)|Nastaví na tlačítko pro záhlaví.|
|[CMFCCaptionBar::SetButtonPressed](#setbuttonpressed)|Určuje, zda zůstává při stisknutí tlačítka.|
|[CMFCCaptionBar::SetButtonToolTip](#setbuttontooltip)|Nastaví popisek tlačítka.|
|[CMFCCaptionBar::SetFlatBorder](#setflatborder)|Nastaví styl ohraničení záhlaví.|
|[CMFCCaptionBar::SetIcon](#seticon)|Určuje ikonu pro záhlaví.|
|[CMFCCaptionBar::SetImageToolTip](#setimagetooltip)|Nastaví popisek pro bitovou kopii pro záhlaví.|
|[CMFCCaptionBar::SetMargin](#setmargin)|Nastaví vzdálenost mezi okraj panelu element caption a okrajem ovládacího prvku panelu titulek.|
|[CMFCCaptionBar::SetText](#settext)|Nastaví textový popisek pro záhlaví.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CMFCCaptionBar::OnDrawBackground](#ondrawbackground)|Volá se rozhraním, aby vyplnit pozadí záhlaví.|
|[CMFCCaptionBar::OnDrawBorder](#ondrawborder)|Volá se rozhraním, chcete-li nakreslit ohraničení záhlaví.|
|[CMFCCaptionBar::OnDrawButton](#ondrawbutton)|Volá se rozhraním, chcete-li nakreslit tlačítko na panelu titulek.|
|[CMFCCaptionBar::OnDrawImage](#ondrawimage)|Volá se rozhraním, chcete-li nakreslit obrázek panelu titulek.|
|[CMFCCaptionBar::OnDrawText](#ondrawtext)|Volá se rozhraním, chcete-li nakreslit text titulku panelu.|

### <a name="data-members"></a>Datové členy

|Název|Popis|
|----------|-----------------|
|[CMFCCaptionBar::m_clrBarBackground](#m_clrbarbackground)|Barva pozadí záhlaví.|
|[CMFCCaptionBar::m_clrBarBorder](#m_clrbarborder)|Barva ohraničení záhlaví.|
|[CMFCCaptionBar::m_clrBarText](#m_clrbartext)|Barva textu řádku titulek.|

## <a name="remarks"></a>Poznámky

Pokud chcete vytvořit záhlaví, postupujte takto:

1. Vytvořit `CMFCCaptionBar` objektu. Obvykle by přidat záhlaví do třídy okna rámce.

1. Volání [CMFCCaptionBar::Create](#create) metodu pro vytvoření ovládacích prvků panelu titulek a připojte ji k `CMFCCaptionBar` objektu.

1. Volání [CMFCCaptionBar::SetButton](#setbutton), [CMFCCaptionBar::SetText](#settext), [CMFCCaptionBar::SetIcon](#seticon), a [CMFCCaptionBar::SetBitmap](#setbitmap)nastavit prvky panelu titulek.

Když nastavíte prvku button, musíte přiřadit ID příkazu pro tlačítko. Když uživatel klikne na tlačítko, směruje záhlaví wm_command – zprávy, které bylo toto ID nadřazeného rámce okna.

Záhlaví může spolupracovat také v režimu panel zpráv, které emuluje panel zpráv, který se zobrazí v aplikacích Microsoft Office 2007. V režimu zpráv panelu zobrazí záhlaví rastrový obrázek, zprávu a tlačítko (což obvykle otevře dialogové okno.) Popisek můžete přiřadit rastrového obrázku.

Chcete-li povolit režim panel zpráv, zavolejte [CMFCCaptionBar::Create](#create) a čtvrtý parametr (bIsMessageBarMode) nastavena na hodnotu TRUE.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít různé metody v `CMFCCaptionBar` třídy. Tento příklad ukazuje, jak vytvořit ovládací prvek panel titulek, nastavte 3D okraj záhlaví, nastavte vzdálenost v pixelech mezi hraniční titulek panelu elementy a okrajem ovládacího prvku panelu titulek, nastavení tlačítka pro záhlaví , nastavit popisu tlačítka pro tlačítko, nastavte textový popisek pro záhlaví, nastavit rastrový obrázek pro záhlaví a nastavit popis bitové kopie v záhlaví. Tento fragment kódu je součástí [MS Office 2007 demonstrační ukázka](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#1](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_1.h)]
[!code-cpp[NVC_MFC_MSOffice2007Demo#2](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCCaptionBar](../../mfc/reference/cmfccaptionbar-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcaptionbar.h

##  <a name="create"></a>  CMFCCaptionBar::Create

Vytvoří ovládací prvek panel titulek a připojí ho k `CMFCCaptionBar` objektu.

```
BOOL Create(
    DWORD dwStyle,
    CWnd* pParentWnd,
    UINT uID,
    int nHeight=-1,
    BOOL bIsMessageBarMode=FALSE);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Logický OR kombinace styly řádku titulek.

*pParentWnd*<br/>
Nadřazené okno ovládacího prvku panelu titulek.

*uID*<br/>
ID ovládacího prvku panelu titulek.

*nHeight*<br/>
Výška v pixelech, panel ovládacího prvku popisek. Pokud je hodnota -1, výška se vypočítává podle výšky na ikonu, text a tlačítko, které se zobrazí ovládací prvek panel titulek.

*bIsMessageBarMode*<br/>
Hodnota TRUE, pokud je záhlaví v režimu řádku zprávy; FALSE v opačném případě.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud ovládací prvek panel titulků je vytvořen úspěšně; FALSE v opačném případě.

### <a name="remarks"></a>Poznámky

Můžete vytvořit `CMFCCaptionBar` objektu ve dvou krocích. Nejprve volat konstruktor a následně zavolat `Create` metodu, která vytvoří ovládací prvek Windows a připojí ho k `CMFCCaptionBar` objektu.

##  <a name="doesallowdyninsertbefore"></a>  CMFCCaptionBar::DoesAllowDynInsertBefore

Určuje, zda jiný podokně můžete dynamicky vložen mezi záhlaví a jeho nadřazeného rámce.

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu FALSE, pokud nejsou přepsány.

### <a name="remarks"></a>Poznámky

##  <a name="enablebutton"></a>  CMFCCaptionBar::EnableButton

Povolí nebo zakáže tlačítko v záhlaví.

```
void EnableButton(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[in] TRUE pro povolení panelu FALSE zakázat tlačítko.

##  <a name="getalignment"></a>  CMFCCaptionBar::GetAlignment

Vrátí zadaný element zarovnání.

```
BarElementAlignment GetAlignment(BarElement elem);
```

### <a name="parameters"></a>Parametry

*Elem*<br/>
[in] Element caption panel pro kterou se má načíst zarovnání.

### <a name="return-value"></a>Návratová hodnota

Zarovnání prvku, jako je například tlačítko, rastrový obrázek, text nebo ikonu.

### <a name="remarks"></a>Poznámky

Zarovnání prvku může být jedna z následujících hodnot:

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

##  <a name="getbordersize"></a>  CMFCCaptionBar::GetBorderSize

Vrátí velikost ohraničení záhlaví.

```
int GetBorderSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Velikost v pixelech, ohraničení.

##  <a name="getbuttonrect"></a>  CMFCCaptionBar::GetButtonRect

Načte ohraničující obdélník tlačítko v záhlaví.

```
CRect GetButtonRect() const;
```

### <a name="return-value"></a>Návratová hodnota

A `CRect` objekt, který obsahuje souřadnice ohraničující obdélník tlačítko v záhlaví.

##  <a name="getmargin"></a>  CMFCCaptionBar::GetMargin

Vrací vzdálenost mezi hraniční prvky panelu titulek a okrajem ovládacího prvku panelu titulek.

```
int GetMargin() const;
```

### <a name="return-value"></a>Návratová hodnota

Vzdálenost v pixelech mezi hraniční prvky panelu titulek a okrajem ovládacího prvku panelu titulek.

##  <a name="ismessagebarmode"></a>  CMFCCaptionBar::IsMessageBarMode

Určuje, zda záhlaví je v režimu panel zpráv.

```
BOOL IsMessageBarMode() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je záhlaví v režimu řádku zprávy; FALSE v opačném případě.

### <a name="remarks"></a>Poznámky

V režimu panel zpráv zobrazí záhlaví bitovou kopii s popis tlačítka, text zprávy a tlačítko.

##  <a name="m_clrbarbackground"></a>  CMFCCaptionBar::m_clrBarBackground

Barva pozadí záhlaví.

```
COLORREF m_clrBarBackground
```

##  <a name="m_clrbarborder"></a>  CMFCCaptionBar::m_clrBarBorder

Barva ohraničení záhlaví.

```
COLORREF m_clrBarBorder
```

##  <a name="m_clrbartext"></a>  CMFCCaptionBar::m_clrBarText

Barva textu řádku titulek.

```
COLORREF m_clrBarText
```

##  <a name="ondrawbackground"></a>  CMFCCaptionBar::OnDrawBackground

Volá se rozhraním, aby vyplnit pozadí záhlaví.

```
virtual void OnDrawBackground(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Ukazatel na kontext zařízení záhlaví.

*Rect*<br/>
[in] Ohraničující obdélník tak, aby vyplnil.

### <a name="remarks"></a>Poznámky

`OnDrawBackground` Metoda se volá, když na pozadí záhlaví je vyplnění. Výchozí implementace vyplní na pozadí s použitím [CMFCCaptionBar::m_clrBarBackground](#m_clrbarbackground) barvu.

Potlačí tuto metodu v `CMFCCaptionBar` odvozené třídy pro přizpůsobení vzhledu záhlaví.

##  <a name="ondrawborder"></a>  CMFCCaptionBar::OnDrawBorder

Volá se rozhraním, chcete-li nakreslit ohraničení záhlaví.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Kontext zařízení, která se používá k zobrazení ohraničení.

*Rect*<br/>
[in] Ohraničující obdélník.

### <a name="remarks"></a>Poznámky

Ohraničení, která mají ve výchozím nastavení plochý.

Potlačí tuto metodu v `CMFCCaptionBar` odvozené třídy pro přizpůsobení vzhledu ohraničení panelu titulek.

##  <a name="ondrawbutton"></a>  CMFCCaptionBar::OnDrawButton

Volá se rozhraním, chcete-li nakreslit tlačítko na panelu titulek.

```
virtual void OnDrawButton(
    CDC* pDC,
    CRect rect,
    const CString& strButton,
    BOOL bEnabled);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Ukazatel na kontext zařízení, který se používá k zobrazení tlačítka.

*Rect*<br/>
[in] Ohraničující obdélník na tlačítko.

*strButton*<br/>
[in] Textový popisek tlačítka.

*bEnabled*<br/>
[in] Hodnota TRUE, pokud je povolené tlačítko; FALSE v opačném případě.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu v `CMFCCaptionBar` odvozené třídy pro přizpůsobení vzhledu tlačítka záhlaví.

##  <a name="ondrawimage"></a>  CMFCCaptionBar::OnDrawImage

Volá se rozhraním, chcete-li nakreslit obrázek panelu titulek.

```
virtual void OnDrawImage(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Ukazatel na kontext zařízení, který se používá k zobrazení obrázku.

*Rect*<br/>
[in] Určuje ohraničující obdélník bitové kopie.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu v `CMFCCaptionBar` odvozené třídy pro přizpůsobení vzhledu bitové kopie.

##  <a name="ondrawtext"></a>  CMFCCaptionBar::OnDrawText

Volá se rozhraním, chcete-li nakreslit text titulku panelu.

```
virtual void OnDrawText(
    CDC* pDC,
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Ukazatel na kontext zařízení, který se používá k zobrazení tlačítka.

*Rect*<br/>
[in] Ohraničující obdélník textu.

*strText*<br/>
[in] Textový řetězec k zobrazení.

### <a name="remarks"></a>Poznámky

Výchozí implementace zobrazí text pomocí `CDC::DrawText` a [CMFCCaptionBar::m_clrBarText](#m_clrbartext) barvu.

Potlačí tuto metodu v `CMFCCaptionBar` odvozené třídy pro přizpůsobení vzhledu textu záhlaví.

##  <a name="removebitmap"></a>  CMFCCaptionBar::RemoveBitmap

Odebere rastrový obrázek ze záhlaví.

```
void RemoveBitmap();
```

##  <a name="removebutton"></a>  CMFCCaptionBar::RemoveButton

Odebere tlačítko z záhlaví.

```
void RemoveButton();
```

### <a name="remarks"></a>Poznámky

Automaticky se upraví rozložení prvků panelu titulek.

##  <a name="removeicon"></a>  CMFCCaptionBar::RemoveIcon

Ikona se odebere ze záhlaví.

```
void RemoveIcon();
```

##  <a name="removetext"></a>  CMFCCaptionBar::RemoveText

Textový popisek se odebere ze záhlaví.

```
void RemoveText();
```

##  <a name="setbitmap"></a>  CMFCCaptionBar::SetBitmap

Nastavuje rastrový obrázek pro záhlaví.

```
void SetBitmap(
    HBITMAP hBitmap,
    COLORREF clrTransparent,
    BOOL bStretch=FALSE,
    BarElementAlignment bmpAlignment=ALIGN_RIGHT);

void SetBitmap(
    UINT uiBmpResID,
    COLORREF clrTransparent,
    BOOL bStretch=FALSE,
    BarElementAlignment bmpAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>Parametry

*hBitmap*<br/>
[in] Popisovač rastrový obrázek pro nastavení.

*clrTransparent*<br/>
[in] Hodnota RGB, která určuje průhlednou barvu rastrového obrázku.

*bStretch*<br/>
[in] Při hodnotě TRUE je roztažená rastrového obrázku, pokud nevejde do bitové kopie ohraničující obdélník. Jinak není roztažená rastrového obrázku.

*bmpAlignment*<br/>
[in] Zarovnání rastrového obrázku.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete nastavit rastrový obrázek záhlaví.

Předchozí rastrového obrázku je zničen automaticky. Pokud záhlaví zobrazuje ikonu, protože jste volali [CMFCCaptionBar::SetIcon](#seticon) metody rastrového obrázku se nezobrazí, dokud neodeberete ikonu voláním [CMFCCaptionBar::RemoveIcon](#removeicon).

Rastrový obrázek je zarovnán podle *bmpAlignment* parametru.  Tento parametr může být jeden z následujících `BarElementAlignment` hodnoty:

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

##  <a name="setbordersize"></a>  CMFCCaptionBar::SetBorderSize

Nastaví velikost ohraničení záhlaví.

```
void SetBorderSize(int nSize);
```

### <a name="parameters"></a>Parametry

*nSize*<br/>
[in] Nová velikost v pixelech, popisek ohraničení panelu.

##  <a name="setbutton"></a>  CMFCCaptionBar::SetButton

Nastaví na tlačítko pro záhlaví.

```
void SetButton(
    LPCTSTR lpszLabel,
    UINT uiCmdUI,
    BarElementAlignment btnAlignmnet=ALIGN_LEFT,
    BOOL bHasDropDownArrow=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
Příkaz popisek tlačítka.

*uiCmdUI*<br/>
ID příkazu pro tlačítka.

*btnAlignmnet*<br/>
Zarovnání na tlačítko.

*bHasDropDownArrow*<br/>
TRUE, pokud na tomto tlačítku zobrazí na rozevírací šipku, FALSE v opačném případě.

##  <a name="setbuttonpressed"></a>  CMFCCaptionBar::SetButtonPressed

Určuje, zda zůstává při stisknutí tlačítka.

```
void SetButtonPressed(BOOL bPresed=TRUE);
```

### <a name="parameters"></a>Parametry

*bPresed*<br/>
TRUE, pokud tlačítko udržuje stavu při stisknutí FALSE v opačném případě.

##  <a name="setbuttontooltip"></a>  CMFCCaptionBar::SetButtonToolTip

Nastaví popisek tlačítka.

```
void SetButtonToolTip(
    LPCTSTR lpszToolTip,
    LPCTSTR lpszDescription=NULL);
```

### <a name="parameters"></a>Parametry

*lpszToolTip*<br/>
[in] Popisek popisu tlačítka.

*lpszDescription*<br/>
[in] Popis popisku.

##  <a name="setflatborder"></a>  CMFCCaptionBar::SetFlatBorder

Nastaví styl ohraničení záhlaví.

```
void SetFlatBorder(BOOL bFlat=TRUE);
```

### <a name="parameters"></a>Parametry

*bFlat*<br/>
[in] TRUE, pokud je plochý ohraničení záhlaví. FALSE, pokud je 3D ohraničení.

##  <a name="seticon"></a>  CMFCCaptionBar::SetIcon

Určuje ikonu pro záhlaví.

```
void SetIcon(
    HICON hIcon,
    BarElementAlignment iconAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>Parametry

*hIcon*<br/>
[in] Popisovač na ikonu nastavení.

*iconAlignment*<br/>
[in] Zarovnání na ikonu.

### <a name="remarks"></a>Poznámky

Titulek panely můžete zobrazit ikony nebo rastrové obrázky. Zobrazit [CMFCCaptionBar::SetBitmap](#setbitmap) a zjistěte, jak zobrazit rastrový obrázek. Pokud nastavíte ikony i bitmapy, ikony je vždy zobrazen. Volání [CMFCCaptionBar::RemoveIcon](#removeicon) ikona odebrání záhlaví.

Ikona je zarovnán podle *iconAlignment* parametru. Může být jeden z následujících `BarElementAlignment` hodnoty:

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

##  <a name="setimagetooltip"></a>  CMFCCaptionBar::SetImageToolTip

Nastaví popisek pro bitovou kopii v záhlaví.

```
void SetImageToolTip(
    LPCTSTR lpszToolTip,
    LPCTSTR lpszDescription=NULL);
```

### <a name="parameters"></a>Parametry

*lpszToolTip*<br/>
[in] Text popisu tlačítka.

*lpszDescription*<br/>
[in] Popis popisku.

##  <a name="setmargin"></a>  CMFCCaptionBar::SetMargin

Nastaví vzdálenost mezi okraj panelu element caption a okrajem ovládacího prvku panelu titulek.

```
void SetMargin(int nMargin);
```

### <a name="parameters"></a>Parametry

*nMargin*<br/>
[in] Vzdálenost v pixelech mezi hraniční prvky panelu titulek a okrajem ovládacího prvku panelu titulek.

##  <a name="settext"></a>  CMFCCaptionBar::SetText

Nastaví textový popisek pro záhlaví.

```
void SetText(
    const CString& strText,
    BarElementAlignment textAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>Parametry

*strText*<br/>
[in] Textový řetězec pro nastavení.

*textAlignment*<br/>
[in] Zarovnání textu.

### <a name="remarks"></a>Poznámky

Textový popisek je zarovnán podle *textAlignment* parametru. Může být jeden z následujících `BarElementAlignment` hodnoty:

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
