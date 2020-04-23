---
title: CD2DBitmapBrush – třída
ms.date: 11/04/2016
f1_keywords:
- CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::Attach
- AFXRENDERTARGET/CD2DBitmapBrush::Create
- AFXRENDERTARGET/CD2DBitmapBrush::Destroy
- AFXRENDERTARGET/CD2DBitmapBrush::Detach
- AFXRENDERTARGET/CD2DBitmapBrush::Get
- AFXRENDERTARGET/CD2DBitmapBrush::GetBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::GetExtendModeX
- AFXRENDERTARGET/CD2DBitmapBrush::GetExtendModeY
- AFXRENDERTARGET/CD2DBitmapBrush::GetInterpolationMode
- AFXRENDERTARGET/CD2DBitmapBrush::SetBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::SetExtendModeX
- AFXRENDERTARGET/CD2DBitmapBrush::SetExtendModeY
- AFXRENDERTARGET/CD2DBitmapBrush::SetInterpolationMode
- AFXRENDERTARGET/CD2DBitmapBrush::CommonInit
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmapBrushProperties
helpviewer_keywords:
- CD2DBitmapBrush [MFC], CD2DBitmapBrush
- CD2DBitmapBrush [MFC], Attach
- CD2DBitmapBrush [MFC], Create
- CD2DBitmapBrush [MFC], Destroy
- CD2DBitmapBrush [MFC], Detach
- CD2DBitmapBrush [MFC], Get
- CD2DBitmapBrush [MFC], GetBitmap
- CD2DBitmapBrush [MFC], GetExtendModeX
- CD2DBitmapBrush [MFC], GetExtendModeY
- CD2DBitmapBrush [MFC], GetInterpolationMode
- CD2DBitmapBrush [MFC], SetBitmap
- CD2DBitmapBrush [MFC], SetExtendModeX
- CD2DBitmapBrush [MFC], SetExtendModeY
- CD2DBitmapBrush [MFC], SetInterpolationMode
- CD2DBitmapBrush [MFC], CommonInit
- CD2DBitmapBrush [MFC], m_pBitmap
- CD2DBitmapBrush [MFC], m_pBitmapBrush
- CD2DBitmapBrush [MFC], m_pBitmapBrushProperties
ms.assetid: 46ebbe34-66e0-44c8-af1d-d129e851de5e
ms.openlocfilehash: 8d0804c094204bc0e8ab420e20c8b6a6a35dc70a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754288"
---
# <a name="cd2dbitmapbrush-class"></a>CD2DBitmapBrush – třída

Obálka pro ID2D1BitmapBrush.

## <a name="syntax"></a>Syntaxe

```
class CD2DBitmapBrush : public CD2DBrush;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CD2DBitmapBrush::CD2DBitmapBrush](#cd2dbitmapbrush)|Přetíženo. Vytvoří objekt CD2DBitmapBrush ze souboru.|
|[CD2DBitmapBrush::~CD2DBitmapBrush](#dtor)|Destruktor. Nazývá se při zničení objektu stopy bitmapy D2D.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CD2DBitmapBrush::Připojit](#attach)|Připojí k objektu existující rozhraní prostředků.|
|[CD2DBitmapBrush::Vytvořit](#create)|Vytvoří CD2DBitmapBrush. (Přepíše [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DBitmapBrush::Destroy](#destroy)|Zničí objekt CD2DBitmapBrush. (Přepíše [CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|
|[CD2DBitmapBrush::Detach](#detach)|Odpojí rozhraní prostředků od objektu.|
|[CD2DBitmapBrush::Získat](#get)|Vrátí rozhraní ID2D1BitmapBrush.|
|[CD2DBitmapBrush::GetBitmap](#getbitmap)|Získá zdroj bitmapy, který tato stopa používá k malování|
|[CD2DBitmapBrush::GetExtendModeX](#getextendmodex)|Získá metodu, kterou stopa vodorovně dlaždice ty oblasti, které přesahují jeho rastrový obrázek|
|[CD2DBitmapBrush::GetExtendModeY](#getextendmodey)|Získá metodu, kterou stopa svisle dlaždice ty oblasti, které přesahují jeho rastrový obrázek|
|[CD2DBitmapBrush::GetInterpolationMode](#getinterpolationmode)|Získá metodu interpolace použitou při zmenšení nebo otočení bitmapy stopy.|
|[CD2DBitmapBrush::SetBitmap](#setbitmap)|Určuje zdroj bitmapy, který tato stopa používá k malování.|
|[CD2DBitmapBrush::SetExtendModeX](#setextendmodex)|Určuje, jak stopa vodorovně obsadí oblasti, které přesahují její bitmapu.|
|[CD2DBitmapBrush::SetExtendModeY](#setextendmodey)|Určuje, jak stopa svisle obsadí oblasti, které přesahují její bitmapu.|
|[CD2DBitmapBrush::Nastavit režim interpolace](#setinterpolationmode)|Určuje režim interpolace použitý při změna měřítka nebo otočení bitmapy stopy.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CD2DBitmapBrush::CommonInit](#commoninit)|Inicializuje objekt.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CD2DBitmapBrush::operátor ID2D1BitmapBrush*](#operator_id2d1bitmapbrush_star)|Vrátí rozhraní ID2D1BitmapBrush.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Název|Popis|
|----------|-----------------|
|[CD2DBitmapBrush::m_pBitmap](#m_pbitmap)|Uloží ukazatel na objekt CD2DBitmap.|
|[CD2DBitmapBrush::m_pBitmapBrush](#m_pbitmapbrush)|Uloží ukazatel na objekt ID2D1BitmapBrush.|
|[CD2DBitmapBrush::m_pBitmapBrushProperties](#m_pbitmapbrushproperties)|Vlastnosti bitmapového stopy.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Zdroj CD2D](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

`CD2DBitmapBrush`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

## <a name="cd2dbitmapbrushcd2dbitmapbrush"></a><a name="dtor"></a>CD2DBitmapBrush::~CD2DBitmapBrush

Destruktor. Nazývá se při zničení objektu stopy bitmapy D2D.

```
virtual ~CD2DBitmapBrush();
```

## <a name="cd2dbitmapbrushattach"></a><a name="attach"></a>CD2DBitmapBrush::Připojit

Připojí k objektu existující rozhraní prostředků.

```cpp
void Attach(ID2D1BitmapBrush* pResource);
```

### <a name="parameters"></a>Parametry

*pZdroj*<br/>
Existující rozhraní prostředků. Nelze získat hodnotu NULL.

## <a name="cd2dbitmapbrushcd2dbitmapbrush"></a><a name="cd2dbitmapbrush"></a>CD2DBitmapBrush::CD2DBitmapBrush

Vytvoří objekt CD2DBitmapBrush.

```
CD2DBitmapBrush(
    CRenderTarget* pParentTarget,
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);

