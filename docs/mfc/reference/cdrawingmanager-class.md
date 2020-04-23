---
title: CDrawingManager – třída
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
ms.openlocfilehash: 73c5775c2cb83dea79401615b31f2194094fac8e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753236"
---
# <a name="cdrawingmanager-class"></a>CDrawingManager – třída

Třída `CDrawingManager` implementuje komplexní kreslicí algoritmy.

## <a name="syntax"></a>Syntaxe

```
class CDrawingManager : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDrawingManager::CDrawingManager](#cdrawingmanager)|Vytvoří `CDrawingManager` objekt.|
|`CDrawingManager::~CDrawingManager`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDrawingManager::CreateBitmap_32](#createbitmap_32)|Vytvoří 32bitovou bitmapu (DIB) nezávislou na zařízení, do které mohou aplikace přímo zapisovat.|
|[CDrawingManager::DrawAlpha](#drawalpha)|Zobrazí bitmapy s průhlednými nebo poloprůhlednými obrazovými body.|
|[CDrawingManager::DrawRotated](#drawrotated)|Otočí zdrojový obsah stejnosměrného řadiče domény uvnitř daného obdélníku o +/- 90 stupňů.|
|[CDrawingManager::DrawEllipse](#drawellipse)|Nakreslí elipsu s dodanou výplní a barvami ohraničení.|
|[CDrawingManager::DrawGradientRing](#drawgradientring)|Nakreslí prsten a vyplní ho barevným přechodem.|
|[CDrawingManager::DrawLine, CDrawingManager::DrawLineA](#drawline_cdrawingmanager__drawlinea)|Nakreslí čáru.|
|[CDrawingManager::DrawRect](#drawrect)|Nakreslí obdélník s dodanou výplní a barvami ohraničení.|
|[CDrawingManager::DrawShadow](#drawshadow)|Nakreslí stín pro obdélníkovou oblast.|
|[CDrawingManager::Fill4ColorsGradient](#fill4colorsgradient)|Vyplní obdélníkovou oblast dvěma barevnými přechody.|
|[CDrawingManager::FillGradient](#fillgradient)|Vyplní obdélníkovou oblast určeným barevným přechodem.|
|[CDrawingManager::FillGradient2](#fillgradient2)|Vyplní obdélníkovou oblast určeným barevným přechodem. Je také určen směr změny barvy přechodu.|
|[CDrawingManager::GrayRect](#grayrect)|Vyplní obdélník zadanou šedou barvou.|
|[CDrawingManager::HighlightRect](#highlightrect)|Zvýrazní obdélníkovou oblast.|
|[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)|Převede barvu z reprezentace HLS na reprezentaci RGB.|
|[CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)|Převede barvu z reprezentace HLS na reprezentaci RGB.|
|[CDrawingManager::HSVtoRGB](#hsvtorgb)|Převede barvu z reprezentace HSV na reprezentaci RGB.|
|[CDrawingManager::HuetoRGB](#huetorgb)|Pomocná metoda, která převede hodnotu odstínu na červenou, zelenou nebo modrou komponentu.|
|[CDrawingManager::MirrorRect](#mirrorrect)|Překlopí obdélníkovou oblast.|
|[CDrawingManager::PixelAlpha](#pixelalpha)|Pomocná metoda, která určuje konečnou barvu pro poloprůhledný obrazový bod.|
|[CDrawingManager::PrepareShadowMask](#prepareshadowmask)|Vytvoří bitmapu, kterou lze použít jako stín.|
|[CDrawingManager::RGBtoHSL](#rgbtohsl)|Převede barvu z reprezentace RGB na reprezentaci HSL.|
|[CDrawingManager::RGBtoHSV](#rgbtohsv)|Převede barvu z reprezentace RGB na reprezentaci HSV.|
|[CDrawingManager::SetAlphaPixel](#setalphapixel)|Pomocná metoda, která vybarví částečně průhledný obrazový bod v bitmapě.|
|[CDrawingManager::SetPixel](#setpixel)|Pomocná metoda, která změní jeden obrazový bod v bitmapě na zadanou barvu.|
|[CDrawingManager::SmartMixColors](#smartmixcolors)|Zkombinuje dvě barvy na základě váženého poměru.|

## <a name="remarks"></a>Poznámky

Třída `CDrawingManager` poskytuje funkce pro kreslení stínů, barevných přechodů a zvýrazněných obdélníků. Provádí také alfa prolnutí. Tuto třídu můžete použít k přímé změně ui aplikace.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)<br/>
`CDrawingManager`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdrawmanager.h

## <a name="cdrawingmanagercdrawingmanager"></a><a name="cdrawingmanager"></a>CDrawingManager::CDrawingManager

Vytvoří objekt [CDrawingManager.](../../mfc/reference/cdrawingmanager-class.md)

```
CDrawingManager(CDC& dc);
```

### <a name="parameters"></a>Parametry

*Dc*<br/>
[v] Odkaz na kontext zařízení. Používá `CDrawingManager` tento kontext pro kreslení.

## <a name="cdrawingmanagercreatebitmap_32"></a><a name="createbitmap_32"></a>CDrawingManager::CreateBitmap_32

Vytvoří 32bitovou bitmapu (DIB) nezávislou na zařízení, do které mohou aplikace přímo zapisovat.

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
|*Velikost*|[v] A [CSize](../../atl-mfc-shared/reference/csize-class.md) parametr, který označuje velikost bitmapy.|
|*pBity*|[out] Ukazatel na ukazatel dat, který přijímá umístění bitových hodnot DIB.|
|*Bitmapové*|Úchyt k původnímu bitmapě|
|*clrTransparent*|Hodnota RGB určující průhlednou barvu původní bitmapy.|

### <a name="return-value"></a>Návratová hodnota

Popisovač nově vytvořené bitmapy DIB, pokud je tato metoda úspěšná; jinak NULL.

### <a name="remarks"></a>Poznámky

Další informace o vytvoření bitmapy DIB naleznete v tématu [CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibitmap).

## <a name="cdrawingmanagerdrawalpha"></a><a name="drawalpha"></a>CDrawingManager::DrawAlpha

Zobrazí bitmapy s průhlednými nebo poloprůhlednými obrazovými body.

```cpp
void DrawAlpha(
    CDC* pDstDC,
    const CRect& rectDst,
    CDC* pSrcDC,
    const CRect& rectSrc);
