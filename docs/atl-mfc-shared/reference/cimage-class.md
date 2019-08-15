---
title: Služby CImage ve – třída
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
ms.openlocfilehash: 6c651f160fdab582b769cf1764add2cc482745bf
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491331"
---
# <a name="cimage-class"></a>Služby CImage ve – třída

`CImage`poskytuje rozšířenou podporu rastrového obrázku, včetně možnosti načítání a ukládání obrázků ve formátech JPEG, GIF, BMP a PNG (Portable Network Graphics).

> [!IMPORTANT]
> Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CImage
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[Služby CImage ve:: služby CImage ve](#cimage)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[Služby CImage ve:: AlphaBlend](#alphablend)|Zobrazí rastrové obrázky, které mají transparentní nebo poloprůhledný pixel.|
|[Služby CImage ve:: Attach](#attach)|Připojí HBITMAP k `CImage` objektu. Dá se použít s rastrovým obrázkem oddílu bez formátu DIB nebo bitmapami oddílu DIB.|
|[Služby CImage ve:: BitBlt](#bitblt)|Zkopíruje rastrový obrázek z kontextu zdrojového zařízení do tohoto aktuálního kontextu zařízení.|
|[Služby CImage ve:: Create](#create)|Vytvoří rastrový obrázek oddílu DIB a připojí ho k dříve vytvořenému `CImage` objektu.|
|[CImage::CreateEx](#createex)|Vytvoří rastrový obrázek oddílu DIB (s dalšími parametry) a připojí ho k dříve vytvořenému `CImage` objektu.|
|[Služby CImage ve::D estroy](#destroy)|Odpojí rastrový obrázek od `CImage` objektu a odstraní rastrový obrázek.|
|[CImage::Detach](#detach)|Odpojí rastrový obrázek od `CImage` objektu.|
|[Služby CImage ve: nezpracované:D](#draw)|Zkopíruje rastrový obrázek ze zdrojového obdélníku do cílového obdélníku. `Draw`roztáhne nebo komprimuje rastr, aby odpovídal rozměrům cílového obdélníku, je-li to nutné, a zpracovává alfa barvy a transparentní barvy.|
|[Služby CImage ve:: getbitů](#getbits)|Načte ukazatel na skutečné hodnoty pixelů rastrového obrázku.|
|[Služby CImage ve:: GetBPP](#getbpp)|Načte bity na pixel.|
|[Služby CImage ve:: GetColor – k](#getcolortable)|Načte červené, zelené, modré (RGB) hodnoty barev z rozsahu záznamů v tabulce barev.|
|[CImage::GetDC](#getdc)|Načte kontext zařízení, ve kterém je vybraný aktuální rastrový obrázek.|
|[CImage::GetExporterFilterString](#getexporterfilterstring)|Najde dostupné formáty obrázků a jejich popisy.|
|[Služby CImage ve:: GetHeight](#getheight)|Načte výšku aktuálního obrázku v pixelech.|
|[CImage::GetImporterFilterString](#getimporterfilterstring)|Najde dostupné formáty obrázků a jejich popisy.|
|[CImage::GetMaxColorTableEntries](#getmaxcolortableentries)|Načte maximální počet položek v tabulce barev.|
|[Služby CImage ve:: getrozteč](#getpitch)|Načte rozteč aktuálního obrázku v bajtech.|
|[CImage::GetPixel](#getpixel)|Načte barvu pixelu určenou *x* a *y*.|
|[Služby CImage ve:: GetPixelAddress](#getpixeladdress)|Načte adresu daného pixelu.|
|[Služby CImage ve:: GetTransparentColor](#gettransparentcolor)|Načte pozici průhledné barvy v tabulce barev.|
|[Služby CImage ve:: getwidth](#getwidth)|Načte šířku aktuálního obrázku v pixelech.|
|[CImage::IsDIBSection](#isdibsection)|Určuje, zda je připojen rastrový obrázek oddíl DIB.|
|[Služby CImage ve::-Indexed](#isindexed)|Označuje, že barvy rastrového obrázku jsou namapovány na indexovanou paletu.|
|[CImage::IsNull](#isnull)|Určuje, zda je zdrojová bitmapa momentálně načtena.|
|[Služby CImage ve:: IsTransparencySupported](#istransparencysupported)|Určuje, zda aplikace podporuje transparentní rastrové obrázky.|
|[Služby CImage ve:: Load](#load)|Načte obrázek ze zadaného souboru.|
|[Služby CImage ve:: LoadFromResource](#loadfromresource)|Načte obrázek ze zadaného prostředku.|
|[Služby CImage ve:: MaskBlt](#maskblt)|Kombinuje barevná data pro zdrojové a cílové bitmapy pomocí zadané masky a operace rastrového obrázku.|
|[Služby CImage ve::P lgBlt](#plgblt)|Provede přenos bitového bloku z obdélníku v kontextu zdrojového zařízení do kosoúhelníke v kontextu cílového zařízení.|
|[Služby CImage ve:: ReleaseDC](#releasedc)|Uvolní kontext zařízení, který byl načten pomocí [služby CImage ve:: GetDC](#getdc).|
|[Služby CImage ve:: ReleaseGDIPlus](#releasegdiplus)|Uvolňuje prostředky používané rozhraním GDI+. Musí být volána pro uvolnění prostředků vytvořených globálním `CImage` objektem.|
|[Služby CImage ve:: Save](#save)|Uloží obrázek jako zadaný typ. `Save`nelze zadat možnosti obrázku.|
|[Služby CImage ve:: SetColorTable](#setcolortable)|Nastaví červené, zelené a modré RGB hodnoty barev v rozsahu záznamů v tabulce Color oddílu DIB.|
|[Služby CImage ve:: funkce SetPixel](#setpixel)|Nastaví pixel na zadaných souřadnicích na určenou barvu.|
|[CImage::SetPixelIndexed](#setpixelindexed)|Nastaví pixel na zadaných souřadnicích na barvu v zadaném indexu palety.|
|[CImage::SetPixelRGB](#setpixelrgb)|Nastaví pixel na zadaných souřadnicích na zadanou červenou, zelenou, modrou (RGB) hodnotu.|
|[Služby CImage ve:: SetTransparentColor](#settransparentcolor)|Nastaví index barvy, které mají být považovány za transparentní. Průhledná může být pouze jedna barva v paletě.|
|[Služby CImage ve:: StretchBlt](#stretchblt)|Zkopíruje rastrový obrázek ze zdrojového obdélníku do cílového obdélníku a v případě potřeby roztáhne nebo zkomprimuje rastr, aby odpovídal rozměrům cílového obdélníku.|
|[Služby CImage ve:: TransparentBlt](#transparentblt)|Zkopíruje rastrový obrázek s průhlednou barvou z kontextu zdrojového zařízení do tohoto aktuálního kontextu zařízení.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[Služby CImage ve:: operator HBITMAP](#operator_hbitmap)|Vrátí popisovač systému Windows připojený k `CImage` objektu.|

## <a name="remarks"></a>Poznámky

`CImage`používá bitmapy, které jsou buď oddíly rastrového obrázku nezávislé na zařízení (DIB), nebo ne. Můžete však použít příkaz [Create](#create) nebo [služby CImage ve:: Load](#load) s pouze oddíly DIB. Rastrový obrázek oddílu, který není ve formátu DIB, `CImage` můžete k objektu připojit pomocí [připojit](#attach), ale nemůžete `CImage` použít následující metody, které podporují pouze rastrové obrázky oddílu DIB:

- [Getbity](#getbits)

- [GetColor](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [Getrozteč](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

Chcete-li zjistit, zda je připojen rastrový obrázek oddíl DIB, zavolejte [IsDibSection](#isdibsection).

> [!NOTE]
> V aplikaci Visual Studio .NET 2003 tato třída udržuje počet `CImage` vytvořených objektů. Pokaždé, když je počet převede na `GdiplusShutdown` 0, funkce je automaticky volána k uvolnění prostředků používaných rozhraním GDI+. Tím zajistíte, `CImage` že všechny objekty vytvořené přímo nebo nepřímo pomocí knihoven DLL jsou vždy zničeny správně a které `DllMain` `GdiplusShutdown` nejsou volány z.

> [!NOTE]
> Použití globálních `CImage` objektů v knihovně DLL se nedoporučuje. Pokud potřebujete použít globální `CImage` objekt v knihovně DLL, zavolejte [služby CImage ve:: ReleaseGDIPlus](#releasegdiplus) , aby byly explicitně vydány prostředky využívané rozhraním GDI+.

`CImage`nelze vybrat do nového funkce [CDC](../../mfc/reference/cdc-class.md). `CImage`Vytvoří vlastní HDC pro obrázek. Vzhledem k tomu, že HBITMAP lze vybrat pouze do jednoho HDC v jednom okamžiku, HBITMAP přidružená `CImage` k objektu nemůže být vybrána do jiného HDC. Pokud potřebujete CDC, načtěte HDC z rozhraní `CImage` a přidělte ho k [CDC:: FromHandle](../../mfc/reference/cdc-class.md#fromhandle).

## <a name="example"></a>Příklad

```cpp
// Get a CDC for the image
CDC* pDC = CDC::FromHandle(m_myImage.GetDC());

// Use pDC here
pDC->Rectangle(0, 40, 100, 50);
m_myImage.ReleaseDC();
```

Při použití `CImage` v projektu knihovny MFC si všimněte, které členské funkce v projektu očekávají ukazatel na objekt [CBitmap –](../../mfc/reference/cbitmap-class.md) . Pokud `CImage` chcete použít s takovou funkcí, jako je například [CMenu –:: AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu), použijte [CBitmap –::](../../mfc/reference/cbitmap-class.md#fromhandle) `CImage` FromHandle, předejte ji HBITMAP a použijte vrácenou `CBitmap*`hodnotu.

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

Prostřednictvím `CImage`nástroje máte přístup k skutečným bitům oddílu DIB. `CImage` Objekt můžete použít všude, kde jste dříve použili oddíl Win32 HBITMAP nebo DIB.

Můžete použít `CImage` buď z knihovny MFC nebo knihovny ATL.

> [!NOTE]
> Při vytváření projektu pomocí `CImage`, je nutné definovat `CString` před zahrnutím `atlimage.h`. Pokud váš projekt používá ATL bez knihovny MFC, `atlstr.h` zahrňte před `atlimage.h`zahrnutím. Pokud váš projekt používá knihovnu MFC (nebo pokud se jedná o projekt ATL s podporou MFC), `afxstr.h` zahrňte před `atlimage.h`zahrnutím.<br/>
> <br/>
> Podobně je nutné zahrnout `atlimage.h` před zahrnutím. `atlimpl.cpp` Pokud to chcete provést snadno, `atlimage.h` zahrňte `stdafx.h`do svého.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlimage. h

##  <a name="alphablend"></a>Služby CImage ve:: AlphaBlend

Zobrazí rastrové obrázky, které mají transparentní nebo poloprůhledný pixel.

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
Zpracování kontextu cílového zařízení.

*xDest*<br/>
Souřadnice x (v logických jednotkách) levého horního rohu cílového obdélníku.

*yDest*<br/>
Souřadnice y v levém horním rohu cílového obdélníku v logických jednotkách.

*bSrcAlpha*<br/>
Hodnota průhlednosti alfa, která se má použít na celé zdrojové bitmapě. Výchozí hodnota 0xFF (255) předpokládá, že je váš obrázek neprůhledný a že chcete použít pouze hodnoty pro alfa pixel.

*bBlendOp*<br/>
Funkce rozkládání alfa pro zdrojové a cílové rastrové obrázky, globální hodnotu alfa, která se má použít pro celou zdrojovou bitmapu, a informace o formátu zdrojové bitmapy. Funkce Blendu zdroje a cíle jsou aktuálně omezené na AC_SRC_OVER.

*pointDest*<br/>
Odkaz na strukturu [bodu](/previous-versions/dd162805\(v=vs.85\)) , která identifikuje levý horní roh cílového obdélníku v logických jednotkách.

*nDestWidth*<br/>
Šířka cílového obdélníku v logických jednotkách.

*nDestHeight*<br/>
Výška cílového obdélníku v logických jednotkách.

*xSrc*<br/>
Logická souřadnice x levého horního rohu zdrojového obdélníku.

*ySrc*<br/>
Logická souřadnice y levého horního rohu zdrojového obdélníku.

*nSrcWidth*<br/>
Šířka zdrojového obdélníku v logických jednotkách.

*nSrcHeight*<br/>
Výška zdrojového obdélníku v logických jednotkách

*rectDest*<br/>
Odkaz na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) , která identifikuje cíl.

*rectSrc*<br/>
Odkaz na `RECT` strukturu, která identifikuje zdroj.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Rastrové obrázky s alfa směsí podporují prolnutí barev po jednotlivých pixelech.

Když je *bBlendOp* nastavené na výchozí hodnotu AC_SRC_OVER, zdrojová bitmapa se umístí přes cílovou bitmapu na základě hodnot alfa zdrojových pixelů.

##  <a name="attach"></a>Služby CImage ve:: Attach

Připojí *HBITMAP* k `CImage` objektu.

```
void Attach(HBITMAP hBitmap, DIBOrientation eOrientation = DIBOR_DEFAULT) throw();
```

### <a name="parameters"></a>Parametry

*hBitmap*<br/>
Popisovač pro HBITMAP.

*eOrientation*<br/>
Určuje orientaci rastrového obrázku. Může být jedna z následujících akcí:

- DIBOR_DEFAULT orientace rastrového obrázku je určena operačním systémem.

- DIBOR_BOTTOMUP čáry rastrového obrázku jsou v opačném pořadí. To způsobí, že [služby CImage ve:: getbitů](#getbits) vrátí ukazatel na konci vyrovnávací paměti rastrového obrázku a [služby CImage ve:: getrozteč](#getpitch) pro vrácení záporného čísla.

- DIBOR_TOPDOWN čáry rastrového obrázku jsou v horní části do dolního pořadí. To způsobí, že [služby CImage ve:: getbitů](#getbits) vrátí ukazatel na první bajt vyrovnávací paměti rastrového obrázku a [služby CImage ve:: getrozteč](#getpitch) pro vrácení kladného čísla.

### <a name="remarks"></a>Poznámky

Rastr může být buď rastrový obrázek oddílu, který není ve formátu DIB, nebo rastrový obrázek oddílu DIB. Seznam metod, které lze použít pouze s rastrovými obrázky oddílu DIB, naleznete v tématu [IsDIBSection](#isdibsection) .

##  <a name="bitblt"></a>Služby CImage ve:: BitBlt

Zkopíruje rastrový obrázek z kontextu zdrojového zařízení do tohoto aktuálního kontextu zařízení.

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
Cílová HDC.

*xDest*<br/>
Logická souřadnice x levého horního rohu cílového obdélníku.

*yDest*<br/>
Logická souřadnice y levého horního rohu cílového obdélníku.

*dwROP*<br/>
Operace rastru, která má být provedena. Kódy pro rastrové operace definují přesně způsob, jak kombinovat bity zdroje, cíle a vzor (jak definuje aktuálně vybraný štětec) k vytvoření cíle. Seznam dalších kódů s rastrovými operace a jejich popis naleznete v tématu [BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) v Windows SDK.

*pointDest*<br/>
Struktura [bodu](/previous-versions/dd162805\(v=vs.85\)) označující levý horní roh cílového obdélníku.

*nDestWidth*<br/>
Šířka cílového obdélníku v logických jednotkách.

*nDestHeight*<br/>
Výška cílového obdélníku v logických jednotkách.

*xSrc*<br/>
Logická souřadnice x levého horního rohu zdrojového obdélníku.

*ySrc*<br/>
Logická souřadnice y levého horního rohu zdrojového obdélníku.

*rectDest*<br/>
Struktura [Rect](/previous-versions/dd162897\(v=vs.85\)) indikující cílový obdélník.

*pointSrc*<br/>
`POINT` Struktura označující levý horní roh zdrojového obdélníku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; jinak nula.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) v Windows SDK.

##  <a name="cimage"></a>Služby CImage ve:: služby CImage ve

`CImage` Vytvoří objekt.

```
CImage() throw();
```

### <a name="remarks"></a>Poznámky

Jakmile vytvoříte objekt, voláním metody [Create](#create), [Load](#load), [LoadFromResource](#loadfromresource)nebo [Attach](#attach) připojte k objektu rastrový obrázek.

**Poznámka:** V aplikaci Visual Studio Tato třída udržuje počet `CImage` vytvořených objektů. Pokaždé, když je počet převede na `GdiplusShutdown` 0, funkce je automaticky volána k uvolnění prostředků používaných rozhraním GDI+. Tím zajistíte, `CImage` že všechny objekty vytvořené přímo nebo nepřímo pomocí knihoven DLL jsou vždy zničeny správně a které `GdiplusShutdown` nejsou volány z DllMain.

Použití globálních `CImage` objektů v knihovně DLL se nedoporučuje. Pokud potřebujete použít globální `CImage` objekt v knihovně DLL, zavolejte [služby CImage ve:: ReleaseGDIPlus](#releasegdiplus) , aby byly explicitně vydány prostředky využívané rozhraním GDI+.

##  <a name="create"></a>Služby CImage ve:: Create

Vytvoří rastrový obrázek a připojí ho k dříve vytvořenému `CImage` objektu. `CImage`

```
BOOL Create(
    int nWidth,
    int nHeight,
    int nBPP,
    DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parametry

*nWidth*<br/>
Šířka `CImage` rastrového obrázku (v pixelech).

*nHeight*<br/>
Výška `CImage` rastrového obrázku (v pixelech) Pokud je *nHeight* pozitivní, rastrový obrázek je v dolní části DIB a jeho počátek je spodní levý roh. Pokud je *nHeight* záporné, rastrový obrázek je v levém horním rohu DIB a jeho zdrojem je levý horní roh.

*nBPP*<br/>
Počet bitů na pixel v rastrovém obrázku. Obvykle 4, 8, 16, 24 nebo 32. Může být 1 pro monochromatické rastrové obrázky nebo masky.

*dwFlags*<br/>
Určuje, zda má objekt rastrového obrázku alfa kanál. Může být kombinací nuly nebo více z následujících hodnot:

- *createAlphaChannel* Lze ji použít pouze v případě, že je *nBPP* 32 a *eCompression* je BI_RGB. Je-li tento parametr zadán, má vytvořená bitová kopie hodnotu alfa (transparentnost) pro každý pixel uloženou v 4 bajtech každého pixelu (nepoužívá se v nealfa 32 bitové imagi). Tento alfa kanál se automaticky použije při volání metody [služby CImage ve:: AlphaBlend](#alphablend).

> [!NOTE]
> V volání [služby CImage ve::D RAW](#draw)se obrázky s alfa kanálem automaticky rozmísí do cíle.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

##  <a name="createex"></a>Služby CImage ve:: CreateEx

Vytvoří rastrový obrázek a připojí ho k dříve vytvořenému `CImage` objektu. `CImage`

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
Šířka `CImage` rastrového obrázku (v pixelech).

*nHeight*<br/>
Výška `CImage` rastrového obrázku (v pixelech) Pokud je *nHeight* pozitivní, rastrový obrázek je v dolní části DIB a jeho počátek je spodní levý roh. Pokud je *nHeight* záporné, rastrový obrázek je v levém horním rohu DIB a jeho zdrojem je levý horní roh.

*nBPP*<br/>
Počet bitů na pixel v rastrovém obrázku. Obvykle 4, 8, 16, 24 nebo 32. Může být 1 pro monochromatické rastrové obrázky nebo masky.

*eCompression*<br/>
Určuje typ komprese komprimovaného dolního rastrového obrázku (DIB shora dolů nelze komprimovat). Může to být jedna z následujících hodnot:

- BI_RGB formát není komprimován. Zadání této hodnoty při volání `CImage::CreateEx` je ekvivalentní volání. `CImage::Create`

- BI_BITFIELDS formát není komprimovaný a tabulka barev se skládá ze tří barevných masek typu DWORD, které určují červené, zelené a modré komponenty v jednotlivých pixelech. To platí v případě, že se používá s 16 a 32 bpp rastrami.

*pdwBitfields*<br/>
Používá se jenom v případě, že je *eCompression* nastavené na BI_BITFIELDS, v opačném případě musí mít hodnotu null. Ukazatel na pole tří hodnot typu DWORD vyčíslení určující, které bity každého pixelu jsou použity pro červené, zelené a modré komponenty barvy, v uvedeném pořadí. Informace o omezeních pro bitová pole najdete v tématu [BITMAPINFOHEADER](/previous-versions//dd183376\(v=vs.85\)) v Windows SDK.

*dwFlags*<br/>
Určuje, zda má objekt rastrového obrázku alfa kanál. Může být kombinací nuly nebo více z následujících hodnot:

- *createAlphaChannel* Lze ji použít pouze v případě, že je *nBPP* 32 a *eCompression* je BI_RGB. Je-li tento parametr zadán, má vytvořená bitová kopie hodnotu alfa (transparentnost) pro každý pixel uloženou v 4 bajtech každého pixelu (nepoužívá se v nealfa 32 bitové imagi). Tento alfa kanál se automaticky použije při volání metody [služby CImage ve:: AlphaBlend](#alphablend).

   > [!NOTE]
   > V volání [služby CImage ve::D RAW](#draw)se obrázky s alfa kanálem automaticky rozmísí do cíle.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud bylo úspěšné. V opačném případě FALSE.

### <a name="example"></a>Příklad

Následující příklad vytvoří rastrový obrázek 100x100 pixelů s použitím 16 bitů ke kódování jednotlivých pixelů. V daném 16bitovém pixelu BITS 0-3 zakóduje červenou komponentu, BITS 4-7 encode zeleně a bity 8-11 modrou. Zbylých 4 bitů se nepoužívá.

```cpp
DWORD adwBitmasks[3] = { 0x0000000f, 0x000000f0, 0x00000f00 };
m_myImage.CreateEx(100, 100, 16, BI_BITFIELDS, adwBitmasks, 0);
```

##  <a name="destroy"></a>Služby CImage ve::D estroy

Odpojí rastrový obrázek od `CImage` objektu a odstraní rastrový obrázek.

```
void Destroy() throw();
```

##  <a name="detach"></a>Služby CImage ve::D etach

Odpojí rastrový obrázek od `CImage` objektu.

```
HBITMAP Detach() throw();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač rastrového obrázku byl odpojen, nebo má hodnotu NULL, pokud není připojena žádná bitmapa.

##  <a name="draw"></a>Služby CImage ve: nezpracované:D

Zkopíruje rastrový obrázek z kontextu zdrojového zařízení do kontextu aktuálního zařízení.

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
Souřadnice x (v logických jednotkách) levého horního rohu cílového obdélníku.

*yDest*<br/>
Souřadnice y v levém horním rohu cílového obdélníku v logických jednotkách.

*nDestWidth*<br/>
Šířka cílového obdélníku v logických jednotkách.

*nDestHeight*<br/>
Výška cílového obdélníku v logických jednotkách.

*xSrc*<br/>
Souřadnice x (v logických jednotkách) levého horního rohu zdrojového obdélníku.

*ySrc*<br/>
Souřadnice y v levém horním rohu zdrojového obdélníku v logických jednotkách.

*nSrcWidth*<br/>
Šířka zdrojového obdélníku v logických jednotkách.

*nSrcHeight*<br/>
Výška zdrojového obdélníku v logických jednotkách

*rectDest*<br/>
Odkaz na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) , která identifikuje cíl.

*rectSrc*<br/>
Odkaz na `RECT` strukturu, která identifikuje zdroj.

*pointDest*<br/>
Odkaz na strukturu [bodu](/previous-versions/dd162805\(v=vs.85\)) , která identifikuje levý horní roh cílového obdélníku v logických jednotkách.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

`Draw`provede stejnou operaci jako [StretchBlt](#stretchblt), pokud Image neobsahuje průhlednou barvu nebo alfa kanál. V takovém případě `Draw` provede stejnou operaci jako [TransparentBlt](#transparentblt) nebo [AlphaBlend](#alphablend) , jak je to nutné.

U verzí `Draw` , které nespecifikují zdrojový obdélník, je celý zdrojový obraz výchozí. Pro verzi `Draw` , která neurčuje velikost pro cílový obdélník, je velikost zdrojového obrázku výchozí a nedochází k žádnému roztažení ani zmenšení.

##  <a name="getbits"></a>Služby CImage ve:: getbitů

Načte ukazatel na skutečné bitové hodnoty daného pixelu v rastrovém obrázku.

```
void* GetBits() throw();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na vyrovnávací paměť rastrového obrázku. Pokud je rastrový obrázek ve formátu DIB, ukazatel ukazuje na konci vyrovnávací paměti. Pokud je rastrový obrázek v horní části DIB, ukazatel ukazuje na první bajt vyrovnávací paměti.

### <a name="remarks"></a>Poznámky

Pomocí tohoto ukazatele spolu s hodnotou vrácenou funkcí [getrozteč](#getpitch)můžete vyhledat a změnit jednotlivé pixely v obrázku.

> [!NOTE]
> Tato metoda podporuje pouze rastrové obrázky oddílů DIB; v důsledku toho získáte přístup k pixelům `CImage` objektu stejným způsobem jako pixely oddílu DIB. Vrácený ukazatel ukazuje na pixel v umístění (0, 0).

##  <a name="getbpp"></a>Služby CImage ve:: GetBPP

Načte hodnotu bitů na pixel.

```
int GetBPP() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Počet bitů na pixel.

### <a name="remarks"></a>Poznámky

Tato hodnota určuje počet bitů, které definují jednotlivé pixely, a maximální počet barev v rastrovém obrázku.

Bity na pixel jsou obvykle 1, 4, 8, 16, 24 nebo 32. Další informace o této [](/previous-versions//dd183376\(v=vs.85\)) hodnotě najdete v tématu věnovaném členuBITMAPINFOHEADERv`biBitCount` Windows SDK.

##  <a name="getcolortable"></a>Služby CImage ve:: GetColor – k

Načte červené, zelené, modré (RGB) hodnoty barev z rozsahu položek v paletě oddílu DIB.

```
void GetColorTable(
    UINT iFirstColor,
    UINT nColors,
    RGBQUAD* prgbColors) const throw();
```

### <a name="parameters"></a>Parametry

*iFirstColor*<br/>
Index tabulky barev prvního záznamu, který se má načíst

*nColors*<br/>
Počet položek tabulky barev, které mají být načteny.

*prgbColors*<br/>
Ukazatel na pole struktur [RGBQUAD](/windows/win32/api/wingdi/ns-wingdi-rgbquad) , aby se načetly položky tabulky barev.

##  <a name="getdc"></a>Služby CImage ve:: GetDC

Načte kontext zařízení, ve kterém je aktuálně vybraná image.

```
HDC GetDC() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač kontextu zařízení.

### <a name="remarks"></a>Poznámky

Pro každé volání do `GetDC`musíte mít následné volání [ReleaseDC](#releasedc).

##  <a name="getexporterfilterstring"></a>Služby CImage ve:: GetExporterFilterString

Najde formáty obrázků, které jsou k dispozici pro ukládání obrázků.

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
Odkaz na `CSimpleString` objekt. Další informace najdete v části **poznámky** .

*aguidFileTypes*<br/>
Pole identifikátorů GUID s každým prvkem odpovídajícím jednomu z typů souborů v řetězci. V příkladu v *pszAllFilesDescription* níže je *aguidFileTypes*[0] GUID_NULL a zbývající hodnoty pole jsou formáty souborů obrázků podporované aktuálním operačním systémem.

> [!NOTE]
> Úplný seznam konstant najdete v tématu konstanty **formátu souboru obrázku** v Windows SDK.

*pszAllFilesDescription*<br/>
Pokud tento parametr není NULL, bude mít řetězec filtru na začátku seznamu jeden další filtr. Tento filtr bude mít aktuální hodnotu *pszAllFilesDescription* pro svůj popis a přijímá soubory všech přípon podporovaných jakýmkoli jiným vývozcem v seznamu.

Příklad:

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any exporter.
CImage::GetExporterFilterString(
    strExporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
Sada bitových příznaků určujících typy souborů, které mají být vyloučeny ze seznamu. Povolené příznaky:

- `excludeGIF`= 0x01 vylučuje soubory GIF.

- `excludeBMP`= 0x02 vyloučí soubory BMP (Windows BMP).

- `excludeEMF`= 0x04 vyloučí soubory EMF (Enhanced Metafile).

- `excludeWMF`= 0x08 vyloučí soubory WMF (Windows Metafile).

- `excludeJPEG`= 0x10 vyloučí soubory JPEG.

- `excludePNG`= 0x20 vyloučí soubory PNG.

- `excludeTIFF`= 0x40 vyloučí soubory TIFF.

- `excludeIcon`= 0x80 vyloučí soubory ICO (Windows Icon).

- `excludeOther`= 0x80000000 vyloučí všechny ostatní typy souborů, které nejsou uvedené výše.

- `excludeDefaultLoad`= 0 pro načtení jsou ve výchozím nastavení zahrnuty všechny typy souborů.

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF`Pro uložení jsou tyto soubory ve výchozím nastavení vyloučené, protože obvykle mají zvláštní požadavky.

*chSeparator*<br/>
Oddělovač použitý mezi formáty obrázků. Další informace najdete v části **poznámky** .

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Výsledný řetězec formátu můžete předat objektu [CFileDialog](../../mfc/reference/cfiledialog-class.md) knihovny MFC a zpřístupnit tak přípony souborů dostupných formátů obrázků v dialogovém okně soubor uložit jako.

Parametr *strExporter* má formát:

soubor description0&#124;\*. EXT0&#124;&#124;filedescription1\*. EXT1&#124;... Popis souboru *n*&#124;\*. ext *n*&#124;&#124;

kde '&#124;' je znak oddělovače určený parametrem `chSeparator`. Příklad:

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

Použijte výchozí oddělovač '&#124;', Pokud předáte tento řetězec do objektu knihovny `CFileDialog` MFC. Použijte oddělovač null \ 0, pokud tento řetězec předáte do dialogového okna společné uložení souboru.

##  <a name="getheight"></a>Služby CImage ve:: GetHeight

Načte výšku obrázku v pixelech.

```
int GetHeight() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Výška obrázku v pixelech.

##  <a name="getimporterfilterstring"></a>Služby CImage ve:: GetImporterFilterString

Najde formáty obrázků, které jsou k dispozici pro načítání obrázků.

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
Odkaz na `CSimpleString` objekt. Další informace najdete v části **poznámky** .

*aguidFileTypes*<br/>
Pole identifikátorů GUID s každým prvkem odpovídajícím jednomu z typů souborů v řetězci. V příkladu v *pszAllFilesDescription* níže je *aguidFileTypes*[0] GUID_NULL s hodnotami zbývajících polí jsou formáty souborů obrázků podporované aktuálním operačním systémem.

> [!NOTE]
> Úplný seznam konstant najdete v tématu konstanty **formátu souboru obrázku** v Windows SDK.

*pszAllFilesDescription*<br/>
Pokud tento parametr není NULL, bude mít řetězec filtru na začátku seznamu jeden další filtr. Tento filtr bude mít aktuální hodnotu *pszAllFilesDescription* pro svůj popis a přijímá soubory všech přípon podporovaných jakýmkoli jiným vývozcem v seznamu.

Příklad:

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any importer.
CImage::GetImporterFilterString(
    strImporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
Sada bitových příznaků určujících typy souborů, které mají být vyloučeny ze seznamu. Povolené příznaky:

- `excludeGIF`= 0x01 vylučuje soubory GIF.

- `excludeBMP`= 0x02 vyloučí soubory BMP (Windows BMP).

- `excludeEMF`= 0x04 vyloučí soubory EMF (Enhanced Metafile).

- `excludeWMF`= 0x08 vyloučí soubory WMF (Windows Metafile).

- `excludeJPEG`= 0x10 vyloučí soubory JPEG.

- `excludePNG`= 0x20 vyloučí soubory PNG.

- `excludeTIFF`= 0x40 vyloučí soubory TIFF.

- `excludeIcon`= 0x80 vyloučí soubory ICO (Windows Icon).

- `excludeOther`= 0x80000000 vyloučí všechny ostatní typy souborů, které nejsou uvedené výše.

- `excludeDefaultLoad`= 0 pro načtení jsou ve výchozím nastavení zahrnuty všechny typy souborů.

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF`Pro uložení jsou tyto soubory ve výchozím nastavení vyloučené, protože obvykle mají zvláštní požadavky.

*chSeparator*<br/>
Oddělovač použitý mezi formáty obrázků. Další informace najdete v části **poznámky** .

### <a name="remarks"></a>Poznámky

Výsledný řetězec formátu můžete předat objektu [CFileDialog](../../mfc/reference/cfiledialog-class.md) knihovny MFC a zpřístupnit tak přípony souborů dostupných formátů obrázků v dialogovém okně **otevřít soubor** .

Parametr *strImporter* má formát:

soubor description0&#124;\*. EXT0&#124;&#124;filedescription1\*. EXT1&#124;... Popis souboru *n*&#124;\*. ext *n*&#124;&#124;

kde '&#124;' je znak oddělovače určený parametrem *chSeparator*. Příklad:

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

Použijte výchozí oddělovač '&#124;', Pokud předáte tento řetězec do objektu knihovny `CFileDialog` MFC. Použijte oddělovač null \ 0, pokud tento řetězec předáte do dialogového okna společné **otevření souboru** .

##  <a name="getmaxcolortableentries"></a>Služby CImage ve:: GetMaxColorTableEntries

Načte maximální počet položek v tabulce barev.

```
int GetMaxColorTableEntries() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v tabulce barev.

### <a name="remarks"></a>Poznámky

Tato metoda podporuje pouze rastrové obrázky oddílů DIB.

##  <a name="getpitch"></a>Služby CImage ve:: getrozteč

Načte sklon obrázku.

```
int GetPitch() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Rozteč obrázku Pokud je vrácená hodnota záporná, rastrový obrázek je v dolní části DIB a jeho počátek je spodní levý roh. Pokud je vrácená hodnota kladná, je rastrový obrázek v levém horním rohu a jeho počátek je levý horní roh.

### <a name="remarks"></a>Poznámky

Rozteč je vzdálenost (v bajtech) mezi dvěma adresami paměti, které reprezentují začátek jedné rastrové čáry a začátek další rastrové čáry. Vzhledem k tomu, že se v bajtech měří rozteč, výška obrázku vám pomůže určit formát pixelu. Rozteč může také zahrnovat další paměť vyhrazenou pro rastrový obrázek.

Použijte `GetPitch` s [getbity](#getbits) k nalezení jednotlivých pixelů obrázku.

> [!NOTE]
> Tato metoda podporuje pouze rastrové obrázky oddílů DIB.

##  <a name="getpixel"></a>Služby CImage ve:: GetPixel

Načte barvu pixelu v umístění určeném *x* a *y*.

```
COLORREF GetPixel(int x, int y) const throw();
```

### <a name="parameters"></a>Parametry

*x*<br/>
Souřadnice x v pixelech

*y*<br/>
Souřadnice y v pixelech

### <a name="return-value"></a>Návratová hodnota

Červená, zelená, modrá (RGB) hodnota pixelu. Pokud je pixel mimo aktuální oblast oříznutí, návratová hodnota je CLR_INVALID.

##  <a name="getpixeladdress"></a>Služby CImage ve:: GetPixelAddress

Načte přesnou adresu pixelu.

```
void* GetPixelAddress(int x, int y) throw();
```

### <a name="parameters"></a>Parametry

*x*<br/>
Souřadnice x v pixelech

*y*<br/>
Souřadnice y v pixelech

### <a name="remarks"></a>Poznámky

Adresa se určuje podle souřadnic pixelu, sklonu rastrového obrázku a bitů na pixel.

Pro formáty, které mají méně než 8 bitů na pixel, vrátí tato metoda adresu bajtu obsahujícího pixel. Pokud má například formát obrázku 4 bity na pixel, `GetPixelAddress` vrátí adresu prvního pixelu v bajtu a je třeba vypočítat 2 pixely na bajt.

> [!NOTE]
> Tato metoda podporuje pouze rastrové obrázky oddílů DIB.

##  <a name="gettransparentcolor"></a>Služby CImage ve:: GetTransparentColor

Načte indexované umístění transparentní barvy v paletě barev.

```
LONG GetTransparentColor() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Index průhledné barvy

##  <a name="getwidth"></a>Služby CImage ve:: getwidth

Načte šířku obrázku v pixelech.

```
int GetWidth() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Šířka rastrového obrázku (v pixelech).

##  <a name="isdibsection"></a>Služby CImage ve:: IsDIBSection

Určuje, zda je připojen rastrový obrázek oddíl DIB.

```
bool IsDIBSection() const throw();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je připojen rastrový obrázek oddíl DIB. V opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Pokud rastr není oddíl DIB, nemůžete použít následující `CImage` metody, které podporují pouze rastrové obrázky oddílů DIB:

- [Getbity](#getbits)

- [GetColor](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [Getrozteč](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

##  <a name="isindexed"></a>Služby CImage ve::-Indexed

Určuje, zda jsou pixely rastrového obrázku mapovány na paletu barev.

```
bool IsIndexed() const throw();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je indexovaná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí hodnotu TRUE pouze v případě, že je rastrový obrázek 8 bitů (256 barev) nebo méně.

> [!NOTE]
> Tato metoda podporuje pouze rastrové obrázky oddílů DIB.

##  <a name="isnull"></a>Služby CImage ve:: IsNull

Určuje, zda je rastrový obrázek aktuálně načten.

```
bool IsNull() const throw();
```

### <a name="remarks"></a>Poznámky

Tato metoda vrátí hodnotu TRUE, pokud není bitmapa momentálně načtena; v opačném případě FALSE.

##  <a name="istransparencysupported"></a>Služby CImage ve:: IsTransparencySupported

Určuje, zda aplikace podporuje transparentní rastrové obrázky.

```
static BOOL IsTransparencySupported() throw();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud aktuální platforma podporuje průhlednost. V opačném případě 0.

### <a name="remarks"></a>Poznámky

Pokud je návratová hodnota nenulová a je podporována průhlednost, volání [AlphaBlend](#alphablend), [TransparentBlt](#transparentblt)nebo [Draw](#draw) zpracuje průhledné barvy.

##  <a name="load"></a>Služby CImage ve:: Load

Načte obrázek.

```
HRESULT Load(LPCTSTR pszFileName) throw();
HRESULT Load(IStream* pStream) throw();
```

### <a name="parameters"></a>Parametry

*pszFileName*<br/>
Ukazatel na řetězec obsahující název souboru obrázku, který se má načíst.

*pStream*<br/>
Ukazatel na datový proud obsahující název souboru obrázku, který se má načíst.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Načte obrázek určený parametrem *pszFileName* nebo *pStream*.

Platné typy obrázků jsou BMP, GIF, JPEG, PNG a TIFF.

##  <a name="loadfromresource"></a>Služby CImage ve:: LoadFromResource

Načte obrázek z RASTRového prostředku.

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
Pořídí instanci modulu, který obsahuje obrázek, který má být načten.

*pszResourceName*<br/>
Ukazatel na řetězec obsahující název prostředku, který obsahuje obrázek, který se má načíst.

*nIDResource*<br/>
ID prostředku, který se má načíst

### <a name="remarks"></a>Poznámky

Prostředek musí být typu RASTRový.

##  <a name="maskblt"></a>Služby CImage ve:: MaskBlt

Kombinuje barevná data pro zdrojové a cílové bitmapy pomocí zadané masky a operace rastrového obrázku.

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
Popisovač modulu, jehož spustitelný soubor obsahuje prostředek.

*xDest*<br/>
Souřadnice x (v logických jednotkách) levého horního rohu cílového obdélníku.

*yDest*<br/>
Souřadnice y v levém horním rohu cílového obdélníku v logických jednotkách.

*nDestWidth*<br/>
Šířka cílového obdélníku a zdrojové bitmapy v logických jednotkách.

*nDestHeight*<br/>
Výška cílového obdélníku a zdrojové bitmapy v logických jednotkách.

*xSrc*<br/>
Logická souřadnice x levého horního rohu zdrojové bitmapy.

*ySrc*<br/>
Logická souřadnice y levého horního rohu zdrojové bitmapy.

*hbmMask*<br/>
Zpracování rastrového obrázku s monochromatickou maskou v kombinaci s barevným rastrovým obrázkem v kontextu zdrojového zařízení.

*xMask*<br/>
Vodorovný posun pixelu pro rastrový obrázek masky určený parametrem *hbmMask*

*yMask*<br/>
Posun svislého pixelu pro rastrový obrázek masky určený parametrem *hbmMask*

*dwROP*<br/>
Určuje kódy operací rastrového typu popředí a pozadí, které metoda používá k řízení kombinace zdrojových a cílových dat. Kód operace rastrového obrazu na pozadí je uložen v horním bajtu slova s vyšším pořadím této hodnoty; kód operace rastru na popředí je uložen v bajtu s nižším pořadím slova této hodnoty v dolním pořadí. slovo s nižším pořadím této hodnoty je ignorováno a mělo by být nula. Diskuzi o popředí a pozadí v souvislosti s touto metodou naleznete v části `MaskBlt` v Windows SDK. Seznam běžných kódů rastrových operací najdete v části `BitBlt` v Windows SDK.

*rectDest*<br/>
Odkaz na `RECT` strukturu, která identifikuje cíl.

*pointSrc*<br/>
`POINT` Struktura označující levý horní roh zdrojového obdélníku.

*pointMask*<br/>
`POINT` Struktura označující levý horní roh rastrového obrázku masky.

*pointDest*<br/>
Odkaz na `POINT` strukturu, která identifikuje levý horní roh cílového obdélníku v logických jednotkách.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné, jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda se vztahuje jenom na Windows NT verze 4,0 a novější.

##  <a name="operator_hbitmap"></a>Služby CImage ve:: operator HBITMAP

Tento operátor použijte k získání připojené obslužné rutiny `CImage` Windows GDI objektu. Tento operátor je operátor přetypování, který podporuje přímé použití objektu HBITMAP.

##  <a name="plgblt"></a>Služby CImage ve::P lgBlt

Provede přenos bitového bloku z obdélníku v kontextu zdrojového zařízení do kosoúhelníke v kontextu cílového zařízení.

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
Ukazatel na pole tří bodů v logickém prostoru, který identifikuje tři rohy cílové kosoúhelníke. Levý horní roh zdrojového obdélníku je namapován na první bod v tomto poli, v pravém horním rohu druhého bodu v tomto poli a v levém dolním rohu na třetí bod. Pravý dolní roh zdrojového obdélníku je namapován na implicitní čtvrtý bod v kosoúhelníki.

*hbmMask*<br/>
Popisovač volitelné monochromatické bitmapy, který se používá k maskování barev zdrojového obdélníku.

*xSrc*<br/>
Souřadnice x (v logických jednotkách) levého horního rohu zdrojového obdélníku.

*ySrc*<br/>
Souřadnice y v levém horním rohu zdrojového obdélníku v logických jednotkách.

*nSrcWidth*<br/>
Šířka zdrojového obdélníku v logických jednotkách.

*nSrcHeight*<br/>
Výška zdrojového obdélníku v logických jednotkách

*xMask*<br/>
Souřadnice x levého horního rohu monochromatického rastrového obrázku.

*yMask*<br/>
Souřadnice y levého horního rohu monochromatického rastrového obrázku.

*rectSrc*<br/>
Odkaz na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) , která určuje souřadnice zdrojového obdélníku.

*pointMask*<br/>
Struktura [bodu](/previous-versions/dd162805\(v=vs.85\)) označující levý horní roh rastrového obrázku masky.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné, jinak 0.

### <a name="remarks"></a>Poznámky

Pokud *hbmMask* identifikuje platný monochromatický rastrový `PlgBit` obrázek, používá tento rastrový obrázek k maskování bitů dat barev ze zdrojového obdélníku.

Tato metoda se vztahuje jenom na Windows NT verze 4,0 a novější. Podrobnější informace najdete v tématu [PlgBlt](/windows/win32/api/wingdi/nf-wingdi-plgblt) v Windows SDK.

##  <a name="releasedc"></a>Služby CImage ve:: ReleaseDC

Uvolní kontext zařízení.

```
void ReleaseDC() const throw();
```

### <a name="remarks"></a>Poznámky

Vzhledem k tomu, že pouze jedna Bitmapa může být vybrána v kontextu zařízení v jednom okamžiku `ReleaseDC` , je nutné zavolat pro každé volání [GetDC](#getdc).

##  <a name="releasegdiplus"></a>Služby CImage ve:: ReleaseGDIPlus

Uvolňuje prostředky používané rozhraním GDI+.

```
void ReleaseGDIPlus() throw();
```

### <a name="remarks"></a>Poznámky

Tato metoda musí být volána, aby uvolnila prostředky, které `CImage` jsou přiděleny globálním objektem. Viz [služby CImage ve:: služby CImage ve](#cimage).

##  <a name="save"></a>Služby CImage ve:: Save

Uloží obrázek do zadaného datového proudu nebo souboru na disku.

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
Ukazatel na objekt COM IStream obsahující data bitové kopie souboru.

*pszFileName*<br/>
Ukazatel na název souboru pro obrázek.

*guidFileType*<br/>
Typ souboru, ve kterém má být obrázek uložen. Může být jedna z následujících akcí:

- `ImageFormatBMP`Nekomprimovaný rastrový obrázek.

- `ImageFormatPNG`Komprimovaný obrázek PNG (Portable Network Graphics).

- `ImageFormatJPEG`Komprimovaný obrázek JPEG.

- `ImageFormatGIF`Komprimovaný obrázek GIF.

> [!NOTE]
> Úplný seznam konstant najdete v tématu konstanty **formátu souboru obrázku** v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Voláním této funkce uložíte image s použitím zadaného názvu a typu. Pokud parametr *guidFileType* není zahrnutý, použije se k určení formátu obrázku Přípona souboru názvu souboru. Pokud není k dispozici žádné rozšíření, bude obrázek uložen ve formátu BMP.

##  <a name="setcolortable"></a>Služby CImage ve:: SetColorTable

Nastaví hodnoty barvy červené, zelené, modré (RGB) pro rozsah položek v paletě oddílu DIB.

```
void SetColorTable(
    UINT iFirstColor,
    UINT nColors,
    const RGBQUAD* prgbColors) throw();
```

### <a name="parameters"></a>Parametry

*iFirstColor*<br/>
Index tabulky barev prvního záznamu, který se má nastavit

*nColors*<br/>
Počet položek tabulky barev, které mají být nastaveny.

*prgbColors*<br/>
Ukazatel na pole struktur [RGBQUAD](/windows/win32/api/wingdi/ns-wingdi-rgbquad) pro nastavení položek v tabulce barev.

### <a name="remarks"></a>Poznámky

Tato metoda podporuje pouze rastrové obrázky oddílů DIB.

##  <a name="setpixel"></a>Služby CImage ve:: funkce SetPixel

Nastaví barvu pixelu v daném umístění rastrového obrázku.

```
void SetPixel(int x, int y, COLORREF color) throw();
```

### <a name="parameters"></a>Parametry

*x*<br/>
Vodorovné umístění pixelu, které se má nastavit

*y*<br/>
Svislé umístění pixelu, které se má nastavit

*barevných*<br/>
Barva, na kterou nastavíte pixel.

### <a name="remarks"></a>Poznámky

Tato metoda se nezdařila, pokud souřadnice pixelu leží mimo vybranou oblast oříznutí.

##  <a name="setpixelindexed"></a>Služby CImage ve:: SetPixelIndexed

Nastaví barvu v pixelech na barvu umístěnou na *iIndex* v paletě barev.

```
void SetPixelIndexed(int x, int y, int iIndex) throw();
```

### <a name="parameters"></a>Parametry

*x*<br/>
Vodorovné umístění pixelu, které se má nastavit

*y*<br/>
Svislé umístění pixelu, které se má nastavit

*iIndex*<br/>
Index barvy v paletě barev

##  <a name="setpixelrgb"></a>Služby CImage ve:: SetPixelRGB

Nastaví pixel v umístěních určených *x* a *y* na barvy označené *r*, *g*a *b*v červené, zelené a modré imagi (RGB).

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
Vodorovné umístění pixelu, které se má nastavit

*y*<br/>
Svislé umístění pixelu, které se má nastavit

*r*<br/>
Intenzita červené barvy.

*g*<br/>
Intenzita zelené barvy.

*b*<br/>
Intenzita modré barvy.

### <a name="remarks"></a>Poznámky

Červené, zelené a modré parametry jsou reprezentované číslem mezi 0 a 255. Pokud nastavíte všechny tři parametry na hodnotu nula, kombinovaná Výsledná barva je černá. Pokud nastavíte všechny tři parametry na 255, kombinovaná Výsledná barva je bílá.

##  <a name="settransparentcolor"></a>Služby CImage ve:: SetTransparentColor

Nastaví barvu v daném indexovaném umístění jako transparentní.

```
LONG SetTransparentColor(LONG iTransparentColor) throw();
```

### <a name="parameters"></a>Parametry

*iTransparentColor*<br/>
Index v paletě barev barvy, který má být nastaven na hodnotu Transparent. Pokud-1, není žádná barva nastavena na transparentní.

### <a name="return-value"></a>Návratová hodnota

Index barvy, která byla dříve nastavena jako průhledná.

##  <a name="stretchblt"></a>Služby CImage ve:: StretchBlt

Zkopíruje rastrový obrázek z kontextu zdrojového zařízení do tohoto aktuálního kontextu zařízení.

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
Souřadnice x (v logických jednotkách) levého horního rohu cílového obdélníku.

*yDest*<br/>
Souřadnice y v levém horním rohu cílového obdélníku v logických jednotkách.

*nDestWidth*<br/>
Šířka cílového obdélníku v logických jednotkách.

*nDestHeight*<br/>
Výška cílového obdélníku v logických jednotkách.

*dwROP*<br/>
Operace rastru, která má být provedena. Kódy pro rastrové operace definují přesně způsob, jak kombinovat bity zdroje, cíle a vzor (jak definuje aktuálně vybraný štětec) k vytvoření cíle. Seznam dalších kódů s rastrovými operace a jejich popis naleznete v tématu [BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) v Windows SDK.

*rectDest*<br/>
Odkaz na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) , která identifikuje cíl.

*xSrc*<br/>
Souřadnice x (v logických jednotkách) levého horního rohu zdrojového obdélníku.

*ySrc*<br/>
Souřadnice y v levém horním rohu zdrojového obdélníku v logických jednotkách.

*nSrcWidth*<br/>
Šířka zdrojového obdélníku v logických jednotkách.

*nSrcHeight*<br/>
Výška zdrojového obdélníku v logických jednotkách

*rectSrc*<br/>
Odkaz na `RECT` strukturu, která identifikuje zdroj.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné, jinak 0.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [StretchBlt](/windows/win32/api/wingdi/nf-wingdi-stretchblt) v Windows SDK.

##  <a name="transparentblt"></a>Služby CImage ve:: TransparentBlt

Zkopíruje rastrový obrázek z kontextu zdrojového zařízení do tohoto aktuálního kontextu zařízení.

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
Souřadnice x (v logických jednotkách) levého horního rohu cílového obdélníku.

*yDest*<br/>
Souřadnice y v levém horním rohu cílového obdélníku v logických jednotkách.

*nDestWidth*<br/>
Šířka cílového obdélníku v logických jednotkách.

*nDestHeight*<br/>
Výška cílového obdélníku v logických jednotkách.

*crTransparent*<br/>
Barva ve zdrojové bitmapě, která má být považována za průhlednou. Ve výchozím nastavení je CLR_INVALID, což znamená, že by měla být použita barva aktuálně nastavená jako průhledná barva obrázku.

*rectDest*<br/>
Odkaz na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) , která identifikuje cíl.

*xSrc*<br/>
Souřadnice x (v logických jednotkách) levého horního rohu zdrojového obdélníku.

*ySrc*<br/>
Souřadnice y v levém horním rohu zdrojového obdélníku v logických jednotkách.

*nSrcWidth*<br/>
Šířka zdrojového obdélníku v logických jednotkách.

*nSrcHeight*<br/>
Výška zdrojového obdélníku v logických jednotkách

*rectSrc*<br/>
Odkaz na `RECT` strukturu, která identifikuje zdroj.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je to úspěšné, jinak FALSE.

### <a name="remarks"></a>Poznámky

`TransparentBlt`je podporováno pro zdrojové bitmapy o velikosti 4 bitů na pixel a 8 bitů na pixel. Použijte [služby CImage ve:: AlphaBlend](#alphablend) k určení 32 rastrových obrázků bitů na pixel s průhledností.

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

[Ukázka MMXSwarm](../../overview/visual-cpp-samples.md)<br/>
[Ukázka SimpleImage](../../overview/visual-cpp-samples.md)<br/>
[Rastrové obrázky nezávislé na zařízení](/windows/win32/gdi/device-independent-bitmaps)<br/>
[CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibsection)<br/>
[Desktopové komponenty ATL objektů COM](../../atl/atl-com-desktop-components.md)<br/>
[Rastrové obrázky nezávislé na zařízení](/windows/win32/gdi/device-independent-bitmaps)<br/>
[CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibsection)
