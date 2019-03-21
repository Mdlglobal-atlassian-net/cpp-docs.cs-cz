---
title: CDrawingManager Class
ms.date: 11/04/2016
f1_keywords:
- CDrawingManager
- AFXDRAWMANAGER/CDrawingManager
- AFXDRAWMANAGER/CDrawingManager::CDrawingManager
- AFXDRAWMANAGER/CDrawingManager::CreateBitmap_32
- AFXDRAWMANAGER/CDrawingManager::DrawAlpha
- AFXDRAWMANAGER/CDrawingManager::DrawRotated
- AFXDRAWMANAGER/CDrawingManager::DrawEllipse
- AFXDRAWMANAGER/CDrawingManager::DrawGradientRing
- AFXDRAWMANAGER/CDrawingManager::DrawRect
- AFXDRAWMANAGER/CDrawingManager::DrawShadow
- AFXDRAWMANAGER/CDrawingManager::Fill4ColorsGradient
- AFXDRAWMANAGER/CDrawingManager::FillGradient
- AFXDRAWMANAGER/CDrawingManager::FillGradient2
- AFXDRAWMANAGER/CDrawingManager::GrayRect
- AFXDRAWMANAGER/CDrawingManager::HighlightRect
- AFXDRAWMANAGER/CDrawingManager::HLStoRGB_ONE
- AFXDRAWMANAGER/CDrawingManager::HLStoRGB_TWO
- AFXDRAWMANAGER/CDrawingManager::HSVtoRGB
- AFXDRAWMANAGER/CDrawingManager::HuetoRGB
- AFXDRAWMANAGER/CDrawingManager::MirrorRect
- AFXDRAWMANAGER/CDrawingManager::PixelAlpha
- AFXDRAWMANAGER/CDrawingManager::PrepareShadowMask
- AFXDRAWMANAGER/CDrawingManager::RGBtoHSL
- AFXDRAWMANAGER/CDrawingManager::RGBtoHSV
- AFXDRAWMANAGER/CDrawingManager::SetAlphaPixel
- AFXDRAWMANAGER/CDrawingManager::SetPixel
- AFXDRAWMANAGER/CDrawingManager::SmartMixColors
helpviewer_keywords:
- CDrawingManager [MFC], CDrawingManager
- CDrawingManager [MFC], CreateBitmap_32
- CDrawingManager [MFC], DrawAlpha
- CDrawingManager [MFC], DrawRotated
- CDrawingManager [MFC], DrawEllipse
- CDrawingManager [MFC], DrawGradientRing
- CDrawingManager [MFC], DrawRect
- CDrawingManager [MFC], DrawShadow
- CDrawingManager [MFC], Fill4ColorsGradient
- CDrawingManager [MFC], FillGradient
- CDrawingManager [MFC], FillGradient2
- CDrawingManager [MFC], GrayRect
- CDrawingManager [MFC], HighlightRect
- CDrawingManager [MFC], HLStoRGB_ONE
- CDrawingManager [MFC], HLStoRGB_TWO
- CDrawingManager [MFC], HSVtoRGB
- CDrawingManager [MFC], HuetoRGB
- CDrawingManager [MFC], MirrorRect
- CDrawingManager [MFC], PixelAlpha
- CDrawingManager [MFC], PrepareShadowMask
- CDrawingManager [MFC], RGBtoHSL
- CDrawingManager [MFC], RGBtoHSV
- CDrawingManager [MFC], SetAlphaPixel
- CDrawingManager [MFC], SetPixel
- CDrawingManager [MFC], SmartMixColors
ms.assetid: 9e4775ca-101b-4aa9-a85a-4d047c701215
ms.openlocfilehash: f14b21c97e5a36d5107e7db526e4153446ae2a01
ms.sourcegitcommit: 90817d9d78fbaed8ffacde63f3add334842e596f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2019
ms.locfileid: "58278528"
---
# <a name="cdrawingmanager-class"></a>CDrawingManager Class

`CDrawingManager` Třída implementuje složité algoritmy kreslení.

## <a name="syntax"></a>Syntaxe