CD2DBitmapBrush(
    CRenderTarget* pParentTarget,
    UINT uiResID,
    LPCTSTR lpszType = NULL,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);

CD2DBitmapBrush(
    CRenderTarget* pParentTarget,
    LPCTSTR lpszImagePath,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Ukazatel na cíl vykreslení.

*pBitmapBrushProperties*<br/>
Ukazatel na režimy rozšíření a režim interpolace bitmapového štětce.

*pVlastnosti brushu*<br/>
Ukazatel na krytí a transformaci stopy.

*bAutoDestroy*<br/>
Označuje, že objekt bude zničen vlastníkem (pParentTarget).

*uiResID*<br/>
Číslo ID prostředku.

*lpszTyp*<br/>
Ukazatel na řetězec s ukončeným hodnotou null, který obsahuje typ prostředku.

*sizeDest*<br/>
Cílová velikost bitmapy.

*lpszImagePath*<br/>
Ukazatel na řetězec s ukončeným hodnotou null, který obsahuje název souboru.

## <a name="cd2dbitmapbrushcommoninit"></a><a name="commoninit"></a>CD2DBitmapBrush::CommonInit

Inicializuje objekt.

```cpp
void CommonInit(D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties);
```

### <a name="parameters"></a>Parametry

*pBitmapBrushProperties*<br/>
Ukazatel na vlastnosti bitmapového stopy.

## <a name="cd2dbitmapbrushcreate"></a><a name="create"></a>CD2DBitmapBrush::Vytvořit

Vytvoří CD2DBitmapBrush.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Ukazatel na cíl vykreslení.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. V opačném případě vrátí kód chyby HRESULT.

## <a name="cd2dbitmapbrushdestroy"></a><a name="destroy"></a>CD2DBitmapBrush::Destroy

Zničí objekt CD2DBitmapBrush.

```
virtual void Destroy();
```

## <a name="cd2dbitmapbrushdetach"></a><a name="detach"></a>CD2DBitmapBrush::Detach

Odpojí rozhraní prostředků od objektu.

```
ID2D1BitmapBrush* Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní odpojeného prostředku.

## <a name="cd2dbitmapbrushget"></a><a name="get"></a>CD2DBitmapBrush::Získat

Vrátí rozhraní ID2D1BitmapBrush.

```
ID2D1BitmapBrush* Get();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1BitmapBrush nebo NULL, pokud objekt ještě není inicializován.

## <a name="cd2dbitmapbrushgetbitmap"></a><a name="getbitmap"></a>CD2DBitmapBrush::GetBitmap

Získá zdroj bitmapy, který tato stopa používá k malování

```
CD2DBitmap* GetBitmap();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt CD2DBitmap nebo NULL, pokud objekt ještě není inicializován.

## <a name="cd2dbitmapbrushgetextendmodex"></a><a name="getextendmodex"></a>CD2DBitmapBrush::GetExtendModeX

Získá metodu, kterou stopa vodorovně dlaždice ty oblasti, které přesahují jeho rastrový obrázek

```
D2D1_EXTEND_MODE GetExtendModeX() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která určuje, jak stopa vodorovně dlaždice ty oblasti, které přesahují jeho rastrový obrázek

## <a name="cd2dbitmapbrushgetextendmodey"></a><a name="getextendmodey"></a>CD2DBitmapBrush::GetExtendModeY

Získá metodu, kterou stopa svisle dlaždice ty oblasti, které přesahují jeho rastrový obrázek

```
D2D1_EXTEND_MODE GetExtendModeY() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která určuje, jak stopa svisle dlaždice ty oblasti, které přesahují jeho rastrový obrázek

## <a name="cd2dbitmapbrushgetinterpolationmode"></a><a name="getinterpolationmode"></a>CD2DBitmapBrush::GetInterpolationMode

Získá metodu interpolace použitou při zmenšení nebo otočení bitmapy stopy.

```
D2D1_BITMAP_INTERPOLATION_MODE GetInterpolationMode() const;
```

### <a name="return-value"></a>Návratová hodnota

Metoda interpolace použitá při změna měřítka nebo otočení bitmapy stopy

## <a name="cd2dbitmapbrushm_pbitmap"></a><a name="m_pbitmap"></a>CD2DBitmapBrush::m_pBitmap

Uloží ukazatel na objekt CD2DBitmap.

```
CD2DBitmap* m_pBitmap;
```

## <a name="cd2dbitmapbrushm_pbitmapbrush"></a><a name="m_pbitmapbrush"></a>CD2DBitmapBrush::m_pBitmapBrush

Uloží ukazatel na objekt ID2D1BitmapBrush.

```
ID2D1BitmapBrush* m_pBitmapBrush;
```

## <a name="cd2dbitmapbrushm_pbitmapbrushproperties"></a><a name="m_pbitmapbrushproperties"></a>CD2DBitmapBrush::m_pBitmapBrushProperties

Vlastnosti bitmapového stopy.

```
D2D1_BITMAP_BRUSH_PROPERTIES* m_pBitmapBrushProperties;
```

## <a name="cd2dbitmapbrushoperator-id2d1bitmapbrush"></a><a name="operator_id2d1bitmapbrush_star"></a>CD2DBitmapBrush::operátor ID2D1BitmapBrush*

Vrátí rozhraní ID2D1BitmapBrush.

```
operator ID2D1BitmapBrush*();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1BitmapBrush nebo NULL, pokud objekt ještě není inicializován.

## <a name="cd2dbitmapbrushsetbitmap"></a><a name="setbitmap"></a>CD2DBitmapBrush::SetBitmap

Určuje zdroj bitmapy, který tato stopa používá k malování.

```cpp
void SetBitmap(CD2DBitmap* pBitmap);
```

### <a name="parameters"></a>Parametry

*pBitmap*<br/>
Zdroj bitmapy používaný stopou

## <a name="cd2dbitmapbrushsetextendmodex"></a><a name="setextendmodex"></a>CD2DBitmapBrush::SetExtendModeX

Určuje, jak stopa vodorovně obsadí oblasti, které přesahují její bitmapu.

```cpp
void SetExtendModeX(D2D1_EXTEND_MODE extendModeX);
```

### <a name="parameters"></a>Parametry

*extendModeX*<br/>
Hodnota, která určuje, jak stopa vodorovně dlaždice ty oblasti, které přesahují jeho rastrový obrázek

## <a name="cd2dbitmapbrushsetextendmodey"></a><a name="setextendmodey"></a>CD2DBitmapBrush::SetExtendModeY

Určuje, jak stopa svisle obsadí oblasti, které přesahují její bitmapu.

```cpp
void SetExtendModeY(D2D1_EXTEND_MODE extendModeY);
```

### <a name="parameters"></a>Parametry

*extendModeY*<br/>
Hodnota, která určuje, jak stopa svisle dlaždice ty oblasti, které přesahují jeho rastrový obrázek

## <a name="cd2dbitmapbrushsetinterpolationmode"></a><a name="setinterpolationmode"></a>CD2DBitmapBrush::Nastavit režim interpolace

Určuje režim interpolace použitý při změna měřítka nebo otočení bitmapy stopy.

```cpp
void SetInterpolationMode(D2D1_BITMAP_INTERPOLATION_MODE interpolationMode);
```

### <a name="parameters"></a>Parametry

*interpolationMode*<br/>
Režim interpolace používaný při změna měřítka nebo otočení bitmapy stopy

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
