---
title: Třída CD2DLinearGradientBrush
ms.date: 11/04/2016
f1_keywords:
- CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush::CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush::Attach
- AFXRENDERTARGET/CD2DLinearGradientBrush::Create
- AFXRENDERTARGET/CD2DLinearGradientBrush::Destroy
- AFXRENDERTARGET/CD2DLinearGradientBrush::Detach
- AFXRENDERTARGET/CD2DLinearGradientBrush::Get
- AFXRENDERTARGET/CD2DLinearGradientBrush::GetEndPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::GetStartPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::SetEndPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::SetStartPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::m_LinearGradientBrushProperties
- AFXRENDERTARGET/CD2DLinearGradientBrush::m_pLinearGradientBrush
helpviewer_keywords:
- CD2DLinearGradientBrush [MFC], CD2DLinearGradientBrush
- CD2DLinearGradientBrush [MFC], Attach
- CD2DLinearGradientBrush [MFC], Create
- CD2DLinearGradientBrush [MFC], Destroy
- CD2DLinearGradientBrush [MFC], Detach
- CD2DLinearGradientBrush [MFC], Get
- CD2DLinearGradientBrush [MFC], GetEndPoint
- CD2DLinearGradientBrush [MFC], GetStartPoint
- CD2DLinearGradientBrush [MFC], SetEndPoint
- CD2DLinearGradientBrush [MFC], SetStartPoint
- CD2DLinearGradientBrush [MFC], m_LinearGradientBrushProperties
- CD2DLinearGradientBrush [MFC], m_pLinearGradientBrush
ms.assetid: d4be9ff9-0ea8-45e6-9b8d-f3bc5673cbac
ms.openlocfilehash: 6c488d66962f26b6ca9b8c63cb387fc75191085a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369200"
---
# <a name="cd2dlineargradientbrush-class"></a>Třída CD2DLinearGradientBrush

Obálka pro ID2D1LinearGradientBrush.

## <a name="syntax"></a>Syntaxe

