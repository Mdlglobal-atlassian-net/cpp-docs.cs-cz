---
title: Cd2dbitmap – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d232eec6593e0daafb31461847e8d481e60f80ba
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374351"
---
# <a name="cd2dbitmap-class"></a>Cd2dbitmap – třída

Obálka pro ID2D1Bitmap.

## <a name="syntax"></a>Syntaxe

```
class CD2DBitmap : public CD2DResource;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CD2DBitmap::CD2DBitmap](#cd2dbitmap)|Přetíženo. Vytvoří objekt cd2dbitmap – od HBITMAP.|
|[Cd2dbitmap –:: ~ cd2dbitmap –](#_dtorcd2dbitmap)|Destruktor. Volá se, když se likviduje objektu D2D rastrového obrázku.|

### <a name="protected-constructors"></a>Chráněné konstruktory

|Název|Popis|
|----------|-----------------|
|[CD2DBitmap::CD2DBitmap](#cd2dbitmap)|Přetíženo. Vytvoří objekt cd2dbitmap –.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CD2DBitmap::Attach](#attach)|Bude k obrazci existujících prostředků rozhraní pro objekt|
|[CD2DBitmap::CopyFromBitmap](#copyfrombitmap)|Zkopíruje zadanou oblast ze zadaného rastrový obrázek do aktuální rastrový obrázek|
|[CD2DBitmap::CopyFromMemory](#copyfrommemory)|Zkopíruje zadanou oblast z paměti do aktuálního rastrový obrázek|
|[CD2DBitmap::CopyFromRenderTarget](#copyfromrendertarget)|Zkopíruje zadanou oblast ze zadaného cíl vykreslování do aktuální rastrový obrázek|
|[CD2DBitmap::Create](#create)|Vytvoří cd2dbitmap –. (Přepíše [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DBitmap::Destroy](#destroy)|Odstraní objekt cd2dbitmap –. (Přepíše [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DBitmap::detach](#detach)|Odpojí prostředků rozhraní z objektu|
|[CD2DBitmap::Get](#get)|Vrátí ID2D1Bitmap rozhraní|
|[CD2DBitmap::GetDPI](#getdpi)|Vrátí bodů na palec (DPI) rastrového obrázku|
|[CD2DBitmap::GetPixelFormat](#getpixelformat)|Načte režim pixel formátu a alfa rastrového obrázku|
|[CD2DBitmap::GetPixelSize](#getpixelsize)|Vrátí velikost v jednotkách závislé na zařízení (v pixelech), rastrového obrázku|
|[CD2DBitmap::GetSize](#getsize)|Vrátí velikost v pixelech nezávislých na zařízení (DIP) rastrového obrázku|
|[CD2DBitmap::IsValid](#isvalid)|Zkontroluje platnost prostředku (přepíše [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CD2DBitmap::CommonInit](#commoninit)|Inicializuje objekt|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CD2DBitmap::Operator ID2D1Bitmap *](#operator_id2d1bitmap_star)|Vrátí ID2D1Bitmap rozhraní|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CD2DBitmap::m_bAutoDestroyHBMP](#m_bautodestroyhbmp)|Hodnota TRUE, pokud by měl být zničeny m_hBmpSrc; v opačném případě FALSE.|
|[CD2DBitmap::m_hBmpSrc](#m_hbmpsrc)|Popisovač zdroj rastrového obrázku.|
|[CD2DBitmap::m_lpszType](#m_lpsztype)|Typ prostředku.|
|[CD2DBitmap::m_pBitmap](#m_pbitmap)|Uchovává ukazatel na objekt ID2D1Bitmap.|
|[CD2DBitmap::m_sizeDest](#m_sizedest)|Bitmap – určení velikosti.|
|[CD2DBitmap::m_strPath](#m_strpath)|Cesta k souboru Botmap.|
|[CD2DBitmap::m_uiResID](#m_uiresid)|ID prostředku rastrového obrázku|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cd2dresource –](../../mfc/reference/cd2dresource-class.md)

`CD2DBitmap`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

##  <a name="_dtorcd2dbitmap"></a>  Cd2dbitmap –:: ~ cd2dbitmap –

Destruktor. Volá se, když se likviduje objektu D2D rastrového obrázku.

```
virtual ~CD2DBitmap();
```

##  <a name="attach"></a>  CD2DBitmap::Attach

Bude k obrazci existujících prostředků rozhraní objektu.

```
void Attach(ID2D1Bitmap* pResource);
```

### <a name="parameters"></a>Parametry

*pResource*<br/>
Rozhraní existující prostředek. Nemůže mít hodnotu NULL.

##  <a name="cd2dbitmap"></a>  CD2DBitmap::CD2DBitmap

Vytvoří objekt cd2dbitmap – z prostředku.

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
Ukazatel na cíl vykreslování.

*uiResID*<br/>
Číslo ID prostředku prostředku.

*lpszType*<br/>
Ukazatel na řetězec zakončený hodnotou null, který obsahuje typ prostředku.

*sizeDest*<br/>
Velikost cílové bitmapy.

*bAutoDestroy*<br/>
Označuje, že bude objekt zničen. vlastník (pParentTarget).

*lpszPath*<br/>
Ukazatel na řetězec zakončený hodnotou null, který obsahuje název souboru.

*hbmpSrc*<br/>
Popisovače rastrového obrázku.

##  <a name="commoninit"></a>  CD2DBitmap::CommonInit

Inicializuje objekt.

```
void CommonInit();
```

##  <a name="copyfrombitmap"></a>  CD2DBitmap::CopyFromBitmap

Zkopíruje zadanou oblast ze zadaného rastrový obrázek do aktuální rastrového obrázku.

```
HRESULT CopyFromBitmap(
    const CD2DBitmap* pBitmap,
    const CD2DPointU* destPoint = NULL,
    const CD2DRectU* srcRect = NULL);
