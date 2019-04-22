---
title: CMFCColorPickerCtrl Class
ms.date: 11/19/2018
f1_keywords:
- CMFCColorPickerCtrl
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::CMFCColorPickerCtrl
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetColor
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetHLS
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetHue
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetLuminance
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetSaturation
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SelectCellHexagon
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetColor
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetHLS
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetHue
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetLuminance
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetLuminanceBarWidth
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetOriginalColor
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetPalette
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetSaturation
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetType
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::DrawCursor
helpviewer_keywords:
- CMFCColorPickerCtrl [MFC], CMFCColorPickerCtrl
- CMFCColorPickerCtrl [MFC], GetColor
- CMFCColorPickerCtrl [MFC], GetHLS
- CMFCColorPickerCtrl [MFC], GetHue
- CMFCColorPickerCtrl [MFC], GetLuminance
- CMFCColorPickerCtrl [MFC], GetSaturation
- CMFCColorPickerCtrl [MFC], SelectCellHexagon
- CMFCColorPickerCtrl [MFC], SetColor
- CMFCColorPickerCtrl [MFC], SetHLS
- CMFCColorPickerCtrl [MFC], SetHue
- CMFCColorPickerCtrl [MFC], SetLuminance
- CMFCColorPickerCtrl [MFC], SetLuminanceBarWidth
- CMFCColorPickerCtrl [MFC], SetOriginalColor
- CMFCColorPickerCtrl [MFC], SetPalette
- CMFCColorPickerCtrl [MFC], SetSaturation
- CMFCColorPickerCtrl [MFC], SetType
- CMFCColorPickerCtrl [MFC], DrawCursor
ms.assetid: b9bbd03c-beb0-4b55-9765-9985fd05e5dc
ms.openlocfilehash: 1977717ee590acb63655ba21bfa5eb6bfe7c9bd8
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58772355"
---
# <a name="cmfccolorpickerctrl-class"></a>CMFCColorPickerCtrl Class

`CMFCColorPickerCtrl` Třída poskytuje funkce pro ovládací prvek, který se používá pro výběr barvy.

## <a name="syntax"></a>Syntaxe

```
class CMFCColorPickerCtrl : public CButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMFCColorPickerCtrl::CMFCColorPickerCtrl](#cmfccolorpickerctrl)|Vytvoří `CMFCColorPickerCtrl` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMFCColorPickerCtrl::GetColor](#getcolor)|Zjišťuje barvu, kterou uživatel vybere.|
|[CMFCColorPickerCtrl::GetHLS](#gethls)|Načte hodnoty hue, světelnost a sytost barev, které uživatel vybere.|
|[CMFCColorPickerCtrl::GetHue](#gethue)|Obnoví komponenty odstín barvy, kterou uživatel vybere.|
|[CMFCColorPickerCtrl::GetLuminance](#getluminance)|Obnoví komponenty jasu barvy, kterou uživatel vybere.|
|[CMFCColorPickerCtrl::GetSaturation](#getsaturation)|Obnoví komponenty sytost barev, které uživatel vybere.|
|[CMFCColorPickerCtrl::SelectCellHexagon](#selectcellhexagon)|Nastaví aktuální barvu na barvu definované zadané součásti barva RGB nebo zadaná buňka šestiúhelník.|
|[CMFCColorPickerCtrl::SetColor](#setcolor)|Nastaví zadanou hodnotu barvy RGB aktuální barvu.|
|[CMFCColorPickerCtrl::SetHLS](#sethls)|Nastaví aktuální barvu na zadanou hodnotu barvy HLS.|
|[CMFCColorPickerCtrl::SetHue](#sethue)|Komponenta odstín, který aktuálně vybraná barva se změní.|
|[CMFCColorPickerCtrl::SetLuminance](#setluminance)|Komponenta světelnost aktuálně vybraná barva se změní.|
|[CMFCColorPickerCtrl::SetLuminanceBarWidth](#setluminancebarwidth)|Šířka pruhu světelnost nastaví v ovládacím prvku pro výběr barvy.|
|[CMFCColorPickerCtrl::SetOriginalColor](#setoriginalcolor)|Nastaví počáteční barvu vybrané.|
|[CMFCColorPickerCtrl::SetPalette](#setpalette)|Nastaví aktuální palety barev.|
|[CMFCColorPickerCtrl::SetSaturation](#setsaturation)|Sytost součást aktuálně vybraná barva se změní.|
|[CMFCColorPickerCtrl::SetType](#settype)|Nastaví typ ovládacího prvku pro výběr barev k zobrazení.|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[CMFCColorPickerCtrl::DrawCursor](#drawcursor)|Volá se rozhraním, než se zobrazí kurzor, který odkazuje na vybraném barevném.|

## <a name="remarks"></a>Poznámky

Standardní barvy jsou vybrány z palety barev šestiúhelníkový a vlastních barev jsou vybrány z panelu světelnost tam, kde jsou barvy definované pomocí notace červená, zelená/modrá nebo zápis hue/satuaration/světelnost.

Následující obrázek znázorňuje několik `CMFCColorPickerCtrl` objekty.

![Dialogové okno CMFCColorPickerCtrl](../../mfc/reference/media/colorpicker.png "CMFCColorPickerCtrl – dialogové okno")

`CMFCColorPickerCtrl` Podporuje dvě dvojice stylů. HEX a HEX_GREYSCALE styly jsou vhodné pro výběr standardní barvy. Výběr a SVĚTLOSTI styly jsou vhodné pro výběr vlastní barvy.

Proveďte následující kroky, abyste zapracovali `CMFCColorPickerCtrl` řízení na vašem dialogovém okně:

1. Pokud používáte **ClassWizard**, vložte nový ovládací prvek tlačítko do vaší šablony dialogového okna (protože `CMFCColorPickerCtrl` třída dědí z `CButton` třídy).

1. Vložte členské proměnné, která souvisí s nový ovládací prvek tlačítko do vaší třídy dialogového okna. Potom změnit typ proměnné z `CButton` k `CMFCColorPickerCtrl`.

1. Vložit `WM_INITDIALOG` obslužné rutiny zpráv pro třídy dialogového okna. V obslužné rutině nastavit typ, palety a počáteční vybranou barvu `CMFCColorPickerCtrl` ovládacího prvku.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak nakonfigurovat `CMFCColorPickerCtrl` pomocí různých metod v objektu `CMFCColorPickerCtrl` třídy. Příklad ukazuje, jak nastavit typ ovládacího prvku pro výběr a jak nastavit její barvu, hue, světelnost a sytost. V příkladu je součástí [nové ovládací prvky ukázka](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#4](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#5](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcolorpickerctrl.h

##  <a name="cmfccolorpickerctrl"></a>  CMFCColorPickerCtrl::CMFCColorPickerCtrl

Vytvoří `CMFCColorPickerCtrl` objektu.

```
CMFCColorPickerCtrl();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="drawcursor"></a>  CMFCColorPickerCtrl::DrawCursor

