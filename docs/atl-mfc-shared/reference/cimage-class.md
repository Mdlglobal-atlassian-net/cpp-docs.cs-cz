---
title: Cimage – třída
ms.date: 02/01/2018
f1_keywords:
- CImage
- ATLIMAGE/ATL::CImage
- ATLIMAGE/ATL::CImage::CImage
- ATLIMAGE/ATL::CImage::AlphaBlend
- ATLIMAGE/ATL::CImage::Attach
- ATLIMAGE/ATL::CImage::BitBlt
- ATLIMAGE/ATL::CImage::Create
- ATLIMAGE/ATL::CImage::CreateEx
- ATLIMAGE/ATL::CImage::Destroy
- ATLIMAGE/ATL::CImage::Detach
- ATLIMAGE/ATL::CImage::Draw
- ATLIMAGE/ATL::CImage::GetBits
- ATLIMAGE/ATL::CImage::GetBPP
- ATLIMAGE/ATL::CImage::GetColorTable
- ATLIMAGE/ATL::CImage::GetDC
- ATLIMAGE/ATL::CImage::GetExporterFilterString
- ATLIMAGE/ATL::CImage::GetHeight
- ATLIMAGE/ATL::CImage::GetImporterFilterString
- ATLIMAGE/ATL::CImage::GetMaxColorTableEntries
- ATLIMAGE/ATL::CImage::GetPitch
- ATLIMAGE/ATL::CImage::GetPixel
- ATLIMAGE/ATL::CImage::GetPixelAddress
- ATLIMAGE/ATL::CImage::GetTransparentColor
- ATLIMAGE/ATL::CImage::GetWidth
- ATLIMAGE/ATL::CImage::IsDIBSection
- ATLIMAGE/ATL::CImage::IsIndexed
- ATLIMAGE/ATL::CImage::IsNull
- ATLIMAGE/ATL::CImage::IsTransparencySupported
- ATLIMAGE/ATL::CImage::Load
- ATLIMAGE/ATL::CImage::LoadFromResource
- ATLIMAGE/ATL::CImage::MaskBlt
- ATLIMAGE/ATL::CImage::PlgBlt
- ATLIMAGE/ATL::CImage::ReleaseDC
- ATLIMAGE/ATL::CImage::ReleaseGDIPlus
- ATLIMAGE/ATL::CImage::Save
- ATLIMAGE/ATL::CImage::SetColorTable
- ATLIMAGE/ATL::CImage::SetPixel
- ATLIMAGE/ATL::CImage::SetPixelIndexed
- ATLIMAGE/ATL::CImage::SetPixelRGB
- ATLIMAGE/ATL::CImage::SetTransparentColor
- ATLIMAGE/ATL::CImage::StretchBlt
- ATLIMAGE/ATL::CImage::TransparentBlt
helpviewer_keywords:
- jpeg files
- bitmaps [C++], ATL and MFC support for
- images [C++], ATL and MFC support for
- gif files, ATL and MFC support
- .gif files, ATL and MFC support
- PNG files, ATL and MFC support
- CImage class
- transparent color
ms.assetid: 52861e3d-bf7e-481f-a240-90e88f76c490
ms.openlocfilehash: 14a4691e0c1f25a8f9e8b2b652c6e582f51c954a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58775943"
---
# <a name="cimage-class"></a>Cimage – třída

`CImage` poskytuje podporu rozšířenou rastrový obrázek, včetně možnosti k načtení a uložení Image ve formátu JPEG, GIF, BMP a Portable Network Graphics (PNG).

