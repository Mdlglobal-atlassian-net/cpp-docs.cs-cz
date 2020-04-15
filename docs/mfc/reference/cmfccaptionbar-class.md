---
title: Třída CMFCCaptionBar
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
ms.openlocfilehash: 3a1e8890176fe686b54fe4756dfd578869cbcdfb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367799"
---
# <a name="cmfccaptionbar-class"></a>Třída CMFCCaptionBar

Objekt `CMFCCaptionBar` je ovládací panel, který může zobrazit tři prvky: tlačítko, textový popisek a bitmapu. Může zobrazit pouze jeden prvek každého typu najednou. Každý prvek můžete zarovnat k levému nebo pravému okraji ovládacího prvku nebo ke středu. Můžete také použít plochý nebo 3D styl na horní a dolní okraj pruhu titulků.

## <a name="syntax"></a>Syntaxe

```
class CMFCCaptionBar : public CPane
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCcaptionBar::Vytvořit](#create)|Vytvoří ovládací prvek pruhu titulků `CMFCCaptionBar` a připojí jej k objektu.|
|[CMFCCaptionBar::DoesAllowDynInsertPřed](#doesallowdyninsertbefore)|Označuje, zda lze mezi pruh titulků a nadřazený rámeček dynamicky vložit jiné podokno. (Přepíše [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CMFCcaptionBar::EnableButton](#enablebutton)|Povolí nebo zakáže tlačítko na panelu titulků.|
|[CMFCcaptionBar::GetAlignment](#getalignment)|Vrátí zarovnání zadaného prvku.|
|[CMFCcaptionBar::GetBorderSize](#getbordersize)|Vrátí velikost ohraničení pruhu titulků.|
|[CMFCCaptionBar::GetButtonRect](#getbuttonrect)|Načte ohraničovací obdélník tlačítka na panelu titulků.|
|[CMFCcaptionBar::GetMargin](#getmargin)|Vrátí vzdálenost mezi okrajem prvků pruhu titulků a okrajem ovládacího prvku panelu titulků.|
|[CMFCcaptionBar::Režim ismessagebarmode](#ismessagebarmode)|Určuje, zda je panel titulků v režimu panelu zpráv.|
|[CMFCCaptionBar::RemoveBitmap](#removebitmap)|Odebere bitmapový obraz z pruhu titulků.|
|[CMFCcaptionBar::Tlačítko RemoveButton](#removebutton)|Odebere tlačítko z pruhu titulků.|
|[CMFCcaptionBar::RemoveIcon](#removeicon)|Odebere ikonu z pruhu titulků.|
|[CMFCcaptionBar::Odstranittext](#removetext)|Odebere textový popisek z pruhu titulků.|
|[CMFCCaptionBar::SetBitmap](#setbitmap)|Nastaví bitmapový obraz pro pruh titulků.|
|[CMFCcaptionBar::SetBorderSize](#setbordersize)|Nastaví velikost ohraničení pruhu titulků.|
|[CMFCcaptionBar::SetButton](#setbutton)|Nastaví tlačítko pro panel titulků.|
|[CMFCcaptionBar::SetButtonPressed](#setbuttonpressed)|Určuje, zda tlačítko zůstane stisknuté.|
|[CMFCcaptionBar::SetButtonToolTip](#setbuttontooltip)|Nastaví popis pro tlačítko.|
|[CMFCcaptionBar::Nastavit ohraničení](#setflatborder)|Nastaví styl ohraničení pruhu titulků.|
|[CMFCcaptionBar::SetIcon](#seticon)|Nastaví ikonu pro panel titulků.|
|[CMFCcaptionBar:SetImageToolTip](#setimagetooltip)|Nastaví popisek obrázku pro pruh titulků.|
|[CMFCcaptionBar::SetMargin](#setmargin)|Nastaví vzdálenost mezi okrajem prvku panelu titulků a okrajem ovládacího prvku pruhu titulků.|
|[CMFCcaptionBar:SetText](#settext)|Nastaví textový popisek pro pruh titulků.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCcaptionBar::Pozadí při kreslení](#ondrawbackground)|Volat rámci vyplnit pozadí panelu titulků.|
|[CMFCcaptionBar::OnDrawBorder](#ondrawborder)|Volat rámci k nakreslení hranice indikátoru titulků.|
|[CMFCcaptionBar::OnDrawButton](#ondrawbutton)|Volat rámci nakreslit tlačítko titulku pruhu.|
|[CMFCcaptionBar::OnDrawImage](#ondrawimage)|Volat rámci k nakreslení obrázek titulku pruhu.|
|[CMFCcaptionBar::OnDrawText](#ondrawtext)|Volat rámci k nakreslení textu titulku pruhu.|

### <a name="data-members"></a>Členové dat

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCCaptionBar::m_clrBarBackground](#m_clrbarbackground)|Barva pozadí panelu titulků.|
|[CMFCCaptionBar::m_clrBarBorder](#m_clrbarborder)|Barva ohraničení pruhu titulků.|
|[CMFCCaptionBar::m_clrBarText](#m_clrbartext)|Barva textu záhlaví.|

## <a name="remarks"></a>Poznámky

Chcete-li vytvořit panel titulků, postupujte takto:

1. Vytvořte `CMFCCaptionBar` objekt. Obvykle byste přidat panel titulků do třídy okna rámce.

1. Volání [CMFCCaptionBar::Create](#create) metoda vytvořit ovládací prvek titulku `CMFCCaptionBar` pruhu a připojit jej k objektu.

1. Volání [CMFCCaptionBar::SetButton](#setbutton), [CMFCCaptionBar::SetText](#settext), [CMFCCaptionBar::SetIcon](#seticon)a [CMFCCaptionBar::SetBitmap](#setbitmap) pro nastavení prvků pruhu titulků.

Při nastavování prvku tlačítka je nutné tlačítku přiřadit ID příkazu. Když uživatel klepne na tlačítko, panel titulků směruje WM_COMMAND zprávy, které mají toto ID, do okna nadřazeného rámečku.

Panel titulků může fungovat také v režimu panelu zpráv, který emuluje panel zpráv, který se zobrazí v aplikacích sady Microsoft Office 2007. V režimu panelu zpráv se na panelu titulků zobrazí rastrový obrázek, zpráva a tlačítko (které obvykle otevře dialogové okno).) Bitmapě můžete přiřadit popisek.

Chcete-li povolit režim panelu zpráv, zavolejte [CMFCCaptionBar::Create](#create) a set the fourth parameter (bIsMessageBarMode) to TRUE.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat různé `CMFCCaptionBar` metody ve třídě. Příklad ukazuje, jak vytvořit ovládací prvek panelu titulků, nastavit 3D ohraničení pruhu titulků, nastavit vzdálenost v obrazových bodech mezi okrajem prvků pruhu titulků a okrajem ovládacího prvku pruhu titulků, nastavit tlačítko pro pruh titulků, nastavit popisek tlačítka, nastavit textový popis pro pruh titulků, nastavit bitmapový obraz pro pruh titulků a nastavte popisek obrazu v pruhu titulků. Tento fragment kódu je součástí [ukázky ukázky ukázky ukázky ms office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#1](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_1.h)]
[!code-cpp[NVC_MFC_MSOffice2007Demo#2](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CmFCcaptionBar](../../mfc/reference/cmfccaptionbar-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcaptionbar.h

## <a name="cmfccaptionbarcreate"></a><a name="create"></a>CMFCcaptionBar::Vytvořit

Vytvoří ovládací prvek pruhu titulků `CMFCCaptionBar` a připojí jej k objektu.

```
BOOL Create(
    DWORD dwStyle,
    CWnd* pParentWnd,
    UINT uID,
    int nHeight=-1,
    BOOL bIsMessageBarMode=FALSE);
