---
title: Cd2dbitmapbrush – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6b40f7e3d4a37dbc73494444fbfcc398621b7ec4
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080010"
---
# <a name="cd2dbitmapbrush-class"></a>Cd2dbitmapbrush – třída

Obálka pro ID2D1BitmapBrush.

## <a name="syntax"></a>Syntaxe

```
class CD2DBitmapBrush : public CD2DBrush;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CD2DBitmapBrush::CD2DBitmapBrush](#cd2dbitmapbrush)|Přetíženo. Vytvoří objekt cd2dbitmapbrush – ze souboru.|
|[Cd2dbitmapbrush –:: ~ cd2dbitmapbrush –](#dtor)|Destruktor. Volá se, když se likviduje štětce objektu D2D rastrového obrázku.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CD2DBitmapBrush::Attach](#attach)|Bude k obrazci existujících prostředků rozhraní pro objekt|
|[CD2DBitmapBrush::Create](#create)|Vytvoří cd2dbitmapbrush –. (Přepíše [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DBitmapBrush::Destroy](#destroy)|Odstraní objekt cd2dbitmapbrush –. (Přepíše [CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|
|[CD2DBitmapBrush::detach](#detach)|Odpojí prostředků rozhraní z objektu|
|[CD2DBitmapBrush::Get](#get)|Vrátí ID2D1BitmapBrush rozhraní|
|[CD2DBitmapBrush::GetBitmap](#getbitmap)|Získá zdroj rastrového obrázku, který používá tento štětce k vykreslení|
|[CD2DBitmapBrush::GetExtendModeX](#getextendmodex)|Získá metodu, pomocí kterého štětec vodorovně dlaždice těchto oblastí, které přesahují za jeho rastrový obrázek|
|[CD2DBitmapBrush::GetExtendModeY](#getextendmodey)|Získá metodu, pomocí kterého štětec dlaždice svisle těchto oblastí, které přesahují za jeho rastrový obrázek|
|[CD2DBitmapBrush::GetInterpolationMode](#getinterpolationmode)|Získá metodu interpolace použita, pokud je škálovat nebo otočit rastrový obrázek štětec|
|[CD2DBitmapBrush::SetBitmap](#setbitmap)|Určuje zdroj rastrového obrázku, který tento štětce používá k vykreslení|
|[CD2DBitmapBrush::SetExtendModeX](#setextendmodex)|Určuje, jak štětec vodorovně dlaždice těchto oblastí, které přesahují za jeho rastrový obrázek|
|[CD2DBitmapBrush::SetExtendModeY](#setextendmodey)|Určuje, jak štětec dlaždice svisle těchto oblastí, které přesahují za jeho rastrový obrázek|
|[CD2DBitmapBrush::SetInterpolationMode](#setinterpolationmode)|Určuje režim interpolace použita, pokud je škálovat nebo otočit rastrový obrázek štětec|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CD2DBitmapBrush::CommonInit](#commoninit)|Inicializuje objekt|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CD2DBitmapBrush::Operator ID2D1BitmapBrush *](#operator_id2d1bitmapbrush_star)|Vrátí ID2D1BitmapBrush rozhraní|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CD2DBitmapBrush::m_pBitmap](#m_pbitmap)|Uchovává ukazatel na objekt cd2dbitmap –.|
|[CD2DBitmapBrush::m_pBitmapBrush](#m_pbitmapbrush)|Uchovává ukazatel na objekt ID2D1BitmapBrush.|
|[CD2DBitmapBrush::m_pBitmapBrushProperties](#m_pbitmapbrushproperties)|Bitmap – vlastnosti štětce.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cd2dresource –](../../mfc/reference/cd2dresource-class.md)

[Cd2dbrush –](../../mfc/reference/cd2dbrush-class.md)

`CD2DBitmapBrush`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

##  <a name="dtor"></a>  Cd2dbitmapbrush –:: ~ cd2dbitmapbrush –

Destruktor. Volá se, když se likviduje štětce objektu D2D rastrového obrázku.

```
virtual ~CD2DBitmapBrush();
```

##  <a name="attach"></a>  CD2DBitmapBrush::Attach

Bude k obrazci existujících prostředků rozhraní pro objekt

```
void Attach(ID2D1BitmapBrush* pResource);
```

### <a name="parameters"></a>Parametry

*pResource*<br/>
Rozhraní existující prostředek. Nesmí být NULL.

##  <a name="cd2dbitmapbrush"></a>  CD2DBitmapBrush::CD2DBitmapBrush

Vytvoří objekt cd2dbitmapbrush –.

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
Ukazatel na cíl vykreslování.

*pBitmapBrushProperties*<br/>
Ukazatel na režimy rozšířit a režim interpolace štětce rastrového obrázku.

*pBrushProperties*<br/>
Ukazatel na krytí a transformace štětce.

*bAutoDestroy*<br/>
Označuje, že bude objekt zničen. vlastník (pParentTarget).

*uiResID*<br/>
Číslo ID prostředku prostředku.

*lpszType*<br/>
Ukazatel na řetězec zakončený hodnotou null, který obsahuje typ prostředku.

*sizeDest*<br/>
Velikost cílové bitmapy.

*lpszImagePath*<br/>
Ukazatel na řetězec zakončený hodnotou null, který obsahuje název souboru.

##  <a name="commoninit"></a>  CD2DBitmapBrush::CommonInit

Inicializuje objekt

```
void CommonInit(D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties);
```

### <a name="parameters"></a>Parametry

*pBitmapBrushProperties*<br/>
Ukazatel na vlastnosti štětce rastrového obrázku.

##  <a name="create"></a>  CD2DBitmapBrush::Create

Vytvoří cd2dbitmapbrush –.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Ukazatel na cíl vykreslování.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu S_OK. V opačném případě vrátí kód chyby HRESULT.

##  <a name="destroy"></a>  CD2DBitmapBrush::Destroy

Odstraní objekt cd2dbitmapbrush –.

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DBitmapBrush::detach

Odpojí prostředků rozhraní z objektu

```
ID2D1BitmapBrush* Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní odpojit prostředek.

