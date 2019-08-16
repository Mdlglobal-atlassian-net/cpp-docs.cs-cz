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
ms.openlocfilehash: 69365b66b12d5a9284c9b097b225ba041e07b6b0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506811"
---
# <a name="cdrawingmanager-class"></a>CDrawingManager Class

`CDrawingManager` Třída implementuje složité kreslicí algoritmy.

## <a name="syntax"></a>Syntaxe

```
class CDrawingManager : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CDrawingManager::CDrawingManager](#cdrawingmanager)|`CDrawingManager` Vytvoří objekt.|
|`CDrawingManager::~CDrawingManager`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CDrawingManager::CreateBitmap_32](#createbitmap_32)|Vytvoří 32 rastrový obrázek nezávislý na zařízení (DIB), do kterého můžou aplikace zapisovat přímo.|
|[CDrawingManager::DrawAlpha](#drawalpha)|Zobrazí rastrové obrázky, které mají transparentní nebo poloprůhledný pixel.|
|[CDrawingManager::DrawRotated](#drawrotated)|Otočí zdrojový obsah DC v daném obdélníku o +/-90 stupňů.|
|[CDrawingManager::DrawEllipse](#drawellipse)|Nakreslí elipsu s dodanými barvami výplně a ohraničení.|
|[CDrawingManager::DrawGradientRing](#drawgradientring)|Nakreslí prstenec a vyplní ho barevným přechodem.|
|[CDrawingManager::DrawLine, CDrawingManager::DrawLineA](#drawline_cdrawingmanager__drawlinea)|Nakreslí čáru.|
|[CDrawingManager::DrawRect](#drawrect)|Nakreslí obdélník se zadanými barvami výplně a ohraničení.|
|[CDrawingManager::DrawShadow](#drawshadow)|Nakreslí stín pro obdélníkovou oblast.|
|[CDrawingManager::Fill4ColorsGradient](#fill4colorsgradient)|Vyplní obdélníkovou oblast dvěma barevnými přechody.|
|[CDrawingManager::FillGradient](#fillgradient)|Vyplní obdélníkovou oblast se zadaným barevným přechodem.|
|[CDrawingManager::FillGradient2](#fillgradient2)|Vyplní obdélníkovou oblast se zadaným barevným přechodem. Je také určen směr změny barvy přechodu.|
|[CDrawingManager::GrayRect](#grayrect)|Vyplní obdélník se zadanou šedou barvou.|
|[CDrawingManager::HighlightRect](#highlightrect)|Zvýrazní obdélníkovou oblast.|
|[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)|Převede barvu z reprezentace HLS na reprezentaci RGB.|
|[CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)|Převede barvu z reprezentace HLS na reprezentaci RGB.|
|[CDrawingManager::HSVtoRGB](#hsvtorgb)|Převede barvu z reprezentace HSV na reprezentaci RGB.|
|[CDrawingManager::HuetoRGB](#huetorgb)|Pomocná metoda, která převede hodnotu odstínu na červenou, zelenou nebo modrou komponentu.|
|[CDrawingManager::MirrorRect](#mirrorrect)|Překlopí obdélníkovou oblast.|
|[CDrawingManager::PixelAlpha](#pixelalpha)|Pomocná metoda, která určuje konečnou barvu pro Poloprůhledný pixel.|
|[CDrawingManager::PrepareShadowMask](#prepareshadowmask)|Vytvoří rastrový obrázek, který lze použít jako stín.|
|[CDrawingManager::RGBtoHSL](#rgbtohsl)|Převede barvu z reprezentace RGB na reprezentace HSL.|
|[CDrawingManager::RGBtoHSV](#rgbtohsv)|Převede barvu z reprezentace RGB na reprezentaci HSV.|
|[CDrawingManager::SetAlphaPixel](#setalphapixel)|Pomocná metoda, která barvy částečně transparentního pixelu v rastrovém obrázku|
|[CDrawingManager::SetPixel](#setpixel)|Pomocná metoda, která mění jeden pixel v bitmapě na určenou barvu.|
|[CDrawingManager::SmartMixColors](#smartmixcolors)|Kombinuje dvě barvy na základě váženého poměru.|

## <a name="remarks"></a>Poznámky

`CDrawingManager` Třída poskytuje funkce pro vykreslování stínů, barevné přechody a zvýrazněné obdélníky. Provádí také alfa-míchání. Tuto třídu můžete použít k přímé změně uživatelského rozhraní aplikace.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)<br/>
`CDrawingManager`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdrawmanager. h

##  <a name="cdrawingmanager"></a>  CDrawingManager::CDrawingManager

Vytvoří objekt [CDrawingManager](../../mfc/reference/cdrawingmanager-class.md) .

```
CDrawingManager(CDC& dc);
```

### <a name="parameters"></a>Parametry

*dc*<br/>
pro Odkaz na kontext zařízení. Pro `CDrawingManager` kreslení používá tento kontext.

##  <a name="createbitmap_32"></a>  CDrawingManager::CreateBitmap_32

Vytvoří 32 rastrový obrázek nezávislý na zařízení (DIB), do kterého můžou aplikace zapisovat přímo.

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
|*hodnota*|pro Parametr [CSize](../../atl-mfc-shared/reference/csize-class.md) , který určuje velikost rastrového obrázku.|
|*pBits*|mimo Ukazatel na ukazatel dat, který přijímá umístění bitových hodnot DIB.|
|*bitmap*|Popisovač původního rastrového obrázku|
|*clrTransparent*|Hodnota RGB určující průhlednou barvu původního rastrového obrázku.|

### <a name="return-value"></a>Návratová hodnota

Popisovač nově vytvořeného rastrového obrázku DIB, pokud je tato metoda úspěšná; jinak NULL.

### <a name="remarks"></a>Poznámky

Další informace o tom, jak vytvořit rastrový obrázek DIB, najdete v tématu [CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibitmap).

##  <a name="drawalpha"></a>  CDrawingManager::DrawAlpha

Zobrazí rastrové obrázky, které mají transparentní nebo poloprůhledný pixel.

```
void DrawAlpha(
    CDC* pDstDC,
    const CRect& rectDst,
    CDC* pSrcDC,
    const CRect& rectSrc);