> [!IMPORTANT]
> Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CImage
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CImage::CImage](#cimage)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CImage::AlphaBlend](#alphablend)|Zobrazí rastrové obrázky, být transparentní nebo poloprůhledných pixelů.|
|[CImage::Attach](#attach)|Připojí HBITMAP k `CImage` objektu. Je možné s rastrových obrázků bez DIB části nebo části DIB rastrových obrázků.|
|[CImage::BitBlt](#bitblt)|Zkopíruje bitmapu ze kontext zdrojového zařízení pro toto aktuální kontext zařízení.|
|[CImage::Create](#create)|Rastrový obrázek části DIB vytvoří a připojí ho k dříve vytvořeného `CImage` objektu.|
|[CImage::CreateEx](#createex)|Rastrový obrázek části DIB (s další parametry) vytvoří a připojí ho k dříve vytvořeného `CImage` objektu.|
|[CImage::Destroy](#destroy)|Odpojí rastrový obrázek z `CImage` objektu a odstraní rastrového obrázku.|
|[CImage::Detach](#detach)|Odpojí rastrový obrázek z `CImage` objektu.|
|[CImage::Draw](#draw)|Zkopíruje bitmapu ze zdrojového obdélníku do cílového obdélníku. `Draw` Roztáhne nebo komprimuje rastrový obrázek, aby odpovídala rozměrům cílového obdélníku, v případě potřeby a zpracovává alfa míchání a průhledné barvy.|
|[CImage::GetBits](#getbits)|Načte ukazatel na skutečné pixel hodnoty rastrového obrázku.|
|[CImage::GetBPP](#getbpp)|Načte bitů na pixel.|
|[CImage::GetColorTable](#getcolortable)|Načte červená, zelená, modrá barva hodnoty (RGB) z rozsahu položek v tabulce barev.|
|[CImage::GetDC](#getdc)|Načte kontext zařízení, do kterého je vybrána aktuální rastrového obrázku.|
|[CImage::GetExporterFilterString](#getexporterfilterstring)|Vyhledá dostupné image formátů a jejich popisy.|
|[CImage::GetHeight](#getheight)|Získá výšku aktuální obrázku v pixelech.|
|[CImage::GetImporterFilterString](#getimporterfilterstring)|Vyhledá dostupné image formátů a jejich popisy.|
|[CImage::GetMaxColorTableEntries](#getmaxcolortableentries)|Získá maximální počet položek v tabulce barev.|
|[CImage::GetPitch](#getpitch)|Načte od aktuální obrázek v bajtech.|
|[CImage::GetPixel](#getpixel)|Zjišťuje barvu pixelu určené *x* a *y*.|
|[CImage::GetPixelAddress](#getpixeladdress)|Načte adresu daného pixelů.|
|[CImage::GetTransparentColor](#gettransparentcolor)|Načte pozici průhlednou barvu v tabulce barev.|
|[CImage::GetWidth](#getwidth)|Zjišťuje šířku aktuálního obrázku v pixelech.|
|[CImage::IsDIBSection](#isdibsection)|Určuje, jestli je připojené rastrový obrázek DIB části.|
|[CImage::IsIndexed](#isindexed)|Označuje, že rastrový obrázek barvy se mapují na indexované palety.|
|[CImage::IsNull](#isnull)|Označuje, pokud je aktuálně načtená zdrojovou bitmapu.|
|[CImage::IsTransparencySupported](#istransparencysupported)|Určuje, jestli aplikace podporuje transparentní rastrových obrázků.|
|[CImage::Load](#load)|Načte obrázek ze zadaného souboru.|
|[CImage::LoadFromResource](#loadfromresource)|Načte obrázek ze zadaného prostředku.|
|[CImage::MaskBlt](#maskblt)|Kombinuje data o barvách pro zdrojové a cílové bitmapy, pomocí zadané masce a rastrovou operaci.|
|[CImage::PlgBlt](#plgblt)|Provede přenos bitového bloku z obdélníku v kontextu zdrojového zařízení do rovnoběžník v kontextu cílového zařízení.|
|[CImage::ReleaseDC](#releasedc)|Uvolní kontextu zařízení, která byla načtena s [CImage::GetDC](#getdc).|
|[CImage::ReleaseGDIPlus](#releasegdiplus)|Uvolní prostředky využívané třídou rozhraní GDI +. Musí být volána k uvolnění prostředků vytvořené globální `CImage` objektu.|
|[CImage::Save](#save)|Uloží obrázek jako zadaného typu. `Save` Nelze zadat možnosti bitové kopie.|
|[CImage::SetColorTable](#setcolortable)|Nastaví červená, zelená, modrá RGB) barevné hodnoty v rozsahu položek v tabulce barev DIB oddílu.|
|[CImage::SetPixel](#setpixel)|Nastaví obrazového bodu na zadaných souřadnicích zadanou barvu.|
|[CImage::SetPixelIndexed](#setpixelindexed)|Nastaví obrazového bodu na zadaných souřadnicích barvu na zadaném indexu na paletě.|
|[CImage::SetPixelRGB](#setpixelrgb)|Nastaví obrazového bodu na zadaných souřadnicích hodnotě zadané červené, zelené, modré (RGB).|
|[CImage::SetTransparentColor](#settransparentcolor)|Nastaví index založený na barvy pracovat jako průhledná. Pouze jednu barvu na paletě může být průhledná.|
|[CImage::StretchBlt](#stretchblt)|Zkopíruje bitmapu ze zdrojového obdélníku do cílového obdélníku a roztáhne nebo ji zkomprimuje tak, aby odpovídala rozměrům cílového obdélníku a v případě potřeby.|
|[CImage::TransparentBlt](#transparentblt)|Zkopíruje bitmapu s průhlednou barvu z kontextu zdrojového zařízení pro toto aktuální kontext zařízení.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CImage::operator HBITMAP](#operator_hbitmap)|Vrátí popisovač Windows připojené k `CImage` objektu.|

## <a name="remarks"></a>Poznámky

`CImage` přijímá rastrové obrázky, které jsou buď oddíly bitmap nezávislých na zařízení (DIB) nebo ne; Můžete však použít [vytvořit](#create) nebo [CImage::Load](#load) s pouze DIB oddíly. Můžete připojit bez DIB rastrový obrázek části k `CImage` pomocí [připojit](#attach), ale nemůžete použít následující `CImage` metody, které podporují pouze rastrové obrázky části DIB:

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

Chcete-li zjistit, zda připojené rastrového obrázku je oddíl DIB, zavolejte [IsDibSection](#isdibsection).

> [!NOTE]
> V aplikaci Visual Studio .NET 2003, tato třída sleduje počet počet `CImage` objekty vytvořené. Vždy, když počet přejde na hodnotu 0, funkce `GdiplusShutdown` je automaticky volána uvolnit prostředky využívané třídou rozhraní GDI +. To zajistí, že některé `CImage` objektů vytvořených přímo nebo nepřímo knihoven DLL jsou vždy správně zničeny a že `GdiplusShutdown` není volána z `DllMain`.

> [!NOTE]
> Pomocí globálního `CImage` objektů v knihovně DLL se nedoporučuje. Pokud je třeba použít globální `CImage` objektů v knihovně DLL, volání [CImage::ReleaseGDIPlus](#releasegdiplus) explicitně uvolnit prostředky využívané třídou rozhraní GDI +.

`CImage` Nelze vybrat, do nového [CDC](../../mfc/reference/cdc-class.md). `CImage` Vytvoří vlastní HDC bitové kopie. Protože HBITMAP lze vybrat pouze do jedné HDC najednou, HBITMAP přidružené `CImage` nelze vybrat, do jiného HDC. Pokud potřebujete CDC, načtení HDC z `CImage` a přiřaďte mu [CDC::FromHandle] (.. /.. /MFC/reference/CDC-Class.MD#cdc__fromhandle.

## <a name="example"></a>Příklad

```cpp
// Get a CDC for the image
CDC* pDC = CDC::FromHandle(m_myImage.GetDC());

// Use pDC here
pDC->Rectangle(0, 40, 100, 50);
m_myImage.ReleaseDC();
```

Při použití `CImage` v projektu knihovny MFC, mějte na paměti očekávat ukazatele na členské funkce, které ve vašem projektu [cbitmap –](../../mfc/reference/cbitmap-class.md) objektu. Pokud chcete použít `CImage` s funkcí, jako je [CMenu::AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu), použijte [CBitmap::FromHandle](../../mfc/reference/cbitmap-class.md#fromhandle), předáváme vaše `CImage` HBITMAP a použití vráceného `CBitmap*`.

## <a name="example"></a>Příklad

```cpp
void CMyDlg::OnRButtonDown(UINT nFlags, CPoint point)
{
    UNREFERENCED_PARAMETER(nFlags);

    CBitmap* pBitmap = CBitmap::FromHandle(m_myImage);
    m_pmenuPop->AppendMenu(0, ID_BMPCOMMAND, pBitmap);
    ClientToScreen(&point);
    m_pmenuPop->TrackPopupMenu(TPM_RIGHTBUTTON | TPM_LEFTALIGN, point.x,
    point.y, this);
}
```

Prostřednictvím `CImage`, máte přístup k bitů DIB oddílu. Můžete použít `CImage` objektu kdekoli jste dříve používali Win32 HBITMAP nebo DIB oddílu.

Můžete použít `CImage` z knihovny MFC ani ATL.

> [!NOTE]
> Při vytváření projektu pomocí `CImage`, je nutné definovat `CString` teprve potom zahrňte `atlimage.h`. Pokud váš projekt používá ATL bez knihovny MFC, zahrňte `atlstr.h` teprve potom zahrňte `atlimage.h`. Pokud váš projekt používá MFC (nebo pokud je projekt knihovny ATL pomocí podpory knihovny MFC), zahrnují `afxstr.h` teprve potom zahrňte `atlimage.h`.<br/>
> <br/>
> Podobně, je nutné zahrnout `atlimage.h` teprve potom zahrňte `atlimpl.cpp`. K tomu snadno zahrnout `atlimage.h` ve vašich `stdafx.h`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlimage.h

##  <a name="alphablend"></a>  CImage::AlphaBlend

Zobrazí rastrové obrázky, být transparentní nebo poloprůhledných pixelů.

```
BOOL AlphaBlend(
    HDC hDestDC,
    int xDest,
    int yDest,
    BYTE bSrcAlpha = 0xff,
    BYTE bBlendOp = AC_SRC_OVER) const throw();

BOOL AlphaBlend(
    HDC hDestDC,
    const POINT& pointDest,
    BYTE bSrcAlpha = 0xff,
    BYTE bBlendOp = AC_SRC_OVER) const throw();

BOOL AlphaBlend(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight,
    BYTE bSrcAlpha = 0xff,
    BYTE bBlendOp = AC_SRC_OVER);

BOOL AlphaBlend(
    HDC hDestDC,
    const RECT& rectDest,
    const RECT& rectSrc,
    BYTE bSrcAlpha = 0xff,
    BYTE bBlendOp = AC_SRC_OVER);
```

### <a name="parameters"></a>Parametry

*hDestDC*<br/>
Popisovač kontextu cílového zařízení.

*xDest*<br/>
Souřadnice x, v logických jednotkách, levého horního rohu cílového obdélníku.

*yDest*<br/>
Souřadnice y, v logických jednotkách, levého horního rohu cílového obdélníku.

*bSrcAlpha*<br/>
Hodnotu alfa průhlednost na pro přechod na celý zdrojovou bitmapu. Výchozí 0xff (255) se předpokládá, že vaše image je neprůhledný, a chcete použít jednotlivých pixelů pouze alfanumerické hodnoty.

*bBlendOp*<br/>
Funkce alfa blending pro zdroj a cílovým bitmapám, globální alfa hodnotu použít celý zdrojovou bitmapu a informace o formátu pro zdrojovou bitmapu. Funkce blendu zdrojových a cílových jsou aktuálně omezené na AC_SRC_OVER.

*pointDest*<br/>
Odkaz na [bodu](/previous-versions/dd162805\(v=vs.85\)) strukturu, která identifikuje levém horním rohu cílového obdélníku v logických jednotkách.

*nDestWidth*<br/>
Šířka v logické jednotky cílového obdélníku.

*nDestHeight*<br/>
Výška v logických jednotkách cílového obdélníku.

*xSrc*<br/>
Logickou souřadnici x levého horního rohu zdrojového obdélníku.

*ySrc*<br/>
Logickou souřadnici y levého horního rohu zdrojového obdélníku.

*nSrcWidth*<br/>
Šířka v logických jednotkách, zdrojového obdélníku.

*nSrcHeight*<br/>
Výška v logických jednotkách, zdrojového obdélníku.

*rectDest*<br/>
Odkaz na [RECT](/previous-versions/dd162897\(v=vs.85\)) strukturu, identifikace cíle.

*rectSrc*<br/>
Odkaz na `RECT` strukturu, identifikace zdroji.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Prolnutí alfa bitmap podporují prolnutí barvu na základě jednotlivých pixelů.

Když *bBlendOp* je nastavena na výchozí hodnotu AC_SRC_OVER zdrojovou bitmapu umístěno nad cílovou bitmapu podle hodnoty alfa zdroj pixelů.

##  <a name="attach"></a>  CImage::Attach

Připojí *hBitmap* k `CImage` objektu.

```
void Attach(HBITMAP hBitmap, DIBOrientation eOrientation = DIBOR_DEFAULT) throw();
```

### <a name="parameters"></a>Parametry

*hBitmap*<br/>
Popisovač HBITMAP.

*eOrientation*<br/>
Určuje orientaci rastrového obrázku. Může být jedna z následujících akcí:

- DIBOR_DEFAULT orientace rastrového obrázku se určuje podle operačního systému.

- DIBOR_BOTTOMUP řádky rastrového obrázku jsou v opačném pořadí. To způsobí, že [CImage::GetBits](#getbits) a vrátí ukazatel na konci rastrový obrázek vyrovnávací paměti a [CImage::GetPitch](#getpitch) se vraťte na záporné číslo.

- DIBOR_TOPDOWN řádky rastrového obrázku jsou v horní části pořadí. To způsobí, že [CImage::GetBits](#getbits) k vrácení ukazatele do prvního bajtu rastrový obrázek vyrovnávací paměti a [CImage::GetPitch](#getpitch) vrátit kladné číslo.

### <a name="remarks"></a>Poznámky

Rastrový obrázek může být bez DIB části rastrový obrázek nebo obrázek části ve formátu DIB. Zobrazit [IsDIBSection](#isdibsection) seznam metod, které můžete použít pouze s DIB části rastrových obrázků.

##  <a name="bitblt"></a>  CImage::BitBlt

Zkopíruje bitmapu ze kontext zdrojového zařízení pro toto aktuální kontext zařízení.

```
BOOL BitBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    DWORD dwROP = SRCCOPY) const throw();

BOOL BitBlt(
    HDC hDestDC,
    const POINT& pointDest,
    DWORD dwROP = SRCCOPY) const throw();

BOOL BitBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    DWORD dwROP = SRCCOPY) const throw();

BOOL BitBlt(
    HDC hDestDC,
    const RECT& rectDest,
    const POINT& pointSrc,
    DWORD dwROP = SRCCOPY) const throw();
```

### <a name="parameters"></a>Parametry

*hDestDC*<br/>
Cíl HDC.

*xDest*<br/>
Logickou souřadnici x levého horního rohu cílového obdélníku.

*yDest*<br/>
Logickou souřadnici y levého horního rohu cílového obdélníku.

*dwROP*<br/>
Rastrová operace provést. Kódy rastrové operace definovat přesně jak kombinovat bity zdroje, cíle a vzor k cíli (podle aktuálně vybraného štětce). Zobrazit [přenos bitových bloků](/windows/desktop/api/wingdi/nf-wingdi-bitblt) v sadě Windows SDK pro seznam další kódy rastrové operace a jejich popisy.

*pointDest*<br/>
A [bodu](/previous-versions/dd162805\(v=vs.85\)) struktura označující levém horním rohu cílového obdélníku.

*nDestWidth*<br/>
Šířka v logické jednotky cílového obdélníku.

*nDestHeight*<br/>
Výška v logických jednotkách cílového obdélníku.

*xSrc*<br/>
Logickou souřadnici x levého horního rohu zdrojového obdélníku.

*ySrc*<br/>
Logickou souřadnici y levého horního rohu zdrojového obdélníku.

*rectDest*<br/>
A [RECT](/previous-versions/dd162897\(v=vs.85\)) struktura označující cílového obdélníku.

*pointSrc*<br/>
A `POINT` struktura označující levém horním rohu zdrojového obdélníku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak nula.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [přenos bitových bloků](/windows/desktop/api/wingdi/nf-wingdi-bitblt) v sadě Windows SDK.

##  <a name="cimage"></a>  CImage::CImage

Vytvoří `CImage` objektu.

```
CImage() throw();
```

### <a name="remarks"></a>Poznámky

Jakmile máte vytvořený objekt, volání [vytvořit](#create), [zatížení](#load), [LoadFromResource](#loadfromresource), nebo [připojit](#attach) Chcete-li objekt připojit rastrový obrázek.

**Poznámka:** v sadě Visual Studio, tato třída sleduje počet počet `CImage` objekty vytvořené. Vždy, když počet přejde na hodnotu 0, funkce `GdiplusShutdown` je automaticky volána uvolnit prostředky využívané třídou rozhraní GDI +. To zajistí, že některé `CImage` objektů vytvořených přímo nebo nepřímo knihoven DLL jsou vždy správně zničeny a že `GdiplusShutdown` není volána z funkce DllMain.

Pomocí globálního `CImage` objektů v knihovně DLL se nedoporučuje. Pokud je třeba použít globální `CImage` objektů v knihovně DLL, volání [CImage::ReleaseGDIPlus](#releasegdiplus) explicitně uvolnit prostředky využívané třídou rozhraní GDI +.

##  <a name="create"></a>  CImage::Create

Vytvoří `CImage` rastrového obrázku a jeho připojení k dříve vytvořeného `CImage` objektu.

```
BOOL Create(
    int nWidth,
    int nHeight,
    int nBPP,
    DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parametry

*nWidth*<br/>
Šířka `CImage` rastrového obrázku v pixelech.

*nHeight*<br/>
Výška `CImage` rastrového obrázku v pixelech. Pokud *nHeight* kladné rastrového obrázku je DIB zdola nahoru a jeho původ levého dolního rohu. Pokud *nHeight* je záporný, je rastrového obrázku DIB shora dolů a jeho původ levého horního rohu.

*nBPP*<br/>
Počet bitů na pixel rastrového obrázku nastaven. Obvykle 4, 8, 16, 24 nebo 32. Může být 1 pro monochromatický rastrové obrázky nebo masky.

*dwFlags*<br/>
Určuje, zda má objekt bitmap alfa kanál. Může být kombinace nuly nebo více z následujících hodnot:

- *createAlphaChannel* lze použít pouze v případě *nBPP* je 32, a *eCompression* je BI_RGB. -Li zadána, vytvořené image má hodnotu alfa (průhlednost) pro každý pixel, uložené v 4 bajtů každý pixel (nepoužívané v imagi jiné než alfanumerické 32-bit). Tento kanál alfa je automaticky použitá při volání metody [CImage::AlphaBlend](#alphablend).

> [!NOTE]
> Ve volání do [CImage::Draw](#draw), bitové kopie s kanálem alfa jsou automaticky alfa prolnuty do cíle.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

##  <a name="createex"></a>  CImage::CreateEx

Vytvoří `CImage` rastrového obrázku a jeho připojení k dříve vytvořeného `CImage` objektu.

```
BOOL CreateEx(
    int nWidth,
    int nHeight,
    int nBPP,
    DWORD eCompression,
    const DWORD* pdwBitmasks = NULL,
    DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parametry

*nWidth*<br/>
Šířka `CImage` rastrového obrázku v pixelech.

*nHeight*<br/>
Výška `CImage` rastrového obrázku v pixelech. Pokud *nHeight* kladné rastrového obrázku je DIB zdola nahoru a jeho původ levého dolního rohu. Pokud *nHeight* je záporný, je rastrového obrázku DIB shora dolů a jeho původ levého horního rohu.

*nBPP*<br/>
Počet bitů na pixel rastrového obrázku nastaven. Obvykle 4, 8, 16, 24 nebo 32. Může být 1 pro monochromatický rastrové obrázky nebo masky.

*eCompression*<br/>
Určuje typ komprese pro komprimované rastrový obrázek zdola nahoru (DIB shora dolů nejde zkomprimovat). Může být jedna z následujících hodnot:

- BI_RGB formát nekomprimované. Zadání této hodnoty při volání metody `CImage::CreateEx` je ekvivalentní volání `CImage::Create`.

- Tabulky barev se skládá ze tří masky barva DWORD, které v uvedeném pořadí, zadejte komponenty červené, zelené a modré každý pixel BI_BITFIELDS formát nekomprimované. Toto je platný při použití s 16 a 32 bpp rastrových obrázků.

*pdwBitfields*<br/>
Použít jenom v případě *eCompression* je nastavena na BI_BITFIELDS, jinak ho musí mít hodnotu NULL. Ukazatel na pole tři vyčíslení DWORD zadání bity každý pixel, které se používají pro komponenty červené, zelené a modré barvy. Informace o omezeních pro bitová pole najdete v tématu [BITMAPINFOHEADER](https://msdn.microsoft.com/library/windows/desktop/dd183376) v sadě Windows SDK.

*dwFlags*<br/>
Určuje, zda má objekt bitmap alfa kanál. Může být kombinace nuly nebo více z následujících hodnot:

- *createAlphaChannel* lze použít pouze v případě *nBPP* je 32, a *eCompression* je BI_RGB. -Li zadána, vytvořené image má hodnotu alfa (průhlednost) pro každý pixel, uložené v 4 bajtů každý pixel (nepoužívané v imagi jiné než alfanumerické 32-bit). Tento kanál alfa je automaticky použitá při volání metody [CImage::AlphaBlend](#alphablend).

   > [!NOTE]
   > Ve volání do [CImage::Draw](#draw), bitové kopie s kanálem alfa jsou automaticky alfa prolnuty do cíle.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE v případě úspěšného ověření. V opačném případě FALSE.

### <a name="example"></a>Příklad

Následující příklad vytvoří pomocí 16 bitů určený ke kódování každý pixel rastrového obrázku 100 x 100 pixelů. V dané 16bitové pixel bits 0 – 3 kódování červené, bits 4 – 7 kódování zelené a bits 8-11 kódování modrá. Zbývající bity 4 se nepoužívají.

```cpp
DWORD adwBitmasks[3] = { 0x0000000f, 0x000000f0, 0x00000f00 };
m_myImage.CreateEx(100, 100, 16, BI_BITFIELDS, adwBitmasks, 0);
```

##  <a name="destroy"></a>  CImage::Destroy

Odpojí rastrový obrázek z `CImage` objektu a odstraní rastrového obrázku.

```
void Destroy() throw();
```

##  <a name="detach"></a>  CImage::Detach

Odpojí rastrový obrázek z `CImage` objektu.

```
HBITMAP Detach() throw();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač na rastrový obrázek odpojit, nebo hodnota NULL, pokud je připojena žádná rastrového obrázku.

##  <a name="draw"></a>  CImage::Draw

Zkopíruje bitmapu ze kontext zdrojového zařízení k aktuálnímu kontextu zařízení.

```
BOOL Draw(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight) const throw();

BOOL Draw(
    HDC hDestDC,
    const RECT& rectDest,
    const RECT& rectSrc) const throw();

BOOL Draw(
    HDC hDestDC,
    int xDest,
    int yDest) const throw();

BOOL Draw(
    HDC hDestDC,
    const POINT& pointDest) const throw();

BOOL Draw(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight) const throw();

BOOL Draw(
    HDC hDestDC,
    const RECT& rectDest) const throw();
```

### <a name="parameters"></a>Parametry

*hDestDC*<br/>
Popisovač kontextu cílového zařízení.

*xDest*<br/>
Souřadnice x, v logických jednotkách, levého horního rohu cílového obdélníku.

*yDest*<br/>
Souřadnice y, v logických jednotkách, levého horního rohu cílového obdélníku.

*nDestWidth*<br/>
Šířka v logické jednotky cílového obdélníku.

*nDestHeight*<br/>
Výška v logických jednotkách cílového obdélníku.

*xSrc*<br/>
Souřadnice x, v logických jednotkách, levého horního rohu zdrojového obdélníku.

*ySrc*<br/>
Souřadnice y, v logických jednotkách, levého horního rohu zdrojového obdélníku.

*nSrcWidth*<br/>
Šířka v logických jednotkách, zdrojového obdélníku.

*nSrcHeight*<br/>
Výška v logických jednotkách, zdrojového obdélníku.

*rectDest*<br/>
Odkaz na [RECT](/previous-versions/dd162897\(v=vs.85\)) strukturu, identifikace cíle.

*rectSrc*<br/>
Odkaz na `RECT` strukturu, identifikace zdroji.

*pointDest*<br/>
Odkaz na [bodu](/previous-versions/dd162805\(v=vs.85\)) strukturu, která identifikuje levém horním rohu cílového obdélníku v logických jednotkách.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

`Draw` provede stejné operace jako [StretchBlt](#stretchblt), pokud image obsahuje průhlednou barvu nebo alfa kanálu. V takovém případě `Draw` provede stejné operace jako [TransparentBlt](#transparentblt) nebo [AlphaBlend](#alphablend) podle potřeby.

Verze `Draw` zdrojového obdélníku, který není zadán, celého zdrojového obrázku je výchozí nastavení. Pro verzi `Draw` , která neurčuje velikost cílového obdélníku, velikost zdrojového obrázku je výchozí a žádné roztažení nebo zmenšení vyvolá.

##  <a name="getbits"></a>  CImage::GetBits

Načte ukazatel na skutečné bitové hodnoty daného pixel v rastrový obrázek.

```
void* GetBits() throw();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel do vyrovnávací paměti rastrového obrázku. Pokud bitmapy DIB zdola nahoru, ukazatel ukazuje téměř na konci vyrovnávací paměti. Pokud bitmapy DIB shora dolů, ukazatel odkazuje na první bajt vyrovnávací paměti.

### <a name="remarks"></a>Poznámky

Pomocí tohoto ukazatele, včetně jejich hodnoty vrácené [GetPitch](#getpitch), můžete najít a změnit jednotlivých pixelech ve bitovou kopii.

> [!NOTE]
> Tato metoda podporuje pouze DIB části rastrové obrázky; v důsledku toho přístup pixelech `CImage` stejně jako byste to udělali pixelů DIB části objektu. Vrácený ukazatel odkazuje na pixel v umístění (0, 0).

##  <a name="getbpp"></a>  CImage::GetBPP

Načte hodnotu bitů na pixel.

```
int GetBPP() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Počet bitů na pixel.

### <a name="remarks"></a>Poznámky

Tato hodnota určuje počet bitů, které definují každý pixel a maximální počet barev v rastrového obrázku.

Bitů na pixel, je obvykle 1, 4, 8, 16, 24 nebo 32. Zobrazit `biBitCount` členem [BITMAPINFOHEADER](https://msdn.microsoft.com/library/windows/desktop/dd183376) v sadě Windows SDK pro další informace o této hodnotě.

##  <a name="getcolortable"></a>  CImage::GetColorTable

Načte červená, zelená, modrá barva hodnoty (RGB) z rozsahu položek na paletě DIB oddílu.

```
void GetColorTable(
    UINT iFirstColor,
    UINT nColors,
    RGBQUAD* prgbColors) const throw();
```

### <a name="parameters"></a>Parametry

*iFirstColor*<br/>
Index tabulky barev první položky určené k načtení.

*nColors*<br/>
Počet zápisy v tabulce barev pro načtení.

*prgbColors*<br/>
Ukazatel na pole [RGBQUAD](/windows/desktop/api/wingdi/ns-wingdi-tagrgbquad) struktury načíst barvu tabulky položky.

##  <a name="getdc"></a>  CImage::GetDC

Načte kontext zařízení, který nemá aktuálně vybrán do něj obrázek.

```
HDC GetDC() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač kontextu zařízení.

### <a name="remarks"></a>Poznámky

Pro každé volání `GetDC`, musíte mít následující volání [ReleaseDC](#releasedc).

##  <a name="getexporterfilterstring"></a>  CImage::GetExporterFilterString

Vyhledá dostupné image formáty pro ukládání imagí.

```
static HRESULT GetExporterFilterString(
    CSimpleString& strExporters,
    CSimpleArray<GUID>& aguidFileTypes,
    LPCTSTR pszAllFilesDescription = NULL,
    DWORD dwExclude = excludeDefaultSave,
    TCHAR chSeparator = _T('|'));
```

### <a name="parameters"></a>Parametry

*strExporters*<br/>
Odkaz na `CSimpleString` objektu. Zobrazit **poznámky** Další informace.

*aguidFileTypes*<br/>
Pole identifikátory GUID, s každý prvek odpovídající typy souborů v řetězci. V příkladu v *pszAllFilesDescription* níže, *aguidFileTypes*[0] je GUID_NULL a zbývající hodnoty pole jsou formátu souborů obrázků, podporuje aktuální operační systém.

> [!NOTE]
> Úplný seznam konstant, naleznete v tématu **konstanty formát souboru obrázku** v sadě Windows SDK.

*pszAllFilesDescription*<br/>
Pokud tento parametr není NULL, řetězec filtru bude mít jeden další filtr na začátku seznamu. Tento filtr bude mít aktuální hodnotu *pszAllFilesDescription* jeho popis a přijímá soubory všechna rozšíření, která podporuje další Exportér v seznamu.

Příklad:

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any exporter.
CImage::GetExporterFilterString(
    strExporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
Sada bitové příznaky určující, které typy souborů k vyloučení ze seznamu. Jsou povolená příznaky:

- `excludeGIF` = soubory GIF vyloučí 0x01.

- `excludeBMP` = 0x02 soubory vyloučí BMP (rastrového obrázku Windows).

- `excludeEMF` = 0x04 soubory vyloučí EMF (Enhanced Metafile).

- `excludeWMF` = 0x08 soubory vyloučí WMF (Windows Metafile).

- `excludeJPEG` soubory JPEG vyloučí 0x10 =.

- `excludePNG` = 0x20 soubory vyloučí PNG.

- `excludeTIFF` soubory TIFF vyloučí 0x40 =.

- `excludeIcon` = 0x80 soubory vyloučí ICO (ikona Windows).

- `excludeOther` = 0x80000000 vyloučí jakýkoli jiný typ souboru není uvedené výš.

- `excludeDefaultLoad` = 0 pro načtení všech souborů, typy jsou zahrnuté ve výchozím nastavení

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF` Pro ukládání, jsou tyto soubory vyloučeny ve výchozím nastavení, protože mají obvykle zvláštní požadavky.

*chSeparator*<br/>
Oddělovač použitý mezi formátů obrázku. Zobrazit **poznámky** Další informace.

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

### <a name="remarks"></a>Poznámky

Výsledný řetězec formátu můžete předat do vaší knihovny MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md) formátuje objekt vystavit přípony souborů k dispozici bitové kopie v dialogovém okně Uložit jako.

Parametr *strExporter* má formát:

soubor description0&#124;\*.ext0&#124;filedescription1&#124;\*.ext1&#124;.. .file popis *n*&#124;\*.ext *n*&#124;&#124;

kde "&#124;" je znak oddělovače zadána `chSeparator`. Příklad:

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

Použít výchozí oddělovač '&#124;"Pokud předáte tento řetězec do knihovny MFC `CFileDialog` objektu. Pokud jste tento řetězec předat běžným dialogovým oknem uložit soubor, použijte hodnotu null oddělovač '\0'.

##  <a name="getheight"></a>  CImage::GetHeight

Získá výšku v pixelech, bitové kopie.

```
int GetHeight() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Výška v pixelech, bitové kopie.

##  <a name="getimporterfilterstring"></a>  CImage::GetImporterFilterString

Vyhledá formátů obrázku je k dispozici pro načítání obrázků.

```
static HRESULT GetImporterFilterString(
    CSimpleString& strImporters,
    CSimpleArray<GUID>& aguidFileTypes,
    LPCTSTR pszAllFilesDescription = NULL,
    DWORD dwExclude = excludeDefaultLoad,
    TCHAR chSeparator = _T('|'));
```

### <a name="parameters"></a>Parametry

*strImporters*<br/>
Odkaz na `CSimpleString` objektu. Zobrazit **poznámky** Další informace.

*aguidFileTypes*<br/>
Pole identifikátory GUID, s každý prvek odpovídající typy souborů v řetězci. V příkladu v *pszAllFilesDescription* níže, *aguidFileTypes*[0] je GUID_NULL zbývající hodnotami pole jsou formátu souborů obrázků, podporuje aktuální operační systém.

> [!NOTE]
> Úplný seznam konstant, naleznete v tématu **konstanty formát souboru obrázku** v sadě Windows SDK.

*pszAllFilesDescription*<br/>
Pokud tento parametr není NULL, řetězec filtru bude mít jeden další filtr na začátku seznamu. Tento filtr bude mít aktuální hodnotu *pszAllFilesDescription* jeho popis a přijímá soubory všechna rozšíření, která podporuje další Exportér v seznamu.

Příklad:

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any importer.
CImage::GetImporterFilterString(
    strImporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
Sada bitové příznaky určující, které typy souborů k vyloučení ze seznamu. Jsou povolená příznaky:

- `excludeGIF` = soubory GIF vyloučí 0x01.

- `excludeBMP` = 0x02 soubory vyloučí BMP (rastrového obrázku Windows).

- `excludeEMF` = 0x04 soubory vyloučí EMF (Enhanced Metafile).

- `excludeWMF` = 0x08 soubory vyloučí WMF (Windows Metafile).

- `excludeJPEG` soubory JPEG vyloučí 0x10 =.

- `excludePNG` = 0x20 soubory vyloučí PNG.

- `excludeTIFF` soubory TIFF vyloučí 0x40 =.

- `excludeIcon` = 0x80 soubory vyloučí ICO (ikona Windows).

- `excludeOther` = 0x80000000 vyloučí jakýkoli jiný typ souboru není uvedené výš.

- `excludeDefaultLoad` = 0 pro načtení všech souborů, typy jsou zahrnuté ve výchozím nastavení

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF` Pro ukládání, jsou tyto soubory vyloučeny ve výchozím nastavení, protože mají obvykle zvláštní požadavky.

*chSeparator*<br/>
Oddělovač použitý mezi formátů obrázku. Zobrazit **poznámky** Další informace.

### <a name="remarks"></a>Poznámky

Výsledný řetězec formátu můžete předat do vaší knihovny MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md) formátuje objekt vystavit přípony souborů k dispozici bitové kopie v **otevřít soubor** dialogové okno.

Parametr *strImporter* má formát:

soubor description0&#124;\*.ext0&#124;filedescription1&#124;\*.ext1&#124;.. .file popis *n*&#124;\*.ext *n*&#124;&#124;

kde "&#124;" je znak oddělovače určené *chSeparator*. Příklad:

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

Použít výchozí oddělovač '&#124;"Pokud předáte tento řetězec do knihovny MFC `CFileDialog` objektu. Použít null oddělovač '\0', pokud předáte tento řetězec do společného **otevřít soubor** dialogové okno.

##  <a name="getmaxcolortableentries"></a>  CImage::GetMaxColorTableEntries

Získá maximální počet položek v tabulce barev.

```
int GetMaxColorTableEntries() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v tabulce barev.

### <a name="remarks"></a>Poznámky

Tato metoda podporuje pouze část bitmap DIB.

##  <a name="getpitch"></a>  CImage::GetPitch

Získá výšku obrázku.

```
int GetPitch() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Výška obrázku. Pokud je návratová hodnota záporná, rastrového obrázku je DIB zdola nahoru a jeho původ levého dolního rohu. Pokud vrácená hodnota je pozitivní, rastrového obrázku je DIB shora dolů a jeho původ levého horního rohu.

### <a name="remarks"></a>Poznámky

Prvotního je vzdálenost v bajtech, mezi dvě adresy paměti, které představují začátek jeden řádek rastrového obrázku a na začátek dalšího řádku rastrového obrázku. Protože rozteč se měří v bajtech, výšku obrázku vám umožňuje určit formát pixelu. Prvotního může taky obsahovat další paměti vyhrazená pro rastrový obrázek.

Použití `GetPitch` s [GetBits](#getbits) najít jednotlivých pixelech bitovou kopii.

> [!NOTE]
> Tato metoda podporuje pouze část bitmap DIB.

##  <a name="getpixel"></a>  CImage::GetPixel

Zjišťuje barvu pixelu na umístění, které určuje *x* a *y*.

```
COLORREF GetPixel(int x, int y) const throw();
```

### <a name="parameters"></a>Parametry

*x*<br/>
Souřadnice x pixelu.

*y*<br/>
Souřadnice y pixelu.

### <a name="return-value"></a>Návratová hodnota

Červená, zelená, modré (RGB) hodnota pixelu. Pokud je pixel je mimo aktuální oblast ořezu, vrácená hodnota je CLR_INVALID.

##  <a name="getpixeladdress"></a>  CImage::GetPixelAddress

Načte adresu přesný pixel.

```
void* GetPixelAddress(int x, int y) throw();
```

### <a name="parameters"></a>Parametry

*x*<br/>
Souřadnice x pixelu.

*y*<br/>
Souřadnice y pixelu.

### <a name="remarks"></a>Poznámky

Adresa se určuje podle souřadnic pixel, výška bitmapy a bitů na pixel.

Pro formáty, které mají méně než 8 bitů na pixel vrátí tato metoda adresu bajtů obsahující je pixel. Pokud vaše formát obrázku má 4 bitů na pixel, například `GetPixelAddress` vrátí adresu první pixel v bajtu a musí vypočítat pro počet bajtů 2 pixelů.

> [!NOTE]
> Tato metoda podporuje pouze část bitmap DIB.

##  <a name="gettransparentcolor"></a>  CImage::GetTransparentColor

Načte indexované umístění průhledné barvy palety barev.

```
LONG GetTransparentColor() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Index průhlednou barvu.

##  <a name="getwidth"></a>  CImage::GetWidth

Načte šířka v pixelech, bitové kopie.

```
int GetWidth() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Šířka rastrového obrázku v pixelech.

##  <a name="isdibsection"></a>  CImage::IsDIBSection

Určuje, jestli je připojené rastrový obrázek DIB části.

```
bool IsDIBSection() const throw();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud připojené rastrový obrázek hodnotu DIB oddílu. V opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Pokud rastrového obrázku není oddíl DIB, nemůžete použít následující `CImage` metody, které podporují pouze rastrové obrázky DIB části:

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

##  <a name="isindexed"></a>  CImage::IsIndexed

Určuje, zda pixelů rastrový obrázek se mapují na paletu barev.

```
bool IsIndexed() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE v případě indexované; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí hodnotu TRUE pouze v případě, že je 8 bitů rastrového obrázku (256 barev) nebo méně.

> [!NOTE]
> Tato metoda podporuje pouze část bitmap DIB.

##  <a name="isnull"></a>  CImage::IsNull

Určuje, pokud je aktuálně načtená rastrový obrázek.

```
bool IsNull() const throw();
```

### <a name="remarks"></a>Poznámky

Tato metoda vrátí hodnotu TRUE, pokud aktuálně není načten rastrový obrázek. v opačném případě FALSE.

##  <a name="istransparencysupported"></a>  CImage::IsTransparencySupported

Určuje, jestli aplikace podporuje transparentní rastrových obrázků.

```
static BOOL IsTransparencySupported() throw();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud aktuální platforma podporuje průhlednost. Jinak 0.

### <a name="remarks"></a>Poznámky

Pokud vrácená hodnota je nenulový a transparentnost je podporováno, volání [AlphaBlend](#alphablend), [TransparentBlt](#transparentblt), nebo [nakreslit](#draw) zpracuje průhledné barvy.

##  <a name="load"></a>  CImage::Load

Načte bitovou kopii.

```
HRESULT Load(LPCTSTR pszFileName) throw();
HRESULT Load(IStream* pStream) throw();
```

### <a name="parameters"></a>Parametry

*pszFileName*<br/>
Ukazatel na řetězec obsahující název souboru obrázku se načíst.

*pStream*<br/>
Ukazatel na datový proud obsahující název souboru obrázku se načíst.

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

### <a name="remarks"></a>Poznámky

Načte obrázek určené *pszFileName* nebo *pStream*.

Platná bitová kopie typy jsou BMP, GIF, JPEG, PNG a TIFF.

##  <a name="loadfromresource"></a>  CImage::LoadFromResource

Načte obrázek z prostředku rastrového OBRÁZKU.

```
void LoadFromResource(
    HINSTANCE hInstance,
    LPCTSTR pszResourceName) throw();

void LoadFromResource(
    HINSTANCE hInstance,
    UINT nIDResource) throw();
```

### <a name="parameters"></a>Parametry

*hInstance*<br/>
Popisovač instance modulu, který obsahuje bitovou kopii, který se má načíst.

*pszResourceName*<br/>
Ukazatel na řetězec obsahující název prostředku obsahující bitovou kopii k načtení.

*nIDResource*<br/>
ID prostředku pro načtení.

### <a name="remarks"></a>Poznámky

Prostředek musí být typu rastrového OBRÁZKU.

##  <a name="maskblt"></a>  CImage::MaskBlt

Kombinuje data o barvách pro zdrojové a cílové bitmapy, pomocí zadané masce a rastrovou operaci.

```
BOOL MaskBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    HBITMAP hbmMask,
    int xMask,
    int yMask,
    DWORD dwROP = SRCCOPY) const throw();

BOOL MaskBlt(
    HDC hDestDC,
    const RECT& rectDest,
    const POINT& pointSrc,
    HBITMAP hbmMask,
    const POINT& pointMask,
    DWORD dwROP = SRCCOPY) const throw();

BOOL MaskBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    HBITMAP hbmMask,
    DWORD dwROP = SRCCOPY) const throw();

BOOL MaskBlt(
    HDC hDestDC,
    const POINT& pointDest,
    HBITMAP hbmMask,
    DWORD dwROP = SRCCOPY) const throw();
```

### <a name="parameters"></a>Parametry

*hDestDC*<br/>
Obslužná rutina modulu, jehož spustitelný soubor obsahuje prostředek.

*xDest*<br/>
Souřadnice x, v logických jednotkách, levého horního rohu cílového obdélníku.

*yDest*<br/>
Souřadnice y, v logických jednotkách, levého horního rohu cílového obdélníku.

*nDestWidth*<br/>
Šířka v logické jednotky cílového obdélníku a zdrojové bitmapy.

*nDestHeight*<br/>
Výška v logických jednotkách cílového obdélníku a zdrojové bitmapy.

*xSrc*<br/>
Logickou souřadnici x levého horního rohu zdrojovou bitmapu.

*ySrc*<br/>
Logickou souřadnici y levého horního rohu zdrojovou bitmapu.

*hbmMask*<br/>
Popisovač maska monochromatický rastrový obrázek v kombinaci s barvy rastrového obrázku v kontextu zdrojového zařízení.

*xMask*<br/>
Posun vodorovné pixel rastrového obrázku maska určené *hbmMask* parametru.

*yMask*<br/>
Posun svislé pixel rastrového obrázku maska určené *hbmMask* parametru.

*dwROP*<br/>
Určuje kódy Ternární rastrové operace popředí a pozadí, která metoda se používá k řízení kombinací datový zdroj a cíl. Kód na pozadí rastrové operace je uložen v nejvyšším bajt vyšší řád slova tuto hodnotu; popředí rastrovou operaci kód je uložen v nejnižší bajt vyšší řád slova tuto hodnotu; nižší řád slova z této hodnoty je ignorována a musí být nula. Diskuzi o popředí a pozadí v rámci této metody, naleznete v tématu `MaskBlt` v sadě Windows SDK. Seznam běžných kódy rastrové operace najdete v tématu `BitBlt` v sadě Windows SDK.

*rectDest*<br/>
Odkaz na `RECT` strukturu, identifikace cíle.

*pointSrc*<br/>
A `POINT` struktura označující levém horním rohu zdrojového obdélníku.

*pointMask*<br/>
A `POINT` struktura označující levý horní roh maska rastrového obrázku.

*pointDest*<br/>
Odkaz na `POINT` strukturu, která identifikuje levém horním rohu cílového obdélníku v logických jednotkách.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná, jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda se vztahuje na Windows NT verze 4.0 nebo vyšší.

##  <a name="operator_hbitmap"></a>  CImage::operator HBITMAP

Tento operátor se získat popisovač Windows GDI připojené `CImage` objektu. Tento operátor je operátor přetypování, která podporuje přímému použití objektu HBITMAP.

##  <a name="plgblt"></a>  CImage::PlgBlt

Provede přenos bitového bloku z obdélníku v kontextu zdrojového zařízení do rovnoběžník v kontextu cílového zařízení.

```
BOOL PlgBlt(
    HDC hDestDC,
    const POINT* pPoints,
    HBITMAP hbmMask = NULL) const throw();

BOOL PlgBlt(
    HDC hDestDC,
    const POINT* pPoints,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight,
    HBITMAP hbmMask = NULL,
    int xMask = 0,
    int yMask = 0) const throw();

BOOL PlgBlt(
    HDC hDestDC,
    const POINT* pPoints,
    const RECT& rectSrc,
    HBITMAP hbmMask = NULL,
    const POINT& pointMask = CPoint(0, 0)) const throw();
```

### <a name="parameters"></a>Parametry

*hDestDC*<br/>
Popisovač kontextu cílového zařízení.

*pPoints*<br/>
Ukazatel na tři body v logické místo, které identifikují tři rohů rovnoběžník cílového pole. Levém horním rohu zdrojového obdélníku je namapována na prvním bodem toto pole, pravém horním rohu na druhý bod v tomto poli a levého dolního rohu třetí bod. Pravém dolním rohu zdrojového obdélníku je namapována na implicitní čtvrtý časovému rovnoběžník.

*hbmMask*<br/>
Popisovač volitelné monochromatický rastrový obrázek, který slouží k maskování barvy zdrojového obdélníku.

*xSrc*<br/>
Souřadnice x, v logických jednotkách, levého horního rohu zdrojového obdélníku.

*ySrc*<br/>
Souřadnice y, v logických jednotkách, levého horního rohu zdrojového obdélníku.

*nSrcWidth*<br/>
Šířka v logických jednotkách, zdrojového obdélníku.

*nSrcHeight*<br/>
Výška v logických jednotkách, zdrojového obdélníku.

*xMask*<br/>
Souřadnice x levého horního rohu monochromatický rastrový obrázek.

*yMask*<br/>
Souřadnice y levého horního rohu monochromatický rastrový obrázek.

*rectSrc*<br/>
Odkaz na [RECT](/previous-versions/dd162897\(v=vs.85\)) struktura zadání souřadnic zdrojového obdélníku.

*pointMask*<br/>
A [bodu](/previous-versions/dd162805\(v=vs.85\)) struktura označující levý horní roh maska rastrového obrázku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná, jinak 0.

### <a name="remarks"></a>Poznámky

Pokud *hbmMask* identifikuje platný monochromatický rastrový obrázek, `PlgBit` používá tento rastrový obrázek k maskování bitů barev dat ze zdrojového obdélníku.

Tato metoda se vztahuje na Windows NT verze 4.0 nebo vyšší. Zobrazit [PlgBlt](/windows/desktop/api/wingdi/nf-wingdi-plgblt) v sadě Windows SDK pro podrobnější informace.

##  <a name="releasedc"></a>  CImage::ReleaseDC

Uvolní kontextu zařízení.

```
void ReleaseDC() const throw();
```

### <a name="remarks"></a>Poznámky

Protože pouze jeden rastrového obrázku se dají do kontextu zařízení najednou, je nutné volat `ReleaseDC` pro každé volání [GetDC](#getdc).

##  <a name="releasegdiplus"></a>  CImage::ReleaseGDIPlus

Uvolní prostředky využívané třídou rozhraní GDI +.

```
void ReleaseGDIPlus() throw();
```

### <a name="remarks"></a>Poznámky

Tato metoda musí být volána k uvolnění prostředků přidělaná globální `CImage` objektu. Zobrazit [CImage::CImage](#cimage).

##  <a name="save"></a>  CImage::Save

Obrázek uloží do zadaného datového proudu nebo souboru na disku.

```
HRESULT Save(
    IStream* pStream,
    REFGUID guidFileType) const throw();

HRESULT Save(
    LPCTSTR pszFileName,
    REFGUID guidFileType = GUID_NULL) const throw();
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
Ukazatel na objekt modelu COM IStream obsahující data bitové kopie souboru.

*pszFileName*<br/>
Ukazatel na název souboru obrázku.

*guidFileType*<br/>
Typ souboru, který chcete uložit obrázek jako. Může být jedna z následujících akcí:

- `ImageFormatBMP` Nekomprimovaný rastrový obrázek.

- `ImageFormatPNG` Komprimovanou bitovou kopii grafické PNG (Portable Network).

- `ImageFormatJPEG` Komprimovanou bitovou kopii ve formátu JPEG.

- `ImageFormatGIF` Komprimovanou bitovou kopii ve formátu GIF.

> [!NOTE]
> Úplný seznam konstant, naleznete v tématu **konstanty formát souboru obrázku** v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

### <a name="remarks"></a>Poznámky

Voláním této funkce, které chcete uložit obrázek pomocí zadaného názvu a typu. Pokud *guidFileType* není zahrnutý parametr, název souboru příponu souboru se použije k určení formátu image. Pokud je k dispozici žádné rozšíření, na obrázku se uloží ve formátu BMP.

##  <a name="setcolortable"></a>  CImage::SetColorTable

Nastaví hodnoty barvy červená, zelená, modrá (RGB) pro celou řadu položek na paletě části DIB.

```
void SetColorTable(
    UINT iFirstColor,
    UINT nColors,
    const RGBQUAD* prgbColors) throw();
```

### <a name="parameters"></a>Parametry

*iFirstColor*<br/>
Index tabulky barev první položky nastavení.

*nColors*<br/>
Počet zápisy v tabulce barev k nastavení.

*prgbColors*<br/>
Ukazatel na pole [RGBQUAD](/windows/desktop/api/wingdi/ns-wingdi-tagrgbquad) struktury barvu tabulky položky.

### <a name="remarks"></a>Poznámky

Tato metoda podporuje pouze část bitmap DIB.

##  <a name="setpixel"></a>  CImage::SetPixel

Nastavuje barvu pixel v daném místě rastrového obrázku nastaven.

```
void SetPixel(int x, int y, COLORREF color) throw();
```

### <a name="parameters"></a>Parametry

*x*<br/>
Vodorovné umístění obrazového bodu nastavit.

*y*<br/>
Svislé umístění obrazového bodu nastavit.

*color*<br/>
Barva, do které jste nastavili je pixel.

### <a name="remarks"></a>Poznámky

Tato metoda selže, pokud je pixel koordinuje leží mimo oblast ořezu vybrané.

##  <a name="setpixelindexed"></a>  CImage::SetPixelIndexed

Nastavuje barvu pixelu na barvu na *iIndex* palety barev.

```
void SetPixelIndexed(int x, int y, int iIndex) throw();
```

### <a name="parameters"></a>Parametry

*x*<br/>
Vodorovné umístění obrazového bodu nastavit.

*y*<br/>
Svislé umístění obrazového bodu nastavit.

*iIndex*<br/>
Index barev palety barev.

##  <a name="setpixelrgb"></a>  CImage::SetPixelRGB

Nastaví je pixel v umístění určeném *x* a *y* barvy indikován *r*, *g*, a *b*, v červené, zelené a modré (RGB) image.

```
void SetPixelRGB(
    int x,
    int y,
    BYTE r,
    BYTE g,
    BYTE b) throw();
```

### <a name="parameters"></a>Parametry

*x*<br/>
Vodorovné umístění obrazového bodu nastavit.

*y*<br/>
Svislé umístění obrazového bodu nastavit.

*r*<br/>
Intenzita červenou barvou.

*g*<br/>
Intenzita zelené barvy.

*b*<br/>
Intenzita modré barvy.

### <a name="remarks"></a>Poznámky

Každý červené, zelené a modré parametry jsou reprezentované pomocí číslo mezi 0 a 255. Pokud nastavíte všechny tři parametry na hodnotu nula, kombinované výsledné barvy je černá. Pokud nastavíte všechny tři parametry na 255, je bílé kombinované výsledné barvy.

##  <a name="settransparentcolor"></a>  CImage::SetTransparentColor

Nastaví barvu, která v daném místě indexované jako průhledná.

```
LONG SetTransparentColor(LONG iTransparentColor) throw();
```

### <a name="parameters"></a>Parametry

*iTransparentColor*<br/>
Index v barevné palety barev k nastavení na transparentní. Pokud hodnotu-1, žádné barva je nastavena na transparentní.

### <a name="return-value"></a>Návratová hodnota

Index barva předtím nastavili jako průhledná.

##  <a name="stretchblt"></a>  CImage::StretchBlt

Zkopíruje bitmapu ze kontext zdrojového zařízení pro toto aktuální kontext zařízení.

```
BOOL StretchBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    DWORD dwROP = SRCCOPY) const throw();

BOOL StretchBlt(
    HDC hDestDC,
    const RECT& rectDest,
    DWORD dwROP = SRCCOPY) const throw();

BOOL StretchBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight,
    DWORD dwROP = SRCCOPY) const throw();

BOOL StretchBlt(
    HDC hDestDC,
    const RECT& rectDest,
    const RECT& rectSrc,
    DWORD dwROP = SRCCOPY) const throw();
```

### <a name="parameters"></a>Parametry

*hDestDC*<br/>
Popisovač kontextu cílového zařízení.

*xDest*<br/>
Souřadnice x, v logických jednotkách, levého horního rohu cílového obdélníku.

*yDest*<br/>
Souřadnice y, v logických jednotkách, levého horního rohu cílového obdélníku.

*nDestWidth*<br/>
Šířka v logické jednotky cílového obdélníku.

*nDestHeight*<br/>
Výška v logických jednotkách cílového obdélníku.

*dwROP*<br/>
Rastrová operace provést. Kódy rastrové operace definovat přesně jak kombinovat bity zdroje, cíle a vzor k cíli (podle aktuálně vybraného štětce). Zobrazit [přenos bitových bloků](/windows/desktop/api/wingdi/nf-wingdi-bitblt) v sadě Windows SDK pro seznam další kódy rastrové operace a jejich popisy.

*rectDest*<br/>
Odkaz na [RECT](/previous-versions/dd162897\(v=vs.85\)) strukturu, identifikace cíle.

*xSrc*<br/>
Souřadnice x, v logických jednotkách, levého horního rohu zdrojového obdélníku.

*ySrc*<br/>
Souřadnice y, v logických jednotkách, levého horního rohu zdrojového obdélníku.

*nSrcWidth*<br/>
Šířka v logických jednotkách, zdrojového obdélníku.

*nSrcHeight*<br/>
Výška v logických jednotkách, zdrojového obdélníku.

*rectSrc*<br/>
Odkaz na `RECT` strukturu, identifikace zdroji.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná, jinak 0.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [StretchBlt](/windows/desktop/api/wingdi/nf-wingdi-stretchblt) v sadě Windows SDK.

##  <a name="transparentblt"></a>  CImage::TransparentBlt

Zkopíruje bitmapu ze kontext zdrojového zařízení pro toto aktuální kontext zařízení.

```
BOOL TransparentBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    UINT crTransparent = CLR_INVALID) const throw();

BOOL TransparentBlt(
    HDC hDestDC,
    const RECT& rectDest,
    UINT crTransparent = CLR_INVALID) const throw();

BOOL TransparentBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight,
    UINT crTransparent = CLR_INVALID) const throw();

BOOL TransparentBlt(
    HDC hDestDC,
    const RECT& rectDest,
    const RECT& rectSrc,
    UINT crTransparent = CLR_INVALID) const throw();
```

### <a name="parameters"></a>Parametry

*hDestDC*<br/>
Popisovač kontextu cílového zařízení.

*xDest*<br/>
Souřadnice x, v logických jednotkách, levého horního rohu cílového obdélníku.

*yDest*<br/>
Souřadnice y, v logických jednotkách, levého horního rohu cílového obdélníku.

*nDestWidth*<br/>
Šířka v logické jednotky cílového obdélníku.

*nDestHeight*<br/>
Výška v logických jednotkách cílového obdélníku.

*crTransparent*<br/>
Barva v zdrojovou bitmapu do považována za průhlednou. Ve výchozím nastavení CLR_INVALID, by měl být použit označující, že barva aktuálně nastavený jako průhledná barva obrázku.

*rectDest*<br/>
Odkaz na [RECT](/previous-versions/dd162897\(v=vs.85\)) strukturu, identifikace cíle.

*xSrc*<br/>
Souřadnice x, v logických jednotkách, levého horního rohu zdrojového obdélníku.

*ySrc*<br/>
Souřadnice y, v logických jednotkách, levého horního rohu zdrojového obdélníku.

*nSrcWidth*<br/>
Šířka v logických jednotkách, zdrojového obdélníku.

*nSrcHeight*<br/>
Výška v logických jednotkách, zdrojového obdélníku.

*rectSrc*<br/>
Odkaz na `RECT` strukturu, identifikace zdroji.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je úspěšná, jinak hodnota FALSE.

### <a name="remarks"></a>Poznámky

`TransparentBlt` platí pro zdrojové bitmapy 4 bitů na pixel a 8 bitů na pixel. Použití [CImage::AlphaBlend](#alphablend) určit rastrové obrázky 32 bitů na pixel se transparentnost.

### <a name="example"></a>Příklad

```cpp
// Performs a transparent blit from the source image to the destination
// image using the images' current transparency settings
BOOL TransparentBlt(CImage* pSrcImage, CImage* pDstImage,
       int xDest, int yDest, int nDestWidth, int nDestHeight)
{
    HDC hDstDC = NULL;
    BOOL bResult;

    if(pSrcImage == NULL || pDstImage == NULL)
    {
        // Invalid parameter
        return FALSE;
    }

    // Obtain a DC to the destination image
    hDstDC = pDstImage->GetDC();
    // Perform the blit
    bResult = pSrcImage->TransparentBlt(hDstDC, xDest, yDest, nDestWidth, nDestHeight);

    // Release the destination DC
    pDstImage->ReleaseDC();

    return bResult;
}
```

## <a name="see-also"></a>Viz také:

[MMXSwarm Sample](../../overview/visual-cpp-samples.md)<br/>
[Ukázka SimpleImage](../../overview/visual-cpp-samples.md)<br/>
[Bitmap nezávislých na zařízení](/windows/desktop/gdi/device-independent-bitmaps)<br/>
[CreateDIBSection](/windows/desktop/api/wingdi/nf-wingdi-createdibsection)<br/>
[Desktopové komponenty ATL objektů COM](../../atl/atl-com-desktop-components.md)<br/>
[Bitmap nezávislých na zařízení](/windows/desktop/gdi/device-independent-bitmaps)<br/>
[CreateDIBSection](/windows/desktop/api/wingdi/nf-wingdi-createdibsection)
