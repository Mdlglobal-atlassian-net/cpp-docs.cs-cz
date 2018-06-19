---
title: CImage – třída | Microsoft Docs
ms.custom: ''
ms.date: 02/01/2018
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 762941834820edda09970750af752d4c8a9df61c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366312"
---
# <a name="cimage-class"></a>CImage – třída
`CImage` Poskytuje podporu rozšířené rastrového obrázku, včetně možnosti spouštění a ukládání bitových kopií ve formátech JPEG, GIF, BMP a Portable Network Graphics (PNG).  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CImage
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CImage::CImage](#cimage)|Konstruktor|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CImage::AlphaBlend](#alphablend)|Zobrazí rastrové obrázky, které mají průhledných nebo poloprůhledných pixelů.|  
|[CImage::Attach](#attach)|Připojí `HBITMAP` k `CImage` objektu. Lze použít s bez DIB části Bitmap nebo DIB části bitmapy.|  
|[CImage::BitBlt](#bitblt)|Kopíruje rastrový obrázek z kontextu zařízení zdroj pro tuto aktuální kontext zařízení.|  
|[CImage::Create](#create)|Rastrový obrázek části DIB vytvoří a připojí se k dříve vytvořený `CImage` objektu.|  
|[CImage::CreateEx](#createex)|Vytvoří rastru části DIB (pomocí dalších parametrů) a připojí se k dříve vytvořený `CImage` objektu.|  
|[CImage::Destroy](#destroy)|Umožňuje odpojit bitovou mapu z `CImage` objektu a zničí bitové mapy.|  
|[CImage::Detach](#detach)|Umožňuje odpojit bitovou mapu z `CImage` objektu.|  
|[CImage::Draw](#draw)|Zkopíruje rastrový obrázek ze zdrojového obdélníku do obdélníku cílový. **Kreslení** roztahovány nebo komprimaci rastrového obrázku v případě potřeby přizpůsobit dimenze rámeček cílové a zpracovává alfa míchání a transparentní barev.|  
|[CImage::GetBits](#getbits)|Načte ukazatel na pixel skutečné hodnoty bitové mapy.|  
|[CImage::GetBPP](#getbpp)|Načte bitů na pixel.|  
|[CImage::GetColorTable](#getcolortable)|Načte red, zelená, blue – hodnoty barev (RGB) z rozsahu položek v tabulce barev.|  
|[CImage::GetDC](#getdc)|Načte kontext zařízení, do kterého je vybrána aktuální rastrového obrázku.|  
|[CImage::GetExporterFilterString](#getexporterfilterstring)|Vyhledá formáty k dispozici bitovou kopii a jejich popisy.|  
|[CImage::GetHeight](#getheight)|Načte výšku aktuální obrázku v pixelech.|  
|[CImage::GetImporterFilterString](#getimporterfilterstring)|Vyhledá formáty k dispozici bitovou kopii a jejich popisy.|  
|[CImage::GetMaxColorTableEntries](#getmaxcolortableentries)|Načte maximální počet položek v tabulce barev.|  
|[CImage::GetPitch](#getpitch)|Načte výška aktuální image v bajtech.|  
|[CImage::GetPixel](#getpixel)|Načte barva pixelů určeného *x* a *y*.|  
|[CImage::GetPixelAddress](#getpixeladdress)|Načte adresu daného pixelů.|  
|[CImage::GetTransparentColor](#gettransparentcolor)|Načte pozici průhlednou barvu v tabulce barev.|  
|[CImage::GetWidth](#getwidth)|Načte šířku aktuální obrázku v pixelech.|  
|[CImage::IsDIBSection](#isdibsection)|Určuje, zda připojené rastrový obrázek DIB oddíl.|  
|[CImage::IsIndexed](#isindexed)|Označuje, že barvy rastrového obrázku jsou namapované na indexované palety.|  
|[CImage::IsNull](#isnull)|Označuje, pokud je momentálně načtených rastrový obrázek zdroje.|  
|[CImage::IsTransparencySupported](#istransparencysupported)|Určuje, jestli aplikace podporuje transparentní bitmapy.|  
|[CImage::Load](#load)|Načte obrázek ze zadaného souboru.|  
|[CImage::LoadFromResource](#loadfromresource)|Načte obrázek ze zadaného prostředku.|  
|[CImage::MaskBlt](#maskblt)|Kombinuje data barvu pro zdrojové a cílové rastrové obrázky, pomocí zadané maska a rastrové operace.|  
|[CImage::PlgBlt](#plgblt)|Provede přenos bitového bloku z obdélníku v kontextu zařízení zdroje do rovnoběžník v kontextu cílové zařízení.|  
|[CImage::ReleaseDC](#releasedc)|Uvolní kontextu zařízení, která byla načtena s [CImage::GetDC](#getdc).|  
|[CImage::ReleaseGDIPlus](#releasegdiplus)|Uvolní prostředky využívané třídou GDI +. Musí být volána kvůli uvolnění prostředků vytvořené globální `CImage` objektu.|  
|[CImage::Save](#save)|Uloží obrázek jako zadaného typu. **Uložit** nelze určit možnosti bitové kopie.|  
|[CImage::SetColorTable](#setcolortable)|Nastaví RGB red, zelené, modré) barvu hodnoty v rozsahu položek v tabulce barev DIB oddílu.|  
|[CImage::SetPixel](#setpixel)|Nastaví pixel v zadaných souřadnic k barvě pro zadaný.|  
|[CImage::SetPixelIndexed](#setpixelindexed)|V zadané souřadnice na barvu v zadaném indexu palety nastaví pixel.|  
|[CImage::SetPixelRGB](#setpixelrgb)|Nastaví pixelů na zadaný souřadnice hodnotě zadané red zelená, modrá (RGB).|  
|[CImage::SetTransparentColor](#settransparentcolor)|Nastaví index barvy, která má být považován za průhlednou. Pouze jednu barvu na paletě může být průhledná.|  
|[CImage::StretchBlt](#stretchblt)|Zkopíruje rastrový obrázek ze obdélníku zdrojového do cílového obdélníku, roztažení nebo kompresi rastrový obrázek podle dimenze cílové obdélníku, v případě potřeby.|  
|[CImage::TransparentBlt](#transparentblt)|Kopíruje bitmap s průhledná barva z kontextu zařízení zdroj pro tuto aktuální kontext zařízení.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CImage::operator HBITMAP](#operator_hbitmap)|Vrátí popisovač Windows připojené k `CImage` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `CImage` přebírá rastrové obrázky, které jsou buď části device independent bitmap (DIB) nebo ne; Můžete však použít [vytvořit](#create) nebo [CImage::Load](#load) s jenom DIB oddíly. Bez DIB bitmapa část, aby se můžete připojit `CImage` pomocí [připojit](#attach), ale nemůžete použít následující `CImage` metody, které podporují pouze rastrové obrázky DIB části:  
  
- [GetBits](#getbits)  
  
- [GetColorTable](#getcolortable)  
  
- [GetMaxColorTableEntries](#getmaxcolortableentries)  
  
- [GetPitch](#getpitch)  
  
- [GetPixelAddress](#getpixeladdress)  
  
- [IsIndexed](#isindexed)  
  
- [SetColorTable](#setcolortable)  
  
 Chcete-li zjistit, jestli je připojené rastrový obrázek části DIB, volejte [IsDibSection](#isdibsection)**.**  
  
> [!NOTE]
> **Poznámka:** ve Visual Studio .NET 2003, tato třída sleduje počet počet `CImage` objekty vytvořené. Vždy, když počet přejde na hodnotu 0, funkce **GdiplusShutdown** je automaticky volána k uvolnění prostředků používané GDI +. To zajistí, že všechny `CImage` objekty vytvořené knihovny DLL přímo nebo nepřímo jsou vždy zničen správně a že **GdiplusShutdown** není volat z `DllMain`.  
  
> [!NOTE]
>  Pomocí globální `CImage` objektů v knihovně DLL se nedoporučuje. Pokud budete muset použít globální konfiguraci `CImage` objektu v knihovně DLL, volání [CImage::ReleaseGDIPlus](#releasegdiplus) explicitně uvolnit prostředky využívané třídou GDI +.  
  
 `CImage` Nelze vybrat, do nového [CDC](../../mfc/reference/cdc-class.md). `CImage` Vytvoří vlastní **HDC** pro bitovou kopii. Protože `HBITMAP` lze vybrat pouze do jedné **HDC** současně, `HBITMAP` přidružené `CImage` nelze vybrat do jiné **HDC**. Pokud potřebujete `CDC`, načíst **HDC** z `CImage` a pojmenujte ho [CDC::FromHandle] (.. /.. /MFC/reference/CDC-Class.MD#cdc__fromhandle.  
  
## <a name="example"></a>Příklad  
```cpp  
// Get a CDC for the image
CDC* pDC = CDC::FromHandle(m_myImage.GetDC());

// Use pDC here
pDC->Rectangle(0, 40, 100, 50);
m_myImage.ReleaseDC();
```  
  
 Při použití `CImage` v projektu knihovny MFC Všimněte si, které členské funkce ve vašem projektu očekávat ukazatel [CBitmap](../../mfc/reference/cbitmap-class.md) objektu. Pokud chcete použít `CImage` pomocí funkce, jako [CMenu::AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu), použijte [CBitmap::FromHandle](../../mfc/reference/cbitmap-class.md#fromhandle), předejte ji vaše `CImage` `HBITMAP`a použijte vrácený `CBitmap*`.  

  
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

  
 Prostřednictvím `CImage`, máte přístup k skutečné bits DIB oddílu. Můžete použít `CImage` objektu kdekoli použil Win32 HBITMAP nebo DIB části.  
  
 Můžete použít `CImage` z MFC nebo ATL.  
  
> [!NOTE]
>  Když vytvoříte projekt pomocí `CImage`, je nutné definovat `CString` předtím, než zahrnete `atlimage.h`. Pokud váš projekt používá ATL bez MFC, zahrnují `atlstr.h` předtím, než zahrnete `atlimage.h`. Pokud váš projekt používá MFC (nebo pokud je projektu knihovny ATL s MFC podpory), zahrnují `afxstr.h` předtím, než zahrnete `atlimage.h`.  
>   
>  Podobně platí, musíte zahrnout `atlimage.h` předtím, než zahrnete `atlimpl.cpp`. K tomu snadno zahrnout `atlimage.h` ve vaší `stdafx.h`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlimage.h  
  
##  <a name="alphablend"></a>  CImage::AlphaBlend  
 Zobrazí rastrové obrázky, které mají průhledných nebo poloprůhledných pixelů.  
  
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
 `hDestDC`  
 Popisovač kontextu cílové zařízení.  
  
 `xDest`  
 Souřadnice x, v logických jednotek, levého horního rohu obdélníku cílový.  
  
 `yDest`  
 Souřadnice y, v logických jednotek, levého horního rohu obdélníku cílový.  
  
 *bSrcAlpha*  
 Hodnotu alfa průhlednost pro celý zdrojový rastrový obrázek používat. Výchozí 0xff (255) se předpokládá, že obraz je plné krytí a chcete použít na pixel pouze alfanumerické hodnoty.  
  
 `bBlendOp`  
 Prolnutí alfa funkce pro zdrojové a cílové bitmap, globální alfa hodnota má být použita pro celý zdrojový rastrového obrázku a informace o formátu pro bitovou mapu zdroje. Funkce blend zdrojové a cílové je aktuálně omezená na **AC_SRC_OVER**.  
  
 `pointDest`  
 Odkaz na [bodu](http://msdn.microsoft.com/library/windows/desktop/dd162805) struktura, která identifikuje levém horním rohu obdélníku cílové, v logické jednotky.  
  
 `nDestWidth`  
 Šířka v logických jednotek, cílový rámečku.  
  
 `nDestHeight`  
 Výška v logických jednotek, cílový rámečku.  
  
 `xSrc`  
 Logické souřadnici x levého horního rohu obdélníku zdroje.  
  
 `ySrc`  
 Logické souřadnici y levého horního rohu obdélníku zdroje.  
  
 `nSrcWidth`  
 Šířka v logických jednotek, obdélníku zdroje.  
  
 `nSrcHeight`  
 Výška v logických jednotek, obdélníku zdroje.  
  
 `rectDest`  
 Odkaz na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura, identifikace cíl.  
  
 `rectSrc`  
 Odkaz na `RECT` struktura, identifikace zdroji.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Prolnutí alfa bitmap podporovat barva prolnutí na základě za pixelů.  
  
 Když `bBlendOp` je nastaven na výchozí **AC_SRC_OVER**, přes cílové rastrový obrázek, na základě alfa hodnot pixelů zdroje je umístěn zdroj bitové mapy.  

##  <a name="attach"></a>  CImage::Attach  
 Připojí `hBitmap` k `CImage` objektu.  
  
```
void Attach(HBITMAP hBitmap, DIBOrientation eOrientation = DIBOR_DEFAULT) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `hBitmap`  
 Popisovač pro `HBITMAP`.  
  
 *eOrientation*  
 Určuje orientaci bitové mapy. Může být jedna z následujících akcí:  
  
- **DIBOR_DEFAULT** orientaci bitmapy je určen podle operačního systému. Ale to nemusí mít vždy požadovaných výsledků na všech operačních systémech. Další informace o to, najdete v následujícím článku znalostní báze Knowledge Base ( **Q186586**): PRB: GetObject() vždy vrátí kladné výšku pro DIB oddíly.  
  
- **DIBOR_BOTTOMUP** řádky bitmapy jsou v obráceném pořadí. To způsobí, že [CImage::GetBits](#getbits) vrátit ukazatel u konce vyrovnávací paměti rastrového obrázku a [CImage::GetPitch](#getpitch) vrátit na záporné číslo.  
  
- **DIBOR_TOPDOWN** řádky bitmapy jsou v nejvyšší pořadí dole. To způsobí, že [CImage::GetBits](#getbits) vrátit ukazatel do prvního bajtu rastrový obrázek vyrovnávací paměti a [CImage::GetPitch](#getpitch) vrátit kladné číslo.  
  
### <a name="remarks"></a>Poznámky  
 Bitmapy může být rastrový obrázek části bez DIB nebo rastrový obrázek DIB části. V tématu [IsDIBSection](#isdibsection) seznam metod, které lze použít pouze s DIB části rastrové obrázky.  
  
##  <a name="bitblt"></a>  CImage::BitBlt  
 Kopíruje rastrový obrázek z kontextu zařízení zdroj pro tuto aktuální kontext zařízení.  
  
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
 `hDestDC`  
 Cíl **HDC**.  
  
 `xDest`  
 Logické souřadnici x levého horního rohu obdélníku cílový.  
  
 `yDest`  
 Logické souřadnici y levého horního rohu obdélníku cílový.  
  
 `dwROP`  
 Rastrové operaci provést. Rastrové operace kódy definovat přesně jak kombinovat bits zdroj, cíl a vzoru (podle definice v aktuálně vybraném štětce) a vytvořit cíl. V tématu [přenos bitových bloků](http://msdn.microsoft.com/library/windows/desktop/dd183370) ve Windows SDK pro seznam ostatní kódy rastrové operace a jejich popisy.  
  
 `pointDest`  
 A [bodu](http://msdn.microsoft.com/library/windows/desktop/dd162805) struktura označující levém horním rohu obdélníku cílový.  
  
 `nDestWidth`  
 Šířka v logických jednotek, cílový rámečku.  
  
 `nDestHeight`  
 Výška v logických jednotek, cílový rámečku.  
  
 `xSrc`  
 Logické souřadnici x levého horního rohu obdélníku zdroje.  
  
 `ySrc`  
 Logické souřadnici y levého horního rohu obdélníku zdroje.  
  
 `rectDest`  
 A [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura označující rámeček cílový.  
  
 `pointSrc`  
 A **bodu** struktura označující levém horním rohu obdélníku zdroje.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [přenos bitových bloků](http://msdn.microsoft.com/library/windows/desktop/dd183370) ve Windows SDK.  
  
##  <a name="cimage"></a>  CImage::CImage  
 Vytvoří `CImage` objektu.  
  
```
CImage() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Jakmile budete mít sestavený objekt, volání [vytvořit](#create), [zatížení](#load), [LoadFromResource –](#loadfromresource), nebo [Attach](#attach) rastrový obrázek připojit k objektu.  
  
 **Poznámka:** v sadě Visual Studio, tato třída sleduje počet počet `CImage` objekty vytvořené. Vždy, když počet přejde na hodnotu 0, funkce **GdiplusShutdown** je automaticky volána k uvolnění prostředků používané GDI +. To zajistí, že všechny `CImage` objekty vytvořené knihovny DLL přímo nebo nepřímo jsou vždy zničen správně a že **GdiplusShutdown** není volat z DllMain.  
  
 Pomocí globální `CImage` objektů v knihovně DLL se nedoporučuje. Pokud budete muset použít globální konfiguraci `CImage` objektu v knihovně DLL, volání [CImage::ReleaseGDIPlus](#releasegdiplus) explicitně uvolnit prostředky využívané třídou GDI +.  
  
##  <a name="create"></a>  CImage::Create  
 Vytvoří `CImage` bitmap a připojte ji k dříve vytvořený `CImage` objektu.  
  
```
BOOL Create(
 int nWidth,
 int nHeight,
 int nBPP,
 DWORD dwFlags = 0) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nWidth`  
 Šířka `CImage` rastrového obrázku v pixelech.  
  
 `nHeight`  
 Výška `CImage` rastrového obrázku v pixelech. Pokud `nHeight` kladné, bitmapy DIB zdola nahoru a původu je levého dolního rohu. Pokud `nHeight` záporná, je bitmapy DIB shora dolů a původu je levém horním rohu.  
  
 `nBPP`  
 Počet bitů na pixel v souboru bitové mapy. Obvykle 4, 8, 16, 24 nebo 32. Může být 1 pro černobílý Bitmap nebo masky.  
  
 `dwFlags`  
 Určuje, zda má objekt rastrový obrázek alfa kanálu. Může být kombinací nula nebo více z následujících hodnot:  
  
- **createAlphaChannel** lze použít pouze v případě `nBPP` je 32, a `eCompression` je **BI_RGB**. -Li zadána, vytvořené bitové kopie má hodnotu alfa (průhlednost) pro každý pixelů, uložené v 4. bajt každý pixelů (nepoužívané v bitové kopii jiné než alfanumerické 32bitová verze). Tento alfa kanálu je automaticky se používá při volání metody [CImage::AlphaBlend](#alphablend).  
  
> [!NOTE]
>  Ve volání [CImage::Draw](#draw), bitové kopie s kanálem alfa jsou automaticky alfa smíšení do cílového umístění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
##  <a name="createex"></a>  CImage::CreateEx  
 Vytvoří `CImage` bitmap a připojte ji k dříve vytvořený `CImage` objektu.  
  
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
 `nWidth`  
 Šířka `CImage` rastrového obrázku v pixelech.  
  
 `nHeight`  
 Výška `CImage` rastrového obrázku v pixelech. Pokud `nHeight` kladné, bitmapy DIB zdola nahoru a původu je levého dolního rohu. Pokud `nHeight` záporná, je bitmapy DIB shora dolů a původu je levém horním rohu.  
  
 `nBPP`  
 Počet bitů na pixel v souboru bitové mapy. Obvykle 4, 8, 16, 24 nebo 32. Může být 1 pro černobílý Bitmap nebo masky.  
  
 `eCompression`  
 Určuje typ komprese komprimované bitové mapy zdola nahoru (nejde zkomprimovat obrázky DIB shora dolů). Může být jedna z následujících hodnot:  
  
- **BI_RGB** formát nekomprimované. Zadání hodnoty při volání metody `CImage::CreateEx` je ekvivalentní volání `CImage::Create`.  
  
- **BI_BITFIELDS** formát nekomprimované a tabulce barev se skládá ze tří `DWORD` masky barev, které zadejte red, zelená a modrá součásti, z každé pixelů. Toto je platný při použití s bitovými mapami bpp 16 a 32.  
  
 *pdwBitfields*  
 Použít jen v případě `eCompression` je nastaven na **BI_BITFIELDS**, v opačném případě musí být **NULL**. Ukazatel na tři pole `DWORD` bitové masky, určení, které bitů každý pixelů se používá pro červená, zelená a modrá součástí barvu, v uvedeném pořadí. Informace o omezení pro bitová pole, v tématu [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376) ve Windows SDK.  
  
 `dwFlags`  
 Určuje, zda má objekt rastrový obrázek alfa kanálu. Může být kombinací nula nebo více z následujících hodnot:  
  
- **createAlphaChannel** lze použít pouze v případě `nBPP` je 32, a `eCompression` je **BI_RGB**. -Li zadána, vytvořené bitové kopie má hodnotu alfa (průhlednost) pro každý pixelů, uložené v 4. bajt každý pixelů (nepoužívané v bitové kopii jiné než alfanumerické 32bitová verze). Tento alfa kanálu je automaticky se používá při volání metody [CImage::AlphaBlend](#alphablend).  
  
    > [!NOTE]
    >  Ve volání [CImage::Draw](#draw), bitové kopie s kanálem alfa jsou automaticky alfa smíšení do cílového umístění.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** v případě úspěchu. V opačném případě **FALSE**.  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří pomocí 16 bitů ke kódování jednotlivých pixelů rastrový obrázek 100 x 100 pixelů. V dané 16bitové pixelů bits 0 až 3 kódování komponentu red, služba bits 4-7 zakódovat zelená a bits 8 11 kódování blue. Zbývající 4 bits se nepoužívá.  

```cpp  
DWORD adwBitmasks[3] = { 0x0000000f, 0x000000f0, 0x00000f00 };
m_myImage.CreateEx(100, 100, 16, BI_BITFIELDS, adwBitmasks, 0);
```


##  <a name="destroy"></a>  CImage::Destroy  
 Umožňuje odpojit bitovou mapu z `CImage` objektu a zničí bitové mapy.  
  
```
void Destroy() throw();
```  
  
##  <a name="detach"></a>  CImage::Detach  
 Umožňuje odpojit rastrového obrázku z `CImage` objektu.  
  
```
HBITMAP Detach() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro bitovou mapu odpojit, nebo **NULL** Pokud je připojen žádný rastrového obrázku.  
  
##  <a name="draw"></a>  CImage::Draw  
 Kopíruje rastrový obrázek z kontextu zařízení zdroj pro aktuální kontext zařízení.  
  
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
 `hDestDC`  
 Popisovač pro kontext cílové zařízení.  
  
 `xDest`  
 Souřadnice x, v logických jednotek, levého horního rohu obdélníku cílový.  
  
 `yDest`  
 Souřadnice y, v logických jednotek, levého horního rohu obdélníku cílový.  
  
 `nDestWidth`  
 Šířka v logických jednotek, cílový rámečku.  
  
 `nDestHeight`  
 Výška v logických jednotek, cílový rámečku.  
  
 `xSrc`  
 Souřadnice x, v logických jednotek, levého horního rohu obdélníku zdroje.  
  
 `ySrc`  
 Souřadnice y, v logických jednotek, levého horního rohu obdélníku zdroje.  
  
 `nSrcWidth`  
 Šířka v logických jednotek, obdélníku zdroje.  
  
 `nSrcHeight`  
 Výška v logických jednotek, obdélníku zdroje.  
  
 `rectDest`  
 Odkaz na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura, identifikace cíl.  
  
 `rectSrc`  
 Odkaz na `RECT` struktura, identifikace zdroji.  
  
 `pointDest`  
 Odkaz na [bodu](http://msdn.microsoft.com/library/windows/desktop/dd162805) struktura, která identifikuje levém horním rohu obdélníku cílové, v logické jednotky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 **Kreslení** provádí stejné operace jako [StretchBlt](#stretchblt), pokud bitová kopie obsahuje průhlednou barvu nebo alfa kanálu. V takovém případě **kreslení** provádí stejné operace jako [TransparentBlt](#transparentblt) nebo [AlphaBlend](#alphablend) podle potřeby.  
  
 Verze **kreslení** nezadávejte obdélníku zdroje, celý zdrojový je výchozí. Pro verzi **kreslení** neurčuje velikost cílového obdélníku, velikost zdrojové bitové kopie je výchozí a žádné roztažení nebo zmenšení dojde.  
  
##  <a name="getbits"></a>  CImage::GetBits  
 Načte ukazatel bit skutečné hodnoty dané pixelů v rastrový obrázek.  
  
```
void* GetBits() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel do vyrovnávací paměti rastrového obrázku. Pokud bitmapy DIB zdola nahoru, body ukazatel téměř na konci vyrovnávací paměti. Pokud bitmapy DIB shora dolů, ukazatele bodů do prvního bajtu vyrovnávací paměti.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí tento ukazatel, společně s hodnoty vrácené [GetPitch](#getpitch), můžete vyhledat a změnit jednotlivých pixelů bitovou kopii.  
  
> [!NOTE]
>  Tato metoda podporuje pouze DIB části bitmap; v důsledku toho přístup pixelů z `CImage` objekt stejným způsobem, jako by pixelů DIB oddílu. Vrácený ukazatel odkazuje na pixel v umístění (0, 0).  
  
##  <a name="getbpp"></a>  CImage::GetBPP  
 Načte hodnotu bitů na pixel.  
  
```
int GetBPP() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet bitů na pixel.  
  
### <a name="remarks"></a>Poznámky  
 Tato hodnota určuje počet bitů, které definují každý pixelů a maximální počet barev v souboru bitové mapy.  
  
 Bitů na pixel je obvykle 1, 4, 8, 16, 24 nebo 32. Najdete v článku **biBitCount** členem [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376) ve Windows SDK pro další informace o této hodnotě.  
  
##  <a name="getcolortable"></a>  CImage::GetColorTable  
 Načte red, zelená, blue – hodnoty barev (RGB) z rozsahu položek v palety DIB oddílu.  
  
```
void GetColorTable(UINT iFirstColor,
 UINT nColors,
 RGBQUAD* prgbColors) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `iFirstColor`  
 Index tabulky barev první položky určené k načtení.  
  
 `nColors`  
 Počet položek barev tabulce k načtení.  
  
 `prgbColors`  
 Ukazatel na pole [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938) struktury načíst barvu tabulky položky.  
  
##  <a name="getdc"></a>  CImage::GetDC  
 Načte kontext zařízení, který má aktuálně bitovou kopii vybrané do ní.  
  
```
HDC GetDC() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro kontext zařízení.  
  
### <a name="remarks"></a>Poznámky  
 Pro každé volání `GetDC`, musíte mít následující volání [ReleaseDC](#releasedc).  
  
##  <a name="getexporterfilterstring"></a>  CImage::GetExporterFilterString  
 Vyhledá formáty bitové kopie k dispozici pro uložení bitové kopie.  
  
```
static HRESULT GetExporterFilterString(CSimpleString& strExporters,
 CSimpleArray<GUID>& aguidFileTypes,
 LPCTSTR pszAllFilesDescription = NULL,
 DWORD dwExclude = excludeDefaultSave,
 TCHAR chSeparator = _T('|'));
```  
  
### <a name="parameters"></a>Parametry  
 *strExporters*  
 Odkaz na **CSimpleString** objektu. V tématu **poznámky** Další informace.  
  
 `aguidFileTypes`  
 Pole identifikátory GUID, s každý prvek odpovídající jeden z typů souborů v řetězci. V příkladu v `pszAllFilesDescription` níže, `aguidFileTypes`[0] je `GUID_NULL` a zbývající hodnoty pole jsou formátů souboru obrázku, který se nepodporuje v aktuálním operačním systému.  
  
> [!NOTE]
>  Úplný seznam konstanty, najdete v části **konstanty formát souboru obrázku** ve Windows SDK.  
  
 `pszAllFilesDescription`  
 Pokud není tento parametr **NULL**, řetězec filtru bude mít jeden další filtr na začátku seznamu. Aktuální hodnota bude mít tento filtr `pszAllFilesDescription` jeho popis a přijímá soubory všechna rozšíření nepodporuje žádné jiné exportu v seznamu.  
  
 Příklad:  

```cpp  
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any exporter.
CImage::GetExporterFilterString(
    strExporters, aguidFileTypes, 
 _T("All Image Files"));
```  

  
 `dwExclude`  
 Sada bitové příznaky určující, které typy souborů vyloučit ze seznamu. Povolená příznaky jsou:  
  
- **excludeGIF** = 0x01 vyloučí GIF – soubory.  
  
- **excludeBMP** = 0x02 soubory vyloučí BMP (rastrového obrázku).  
  
- **excludeEMF** = 0x04 vyloučí EMF (Enhanced Metafile) soubory.  
  
- **excludeWMF** = 0x08 vyloučí WMF (WMF) soubory.  
  
- **excludeJPEG** = 0x10 vyloučí JPEG – soubory.  
  
- **excludePNG** = 0x20 soubory vyloučí PNG.  
  
- **excludeTIFF** = 0x40 vyloučí TIFF soubory.  
  
- **excludeIcon** = 0x80 soubory vyloučí ICO (ikona Windows).  
  
- **excludeOther** = 0x80000000 vyloučí jiný typ souboru nejsou uvedené výše.  
  
- **excludeDefaultLoad** = 0, pro zatížení, všechny souboru typy jsou zahrnuté ve výchozím nastavení  
  
- **excludeDefaultSave** = **excludeIcon &#124; excludeEMF &#124; excludeWMF** pro ukládání, tyto soubory jsou vyloučeny ve výchozím nastavení protože obvykle mají zvláštní požadavky.  
  
 `chSeparator`  
 Oddělovač použitý mezi formáty bitové kopie. V tématu **poznámky** Další informace.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
### <a name="remarks"></a>Poznámky  
 Výsledný řetězec formátu můžete předat vaší MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md) formáty objekt, který chcete vystavit přípony souborů bitové kopie k dispozici v dialogovém okně Uložit jako.  
  
 Parametr *strExporter* má formát:  
  
 soubor description0&#124;\*.ext0&#124;filedescription1&#124;\*.ext1&#124;.. .file popis *n*&#124;\*.ext *n*&#124;&#124;  
  
 kde se&#124;' je oddělovací znak zadána `chSeparator`. Příklad:  
  
 `"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`  
  
 Použít výchozí oddělovač '&#124;' Pokud tento řetězec předáte do knihovny MFC `CFileDialog` objektu. Pokud předáte tento řetězec do běžné uložit soubor dialogového okna, použijte hodnotu null oddělovač '\0'.  
  
##  <a name="getheight"></a>  CImage::GetHeight  
 Načte výška v pixelech, bitové kopie.  
  
```
int GetHeight() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výška v pixelech, bitové kopie.  
  
##  <a name="getimporterfilterstring"></a>  CImage::GetImporterFilterString  
 Vyhledá formáty bitové kopie k dispozici pro načítání obrázků.  
  
```
static HRESULT GetImporterFilterString(CSimpleString& strImporters,
 CSimpleArray<GUID>& aguidFileTypes,
 LPCTSTR pszAllFilesDescription = NULL,
 DWORD dwExclude = excludeDefaultLoad,
 TCHAR chSeparator = _T('|'));
```  
  
### <a name="parameters"></a>Parametry  
 *strImporters*  
 Odkaz na **CSimpleString** objektu. V tématu **poznámky** Další informace.  
  
 `aguidFileTypes`  
 Pole identifikátory GUID, s každý prvek odpovídající jeden z typů souborů v řetězci. V příkladu v `pszAllFilesDescription` níže, `aguidFileTypes`[0] je `GUID_NULL` s poli Zbývající hodnoty jsou formátů souboru obrázku, který se nepodporuje v aktuálním operačním systému.  
  
> [!NOTE]
>  Úplný seznam konstanty, najdete v části **konstanty formát souboru obrázku** ve Windows SDK.  
  
 `pszAllFilesDescription`  
 Pokud není tento parametr **NULL**, řetězec filtru bude mít jeden další filtr na začátku seznamu. Aktuální hodnota bude mít tento filtr `pszAllFilesDescription` jeho popis a přijímá soubory všechna rozšíření nepodporuje žádné jiné exportu v seznamu.  
  
 Příklad:  

```cpp  
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any importer.
CImage::GetImporterFilterString(
    strImporters, aguidFileTypes, 
 _T("All Image Files"));
```  

  
 `dwExclude`  
 Sada bitové příznaky určující, které typy souborů vyloučit ze seznamu. Povolená příznaky jsou:  
  
- **excludeGIF** = 0x01 vyloučí GIF – soubory.  
  
- **excludeBMP** = 0x02 soubory vyloučí BMP (rastrového obrázku).  
  
- **excludeEMF** = 0x04 vyloučí EMF (Enhanced Metafile) soubory.  
  
- **excludeWMF** = 0x08 vyloučí WMF (WMF) soubory.  
  
- **excludeJPEG** = 0x10 vyloučí JPEG – soubory.  
  
- **excludePNG** = 0x20 soubory vyloučí PNG.  
  
- **excludeTIFF** = 0x40 vyloučí TIFF soubory.  
  
- **excludeIcon** = 0x80 soubory vyloučí ICO (ikona Windows).  
  
- **excludeOther** = 0x80000000 vyloučí jiný typ souboru nejsou uvedené výše.  
  
- **excludeDefaultLoad** = 0, pro zatížení, všechny souboru typy jsou zahrnuté ve výchozím nastavení  
  
- **excludeDefaultSave** = **excludeIcon &#124; excludeEMF &#124; excludeWMF** pro ukládání, tyto soubory jsou vyloučeny ve výchozím nastavení protože obvykle mají zvláštní požadavky.  
  
 `chSeparator`  
 Oddělovač použitý mezi formáty bitové kopie. V tématu **poznámky** Další informace.  
  
### <a name="remarks"></a>Poznámky  
 Výsledný řetězec formátu můžete předat vaší MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md) formáty objekt, který chcete vystavit přípony souborů bitové kopie k dispozici v **otevřít soubor** dialogové okno.  
  
 Parametr *strImporter* má formát:  
  
 soubor description0&#124;\*.ext0&#124;filedescription1&#124;\*.ext1&#124;.. .file popis *n*&#124;\*.ext *n*&#124;&#124;  
  
 kde se&#124;' je oddělovací znak zadána `chSeparator`. Příklad:  
  
 `"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`  
  
 Použít výchozí oddělovač '&#124;' Pokud tento řetězec předáte do knihovny MFC `CFileDialog` objektu. Použijte null oddělovač '\0', pokud je tento řetězec předat do společného **otevřít soubor** dialogové okno.  
  
##  <a name="getmaxcolortableentries"></a>  CImage::GetMaxColorTableEntries  
 Načte maximální počet položek v tabulce barev.  
  
```
int GetMaxColorTableEntries() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek v tabulce barev.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda podporuje pouze DIB části bitmapy.  
  
##  <a name="getpitch"></a>  CImage::GetPitch  
 Získá výšku obrázku.  
  
```
int GetPitch() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výška obrázku. Pokud je vrácená hodnota záporná, bitmapy je DIB zdola nahoru a původu je levého dolního rohu. Pokud návratovou hodnotu kladné, bitmapy DIB shora dolů a původu je levém horním rohu.  
  
### <a name="remarks"></a>Poznámky  
 Je hloubka vzdálenost v bajtech mezi dvě adresy paměti, které představují na začátek řádku jeden rastrového obrázku a na začátek řádku další rastrového obrázku. Protože výška se měří v bajtech, výška obrázku pomáhá určit Pixelový formát. Výšku může zahrnovat také další paměť, vyhrazené pro bitové mapy.  
  
 Použití `GetPitch` s [GetBits](#getbits) najít jednotlivých pixelů bitové kopie.  
  
> [!NOTE]
>  Tato metoda podporuje pouze DIB části bitmapy.  
  
##  <a name="getpixel"></a>  CImage::GetPixel  
 Načte barva pixelů na umístění, které *x* a *y*.  
  
```
COLORREF GetPixel(int x,int y) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 Souřadnice x obrazového bodu.  
  
 *y*  
 Souřadnice y obrazového bodu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Červené, zelené, modré (RGB) hodnota pixelech. Pokud pixel mimo oblast ořezu aktuální, je vrácenou hodnotu **CLR_INVALID**.  
  
##  <a name="getpixeladdress"></a>  CImage::GetPixelAddress  
 Načte přesnou adresu jeden bod.  
  
```
void* GetPixelAddress(int x,int y) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 Souřadnice x obrazového bodu.  
  
 *y*  
 Souřadnice y obrazového bodu.  
  
### <a name="remarks"></a>Poznámky  
 Adresa je určen podle souřadnice pixel, výška bitovou mapu a bitů na pixel.  
  
 Formáty, které mají méně než 8 bitů na pixel tato metoda vrátí adresu bajtů obsahující pixelech. Pokud má vaše formát obrázku 4 bitů na pixel, například `GetPixelAddress` vrátí adresu první pixelů v bajtů a je nutné vypočítat pro 2 pixelů na bajt.  
  
> [!NOTE]
>  Tato metoda podporuje pouze DIB části bitmapy.  
  
##  <a name="gettransparentcolor"></a>  CImage::GetTransparentColor  
 Načte indexované umístění průhledná barva palety barev.  
  
```
LONG GetTransparentColor() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Průhledná barva index.  
  
##  <a name="getwidth"></a>  CImage::GetWidth  
 Načte šířku v pixelech, bitové kopie.  
  
```
int GetWidth() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Šířka rastrového obrázku, v pixelech.  
  
##  <a name="isdibsection"></a>  CImage::IsDIBSection  
 Určuje, zda připojené rastrový obrázek DIB oddíl.  
  
```
bool IsDIBSection() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud DIB oddíl má připojené rastrový obrázek. V opačném případě **false**.  
  
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
 Určuje, zda pixelů rastrového obrázku jsou namapované na paletu barev.  
  
```
bool IsIndexed() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud indexované; jinak hodnota **false**.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vrátí hodnotu **true** pouze v případě bitovou mapu je 8bitové (256 barvami) nebo méně.  
  
> [!NOTE]
>  Tato metoda podporuje pouze DIB části bitmapy.  
  
##  <a name="isnull"></a>  CImage::IsNull  
 Určuje, pokud je momentálně načtených rastrový obrázek.  
  
```
bool IsNull() const throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vrátí hodnotu **True** Pokud rastrový obrázek není aktuálně načíst; jinak hodnota **False**.  
  
##  <a name="istransparencysupported"></a>  CImage::IsTransparencySupported  
 Určuje, jestli aplikace podporuje transparentní bitmapy.  
  
```
static BOOL IsTransparencySupported() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je aktuální platforma podporuje průhlednost. Jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je vrácená hodnota nenulové hodnoty a průhlednost je podporováno, volání [AlphaBlend](#alphablend), [TransparentBlt](#transparentblt), nebo [kreslení](#draw) zpracuje transparentní barvy.  
  

##  <a name="load"></a>  CImage::Load  
 Načte obrázek.  
  
```
HRESULT Load(LPCTSTR pszFileName) throw();
HRESULT Load(IStream* pStream) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszFileName`  
 Ukazatel na řetězec obsahující název souboru bitové kopie k načtení.  
  
 `pStream`  
 Ukazatel na datový proud, který obsahuje název souboru bitové kopie načíst.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
### <a name="remarks"></a>Poznámky  
 Načte obrázek určeného *pszFileName* nebo `pStream`.  
  
 Typy platnou bitovou kopií jsou BMP, GIF, JPEG, PNG a TIFF.  
  
##  <a name="loadfromresource"></a>  CImage::LoadFromResource  
 Načte bitovou kopii `BITMAP` prostředků.  
  
```
void LoadFromResource(
 HINSTANCE hInstance,
 LPCTSTR pszResourceName) throw();

void LoadFromResource(
 HINSTANCE hInstance,
 UINT nIDResource) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `hInstance`  
 Zpracování na instanci modul, který obsahuje obrázek, který má být načten.  
  
 `pszResourceName`  
 Ukazatel na řetězec obsahující název prostředek obsahující bitovou kopii načíst.  
  
 `nIDResource`  
 ID prostředku se načíst.  
  
### <a name="remarks"></a>Poznámky  
 Prostředek musí být typu `BITMAP`.  
  
##  <a name="maskblt"></a>  CImage::MaskBlt  
 Kombinuje data barvu pro zdrojové a cílové rastrové obrázky, pomocí zadané maska a rastrové operace.  
  
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
 `hDestDC`  
 Obslužná rutina modulu, jehož spustitelný soubor obsahuje prostředek.  
  
 `xDest`  
 Souřadnice x, v logických jednotek, levého horního rohu obdélníku cílový.  
  
 `yDest`  
 Souřadnice y, v logických jednotek, levého horního rohu obdélníku cílový.  
  
 `nDestWidth`  
 Šířka v logické jednotky cílového obdélníku a zdroj bitové mapy.  
  
 `nDestHeight`  
 Výška v logické jednotky cílového obdélníku a zdroj bitové mapy.  
  
 `xSrc`  
 Logické souřadnici x levého horního rohu rastrový obrázek zdroje.  
  
 `ySrc`  
 Logické souřadnici y levého horního rohu rastrový obrázek zdroje.  
  
 `hbmMask`  
 Popisovač černobílý maska bitmapy v kombinaci s rastrový obrázek barvu v kontextu zařízení zdroje.  
  
 `xMask`  
 Posun vodorovné pixelů pro bitovou mapu maska určeného `hbmMask` parametr.  
  
 `yMask`  
 Posun svislé pixelů pro bitovou mapu maska určeného `hbmMask` parametr.  
  
 `dwROP`  
 Určuje popředí ani pozadí kódy Ternární rastrových operací, které metoda používá k řízení kombinace zdrojového a cílového data. Kód pozadí rastrové operace je uložen v horní bajtů aplikace word horní této hodnoty; Kód popředí rastrové operace je uložen v bajtech nejnižší aplikace word horní této hodnoty; word nejnižší této hodnoty je ignorován a musí být nula. Informace o popředí a na pozadí v kontextu tuto metodu, najdete v části `MaskBlt` ve Windows SDK. Seznam kódů běžné operace rastrových najdete v tématu `BitBlt` ve Windows SDK.  
  
 `rectDest`  
 Odkaz na `RECT` struktura, identifikace cíl.  
  
 `pointSrc`  
 A `POINT` struktura označující levém horním rohu obdélníku zdroje.  
  
 `pointMask`  
 A **bodu** struktura označující levém horním rohu maska rastrového obrázku.  
  
 `pointDest`  
 Odkaz na **bodu** struktura, která identifikuje levém horním rohu obdélníku cílové, v logické jednotky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud bylo úspěšné, jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda se vztahuje na systému Windows NT verze 4.0 a vyšší.  
  
##  <a name="operator_hbitmap"></a>  CImage::operator HBITMAP  
 Tento operátor. použijte k získání připojené popisovač GDI systému Windows `CImage` objektu. Operátor je operátor přetypování, který podporuje přímý použití `HBITMAP` objektu.  
  
##  <a name="plgblt"></a>  CImage::PlgBlt  
 Provede přenos bitového bloku z obdélníku v kontextu zařízení zdroje do rovnoběžník v kontextu cílové zařízení.  
  
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
 `hDestDC`  
 Popisovač pro kontext cílové zařízení.  
  
 *pPoints*  
 Ukazatel na tři body místa logického, které identifikují tři rozích rovnoběžník cílového pole. Levém horním rohu obdélníku zdroj je namapována na prvním bodem toto pole, pravém horním rohu na druhý bod v toto pole a levého dolního rohu třetí bodu. Pravém dolním rohu obdélníku, zdroj je namapována na implicitní čtvrtý bod v rovnoběžník.  
  
 `hbmMask`  
 Popisovač pro volitelné černobílý rastrový obrázek, který se používá k maskování barvy rámeček zdroje.  
  
 `xSrc`  
 Souřadnice x, v logických jednotek, levého horního rohu obdélníku zdroje.  
  
 `ySrc`  
 Souřadnice y, v logických jednotek, levého horního rohu obdélníku zdroje.  
  
 `nSrcWidth`  
 Šířka v logických jednotek, obdélníku zdroje.  
  
 `nSrcHeight`  
 Výška v logických jednotek, obdélníku zdroje.  
  
 `xMask`  
 Souřadnice x levého horního rohu černobílý rastrového obrázku.  
  
 `yMask`  
 Souřadnice y levého horního rohu černobílý rastrového obrázku.  
  
 `rectSrc`  
 Odkaz na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura zadání souřadnice rámeček zdroje.  
  
 `pointMask`  
 A [bodu](http://msdn.microsoft.com/library/windows/desktop/dd162805) struktura označující levém horním rohu maska rastrového obrázku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud bylo úspěšné, jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `hbmMask` identifikuje platný rastrový obrázek černobílý, **PlgBit** používá tento rastrový obrázek k maskování bits barva dat z obdélníku zdroje.  
  
 Tato metoda se vztahuje na systému Windows NT verze 4.0 a vyšší. V tématu [PlgBlt](http://msdn.microsoft.com/library/windows/desktop/dd162804) ve Windows SDK pro podrobnější informace.  
  
##  <a name="releasedc"></a>  CImage::ReleaseDC  
 Uvolní kontextu zařízení.  
  
```
void ReleaseDC() const throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Vzhledem k tomu, že lze vybrat pouze jeden rastrového obrázku v kontextu zařízení současně, je třeba volat `ReleaseDC` pro každé volání [GetDC](#getdc).  
  
##  <a name="releasegdiplus"></a>  CImage::ReleaseGDIPlus  
 Uvolní prostředky využívané třídou GDI +.  
  
```
void ReleaseGDIPlus() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda musí být volána kvůli uvolnění prostředků, které jsou přidělené jako globální `CImage` objektu. V tématu [CImage::CImage](#cimage).  
  
##  <a name="save"></a>  CImage::Save  
 Obrázek uloží do zadaného datového proudu nebo soubor na disku.  
  
```
HRESULT Save(IStream* pStream,
 REFGUID guidFileType) const throw();

HRESULT Save(LPCTSTR pszFileName,
 REFGUID guidFileType= GUID_NULL) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pStream`  
 Ukazatel na objekt IStream on Request COM obsahující data souboru obrázku.  
  
 *pszFileName*  
 Ukazatel na název souboru pro bitovou kopii.  
  
 `guidFileType`  
 Typ souboru, který chcete uložit obrázek jako. Může být jedna z následujících akcí:  
  
- **ImageFormatBMP** bitovou kopii nekomprimované rastrového obrázku.  
  
- **ImageFormatPNG** komprimovanou bitovou kopii A grafické PNG (Portable Network).  
  
- **ImageFormatJPEG** zkomprimovaná bitová kopie A JPEG.  
  
- **ImageFormatGIF** A GIF zkomprimovaná bitová kopie.  
  
> [!NOTE]
>  Úplný seznam konstanty, najdete v části **konstanty formát souboru obrázku** ve Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce, které chcete uložit obrázek pomocí zadaného názvu a typu. Pokud `guidFileType` parametr neuvedete, příponu názvu souboru se použije k určení formátu obrázku. Pokud je k dispozici žádné rozšíření, bitovou kopii se uloží ve formátu BMP.  
  
##  <a name="setcolortable"></a>  CImage::SetColorTable  
 Nastaví hodnoty barev red, zelené, modré (RGB) pro řadu položky v palety DIB oddílu.  
  
```
void SetColorTable(
  UINT iFirstColor, 
  UINT nColors,
  const RGBQUAD* prgbColors) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `iFirstColor`  
 Index tabulky barev první položky nastavení.  
  
 `nColors`  
 Počet položek barev tabulky nastavit.  
  
 `prgbColors`  
 Ukazatel na pole [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938) struktury nastavit barvu tabulky položky.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda podporuje pouze DIB části bitmapy.  
  
##  <a name="setpixel"></a>  CImage::SetPixel  
 Nastaví barvu jeden bod v daném umístění v souboru bitové mapy.  
  
```
void SetPixel(int x, int y, COLORREF color) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 Vodorovné umístění pixelů nastavit.  
  
 *y*  
 Svislé umístění pixelů nastavit.  
  
 `color`  
 Barva, ke kterému nastavena pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda selže, pokud pixelů koordinuje leží mimo oblast ořezu vybrané.  
  
##  <a name="setpixelindexed"></a>  CImage::SetPixelIndexed  
 Nastaví barvu pixelů na barvu nacházející se v `iIndex` palety barev.  
  
```
void SetPixelIndexed(int x, int y, int iIndex) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 Vodorovné umístění pixelů nastavit.  
  
 *y*  
 Svislé umístění pixelů nastavit.  
  
 `iIndex`  
 Index barvy palety barev.  
  
##  <a name="setpixelrgb"></a>  CImage::SetPixelRGB  
 Nastaví pixel v umístěních určeného *x* a *y* pro barev indikován *r*, *g*, a *b*, červeně, zelená, modrá bitové kopie (RGB).  
  
```
void SetPixelRGB(  
 int x,
 int y,
 BYTE r,
 BYTE g,
 BYTE b) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 Vodorovné umístění pixelů nastavit.  
  
 *y*  
 Svislé umístění pixelů nastavit.  
  
 *r*  
 Intenzita červenou barvu.  
  
 *g*  
 Intenzita zelenou barvu.  
  
 *b*  
 Intenzita modrou barvu.  
  
### <a name="remarks"></a>Poznámky  
 Každý červené, zelené a modré parametry jsou reprezentované pomocí číslo mezi 0 a 255. Pokud nastavíte všechny tři parametry na nulu, kombinované výsledná barva je černé. Pokud nastavíte na 255 všechny tři parametry, je bílé kombinované výsledné barvu.  
  
##  <a name="settransparentcolor"></a>  CImage::SetTransparentColor  
 Nastaví barvu, která v daném indexované umístění jako transparentní.  
  
```
LONG SetTransparentColor(LONG iTransparentColor) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *iTransparentColor*  
 Index palety barev, barvy nastavit na transparentní. -1, pokud žádné barva je nastavena na hodnotu transparentní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index barvu dříve nastavené jako průhledná.  
  
##  <a name="stretchblt"></a>  CImage::StretchBlt  
 Kopíruje rastrový obrázek z kontextu zařízení zdroj pro tuto aktuální kontext zařízení.  
  
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
 `hDestDC`  
 Popisovač pro kontext cílové zařízení.  
  
 `xDest`  
 Souřadnice x, v logických jednotek, levého horního rohu obdélníku cílový.  
  
 `yDest`  
 Souřadnice y, v logických jednotek, levého horního rohu obdélníku cílový.  
  
 `nDestWidth`  
 Šířka v logických jednotek, cílový rámečku.  
  
 `nDestHeight`  
 Výška v logických jednotek, cílový rámečku.  
  
 `dwROP`  
 Rastrové operaci provést. Rastrové operace kódy definovat přesně jak kombinovat bits zdroj, cíl a vzoru (podle definice v aktuálně vybraném štětce) a vytvořit cíl. V tématu [přenos bitových bloků](http://msdn.microsoft.com/library/windows/desktop/dd183370) ve Windows SDK pro seznam ostatní kódy rastrové operace a jejich popisy.  
  
 `rectDest`  
 Odkaz na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura, identifikace cíl.  
  
 `xSrc`  
 Souřadnice x, v logických jednotek, levého horního rohu obdélníku zdroje.  
  
 `ySrc`  
 Souřadnice y, v logických jednotek, levého horního rohu obdélníku zdroje.  
  
 `nSrcWidth`  
 Šířka v logických jednotek, obdélníku zdroje.  
  
 `nSrcHeight`  
 Výška v logických jednotek, obdélníku zdroje.  
  
 `rectSrc`  
 Odkaz na `RECT` struktura, identifikace zdroji.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud bylo úspěšné, jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [StretchBlt](http://msdn.microsoft.com/library/windows/desktop/dd145120) ve Windows SDK.  
  
##  <a name="transparentblt"></a>  CImage::TransparentBlt  
 Kopíruje rastrový obrázek z kontextu zařízení zdroj pro tuto aktuální kontext zařízení.  
  
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
 `hDestDC`  
 Popisovač pro kontext cílové zařízení.  
  
 `xDest`  
 Souřadnice x, v logických jednotek, levého horního rohu obdélníku cílový.  
  
 `yDest`  
 Souřadnice y, v logických jednotek, levého horního rohu obdélníku cílový.  
  
 `nDestWidth`  
 Šířka v logických jednotek, cílový rámečku.  
  
 `nDestHeight`  
 Výška v logických jednotek, cílový rámečku.  
  
 *crTransparent*  
 Barva v souboru bitové mapy zdroje k považována za průhlednou. Ve výchozím nastavení **CLR_INVALID**, která určuje, že má být použita barva aktuálně nastaven jako průhledná barva obrázku.  
  
 `rectDest`  
 Odkaz na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura, identifikace cíl.  
  
 `xSrc`  
 Souřadnice x, v logických jednotek, levého horního rohu obdélníku zdroje.  
  
 `ySrc`  
 Souřadnice y, v logických jednotek, levého horního rohu obdélníku zdroje.  
  
 `nSrcWidth`  
 Šířka v logických jednotek, obdélníku zdroje.  
  
 `nSrcHeight`  
 Výška v logických jednotek, obdélníku zdroje.  
  
 `rectSrc`  
 Odkaz na `RECT` struktura, identifikace zdroji.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud bylo úspěšné, jinak **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 `TransparentBlt` je podporován pro zdroj bitmap 4 bitů na pixel a 8 bitů na pixel. Použití [CImage::AlphaBlend](#alphablend) a zadejte 32 bitů na pixel bitmap s průhlednost.  
  
  
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
 [Ukázka MMXSwarm](../../visual-cpp-samples.md)   
 [Ukázka SimpleImage](../../visual-cpp-samples.md)   
 [Rastrové obrázky nezávislé na zařízení](http://msdn.microsoft.com/library/windows/desktop/dd183562)   
 [CreateDIBSection](http://msdn.microsoft.com/library/windows/desktop/dd183494)   
 [ATL COM plochy součásti](../../atl/atl-com-desktop-components.md) [Device Independent Bitmap](http://msdn.microsoft.com/library/windows/desktop/dd183562)   
 [CreateDIBSection](http://msdn.microsoft.com/library/windows/desktop/dd183494)   