Volá se rozhraním, než se zobrazí kurzor, který odkazuje na vybraném barevném.

```
virtual void DrawCursor(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Ukazatel na kontext zařízení.

*Rect*<br/>
[in] Určuje obdélníkovou oblast kolem vybrané barvy.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu, když budete chtít změnit tvar, který odkazuje na vybraném barevném kurzor.

##  <a name="getcolor"></a>  CMFCColorPickerCtrl::GetColor

Zjišťuje barvu, kterou uživatel vybere.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota vybraná barva RGB.

### <a name="remarks"></a>Poznámky

##  <a name="gethls"></a>  CMFCColorPickerCtrl::GetHLS

Načte hodnoty hue, světelnost a sytost barev, které uživatel vybere.

```
void GetHLS(
    double* hue,
    double* luminance,
    double* saturation);
```

### <a name="parameters"></a>Parametry

*HUE*<br/>
[out] Ukazatel na proměnnou typu double, která přijímá informace odstín.

*Světlosti*<br/>
[out] Ukazatel na proměnnou typu double, která přijímá informace světelnost.

*Sytost*<br/>
[out] Ukazatel na proměnnou typu double, která přijímá sytost informace.

### <a name="remarks"></a>Poznámky

##  <a name="gethue"></a>  CMFCColorPickerCtrl::GetHue

Obnoví komponenty odstín barvy, kterou uživatel vybere.

```
double GetHue() const;
```

### <a name="return-value"></a>Návratová hodnota

Odstín, který je součást vybraná barva.

### <a name="remarks"></a>Poznámky

##  <a name="getluminance"></a>  CMFCColorPickerCtrl::GetLuminance

Obnoví komponenty jasu barvy, kterou uživatel vybere.

```
double GetLuminance() const;
```

### <a name="return-value"></a>Návratová hodnota

Komponenta světelnost vybranou barvu.

### <a name="remarks"></a>Poznámky

##  <a name="getsaturation"></a>  CMFCColorPickerCtrl::GetSaturation

Načte hodnotu sytost barev, které uživatel vybere.

```
double GetSaturation() const;
```

### <a name="return-value"></a>Návratová hodnota

Komponenta sytost vybranou barvu.

### <a name="remarks"></a>Poznámky

##  <a name="selectcellhexagon"></a>  CMFCColorPickerCtrl::SelectCellHexagon

Nastaví aktuální barvu na barvu definované zadané součásti barva RGB nebo zadaná buňka šestiúhelník.

```
void SelectCellHexagon(
    BYTE R,
    BYTE G,
    BYTE B);

BOOL SelectCellHexagon(
    int x,
    int y);
