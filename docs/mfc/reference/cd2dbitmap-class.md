---
title: Třída CD2DBitmap
ms.date: 11/04/2016
f1_keywords:
- CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap::CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap::Attach
- AFXRENDERTARGET/CD2DBitmap::CopyFromBitmap
- AFXRENDERTARGET/CD2DBitmap::CopyFromMemory
- AFXRENDERTARGET/CD2DBitmap::CopyFromRenderTarget
- AFXRENDERTARGET/CD2DBitmap::Create
- AFXRENDERTARGET/CD2DBitmap::Destroy
- AFXRENDERTARGET/CD2DBitmap::Detach
- AFXRENDERTARGET/CD2DBitmap::Get
- AFXRENDERTARGET/CD2DBitmap::GetDPI
- AFXRENDERTARGET/CD2DBitmap::GetPixelFormat
- AFXRENDERTARGET/CD2DBitmap::GetPixelSize
- AFXRENDERTARGET/CD2DBitmap::GetSize
- AFXRENDERTARGET/CD2DBitmap::IsValid
- AFXRENDERTARGET/CD2DBitmap::CommonInit
- AFXRENDERTARGET/CD2DBitmap::m_bAutoDestroyHBMP
- AFXRENDERTARGET/CD2DBitmap::m_hBmpSrc
- AFXRENDERTARGET/CD2DBitmap::m_lpszType
- AFXRENDERTARGET/CD2DBitmap::m_pBitmap
- AFXRENDERTARGET/CD2DBitmap::m_sizeDest
- AFXRENDERTARGET/CD2DBitmap::m_strPath
- AFXRENDERTARGET/CD2DBitmap::m_uiResID
helpviewer_keywords:
- CD2DBitmap [MFC], CD2DBitmap
- CD2DBitmap [MFC], CD2DBitmap
- CD2DBitmap [MFC], Attach
- CD2DBitmap [MFC], CopyFromBitmap
- CD2DBitmap [MFC], CopyFromMemory
- CD2DBitmap [MFC], CopyFromRenderTarget
- CD2DBitmap [MFC], Create
- CD2DBitmap [MFC], Destroy
- CD2DBitmap [MFC], Detach
- CD2DBitmap [MFC], Get
- CD2DBitmap [MFC], GetDPI
- CD2DBitmap [MFC], GetPixelFormat
- CD2DBitmap [MFC], GetPixelSize
- CD2DBitmap [MFC], GetSize
- CD2DBitmap [MFC], IsValid
- CD2DBitmap [MFC], CommonInit
- CD2DBitmap [MFC], m_bAutoDestroyHBMP
- CD2DBitmap [MFC], m_hBmpSrc
- CD2DBitmap [MFC], m_lpszType
- CD2DBitmap [MFC], m_pBitmap
- CD2DBitmap [MFC], m_sizeDest
- CD2DBitmap [MFC], m_strPath
- CD2DBitmap [MFC], m_uiResID
ms.assetid: 2b3686f1-812c-462b-b449-9f0cb6949bf6
ms.openlocfilehash: ce4fe49e8af85c4b63be31bf10e9f196f85c019f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369309"
---
# <a name="cd2dbitmap-class"></a>Třída CD2DBitmap

Obálka pro ID2D1Bitmap.

## <a name="syntax"></a>Syntaxe