```
class CDrawingManager : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDrawingManager::CDrawingManager](#cdrawingmanager)|Vytvoří `CDrawingManager` objektu.|
|`CDrawingManager::~CDrawingManager`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDrawingManager::CreateBitmap_32](#createbitmap_32)|Vytvoří 32-bit device independent bitmap (DIB), která aplikace může zapisovat přímo.|
|[CDrawingManager::DrawAlpha](#drawalpha)|Zobrazí rastrové obrázky, být transparentní nebo poloprůhledných pixelů.|
|[CDrawingManager::DrawRotated](#drawrotated)|Otočí zdrojový řadič domény obsah uvnitř daného obdélník podle +/-90 stupňů|
|[CDrawingManager::DrawEllipse](#drawellipse)|Nakreslí elipsu s zadané barvy výplně a ohraničení.|
|[CDrawingManager::DrawGradientRing](#drawgradientring)|Nakreslí okruhu a vyplní barev přechodu.|
|[CDrawingManager::DrawLine, CDrawingManager::DrawLineA](#drawline_cdrawingmanager__drawlinea)|Nakreslí čáru.|
|[CDrawingManager::DrawRect](#drawrect)|Kreslení obdélníku zadaného barvy výplně a ohraničení.|
|[CDrawingManager::DrawShadow](#drawshadow)|Vykreslí stín pro obdélníkovou oblast.|
|[CDrawingManager::Fill4ColorsGradient](#fill4colorsgradient)|Vyplní obdélníkovou oblast dva barevné přechody.|
|[CDrawingManager::FillGradient](#fillgradient)|Zadaná barva přechodu vyplní obdélníkovou oblast.|
|[CDrawingManager::FillGradient2](#fillgradient2)|Zadaná barva přechodu vyplní obdélníkovou oblast. Směr Změna barvy přechodu je také zadán.|
|[CDrawingManager::GrayRect](#grayrect)|Vyplní obdélníku zadaného šedou barvu.|
|[CDrawingManager::HighlightRect](#highlightrect)|Zvýrazní obdélníkovou oblast.|
|[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)|Převede barvu z reprezentace HLS RGB reprezentaci.|
|[CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)|Převede barvu z reprezentace HLS RGB reprezentaci.|
|[CDrawingManager::HSVtoRGB](#hsvtorgb)|Převede barvu z reprezentace HSV RGB reprezentaci.|
|[CDrawingManager::HuetoRGB](#huetorgb)|Pomocná metoda, která převede hodnotu aplikace hue do komponenty červené, zelené nebo modrou.|
|[CDrawingManager::MirrorRect](#mirrorrect)|Převrátí obdélníkovou oblast.|
|[CDrawingManager::PixelAlpha](#pixelalpha)|Pomocná metoda, která určuje konečnou barvu pro poloprůhledných pixelů.|
|[CDrawingManager::PrepareShadowMask](#prepareshadowmask)|Vytvoří rastrový obrázek, který může sloužit jako stínu.|
|[CDrawingManager::RGBtoHSL](#rgbtohsl)|Převede barvu z reprezentace RGB HSL reprezentaci.|
|[CDrawingManager::RGBtoHSV](#rgbtohsv)|Převede barvu z reprezentace RGB HSV reprezentaci.|
|[CDrawingManager::SetAlphaPixel](#setalphapixel)|Pomocná metoda, která barvy částečně transparentní pixel v rastrový obrázek.|
|[CDrawingManager::SetPixel](#setpixel)|Pomocná metoda, která se mění na jeden pixel v rastrový obrázek na zadanou barvu.|
|[CDrawingManager::SmartMixColors](#smartmixcolors)|Kombinuje dvě barvy podle vážený poměr.|

## <a name="remarks"></a>Poznámky

`CDrawingManager` Třída poskytuje funkce pro vykreslování stínů, barevné přechody a zvýrazněné obdélníků. Provádí také prolnutí alfa. Tuto třídu můžete použít přímo změnit uživatelského rozhraní aplikace.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)<br/>
`CDrawingManager`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdrawmanager.h

##  <a name="cdrawingmanager"></a>  CDrawingManager::CDrawingManager

Vytvoří [cdrawingmanager –](../../mfc/reference/cdrawingmanager-class.md) objektu.

```
CDrawingManager(CDC& dc);
```

### <a name="parameters"></a>Parametry

*dc*<br/>
[in] Odkaz na kontext zařízení. `CDrawingManager` Používá tento kontext pro kreslení.

##  <a name="createbitmap_32"></a>  CDrawingManager::CreateBitmap_32

Vytvoří 32-bit device independent bitmap (DIB), která aplikace může zapisovat přímo.

```
static HBITMAP __stdcall CreateBitmap_32(
    const CSize& size,
    void** pBits);

static HBITMAP __stdcall CreateBitmap_32(
    HBITMAP bitmap,
    COLORREF clrTransparent = -1);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*Velikost*|[in] A [CSize](../../atl-mfc-shared/reference/csize-class.md) parametr, který označuje velikost rastrového obrázku.|
|*pBits*|[out] Ukazatel na ukazatel na data, která přijímá umístění DIB bitové hodnoty.|
|*bitmap*|Popisovač pro původní rastrový obrázek|
|*clrTransparent*|Hodnota RGB zadání průhlednou barvu původní rastrového obrázku.|

### <a name="return-value"></a>Návratová hodnota

Popisovač do nově vytvořeného DIB bitmapy, pokud tato metoda je úspěšná. v opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

Další informace o tom, jak vytvořit rastrový obrázek DIB najdete v tématu [CreateDIBSection](/windows/desktop/api/wingdi/nf-wingdi-createdibitmap).

