---
title: Třída CMFCColorPickerCtrl
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
ms.openlocfilehash: fe35ee5d6fc6484788a2636151c386689f4bdd96
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752532"
---
# <a name="cmfccolorpickerctrl-class"></a>Třída CMFCColorPickerCtrl

Třída `CMFCColorPickerCtrl` poskytuje funkce pro ovládací prvek, který se používá k výběru barev.

## <a name="syntax"></a>Syntaxe

```
class CMFCColorPickerCtrl : public CButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCColorPickerCtrl::CMFCColorPickerCtrl](#cmfccolorpickerctrl)|Vytvoří `CMFCColorPickerCtrl` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCColorPickerCtrl::GetColor](#getcolor)|Načte barvu, kterou uživatel vybere.|
|[CMFCColorPickerCtrl::GetHLS](#gethls)|Načte hodnoty odstínu, jasu a sytosti barvy, kterou uživatel vybere.|
|[CMFCColorPickerCtrl::GetHue](#gethue)|Načte komponentu odstínu barvy, kterou uživatel vybere.|
|[CMFCColorPickerCtrl:GetLuminance](#getluminance)|Načte složku jasu barvy, kterou uživatel vybere.|
|[CMFCColorPickerCtrl::Možnost Saturace](#getsaturation)|Načte složku sytosti barvy, kterou uživatel vybere.|
|[CMFCColorPickerCtrl::SelectCellHexagon](#selectcellhexagon)|Nastaví aktuální barvu na barvu definovanou zadanými barevnými složkami RGB nebo zadaným šestiúhelníkem buňky.|
|[CMFCColorPickerCtrl::SetColor](#setcolor)|Nastaví aktuální barvu na zadanou hodnotu barvy RGB.|
|[CMFCColorPickerCtrl::SetHLS](#sethls)|Nastaví aktuální barvu na zadanou hodnotu barvy HLS.|
|[CMFCColorPickerCtrl::SetHue](#sethue)|Změní složku odstínu aktuálně vybrané barvy.|
|[CMFCColorPickerCtrl:SetLuminance](#setluminance)|Změní složku jasu aktuálně vybrané barvy.|
|[CMFCColorPickerCtrl::SetLuminanceBarWidth](#setluminancebarwidth)|Nastaví šířku pruhu jasu v ovládacím prvku pro výběr barvy.|
|[CMFCColorPickerCtrl::SetOriginalColor](#setoriginalcolor)|Nastaví počáteční vybranou barvu.|
|[CMFCColorPickerCtrl::SetPalette](#setpalette)|Nastaví aktuální paletu barev.|
|[CMFCColorPickerCtrl:SetSaturace](#setsaturation)|Změní složku sytosti aktuálně vybrané barvy.|
|[CMFCColorPickerCtrl::SetType](#settype)|Nastaví typ ovládacího prvku pro výběr barev, který se má zobrazit.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CMFCColorPickerCtrl::DrawCursor](#drawcursor)|Volat rámci před kurzor, který odkazuje na vybranou barvu se zobrazí.|

## <a name="remarks"></a>Poznámky

Standardní barvy jsou vybrány z šestihranné palety barev a vlastní barvy jsou vybrány z pruhu jasu, kde jsou barvy určeny buď červenou/zelenou/modrou notací nebo zápisem odstínu/sytosti/jasu.

Následující obrázek znázorňuje několik `CMFCColorPickerCtrl` objektů.

![Dialogové okno CMFCColorPickerCtrl](../../mfc/reference/media/colorpicker.png "Dialogové okno CMFCColorPickerCtrl")

Podporuje `CMFCColorPickerCtrl` dva páry stylů. Styly HEX a HEX_GREYSCALE jsou vhodné pro standardní výběr barev. Styly PICKER a LUMINANCE jsou vhodné pro vlastní výběr barev.

Chcete-li ovládací prvek `CMFCColorPickerCtrl` začlenit do dialogového okna, proveďte následující kroky:

1. Pokud používáte **ClassWizard**, vložte nový ovládací prvek tlačítka `CMFCColorPickerCtrl` do šablony dialogového okna (protože třída je zděděna z `CButton` třídy).

1. Vložte členská proměnnou, která je přidružena k novému ovládacímu prvku tlačítka, do třídy dialogového okna. Potom změňte typ `CButton` `CMFCColorPickerCtrl`proměnné z na .

1. Vložte `WM_INITDIALOG` obslužnou rutinu zprávy pro třídu dialogového okna. V obslužné rutině nastavte typ, `CMFCColorPickerCtrl` paletu a počáteční vybranou barvu ovládacího prvku.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak `CMFCColorPickerCtrl` nakonfigurovat objekt pomocí `CMFCColorPickerCtrl` různých metod ve třídě. Příklad ukazuje, jak nastavit typ ovládacího prvku výběru a jak nastavit jeho barvu, odstín, jas a sytost. Příklad je součástí [ukázky Nové ovládací prvky](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#4](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#5](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcolorpickerctrl.h

## <a name="cmfccolorpickerctrlcmfccolorpickerctrl"></a><a name="cmfccolorpickerctrl"></a>CMFCColorPickerCtrl::CMFCColorPickerCtrl

Vytvoří `CMFCColorPickerCtrl` objekt.

```
CMFCColorPickerCtrl();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfccolorpickerctrldrawcursor"></a><a name="drawcursor"></a>CMFCColorPickerCtrl::DrawCursor