```
class CD2DBitmap : public CD2DResource;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DBitmap::CD2DBitmap](#cd2dbitmap)|Přetíženo. Vytvoří objekt CD2DBitmap z HBITMAP.|
|[CD2DBitmap::~CD2DBitmap](#_dtorcd2dbitmap)|Destruktor. Nazývá se při zničení bitmapového objektu D2D.|

### <a name="protected-constructors"></a>Chráněné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DBitmap::CD2DBitmap](#cd2dbitmap)|Přetíženo. Vytvoří objekt CD2DBitmap.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DBitmap::Připojit](#attach)|Připojí k objektu existující rozhraní prostředků.|
|[CD2DBitmap::CopyFromBitmap](#copyfrombitmap)|Zkopíruje zadanou oblast ze zadané bitmapy do aktuální bitmapy.|
|[CD2DBitmap::CopyFromMemory](#copyfrommemory)|Zkopíruje zadanou oblast z paměti do aktuální bitmapy.|
|[CD2DBitmap::CopyFromRenderTarget](#copyfromrendertarget)|Zkopíruje zadanou oblast ze zadaného cíle vykreslení do aktuální bitmapy.|
|[CD2DBitmap::Vytvořit](#create)|Vytvoří cd2DBitmap. (Přepíše [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DBitmap::Destroy](#destroy)|Zničí objekt CD2DBitmap. (Přepíše [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DBitmap::Detach](#detach)|Odpojí rozhraní prostředků od objektu.|
|[CD2DBitmap::Získat](#get)|Vrátí rozhraní ID2D1Bitmap.|
|[CD2DBitmap::GetDPI](#getdpi)|Vrácení tečů na palec (DPI) bitmapy|
|[CD2DBitmap::GetPixelFormat](#getpixelformat)|Načte formát obrazových bodů a alfa režim bitmapy.|
|[CD2DBitmap::GetPixelSize](#getpixelsize)|Vrátí velikost bitmapy v jednotkách závislých na zařízení (pixelech).|
|[CD2DBitmap::GetSize](#getsize)|Vrátí velikost bitmapy v pixelech nezávislých na zařízení.|
|[CD2DBitmap::IsValid](#isvalid)|Zkontroluje platnost prostředku (přepíše [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DBitmap::CommonInit](#commoninit)|Inicializuje objekt.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DBitmap::operátor ID2D1Bitmap*](#operator_id2d1bitmap_star)|Vrátí rozhraní ID2D1Bitmap.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DBitmap::m_bAutoDestroyHBMP](#m_bautodestroyhbmp)|PRAVDA, pokud m_hBmpSrc by měly být zničeny; jinak FALSE.|
|[CD2DBitmap::m_hBmpSrc](#m_hbmpsrc)|Zdrojový popisovač rastrového plánu.|
|[CD2DBitmap::m_lpszType](#m_lpsztype)|Typ zdroje.|
|[CD2DBitmap::m_pBitmap](#m_pbitmap)|Uloží ukazatel na objekt ID2D1Bitmap.|
|[CD2DBitmap::m_sizeDest](#m_sizedest)|Velikost cíle bitmapy.|
|[CD2DBitmap::m_strPath](#m_strpath)|Cesta k souboru Botmap.|
|[CD2DBitmap::m_uiResID](#m_uiresid)|Bitmapové ID prostředku.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Zdroj CD2D](../../mfc/reference/cd2dresource-class.md)

`CD2DBitmap`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

## <a name="cd2dbitmapcd2dbitmap"></a><a name="_dtorcd2dbitmap"></a>CD2DBitmap::~CD2DBitmap

Destruktor. Nazývá se při zničení bitmapového objektu D2D.

```
virtual ~CD2DBitmap();
```

## <a name="cd2dbitmapattach"></a><a name="attach"></a>CD2DBitmap::Připojit

Připojí k objektu existující rozhraní prostředků.

```
void Attach(ID2D1Bitmap* pResource);
```

### <a name="parameters"></a>Parametry

*pZdroj*<br/>
Existující rozhraní prostředků. Nemůže být null.

## <a name="cd2dbitmapcd2dbitmap"></a><a name="cd2dbitmap"></a>CD2DBitmap::CD2DBitmap

Vytvoří objekt CD2DBitmap z prostředku.

```
CD2DBitmap(
    CRenderTarget* pParentTarget,
    UINT uiResID,
    LPCTSTR lpszType = NULL,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    BOOL bAutoDestroy = TRUE);

CD2DBitmap(
    CRenderTarget* pParentTarget,
    LPCTSTR lpszPath,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    BOOL bAutoDestroy = TRUE);

CD2DBitmap(
    CRenderTarget* pParentTarget,
    HBITMAP hbmpSrc,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    BOOL bAutoDestroy = TRUE);

