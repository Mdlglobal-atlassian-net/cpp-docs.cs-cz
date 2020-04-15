---
title: CD2DRadialGradientBrush – třída
ms.date: 11/04/2016
f1_keywords:
- CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::Attach
- AFXRENDERTARGET/CD2DRadialGradientBrush::Create
- AFXRENDERTARGET/CD2DRadialGradientBrush::Destroy
- AFXRENDERTARGET/CD2DRadialGradientBrush::Detach
- AFXRENDERTARGET/CD2DRadialGradientBrush::Get
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetCenter
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetGradientOriginOffset
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetRadiusX
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetRadiusY
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetCenter
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetGradientOriginOffset
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetRadiusX
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetRadiusY
- AFXRENDERTARGET/CD2DRadialGradientBrush::m_pRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::m_RadialGradientBrushProperties
helpviewer_keywords:
- CD2DRadialGradientBrush [MFC], CD2DRadialGradientBrush
- CD2DRadialGradientBrush [MFC], Attach
- CD2DRadialGradientBrush [MFC], Create
- CD2DRadialGradientBrush [MFC], Destroy
- CD2DRadialGradientBrush [MFC], Detach
- CD2DRadialGradientBrush [MFC], Get
- CD2DRadialGradientBrush [MFC], GetCenter
- CD2DRadialGradientBrush [MFC], GetGradientOriginOffset
- CD2DRadialGradientBrush [MFC], GetRadiusX
- CD2DRadialGradientBrush [MFC], GetRadiusY
- CD2DRadialGradientBrush [MFC], SetCenter
- CD2DRadialGradientBrush [MFC], SetGradientOriginOffset
- CD2DRadialGradientBrush [MFC], SetRadiusX
- CD2DRadialGradientBrush [MFC], SetRadiusY
- CD2DRadialGradientBrush [MFC], m_pRadialGradientBrush
- CD2DRadialGradientBrush [MFC], m_RadialGradientBrushProperties
ms.assetid: 6c76d84a-d831-4ee2-96f1-82c1f5b0d6a9
ms.openlocfilehash: aca9606271040e5c5c9aee81be0a08b64cf2bab7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369134"
---
# <a name="cd2dradialgradientbrush-class"></a>CD2DRadialGradientBrush – třída

Obálka pro ID2D1RadialGradientBrush.

## <a name="syntax"></a>Syntaxe