```

### <a name="parameters"></a>Parametry

*pDstDC*<br/>
pro Ukazatel na kontext zařízení pro cíl.

*rectDst*<br/>
pro Cílový obdélník.

*pSrcDC*<br/>
pro Ukazatel na kontext zařízení pro zdroj.

*rectSrc*<br/>
pro Zdrojový obdélník.

### <a name="remarks"></a>Poznámky

Tato metoda provádí alfa-míchání pro dvě bitmapy. Další informace o alfa-míchání naleznete v tématu [AlphaBlend](/windows/win32/api/wingdi/nf-wingdi-alphablend) v Windows SDK.

##  <a name="drawellipse"></a>  CDrawingManager::DrawEllipse

Nakreslí elipsu s dodanými barvami výplně a ohraničení.

```
void DrawEllipse(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parametry

*OBD*<br/>
pro Ohraničující obdélník pro elipsu

*clrFill*<br/>
pro Barva, kterou tato metoda používá k vyplnění elipsy.

*clrLine*<br/>
pro Barva, kterou tato metoda používá jako ohraničení elipsy.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí bez kreslení elipsy, pokud je jedna barva nastavena na hodnotu-1. Také se vrátí bez kreslení elipsy, pokud je jedna dimenze ohraničujícího obdélníku 0.

##  <a name="drawgradientring"></a>  CDrawingManager::DrawGradientRing

Nakreslí prstenec a vyplní ho barevným přechodem.

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

*OBD*<br/>
pro Parametr [CRect](../../atl-mfc-shared/reference/crect-class.md) , který určuje hranici pro kanál přechodu.

*colorStart*<br/>
pro První barva přechodu

*colorFinish*<br/>
pro Poslední barva přechodu

*colorBorder*<br/>
pro Barva ohraničení

*nAngle*<br/>
pro Parametr, který určuje počáteční úhel vykreslování přechodu. Tato hodnota by měla být mezi 0 a 360.

*nWidth*<br/>
pro Šířka ohraničení prstence

*clrFace*<br/>
pro Barva vnitřku prstence

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Obdélník definovaný v *Rect* musí být alespoň 5 pixelů na šířku a 5 pixelů vysoké.

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
|*x1*|pro Souřadnice x místa, kde se řádek spouští|
|*Y1*|pro Souřadnice y, kde se řádek spouští|
|*x2*|pro Souřadnice x místa, kde končí řádek|
|*y2*|pro Souřadnice y, kde končí řádek|
|*clrLine*|pro Barva čáry|

### <a name="remarks"></a>Poznámky

Tato metoda se nezdařila, pokud je *clrLine* rovno-1.

##  <a name="drawrect"></a>  CDrawingManager::DrawRect

Nakreslí obdélník se zadanými barvami výplně a ohraničení.

```
void DrawRect(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parametry

*OBD*<br/>
pro Hranice rámečku

*clrFill*<br/>
pro Barva, kterou tato metoda používá k vyplnění obdélníku.

*clrLine*<br/>
pro Barva, kterou tato metoda používá pro ohraničení obdélníku.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí bez kreslení obdélníku, je-li jedna barva nastavena na hodnotu-1. Také vrátí, pokud je jedna dimenze obdélníku 0.

##  <a name="drawshadow"></a>  CDrawingManager::DrawShadow

Nakreslí stín pro obdélníkovou oblast.

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

*OBD*<br/>
pro Obdélníková oblast ve vaší aplikaci. Správce kreslení nakreslí stín pod touto oblastí.

*nDepth*<br/>
pro Šířka a výška stínu

*iMinBrightness*<br/>
pro Minimální jas stínu.

*iMaxBrightness*<br/>
pro Maximální jas stínu

*pBmpSaveBottom*<br/>
pro Ukazatel na rastrový obrázek, který obsahuje obrázek dolní části stínu.

*pBmpSaveRight*<br/>
pro Ukazatel na rastr, který obsahuje obrázek pro stín, který je vykreslen na pravé straně obdélníku.

*clrBase*<br/>
pro Barva stínu

*bRightShadow*<br/>
pro Logický parametr, který určuje, jak je stín vykreslen. Pokud je `TRUE`bRightShadow, `DrawShadow` nakreslí stín na pravé straně obdélníku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Pomocí parametrů *pBmpSaveBottom* a *pBmpSaveRight*můžete pro dolní a pravý stín zadat dvě platné rastrové obrázky. Pokud tyto objekty [CBitmap –](../../mfc/reference/cbitmap-class.md) mají připojený objekt GDI, `DrawShadow` budou tyto bitmapy používat jako stíny. Pokud parametry nemají připojený objekt GDI, `DrawShadow` nakreslí stín a připojí rastry k parametrům. `CBitmap` V budoucích voláních `DrawShadow`můžete tyto bitmapy poskytnout pro urychlení procesu kreslení. Další informace o `CBitmap` třídě a objektech GDI naleznete v tématu [Graphic Objects](../../mfc/graphic-objects.md).

Pokud je `NULL`některý z těchto parametrů, `DrawShadow` vykreslí se stín automaticky.

Pokud nastavíte *bRightShadow* na hodnotu false, bude stín vykreslen pod obdélníkovou oblastí a nalevo od ní.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít `DrawShadow` metodu `CDrawingManager` třídy. Tento fragment kódu je součástí ukázkové ukázky [listu Prop](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_PropSheetDemo#1](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_1.cpp)]

##  <a name="fill4colorsgradient"></a>  CDrawingManager::Fill4ColorsGradient

Vyplní obdélníkovou oblast dvěma barevnými přechody.

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

*OBD*<br/>
pro Obdélník, který chcete vyplnit.

*colorStart1*<br/>
pro Počáteční barva prvního barevného přechodu.

*colorFinish1*<br/>
pro Konečná barva prvního barevného přechodu.

*colorStart2*<br/>
pro Počáteční barva pro druhý barevný přechod.

*colorFinish2*<br/>
pro Konečná barva pro druhý barevný přechod.

*bHorz*<br/>
pro Logický parametr, který označuje, `Fill4ColorsGradient` zda jsou barvy vodorovným nebo svislým přechodem. Hodnota TRUE označuje Vodorovný přechod.

*nPercentage*<br/>
pro Celé číslo od 0-100. Tato hodnota označuje procento obdélníku, který má být vyplněn prvním barevným přechodem.

### <a name="remarks"></a>Poznámky

Když je obdélník vyplněn pomocí dvou barevných přechodů, jsou umístěny výše nebo vedle sebe navzájem, v závislosti na hodnotě *bHorz*. Každý barevný přechod je počítán nezávisle s metodou [CDrawingManager:: FillGradient](#fillgradient).

Tato metoda generuje selhání kontrolního výrazu, pokud *nPercentage* je menší než 0 nebo větší než 100.

##  <a name="fillgradient"></a>  CDrawingManager::FillGradient

Vyplní obdélníkovou oblast zadaným barevným přechodem.

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

*OBD*<br/>
pro Obdélníková oblast, která se má vyplnit

*colorStart*<br/>
pro První barva přechodu

*colorFinish*<br/>
pro Konečná barva přechodu.

*bHorz*<br/>
pro Logický parametr, který určuje, `FillGradient` zda má být nakreslen vodorovný nebo svislý přechod.

*nStartFlatPercentage*<br/>
pro Procentuální podíl obdélníku, který `FillGradient` vyplní *colorStart* před zahájením přechodu.

*nEndFlatPercentage*<br/>
pro Procentuální podíl obdélníku, který `FillGradient` vyplní *colorFinish* po dokončení přechodu.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít `FillGradient` metodu `CDrawingManager` třídy. Tento fragment kódu je součástí [ukázky ukázky sady MS Office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#12](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_2.cpp)]

##  <a name="fillgradient2"></a>  CDrawingManager::FillGradient2

Vyplní obdélníkovou oblast se zadaným barevným přechodem.

```
void FillGradient2 (
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    int nAngle = 0);
```

### <a name="parameters"></a>Parametry

*OBD*<br/>
pro Obdélníková oblast, která se má vyplnit

*colorStart*<br/>
pro První barva přechodu

*colorFinish*<br/>
pro Poslední barva přechodu

*nAngle*<br/>
pro Celé číslo od 0 do 360. Tento parametr určuje směr barevného přechodu barvy.

### <a name="remarks"></a>Poznámky

Pomocí *nAngle* Určete směr barevného přechodu barvy. Když zadáte směr barevného přechodu barvy, určíte také, kde se má barevný přechod spustit. Hodnota 0 pro *nAngle* určuje, že přechod začíná od horní části obdélníku. Jak se *nAngle* zvyšuje, počáteční poloha přechodu se přesune ve směru proti směru hodinových ručiček na základě úhlu.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít `FillGradient2` metodu `CDrawingManager` třídy. Tento fragment kódu je součástí [ukázky nové ovládací prvky](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#37](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_3.cpp)]

##  <a name="grayrect"></a>  CDrawingManager::GrayRect

Vyplní obdélník se zadanou šedou barvou.

```
BOOL GrayRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    COLORREF clrDisabled = (COLORREF)-1);
```

### <a name="parameters"></a>Parametry

*OBD*<br/>
pro Obdélníková oblast, která se má vyplnit

*nPercentage*<br/>
pro Procentuální hodnota šedé, kterou chcete v obdélníku.

*clrTransparent*<br/>
pro Průhledná barva.

*clrDisabled*<br/>
pro Barva, kterou tato metoda používá pro sytost v případě, že je *nPercentage* nastaven na hodnotu-1.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byla metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Pro parametr *nPercentage*je nižší hodnota označující tmavší barvu.

Maximální hodnota pro *nPercentage* je 200. Hodnota větší než 200 nezmění vzhled obdélníku. Pokud je hodnota-1, tato metoda používá *clrDisabled* k omezení sytosti obdélníku.

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

*OBD*<br/>
pro Obdélníková oblast, která má být zvýrazněna.

*nPercentage*<br/>
pro Procentuální hodnota, která označuje, jak průhledná má být zvýrazněna.

*clrTransparent*<br/>
pro Průhledná barva.

*nTolerance*<br/>
pro Celé číslo mezi 0 a 255, které určuje toleranci barvy.

*clrBlend*<br/>
pro Základní barva pro prolnutí.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Pokud *nPercentage* je mezi 0 a 99, `HighlightRect` používá algoritmus prolnutí alfa. Další informace o alfa míchání naleznete v tématu [alfa míchání čar a výplní](/dotnet/framework/winforms/advanced/alpha-blending-lines-and-fills). Pokud je *nPercentage* -1, tato metoda používá výchozí úroveň zvýraznění. Pokud je *nPercentage* 100, tato metoda neprovede žádnou akci a vrátí hodnotu true.

Metoda používá parametr *nTolerance* k určení, zda má být zvýrazněna obdélníková oblast. Pro zvýraznění obdélníku musí být rozdíl mezi barvou pozadí vaší aplikace a *clrTransparent* menší než *nTolerance* v každé součásti barvy (červená, zelená a modrá).

##  <a name="hlstorgb_one"></a>CDrawingManager::HLStoRGB_ONE

Převede barvu z reprezentace HLS na reprezentaci RGB.

```
static COLORREF __stdcall HLStoRGB_ONE(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>Parametry

*H*<br/>
pro Číslo mezi 0 a 1, které představuje odstín barvy.

*L*<br/>
pro Číslo mezi 0 a 1, které určuje světlost barvy.

*S*<br/>
pro Číslo mezi 0 a 1, které určuje sytost barvy.

### <a name="return-value"></a>Návratová hodnota

Znázornění HLS barvy v RGB.

### <a name="remarks"></a>Poznámky

Barva může být reprezentována jako HSV (odstín, sytost a hodnota), HSL (odstín, sytost a světlost) nebo RGB (červená, zelená a modrá). Další informace o různých reprezentacech barvy naleznete v tématu [Color](/windows/win32/uxguide/vis-color).

Tato metoda a `CDrawingManager::HLStoRGB_TWO` metoda provádí stejnou operaci, ale vyžaduje pro parametr *H* jiné hodnoty. V této metodě je *H* procentuální hodnota kružnice. V metodě je H hodnotou rozsahu mezi 0 a 360, která představuje červenou hodnotu. `CDrawingManager::HLStoRGB_TWO` Například s `HLStoRGB_ONE`, hodnota 0,25 pro *H* je ekvivalentní hodnotě 90 s `HLStoRGB_TWO`.

##  <a name="hlstorgb_two"></a>CDrawingManager::HLStoRGB_TWO

Převede barvu z reprezentace HLS na reprezentaci RGB.

```
static COLORREF __stdcall HLStoRGB_TWO(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>Parametry

*H*<br/>
pro Číslo mezi 0 a 360, které představuje odstín barvy.

*L*<br/>
pro Číslo mezi 0 a 1, které určuje světlost barvy.

*S*<br/>
pro Číslo mezi 0 a 1, které určuje sytost barvy.

### <a name="return-value"></a>Návratová hodnota

Znázornění HLS barvy v RGB.

### <a name="remarks"></a>Poznámky

Barva může být reprezentována jako HSV (odstín, sytost a hodnota), HSL (odstín, sytost a světlost) nebo RGB (červená, zelená a modrá). Další informace o různých reprezentacech barvy naleznete v tématu [Color](/windows/win32/uxguide/vis-color).

Tato metoda a metoda [CDrawingManager:: HLStoRGB_ONE](#hlstorgb_one) provádí stejnou operaci, ale vyžaduje pro parametr *H* jiné hodnoty. V této metodě je *H* hodnotou rozsahu mezi 0 a 360, která představuje červenou hodnotu. V metodě [CDrawingManager:: HLStoRGB_ONE](#hlstorgb_one) , *H* je procento kružnice. Například s `HLStoRGB_ONE`, hodnota 0,25 pro *H* je ekvivalentní hodnotě 90 s `HLStoRGB_TWO`.

##  <a name="hsvtorgb"></a>CDrawingManager::HSVtoRGB

Převede barvu z reprezentace HSV na reprezentaci RGB.

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
|*H*|pro Číslo mezi 0 a 360, které určuje odstín barvy.|
|*S*|pro Číslo mezi 0 a 1, které určuje sytost barvy.|
|*V*|pro Číslo mezi 0 a 1, které určuje hodnotu barvy.|

### <a name="return-value"></a>Návratová hodnota

Znázornění HSV barvy v RGB.

### <a name="remarks"></a>Poznámky

Barva může být reprezentována jako HSV (odstín, sytost a hodnota), HSL (odstín, sytost a světlost) nebo RGB (červená, zelená a modrá). Další informace o různých reprezentacech barvy naleznete v tématu [Color](/windows/win32/uxguide/vis-color).

##  <a name="huetorgb"></a>CDrawingManager::HuetoRGB

Převede hodnotu odstínu na červenou, zelenou nebo modrou komponentu.

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
pro Viz poznámky.

*m2*<br/>
pro Viz poznámky.

*h*<br/>
pro Viz poznámky.

*rm1*<br/>
pro Viz poznámky.

*rm2*<br/>
pro Viz poznámky.

*RH*<br/>
pro Viz poznámky.

### <a name="return-value"></a>Návratová hodnota

Jednotlivé červené, zelené nebo modré komponenty pro daný odstín.

### <a name="remarks"></a>Poznámky

Tato metoda je pomocná metoda, kterou `CDrawingManager` třída používá k výpočtu jednotlivých červených, zelených a modrých komponent barvy v reprezentaci HSV nebo HSL. Tato metoda není navržena tak, aby byla volána přímo programátorem. Vstupní parametry jsou hodnoty, které závisí na algoritmu převodu.

Chcete-li převést barvy HSV nebo HSL na reprezentaci RGB, zavolejte jednu z následujících metod:

- [CDrawingManager::HSVtoRGB](#hsvtorgb)

- [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)

- [CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)

##  <a name="mirrorrect"></a>  CDrawingManager::MirrorRect

Překlopí obdélníkovou oblast.

```
void MirrorRect(
    CRect rect,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Parametry

*OBD*<br/>
pro Ohraničující obdélník oblasti, která se má překlopit

*bHorz*<br/>
pro Logický parametr, který označuje, zda se obdélník Překlopí vodorovně nebo svisle.

### <a name="remarks"></a>Poznámky

Tato metoda může převracet jakékoli oblasti kontextu zařízení vlastněné `CDrawingManager` třídou. Pokud je *bHorz* nastaveno na hodnotu true, tato metoda Překlopí oblast vodorovně. V opačném případě se oblast Překlopí svisle.

##  <a name="pixelalpha"></a>  CDrawingManager::PixelAlpha

Vypočítá konečnou barvu pro Poloprůhledný pixel.

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
pro Počáteční barva pixelu

*procent*<br/>
pro Číslo mezi 0 a 100, které představuje procento průhlednosti. Hodnota 100 znamená, že počáteční barva je zcela průhledná.

*percentR*<br/>
pro Číslo mezi 0 a 100 představující procentuální hodnotu průhlednosti pro červenou komponentu.

*percentG*<br/>
pro Číslo mezi 0 a 100 představující procentuální hodnotu průhlednosti zelené komponenty.

*percentB*<br/>
pro Číslo mezi 0 a 100 představující procentuální podíl průhlednosti pro modrou komponentu.

*dstPixel*<br/>
pro Základní barva pixelu

### <a name="return-value"></a>Návratová hodnota

Konečná barva pro Poloprůhledný pixel

### <a name="remarks"></a>Poznámky

Toto je pomocná třída pro vybarvení poloprůhledných rastrových obrázků a není navržena tak, aby byla volána přímo programátorem.

Když použijete verzi metody, která má *dstPixel*, konečná barva je kombinací *dstPixel* a *srcPixel*. Barva *srcPixel* je částečně průhledná barva nad základní barvou *dstPixel*.

##  <a name="prepareshadowmask"></a>  CDrawingManager::PrepareShadowMask

Vytvoří rastrový obrázek, který lze použít jako stín.

```
static HBITMAP __stdcall PrepareShadowMask (
    int nDepth,
    COLORREF clrBase,
    int iMinBrightness = 0,
    int iMaxBrightness = 100);
```

### <a name="parameters"></a>Parametry

*nDepth*<br/>
pro Šířka a výška stínu

*clrBase*<br/>
pro Barva stínu

*iMinBrightness*<br/>
pro Minimální jas stínu.

*iMaxBrightness*<br/>
pro Maximální jas stínu

### <a name="return-value"></a>Návratová hodnota

Popisovač vytvořeného rastrového obrázku, pokud je tato metoda úspěšná; jinak NULL.

### <a name="remarks"></a>Poznámky

Pokud je *nDepth* nastavené na 0, tato metoda se ukončí a vrátí hodnotu null. Pokud je *nDepth* menší než 3, Šířka a výška stínu se nastaví na 3 pixely.

##  <a name="rgbtohsl"></a>  CDrawingManager::RGBtoHSL

Převede barvu z červené, zelené a modré (RGB) reprezentace na znázornění odstínu, sytosti a světla (HSL).

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
|*režimu*|pro Barva v hodnotách RGB.|
|*H*|mimo Ukazatel na typ Double, kde Metoda ukládá odstín barvy.|
|*S*|mimo Ukazatel na typ Double, kde Metoda ukládá sytost barvy.|
|*L*|mimo Ukazatel na typ Double, kde Metoda ukládá světlost barvy.|

### <a name="remarks"></a>Poznámky

Barva může být reprezentována jako HSV (odstín, sytost a hodnota), HSL (odstín, sytost a světlost) nebo RGB (červená, zelená a modrá). Další informace o různých reprezentacech barvy naleznete v tématu [Color](/windows/win32/uxguide/vis-color).

Vrácená hodnota pro *H* je vyjádřena jako zlomek mezi 0 a 1, kde 0 i 1 představují červenou hodnotu. Vrácené hodnoty pro *S* a *L* jsou čísla v rozsahu 0 až 1.

##  <a name="rgbtohsv"></a>CDrawingManager::RGBtoHSV

Převede barvu z reprezentace RGB na reprezentaci HSV.

```
static void __stdcall RGBtoHSV(
    COLORREF rgb,
    double* H,
    double* S,
    double* V);
```

### <a name="parameters"></a>Parametry

*režimu*<br/>
pro Barva, která má být převedena v prezentaci RGB.

*H*<br/>
mimo Ukazatel na typ Double, kde tato metoda uloží výsledný odstín barvy.

*S*<br/>
mimo Ukazatel na typ Double, kde tato metoda uloží výslednou sytost barvy.

*V*<br/>
mimo Ukazatel na typ Double, kde tato metoda uloží výslednou hodnotu pro barvu.

### <a name="remarks"></a>Poznámky

Barva může být reprezentována jako HSV (odstín, sytost a hodnota), HSL (odstín, sytost a světlost) nebo RGB (červená, zelená a modrá). Další informace o různých reprezentacech barvy naleznete v tématu [Color](/windows/win32/uxguide/vis-color).

Vrácená hodnota pro *H* je číslo mezi 0 a 360, kde 0 a 360 označují červenou hodnotu. Návratové hodnoty pro *S* a *V* jsou čísla v rozsahu 0 až 1.

##  <a name="setalphapixel"></a>  CDrawingManager::SetAlphaPixel

Barvy průhledného pixelu v rastrovém obrázku.

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
pro Ukazatel na bitové hodnoty rastrového obrázku.

*OBD*<br/>
pro Obdélníková oblast ve vaší aplikaci. Správce kreslení nakreslí stín pod a napravo od této oblasti.

*x*<br/>
pro Vodorovná souřadnice pixelu, která má být barva.

*y*<br/>
pro Svislá souřadnice pixelu, která má být barva.

*procent*<br/>
pro Procentuální podíl průhlednosti.

*iShadowSize*<br/>
pro Šířka a výška stínu

*clrBase*<br/>
pro Barva stínu

*bIsRight*<br/>
pro Logický parametr, který určuje, který pixel má být barevný. Další informace naleznete v části Poznámky.

### <a name="remarks"></a>Poznámky

Tato metoda je pomocná metoda, kterou používá metoda [CDrawingManager::D rawshadow](#drawshadow) . Doporučujeme, abyste místo toho nakreslili stín, a to `CDrawingManager::DrawShadow` za volání.

Pokud je *bIsRight* nastavené na true, pixel pro barevný obraz se měří *x* pixelů od pravého okraje *Rect*. Pokud je hodnota FALSE, pixel k barvě se měří *x* pixelů od levého okraje *Rect*.

##  <a name="setpixel"></a>CDrawingManager:: funkce SetPixel

Změní jeden pixel v rastrovém obrázku na určenou barvu.

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
|*pBits*|pro Ukazatel na bitové hodnoty rastrového obrázku.|
|*cx*|pro Celková šířka rastrového obrázku.|
|*kr*|pro Celková výška rastrového obrázku.|
|*x*|pro Souřadnice x v pixelu v bitmapě, která se má změnit.|
|*y*|pro Souřadnice y v pixelu v bitmapě, která se má změnit.|
|*barevných*|pro Nová barva pro pixel identifikovaný dodanými souřadnicemi|

##  <a name="smartmixcolors"></a>  CDrawingManager::SmartMixColors

Kombinuje dvě barvy na základě váženého poměru.

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
|*color1*|pro První barva, která se má kombinovat|
|*color2*|pro Druhá barva ke smíchání.|
|*dblLumRatio*|pro Poměr pro novou světlost barvy. `SmartMixColors`vynásobí světlost smíšené barvy tímto poměrem před určením konečné barvy.|
|*k1*|pro Vážený poměr první barvy.|
|*k2*|pro Vážený poměr pro druhou barvu.|

### <a name="return-value"></a>Návratová hodnota

Barva, která představuje váženou směs zadaných barev.

### <a name="remarks"></a>Poznámky

Tato metoda se nezdařila s chybou, pokud buď *K1* nebo *K2* je menší než nula. Pokud jsou oba parametry nastaveny na hodnotu 0, vrátí `RGB(0, 0, 0)`metoda.

Vážený poměr se vypočítá pomocí následujícího vzorce: (color1 \* K1 + COLOR2 \* K2)/(K1 + K2). Po určení váženého poměru metoda vypočítá světlost pro smíšenou barvu. Pak vynásobí světlost hodnotou *dblLumRatio*. Pokud je hodnota větší než 1,0, metoda nastaví světlost pro smíšenou barvu na novou hodnotu. V opačném případě je světlost nastavené na 1,0.

##  <a name="drawrotated"></a>  CDrawingManager::DrawRotated

Otočí zdrojový obsah DC v daném obdélníku o 90 stupňů.

```
void DrawRotated(
    CRect rectDest,
    CDC& dcSrc,
    BOOL bClockWise);
```

### <a name="parameters"></a>Parametry

*rectDest*<br/>
Cílový obdélník.

*dcSrc*<br/>
Kontext zdrojového zařízení.

*bClockWise*<br/>
Hodnota TRUE značí otočení + 90 stupňů; Hodnota FALSE indikuje otočení-90 stupňů.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
