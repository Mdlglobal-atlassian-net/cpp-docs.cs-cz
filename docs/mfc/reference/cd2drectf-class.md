---
title: Třída CD2DRectF
ms.date: 11/04/2016
f1_keywords:
- CD2DRectF
- AFXRENDERTARGET/CD2DRectF
- AFXRENDERTARGET/CD2DRectF::CD2DRectF
- AFXRENDERTARGET/CD2DRectF::IsNull
helpviewer_keywords:
- CD2DRectF [MFC], CD2DRectF
- CD2DRectF [MFC], IsNull
ms.assetid: 87c12d87-9d18-4a19-ba14-0f51d6b6835a
ms.openlocfilehash: 33d3c5f9e795ad6c91b689436e8a3b1b56966dce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369126"
---
# <a name="cd2drectf-class"></a>Třída CD2DRectF

Obálka pro `D2D1_RECT_F`.

## <a name="syntax"></a>Syntaxe

```
class CD2DRectF : public D2D1_RECT_F;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DRectF::CD2DRectF](#cd2drectf)|Přetíženo. Vytvoří `CD2DRectF` objekt z `D2D1_RECT_F` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DRectF::IsNull](#isnull)|Vrátí **logickou** hodnotu, která označuje, zda výraz neobsahuje žádná platná data (NULL).|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DRectF::operátor CRect](#operator_crect)|Převede `CD2DRectF` `CRect` na objekt.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`D2D1_RECT_F`

`CD2DRectF`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

## <a name="cd2drectfcd2drectf"></a><a name="cd2drectf"></a>CD2DRectF::CD2DRectF

Vytvoří objekt CD2DRectF z objektu CRect.

```
CD2DRectF(const CRect& rect);
CD2DRectF(const D2D1_RECT_F& rect);
CD2DRectF(const D2D1_RECT_F* rect);

CD2DRectF(
    FLOAT fLeft = 0.,
    FLOAT fTop = 0.,
    FLOAT fRight = 0.,
    FLOAT fBottom = 0.);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
zdrojový obdélník

*fVlevo*<br/>
zdroj levé souřadnice

*fTop*<br/>
zdroj oválná souřadnice

*Strach*<br/>
souřadnice práva na zdroj

*fBottom*<br/>
zdroj spodní souřadnice

## <a name="cd2drectfisnull"></a><a name="isnull"></a>CD2DRectF::IsNull

Vrátí logickou hodnotu, která označuje, zda výraz neobsahuje žádná platná data (Null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud jsou nejvyšší, levé, dolní a pravé hodnoty obdélníku rovny 0; jinak FALSE.

## <a name="cd2drectfoperator-crect"></a><a name="operator_crect"></a>CD2DRectF::operátor CRect

Převede objekt CD2DRectF na objekt CRect.

```
operator CRect();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální hodnota obdélníku D2D.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