CD2DBitmap(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Ukazatel na cíl vykreslení.

*uiResID*<br/>
Číslo ID prostředku.

*lpszTyp*<br/>
Ukazatel na řetězec s ukončeným hodnotou null, který obsahuje typ prostředku.

*sizeDest*<br/>
Cílová velikost bitmapy.

*bAutoDestroy*<br/>
Označuje, že objekt bude zničen vlastníkem (pParentTarget).

*lpszPath*<br/>
Ukazatel na řetězec s ukončeným hodnotou null, který obsahuje název souboru.

*hbmpSrc*<br/>
Zpracovat rastrový obrázek.

## <a name="cd2dbitmapcommoninit"></a><a name="commoninit"></a>CD2DBitmap::CommonInit

Inicializuje objekt.

```
void CommonInit();
```

## <a name="cd2dbitmapcopyfrombitmap"></a><a name="copyfrombitmap"></a>CD2DBitmap::CopyFromBitmap

Zkopíruje zadanou oblast ze zadané bitmapy do aktuální bitmapy.

```
HRESULT CopyFromBitmap(
    const CD2DBitmap* pBitmap,
    const CD2DPointU* destPoint = NULL,
    const CD2DRectU* srcRect = NULL);
```

### <a name="parameters"></a>Parametry

*pBitmap*<br/>
Bitmapa, ze které chcete kopírovat.

*destPoint*<br/>
V aktuální bitmapě je zkopírován levý horní roh oblasti, do které je zkopírována oblast určená srcRect.

*srcRect*<br/>
Oblast bitmapy ke kopírování.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. V opačném případě vrátí kód chyby HRESULT.

## <a name="cd2dbitmapcopyfrommemory"></a><a name="copyfrommemory"></a>CD2DBitmap::CopyFromMemory

Zkopíruje zadanou oblast z paměti do aktuální bitmapy.

```
HRESULT CopyFromMemory(
    const void* srcData,
    UINT32 pitch,
    const CD2DRectU* destRect = NULL);
```

### <a name="parameters"></a>Parametry

*srcData*<br/>
Data ke kopírování.

*Hřiště*<br/>
Krok nebo rozteč zdrojové bitmapy uložené v srcData. Krok je počet bajtů scanline (jeden řádek pixelů v paměti). Krok lze vypočítat z následujícího vzorce: šířka \* pixelů bajtů na pixel + odsazení paměti.

*destRect*<br/>
V aktuální bitmapě je zkopírován levý horní roh oblasti, do které je zkopírována oblast určená srcRect.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. V opačném případě vrátí kód chyby HRESULT.

## <a name="cd2dbitmapcopyfromrendertarget"></a><a name="copyfromrendertarget"></a>CD2DBitmap::CopyFromRenderTarget

Zkopíruje zadanou oblast ze zadaného cíle vykreslení do aktuální bitmapy.

```
HRESULT CopyFromRenderTarget(
    const CRenderTarget* pRenderTarget,
    const CD2DPointU* destPoint = NULL,
    const CD2DRectU* srcRect = NULL);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Cíl vykreslení, který obsahuje oblast ke kopírování.

*destPoint*<br/>
V aktuální bitmapě je zkopírován levý horní roh oblasti, do které je zkopírována oblast určená srcRect.

*srcRect*<br/>
Oblast renderTarget kopírovat.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. V opačném případě vrátí kód chyby HRESULT.

## <a name="cd2dbitmapcreate"></a><a name="create"></a>CD2DBitmap::Vytvořit

Vytvoří cd2DBitmap.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Ukazatel na cíl vykreslení.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. V opačném případě vrátí kód chyby HRESULT.

## <a name="cd2dbitmapdestroy"></a><a name="destroy"></a>CD2DBitmap::Destroy

Zničí objekt CD2DBitmap.

```
virtual void Destroy();
```

## <a name="cd2dbitmapdetach"></a><a name="detach"></a>CD2DBitmap::Detach

Odpojí rozhraní prostředků od objektu.

```
ID2D1Bitmap* Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní odpojeného prostředku.

## <a name="cd2dbitmapget"></a><a name="get"></a>CD2DBitmap::Získat

Vrátí rozhraní ID2D1Bitmap.

```
ID2D1Bitmap* Get();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1Bitmap nebo NULL, pokud objekt ještě není inicializován.

## <a name="cd2dbitmapgetdpi"></a><a name="getdpi"></a>CD2DBitmap::GetDPI

Vraťte tečky na palec (DPI) bitmapy.

```
CD2DSizeF GetDPI() const;
```

### <a name="return-value"></a>Návratová hodnota

Vodorovný a svislý DPI bitmapy.

## <a name="cd2dbitmapgetpixelformat"></a><a name="getpixelformat"></a>CD2DBitmap::GetPixelFormat

Načte formát obrazových bodů a alfa režim bitmapy.

```
D2D1_PIXEL_FORMAT GetPixelFormat() const;
```

### <a name="return-value"></a>Návratová hodnota

Formát obrazových bodů a alfa režim bitmapy.

## <a name="cd2dbitmapgetpixelsize"></a><a name="getpixelsize"></a>CD2DBitmap::GetPixelSize

Vrátí velikost bitmapy v jednotkách závislých na zařízení (pixelech).

```
CD2DSizeU GetPixelSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Velikost bitmapy v obrazových bodech.

## <a name="cd2dbitmapgetsize"></a><a name="getsize"></a>CD2DBitmap::GetSize

Vrátí velikost bitmapy v pixelech nezávislých na zařízení.Returns the size, in device-independent pixels (DIPs) of the bitmap.

```
CD2DSizeF GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Velikost bitmapy v dispozicích DIPs.

## <a name="cd2dbitmapisvalid"></a><a name="isvalid"></a>CD2DBitmap::IsValid

Zkontroluje platnost prostředků.

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je prostředek platný; jinak FALSE.

## <a name="cd2dbitmapm_bautodestroyhbmp"></a><a name="m_bautodestroyhbmp"></a>CD2DBitmap::m_bAutoDestroyHBMP

PRAVDA, pokud m_hBmpSrc by měly být zničeny; jinak FALSE.

```
BOOL m_bAutoDestroyHBMP;
```

## <a name="cd2dbitmapm_hbmpsrc"></a><a name="m_hbmpsrc"></a>CD2DBitmap::m_hBmpSrc

Zdrojový popisovač rastrového plánu.

```
HBITMAP m_hBmpSrc;
```

## <a name="cd2dbitmapm_lpsztype"></a><a name="m_lpsztype"></a>CD2DBitmap::m_lpszType

Typ zdroje.

```
LPCTSTR m_lpszType;
```

## <a name="cd2dbitmapm_pbitmap"></a><a name="m_pbitmap"></a>CD2DBitmap::m_pBitmap

Uloží ukazatel na objekt ID2D1Bitmap.

```
ID2D1Bitmap* m_pBitmap;
```

## <a name="cd2dbitmapm_sizedest"></a><a name="m_sizedest"></a>CD2DBitmap::m_sizeDest

Velikost cíle bitmapy.

```
CD2DSizeU m_sizeDest;
```

## <a name="cd2dbitmapm_strpath"></a><a name="m_strpath"></a>CD2DBitmap::m_strPath

Cesta k souboru Botmap.

```
CString m_strPath;
```

## <a name="cd2dbitmapm_uiresid"></a><a name="m_uiresid"></a>CD2DBitmap::m_uiResID

Bitmapové ID prostředku.

```
UINT m_uiResID;
```

## <a name="cd2dbitmapoperator-id2d1bitmap"></a><a name="operator_id2d1bitmap_star"></a>CD2DBitmap::operátor ID2D1Bitmap*

Vrátí rozhraní ID2D1Bitmap.

```
operator ID2D1Bitmap*();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1Bitmap nebo NULL, pokud objekt ještě není inicializován.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
