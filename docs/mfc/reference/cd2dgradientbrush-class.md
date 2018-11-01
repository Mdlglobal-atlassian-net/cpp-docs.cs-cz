---
title: Cd2dgradientbrush – třída
ms.date: 11/04/2016
f1_keywords:
- CD2DGradientBrush
- AFXRENDERTARGET/CD2DGradientBrush
- AFXRENDERTARGET/CD2DGradientBrush::CD2DGradientBrush
- AFXRENDERTARGET/CD2DGradientBrush::Destroy
- AFXRENDERTARGET/CD2DGradientBrush::m_arGradientStops
- AFXRENDERTARGET/CD2DGradientBrush::m_colorInterpolationGamma
- AFXRENDERTARGET/CD2DGradientBrush::m_extendMode
- AFXRENDERTARGET/CD2DGradientBrush::m_pGradientStops
helpviewer_keywords:
- CD2DGradientBrush [MFC], CD2DGradientBrush
- CD2DGradientBrush [MFC], Destroy
- CD2DGradientBrush [MFC], m_arGradientStops
- CD2DGradientBrush [MFC], m_colorInterpolationGamma
- CD2DGradientBrush [MFC], m_extendMode
- CD2DGradientBrush [MFC], m_pGradientStops
ms.assetid: 5bf133e6-16b7-4e3a-845d-0ce63fafe5ec
ms.openlocfilehash: bc26dd495fb9bd91aaf5eac192011faad80bc668
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50506051"
---
# <a name="cd2dgradientbrush-class"></a>Cd2dgradientbrush – třída

Základní třída cd2dlineargradientbrush – a cd2dradialgradientbrush – třídy.

## <a name="syntax"></a>Syntaxe

```
class CD2DGradientBrush : public CD2DBrush;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CD2DGradientBrush::CD2DGradientBrush](#cd2dgradientbrush)|Vytvoří objekt cd2dgradientbrush –.|
|[Cd2dgradientbrush –:: ~ cd2dgradientbrush –](#cd2dgradientbrush__~cd2dgradientbrush)|Destruktor. Volá se, když se likviduje objektu D2D štětce přechodu.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CD2DGradientBrush::Destroy](#destroy)|Odstraní objekt cd2dgradientbrush –. (Přepíše [CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CD2DGradientBrush::m_arGradientStops](#m_argradientstops)|Pole struktur D2D1_GRADIENT_STOP.|
|[CD2DGradientBrush::m_colorInterpolationGamma](#m_colorinterpolationgamma)|Místo barvou, které se provádí interpolaci mezi Přechodové zarážky.|
|[CD2DGradientBrush::m_extendMode](#m_extendmode)|Chování přechodu mimo rozsah [0,1] normalizovaná.|
|[CD2DGradientBrush::m_pGradientStops](#m_pgradientstops)|Ukazatel na pole D2D1_GRADIENT_STOP struktur.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cd2dresource –](../../mfc/reference/cd2dresource-class.md)

[Cd2dbrush –](../../mfc/reference/cd2dbrush-class.md)

`CD2DGradientBrush`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

##  <a name="_dtorcd2dgradientbrush"></a>  Cd2dgradientbrush –:: ~ cd2dgradientbrush –

Destruktor. Volá se, když se likviduje objektu D2D štětce přechodu.

```
virtual ~CD2DGradientBrush();
```

##  <a name="cd2dgradientbrush"></a>  CD2DGradientBrush::CD2DGradientBrush

Vytvoří objekt cd2dgradientbrush –.

```
CD2DGradientBrush(
    CRenderTarget* pParentTarget,
    const D2D1_GRADIENT_STOP* gradientStops,
    UINT gradientStopsCount,
    D2D1_GAMMA colorInterpolationGamma = D2D1_GAMMA_2_2,
    D2D1_EXTEND_MODE extendMode = D2D1_EXTEND_MODE_CLAMP,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*pParentTarget*<br/>
Ukazatel na cíl vykreslování.

*gradientStops*<br/>
Ukazatel na pole D2D1_GRADIENT_STOP struktur.

*gradientStopsCount*<br/>
Hodnota větší než nebo rovna 1, která určuje počet Přechodové zarážky v poli gradientStops.

*colorInterpolationGamma*<br/>
Místo barvou, které se provádí interpolaci mezi Přechodové zarážky.

*extendMode*<br/>
Chování přechodu mimo rozsah [0,1] normalizovaná.

*pBrushProperties*<br/>
Ukazatel na krytí a transformace štětce.

*bAutoDestroy*<br/>
Označuje, že bude objekt zničen. vlastník (pParentTarget).

##  <a name="destroy"></a>  CD2DGradientBrush::Destroy

Odstraní objekt cd2dgradientbrush –.

```
virtual void Destroy();
```

##  <a name="m_argradientstops"></a>  CD2DGradientBrush::m_arGradientStops

Pole struktur D2D1_GRADIENT_STOP.

```
CArray<D2D1_GRADIENT_STOP, D2D1_GRADIENT_STOP> m_arGradientStops;
```

##  <a name="m_colorinterpolationgamma"></a>  CD2DGradientBrush::m_colorInterpolationGamma

Místo barvou, které se provádí interpolaci mezi Přechodové zarážky.

```
D2D1_GAMMA m_colorInterpolationGamma;
```

##  <a name="m_extendmode"></a>  CD2DGradientBrush::m_extendMode

Chování přechodu mimo rozsah [0,1] normalizovaná.

```
D2D1_EXTEND_MODE m_extendMode;
```

##  <a name="m_pgradientstops"></a>  CD2DGradientBrush::m_pGradientStops

Ukazatel na pole D2D1_GRADIENT_STOP struktur.

```
ID2D1GradientStopCollection* m_pGradientStops;
```

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