```

### <a name="parameters"></a>Parametry

*pDstDC*<br/>
[v] Ukazatel na kontext zařízení pro cíl.

*rectDst*<br/>
[v] Cílový obdélník.

*pSrcDC*<br/>
[v] Ukazatel na kontext zařízení pro zdroj.

*rectSrc*<br/>
[v] Zdrojový obdélník.

### <a name="remarks"></a>Poznámky

Tato metoda provádí alfa prolnutí pro dva bitmapy. Další informace o alfa prolnutí, viz [AlphaBlend](/windows/win32/api/wingdi/nf-wingdi-alphablend) v sada Windows SDK.

## <a name="cdrawingmanagerdrawellipse"></a><a name="drawellipse"></a>CDrawingManager::DrawEllipse

Nakreslí elipsu s dodanou výplní a barvami ohraničení.

```cpp
void DrawEllipse(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[v] Ohraničovací obdélník pro elipsu.

*clrFill*<br/>
[v] Barva, kterou tato metoda používá k vyplnění elipsy.

*clrLine*<br/>
[v] Barva, kterou tato metoda používá jako okraj elipsy.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí bez kreslení elipsy, pokud je nastavena jedna barva na -1. Vrátí se také bez kreslení elipsy, pokud je jeden z rozměrů ohraničovacího obdélníku 0.

## <a name="cdrawingmanagerdrawgradientring"></a><a name="drawgradientring"></a>CDrawingManager::DrawGradientRing

Nakreslí prsten a vyplní ho barevným přechodem.

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
[v] [CRect](../../atl-mfc-shared/reference/crect-class.md) parametr, který určuje hranici pro kroužek přechodu.

*colorStart*<br/>
[v] První barva přechodu.

*colorFinish*<br/>
[v] Poslední barva přechodu.

*colorBorder*<br/>
[v] Barva ohraničení.

*nÚhel*<br/>
[v] Parametr, který určuje počáteční úhel výkresu přechodu. Tato hodnota by měla být mezi 0 a 360.

*nŠířka*<br/>
[v] Šířka okraje pro kroužek.

*clrFace*<br/>
[v] Barva interiéru prstenu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Obdélník definovaný *rect* musí být alespoň 5 pixelů široký a 5 pixelů vysoký.

## <a name="cdrawingmanagerdrawline-cdrawingmanagerdrawlinea"></a><a name="drawline_cdrawingmanager__drawlinea"></a>CDrawingManager::DrawLine, CDrawingManager::DrawLineA

Nakreslí čáru.

```cpp
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
|*x1*|[v] Souřadnice x, kde začíná čára.|
|*y1*|[v] Souřadnice y, kde začíná čára.|
|*x2*|[v] Souřadnice x, kde končí čára.|
|*y2*|[v] Souřadnice y, kde končí čára.|
|*clrLine*|[v] Barva čáry.|

### <a name="remarks"></a>Poznámky

Tato metoda se nezdaří, pokud *clrLine* rovná -1.

## <a name="cdrawingmanagerdrawrect"></a><a name="drawrect"></a>CDrawingManager::DrawRect

Nakreslí obdélník s dodanou výplní a barvami ohraničení.

```cpp
void DrawRect(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[v] Hranice pro obdélník.

*clrFill*<br/>
[v] Barva tato metoda používá k vyplnění obdélníku.

*clrLine*<br/>
[v] Barva, kterou tato metoda používá pro ohraničení obdélníku.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí bez kreslení obdélníku, pokud je nastavena jedna barva -1. Vrátí také, pokud je jeden z rozměrů obdélníku 0.

## <a name="cdrawingmanagerdrawshadow"></a><a name="drawshadow"></a>CDrawingManager::DrawShadow

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

*Rect*<br/>
[v] Obdélníková oblast v aplikaci. Správce výkresu nakreslí stín pod touto oblastí.

*nHloubka*<br/>
[v] Šířka a výška stínu.

*iMinBrightness*<br/>
[v] Minimální jas stínu.

*iMaxBrightness*<br/>
[v] Maximální jas stínu.

*pBmpSaveBottom*<br/>
[v] Ukazatel na bitmapu, která obsahuje obraz pro spodní část stínu.

*pBmpSaveRight*<br/>
[v] Ukazatel na bitmapu, která obsahuje obraz pro stín, který je nakreslena na pravé straně obdélníku.

*clrBase*<br/>
[v] Barva stínu.

*bRightShadow*<br/>
[v] Logický parametr, který označuje, jak je stín nakreslen. Pokud *bRightShadow* je `TRUE`, `DrawShadow` nakreslí stín na pravé straně obdélníku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Pomocí parametrů *pBmpSaveBottom* a *pBmpSaveRight*můžete zadat dvě platné rastrové obrázky pro dolní a pravý stín . Pokud tyto objekty [CBitmap](../../mfc/reference/cbitmap-class.md) mají připojený `DrawShadow` objekt GDI, použije tyto rastrové obrázky jako stíny. Pokud `CBitmap` parametry nemají připojený objekt GDI, `DrawShadow` nakreslí stín a připojí bitmapy k parametrům. V budoucích `DrawShadow`voláních můžete poskytnout tyto rastrové obrázky pro urychlení procesu kreslení. Další informace o `CBitmap` objektech třídy a GDI naleznete v [tématu Grafické objekty](../../mfc/graphic-objects.md).

Pokud některý z těchto `NULL` `DrawShadow` parametrů je , bude automaticky kreslit stín.

Pokud nastavíte *bRightShadow* na FALSE, stín bude nakreslena pod a vlevo obdélníkové oblasti.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak `DrawShadow` používat metodu třídy. `CDrawingManager` Tento fragment kódu je součástí [ukázky ukázky prop sheet .](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_PropSheetDemo#1](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_1.cpp)]

## <a name="cdrawingmanagerfill4colorsgradient"></a><a name="fill4colorsgradient"></a>CDrawingManager::Fill4ColorsGradient

Vyplní obdélníkovou oblast dvěma barevnými přechody.

```cpp
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
[v] Obdélník vyplnit.

*colorStart1*<br/>
[v] Počáteční barva pro první barevný přechod.

*colorFinish1*<br/>
[v] Konečná barva pro první barevný přechod.

*barvaStart2*<br/>
[v] Počáteční barva pro druhý barevný přechod.

*colorFinish2*<br/>
[v] Konečná barva pro druhý barevný přechod.

*bHorz*<br/>
[v] Logický parametr, který `Fill4ColorsGradient` označuje, zda má barvy vodorovný nebo svislý přechod. TRUE označuje vodorovný přechod.

*nProcento*<br/>
[v] Celé číslo od 0-100. Tato hodnota označuje procento obdélníku, které má být vyplněno prvním barevným přechodem.

### <a name="remarks"></a>Poznámky

Je-li obdélník vyplněn dvěma barevnými přechody, jsou buď umístěny nad sebou, nebo vedle sebe, v závislosti na hodnotě *bHorz*. Každý barevný přechod se vypočítá nezávisle s metodou [CDrawingManager::FillGradient](#fillgradient).

Tato metoda generuje selhání kontrolního výrazu, pokud *nPercentage* je menší než 0 nebo více než 100.

## <a name="cdrawingmanagerfillgradient"></a><a name="fillgradient"></a>CDrawingManager::FillGradient

Vyplní obdélníkovou oblast určeným barevným přechodem.

```cpp
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
[v] Obdélníková oblast, kterou chcete vyplnit.

*colorStart*<br/>
[v] První barva přechodu.

*colorFinish*<br/>
[v] Konečná barva přechodu.

*bHorz*<br/>
[v] Logický parametr, který určuje, zda `FillGradient` má být nakreslit vodorovný nebo svislý přechod.

*nStartFlatPercentage*<br/>
[v] Procento obdélníku, `FillGradient` který vyplňuje *colorStart* před spuštěním přechodu.

*nEndFlatPercentage*<br/>
[v] Procento obdélníku, `FillGradient` který se vyplní *colorFinish* po dokončení přechodu.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak `FillGradient` používat metodu třídy. `CDrawingManager` Tento fragment kódu je součástí [ukázky ukázky ukázky ukázky ms office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#12](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_2.cpp)]

## <a name="cdrawingmanagerfillgradient2"></a><a name="fillgradient2"></a>CDrawingManager::FillGradient2

Vyplní obdélníkovou oblast určeným barevným přechodem.

```cpp
void FillGradient2 (
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    int nAngle = 0);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[v] Obdélníková oblast, kterou chcete vyplnit.

*colorStart*<br/>
[v] První barva přechodu.

*colorFinish*<br/>
[v] Poslední barva přechodu.

*nÚhel*<br/>
[v] Celé číslo mezi 0 a 360. Tento parametr určuje směr barevného přechodu.

### <a name="remarks"></a>Poznámky

Pomocí *nAngle* určete směr barevného přechodu. Když určíte směr barevného přechodu, určíte také, kde začíná barevný přechod. Hodnota 0 pro *nAngle* označuje, že přechod začíná od horní části obdélníku. Jak *se nAngle* zvětšuje, počáteční umístění přechodu se pohybuje proti směru hodinových ručiček na základě úhlu.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak `FillGradient2` používat metodu třídy. `CDrawingManager` Tento fragment kódu je součástí [ukázky Nové ovládací prvky](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#37](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_3.cpp)]

## <a name="cdrawingmanagergrayrect"></a><a name="grayrect"></a>CDrawingManager::GrayRect

Vyplní obdélník zadanou šedou barvou.

```
BOOL GrayRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    COLORREF clrDisabled = (COLORREF)-1);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[v] Obdélníková oblast, kterou chcete vyplnit.

*nProcento*<br/>
[v] Požadované procento šedé v obdélníku.

*clrTransparent*<br/>
[v] Průhledná barva.

*clrZakázáno.*<br/>
[v] Barva, která tato metoda používá pro de-sytost, pokud *nPercentage* je nastavena na -1.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byla metoda úspěšná; jinak FALSE.

### <a name="remarks"></a>Poznámky

Pro parametr *nPercentage*, nižší hodnota označuje tmavší barvu.

Maximální hodnota pro *nPercentage* je 200. Hodnota větší než 200 nezmění vzhled obdélníku. Pokud je hodnota -1, tato metoda používá *clrDisabled* k omezení sytosti obdélníku.

## <a name="cdrawingmanagerhighlightrect"></a><a name="highlightrect"></a>CDrawingManager::HighlightRect

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
[v] Obdélníková oblast, která má být zvýrazněna.

*nProcento*<br/>
[v] Procento, které označuje, jak transparentní by mělo být zvýraznění.

*clrTransparent*<br/>
[v] Průhledná barva.

*nTolerance*<br/>
[v] Celé číslo mezi 0 a 255, které označuje toleranci barev.

*clrBlend*<br/>
[v] Základní barva pro prolnutí.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je metoda úspěšná; jinak FALSE.

### <a name="remarks"></a>Poznámky

Pokud *nPercentage* je mezi 0 `HighlightRect` a 99, používá alfa prolnutí algoritmus. Další informace o alfa prolnutí najdete [v tématu Alfa prolnutí čar a výplní](/dotnet/framework/winforms/advanced/alpha-blending-lines-and-fills). Pokud *nPercentage* je -1, tato metoda používá výchozí úroveň zvýraznění. Pokud *nPercentage* je 100, tato metoda neprovede žádnou akci a vrátí hodnotu TRUE.

Metoda používá parametr *nTolerance* k určení, zda chcete zvýraznit obdélníkovou oblast. Chcete-li zvýraznit obdélník, rozdíl mezi barvou pozadí aplikace a *clrTransparent* musí být menší než *nTolerance* v každé barevné složce (červená, zelená a modrá).

## <a name="cdrawingmanagerhlstorgb_one"></a><a name="hlstorgb_one"></a>CDrawingManager::HLStoRGB_ONE

Převede barvu z reprezentace HLS na reprezentaci RGB.

```
static COLORREF __stdcall HLStoRGB_ONE(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>Parametry

*H*<br/>
[v] Číslo mezi 0 a 1, které představuje odstín pro barvu.

*L*<br/>
[v] Číslo mezi 0 a 1, které označuje světelnost barvy.

*S*<br/>
[v] Číslo mezi 0 a 1, které označuje sytost barvy.

### <a name="return-value"></a>Návratová hodnota

RGB reprezentace barvy HLS k dispozici.

### <a name="remarks"></a>Poznámky

Barvu lze reprezentováno jako HSV (odstín, sytost a hodnota), HSL (odstín, sytost a světelnost) nebo RGB (červená, zelená a modrá). Další informace o různých reprezentacích barev naleznete v tématu [Barva](/windows/win32/uxguide/vis-color).

Tato metoda `CDrawingManager::HLStoRGB_TWO` a metoda provést stejnou operaci, ale vyžadují různé hodnoty pro *H* parametr. V této *metodě* h je procento kruhu. V `CDrawingManager::HLStoRGB_TWO` metodě *H* je hodnota stupně mezi 0 a 360, které představují červené. Například s `HLStoRGB_ONE`, hodnota 0,25 pro *H* je ekvivalentní hodnotě 90 s `HLStoRGB_TWO`.

## <a name="cdrawingmanagerhlstorgb_two"></a><a name="hlstorgb_two"></a>CDrawingManager::HLStoRGB_TWO

Převede barvu z reprezentace HLS na reprezentaci RGB.

```
static COLORREF __stdcall HLStoRGB_TWO(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>Parametry

*H*<br/>
[v] Číslo mezi 0 a 360, které představuje odstín pro barvu.

*L*<br/>
[v] Číslo mezi 0 a 1, které označuje světelnost barvy.

*S*<br/>
[v] Číslo mezi 0 a 1, které označuje sytost barvy.

### <a name="return-value"></a>Návratová hodnota

RGB reprezentace barvy HLS k dispozici.

### <a name="remarks"></a>Poznámky

Barvu lze reprezentováno jako HSV (odstín, sytost a hodnota), HSL (odstín, sytost a světelnost) nebo RGB (červená, zelená a modrá). Další informace o různých reprezentacích barev naleznete v tématu [Barva](/windows/win32/uxguide/vis-color).

Tato metoda a [Metoda CDrawingManager::HLStoRGB_ONE](#hlstorgb_one) provádějí stejnou operaci, ale vyžadují různé hodnoty pro parametr *H.* V této metodě *H* je hodnota stupně mezi 0 a 360, které představují červené. V [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one) metoda *H* je procento kruhu. Například s `HLStoRGB_ONE`, hodnota 0,25 pro *H* je ekvivalentní hodnotě 90 s `HLStoRGB_TWO`.

## <a name="cdrawingmanagerhsvtorgb"></a><a name="hsvtorgb"></a>CDrawingManager::HSVtoRGB

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
|*H*|[v] Číslo mezi 0 a 360, které označuje odstín barvy.|
|*S*|[v] Číslo mezi 0 a 1, které označuje sytost barvy.|
|*V*|[v] Číslo mezi 0 a 1, které označuje hodnotu barvy.|

### <a name="return-value"></a>Návratová hodnota

RGB reprezentace barvy HSV k dispozici.

### <a name="remarks"></a>Poznámky

Barvu lze reprezentováno jako HSV (odstín, sytost a hodnota), HSL (odstín, sytost a světelnost) nebo RGB (červená, zelená a modrá). Další informace o různých reprezentacích barev naleznete v tématu [Barva](/windows/win32/uxguide/vis-color).

## <a name="cdrawingmanagerhuetorgb"></a><a name="huetorgb"></a>CDrawingManager::HuetoRGB

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
[v] Viz Poznámky.

*m2*<br/>
[v] Viz Poznámky.

*H*<br/>
[v] Viz Poznámky.

*rm1*<br/>
[v] Viz Poznámky.

*rm2*<br/>
[v] Viz Poznámky.

*Rh*<br/>
[v] Viz Poznámky.

### <a name="return-value"></a>Návratová hodnota

Jednotlivé červené, zelené nebo modré komponenty pro zadaný odstín.

### <a name="remarks"></a>Poznámky

Tato metoda je pomocná `CDrawingManager` metoda, která používá třídu k výpočtu jednotlivých červené, zelené a modré součásti barvy v hsv nebo HSL reprezentace. Tato metoda není určena k přímému volání programátorem. Vstupní parametry jsou hodnoty, které závisí na převodovém algoritmu.

Chcete-li převést barvu HSV nebo HSL na reprezentaci RGB, zavolejte jednu z následujících metod:

- [CDrawingManager::HSVtoRGB](#hsvtorgb)

- [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)

- [CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)

## <a name="cdrawingmanagermirrorrect"></a><a name="mirrorrect"></a>CDrawingManager::MirrorRect

Překlopí obdélníkovou oblast.

```cpp
void MirrorRect(
    CRect rect,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[v] Ohraničovací obdélník oblasti překlopit.

*bHorz*<br/>
[v] Logický parametr, který označuje, zda se obdélník překlopí vodorovně nebo svisle.

### <a name="remarks"></a>Poznámky

Tato metoda můžete překlopit libovolnou `CDrawingManager` oblast kontextu zařízení vlastněné třídy. Pokud *je hodnota bHorz* nastavena na hodnotu TRUE, tato metoda převrátí oblast vodorovně. V opačném případě převrátí oblast svisle.

## <a name="cdrawingmanagerpixelalpha"></a><a name="pixelalpha"></a>CDrawingManager::PixelAlpha

Vypočítá konečnou barvu pro poloprůhledný pixel.

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
[v] Počáteční barva pro pixel.

*Procent*<br/>
[v] Číslo mezi 0 a 100, které představuje procento průhlednosti. Hodnota 100 označuje, že počáteční barva je zcela průhledná.

*percentR*<br/>
[v] Číslo mezi 0 a 100, které představuje procento průhlednosti pro červenou komponentu.

*percentG*<br/>
[v] Číslo mezi 0 a 100, které představuje procento průhlednosti zelené komponenty.

*percentB*<br/>
[v] Číslo mezi 0 a 100, které představuje procento průhlednosti pro modrou komponentu.

*dstPixel*<br/>
[v] Základní barva pro pixel.

### <a name="return-value"></a>Návratová hodnota

Konečná barva poloprůhledného obrazového bodu.

### <a name="remarks"></a>Poznámky

Toto je pomocná třída pro barvení poloprůhledných rastrových obrázků a není navržena tak, aby byla volána přímo programátorem.

Při použití verze metody, která má *dstPixel*, konečná barva je kombinací *dstPixel* a *srcPixel*. Barva *srcPixel* je částečně průhledná barva nad základní barvou *dstPixel*.

## <a name="cdrawingmanagerprepareshadowmask"></a><a name="prepareshadowmask"></a>CDrawingManager::PrepareShadowMask

Vytvoří bitmapu, kterou lze použít jako stín.

```
static HBITMAP __stdcall PrepareShadowMask (
    int nDepth,
    COLORREF clrBase,
    int iMinBrightness = 0,
    int iMaxBrightness = 100);
```

### <a name="parameters"></a>Parametry

*nHloubka*<br/>
[v] Šířka a výška stínu.

*clrBase*<br/>
[v] Barva stínu.

*iMinBrightness*<br/>
[v] Minimální jas stínu.

*iMaxBrightness*<br/>
[v] Maximální jas stínu.

### <a name="return-value"></a>Návratová hodnota

Popisovač vytvořené bitmapy, pokud je tato metoda úspěšná; jinak NULL.

### <a name="remarks"></a>Poznámky

Pokud *nDepth* je nastavena na hodnotu 0, tato metoda ukončí a vrátí NULL. Pokud *nHloubka* je menší než 3, šířka a výška stínu jsou nastaveny na 3 pixely.

## <a name="cdrawingmanagerrgbtohsl"></a><a name="rgbtohsl"></a>CDrawingManager::RGBtoHSL

Převede barvu z reprezentace červené, zelené a modré (RGB) na reprezentaci odstínu, sytosti a světlosti (HSL).

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
|*Rgb*|[v] Barva v hodnotách RGB.|
|*H*|[out] Ukazatel na double, kde metoda ukládá odstín pro barvu.|
|*S*|[out] Ukazatel na double, kde metoda ukládá sytost pro barvu.|
|*L*|[out] Ukazatel na double, kde metoda ukládá světlost pro barvu.|

### <a name="remarks"></a>Poznámky

Barvu lze reprezentováno jako HSV (odstín, sytost a hodnota), HSL (odstín, sytost a světelnost) nebo RGB (červená, zelená a modrá). Další informace o různých reprezentacích barev naleznete v tématu [Barva](/windows/win32/uxguide/vis-color).

Vrácená hodnota pro *H* je reprezentována jako zlomek mezi 0 a 1, kde 0 a 1 představují červenou. Vrácené hodnoty pro *S* a *L* jsou čísla mezi 0 a 1.

## <a name="cdrawingmanagerrgbtohsv"></a><a name="rgbtohsv"></a>CDrawingManager::RGBtoHSV

Převede barvu z reprezentace RGB na reprezentaci HSV.

```
static void __stdcall RGBtoHSV(
    COLORREF rgb,
    double* H,
    double* S,
    double* V);
```

### <a name="parameters"></a>Parametry

*Rgb*<br/>
[v] Barva, kterou chcete převést v reprezentaci RGB.

*H*<br/>
[out] Ukazatel na double, kde tato metoda ukládá výsledný odstín pro barvu.

*S*<br/>
[out] Ukazatel na double, kde tato metoda ukládá výsledné sytost pro barvu.

*V*<br/>
[out] Ukazatel na double, kde tato metoda ukládá výslednou hodnotu pro barvu.

### <a name="remarks"></a>Poznámky

Barvu lze reprezentováno jako HSV (odstín, sytost a hodnota), HSL (odstín, sytost a světelnost) nebo RGB (červená, zelená a modrá). Další informace o různých reprezentacích barev naleznete v tématu [Barva](/windows/win32/uxguide/vis-color).

Vrácená hodnota pro *H* je číslo mezi 0 a 360, kde 0 a 360 označují červenou. Vrácené hodnoty pro *S* a *V* jsou čísla mezi 0 a 1.

## <a name="cdrawingmanagersetalphapixel"></a><a name="setalphapixel"></a>CDrawingManager::SetAlphaPixel

Vybarví průhledný obrazový bod v bitmapě.

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

*pBity*<br/>
[v] Ukazatel na bitové hodnoty pro bitovou mapu.

*Rect*<br/>
[v] Obdélníková oblast v aplikaci. Správce výkresu nakreslí stín pod a vpravo od této oblasti.

*X*<br/>
[v] Vodorovná souřadnice obrazového bodu na barvu.

*Y*<br/>
[v] Svislá souřadnice obrazového bodu na barvu.

*Procent*<br/>
[v] Procento průhlednosti.

*iShadowVelikost*<br/>
[v] Šířka a výška stínu.

*clrBase*<br/>
[v] Barva stínu.

*bIsPrávo*<br/>
[v] Logický parametr, který označuje, který obrazový bod má být barevný. Další informace naleznete v části Poznámky.

### <a name="remarks"></a>Poznámky

Tato metoda je pomocná metoda, která se používá [cdrawingmanager::DrawShadow](#drawshadow) metoda. Doporučujeme, že pokud chcete nakreslit `CDrawingManager::DrawShadow` stín, místo toho volejte.

Pokud je *hodnota bIsRight* nastavena na hodnotu TRUE, změří se obrazový bod na barvu *x* obrazových bodů od pravého okraje *rect*. Pokud je false, pixel na barvu se měří *x* pixelů od levého okraje *rect*.

## <a name="cdrawingmanagersetpixel"></a><a name="setpixel"></a>CDrawingManager::SetPixel

Změní jeden obrazový bod v bitmapě na zadanou barvu.

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
|*pBity*|[v] Ukazatel na bitové hodnoty bitmapy.|
|*Cx*|[v] Celková šířka bitmapy.|
|*Cy*|[v] Celková výška bitmapy.|
|*X*|[v] Souřadnice x obrazového bodu v bitmapě, kterou chcete změnit.|
|*Y*|[v] Souřadnice y obrazového bodu v bitmapě, kterou chcete změnit.|
|*color*|[v] Nová barva pro obrazový bod identifikovaný dodanými souřadnicemi.|

## <a name="cdrawingmanagersmartmixcolors"></a><a name="smartmixcolors"></a>CDrawingManager::SmartMixColors

Zkombinuje dvě barvy na základě váženého poměru.

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
|*barva1*|[v] První barva pro míchání.|
|*barva2*|[v] Druhá barva pro míchání.|
|*dblLumRatio*|[v] Poměr pro svítivost nové barvy. `SmartMixColors`vynásobí světelnost smíšené barvy tímto poměrem před určením konečné barvy.|
|*k1*|[v] Vážený poměr pro první barvu.|
|*k2*|[v] Vážený poměr pro druhou barvu.|

### <a name="return-value"></a>Návratová hodnota

Barva, která představuje váženou směs dodaných barev.

### <a name="remarks"></a>Poznámky

Tato metoda se nezdaří s chybou, pokud *buď k1* nebo *k2* je menší než nula. Pokud jsou oba tyto parametry nastaveny `RGB(0, 0, 0)`na hodnotu 0, vrátí metoda .

Vážený poměr se vypočítá podle následujícího vzorce: \* (barva1 \* k1 + barva2 k2)/(k1 + k2). Po stanovení váženého poměru metoda vypočítá světelnost pro smíšenou barvu. Potom násobí svítivost *dblLumRatio*. Pokud je hodnota větší než 1,0, metoda nastaví světelnost pro smíšenou barvu na novou hodnotu. V opačném případě je svítivost nastavena na 1,0.

## <a name="cdrawingmanagerdrawrotated"></a><a name="drawrotated"></a>CDrawingManager::DrawRotated

Otočí zdrojový obsah řadiče domény uvnitř daného obdélníku o 90 stupňů.

```cpp
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

*bPoručidla ve směru hodinových ru*<br/>
TRUE označuje otočení o +90 stupňů; FALSE označuje otočení -90 stupňů.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
