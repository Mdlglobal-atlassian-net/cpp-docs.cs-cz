---
title: Třída CMFCColorPickerCtrl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ad7e67cc32621fc30108767493c3a7bffd481b68
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33374812"
---
# <a name="cmfccolorpickerctrl-class"></a>CMFCColorPickerCtrl – třída
`CMFCColorPickerCtrl` Třída poskytuje funkce pro ovládací prvek, který slouží k výběru barvy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCColorPickerCtrl : public CButton  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCColorPickerCtrl::CMFCColorPickerCtrl](#cmfccolorpickerctrl)|Vytvoří `CMFCColorPickerCtrl` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCColorPickerCtrl::GetColor](#getcolor)|Načte barvu, která si uživatel vybere.|  
|[CMFCColorPickerCtrl::GetHLS](#gethls)|Načte hodnoty hue, světlostí a sytost barvu, která si uživatel vybere.|  
|[CMFCColorPickerCtrl::GetHue](#gethue)|Načte komponentu odstín barvy, která si uživatel vybere.|  
|[CMFCColorPickerCtrl::GetLuminance](#getluminance)|Načte světlostí součást barvu, která si uživatel vybere.|  
|[CMFCColorPickerCtrl::GetSaturation](#getsaturation)|Načte sytost součást barvu, která si uživatel vybere.|  
|[CMFCColorPickerCtrl::SelectCellHexagon](#selectcellhexagon)|Nastaví barvu aktuální barvu definované komponenty zadaná barva RGB nebo šestiúhelník zadaná buňka.|  
|[CMFCColorPickerCtrl::SetColor](#setcolor)|Nastaví barvu aktuální se zadanou hodnotou barva RGB.|  
|[CMFCColorPickerCtrl::SetHLS](#sethls)|Nastaví barvu aktuální se zadanou hodnotou barva HLS.|  
|[CMFCColorPickerCtrl::SetHue](#sethue)|Změní komponentu hue aktuálně vybrané barvy.|  
|[CMFCColorPickerCtrl::SetLuminance](#setluminance)|Změní komponentu světlostí aktuálně vybrané barvy.|  
|[CMFCColorPickerCtrl::SetLuminanceBarWidth](#setluminancebarwidth)|Šířka pruhu světlostí nastaví v ovládacím prvku pro výběr barev.|  
|[CMFCColorPickerCtrl::SetOriginalColor](#setoriginalcolor)|Nastaví počáteční vybrané barvy.|  
|[CMFCColorPickerCtrl::SetPalette](#setpalette)|Nastaví aktuální palety barev.|  
|[CMFCColorPickerCtrl::SetSaturation](#setsaturation)|Změní komponentu sytost aktuálně vybrané barvy.|  
|[CMFCColorPickerCtrl::SetType](#settype)|Nastaví typ ovládacího prvku pro výběr barev pro zobrazení.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCColorPickerCtrl::DrawCursor](#drawcursor)|Voláno rámcem předtím, než se zobrazí kurzor, který odkazuje na vybrané barvy.|  
  
## <a name="remarks"></a>Poznámky  
 Standardní barvy vybraných z palety barev šestiúhelníkový a vlastní barvy vybraných z panelu světlostí kde barvy jsou definované pomocí notace červená nebo zelená nebo modrá nebo hue/satuaration/světlostí zápis.  
  
 Následující obrázek znázorňuje několik `CMFCColorPickerCtrl` objekty.  
  
 ![Dialogové okno CMFCColorPickerCtrl](../../mfc/reference/media/colorpicker.png "colorpicker")  
  
 `CMFCColorPickerCtrl` Podporuje dvě dvojice stylů. Styly HEX a HEX_GREYSCALE jsou vhodné pro standardní barva výběru. Styly pro výběr a SVĚTLOSTÍ jsou vhodné pro výběr vlastních barev.  
  
 Proveďte následující kroky umožňují začlenění `CMFCColorPickerCtrl` ovládacího prvku do vašeho dialogového okna:  
  
1.  Pokud používáte **ClassWizard**, vložit do šablony pole dialogové okno Nový ovládací prvek tlačítko (protože `CMFCColorPickerCtrl` třída dědí z `CButton` – třída).  
  
2.  Vložte členské proměnné, která souvisí s nový ovládací prvek tlačítko do vaší třídy dialogového okna. Změňte typ proměnné z `CButton` k `CMFCColorPickerCtrl`.  
  
3.  Vložit `WM_INITDIALOG` popisovač zpráv pro třídy dialogového okna. V obslužné rutině nastavení typ, palety a počáteční vybrané barva `CMFCColorPickerCtrl` ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nakonfigurovat `CMFCColorPickerCtrl` objektů pomocí různých metod v `CMFCColorPickerCtrl` třídy. Příklad ukazuje, jak nastavit typ ovládacího prvku pro výběr a jak nastavit barvy, hue, světlostí a sytost. V příkladu je součástí [nové ovládací prvky ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#4](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#5](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
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
 Voláno rámcem předtím, než se zobrazí kurzor, který odkazuje na vybrané barvy.  
  
```  
virtual void DrawCursor(
    CDC* pDC,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDC`  
 Ukazatel na kontextu zařízení.  
  
 [v] `rect`  
 Určuje obdélníkovou oblast kolem vybrané barvy.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu, když potřebujete změnit tvar kurzoru, který odkazuje na vybrané barvy.  
  
##  <a name="getcolor"></a>  CMFCColorPickerCtrl::GetColor  
 Načte barvu, která si uživatel vybere.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota RGB vybrané barvy.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="gethls"></a>  CMFCColorPickerCtrl::GetHLS  
 Načte hodnoty hue, světlostí a sytost barvu, která si uživatel vybere.  
  
```  
void GetHLS(
    double* hue,  
    double* luminance,  
    double* saturation);
```  
  
### <a name="parameters"></a>Parametry  
 [out] `hue`  
 Ukazatel na proměnné typu double, obdrží hue informace.  
  
 [out] `luminance`  
 Ukazatel na proměnné typu double, obdrží světlostí informace.  
  
 [out] `saturation`  
 Ukazatel na proměnné typu double, obdrží sytost informace.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="gethue"></a>  CMFCColorPickerCtrl::GetHue  
 Načte komponentu odstín barvy, která si uživatel vybere.  
  
```  
double GetHue() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hue součást vybrané barvy.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getluminance"></a>  CMFCColorPickerCtrl::GetLuminance  
 Načte světlostí součást barvu, která si uživatel vybere.  
  
```  
double GetLuminance() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Komponenta světlostí vybrané barvy.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getsaturation"></a>  CMFCColorPickerCtrl::GetSaturation  
 Načte hodnotu sytost barvu, která si uživatel vybere.  
  
```  
double GetSaturation() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Komponenta sytost vybrané barvy.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="selectcellhexagon"></a>  CMFCColorPickerCtrl::SelectCellHexagon  
 Nastaví barvu aktuální barvu definované komponenty zadaná barva RGB nebo šestiúhelník zadaná buňka.  
  
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
 [v] `R`  
 Komponenta červenou barvu.  
  
 [v] `G`  
 Komponenta zelenou barvu.  
  
 [v] `B`  
 Komponenta modrou barvu.  
  
 [v] `x`  
 Souřadnice x kurzoru, který odkazuje na šestiúhelníku buňky.  
  
 [v] `y`  
 Souřadnice y kurzoru, který odkazuje na šestiúhelníku buňky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Druhý přetížení tato metoda vždy vrátí hodnotu `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 První přetížení tato metoda nastaví aktuální barvu, která má barvu, která odpovídá ovládacího prvku pro výběr barev je zadán červenou, zelenou a modrou barvu součásti.  
  
 Druhý přetížení tato metoda nastaví barvu aktuální na barvu buňky šestiúhelník, která je nastavena podle umístění zadaná kurzoru.  
  
##  <a name="setcolor"></a>  CMFCColorPickerCtrl::SetColor  
 Nastaví barvu aktuální se zadanou hodnotou barva RGB.  
  
```  
void SetColor(COLORREF Color);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `Color`  
 Hodnotu barva RGB.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="sethls"></a>  CMFCColorPickerCtrl::SetHLS  
 Nastaví barvu aktuální se zadanou hodnotou barva HLS.  
  
```  
void SetHLS(
    double hue,  
    double luminance,  
    double saturation,  
    BOOL bInvalidate=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `hue`  
 Hue hodnota.  
  
 [v] `luminance`  
 Hodnotu světelnosti.  
  
 [v] `saturation`  
 Hodnota sytost.  
  
 [v] `bInvalidate`  
 `TRUE` Chcete-li vynutit okno okamžitě aktualizovat na novou barvu; v opačném `FALSE`. Výchozí hodnota je `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="sethue"></a>  CMFCColorPickerCtrl::SetHue  
 Změní hue aktuálně vybrané barvy.  
  
```  
void SetHue(double Hue);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `Hue`  
 Hue hodnota.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setluminance"></a>  CMFCColorPickerCtrl::SetLuminance  
 Změní světlostí aktuálně vybrané barvy.  
  
```  
void SetLuminance(double Luminance);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `Luminance`  
 Hodnotu světelnosti.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setluminancebarwidth"></a>  CMFCColorPickerCtrl::SetLuminanceBarWidth  
 Šířka pruhu světlostí nastaví v ovládacím prvku pro výběr barev.  
  
```  
void SetLuminanceBarWidth(int w);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `w`  
 Šířka pruhu světlostí měřená v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte ke změně velikosti panelu světlostí, který je na **vlastní** kartě ovládacího prvku pro výběr barev. `w` Parametr určuje nové Šířka pruhu světelnosti. Hodnota width se ignoruje, pokud přesahuje tříčtvrtinovou šířku oblasti klienta.  
  
##  <a name="setoriginalcolor"></a>  CMFCColorPickerCtrl::SetOriginalColor  
 Nastaví počáteční vybrané barvy.  
  
```  
void SetOriginalColor(COLORREF ref);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `ref`  
 Hodnotu barva RGB.  
  
### <a name="remarks"></a>Poznámky  
 Při inicializaci ovládacího prvku pro výběr barev, volejte tuto metodu.  
  
##  <a name="setpalette"></a>  CMFCColorPickerCtrl::SetPalette  
 Nastaví aktuální palety barev.  
  
```  
void SetPalette(CPalette* pPalette);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pPalette`  
 Ukazatel na paletu barev.  
  
### <a name="remarks"></a>Poznámky  
 Palety barev definuje pole barev, které se zobrazí v ovládacím prvku pro výběr barev.  
  
##  <a name="setsaturation"></a>  CMFCColorPickerCtrl::SetSaturation  
 Změní sytost aktuálně vybrané barvy.  
  
```  
void SetSaturation(double Saturation);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `Saturation`  
 Hodnota sytost.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="settype"></a>  CMFCColorPickerCtrl::SetType  
 Nastaví typ ovládacího prvku pro výběr barev pro zobrazení.  
  
```  
void SetType(COLORTYPE colorType);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `colorType`  
 Typ ovládacího prvku pro výběr barev.  
  
 Typy jsou definovány `CMFCColorPickerCtrl::COLORTYPE` výčtu. Možné typy jsou `LUMINANCE`, `PICKER`, `HEX` a `HEX_GREYSCALE`. Je výchozím typem `PICKER`.  
  
### <a name="remarks"></a>Poznámky  
 K určení typu ovládacího prvku pro výběr barev, volejte tuto metodu, před vytvořením ovládacího prvku Windows.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCColorDialog – třída](../../mfc/reference/cmfccolordialog-class.md)
