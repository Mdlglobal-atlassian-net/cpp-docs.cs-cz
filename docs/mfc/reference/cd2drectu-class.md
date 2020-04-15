---
title: CD2DRectU – třída
ms.date: 11/04/2016
f1_keywords:
- CD2DRectU
- AFXRENDERTARGET/CD2DRectU
- AFXRENDERTARGET/CD2DRectU::CD2DRectU
- AFXRENDERTARGET/CD2DRectU::IsNull
helpviewer_keywords:
- CD2DRectU [MFC], CD2DRectU
- CD2DRectU [MFC], IsNull
ms.assetid: a62f17d1-011d-4867-8f51-fd7e7c00561d
ms.openlocfilehash: 26e647ae01a498a6ad8ca2d7c866f33b01910881
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369101"
---
# <a name="cd2drectu-class"></a>CD2DRectU – třída

Obálka pro `D2D1_RECT_U`.

## <a name="syntax"></a>Syntaxe

```
class CD2DRectU : public D2D1_RECT_U;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DRectU::CD2DRectU](#cd2drectu)|Přetíženo. Vytvoří `CD2DRectU` objekt z `D2D1_RECT_U` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DRectU::IsNull](#isnull)|Vrátí **logickou** hodnotu, která označuje, zda výraz neobsahuje žádná platná data (NULL).|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DRectU::operátor CRect](#operator_crect)|Převede `CD2DRectU` `CRect` na objekt.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`D2D1_RECT_U`

`CD2DRectU`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

## <a name="cd2drectucd2drectu"></a><a name="cd2drectu"></a>CD2DRectU::CD2DRectU

Vytvoří objekt CD2DRectU z objektu CRect.

```
CD2DRectU(const CRect& rect);
CD2DRectU(const D2D1_RECT_U& rect);
CD2DRectU(const D2D1_RECT_U* rect);

CD2DRectU(
    UINT32 uLeft = 0,
    UINT32 uTop = 0,
    UINT32 uRight = 0,
    UINT32 uBottom = 0);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
zdrojový obdélník

*uVlevo*<br/>
zdroj levé souřadnice

*uNahoře*<br/>
zdroj oválná souřadnice

*uVpravo*<br/>
souřadnice práva na zdroj

*uDno*<br/>
zdroj spodní souřadnice

## <a name="cd2drectuisnull"></a><a name="isnull"></a>CD2DRectU::IsNull

Vrátí logickou hodnotu, která označuje, zda výraz neobsahuje žádná platná data (Null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud jsou nejvyšší, levé, dolní a pravé hodnoty obdélníku rovny 0; jinak FALSE.

## <a name="cd2drectuoperator-crect"></a><a name="operator_crect"></a>CD2DRectU::operátor CRect

Převede objekt CD2DRectU na objekt CRect.

```
operator CRect();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální hodnota obdélníku D2D.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