##  <a name="get"></a>  CD2DBitmapBrush::Get

Vrátí ID2D1BitmapBrush rozhraní

```
ID2D1BitmapBrush* Get();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1BitmapBrush nebo hodnota NULL, pokud objekt ještě není inicializován.

##  <a name="getbitmap"></a>  CD2DBitmapBrush::GetBitmap

Získá zdroj rastrového obrázku, který používá tento štětce k vykreslení

```
CD2DBitmap* GetBitmap();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt cd2dbitmap – nebo hodnota NULL, pokud objekt ještě není inicializován.

##  <a name="getextendmodex"></a>  CD2DBitmapBrush::GetExtendModeX

Získá metodu, pomocí kterého štětec vodorovně dlaždice těchto oblastí, které přesahují za jeho rastrový obrázek

```
D2D1_EXTEND_MODE GetExtendModeX() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která určuje, jak štětec vodorovně dlaždice těchto oblastí, které přesahují za jeho rastrový obrázek

##  <a name="getextendmodey"></a>  CD2DBitmapBrush::GetExtendModeY

Získá metodu, pomocí kterého štětec dlaždice svisle těchto oblastí, které přesahují za jeho rastrový obrázek

```
D2D1_EXTEND_MODE GetExtendModeY() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která určuje, jak štětec dlaždice svisle těchto oblastí, které přesahují za jeho rastrový obrázek

##  <a name="getinterpolationmode"></a>  CD2DBitmapBrush::GetInterpolationMode

Získá metodu interpolace použita, pokud je škálovat nebo otočit rastrový obrázek štětec

```
D2D1_BITMAP_INTERPOLATION_MODE GetInterpolationMode() const;
```

### <a name="return-value"></a>Návratová hodnota

Metodu interpolace použita, pokud je škálovat nebo otočit rastrový obrázek štětec

##  <a name="m_pbitmap"></a>  CD2DBitmapBrush::m_pBitmap

Uchovává ukazatel na objekt cd2dbitmap –.

```
CD2DBitmap* m_pBitmap;
```

##  <a name="m_pbitmapbrush"></a>  CD2DBitmapBrush::m_pBitmapBrush

Uchovává ukazatel na objekt ID2D1BitmapBrush.

```
ID2D1BitmapBrush* m_pBitmapBrush;
```

##  <a name="m_pbitmapbrushproperties"></a>  CD2DBitmapBrush::m_pBitmapBrushProperties

Bitmap – vlastnosti štětce.

```
D2D1_BITMAP_BRUSH_PROPERTIES* m_pBitmapBrushProperties;
```

##  <a name="operator_id2d1bitmapbrush_star"></a>  CD2DBitmapBrush::Operator ID2D1BitmapBrush *

Vrátí ID2D1BitmapBrush rozhraní

```
operator ID2D1BitmapBrush*();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1BitmapBrush nebo hodnota NULL, pokud objekt ještě není inicializován.

##  <a name="setbitmap"></a>  CD2DBitmapBrush::SetBitmap

Určuje zdroj rastrového obrázku, který tento štětce používá k vykreslení

```
void SetBitmap(CD2DBitmap* pBitmap);
```

### <a name="parameters"></a>Parametry

*pBitmap*<br/>
Zdroj rastrového obrázku používá štětec

##  <a name="setextendmodex"></a>  CD2DBitmapBrush::SetExtendModeX

Určuje, jak štětec vodorovně dlaždice těchto oblastí, které přesahují za jeho rastrový obrázek

```
void SetExtendModeX(D2D1_EXTEND_MODE extendModeX);
```

### <a name="parameters"></a>Parametry

*extendModeX*<br/>
Hodnota, která určuje, jak štětec vodorovně dlaždice těchto oblastí, které přesahují za jeho rastrový obrázek

##  <a name="setextendmodey"></a>  CD2DBitmapBrush::SetExtendModeY

Určuje, jak štětec dlaždice svisle těchto oblastí, které přesahují za jeho rastrový obrázek

```
void SetExtendModeY(D2D1_EXTEND_MODE extendModeY);
```

### <a name="parameters"></a>Parametry

*extendModeY*<br/>
Hodnota, která určuje, jak štětec dlaždice svisle těchto oblastí, které přesahují za jeho rastrový obrázek

##  <a name="setinterpolationmode"></a>  CD2DBitmapBrush::SetInterpolationMode

Určuje režim interpolace použita, pokud je škálovat nebo otočit rastrový obrázek štětec

```
void SetInterpolationMode(D2D1_BITMAP_INTERPOLATION_MODE interpolationMode);
```

### <a name="parameters"></a>Parametry

*interpolationMode*<br/>
Režim interpolace použita, pokud je škálovat nebo otočit rastrový obrázek štětec

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