##  <a name="drawalpha"></a>  CDrawingManager::DrawAlpha

Zobrazí rastrové obrázky, být transparentní nebo poloprůhledných pixelů.

```
void DrawAlpha(
    CDC* pDstDC,
    const CRect& rectDst,
    CDC* pSrcDC,
    const CRect& rectSrc);
```

### <a name="parameters"></a>Parametry

*pDstDC*<br/>
[in] Ukazatel na kontext zařízení pro cíl.

*rectDst*<br/>
[in] Cílového obdélníku.

*pSrcDC*<br/>
[in] Ukazatel na kontext zařízení pro zdroj.

*rectSrc*<br/>
[in] Zdrojového obdélníku.

### <a name="remarks"></a>Poznámky

Tato metoda provádí alfa blending pro dva bitmapy. Další informace o alfa blending najdete v tématu [AlphaBlend](/windows/desktop/api/wingdi/nf-wingdi-alphablend) v sadě Windows SDK.

##  <a name="drawellipse"></a>  CDrawingManager::DrawEllipse

Nakreslí elipsu s zadané barvy výplně a ohraničení.

```
void DrawEllipse(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[in] Ohraničující obdélník elipsy.

*clrFill*<br/>
[in] Barva, kterou tato metoda používá k Vyplnit elipsu.

*clrLine*<br/>
[in] Barva, kterou tato metoda používá jako ohraničení na tři tečky.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí bez kreslení elipsy, pokud buď barva je nastavena na hodnotu -1. Také vrátí hodnotu bez kreslení elipsy, pokud buď dimenze ohraničující obdélník je 0.

##  <a name="drawgradientring"></a>  CDrawingManager::DrawGradientRing

Nakreslí okruhu a vyplní barev přechodu.

```
BOOL DrawGradientRing(
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    COLORREF colorBorder,
    int nAngle,
    int nWidth,
    COLORREF clrFace = (COLORREF)-1);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[in] A [crect –](../../atl-mfc-shared/reference/crect-class.md) parametr, který určuje hranice pro přechod aktualizačního kanálu.

*colorStart*<br/>
[in] První barva přechodu.

*colorFinish*<br/>
[in] Poslední barva přechodu.

*colorBorder*<br/>
[in] Barva ohraničení.

*nAngle*<br/>
[in] Parametr, který určuje počáteční úhel výkresu přechodu. Tato hodnota by měla být v rozmezí od 0 do 360.

*nWidth*<br/>
[in] Šířka ohraničení pro kanál.

*clrFace*<br/>
[in] Barva vnitřní prstence.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Obdélníku definovaném *rect* musí být alespoň 5 pixelů široký a 5 pixelů.

##  <a name="drawline_cdrawingmanager__drawlinea"></a>  CDrawingManager::DrawLine, CDrawingManager::DrawLineA

Nakreslí čáru.