```
class CD2DLinearGradientBrush : public CD2DGradientBrush;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DLinearGradientBrush::CD2DLinearGradientBrush](#cd2dlineargradientbrush)|Vytvoří objekt CD2DLinearGradientBrush.|
|[CD2DLinearGradientBrush::~CD2DLinearGradientBrush](#_dtorcd2dlineargradientbrush)|Destruktor. Nazývá se při zničení objektu stopy lineárního přechodu D2D.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DLinearGradientBrush::Připojit](#attach)|Připojí k objektu existující rozhraní prostředků.|
|[CD2DLinearGradientBrush::Vytvořit](#create)|Vytvoří cd2DLinearGradientBrush. (Přepíše [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DLinearGradientBrush::Destroy](#destroy)|Zničí objekt CD2DLinearGradientBrush. (Přepíše [CD2DGradientBrush::Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy).)|
|[CD2DLinearGradientBrush::Detach](#detach)|Odpojí rozhraní prostředků od objektu.|
|[CD2DLinearGradientBrush::Získat](#get)|Vrátí rozhraní ID2D1LinearGradientBrush.|
|[CD2DLinearGradientBrush::GetendPoint](#getendpoint)|Načte koncové souřadnice lineárního přechodu.|
|[CD2DLinearGradientBrush::GetStartPoint](#getstartpoint)|Načte počáteční souřadnice lineárního přechodu.|
|[CD2DLinearGradientBrush::Setendpoint](#setendpoint)|Nastaví koncové souřadnice lineárního přechodu v souřadnicovém prostoru stopy.|
|[CD2DLinearGradientBrush::SetStartPoint](#setstartpoint)|Nastaví počáteční souřadnice lineárního přechodu v souřadnicovém prostoru stopy.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DLinearGradientBrush::operátor ID2D1LinearGradientBrush*](#operator_id2d1lineargradientbrush_star)|Vrátí rozhraní ID2D1LinearGradientBrush.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DLinearGradientBrush::m_LinearGradientBrushProperties](#m_lineargradientbrushproperties)|Počáteční a koncový bod přechodu.|
|[CD2DLinearGradientBrush::m_pLinearGradientBrush](#m_plineargradientbrush)|Ukazatel na ID2D1LinearGradientBrush.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Zdroj CD2D](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

[CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)

`CD2DLinearGradientBrush`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

## <a name="cd2dlineargradientbrushcd2dlineargradientbrush"></a><a name="_dtorcd2dlineargradientbrush"></a>CD2DLinearGradientBrush::~CD2DLinearGradientBrush

Destruktor. Nazývá se při zničení objektu stopy lineárního přechodu D2D.

```
virtual ~CD2DLinearGradientBrush();
```

## <a name="cd2dlineargradientbrushattach"></a><a name="attach"></a>CD2DLinearGradientBrush::Připojit

Připojí k objektu existující rozhraní prostředků.

```
void Attach(ID2D1LinearGradientBrush* pResource);
```

### <a name="parameters"></a>Parametry

*pZdroj*<br/>
Existující rozhraní prostředků. Nelze získat hodnotu NULL.

## <a name="cd2dlineargradientbrushcd2dlineargradientbrush"></a><a name="cd2dlineargradientbrush"></a>CD2DLinearGradientBrush::CD2DLinearGradientBrush

Vytvoří objekt CD2DLinearGradientBrush.

```
CD2DLinearGradientBrush(
    CRenderTarget* pParentTarget,
    const D2D1_GRADIENT_STOP* gradientStops,
    UINT gradientStopsCount,
    D2D1_LINEAR_GRADIENT_BRUSH_PROPERTIES LinearGradientBrushProperties,
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

*Vlastnosti LinearGradientBrushProperties*<br/>
Počáteční a koncový bod přechodu.

*barvaInterpolaceGamma*<br/>
Prostor, ve kterém se provádí interpolace barev mezi přechodem.

*extendMode*<br/>
Chování přechodu mimo [0,1] normalizované oblasti.

*pVlastnosti brushu*<br/>
Ukazatel na krytí a transformaci stopy.

*bAutoDestroy*<br/>
Označuje, že objekt bude zničen vlastníkem (pParentTarget).

## <a name="cd2dlineargradientbrushcreate"></a><a name="create"></a>CD2DLinearGradientBrush::Vytvořit

Vytvoří cd2DLinearGradientBrush.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parametry

*pRenderTarget*<br/>
Ukazatel na cíl vykreslení.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. V opačném případě vrátí kód chyby HRESULT.

## <a name="cd2dlineargradientbrushdestroy"></a><a name="destroy"></a>CD2DLinearGradientBrush::Destroy

Zničí objekt CD2DLinearGradientBrush.

```
virtual void Destroy();
```

## <a name="cd2dlineargradientbrushdetach"></a><a name="detach"></a>CD2DLinearGradientBrush::Detach

Odpojí rozhraní prostředků od objektu.

```
ID2D1LinearGradientBrush* Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní odpojeného prostředku.

## <a name="cd2dlineargradientbrushget"></a><a name="get"></a>CD2DLinearGradientBrush::Získat

Vrátí rozhraní ID2D1LinearGradientBrush.

```
ID2D1LinearGradientBrush* Get();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1LinearGradientBrush nebo NULL, pokud objekt ještě není inicializován.

## <a name="cd2dlineargradientbrushgetendpoint"></a><a name="getendpoint"></a>CD2DLinearGradientBrush::GetendPoint

Načte koncové souřadnice lineárního přechodu.

```
CD2DPointF GetEndPoint() const;
```

### <a name="return-value"></a>Návratová hodnota

Koncové dvojrozměrné souřadnice lineárního přechodu v souřadnicovém prostoru stopy

## <a name="cd2dlineargradientbrushgetstartpoint"></a><a name="getstartpoint"></a>CD2DLinearGradientBrush::GetStartPoint

Načte počáteční souřadnice lineárního přechodu.

```
CD2DPointF GetStartPoint() const;
```

### <a name="return-value"></a>Návratová hodnota

Počáteční dvojrozměrné souřadnice lineárního gradientu v souřadnicovém prostoru stopy

## <a name="cd2dlineargradientbrushm_lineargradientbrushproperties"></a><a name="m_lineargradientbrushproperties"></a>CD2DLinearGradientBrush::m_LinearGradientBrushProperties

Počáteční a koncový bod přechodu.

```
D2D1_LINEAR_GRADIENT_BRUSH_PROPERTIES m_LinearGradientBrushProperties;
```

## <a name="cd2dlineargradientbrushm_plineargradientbrush"></a><a name="m_plineargradientbrush"></a>CD2DLinearGradientBrush::m_pLinearGradientBrush

Ukazatel na ID2D1LinearGradientBrush.

```
ID2D1LinearGradientBrush* m_pLinearGradientBrush;
```

## <a name="cd2dlineargradientbrushoperator-id2d1lineargradientbrush"></a><a name="operator_id2d1lineargradientbrush_star"></a>CD2DLinearGradientBrush::operátor ID2D1LinearGradientBrush*

Vrátí rozhraní ID2D1LinearGradientBrush.

```
operator ID2D1LinearGradientBrush*();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1LinearGradientBrush nebo NULL, pokud objekt ještě není inicializován.

## <a name="cd2dlineargradientbrushsetendpoint"></a><a name="setendpoint"></a>CD2DLinearGradientBrush::Setendpoint

Nastaví koncové souřadnice lineárního přechodu v souřadnicovém prostoru stopy.

```
void SetEndPoint(CD2DPointF point);
```

### <a name="parameters"></a>Parametry

*Bod*<br/>
Koncové dvojrozměrné souřadnice lineárního přechodu v souřadnicovém prostoru stopy

## <a name="cd2dlineargradientbrushsetstartpoint"></a><a name="setstartpoint"></a>CD2DLinearGradientBrush::SetStartPoint

Nastaví počáteční souřadnice lineárního přechodu v souřadnicovém prostoru stopy.

```
void SetStartPoint(CD2DPointF point);
```

### <a name="parameters"></a>Parametry

*Bod*<br/>
Počáteční dvojrozměrné souřadnice lineárního gradientu v souřadnicovém prostoru stopy

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