```

### <a name="parameters"></a>Parametry

*pBitmap*<br/>
Rastrový obrázek bude kopírováno.

*destPoint*<br/>
V aktuální rastrového obrázku levém horním rohu oblasti, ke které oblasti určené srcRect zkopírován.

*srcRect*<br/>
Oblast rastrové obrázku pro kopírování.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu S_OK. V opačném případě vrátí kód chyby HRESULT.

##  <a name="copyfrommemory"></a>  CD2DBitmap::CopyFromMemory

Zkopíruje zadanou oblast z paměti do aktuálního rastrového obrázku.

```
HRESULT CopyFromMemory(
    const void* srcData,
    UINT32 pitch,
    const CD2DRectU* destRect = NULL);
```

### <a name="parameters"></a>Parametry

*srcData*<br/>
Data ke kopírování.

*Výška*<br/>
Stride nebo výšku zdrojovou bitmapu uložené v srcData. Stride je počet bajtů řádkového rozkladu (jeden řádek v paměti v pixelech). Nelze vypočítat stride z následujícího vzorce: šířka v pixelech \* pixel + odsazení paměti v bajtech.

*destRect*<br/>
V aktuální rastrového obrázku levém horním rohu oblasti, ke které oblasti určené srcRect zkopírován.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu S_OK. V opačném případě vrátí kód chyby HRESULT.

##  <a name="copyfromrendertarget"></a>  CD2DBitmap::CopyFromRenderTarget

Zkopíruje zadanou oblast ze zadaného cíl vykreslování do aktuální rastrového obrázku.

```
HRESULT CopyFromRenderTarget(
    const CRenderTarget* pRenderTarget,
    const CD2DPointU* destPoint = NULL,
    const CD2DRectU* srcRect = NULL);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Cíl vykreslování, který obsahuje oblasti, kterou chcete kopírovat.

