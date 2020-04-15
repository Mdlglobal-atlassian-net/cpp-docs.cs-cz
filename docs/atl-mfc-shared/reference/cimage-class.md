---
title: Třída CImage
ms.date: 08/19/2019
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
ms.openlocfilehash: 5b5ef833a3755b07e42a60b24464b1f260062d16
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317813"
---
# <a name="cimage-class"></a>Třída CImage

`CImage`Poskytuje rozšířenou podporu bitmap, včetně možnosti načítat a ukládat obrazy ve formátech PNG (JPEG, GIF, BMP) a Portable Network Graphics (Portable Network Graphics).

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CImage
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CImage::CImage](#cimage)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CImage::AlphaBlend](#alphablend)|Zobrazí bitmapy s průhlednými nebo poloprůhlednými obrazovými body.|
|[CImage::Připojit](#attach)|Připojí HBITMAP k `CImage` objektu. Lze použít buď s bitmapami oddílu bez DIB, nebo s bitmapami oddílů DIB.|
|[CImage::BitBlt](#bitblt)|Zkopíruje bitmapu z kontextu zdrojového zařízení do tohoto aktuálního kontextu zařízení.|
|[CImage::Vytvořit](#create)|Vytvoří bitmapu oddílu DIB a připojí ji `CImage` k dříve vytvořenému objektu.|
|[CImage::CreateEx](#createex)|Vytvoří bitmapu oddílu DIB (s dalšími parametry) a `CImage` připojí ji k dříve vytvořenému objektu.|
|[CImage::Destroy](#destroy)|Odpojí bitmapu od `CImage` objektu a zničí bitmapu.|
|[CImage::Detach](#detach)|Odpojí bitmapu od `CImage` objektu.|
|[CImage::Draw](#draw)|Zkopíruje bitmapu ze zdrojového obdélníku do cílového obdélníku. `Draw`Roztáhne nebo zkomprimuje bitmapu tak, aby odpovídala rozměrům cílového obdélníku, pokud je to nutné, a zpracovává alfa prolnutí a průhledné barvy.|
|[CImage::GetBits](#getbits)|Načte ukazatel na skutečné hodnoty obrazových bodů bitmapy.|
|[CImage::GetBPP](#getbpp)|Načte bity na pixel.|
|[CImage::GetColortable](#getcolortable)|Načte hodnoty barev červené, zelené, modré (RGB) z oblasti položek v tabulce barev.|
|[CImage::GetDC](#getdc)|Načte kontext zařízení, do kterého je vybrána aktuální bitmapa.|
|[CImage::GetExporterFilterString](#getexporterfilterstring)|Vyhledá dostupné formáty obrázků a jejich popisy.|
|[CImage::GetHeight](#getheight)|Načte výšku aktuálního obrazu v obrazových bodech.|
|[CImage::GetImporterFilterString](#getimporterfilterstring)|Vyhledá dostupné formáty obrázků a jejich popisy.|
|[CImage::GetMaxColortableEntries](#getmaxcolortableentries)|Načte maximální počet položek v tabulce barev.|
|[CImage::GetPitch](#getpitch)|Načte výšku aktuálního obrázku v bajtech.|
|[CImage::GetPixel](#getpixel)|Načte barvu obrazového bodu určenou *parametrem x* a *y*.|
|[CImage::GetPixelAddress](#getpixeladdress)|Načte adresu daného pixelu.|
|[CImage::GetTransparentColor](#gettransparentcolor)|Načte pozici průhledné barvy v tabulce barev.|
|[CImage::GetWidth](#getwidth)|Načte šířku aktuálního obrazu v obrazových bodech.|
|[CImage::IsDibSection](#isdibsection)|Určuje, zda je připojená bitmapa oddílem DIB.|
|[CImage::Indexed](#isindexed)|Označuje, že barvy bitmapy jsou mapovány na indexovanou paletu.|
|[CImage::Isnull](#isnull)|Označuje, zda je aktuálně načtena zdrojová bitmapa.|
|[cimage::Podporováno istransparency](#istransparencysupported)|Označuje, zda aplikace podporuje průhledné bitmapy.|
|[CImage::Načíst](#load)|Načte obraz ze zadaného souboru.|
|[CImage::LoadFromResource](#loadfromresource)|Načte bitovou kopii ze zadaného prostředku.|
|[CImage::MaskBlt](#maskblt)|Zkombinuje barevná data pro zdrojové a cílové bitmapy pomocí zadané masky a rastrové operace.|
|[CImage::PlgBlt](#plgblt)|Provádí přenos bitového bloku z obdélníku v kontextu zdrojového zařízení do rovnoběžníku v kontextu cílového zařízení.|
|[CImage::ReleaseDC](#releasedc)|Uvolní kontext zařízení, který byl načten s [CImage::GetDC](#getdc).|
|[cimage::ReleaseGDIPlus](#releasegdiplus)|Uvolní prostředky používané GDI+. Musí být volána k uvolnění `CImage` prostředků vytvořených globálním objektem.|
|[CImage::Uložit](#save)|Uloží obraz jako zadaný typ. `Save`nelze určit volby obrazu.|
|[CImage::SetColortable](#setcolortable)|Nastaví hodnoty barev červené, zelené a modré RGB) v rozsahu položek v tabulce barev v části DIB.|
|[CImage::SetPixel](#setpixel)|Nastaví obrazový bod na určených souřadnicích na zadanou barvu.|
|[CImage::SetPixelIndexed](#setpixelindexed)|Nastaví obrazový bod na určených souřadnicích barvu na zadaný index palety.|
|[CImage::SetPixelRGB](#setpixelrgb)|Nastaví obrazový bod na určených souřadnicích na zadanou červenou, zelenou, modrou (RGB).|
|[CImage::SetTransparencyColor](#settransparentcolor)|Nastaví index barvy, která má být považována za průhlednou. Pouze jedna barva v paletě může být průhledná.|
|[CImage::StretchBlt](#stretchblt)|Zkopíruje bitmapu ze zdrojového obdélníku do cílového obdélníku a v případě potřeby ji roztáhne nebo zkomprimuje tak, aby odpovídala rozměrům cílového obdélníku.|
|[CImage::TransparentBlt](#transparentblt)|Zkopíruje bitmapu s průhlednou barvou z kontextu zdrojového zařízení do tohoto aktuálního kontextu zařízení.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CImage::operátor HBITMAP](#operator_hbitmap)|Vrátí popisovač systému `CImage` Windows připojený k objektu.|

## <a name="remarks"></a>Poznámky

`CImage`trvá bitmapy, které jsou buď bitmapové (DIB) části nezávislé na zařízení, nebo ne; můžete však použít [Create](#create) nebo [CImage::Load](#load) pouze s oddíly DIB. Bitmapu oddílu bez DIB můžete `CImage` připojit k objektu pomocí [příkazu Připojit](#attach), ale pak nemůžete použít následující `CImage` metody, které podporují pouze bitmapy oddílu DIB:

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [Získat výšku](#getpitch)

- [Adresa GetPixel](#getpixeladdress)

- [JeIndexed](#isindexed)

- [SetColorTable](#setcolortable)

Chcete-li zjistit, zda je připojená bitmapa oddílem DIB, zavolejte [IsDibSection](#isdibsection).

> [!NOTE]
> V sadě Visual Studio .NET 2003 tato třída `CImage` udržuje počet počet vytvořených objektů. Vždy, když počet přejde `GdiplusShutdown` na 0, funkce je automaticky volána k uvolnění prostředků používaných GDI+. Tím je zajištěno, že všechny `CImage` objekty vytvořené přímo nebo nepřímo `GdiplusShutdown` knihovnami `DllMain`DLL jsou vždy správně zničeny a nejsou volány z aplikace .

> [!NOTE]
> Použití `CImage` globálních objektů v dll se nedoporučuje. Pokud potřebujete použít globální `CImage` objekt v knihovně DLL, zavolejte [CImage::ReleaseGDIPlus](#releasegdiplus) explicitně uvolnit prostředky používané GDI+.

`CImage`nelze vybrat do nového [CDC](../../mfc/reference/cdc-class.md). `CImage`vytvoří vlastní HDC pro obraz. Vzhledem k tomu, že HBITMAP lze vybrat pouze do jednoho `CImage` HDC najednou, HBITMAP spojené s nelze vybrat do jiného HDC. Pokud potřebujete CDC, načíst HDC `CImage` z a dát [cdc::FromHandle](../../mfc/reference/cdc-class.md#fromhandle).

## <a name="example"></a>Příklad

```cpp
// Get a CDC for the image
CDC* pDC = CDC::FromHandle(m_myImage.GetDC());

// Use pDC here
pDC->Rectangle(0, 40, 100, 50);
m_myImage.ReleaseDC();
```

Při použití `CImage` v projektu knihovny MFC, poznamenejte si, které členské funkce v projektu očekávat ukazatel na objekt [CBitmap.](../../mfc/reference/cbitmap-class.md) Pokud chcete použít `CImage` s takovou funkcí, jako je [CMenu::AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu), použijte [CBitmap::FromHandle](../../mfc/reference/cbitmap-class.md#fromhandle), předejte ji `CImage` HBITMAP a použijte vrácenou `CBitmap*`.

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

Prostřednictvím `CImage`, máte přístup ke skutečné bity oddílu DIB. `CImage` Objekt můžete použít kdekoli, kde jste dříve použili oddíl Win32 HBITMAP nebo DIB.

Můžete použít `CImage` buď z knihovny MFC nebo ATL.

> [!NOTE]
> Při vytváření projektu `CImage`pomocí , `CString` je nutné definovat před zahrnutím *atlimage.h*. Pokud váš projekt používá knihovnu ATL bez knihovny MFC, zahrňte *soubor atlstr.h* před *zahrnutím souboru atlimage.h*. Pokud váš projekt používá knihovnu MFC (nebo pokud se jedná o projekt knihovny ATL s podporou knihovny MFC), zahrňte před *zahrnutím souboru atlimage.h* *soubor afxstr.h* .<br/>
> <br/>
> Podobně je nutné zahrnout *atlimage.h* před *zahrnutím atlimpl.cpp*. Chcete-li to snadno provést, zahrňte *atlimage.h* do *pch.h* *(stdafx.h* v sadě Visual Studio 2017 a starší).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlimage.h

## <a name="cimagealphablend"></a><a name="alphablend"></a>CImage::AlphaBlend

Zobrazí bitmapy s průhlednými nebo poloprůhlednými obrazovými body.

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
Zpracovat kontext cílového zařízení.

*xDest*<br/>
Souřadnice x v logických jednotkách levého horního rohu cílového obdélníku.

*yDest*<br/>
Souřadnice y v logických jednotkách levého horního rohu cílového obdélníku.

*bSrcAlpha*<br/>
Hodnota průhlednosti alfa, která se použije na celou zdrojovou bitmapu. Výchozí hodnota 0xff (255) předpokládá, že obraz je neprůhledný a že chcete použít pouze hodnoty alfa na pixel.

*bBlendOp*<br/>
Funkce alfa prolnutí pro zdrojové a cílové rastrové obrázky, globální hodnota alfa, která se použije na celou zdrojovou bitmapu, a informace o formátování zdrojové bitmapy. Funkce zdrojové a cílové prolnutí jsou v současné době omezeny na AC_SRC_OVER.

*pointDest*<br/>
Odkaz na [point](/previous-versions/dd162805\(v=vs.85\)) strukturu, která identifikuje levý horní roh cílového obdélníku v logických jednotkách.

*nDestWidth*<br/>
Šířka cílového obdélníku v logických jednotkách.

*nDestVýška*<br/>
Výška cílového obdélníku v logických jednotkách.

*xSrc*<br/>
Logická souřadnice x levého horního rohu zdrojového obdélníku.

*ySrc řekl:*<br/>
Logická souřadnice y levého horního rohu zdrojového obdélníku.

*nSrcWidth*<br/>
Šířka zdrojového obdélníku v logických jednotkách.

*nSrcVýška*<br/>
Výška zdrojového obdélníku v logických jednotkách.

*rectDest*<br/>
Odkaz na strukturu [RECT,](/previous-versions/dd162897\(v=vs.85\)) identifikace cíle.

*rectSrc*<br/>
Odkaz na `RECT` strukturu, identifikace zdroje.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Bitmapy alfa prolnutí podporují prolnutí barev na základě počtu pixelů.

Když je *hodnota bBlendOp* nastavena na výchozí hodnotu AC_SRC_OVER, zdrojová bitmapa je umístěna nad cílovou bitmapu na základě alfa hodnot zdrojových obrazových bodů.

## <a name="cimageattach"></a><a name="attach"></a>CImage::Připojit

Připojí *hBitmap* k `CImage` objektu.

```
void Attach(HBITMAP hBitmap, DIBOrientation eOrientation = DIBOR_DEFAULT) throw();
```

### <a name="parameters"></a>Parametry

*hBitmap*<br/>
Popisovač HBITMAP.

*eOrientace*<br/>
Určuje orientaci bitmapy. Může to být jedna z následujících možností:

- DIBOR_DEFAULT Orientace rastrového plánu je určena operačním systémem.

- DIBOR_BOTTOMUP Čáry bitmapy jsou v obráceném pořadí. To [způsobí, že CImage::GetBits](#getbits) vrátit ukazatel ke konci vyrovnávací paměti bitmapy a [CImage::GetPitch](#getpitch) vrátit záporné číslo.

- DIBOR_TOPDOWN Čáry rastrového mapu jsou v pořadí shora dolů. To [způsobí, že CImage::GetBits](#getbits) vrátit ukazatel na první bajt vyrovnávací paměti rastrového obrázku a [CImage::GetPitch](#getpitch) vrátit kladné číslo.

### <a name="remarks"></a>Poznámky

Bitmapa může být buď bitmapa oddílu bez DIB, nebo bitmapa oddílu DIB. Seznam metod, které lze použít pouze s bitmapami oddílů DIB, naleznete v části [IsDIBSection.](#isdibsection)

## <a name="cimagebitblt"></a><a name="bitblt"></a>CImage::BitBlt

Zkopíruje bitmapu z kontextu zdrojového zařízení do tohoto aktuálního kontextu zařízení.

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
Logická souřadnice x levého horního rohu cílového obdélníku.

*yDest*<br/>
Logická souřadnice y levého horního rohu cílového obdélníku.

*dwROP*<br/>
Rastrová operace, která má být provedena. Kódy rastrových operací přesně definují, jak kombinovat bity zdroje, cíl a vzorek (podle definice aktuálně vybrané stopy) a vytvořit tak cíl. Seznam dalších kódů rastrových operací a jejich popisy naleznete v části [BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) v kanisu Windows SDK.

*pointDest*<br/>
A [POINT](/previous-versions/dd162805\(v=vs.85\)) struktura označující levém horním rohu cílového obdélníku.

*nDestWidth*<br/>
Šířka cílového obdélníku v logických jednotkách.

*nDestVýška*<br/>
Výška cílového obdélníku v logických jednotkách.

*xSrc*<br/>
Logická souřadnice x levého horního rohu zdrojového obdélníku.

*ySrc řekl:*<br/>
Logická souřadnice y levého horního rohu zdrojového obdélníku.

*rectDest*<br/>
A [RECT](/previous-versions/dd162897\(v=vs.85\)) struktura označující cílový obdélník.

*bodSrc*<br/>
Struktura `POINT` označující levý horní roh zdrojového obdélníku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak nula.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) v sadě Windows SDK.

## <a name="cimagecimage"></a><a name="cimage"></a>CImage::CImage

Vytvoří `CImage` objekt.

```
CImage() throw();
```

### <a name="remarks"></a>Poznámky

Jakmile vytvoříte objekt, volejte [Create](#create), [Load](#load), [LoadFromResource](#loadfromresource)nebo [Attach](#attach) pro připojení bitmapy k objektu.

**Poznámka:** V sadě Visual Studio tato třída udržuje `CImage` počet počet vytvořených objektů. Vždy, když počet přejde `GdiplusShutdown` na 0, funkce je automaticky volána k uvolnění prostředků používaných GDI+. Tím je zajištěno, že všechny `CImage` objekty vytvořené přímo nebo nepřímo `GdiplusShutdown` knihovnami DLL jsou vždy správně zničeny a nejsou volány z DllMain.

Použití `CImage` globálních objektů v dll se nedoporučuje. Pokud potřebujete použít globální `CImage` objekt v knihovně DLL, zavolejte [CImage::ReleaseGDIPlus](#releasegdiplus) explicitně uvolnit prostředky používané GDI+.

## <a name="cimagecreate"></a><a name="create"></a>CImage::Vytvořit

Vytvoří `CImage` bitmapu a připojí ji k `CImage` dříve vytvořenému objektu.

```
BOOL Create(
    int nWidth,
    int nHeight,
    int nBPP,
    DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parametry

*nŠířka*<br/>
Šířka `CImage` bitmapy v obrazových bodech.

*nVýška*<br/>
Výška `CImage` bitmapy v obrazových bodech. Pokud *nHeight* je pozitivní, bitmapa je DIB zdola nahoru a jeho počátek je levý dolní roh. Pokud *nHeight* je negativní, bitmapa je dib shora dolů a jeho počátek je levý horní roh.

*nBPP*<br/>
Počet bitů na pixel v bitmapě. Obvykle 4, 8, 16, 24 nebo 32. Může být 1 pro monochromatické rastrové obrázky nebo masky.

*dwFlags*<br/>
Určuje, zda má bitmapový objekt alfa kanál. Může být kombinací nuly nebo více z následujících hodnot:

- *vytvořit AlphaChannel* Lze použít pouze v případě, *že je nBPP* 32 a *eCompression* je BI_RGB. Pokud je zadán, vytvořený obraz má hodnotu alfa (průhlednost) pro každý obrazový bod, uloženou ve 4 bajtech každého obrazového bodu (nepoužitý v nealfa 32bitovém obraze). Tento alfa kanál se automaticky používá při volání [CImage::AlphaBlend](#alphablend).

> [!NOTE]
> Při volání [CImage::Draw](#draw), obrazy s alfa kanálem jsou automaticky alfa prolnutí do cíle.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

## <a name="cimagecreateex"></a><a name="createex"></a>CImage::CreateEx

Vytvoří `CImage` bitmapu a připojí ji k `CImage` dříve vytvořenému objektu.

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

*nŠířka*<br/>
Šířka `CImage` bitmapy v obrazových bodech.

*nVýška*<br/>
Výška `CImage` bitmapy v obrazových bodech. Pokud *nHeight* je pozitivní, bitmapa je DIB zdola nahoru a jeho počátek je levý dolní roh. Pokud *nHeight* je negativní, bitmapa je dib shora dolů a jeho počátek je levý horní roh.

*nBPP*<br/>
Počet bitů na pixel v bitmapě. Obvykle 4, 8, 16, 24 nebo 32. Může být 1 pro monochromatické rastrové obrázky nebo masky.

*eKomprese*<br/>
Určuje typ komprese pro komprimovovně nahoru bitmapu (shora dolů DIBs nelze komprimovat). Může se na nich vyvěšovat jedna z následujících hodnot:

- BI_RGB Formát není komprimovaný. Zadání této hodnoty `CImage::CreateEx` při volání `CImage::Create`je ekvivalentní volání .

- BI_BITFIELDS Formát je nekomprimovaný a tabulka barev se skládá ze tří barevných masek DWORD, které určují červenou, zelenou a modrou složku každého obrazového bodu. To platí při použití s bitmapami 16 a 32 bpp.

*pdwBitfields*<br/>
Používá se pouze v případě, že je *eCompression* nastavena na BI_BITFIELDS, jinak musí mít hodnotu NULL. Ukazatel na pole tří bitových masek DWORD určující, které bity každého obrazového bodu se použijí pro červenou, zelenou a modrou složku barvy. Informace o omezeních pro bitová pole naleznete v [tématu BITMAPINFOHEADER](/previous-versions//dd183376\(v=vs.85\)) v sadě Windows SDK.

*dwFlags*<br/>
Určuje, zda má bitmapový objekt alfa kanál. Může být kombinací nuly nebo více z následujících hodnot:

- *vytvořit AlphaChannel* Lze použít pouze v případě, *že je nBPP* 32 a *eCompression* je BI_RGB. Pokud je zadán, vytvořený obraz má hodnotu alfa (průhlednost) pro každý obrazový bod, uloženou ve 4 bajtech každého obrazového bodu (nepoužitý v nealfa 32bitovém obraze). Tento alfa kanál se automaticky používá při volání [CImage::AlphaBlend](#alphablend).

   > [!NOTE]
   > Při volání [CImage::Draw](#draw), obrazy s alfa kanálem jsou automaticky alfa prolnutí do cíle.

### <a name="return-value"></a>Návratová hodnota

PRAVDA v případě úspěchu. Jinak FALSE.

### <a name="example"></a>Příklad

Následující příklad vytvoří bitmapu o rozměrech 100 x 100, která ke kódování každého obrazového bodu používá 16 bitů. V daném 16bitovém pixelu bity 0-3 kódují červenou komponentu, bity 4-7 kódují zeleně a bity 8-11 kódují modře. Zbývající 4 bity jsou nevyužité.

```cpp
DWORD adwBitmasks[3] = { 0x0000000f, 0x000000f0, 0x00000f00 };
m_myImage.CreateEx(100, 100, 16, BI_BITFIELDS, adwBitmasks, 0);
```

## <a name="cimagedestroy"></a><a name="destroy"></a>CImage::Destroy

Odpojí bitmapu od `CImage` objektu a zničí bitmapu.

```
void Destroy() throw();
```

## <a name="cimagedetach"></a><a name="detach"></a>CImage::Detach

Odpojí bitmapu od `CImage` objektu.

```
HBITMAP Detach() throw();
```

### <a name="return-value"></a>Návratová hodnota

Úchyt k odpojené bitmapě nebo NULL, pokud není připojena žádná bitmapa.

## <a name="cimagedraw"></a><a name="draw"></a>CImage::Draw

Zkopíruje bitmapu z kontextu zdrojového zařízení do aktuálního kontextu zařízení.

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
Souřadnice x v logických jednotkách levého horního rohu cílového obdélníku.

*yDest*<br/>
Souřadnice y v logických jednotkách levého horního rohu cílového obdélníku.

*nDestWidth*<br/>
Šířka cílového obdélníku v logických jednotkách.

*nDestVýška*<br/>
Výška cílového obdélníku v logických jednotkách.

*xSrc*<br/>
Souřadnice x v logických jednotkách levého horního rohu zdrojového obdélníku.

*ySrc řekl:*<br/>
Souřadnice y v logických jednotkách levého horního rohu zdrojového obdélníku.

*nSrcWidth*<br/>
Šířka zdrojového obdélníku v logických jednotkách.

*nSrcVýška*<br/>
Výška zdrojového obdélníku v logických jednotkách.

*rectDest*<br/>
Odkaz na strukturu [RECT,](/previous-versions/dd162897\(v=vs.85\)) identifikace cíle.

*rectSrc*<br/>
Odkaz na `RECT` strukturu, identifikace zdroje.

*pointDest*<br/>
Odkaz na [point](/previous-versions/dd162805\(v=vs.85\)) strukturu, která identifikuje levý horní roh cílového obdélníku v logických jednotkách.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

`Draw`provádí stejnou operaci jako [StretchBlt](#stretchblt), pokud obraz neobsahuje průhlednou barvu nebo alfa kanál. V takovém `Draw` případě provede stejnou operaci jako [TransparentBlt](#transparentblt) nebo [AlphaBlend](#alphablend) podle potřeby.

Pro verze, `Draw` které neurčují zdrojový obdélník, je výchozí celý zdrojový obraz. Pro verzi, `Draw` která neurčuje velikost cílového obdélníku, velikost zdrojového obrazu je výchozí a nedojde k roztažení nebo zmenšení.

## <a name="cimagegetbits"></a><a name="getbits"></a>CImage::GetBits

Načte ukazatel na skutečné bitové hodnoty daného obrazového bodu v bitmapě.

```
void* GetBits() throw();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na vyrovnávací paměť rastrového plánu. Pokud bitmapa je DIB zdola nahoru, ukazatel ukazuje na konci vyrovnávací paměti. Pokud bitmapa je DIB shora dolů, ukazatel odkazuje na první bajt vyrovnávací paměti.

### <a name="remarks"></a>Poznámky

Pomocí tohoto ukazatele spolu s hodnotou vrácenou [GetPitch](#getpitch)můžete vyhledat a změnit jednotlivé obrazové body v obraze.

> [!NOTE]
> Tato metoda podporuje pouze bitmapy oddílu DIB; v důsledku toho přistupujete k obrazovým bodům objektu `CImage` stejným způsobem jako obrazové body oddílu DIB. Vrácený ukazatel odkazuje na obrazový bod v umístění (0, 0).

## <a name="cimagegetbpp"></a><a name="getbpp"></a>CImage::GetBPP

Načte hodnotu bitů na pixel.

```
int GetBPP() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Počet bitů na pixel.

### <a name="remarks"></a>Poznámky

Tato hodnota určuje počet bitů, které definují každý obrazový bod, a maximální počet barev v bitmapě.

Bity na pixel je obvykle 1, 4, 8, 16, 24 nebo 32. Další `biBitCount` informace o této hodnotě naleznete v členu [bitmapinfoheaderu](/previous-versions//dd183376\(v=vs.85\)) v sadě Windows SDK.

## <a name="cimagegetcolortable"></a><a name="getcolortable"></a>CImage::GetColortable

Načte hodnoty barev červené, zelené, modré (RGB) z rozsahu položek v paletě oddílu DIB.

```
void GetColorTable(
    UINT iFirstColor,
    UINT nColors,
    RGBQUAD* prgbColors) const throw();
```

### <a name="parameters"></a>Parametry

*iFirstColor*<br/>
Index tabulky barev první položky načíst.

*nBarvy*<br/>
Počet položek tabulky barev, které chcete načíst.

*prgbBarvy*<br/>
Ukazatel na pole struktur [RGBQUAD](/windows/win32/api/wingdi/ns-wingdi-rgbquad) pro načtení položek tabulky barev.

## <a name="cimagegetdc"></a><a name="getdc"></a>CImage::GetDC

Načte kontext zařízení, ve které je aktuálně vybrán obrázek.

```
HDC GetDC() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač kontextu zařízení.

### <a name="remarks"></a>Poznámky

Pro každé `GetDC`volání do , musíte mít následné volání [ReleaseDC](#releasedc).

## <a name="cimagegetexporterfilterstring"></a><a name="getexporterfilterstring"></a>CImage::GetExporterFilterString

Vyhledá formáty obrázků, které jsou k dispozici pro ukládání obrázků.

```
static HRESULT GetExporterFilterString(
    CSimpleString& strExporters,
    CSimpleArray<GUID>& aguidFileTypes,
    LPCTSTR pszAllFilesDescription = NULL,
    DWORD dwExclude = excludeDefaultSave,
    TCHAR chSeparator = _T('|'));
```

### <a name="parameters"></a>Parametry

*strVývozci*<br/>
Odkaz na `CSimpleString` objekt. Další informace naleznete v **tématu Poznámky.**

*aguidFileTypes*<br/>
Pole identifikátorů GUID s každým prvkem odpovídajícím jednomu z typů souborů v řetězci. V příkladu v *pszAllFilesDescription* níže je *aguidFileTypes*[0] GUID_NULL a zbývající hodnoty pole jsou formáty obrazových souborů podporované aktuálním operačním systémem.

> [!NOTE]
> Úplný seznam konstant naleznete v tématu **Konstanty formátu souboru bitové kopie** v sadě Windows SDK.

*pszAllFilesDescription*<br/>
Pokud tento parametr není null, řetězec filtru bude mít jeden další filtr na začátku seznamu. Tento filtr bude mít aktuální hodnotu *pszAllFilesDescription* pro jeho popis a přijímá soubory jakékoli rozšíření podporované jiným vývozcem v seznamu.

Příklad:

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any exporter.
CImage::GetExporterFilterString(
    strExporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
Sada bitových příznaků určujících, které typy souborů mají být ze seznamu vyloučeny. Přípustné příznaky jsou:

- `excludeGIF`= 0x01 Vylučuje soubory GIF.

- `excludeBMP`= 0x02 Vylučuje soubory BMP (Windows Bitmap).

- `excludeEMF`= 0x04 Vylučuje soubory EMF (Enhanced Metafile).

- `excludeWMF`= 0x08 Vylučuje soubory WMF (Windows Metafile).

- `excludeJPEG`= 0x10 Vylučuje soubory JPEG.

- `excludePNG`= 0x20 Vylučuje soubory PNG.

- `excludeTIFF`= 0x40 Vylučuje soubory TIFF.

- `excludeIcon`= 0x80 Vylučuje soubory ICO (Ikona systému Windows).

- `excludeOther`= 0x80000000 Vylučuje jakýkoli jiný typ souboru, který není uveden výše.

- `excludeDefaultLoad`= 0 Pro načtení jsou ve výchozím nastavení zahrnuty všechny typy souborů

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF`Pro uložení jsou tyto soubory ve výchozím nastavení vyloučeny, protože mají obvykle zvláštní požadavky.

*chSeparátor*<br/>
Oddělovač použitý mezi formáty obrazu. Další informace naleznete v **tématu Poznámky.**

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

### <a name="remarks"></a>Poznámky

Výsledný formátovací řetězec můžete předat objektu [CFileDialog](../../mfc/reference/cfiledialog-class.md) knihovny MFC a vystavit tak přípony dostupných formátů obrazu v dialogovém okně Uložit jako soubor.

Parametr *strExporter* má formát:

popis souboru0&#124;\*.ext0 \*&#124;popis souboru1&#124;.ext1&#124;... popis *n* souboru \*n&#124;.ext *n*&#124;&#124;

kde "&#124;" je znak oddělovače určený písmenem `chSeparator`. Příklad:

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

Pokud tento řetězec předáte objektu knihovny MFC, `CFileDialog` použijte výchozí oddělovač &#124;. Pokud tento řetězec předáte společnému dialogovému oknu Pro ukládání souborů, použijte oddělovač null \0.

## <a name="cimagegetheight"></a><a name="getheight"></a>CImage::GetHeight

Načte výšku obrazu v obrazových bodech.

```
int GetHeight() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Výška obrázku v obrazových bodech.

## <a name="cimagegetimporterfilterstring"></a><a name="getimporterfilterstring"></a>CImage::GetImporterFilterString

Vyhledá formáty obrázků, které jsou k dispozici pro načítání obrázků.

```
static HRESULT GetImporterFilterString(
    CSimpleString& strImporters,
    CSimpleArray<GUID>& aguidFileTypes,
    LPCTSTR pszAllFilesDescription = NULL,
    DWORD dwExclude = excludeDefaultLoad,
    TCHAR chSeparator = _T('|'));
```

### <a name="parameters"></a>Parametry

*StrDovozci*<br/>
Odkaz na `CSimpleString` objekt. Další informace naleznete v **tématu Poznámky.**

*aguidFileTypes*<br/>
Pole identifikátorů GUID s každým prvkem odpovídajícím jednomu z typů souborů v řetězci. V příkladu v *pszAllFilesDescription* níže, *aguidFileTypes*[0] je GUID_NULL se zbývajícími hodnotami pole jsou formáty obrazových souborů podporované aktuálním operačním systémem.

> [!NOTE]
> Úplný seznam konstant naleznete v tématu **Konstanty formátu souboru bitové kopie** v sadě Windows SDK.

*pszAllFilesDescription*<br/>
Pokud tento parametr není null, řetězec filtru bude mít jeden další filtr na začátku seznamu. Tento filtr bude mít aktuální hodnotu *pszAllFilesDescription* pro jeho popis a přijímá soubory jakékoli rozšíření podporované jiným vývozcem v seznamu.

Příklad:

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any importer.
CImage::GetImporterFilterString(
    strImporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
Sada bitových příznaků určujících, které typy souborů mají být ze seznamu vyloučeny. Přípustné příznaky jsou:

- `excludeGIF`= 0x01 Vylučuje soubory GIF.

- `excludeBMP`= 0x02 Vylučuje soubory BMP (Windows Bitmap).

- `excludeEMF`= 0x04 Vylučuje soubory EMF (Enhanced Metafile).

- `excludeWMF`= 0x08 Vylučuje soubory WMF (Windows Metafile).

- `excludeJPEG`= 0x10 Vylučuje soubory JPEG.

- `excludePNG`= 0x20 Vylučuje soubory PNG.

- `excludeTIFF`= 0x40 Vylučuje soubory TIFF.

- `excludeIcon`= 0x80 Vylučuje soubory ICO (Ikona systému Windows).

- `excludeOther`= 0x80000000 Vylučuje jakýkoli jiný typ souboru, který není uveden výše.

- `excludeDefaultLoad`= 0 Pro načtení jsou ve výchozím nastavení zahrnuty všechny typy souborů

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF`Pro uložení jsou tyto soubory ve výchozím nastavení vyloučeny, protože mají obvykle zvláštní požadavky.

*chSeparátor*<br/>
Oddělovač použitý mezi formáty obrazu. Další informace naleznete v **tématu Poznámky.**

### <a name="remarks"></a>Poznámky

Výsledný formátovací řetězec můžete předat objektu [CFileDialog](../../mfc/reference/cfiledialog-class.md) knihovny MFC a vystavit tak přípony dostupných formátů obrazu v dialogovém okně **Otevřít soubor.**

Parametr *strImporter* má formát:

popis souboru0&#124;\*.ext0 \*&#124;popis souboru1&#124;.ext1&#124;... popis *n* souboru \*n&#124;.ext *n*&#124;&#124;

kde '&#124;' je oddělovací znak určený *oddělovačem*. Příklad:

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

Pokud tento řetězec předáte objektu knihovny MFC, `CFileDialog` použijte výchozí oddělovač &#124;. Pokud tento řetězec předáte společnému dialogovému oknu **Otevřít soubor,** použijte oddělovač null \0.

## <a name="cimagegetmaxcolortableentries"></a><a name="getmaxcolortableentries"></a>CImage::GetMaxColortableEntries

Načte maximální počet položek v tabulce barev.

```
int GetMaxColorTableEntries() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v tabulce barev.

### <a name="remarks"></a>Poznámky

Tato metoda podporuje pouze bitmapy oddílu DIB.

## <a name="cimagegetpitch"></a><a name="getpitch"></a>CImage::GetPitch

Načte výšku obrázku.

```
int GetPitch() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Rozteč obrazu. Pokud je vrácená hodnota záporná, bitmapa je DIB zdola nahoru a její počátek je levý dolní roh. Pokud je vrácená hodnota kladná, bitmapa je DIB shora dolů a její počátek je levý horní roh.

### <a name="remarks"></a>Poznámky

Rozteč je vzdálenost v bajtech mezi dvěma adresami paměti, které představují začátek jedné bitmapové čáry a začátek další bitmapové čáry. Vzhledem k tomu, že rozteč se měří v bajtech, výška obrazu vám pomůže určit formát obrazových bodů. Rozteč může také obsahovat další paměť, vyhrazenou pro bitmapu.

Pomocí `GetPitch` [funkce GetBits](#getbits) můžete najít jednotlivé obrazové body obrazu.

> [!NOTE]
> Tato metoda podporuje pouze bitmapy oddílu DIB.

## <a name="cimagegetpixel"></a><a name="getpixel"></a>CImage::GetPixel

Načte barvu obrazového bodu v umístění určeném *x* a *y*.

```
COLORREF GetPixel(int x, int y) const throw();
```

### <a name="parameters"></a>Parametry

*X*<br/>
Souřadnice x pixelu.

*Y*<br/>
Souřadnice y pixelu.

### <a name="return-value"></a>Návratová hodnota

Hodnota červené, zelené, modré (RGB) obrazového bodu. Pokud je obrazový bod mimo aktuální oblast oříznutí, vrátí se hodnota CLR_INVALID.

## <a name="cimagegetpixeladdress"></a><a name="getpixeladdress"></a>CImage::GetPixelAddress

Načte přesnou adresu pixelu.

```
void* GetPixelAddress(int x, int y) throw();
```

### <a name="parameters"></a>Parametry

*X*<br/>
Souřadnice x pixelu.

*Y*<br/>
Souřadnice y pixelu.

### <a name="remarks"></a>Poznámky

Adresa je určena podle souřadnic obrazového bodu, výšky bitmapy a bitů na pixel.

Pro formáty, které mají méně než 8 bitů na pixel, vrátí tato metoda adresu bajtu obsahujícího obrazový bod. Pokud má například formát obrázku 4 `GetPixelAddress` bity na pixel, vrátí adresu prvního obrazového bodu v bajtu a musíte vypočítat 2 obrazové body na bajt.

> [!NOTE]
> Tato metoda podporuje pouze bitmapy oddílu DIB.

## <a name="cimagegettransparentcolor"></a><a name="gettransparentcolor"></a>CImage::GetTransparentColor

Načte indexované umístění průhledné barvy v paletě barev.

```
LONG GetTransparentColor() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Index průhledné barvy.

## <a name="cimagegetwidth"></a><a name="getwidth"></a>CImage::GetWidth

Načte šířku obrazu v obrazových bodech.

```
int GetWidth() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Šířka bitmapy v obrazových bodech.

## <a name="cimageisdibsection"></a><a name="isdibsection"></a>CImage::IsDibSection

Určuje, zda je připojená bitmapa oddílem DIB.

```
bool IsDIBSection() const throw();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je připojená bitmapa oddílEm DIB. Jinak FALSE.

### <a name="remarks"></a>Poznámky

Pokud bitmapa není oddíl DIB, nelze použít `CImage` následující metody, které podporují pouze bitmapy oddílu DIB:

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [Získat výšku](#getpitch)

- [Adresa GetPixel](#getpixeladdress)

- [JeIndexed](#isindexed)

- [SetColorTable](#setcolortable)

## <a name="cimageisindexed"></a><a name="isindexed"></a>CImage::Indexed

Určuje, zda jsou obrazové body bitmapy mapovány na paletu barev.

```
bool IsIndexed() const throw();
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je indexována; jinak FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí hodnotu PRAVDA pouze v případě, že bitmapa je 8bitová (256 barev) nebo méně.

> [!NOTE]
> Tato metoda podporuje pouze bitmapy oddílu DIB.

## <a name="cimageisnull"></a><a name="isnull"></a>CImage::Isnull

Určuje, zda je právě načtena bitmapa.

```
bool IsNull() const throw();
```

### <a name="remarks"></a>Poznámky

Tato metoda vrátí hodnotu PRAVDA, pokud bitmapa není aktuálně načtena. jinak FALSE.

## <a name="cimageistransparencysupported"></a><a name="istransparencysupported"></a>cimage::Podporováno istransparency

Označuje, zda aplikace podporuje průhledné bitmapy.

```
static BOOL IsTransparencySupported() throw();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud aktuální platforma podporuje průhlednost. Jinak 0.

### <a name="remarks"></a>Poznámky

Pokud je vrácená hodnota nenulová a je podporována průhlednost, volání [AlphaBlend](#alphablend), [TransparentBlt](#transparentblt)nebo [Draw](#draw) bude zpracovávat průhledné barvy.

## <a name="cimageload"></a><a name="load"></a>CImage::Načíst

Načte obraz.

```
HRESULT Load(LPCTSTR pszFileName) throw();
HRESULT Load(IStream* pStream) throw();
```

### <a name="parameters"></a>Parametry

*pszNázev_souboru*<br/>
Ukazatel na řetězec obsahující název souboru obrázku, který má být načíst.

*pStream*<br/>
Ukazatel na datový proud obsahující název obrazového souboru, který má být načíst.

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

### <a name="remarks"></a>Poznámky

Načte obrázek určený *pszFileName* nebo *pStream*.

Platné typy obrazů jsou BMP, GIF, JPEG, PNG a TIFF.

## <a name="cimageloadfromresource"></a><a name="loadfromresource"></a>CImage::LoadFromResource

Načte obraz z prostředku BITMAP.

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
Zpracovat na instanci modulu, který obsahuje bitovou kopii, která má být načtena.

*pszResourceName*<br/>
Ukazatel na řetězec obsahující název prostředku obsahujícího bitovou kopii, kterou chcete načíst.

*nIDZdroj*<br/>
ID prostředku k načtení.

### <a name="remarks"></a>Poznámky

Prostředek musí být typu BITMAP.

## <a name="cimagemaskblt"></a><a name="maskblt"></a>CImage::MaskBlt

Zkombinuje barevná data pro zdrojové a cílové bitmapy pomocí zadané masky a rastrové operace.

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
Souřadnice x v logických jednotkách levého horního rohu cílového obdélníku.

*yDest*<br/>
Souřadnice y v logických jednotkách levého horního rohu cílového obdélníku.

*nDestWidth*<br/>
Šířka cílového obdélníku a zdrojové bitmapy v logických jednotkách.

*nDestVýška*<br/>
Výška cílového obdélníku a zdrojové bitmapy v logických jednotkách.

*xSrc*<br/>
Logická souřadnice x levého horního rohu zdrojové bitmapy.

*ySrc řekl:*<br/>
Logická souřadnice y levého horního rohu zdrojové bitmapy.

*hbmMask*<br/>
Zpracovat monochromatický bitmapu masky v kombinaci s barevnou rastrem v kontextu zdrojového zařízení.

*xMask*<br/>
Vodorovný posun obrazových bodů pro bitmapu masky určenou parametrem *hbmMask.*

*yMask*<br/>
Svislé odsazení obrazových bodů pro bitmapu masky určenou parametrem *hbmMask.*

*dwROP*<br/>
Určuje kódy operací ternárního rastru na popředí i pozadí, které metoda používá k řízení kombinace zdrojových a cílových dat. Kód rastrové operace na pozadí je uložen v bajtu nejvyššího řádu slova vyššího řádu této hodnoty; kód rastrové operace na popředí je uložen v bajtu nižšího řádu slova vyššího řádu této hodnoty; slovo nízkého řádu této hodnoty je ignorováno a mělo by být nulové. Diskuse o popředí a pozadí v kontextu této metody `MaskBlt` naleznete v sadě Windows SDK. Seznam běžných kódů rastrových `BitBlt` operací naleznete v sadě Windows SDK.

*rectDest*<br/>
Odkaz na `RECT` strukturu, identifikaci cíle.

*bodSrc*<br/>
Struktura `POINT` označující levý horní roh zdrojového obdélníku.

*maska bodu*<br/>
Struktura `POINT` označující levý horní roh bitmapy masky.

*pointDest*<br/>
Odkaz na `POINT` strukturu, která identifikuje levý horní roh cílového obdélníku v logických jednotkách.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná, jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda platí pro systém Windows NT, pouze verze 4.0 a novější.

## <a name="cimageoperator-hbitmap"></a><a name="operator_hbitmap"></a>CImage::operátor HBITMAP

Pomocí tohoto operátoru získáte připojený popisovač GDI systému Windows objektu. `CImage` Tento operátor je operátor přetypování, který podporuje přímé použití objektu HBITMAP.

## <a name="cimageplgblt"></a><a name="plgblt"></a>CImage::PlgBlt

Provádí přenos bitového bloku z obdélníku v kontextu zdrojového zařízení do rovnoběžníku v kontextu cílového zařízení.

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

*pBody*<br/>
Ukazatel na pole tří bodů v logickém prostoru, které identifikují tři rohy cílového rovnoběžníku. Levý horní roh zdrojového obdélníku je mapován na první bod v tomto poli, do pravého horního rohu do druhého bodu v tomto poli a do levého dolního rohu do třetího bodu. Pravý dolní roh zdrojového obdélníku je mapován na implicitní čtvrtý bod v rovnoběžníku.

*hbmMask*<br/>
Úchyt pro volitelnou monochromatickou bitmapu, která slouží k maskování barev zdrojového obdélníku.

*xSrc*<br/>
Souřadnice x v logických jednotkách levého horního rohu zdrojového obdélníku.

*ySrc řekl:*<br/>
Souřadnice y v logických jednotkách levého horního rohu zdrojového obdélníku.

*nSrcWidth*<br/>
Šířka zdrojového obdélníku v logických jednotkách.

*nSrcVýška*<br/>
Výška zdrojového obdélníku v logických jednotkách.

*xMask*<br/>
Souřadnice x levého horního rohu monochromatické bitmapy.

*yMask*<br/>
Souřadnice y levého horního rohu monochromatické bitmapy.

*rectSrc*<br/>
Odkaz na [rect](/previous-versions/dd162897\(v=vs.85\)) strukturu určující souřadnice zdrojobdélníku.

*maska bodu*<br/>
Struktura [POINT](/previous-versions/dd162805\(v=vs.85\)) označující levý horní roh bitmapy masky.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná, jinak 0.

### <a name="remarks"></a>Poznámky

Pokud *hbmMask* identifikuje platný monochromatický rastrový obrázek, `PlgBit` použije tento rastrový obrázek k maskování bitů barevných dat ze zdrojového obdélníku.

Tato metoda platí pro systém Windows NT, pouze verze 4.0 a novější. Podrobnější informace naleznete v části [PlgBlt](/windows/win32/api/wingdi/nf-wingdi-plgblt) v kstě Sady Windows SDK.

## <a name="cimagereleasedc"></a><a name="releasedc"></a>CImage::ReleaseDC

Uvolní kontext zařízení.

```
void ReleaseDC() const throw();
```

### <a name="remarks"></a>Poznámky

Vzhledem k tomu, že do kontextu zařízení lze vybrat `ReleaseDC` pouze jednu bitmapu, musíte volat pro každé volání [getdc](#getdc).

## <a name="cimagereleasegdiplus"></a><a name="releasegdiplus"></a>cimage::ReleaseGDIPlus

Uvolní prostředky používané GDI+.

```
void ReleaseGDIPlus() throw();
```

### <a name="remarks"></a>Poznámky

Tato metoda musí být volána k `CImage` uvolnění prostředků přidělených globálním objektem. Viz [CImage::CImage](#cimage).

## <a name="cimagesave"></a><a name="save"></a>CImage::Uložit

Uloží bitovou kopii do zadaného datového proudu nebo souboru na disk.

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
Ukazatel na objekt COM IStream obsahující obrazová data souboru.

*pszNázev_souboru*<br/>
Ukazatel na název souboru pro obrázek.

*typ guidFileType*<br/>
Typ souboru, který chcete uložit obraz jako. Může to být jedna z následujících možností:

- `ImageFormatBMP`Nekomprimovaný bitmapový obraz.

- `ImageFormatPNG`Komprimovaný obraz přenosné síťové grafiky (PNG).

- `ImageFormatJPEG`Komprimovaný obraz JPEG.

- `ImageFormatGIF`Komprimovaný obraz GIF.

> [!NOTE]
> Úplný seznam konstant naleznete v tématu **Konstanty formátu souboru bitové kopie** v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

### <a name="remarks"></a>Poznámky

Voláním této funkce uložíte obrázek pomocí zadaného názvu a typu. Pokud není zahrnut parametr *guidFileType,* bude k určení formátu obrazu použita přípona názvu souboru. Pokud není k dispozici žádné rozšíření, obraz bude uložen ve formátu BMP.

## <a name="cimagesetcolortable"></a><a name="setcolortable"></a>CImage::SetColortable

Nastaví hodnoty barev červené, zelené, modré (RGB) pro rozsah položek v paletě oddílu DIB.

```
void SetColorTable(
    UINT iFirstColor,
    UINT nColors,
    const RGBQUAD* prgbColors) throw();
```

### <a name="parameters"></a>Parametry

*iFirstColor*<br/>
Index tabulky barev první položky, která má být nastavena.

*nBarvy*<br/>
Počet položek tabulky barev, které chcete nastavit.

*prgbBarvy*<br/>
Ukazatel na pole struktur [RGBQUAD](/windows/win32/api/wingdi/ns-wingdi-rgbquad) pro nastavení položek tabulky barev.

### <a name="remarks"></a>Poznámky

Tato metoda podporuje pouze bitmapy oddílu DIB.

## <a name="cimagesetpixel"></a><a name="setpixel"></a>CImage::SetPixel

Nastaví barvu obrazového bodu v daném umístění v bitmapě.

```
void SetPixel(int x, int y, COLORREF color) throw();
```

### <a name="parameters"></a>Parametry

*X*<br/>
Vodorovné umístění pixelu, který chcete nastavit.

*Y*<br/>
Svislé umístění pixelu, který chcete nastavit.

*color*<br/>
Barva, na kterou nastavíte pixel.

### <a name="remarks"></a>Poznámky

Tato metoda se nezdaří, pokud souřadnice obrazových bodů leží mimo vybranou oblast oříznutí.

## <a name="cimagesetpixelindexed"></a><a name="setpixelindexed"></a>CImage::SetPixelIndexed

Nastaví barvu obrazového bodu na barvu umístěnou v *iIndex* v paletě barev.

```
void SetPixelIndexed(int x, int y, int iIndex) throw();
```

### <a name="parameters"></a>Parametry

*X*<br/>
Vodorovné umístění pixelu, který chcete nastavit.

*Y*<br/>
Svislé umístění pixelu, který chcete nastavit.

*iIndex*<br/>
Index barvy v paletě barev.

## <a name="cimagesetpixelrgb"></a><a name="setpixelrgb"></a>CImage::SetPixelRGB

Nastaví obrazový bod v umístěních určených *x* a *y* na barvy označené *r*, *g*a *b*v červeném, zeleném, modrém (RGB) obraze.

```
void SetPixelRGB(
    int x,
    int y,
    BYTE r,
    BYTE g,
    BYTE b) throw();
```

### <a name="parameters"></a>Parametry

*X*<br/>
Vodorovné umístění pixelu, který chcete nastavit.

*Y*<br/>
Svislé umístění pixelu, který chcete nastavit.

*R*<br/>
Intenzita červené barvy.

*G*<br/>
Intenzita zelené barvy.

*B*<br/>
Intenzita modré barvy.

### <a name="remarks"></a>Poznámky

Červené, zelené a modré parametry jsou reprezentovány číslem mezi 0 a 255. Pokud nastavíte všechny tři parametry na nulu, kombinovaná výsledná barva bude černá. Pokud nastavíte všechny tři parametry na 255, kombinovaná výsledná barva je bílá.

## <a name="cimagesettransparentcolor"></a><a name="settransparentcolor"></a>CImage::SetTransparencyColor

Nastaví barvu v daném indexovaném umístění jako průhlednou.

```
LONG SetTransparentColor(LONG iTransparentColor) throw();
```

### <a name="parameters"></a>Parametry

*iTransparentColor*<br/>
Index barvy, která má být nastavena na průhlednou, v paletě barev. Pokud -1, žádná barva je nastavena na průhlednou.

### <a name="return-value"></a>Návratová hodnota

Index barvy dříve nastavenjako průhledný.

## <a name="cimagestretchblt"></a><a name="stretchblt"></a>CImage::StretchBlt

Zkopíruje bitmapu z kontextu zdrojového zařízení do tohoto aktuálního kontextu zařízení.

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
Souřadnice x v logických jednotkách levého horního rohu cílového obdélníku.

*yDest*<br/>
Souřadnice y v logických jednotkách levého horního rohu cílového obdélníku.

*nDestWidth*<br/>
Šířka cílového obdélníku v logických jednotkách.

*nDestVýška*<br/>
Výška cílového obdélníku v logických jednotkách.

*dwROP*<br/>
Rastrová operace, která má být provedena. Kódy rastrových operací přesně definují, jak kombinovat bity zdroje, cíl a vzorek (podle definice aktuálně vybrané stopy) a vytvořit tak cíl. Seznam dalších kódů rastrových operací a jejich popisy naleznete v části [BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) v kanisu Windows SDK.

*rectDest*<br/>
Odkaz na strukturu [RECT,](/previous-versions/dd162897\(v=vs.85\)) identifikace cíle.

*xSrc*<br/>
Souřadnice x v logických jednotkách levého horního rohu zdrojového obdélníku.

*ySrc řekl:*<br/>
Souřadnice y v logických jednotkách levého horního rohu zdrojového obdélníku.

*nSrcWidth*<br/>
Šířka zdrojového obdélníku v logických jednotkách.

*nSrcVýška*<br/>
Výška zdrojového obdélníku v logických jednotkách.

*rectSrc*<br/>
Odkaz na `RECT` strukturu, identifikace zdroje.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná, jinak 0.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [StretchBlt](/windows/win32/api/wingdi/nf-wingdi-stretchblt) v sadě Windows SDK.

## <a name="cimagetransparentblt"></a><a name="transparentblt"></a>CImage::TransparentBlt

Zkopíruje bitmapu z kontextu zdrojového zařízení do tohoto aktuálního kontextu zařízení.

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
Souřadnice x v logických jednotkách levého horního rohu cílového obdélníku.

*yDest*<br/>
Souřadnice y v logických jednotkách levého horního rohu cílového obdélníku.

*nDestWidth*<br/>
Šířka cílového obdélníku v logických jednotkách.

*nDestVýška*<br/>
Výška cílového obdélníku v logických jednotkách.

*crTransparentní*<br/>
Barva ve zdrojové bitmapě, která má být považována za průhlednou. Ve výchozím nastavení CLR_INVALID, což znamená, že by měla být použita barva aktuálně nastavená jako průhledná barva obrazu.

*rectDest*<br/>
Odkaz na strukturu [RECT,](/previous-versions/dd162897\(v=vs.85\)) identifikace cíle.

*xSrc*<br/>
Souřadnice x v logických jednotkách levého horního rohu zdrojového obdélníku.

*ySrc řekl:*<br/>
Souřadnice y v logických jednotkách levého horního rohu zdrojového obdélníku.

*nSrcWidth*<br/>
Šířka zdrojového obdélníku v logických jednotkách.

*nSrcVýška*<br/>
Výška zdrojového obdélníku v logických jednotkách.

*rectSrc*<br/>
Odkaz na `RECT` strukturu, identifikace zdroje.

### <a name="return-value"></a>Návratová hodnota

PRAVDA v případě úspěchu, jinak FALSE.

### <a name="remarks"></a>Poznámky

`TransparentBlt`je podporován pro zdrojové bitmapy 4 bitů na pixel a 8 bitů na pixel. Pomocí [CImage::AlphaBlend](#alphablend) určete 32 bitmap bitů na pixel s průhledností.

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

## <a name="see-also"></a>Viz také

[Ukázka MMXSwarm](../../overview/visual-cpp-samples.md)<br/>
[Ukázka simpleimage](../../overview/visual-cpp-samples.md)<br/>
[Bitmapy nezávislé na zařízení](/windows/win32/gdi/device-independent-bitmaps)<br/>
[CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibsection)<br/>
[Desktopové komponenty ATL objektů COM](../../atl/atl-com-desktop-components.md)<br/>
[Bitmapy nezávislé na zařízení](/windows/win32/gdi/device-independent-bitmaps)<br/>
[CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibsection)