```
void DrawLine(
    int x1,
    int y1,
    int x2,
    int y2,
    COLORREF clrLine);

void DrawLineA(
    double x1,
    double y1,
    double x2,
    double y2,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*x1*|[in] Souřadnice x, kde začíná na řádku.|
|*y1*|[in] Souřadnice y, kde začíná na řádku.|
|*x2*|[in] Souřadnice x ukončení řádku.|
|*y2*|[in] Souřadnice y ukončení řádku.|
|*clrLine*|[in] Barva čáry.|

### <a name="remarks"></a>Poznámky

Tato metoda selže, pokud *clrLine* rovná -1.

##  <a name="drawrect"></a>  CDrawingManager::DrawRect

Kreslení obdélníku zadaného barvy výplně a ohraničení.

```
void DrawRect(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[in] Hranice obdélníku.

*clrFill*<br/>
[in] Barva, kterou tato metoda používá k vyplnění obdélníku.

*clrLine*<br/>
[in] Barva, kterou tato metoda používá ohraničení obdélníku.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí bez kreslení obdélníku, pokud buď barva je nastavena na hodnotu -1. Také se vrátí, pokud buď dimenze obdélníku je 0.

##  <a name="drawshadow"></a>  CDrawingManager::DrawShadow

Vykreslí stín pro obdélníkovou oblast.

```
BOOL DrawShadow(
    CRect rect,
    int nDepth,
    int iMinBrightness = 100,
    int iMaxBrightness = 50,
    CBitmap* pBmpSaveBottom = NULL,
    CBitmap* pBmpSaveRight = NULL,
    COLORREF clrBase = (COLORREF)-1,
    BOOL bRightShadow = TRUE);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[in] Obdélníkovou oblast ve vaší aplikaci. Kreslení správce nakreslí stínu pod tuto oblast.

*nDepth*<br/>
[in] Šířka a výška stínu.

*iMinBrightness*<br/>
[in] Minimální jas stínu.

*iMaxBrightness*<br/>
[in] Maximální jas stínu.

*pBmpSaveBottom*<br/>
[in] Ukazatel na rastrový obrázek, který obsahuje bitovou kopii pro dolní část stínu.

*pBmpSaveRight*<br/>
[in] Ukazatel na rastrový obrázek, který obsahuje bitovou kopii pro sledování, který je vykreslen na pravé straně obdélníku.

*clrBase*<br/>
[in] Barva stínu.

*bRightShadow*<br/>
[in] Parametr logické hodnoty, která určuje, jak se bude stín vykreslen. Pokud *bRightShadow* je `TRUE`, `DrawShadow` vykreslí stín na pravé straně obdélníku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Pomocí parametrů můžete zadat dva platné rastrové obrázky pro dolní a pravé stíny *pBmpSaveBottom* a *pBmpSaveRight*. Pokud tyto [cbitmap –](../../mfc/reference/cbitmap-class.md) objekty mají připojeného objektu GDI `DrawShadow` použije tyto bitmap jako stínů. Pokud `CBitmap` parametry nemají připojeného objektu GDI `DrawShadow` vykreslí stín a připojí rastrové obrázky na parametry. V budoucích volání `DrawShadow`, můžete zadat tyto rastrové obrázky, ke zrychlení procesu vykreslování. Další informace o `CBitmap` třídy a objekty GDI, naleznete v tématu [grafické objekty](../../mfc/graphic-objects.md).

Pokud platí některá z těchto parametrů `NULL`, `DrawShadow` automaticky vykreslí stín.

Pokud nastavíte *bRightShadow* na hodnotu FALSE, bude vykreslen stínu pod a nalevo od oblasti obdélníkový.

### <a name="example"></a>Příklad

Následující příklad ukazuje způsob použití `DrawShadow` metodu `CDrawingManager` třídy. Tento fragment kódu je součástí [Prop list demonstrační ukázka](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_PropSheetDemo#1](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_1.cpp)]

##  <a name="fill4colorsgradient"></a>  CDrawingManager::Fill4ColorsGradient

Vyplní obdélníkovou oblast dva barevné přechody.

```
void Fill4ColorsGradient(
    CRect rect,
    COLORREF colorStart1,
    COLORREF colorFinish1,
    COLORREF colorStart2,
    COLORREF colorFinish2,
    BOOL bHorz = TRUE,
    int nPercentage = 50);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[in] Obdélník tak, aby vyplnil.

*colorStart1*<br/>
[in] Počáteční barva přechodu první barva.

*colorFinish1*<br/>
[in] Konečná Barva první barva přechodu.

*colorStart2*<br/>
[in] Počáteční barva druhý barev přechodu.

*colorFinish2*<br/>
[in] Konečná barva druhá barva přechodu.

*bHorz*<br/>
[in] Parametr logické hodnoty označující, zda `Fill4ColorsGradient` barvy přechodu vodorovně nebo svisle. Hodnota TRUE Určuje vodorovný přechod.

*nPercentage*<br/>
[in] Celé číslo od 0 do 100. Tato hodnota informuje o procentu obdélník s první barva přechodu výplně.

### <a name="remarks"></a>Poznámky

Když dva barevné přechody je vyplněna obdélníku, se nachází nad sebe nebo další k sobě navzájem, závisí na hodnotě *bHorz*. Každá barva přechodu se počítá samostatně pomocí metody [CDrawingManager::FillGradient](#fillgradient).

Tato metoda generuje selhání kontrolního výrazu, pokud *nPercentage* je menší než 0 nebo více než 100.

##  <a name="fillgradient"></a>  CDrawingManager::FillGradient

Zadaná barva přechodu vyplní obdélníkovou oblast.

```
void FillGradient(
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    BOOL bHorz = TRUE,
    int nStartFlatPercentage = 0,
    int nEndFlatPercentage = 0);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[in] Obdélníkovou oblast k vyplnění.

*colorStart*<br/>
[in] První barva přechodu.

*colorFinish*<br/>
[in] Konečná barva přechodu.

*bHorz*<br/>
[in] Parametr logické hodnoty, která určuje, zda `FillGradient` vykreslovat vodorovný nebo svislý přechod.

*nStartFlatPercentage*<br/>
[in] Procento obdélníku, který `FillGradient` vyplní *colorStart* před spuštěním přechodu.

*nEndFlatPercentage*<br/>
[in] Procento obdélníku, který `FillGradient` vyplní *colorFinish* po jejím dokončení přechodu.

### <a name="example"></a>Příklad

Následující příklad ukazuje způsob použití `FillGradient` metodu `CDrawingManager` třídy. Tento fragment kódu je součástí [MS Office 2007 demonstrační ukázka](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#12](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_2.cpp)]

##  <a name="fillgradient2"></a>  CDrawingManager::FillGradient2

Zadaná barva přechodu vyplní obdélníkovou oblast.

```
void FillGradient2 (
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    int nAngle = 0);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[in] Obdélníkovou oblast k vyplnění.

*colorStart*<br/>
[in] První barvou přechodu.

*colorFinish*<br/>
[in] Poslední barva přechodu.

*nAngle*<br/>
[in] Celé číslo od 0 do 360. Tento parametr určuje směr barev přechodu.

### <a name="remarks"></a>Poznámky

Použití *nAngle* k určení směru barev přechodu. Při zadávání směr barvy také určit, kde začíná barev přechodu. Hodnota 0 pro *nAngle* informuje o přechodu začne z horní části obdélníku. Jako *nAngle* zvyšuje, počáteční umístění pro přesun přechodu podle úhel proti směru hodinových ručiček směrem.

### <a name="example"></a>Příklad

Následující příklad ukazuje způsob použití `FillGradient2` metodu `CDrawingManager` třídy. Tento fragment kódu je součástí [nové ovládací prvky ukázka](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#37](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_3.cpp)]

##  <a name="grayrect"></a>  CDrawingManager::GrayRect

Vyplní obdélníku zadaného šedou barvu.

```
BOOL GrayRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    COLORREF clrDisabled = (COLORREF)-1);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[in] Obdélníkovou oblast k vyplnění.

*nPercentage*<br/>
[in] Procento šedá, které chcete v obdélníku.

*clrTransparent*<br/>
[in] Průhledná barva.

*clrDisabled*<br/>
[in] Barva, která používá tuto metodu pro uvolnění sytost, pokud *nPercentage* je nastavena na hodnotu -1.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud metoda byla úspěšná. v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Pro parametr *nPercentage*, nižší hodnota znamená tmavší barev.

Maximální hodnota *nPercentage* je 200. Větší hodnota než 200 nedojde ke změně vzhledu rámečku. Pokud je hodnota -1, tato metoda používá *clrDisabled* omezit sytost obdélníku.

##  <a name="highlightrect"></a>  CDrawingManager::HighlightRect

Zvýrazní obdélníkovou oblast.

```
BOOL HighlightRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    int nTolerance = 0,
    COLORREF clrBlend = (COLORREF)-1);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[in] Obdélníkovou oblast, abyste měli na očích.

*nPercentage*<br/>
[in] Procento, která určuje, jak transparentní by měl být zvýraznění.

*clrTransparent*<br/>
[in] Průhledná barva.

*nTolerance*<br/>
[in] Celé číslo mezi 0 a 255, která určuje barvu proti chybám.

*clrBlend*<br/>
[in] Základní barva prolnutí.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je metoda úspěšná. v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Pokud *nPercentage* je mezi 0 a 99, `HighlightRect` používá alfa míchání algoritmus. Další informace o alfa míchání najdete v tématu [alfa míchání čar a výplní](/dotnet/framework/winforms/advanced/alpha-blending-lines-and-fills). Pokud *nPercentage* -1, je tato metoda používá výchozí úroveň zvýraznění. Pokud *nPercentage* 100, tato metoda neprovede žádnou akci a vrátí hodnotu TRUE.

Metoda používá parametr *nTolerance* k určení, jestli chcete zvýraznit oblasti obdélníkový. Abyste měli na očích obdélník rozdíl mezi barvu pozadí vaší aplikace a *clrTransparent* musí být menší než *nTolerance* v každou složku barvy (červené, zelené a modré).

##  <a name="hlstorgb_one"></a>  CDrawingManager::HLStoRGB_ONE

Převede barvu z reprezentace HLS RGB reprezentaci.

```
static COLORREF __stdcall HLStoRGB_ONE(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>Parametry

*H*<br/>
[in] Číslo mezi 0 a 1, který představuje odstín barvy.

*L*<br/>
[in] Číslo mezi 0 a 1, která označuje světelnost pro barvu.

*S*<br/>
[in] Číslo mezi 0 a 1 určující sytost pro barvu.

### <a name="return-value"></a>Návratová hodnota

Reprezentuje RGB barvu HLS k dispozici.

### <a name="remarks"></a>Poznámky

Barvy může být reprezentován jako HSV (odstín, sytost a hodnota), HSL (hue, sytosti a světlosti) nebo RGB (červené, zelené a modré). Další informace o různých reprezentace barvy, naleznete v tématu [barva](/windows/desktop/uxguide/vis-color).

Tato metoda a `CDrawingManager::HLStoRGB_TWO` metoda provádět stejnou operaci, ale vyžadují různé hodnoty *H* parametru. V této metodě *H* je procento kruhu. V `CDrawingManager::HLStoRGB_TWO` metody *H* míru hodnota od 0 do 360, které obě představují červenou. Třeba index Mei `HLStoRGB_ONE`, hodnota 0,25 pro *H* je rovna hodnotě 90 s `HLStoRGB_TWO`.

##  <a name="hlstorgb_two"></a>  CDrawingManager::HLStoRGB_TWO

Převede barvu z reprezentace HLS RGB reprezentaci.

```
static COLORREF __stdcall HLStoRGB_TWO(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>Parametry

*H*<br/>
[in] Číslo od 0 do 360, které představuje odstín barvy.

*L*<br/>
[in] Číslo mezi 0 a 1, která označuje světelnost pro barvu.

*S*<br/>
[in] Číslo mezi 0 a 1 určující sytost pro barvu.

### <a name="return-value"></a>Návratová hodnota

Reprezentuje RGB barvu HLS k dispozici.

### <a name="remarks"></a>Poznámky

Barvy může být reprezentován jako HSV (odstín, sytost a hodnota), HSL (hue, sytosti a světlosti) nebo RGB (červené, zelené a modré). Další informace o různých reprezentace barvy, naleznete v tématu [barva](/windows/desktop/uxguide/vis-color).

Tato metoda a [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one) metoda provádět stejnou operaci, ale vyžadují různé hodnoty *H* parametru. V této metodě *H* míru hodnota od 0 do 360, které obě představují červenou. V [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one) metody *H* je procento kruhu. Třeba index Mei `HLStoRGB_ONE`, hodnota 0,25 pro *H* je rovna hodnotě 90 s `HLStoRGB_TWO`.

##  <a name="hsvtorgb"></a>  CDrawingManager::HSVtoRGB

Převede barvu z reprezentace HSV RGB reprezentaci.

```
static COLORREF __stdcall HSVtoRGB(
    double H,
    double S,
    double V);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*H*|[in] Číslo od 0 do 360, která určuje odstín barvy.|
|*S*|[in] Číslo mezi 0 a 1 určující sytost pro barvu.|
|*V*|[in] Číslo mezi 0 a 1, která určuje hodnotu barvy.|

### <a name="return-value"></a>Návratová hodnota

Reprezentuje RGB barvu HSV k dispozici.

### <a name="remarks"></a>Poznámky

Barvy může být reprezentován jako HSV (odstín, sytost a hodnota), HSL (hue, sytosti a světlosti) nebo RGB (červené, zelené a modré). Další informace o různých reprezentace barvy, naleznete v tématu [barva](/windows/desktop/uxguide/vis-color).

##  <a name="huetorgb"></a>  CDrawingManager::HuetoRGB

Převede hodnotu hue do komponenty červené, zelené nebo modrou.

```
static double __stdcall HuetoRGB(
    double m1,
    double m2,
    double h);

static BYTE __stdcall HueToRGB(
    float rm1,
    float rm2,
    float rh);
```

### <a name="parameters"></a>Parametry

*m1*<br/>
[in] Viz poznámky.

*m2*<br/>
[in] Viz poznámky.

*h*<br/>
[in] Viz poznámky.

*rm1*<br/>
[in] Viz poznámky.

*rm2*<br/>
[in] Viz poznámky.

*rh*<br/>
[in] Viz poznámky.

### <a name="return-value"></a>Návratová hodnota

Jednotlivé červenou, zelenou nebo modré komponenta pro zadaný odstín.

### <a name="remarks"></a>Poznámky

Tato metoda je pomocná metoda, která `CDrawingManager` třídy používá k výpočtu jednotlivé komponenty červené, zelené a modré barvy v HSV nebo HSL reprezentaci. Tato metoda není určená k volání přímo programátorem. Vstupní parametry jsou hodnoty, které jsou závislé na algoritmu převodu.

Převést barvu HSV nebo HSL na reprezentaci RGB, volání jedné z následujících metod:

- [CDrawingManager::HSVtoRGB](#hsvtorgb)

- [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)

- [CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)

##  <a name="mirrorrect"></a>  CDrawingManager::MirrorRect

Převrátí obdélníkovou oblast.

```
void MirrorRect(
    CRect rect,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[in] Ohraničující obdélník oblasti k převrácení

*bHorz*<br/>
[in] Parametr logické hodnoty označující, zda obdélník převrátí vodorovně nebo svisle.

### <a name="remarks"></a>Poznámky

Tuto metodu přepnout libovolnou oblast kontextu zařízení ve vlastnictví `CDrawingManager` třídy. Pokud *bHorz* je nastavena na hodnotu TRUE, tato metoda převrátí oblasti vodorovně. V opačném případě se Překlopí oblasti svisle.

##  <a name="pixelalpha"></a>  CDrawingManager::PixelAlpha

Vypočítá konečnou barvu pro poloprůhledných pixelů.

```
static COLORREF __stdcall PixelAlpha(
    COLORREF srcPixel,
    int percent);

static COLORREF __stdcall PixelAlpha(
    COLORREF srcPixel,
    double percentR,
    double percentG,
    double percentB);

static COLORREF __stdcall PixelAlpha(
    COLORREF srcPixel,
    COLORREF dstPixel,
    int percent);
```

### <a name="parameters"></a>Parametry

*srcPixel*<br/>
[in] Počáteční barva je pixel.

*percent*<br/>
[in] Číslo mezi 0 a 100, které představuje procento průhlednost. Hodnota 100 značí, že je počáteční barva zcela transparentní.

*percentR*<br/>
[in] Číslo mezi 0 a 100, které představuje procentuální hodnotu průhlednosti pro červené.

*percentG*<br/>
[in] Číslo mezi 0 a 100, které představuje procentuální hodnotu průhlednosti pro zelené.

*percentB*<br/>
[in] Číslo mezi 0 a 100, které představuje procentuální hodnotu průhlednosti pro modré.

*dstPixel*<br/>
[in] Základní barva je pixel.

### <a name="return-value"></a>Návratová hodnota

Konečná barva poloprůhledných pixelů.

### <a name="remarks"></a>Poznámky

Toto je pomocná třída pro barevné zvýrazňování poloprůhledných rastrové obrázky a není určena k volání přímo programátorem.

Pokud používáte verzi metody, která má *dstPixel*, konečnou barvu je kombinací *dstPixel* a *srcPixel*. *SrcPixel* barva je částečně průhlednou barvu nad základní barva *dstPixel*.

##  <a name="prepareshadowmask"></a>  CDrawingManager::PrepareShadowMask

Vytvoří rastrový obrázek, který může sloužit jako stínu.

```
static HBITMAP __stdcall PrepareShadowMask (
    int nDepth,
    COLORREF clrBase,
    int iMinBrightness = 0,
    int iMaxBrightness = 100);
```

### <a name="parameters"></a>Parametry

*nDepth*<br/>
[in] Šířka a výška stínu.

*clrBase*<br/>
[in] Barva stínu.

*iMinBrightness*<br/>
[in] Minimální jas stínu.

*iMaxBrightness*<br/>
[in] Maximální jas stínu.

### <a name="return-value"></a>Návratová hodnota

Popisovač pro vytvořený rastrového obrázku, pokud tato metoda je úspěšná. v opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

Pokud *nDepth* je nastaveno na 0, tato metoda se ukončí a vrátí hodnotu NULL. Pokud *nDepth* je menší než 3, šířku a výšku stínu jsou nastaveny na 3 pixelů.

##  <a name="rgbtohsl"></a>  CDrawingManager::RGBtoHSL

Převede barvu z reprezentace červené, zelené a modré (RGB) na odstín, sytosti a světlosti (HSL) reprezentace.

```
static void __stdcall RGBtoHSL(
    COLORREF rgb,
    double* H,
    double* S,
    double* L);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*rgb*|[in] Barva RGB hodnoty.|
|*H*|[out] Ukazatel na hodnotu double, kde Metoda ukládá odstín barvy.|
|*S*|[out] Ukazatel na hodnotu double, kde Metoda ukládá sytost pro barvu.|
|*L*|[out] Ukazatel na hodnotu double, kde Metoda ukládá světlosti barvy.|

### <a name="remarks"></a>Poznámky

Barvy může být reprezentován jako HSV (odstín, sytost a hodnota), HSL (hue, sytosti a světlosti) nebo RGB (červené, zelené a modré). Další informace o různých reprezentace barvy, naleznete v tématu [barva](/windows/desktop/uxguide/vis-color).

Vrácená hodnota pro *H* je reprezentována jako desetinné číslo mezi 0 a 1, kde 0 a 1 představují červenou. Vrácené hodnoty pro *S* a *L* jsou čísla od 0 do 1.

##  <a name="rgbtohsv"></a>  CDrawingManager::RGBtoHSV

Převede barvu z reprezentace RGB HSV reprezentaci.

```
static void __stdcall RGBtoHSV(
    COLORREF rgb,
    double* H,
    double* S,
    double* V);
```

### <a name="parameters"></a>Parametry

*rgb*<br/>
[in] Barva pro převod v reprezentaci RGB.

*H*<br/>
[out] Ukazatel na hodnotu double, kde tato metoda ukládá výsledný odstín barvy.

*S*<br/>
[out] Ukazatel na hodnotu double, kde tato metoda ukládá výsledný sytost pro barvu.

*V*<br/>
[out] Ukazatel na hodnotu double, kde tato metoda ukládá výsledná hodnota barvy.

### <a name="remarks"></a>Poznámky

Barvy může být reprezentován jako HSV (odstín, sytost a hodnota), HSL (hue, sytosti a světlosti) nebo RGB (červené, zelené a modré). Další informace o různých reprezentace barvy, naleznete v tématu [barva](/windows/desktop/uxguide/vis-color).

Vrácená hodnota pro *H* je číslo v rozsahu od 0 do 360, kde 0 až 360 označuje červenou. Vrácení hodnoty *S* a *V* jsou čísla od 0 do 1.

##  <a name="setalphapixel"></a>  CDrawingManager::SetAlphaPixel

Barvy transparentní pixel v rastrový obrázek.

```
static void __stdcall SetAlphaPixel(
    COLORREF* pBits,
    CRect rect,
    int x,
    int y,
    int percent,
    int iShadowSize,
    COLORREF clrBase = (COLORREF)-1,
    BOOL bIsRight = TRUE);
```

### <a name="parameters"></a>Parametry

*pBits*<br/>
[in] Ukazatel na bitové hodnoty rastrového obrázku.

*Rect*<br/>
[in] Obdélníkovou oblast ve vaší aplikaci. Kreslení správce vykreslí stín pod a napravo od této oblasti.

*x*<br/>
[in] Vodorovné souřadnice barvu pixelu.

*y*<br/>
[in] Svislé souřadnice barvu pixelu.

*percent*<br/>
[in] Procento průhlednost.

*iShadowSize*<br/>
[in] Šířka a výška stínu.

*clrBase*<br/>
[in] Barva stínu.

*bIsRight*<br/>
[in] Parametr logické hodnoty označující, které pixel na barvu. Další informace naleznete v části Poznámky.

### <a name="remarks"></a>Poznámky

Tato metoda je pomocná metoda, která se používá [CDrawingManager::DrawShadow](#drawshadow) metody. Doporučujeme vám, pokud chcete vykreslovat stín, volání `CDrawingManager::DrawShadow` místo.

Pokud *bIsRight* je nastavena na hodnotu TRUE, je pixel na barvu měří *x* pixelů od pravého okraje *rect*. Pokud je FALSE, je pixel na barvu měří *x* pixelů od levého okraje *rect*.

##  <a name="setpixel"></a>  CDrawingManager::SetPixel

Změní na jeden pixel v rastrový obrázek zadanou barvu.

```
static void __stdcall SetPixel(
    COLORREF* pBits,
    int cx,
    int cy,
    int x,
    int y,
    COLORREF color);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*pBits*|[in] Ukazatel na bitové hodnoty rastrového obrázku.|
|*cx*|[in] Celková šířka rastrového obrázku.|
|*cy*|[in] Celkový počet výšku rastrového obrázku.|
|*x*|[in] Souřadnice x pixelu rastrového obrázku nastaven, chcete-li změnit.|
|*y*|[in] Souřadnice y pixelu rastrového obrázku nastaven, chcete-li změnit.|
|*color*|[in] Nová barva pixel identifikovaný zadané souřadnice.|

##  <a name="smartmixcolors"></a>  CDrawingManager::SmartMixColors

Kombinuje dvě barvy podle vážený poměr.

```
static COLORREF __stdcall SmartMixColors(
    COLORREF color1,
    COLORREF color2,
    double dblLumRatio = 1.,
    int k1 = 1,
    int k2 = 1);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*color1*|[in] První barva kombinovat.|
|*color2*|[in] Druhá barva kombinovat.|
|*dblLumRatio*|[in] Poměr světelnost novou barvu. `SmartMixColors` Vynásobí světelnost smíšené barvy tento poměr před určení konečné barvy.|
|*k1*|[in] Vážený poměr první barvou.|
|*k2*|[in] Vážený poměr pro druhou barvou.|

### <a name="return-value"></a>Návratová hodnota

Barva, která představuje vážený kombinaci zadané barvy.

### <a name="remarks"></a>Poznámky

Tato metoda se nezdaří s chybou, pokud buď *k1* nebo *k2* je menší než nula. Pokud se oba tyto parametry jsou nastaveny na hodnotu 0, vrátí metoda `RGB(0, 0, 0)`.

Vážený poměr se počítá pomocí následujícího vzorce: (barvou1 \* k1 + barva2 \* k2) /(k1 + k2). Po vážený poměr se určí, metoda počítá světelnost pro smíšený barvu. Potom vynásobí světelnost podle *dblLumRatio*. Pokud je hodnota větší než 1.0, metoda nastaví světelnost pro smíšený barvu na novou hodnotu. V opačném případě světelnost nastavena na 1.0.

##  <a name="drawrotated"></a>  CDrawingManager::DrawRotated

Zdrojový řadič domény obsah uvnitř daného obdélník se otočí o 90 stupňů.

```
void DrawRotated(
    CRect rectDest,
    CDC& dcSrc,
    BOOL bClockWise);
```

### <a name="parameters"></a>Parametry

*rectDest*<br/>
Cílového obdélníku.

*dcSrc*<br/>
Kontext zdrojového zařízení.

*bClockWise*<br/>
Hodnota TRUE označuje otočit + 90 stupňů; Hodnota FALSE označuje otočit-90 stupňů.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