*destPoint*<br/>
V aktuální rastrového obrázku levém horním rohu oblasti, ke které oblasti určené srcRect zkopírován.

*srcRect*<br/>
Oblast RenderTarget ke kopírování.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu S_OK. V opačném případě vrátí kód chyby HRESULT.

##  <a name="create"></a>  CD2DBitmap::Create

Vytvoří cd2dbitmap –.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Ukazatel na cíl vykreslování.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu S_OK. V opačném případě vrátí kód chyby HRESULT.

##  <a name="destroy"></a>  CD2DBitmap::Destroy

Odstraní objekt cd2dbitmap –.

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DBitmap::detach

Odpojí prostředků rozhraní z objektu.

```
ID2D1Bitmap* Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní odpojit prostředek.

##  <a name="get"></a>  CD2DBitmap::Get

Vrátí ID2D1Bitmap rozhraní.

```
ID2D1Bitmap* Get();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1Bitmap nebo hodnota NULL, pokud objekt ještě není inicializován.

##  <a name="getdpi"></a>  CD2DBitmap::GetDPI

Vrátí bodů na palec (DPI) rastrového obrázku.

```
CD2DSizeF GetDPI() const;
```

### <a name="return-value"></a>Návratová hodnota

Vodorovné a svislé DPI rastrového obrázku.

##  <a name="getpixelformat"></a>  CD2DBitmap::GetPixelFormat

Načte režim pixel formátu a alfa rastrového obrázku

```
D2D1_PIXEL_FORMAT GetPixelFormat() const;
```

### <a name="return-value"></a>Návratová hodnota

Pixel formátu a alfa režim rastrového obrázku.

##  <a name="getpixelsize"></a>  CD2DBitmap::GetPixelSize

Vrátí velikost v jednotkách závislé na zařízení (v pixelech), rastrového obrázku.

```
CD2DSizeU GetPixelSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Velikost v pixelech, rastrového obrázku...

##  <a name="getsize"></a>  CD2DBitmap::GetSize

Vrátí velikost v pixelech nezávislých na zařízení (DIP) rastrového obrázku.

```
CD2DSizeF GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Velikost v DIP rastrového obrázku.

##  <a name="isvalid"></a>  CD2DBitmap::IsValid

Ověří platnost prostředku.

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud prostředek je platná. v opačném případě FALSE.

##  <a name="m_bautodestroyhbmp"></a>  CD2DBitmap::m_bAutoDestroyHBMP

Hodnota TRUE, pokud by měl být zničeny m_hBmpSrc; v opačném případě FALSE.

```
BOOL m_bAutoDestroyHBMP;
```

##  <a name="m_hbmpsrc"></a>  CD2DBitmap::m_hBmpSrc

Popisovač zdroj rastrového obrázku.

```
HBITMAP m_hBmpSrc;
```

##  <a name="m_lpsztype"></a>  CD2DBitmap::m_lpszType

Typ prostředku.

```
LPCTSTR m_lpszType;
```

##  <a name="m_pbitmap"></a>  CD2DBitmap::m_pBitmap

Uchovává ukazatel na objekt ID2D1Bitmap.

```
ID2D1Bitmap* m_pBitmap;
```

##  <a name="m_sizedest"></a>  CD2DBitmap::m_sizeDest

Bitmap – určení velikosti.

```
CD2DSizeU m_sizeDest;
```

##  <a name="m_strpath"></a>  CD2DBitmap::m_strPath

Cesta k souboru Botmap.

```
CString m_strPath;
```

##  <a name="m_uiresid"></a>  CD2DBitmap::m_uiResID

ID prostředku rastrového obrázku

```
UINT m_uiResID;
```

##  <a name="operator_id2d1bitmap_star"></a>  CD2DBitmap::Operator ID2D1Bitmap *

Vrátí ID2D1Bitmap rozhraní

```
operator ID2D1Bitmap*();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1Bitmap nebo hodnota NULL, pokud objekt ještě není inicializován.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