Volat rámci před kurzor, který odkazuje na vybranou barvu se zobrazí.

```
virtual void DrawCursor(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení.

*Rect*<br/>
[v] Určuje obdélníkovou oblast kolem vybrané barvy.

### <a name="remarks"></a>Poznámky

Tuto metodu přepište, když potřebujete změnit tvar kurzoru, který odkazuje na vybranou barvu.

## <a name="cmfccolorpickerctrlgetcolor"></a><a name="getcolor"></a>CMFCColorPickerCtrl::GetColor

Načte barvu, kterou uživatel vybere.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota RGB vybrané barvy.

### <a name="remarks"></a>Poznámky

## <a name="cmfccolorpickerctrlgethls"></a><a name="gethls"></a>CMFCColorPickerCtrl::GetHLS

Načte hodnoty odstínu, jasu a sytosti barvy, kterou uživatel vybere.

```cpp
void GetHLS(
    double* hue,
    double* luminance,
    double* saturation);
```

### <a name="parameters"></a>Parametry

*Odstín*<br/>
[out] Ukazatel na proměnnou typu double, která přijímá informace o odstínu.

*Světlostí*<br/>
[out] Ukazatel na proměnnou typu double, která přijímá informace o svítivosti.

*Sytost*<br/>
[out] Ukazatel na proměnnou typu double, která přijímá informace o sytosti.

### <a name="remarks"></a>Poznámky

## <a name="cmfccolorpickerctrlgethue"></a><a name="gethue"></a>CMFCColorPickerCtrl::GetHue

Načte komponentu odstínu barvy, kterou uživatel vybere.

```
double GetHue() const;
```

### <a name="return-value"></a>Návratová hodnota

Složka odstínu vybrané barvy.

### <a name="remarks"></a>Poznámky

## <a name="cmfccolorpickerctrlgetluminance"></a><a name="getluminance"></a>CMFCColorPickerCtrl:GetLuminance

Načte složku jasu barvy, kterou uživatel vybere.

```
double GetLuminance() const;
```

### <a name="return-value"></a>Návratová hodnota

Složka jasu vybrané barvy.

### <a name="remarks"></a>Poznámky

## <a name="cmfccolorpickerctrlgetsaturation"></a><a name="getsaturation"></a>CMFCColorPickerCtrl::Možnost Saturace

Načte hodnotu sytosti barvy, kterou uživatel vybere.

```
double GetSaturation() const;
```

### <a name="return-value"></a>Návratová hodnota

Složka sytosti vybrané barvy.

### <a name="remarks"></a>Poznámky

## <a name="cmfccolorpickerctrlselectcellhexagon"></a><a name="selectcellhexagon"></a>CMFCColorPickerCtrl::SelectCellHexagon

Nastaví aktuální barvu na barvu definovanou zadanými barevnými složkami RGB nebo zadaným šestiúhelníkem buňky.

```cpp
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
[v] Červená barevná složka.

*G*<br/>
[v] Složka zelené barvy.

*B*<br/>
[v] Modrá barevná složka.

*X*<br/>
[v] Souřadnice x kurzoru, která ukazuje na šestiúhelník buňky.

*Y*<br/>
[v] Souřadnice y kurzoru, která ukazuje na šestiúhelník buňky.

### <a name="return-value"></a>Návratová hodnota

Druhé přetížení této metody vždy vrátí FALSE.

### <a name="remarks"></a>Poznámky

První přetížení této metody nastaví aktuální barvu na barvu, která odpovídá ovládacímu prvku výběru barev zadané červené, zelené a modré barevné komponenty.

Druhé přetížení této metody nastaví aktuální barvu na barvu šestiúhelníku buňky, na kterou se vztahuje zadané umístění kurzoru.

## <a name="cmfccolorpickerctrlsetcolor"></a><a name="setcolor"></a>CMFCColorPickerCtrl::SetColor

Nastaví aktuální barvu na zadanou hodnotu barvy RGB.

