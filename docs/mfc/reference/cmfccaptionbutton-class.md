---
title: CMFCCaptionButton – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetHit
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetIconID
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetRect
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetSize
- AFXCAPTIONBUTTON/CMFCCaptionButton::IsMiniFrameButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::Move
- AFXCAPTIONBUTTON/CMFCCaptionButton::OnDraw
- AFXCAPTIONBUTTON/CMFCCaptionButton::SetMiniFrameButton
helpviewer_keywords:
- CMFCCaptionButton [MFC], CMFCCaptionButton
- CMFCCaptionButton [MFC], GetHit
- CMFCCaptionButton [MFC], GetIconID
- CMFCCaptionButton [MFC], GetRect
- CMFCCaptionButton [MFC], GetSize
- CMFCCaptionButton [MFC], IsMiniFrameButton
- CMFCCaptionButton [MFC], Move
- CMFCCaptionButton [MFC], OnDraw
- CMFCCaptionButton [MFC], SetMiniFrameButton
ms.assetid: c5774b38-c0dd-414a-9ede-3b2f78f233ec
ms.openlocfilehash: fb47e4373bf53e66dd4af17c89fe2f761858fbfd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367761"
---
# <a name="cmfccaptionbutton-class"></a>CMFCCaptionButton – třída

Třída `CMFCCaptionButton` implementuje tlačítko, které se zobrazí na panelu titulků pro dokovací podokno nebo okno minirámečku. Rámec obvykle vytvoří tlačítka titulků automaticky.

## <a name="syntax"></a>Syntaxe