```

### <a name="parameters"></a>Parametry

*R*<br/>
[in] Komponenta červenou barvou.

*G*<br/>
[in] Zelenou barvu, která komponenta.

*B*<br/>
[in] Komponenta modrou barvou.

*x*<br/>
[in] Souřadnice x kurzoru, která odkazuje na šestiúhelník buňky.

*y*<br/>
[in] Souřadnice y kurzoru, která odkazuje na šestiúhelník buňky.

### <a name="return-value"></a>Návratová hodnota

Druhé přetížení této metody vždy vrátí hodnotu FALSE.

### <a name="remarks"></a>Poznámky

První přetížení této metody nastaví aktuální barvu na barvu, která odpovídá ovládacího prvku pro výběr barvy určené komponenty červené, zelené a modré barvu.

Druhé přetížení této metody nastaví aktuální barvu na barvu šestiúhelník buňky, které ukazuje pomocí umístění zadaného kurzoru.

##  <a name="setcolor"></a>  CMFCColorPickerCtrl::SetColor

Nastaví zadanou hodnotu barvy RGB aktuální barvu.

```
void SetColor(COLORREF Color);
```

### <a name="parameters"></a>Parametry

*Barva*<br/>
[in] Hodnota barvy RGB.

### <a name="remarks"></a>Poznámky

##  <a name="sethls"></a>  CMFCColorPickerCtrl::SetHLS

Nastaví aktuální barvu na zadanou hodnotu barvy HLS.

```
void SetHLS(
    double hue,
    double luminance,
    double saturation,
    BOOL bInvalidate=TRUE);
```

### <a name="parameters"></a>Parametry

*HUE*<br/>
[in] Hue hodnotu.

*Světlosti*<br/>
[in] Hodnota, světelnost.

*Sytost*<br/>
[in] Sytost hodnotu.

*bInvalidate*<br/>
[in] TRUE, pokud chcete vynutit v okně se okamžitě aktualizovat na novou barvu; v opačném případě hodnota FALSE. Výchozí hodnota je TRUE.

### <a name="remarks"></a>Poznámky

##  <a name="sethue"></a>  CMFCColorPickerCtrl::SetHue

Hue aktuálně vybraná barva se změní.

```
void SetHue(double Hue);
```

### <a name="parameters"></a>Parametry

*HUE*<br/>
[in] Hue hodnotu.

### <a name="remarks"></a>Poznámky

##  <a name="setluminance"></a>  CMFCColorPickerCtrl::SetLuminance

Změní světelnost aktuálně vybranou barvu.

```
void SetLuminance(double Luminance);
```

### <a name="parameters"></a>Parametry

*Světlosti*<br/>
[in] Hodnota, světelnost.

### <a name="remarks"></a>Poznámky

##  <a name="setluminancebarwidth"></a>  CMFCColorPickerCtrl::SetLuminanceBarWidth

Šířka pruhu světelnost nastaví v ovládacím prvku pro výběr barvy.

```
void SetLuminanceBarWidth(int w);
```

### <a name="parameters"></a>Parametry

*w*<br/>
[in] Šířka pruhu světelnost měřená v pixelech.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete změnit velikost panelu světelnost, který je na **vlastní** kartu ovládacího prvku pro výběr barvy. *w* parametr určuje novou šířku panelu světelnost. Hodnota šířky se ignoruje, pokud se překročí tři čtvrtiny Šířka oblasti klienta.

##  <a name="setoriginalcolor"></a>  CMFCColorPickerCtrl::SetOriginalColor

Nastaví počáteční barvu vybrané.

```
void SetOriginalColor(COLORREF ref);
```

### <a name="parameters"></a>Parametry

*ref*<br/>
[in] Hodnota barvy RGB.

### <a name="remarks"></a>Poznámky

Tuto metodu volejte, když se inicializuje ovládací prvek Výběr barvy.

##  <a name="setpalette"></a>  CMFCColorPickerCtrl::SetPalette

Nastaví aktuální palety barev.

```
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>Parametry

*pPalette*<br/>
[in] Ukazatel na paletu barev.

### <a name="remarks"></a>Poznámky

Palety barev definuje pole barev, které se zobrazí v ovládacím prvku pro výběr barvy.

##  <a name="setsaturation"></a>  CMFCColorPickerCtrl::SetSaturation

Sytost aktuálně vybraná barva se změní.

```
void SetSaturation(double Saturation);
```

### <a name="parameters"></a>Parametry

*Sytost*<br/>
[in] Sytost hodnotu.

### <a name="remarks"></a>Poznámky

##  <a name="settype"></a>  CMFCColorPickerCtrl::SetType

Nastaví typ ovládacího prvku pro výběr barev k zobrazení.

```
void SetType(COLORTYPE colorType);
```

### <a name="parameters"></a>Parametry

*colorType*<br/>
[in] Typ ovládacího prvku pro výběr barvy.

Typy jsou definovány `CMFCColorPickerCtrl::COLORTYPE` výčtu. Možné typy jsou SVĚTELNOST, výběr, HEX a HEX_GREYSCALE. Výchozí typ je výběr.

### <a name="remarks"></a>Poznámky

Chcete-li určit typ ovládacího prvku pro výběr barev, volejte tuto metodu, před vytvořením ovládacím prvku Windows.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorDialog – třída](../../mfc/reference/cmfccolordialog-class.md)