```

### <a name="parameters"></a>Parametry

*dwStyl*<br/>
Logická kombinace nebo stylů titulků pruhu.

*pParentWnd*<br/>
Nadřazené okno ovládacího prvku panelu titulků.

*Uid*<br/>
ID ovládacího prvku paneltitulku.

*nVýška*<br/>
Výška ovládacího prvku panelu titulků v obrazových bodech. Pokud je -1, výška se vypočítá podle výšky ikony, textu a tlačítka, které se zobrazí ovládací prvek panelu titulků.

*bIsMessageBarMode*<br/>
TRUE, pokud je panel titulků v režimu panelu zpráv; FALSE jinak.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je ovládací prvek panelu titulků úspěšně vytvořen; FALSE jinak.

### <a name="remarks"></a>Poznámky

Objekt vytvoříte ve `CMFCCaptionBar` dvou krocích. Nejprve zavoláte konstruktor a potom `Create` zavoláte metodu, která vytvoří ovládací `CMFCCaptionBar` prvek systému Windows a připojí jej k objektu.

## <a name="cmfccaptionbardoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CMFCCaptionBar::DoesAllowDynInsertPřed

Označuje, zda lze mezi pruh titulků a nadřazený rámeček dynamicky vložit jiné podokno.

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu NEPRAVDA, pokud není přepsána.

### <a name="remarks"></a>Poznámky

## <a name="cmfccaptionbarenablebutton"></a><a name="enablebutton"></a>CMFCcaptionBar::EnableButton

Povolí nebo zakáže tlačítko na panelu titulků.

```
void EnableButton(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[v] TRUE povolit tlačítko, FALSE zakázat tlačítko.

## <a name="cmfccaptionbargetalignment"></a><a name="getalignment"></a>CMFCcaptionBar::GetAlignment

Vrátí zarovnání zadaného prvku.

```
BarElementAlignment GetAlignment(BarElement elem);
```

### <a name="parameters"></a>Parametry

*Elem*<br/>
[v] Prvek pruhu titulků, pro který chcete načíst zarovnání.

### <a name="return-value"></a>Návratová hodnota

Zarovnání prvku, například tlačítka, rastrového klíče, textu nebo ikony.

### <a name="remarks"></a>Poznámky

Zarovnání prvku může být jedna z následujících hodnot:

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="cmfccaptionbargetbordersize"></a><a name="getbordersize"></a>CMFCcaptionBar::GetBorderSize

Vrátí velikost ohraničení pruhu titulků.

```
int GetBorderSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Velikost ohraničení v obrazových bodech.

## <a name="cmfccaptionbargetbuttonrect"></a><a name="getbuttonrect"></a>CMFCCaptionBar::GetButtonRect

Načte ohraničovací obdélník tlačítka na panelu titulků.

```
CRect GetButtonRect() const;
```

### <a name="return-value"></a>Návratová hodnota

Objekt, `CRect` který obsahuje souřadnice ohraničujícího obdélníku tlačítka na panelu titulků.

## <a name="cmfccaptionbargetmargin"></a><a name="getmargin"></a>CMFCcaptionBar::GetMargin

Vrátí vzdálenost mezi okrajem prvků pruhu titulků a okrajem ovládacího prvku panelu titulků.

```
int GetMargin() const;
```

### <a name="return-value"></a>Návratová hodnota

Vzdálenost v obrazových bodech mezi okrajem prvků pruhu titulků a okrajem ovládacího prvku pruhu titulků.

## <a name="cmfccaptionbarismessagebarmode"></a><a name="ismessagebarmode"></a>CMFCcaptionBar::Režim ismessagebarmode

Určuje, zda je panel titulků v režimu panelu zpráv.

```
BOOL IsMessageBarMode() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je panel titulků v režimu panelu zpráv; FALSE jinak.

### <a name="remarks"></a>Poznámky

V režimu panelu zpráv se na panelu titulků zobrazí obrázek s popiskem, textem zprávy a tlačítkem.

## <a name="cmfccaptionbarm_clrbarbackground"></a><a name="m_clrbarbackground"></a>CMFCCaptionBar::m_clrBarBackground

Barva pozadí panelu titulků.

```
COLORREF m_clrBarBackground
```

## <a name="cmfccaptionbarm_clrbarborder"></a><a name="m_clrbarborder"></a>CMFCCaptionBar::m_clrBarBorder

Barva ohraničení pruhu titulků.

```
COLORREF m_clrBarBorder
```

## <a name="cmfccaptionbarm_clrbartext"></a><a name="m_clrbartext"></a>CMFCCaptionBar::m_clrBarText

Barva textu záhlaví.

```
COLORREF m_clrBarText
```

## <a name="cmfccaptionbarondrawbackground"></a><a name="ondrawbackground"></a>CMFCcaptionBar::Pozadí při kreslení

Volat rámci vyplnit pozadí panelu titulků.

```
virtual void OnDrawBackground(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení panelu titulků.

*Rect*<br/>
[v] Ohraničovací obdélník vyplnit.

### <a name="remarks"></a>Poznámky

Metoda `OnDrawBackground` je volána, když se má vyplnit pozadí panelu titulků. Výchozí implementace vyplní pozadí pomocí barvy [CMFCCaptionBar::m_clrBarBackground.](#m_clrbarbackground)

Přepsat tuto metodu `CMFCCaptionBar` v odvozené třídě přizpůsobit vzhled panelu titulků.

## <a name="cmfccaptionbarondrawborder"></a><a name="ondrawborder"></a>CMFCcaptionBar::OnDrawBorder

Volat rámci k nakreslení hranice indikátoru titulků.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Kontext zařízení, který se používá k zobrazení ohraničení.

*Rect*<br/>
[v] Ohraničovací obdélník.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení mají ohraničení plochý styl.

Přepsat tuto metodu `CMFCCaptionBar` v odvozené třídě přizpůsobit vzhled ohraničení panelu titulků.

## <a name="cmfccaptionbarondrawbutton"></a><a name="ondrawbutton"></a>CMFCcaptionBar::OnDrawButton

Volat rámci nakreslit tlačítko titulku pruhu.

```
virtual void OnDrawButton(
    CDC* pDC,
    CRect rect,
    const CString& strButton,
    BOOL bEnabled);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení, který se používá k zobrazení tlačítka.

*Rect*<br/>
[v] Ohraničovací obdélník tlačítka.

*strButton*<br/>
[v] Textový popisek tlačítka.

*bPovoleno*<br/>
[v] TRUE, pokud je tlačítko povoleno; FALSE jinak.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu `CMFCCaptionBar` v odvozené třídě přizpůsobit vzhled tlačítka titulku pruhu.

## <a name="cmfccaptionbarondrawimage"></a><a name="ondrawimage"></a>CMFCcaptionBar::OnDrawImage

Volat rámci k nakreslení obrázek titulku pruhu.

```
virtual void OnDrawImage(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení, který se používá k zobrazení obrázku.

*Rect*<br/>
[v] Určuje ohraničovací obdélník obrazu.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu `CMFCCaptionBar` v odvozené třídě přizpůsobit vzhled obrazu.

## <a name="cmfccaptionbarondrawtext"></a><a name="ondrawtext"></a>CMFCcaptionBar::OnDrawText

Volat rámci k nakreslení textu titulku pruhu.

```
virtual void OnDrawText(
    CDC* pDC,
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení, který se používá k zobrazení tlačítka.

*Rect*<br/>
[v] Ohraničující obdélník textu.

*strText*<br/>
[v] Textový řetězec, který se má zobrazit.

### <a name="remarks"></a>Poznámky

Výchozí implementace zobrazí text `CDC::DrawText` pomocí [cmfccaptionbar::m_clrBarText](#m_clrbartext) barvu.

Přepsat tuto metodu `CMFCCaptionBar` v odvozené třídě přizpůsobit vzhled textu titulku pruhu.

## <a name="cmfccaptionbarremovebitmap"></a><a name="removebitmap"></a>CMFCCaptionBar::RemoveBitmap

Odebere bitmapový obraz z pruhu titulků.

```
void RemoveBitmap();
```

## <a name="cmfccaptionbarremovebutton"></a><a name="removebutton"></a>CMFCcaptionBar::Tlačítko RemoveButton

Odebere tlačítko z pruhu titulků.

```
void RemoveButton();
```

### <a name="remarks"></a>Poznámky

Rozložení prvků pruhů titulků se upraví automaticky.

## <a name="cmfccaptionbarremoveicon"></a><a name="removeicon"></a>CMFCcaptionBar::RemoveIcon

Odebere ikonu z pruhu titulků.

```
void RemoveIcon();
```

## <a name="cmfccaptionbarremovetext"></a><a name="removetext"></a>CMFCcaptionBar::Odstranittext

Odebere textový popisek z pruhu titulků.

```
void RemoveText();
```

## <a name="cmfccaptionbarsetbitmap"></a><a name="setbitmap"></a>CMFCCaptionBar::SetBitmap

Nastaví bitmapový obraz pro pruh titulků.

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
[v] Popisovač pro rastrový obrázek nastavit.

*clrTransparent*<br/>
[v] Hodnota RGB, která určuje průhlednou barvu bitmapy.

*bÚsek*<br/>
[v] Pokud true, bitmapa je roztažená, pokud se nevejde do obdélníku ohraničující obraz. V opačném případě bitmapa není roztažená.

*bmpAlignment*<br/>
[v] Zarovnání bitmapy.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte k nastavení rastrového obrázku na panelu titulků.

Předchozí bitmapa je automaticky zničena. Pokud se na panelu titulků zobrazí ikona, protože jste volali metodu [CMFCCaptionBar::SetIcon,](#seticon) bitmapa se nezobrazí, pokud ikonu neodeberete voláním [CMFCCaptionBar::RemoveIcon](#removeicon).

Bitmapa je zarovnána podle specifikace parametru *bmpAlignment.*  Tento parametr může být `BarElementAlignment` jedna z následujících hodnot:

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="cmfccaptionbarsetbordersize"></a><a name="setbordersize"></a>CMFCcaptionBar::SetBorderSize

Nastaví velikost ohraničení pruhu titulků.

```
void SetBorderSize(int nSize);
```

### <a name="parameters"></a>Parametry

*nVelikost*<br/>
[v] Nová velikost ohraničení pruhu titulků v pixelech.

## <a name="cmfccaptionbarsetbutton"></a><a name="setbutton"></a>CMFCcaptionBar::SetButton

Nastaví tlačítko pro panel titulků.

```
void SetButton(
    LPCTSTR lpszLabel,
    UINT uiCmdUI,
    BarElementAlignment btnAlignmnet=ALIGN_LEFT,
    BOOL bHasDropDownArrow=TRUE);
```

### <a name="parameters"></a>Parametry

*popisek lpsz*<br/>
Popisek příkazu tlačítka.

*uiCmdUI*<br/>
ID příkazu tlačítka.

*btnAlignmnet*<br/>
Tlačítko je zarovnáno.

*bHasDropDownArrow*<br/>
PRAVDA, pokud tlačítko zobrazí šipku rozevíracího seznamu, jinak NEPRAVDA.

## <a name="cmfccaptionbarsetbuttonpressed"></a><a name="setbuttonpressed"></a>CMFCcaptionBar::SetButtonPressed

Určuje, zda tlačítko zůstane stisknuté.

```
void SetButtonPressed(BOOL bPresed=TRUE);
```

### <a name="parameters"></a>Parametry

*bPresed*<br/>
TRUE Pokud tlačítko zachová svůj stlačený stav, false jinak.

## <a name="cmfccaptionbarsetbuttontooltip"></a><a name="setbuttontooltip"></a>CMFCcaptionBar::SetButtonToolTip

Nastaví popis pro tlačítko.

```
void SetButtonToolTip(
    LPCTSTR lpszToolTip,
    LPCTSTR lpszDescription=NULL);
```

### <a name="parameters"></a>Parametry

*lpszToolTip*<br/>
[v] Popisek popisku.

*lpszDescription*<br/>
[v] Popis popisku.

## <a name="cmfccaptionbarsetflatborder"></a><a name="setflatborder"></a>CMFCcaptionBar::Nastavit ohraničení

Nastaví styl ohraničení pruhu titulků.

```
void SetFlatBorder(BOOL bFlat=TRUE);
```

### <a name="parameters"></a>Parametry

*bPlochý*<br/>
[v] PRAVDA, pokud je ohraničení pruhu titulků ploché. FALSE, pokud je ohraničení 3D.

## <a name="cmfccaptionbarseticon"></a><a name="seticon"></a>CMFCcaptionBar::SetIcon

Nastaví ikonu pro panel titulků.

```
void SetIcon(
    HICON hIcon,
    BarElementAlignment iconAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>Parametry

*hIkona*<br/>
[v] Úchyt k ikoně, kterou chcete nastavit.

*iconAlignment*<br/>
[v] Zarovnání ikony.

### <a name="remarks"></a>Poznámky

Pruhy titulků mohou zobrazovat ikony nebo rastrové obrázky. Viz [CMFCCaptionBar::SetBitmap,](#setbitmap) kde se dozvíte, jak zobrazit bitmapu. Pokud nastavíte ikonu i bitmapu, ikona se vždy zobrazí. Volání [CMFCCaptionBar::RemoveIcon](#removeicon) odebrat ikonu z panelu titulků.

Ikona je zarovnána podle parametru *iconAlignment.* Může to být jedna `BarElementAlignment` z následujících hodnot:

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="cmfccaptionbarsetimagetooltip"></a><a name="setimagetooltip"></a>CMFCcaptionBar:SetImageToolTip

Nastaví popisek obrazu v pruhu titulků.

```
void SetImageToolTip(
    LPCTSTR lpszToolTip,
    LPCTSTR lpszDescription=NULL);
```

### <a name="parameters"></a>Parametry

*lpszToolTip*<br/>
[v] Text popisku.

*lpszDescription*<br/>
[v] Popis popisku.

## <a name="cmfccaptionbarsetmargin"></a><a name="setmargin"></a>CMFCcaptionBar::SetMargin

Nastaví vzdálenost mezi okrajem prvku panelu titulků a okrajem ovládacího prvku pruhu titulků.

```
void SetMargin(int nMargin);
```

### <a name="parameters"></a>Parametry

*nMarže*<br/>
[v] Vzdálenost v obrazových bodech mezi okrajem prvků pruhu titulků a okrajem ovládacího prvku pruhu titulků.

## <a name="cmfccaptionbarsettext"></a><a name="settext"></a>CMFCcaptionBar:SetText

Nastaví textový popisek pro pruh titulků.

```
void SetText(
    const CString& strText,
    BarElementAlignment textAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>Parametry

*strText*<br/>
[v] Textový řetězec nastavit.

*Textalignment*<br/>
[v] Zarovnání textu.

### <a name="remarks"></a>Poznámky

Popisek textu je zarovnán podle parametru *textAlignment.* Může to být jedna `BarElementAlignment` z následujících hodnot:

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