```
class CMFCCaptionButton : public CObject
```

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCCaptionButton::CMFCCaptionButton](#cmfccaptionbutton)|Vytvoří objekt CMFCCaptionButton.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCCaptionButton::GetHit](#gethit)|Vrátí příkaz reprezentované tlačítkem.|
|[CMFCcaptionButton::GeticonID](#geticonid)|Vrátí ID obrázku přidružené k tlačítku.|
|[CMFCCaptionButton::GetRect](#getrect)|Vrátí obdélník obsazený tlačítkem.|
|[CMFCCaptionButton::GetSize](#getsize)|Vrátí šířku a výšku tlačítka.|
|[CMFCcaptionButton::isminiframebutton](#isminiframebutton)|Označuje, zda je výška záhlaví nastavena na minimální velikost.|
|[CMFCCaptionButton::Přesunout](#move)|Nastaví umístění kreslení tlačítek a stav zobrazení okna.|
|[CMFCCaptionButton::Ondraw](#ondraw)|Nakreslí tlačítko titulku.|
|[CMFCCaptionButton::SetMiniFrameButton](#setminiframebutton)|Nastaví mini velikost záhlaví.|

## <a name="remarks"></a>Poznámky

Třídu můžete odvodit z [třídy CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) a použít chráněnou metodu `AddButton`, k přidání tlačítek titulků do okna mini rámečku.

CPaneFrameWnd.h definuje ID příkazů pro dva typy tlačítek titulků:

- AFX_CAPTION_BTN_PIN, který zobrazí tlačítko pin, když dokovací podokno podporuje režim automatického skrytí.

- AFX_CAPTION_BTN_CLOSE, který zobrazí tlačítko **Zavřít,** když může být podokno zavřeno nebo skryto.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak `CMFCCaptionButton` vytvořit objekt a nastavit mini velikost záhlaví.

[!code-cpp[NVC_MFC_RibbonApp#43](../../mfc/reference/codesnippet/cpp/cmfccaptionbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CmFCCaptionButton](../../mfc/reference/cmfccaptionbutton-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcaptionbutton.h

## <a name="cmfccaptionbuttoncmfccaptionbutton"></a><a name="cmfccaptionbutton"></a>CMFCCaptionButton::CMFCCaptionButton

Vytvoří `CMFCCaptionButton` objekt.

```
CMFCCaptionButton();

CMFCCaptionButton(
    UINT nHit,
    BOOL bLeftAlign = FALSE);
```

### <a name="parameters"></a>Parametry

*nHit*<br/>
[v] Příkaz přidružený k tlačítku.

*bLeftAlign*<br/>
[v] Určuje, zda je tlačítko zarovnáno doleva.

V následující tabulce jsou uvedeny možné hodnoty parametru *nHit.*

|Hodnota|Příkaz|
|-----------|-------------|
|AFX_HTCLOSE|Tlačítko Zavřít.|
|HTMINBUTTON|Minimalizovat tlačítko.|
|HTMAXBUTTON|Tlačítko Maximalizovat.|
|AFX_HTLEFTBUTTON|Tlačítko se šipkou doleva.|
|AFX_HTRIGHTBUTTON|Tlačítko se šipkou doprava.|
|AFX_HTMENU|Tlačítko nabídky šipky dolů.|
|HTNOWHERE|Výchozí hodnota; nepředstavuje žádný příkaz.|

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení nejsou tlačítka titulků přidružena k příkazu.

Tlačítka titulků jsou zarovnána vpravo nebo vlevo.

## <a name="cmfccaptionbuttongethit"></a><a name="gethit"></a>CMFCCaptionButton::GetHit

Vrátí příkaz reprezentované tlačítkem.

```
UINT GetHit() const;
```

### <a name="return-value"></a>Návratová hodnota

Příkaz reprezentované tlačítkem.

V následující tabulce jsou uvedeny možné vrácené hodnoty.

|Hodnota|Příkaz|
|-----------|-------------|
|AFX_HTCLOSE|Tlačítko Zavřít.|
|HTMINBUTTON|Minimalizovat tlačítko.|
|HTMAXBUTTON|Tlačítko Maximalizovat.|
|AFX_HTLEFTBUTTON|Tlačítko se šipkou doleva.|
|AFX_HTRIGHTBUTTON|Tlačítko se šipkou doprava.|
|AFX_HTMENU|Tlačítko nabídky šipky dolů.|
|HTNOWHERE|Výchozí hodnota; nepředstavuje žádný příkaz.|

## <a name="cmfccaptionbuttongeticonid"></a><a name="geticonid"></a>CMFCcaptionButton::GeticonID

Vrátí ID obrázku přidružené k tlačítku.

```
virtual CMenuImages::IMAGES_IDS GetIconID(
    BOOL bHorz,
    BOOL bMaximized = FALSE) const;
```

### <a name="parameters"></a>Parametry

*bHorz*<br/>
[v] TRUE pro ID obrázku se šipkou vlevo nebo vpravo; FALSE pro ID obrázku šipky nahoru nebo dolů.

*bMaximalizace*<br/>
[v] TRUE pro maximalizovat ID obrazu; FALSE pro minimalizaci ID obrázku.

### <a name="return-value"></a>Návratová hodnota

ID obrázku.

### <a name="remarks"></a>Poznámky

Parametry určují ID obrazu pro minimalizaci nebo maximalizaci tlačítek titulků.

## <a name="cmfccaptionbuttongetrect"></a><a name="getrect"></a>CMFCCaptionButton::GetRect

Vrátí obdélník obsazený tlačítkem.

```
virtual CRect GetRect() const;
```

### <a name="return-value"></a>Návratová hodnota

Obdélník, který představuje umístění tlačítka.

### <a name="remarks"></a>Poznámky

Pokud tlačítko nevidíte, vrácená velikost je 0.

## <a name="cmfccaptionbuttongetsize"></a><a name="getsize"></a>CMFCCaptionButton::GetSize

Vrátí šířku a výšku tlačítka.

```
static CSize GetSize();
```

### <a name="return-value"></a>Návratová hodnota

Vnější rozměry tlačítka.

### <a name="remarks"></a>Poznámky

Vrácená velikost zahrnuje okraj tlačítka a ohraničení.

## <a name="cmfccaptionbuttonisminiframebutton"></a><a name="isminiframebutton"></a>CMFCcaptionButton::isminiframebutton

Označuje, zda je výška záhlaví nastavena na minimální velikost.

```
BOOL IsMiniFrameButton() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je titulek nastaven na mini velikost; jinak FALSE.

### <a name="remarks"></a>Poznámky

## <a name="cmfccaptionbuttonmove"></a><a name="move"></a>CMFCCaptionButton::Přesunout

Nastaví umístění kreslení tlačítek a stav zobrazení okna.

```
void Move(
    const CPoint& ptTo,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parametry

*ptTo*<br/>
[v] Nové umístění.

*bSkrýt*<br/>
[v] Zda se má tlačítko zobrazit.

## <a name="cmfccaptionbuttonondraw"></a><a name="ondraw"></a>CMFCCaptionButton::Ondraw

Nakreslí tlačítko titulku.

```
virtual void OnDraw(
    CDC* pDC,
    BOOL bActive,
    BOOL bHorz = TRUE,
    BOOL bMaximized = TRUE,
    BOOL bDisabled = FALSE);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení pro tlačítko.

*bAktivní*<br/>
[v] Určuje, zda se má nakreslit obrázek aktivního tlačítka.

*bHorz*<br/>
[v] Vyhrazeno pro použití v odvozené třídě.

*bMaximalizace*<br/>
[v] Určuje, zda chcete nakreslit obrázek maximalizovaného tlačítka.

*bZakázáno.*<br/>
[v] Určuje, zda se má nakreslit obrázek povoleného tlačítka.

### <a name="remarks"></a>Poznámky

Parametr *bMaximized* se používá, když je tlačítko maximalizovat nebo minimalizovat.

## <a name="cmfccaptionbuttonsetminiframebutton"></a><a name="setminiframebutton"></a>CMFCCaptionButton::SetMiniFrameButton

Nastaví mini velikost záhlaví.

```
void SetMiniFramebutton(BOOL bSet = TRUE);
```

### <a name="parameters"></a>Parametry

*bSet*<br/>
[v] TRUE pro mini výšku záhlaví; NEPRAVDA pro výchozí výšku záhlaví.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)<br/>
[Třída CDockablePane](../../mfc/reference/cdockablepane-class.md)