```
class CD2DRadialGradientBrush : public CD2DGradientBrush;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DRadialGradientBrush::CD2DRadialGradientBrush](#cd2dradialgradientbrush)|Vytvoří objekt CD2DLinearGradientBrush.|
|[CD2DRadialGradientBrush::~CD2DRadialGradientBrush](#_dtorcd2dradialgradientbrush)|Destruktor. Nazývá se při zničení objektu stopy kruhového přechodu D2D.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DRadialGradientBrush::Připojit](#attach)|Připojí k objektu existující rozhraní prostředků.|
|[CD2DRadialGradientBrush::Vytvořit](#create)|Vytvoří CD2DRadialGradientBrush. (Přepíše [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DRadialGradientBrush::Destroy](#destroy)|Zničí objekt CD2DRadialGradientBrush. (Přepíše [CD2DGradientBrush::Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy).)|
|[CD2DRadialGradientBrush::Detach](#detach)|Odpojí rozhraní prostředků od objektu.|
|[CD2DRadialGradientBrush::Získat](#get)|Vrátí rozhraní ID2D1RadialGradientBrush.|
|[CD2DRadialGradientBrush::GetCenter](#getcenter)|Načte střed elipsy přechodu.|
|[CD2DRadialGradientBrush::GetGradientOriginOffset](#getgradientoriginoffset)|Načte posun počátku přechodu vzhledem ke středu elipsy přechodu.|
|[CD2DRadialGradientBrush::GetRadiusX](#getradiusx)|Načte poloměr x elipsy přechodu.|
|[CD2DRadialGradientBrush::GetRadiusY](#getradiusy)|Načte poloměr y elipsy přechodu.|
|[CD2DRadialGradientBrush::SetCenter](#setcenter)|Určuje střed elipsy přechodu v souřadnicovém prostoru stopy.|
|[CD2DRadialGradientBrush::SetGradientOriginOffset](#setgradientoriginoffset)|Určuje odsazení počátku přechodu vzhledem ke středu elipsy přechodu.|
|[CD2DRadialGradientBrush::SetRadiusX](#setradiusx)|Určuje x-poloměr elipsy přechodu v souřadnicovém prostoru stopy.|
|[CD2DRadialGradientBrush::SetRadiusY](#setradiusy)|Určuje poloměr y elipsy přechodu v souřadnicovém prostoru stopy.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DRadialGradientBrush::operátor ID2D1RadialGradientBrush*](#operator_id2d1radialgradientbrush_star)|Vrátí rozhraní ID2D1RadialGradientBrush.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DRadialGradientBrush::m_pRadialGradientBrush](#m_pradialgradientbrush)|Ukazatel na ID2D1RadialGradientBrush.|
|[CD2DRadialGradientBrush::m_RadialGradientBrushProperties](#m_radialgradientbrushproperties)|Střed, odsazení počátku přechodu a poloměr x a poloměr y přechodu stopy.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Zdroj CD2D](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

[CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)

`CD2DRadialGradientBrush`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

## <a name="cd2dradialgradientbrushcd2dradialgradientbrush"></a><a name="_dtorcd2dradialgradientbrush"></a>CD2DRadialGradientBrush::~CD2DRadialGradientBrush

Destruktor. Nazývá se při zničení objektu stopy kruhového přechodu D2D.

```
virtual ~CD2DRadialGradientBrush();
```

## <a name="cd2dradialgradientbrushattach"></a><a name="attach"></a>CD2DRadialGradientBrush::Připojit

Připojí k objektu existující rozhraní prostředků.

```
void Attach(ID2D1RadialGradientBrush* pResource);
```

### <a name="parameters"></a>Parametry

*pZdroj*<br/>
Existující rozhraní prostředků. Nelze získat hodnotu NULL.

## <a name="cd2dradialgradientbrushcd2dradialgradientbrush"></a><a name="cd2dradialgradientbrush"></a>CD2DRadialGradientBrush::CD2DRadialGradientBrush

Vytvoří objekt CD2DLinearGradientBrush.

```
CD2DRadialGradientBrush(
    CRenderTarget* pParentTarget,
    const D2D1_GRADIENT_STOP* gradientStops,
    UINT gradientStopsCount,
    D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES RadialGradientBrushProperties,
    D2D1_GAMMA colorInterpolationGamma = D2D1_GAMMA_2_2,
    D2D1_EXTEND_MODE extendMode = D2D1_EXTEND_MODE_CLAMP,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Ukazatel na cíl vykreslení.

*přechodové zarážky*<br/>
Ukazatel na pole D2D1_GRADIENT_STOP struktur.

*gradientStopsCount*<br/>
Hodnota větší nebo rovna 1, která určuje počet zarážek přechodu v poli gradientStops.

*Vlastnosti radiálního gradientu*<br/>
Střed, odsazení počátku přechodu a poloměr x a poloměr y přechodu stopy.

*barvaInterpolaceGamma*<br/>
Prostor, ve kterém se provádí interpolace barev mezi přechodem.

*extendMode*<br/>
Chování přechodu mimo [0,1] normalizované oblasti.

*pVlastnosti brushu*<br/>
Ukazatel na krytí a transformaci stopy.

*bAutoDestroy*<br/>
Označuje, že objekt bude zničen vlastníkem (pParentTarget).

## <a name="cd2dradialgradientbrushcreate"></a><a name="create"></a>CD2DRadialGradientBrush::Vytvořit

Vytvoří CD2DRadialGradientBrush.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Ukazatel na cíl vykreslení.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. V opačném případě vrátí kód chyby HRESULT.

## <a name="cd2dradialgradientbrushdestroy"></a><a name="destroy"></a>CD2DRadialGradientBrush::Destroy

Zničí objekt CD2DRadialGradientBrush.

```
virtual void Destroy();
```

## <a name="cd2dradialgradientbrushdetach"></a><a name="detach"></a>CD2DRadialGradientBrush::Detach

Odpojí rozhraní prostředků od objektu.

```
ID2D1RadialGradientBrush* Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní odpojeného prostředku.

## <a name="cd2dradialgradientbrushget"></a><a name="get"></a>CD2DRadialGradientBrush::Získat

Vrátí rozhraní ID2D1RadialGradientBrush.

```
ID2D1RadialGradientBrush* Get();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1RadialGradientBrush nebo NULL, pokud objekt ještě není inicializován.

## <a name="cd2dradialgradientbrushgetcenter"></a><a name="getcenter"></a>CD2DRadialGradientBrush::GetCenter

Načte střed elipsy přechodu.

```
CD2DPointF GetCenter() const;
```

### <a name="return-value"></a>Návratová hodnota

Střed elipsy přechodu. Tato hodnota je vyjádřena v souřadnicovém prostoru stopy.

## <a name="cd2dradialgradientbrushgetgradientoriginoffset"></a><a name="getgradientoriginoffset"></a>CD2DRadialGradientBrush::GetGradientOriginOffset

Načte posun počátku přechodu vzhledem ke středu elipsy přechodu.

```
CD2DPointF GetGradientOriginOffset() const;
```

### <a name="return-value"></a>Návratová hodnota

Odsazení počátku přechodu od středu elipsy přechodu. Tato hodnota je vyjádřena v souřadnicovém prostoru stopy.

## <a name="cd2dradialgradientbrushgetradiusx"></a><a name="getradiusx"></a>CD2DRadialGradientBrush::GetRadiusX

Načte poloměr x elipsy přechodu.

```
FLOAT GetRadiusX() const;
```

### <a name="return-value"></a>Návratová hodnota

X-poloměr elipsy přechodu. Tato hodnota je vyjádřena v souřadnicovém prostoru stopy.

## <a name="cd2dradialgradientbrushgetradiusy"></a><a name="getradiusy"></a>CD2DRadialGradientBrush::GetRadiusY

Načte poloměr y elipsy přechodu.

```
FLOAT GetRadiusY() const;
```

### <a name="return-value"></a>Návratová hodnota

Poloměr y elipsy přechodu. Tato hodnota je vyjádřena v souřadnicovém prostoru stopy.

## <a name="cd2dradialgradientbrushm_pradialgradientbrush"></a><a name="m_pradialgradientbrush"></a>CD2DRadialGradientBrush::m_pRadialGradientBrush

Ukazatel na ID2D1RadialGradientBrush.

```
ID2D1RadialGradientBrush* m_pRadialGradientBrush;
```

## <a name="cd2dradialgradientbrushm_radialgradientbrushproperties"></a><a name="m_radialgradientbrushproperties"></a>CD2DRadialGradientBrush::m_RadialGradientBrushProperties

Střed, odsazení počátku přechodu a poloměr x a poloměr y přechodu stopy.

```
D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES m_RadialGradientBrushProperties;
```

## <a name="cd2dradialgradientbrushoperator-id2d1radialgradientbrush"></a><a name="operator_id2d1radialgradientbrush_star"></a>CD2DRadialGradientBrush::operátor ID2D1RadialGradientBrush*

Vrátí rozhraní ID2D1RadialGradientBrush.

```
operator ID2D1RadialGradientBrush*();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1RadialGradientBrush nebo NULL, pokud objekt ještě není inicializován.

## <a name="cd2dradialgradientbrushsetcenter"></a><a name="setcenter"></a>CD2DRadialGradientBrush::SetCenter

Určuje střed elipsy přechodu v souřadnicovém prostoru stopy.

```
void SetCenter(CD2DPointF point);
```

### <a name="parameters"></a>Parametry

*Bod*<br/>
Střed elipsy přechodu v souřadnicovém prostoru stopy

## <a name="cd2dradialgradientbrushsetgradientoriginoffset"></a><a name="setgradientoriginoffset"></a>CD2DRadialGradientBrush::SetGradientOriginOffset

Určuje odsazení počátku přechodu vzhledem ke středu elipsy přechodu.

```
void SetGradientOriginOffset(CD2DPointF gradientOriginOffset);
```

### <a name="parameters"></a>Parametry

*gradientOriginOffset*<br/>
Odsazení počátku přechodu od středu elipsy přechodu

## <a name="cd2dradialgradientbrushsetradiusx"></a><a name="setradiusx"></a>CD2DRadialGradientBrush::SetRadiusX

Určuje x-poloměr elipsy přechodu v souřadnicovém prostoru stopy.

```
void SetRadiusX(FLOAT radiusX);
```

### <a name="parameters"></a>Parametry

*radiusX*<br/>
X-poloměr elipsy přechodu. Tato hodnota je v souřadnicovém prostoru stopy.

## <a name="cd2dradialgradientbrushsetradiusy"></a><a name="setradiusy"></a>CD2DRadialGradientBrush::SetRadiusY

Určuje poloměr y elipsy přechodu v souřadnicovém prostoru stopy.

```
void SetRadiusY(FLOAT radiusY);
```

### <a name="parameters"></a>Parametry

*radiusY*<br/>
Poloměr y elipsy přechodu. Tato hodnota je v souřadnicovém prostoru stopy.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