```cpp
void SetColor(COLORREF Color);
```

### <a name="parameters"></a>Parametry

*Barev*<br/>
[v] Hodnota barvy RGB.

### <a name="remarks"></a>Poznámky

## <a name="cmfccolorpickerctrlsethls"></a><a name="sethls"></a>CMFCColorPickerCtrl::SetHLS

Nastaví aktuální barvu na zadanou hodnotu barvy HLS.

```cpp
void SetHLS(
    double hue,
    double luminance,
    double saturation,
    BOOL bInvalidate=TRUE);
```

### <a name="parameters"></a>Parametry

*Odstín*<br/>
[v] Hodnota odstínu.

*Světlostí*<br/>
[v] Hodnota jasu.

*Sytost*<br/>
[v] Hodnota sytosti.

*bInvalidate*<br/>
[v] TRUE vynutit okno okamžitě aktualizovat na novou barvu; jinak NEPRAVDA. Výchozí hodnota je TRUE.

### <a name="remarks"></a>Poznámky

## <a name="cmfccolorpickerctrlsethue"></a><a name="sethue"></a>CMFCColorPickerCtrl::SetHue

Změní odstín aktuálně vybrané barvy.

```cpp
void SetHue(double Hue);
```

### <a name="parameters"></a>Parametry

*Odstín*<br/>
[v] Hodnota odstínu.

### <a name="remarks"></a>Poznámky

## <a name="cmfccolorpickerctrlsetluminance"></a><a name="setluminance"></a>CMFCColorPickerCtrl:SetLuminance

Změní svítivost aktuálně vybrané barvy.

```cpp
void SetLuminance(double Luminance);
```

### <a name="parameters"></a>Parametry

*Světlostí*<br/>
[v] Hodnota jasu.

### <a name="remarks"></a>Poznámky

## <a name="cmfccolorpickerctrlsetluminancebarwidth"></a><a name="setluminancebarwidth"></a>CMFCColorPickerCtrl::SetLuminanceBarWidth

Nastaví šířku pruhu jasu v ovládacím prvku pro výběr barvy.

```cpp
void SetLuminanceBarWidth(int w);
```

### <a name="parameters"></a>Parametry

*W*<br/>
[v] Šířka pruhu jasu měřená v obrazových bodech.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte ke změně velikosti pruhu jasu, který je na kartě **Vlastní** ovládacího prvku pro výběr barvy. Parametr *w* určuje novou šířku pruhu jasu. Hodnota šířky je ignorována, pokud přesahuje tři čtvrtiny šířky klientské oblasti.

## <a name="cmfccolorpickerctrlsetoriginalcolor"></a><a name="setoriginalcolor"></a>CMFCColorPickerCtrl::SetOriginalColor

Nastaví počáteční vybranou barvu.

```cpp
void SetOriginalColor(COLORREF ref);
```

### <a name="parameters"></a>Parametry

*ref*<br/>
[v] Hodnota barvy RGB.

### <a name="remarks"></a>Poznámky

Tuto metodu zavolejte při inicializování ovládacího prvku výběru barev.

## <a name="cmfccolorpickerctrlsetpalette"></a><a name="setpalette"></a>CMFCColorPickerCtrl::SetPalette

Nastaví aktuální paletu barev.

```cpp
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>Parametry

*pPaleta*<br/>
[v] Ukazatel na paletu barev.

### <a name="remarks"></a>Poznámky

Paleta barev definuje pole barev, které je zobrazeno v ovládacím prvku pro výběr barev.

## <a name="cmfccolorpickerctrlsetsaturation"></a><a name="setsaturation"></a>CMFCColorPickerCtrl:SetSaturace

Změní sytost aktuálně vybrané barvy.

```cpp
void SetSaturation(double Saturation);
```

### <a name="parameters"></a>Parametry

*Sytost*<br/>
[v] Hodnota sytosti.

### <a name="remarks"></a>Poznámky

## <a name="cmfccolorpickerctrlsettype"></a><a name="settype"></a>CMFCColorPickerCtrl::SetType

Nastaví typ ovládacího prvku pro výběr barev, který se má zobrazit.

```cpp
void SetType(COLORTYPE colorType);
```

### <a name="parameters"></a>Parametry

*colorType*<br/>
[v] Typ ovládacího prvku pro výběr barvy.

Typy jsou definovány `CMFCColorPickerCtrl::COLORTYPE` výčtu. Možné typy jsou LUMINANCE, PICKER, HEX a HEX_GREYSCALE. Výchozí typ je PICKER.

### <a name="remarks"></a>Poznámky

Chcete-li určit typ ovládacího prvku pro výběr barvy, zavolejte tuto metodu před vytvořením ovládacího prvku systému Windows.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)
