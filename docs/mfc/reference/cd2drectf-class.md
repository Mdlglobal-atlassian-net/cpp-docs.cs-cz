---
title: CD2DRectF – třída
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
ms.openlocfilehash: 9b91cfaec3827a61152c4116b56e817a436606be
ms.sourcegitcommit: 725e86dabe2901175ecc63261c3bf05802dddff4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/31/2019
ms.locfileid: "68682393"
---
# <a name="cd2drectf-class"></a>CD2DRectF – třída

Obálka pro `D2D1_RECT_F`.

## <a name="syntax"></a>Syntaxe

```
class CD2DRectF : public D2D1_RECT_F;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CD2DRectF::CD2DRectF](#cd2drectf)|Přetíženo. Vytvoří objekt z `D2D1_RECT_F`objektu. `CD2DRectF`|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CD2DRectF:: IsNull](#isnull)|Vrací **logickou** hodnotu, která označuje, zda výraz neobsahuje žádná platná data (null).|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CD2DRectF:: operator CRect](#operator_crect)|Převede `CD2DRectF` na`CRect` objekt.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`D2D1_RECT_F`

`CD2DRectF`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget. h

##  <a name="cd2drectf"></a>CD2DRectF::CD2DRectF

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

*OBD*<br/>
zdrojový obdélník

*fLeft*<br/>
souřadnice zdrojové levé části

*fTop*<br/>
hlavní souřadnice zdroje

*fRight*<br/>
souřadnice zdrojové vpravo

*fBottom*<br/>
Dolní souřadnice zdroje

##  <a name="isnull"></a>CD2DRectF:: IsNull

Vrací logickou hodnotu, která označuje, zda výraz neobsahuje žádná platná data (null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud jsou hodnoty horní, levý, dolní a pravého obdélníku všechny rovny 0; v opačném případě FALSE.

##  <a name="operator_crect"></a>CD2DRectF:: operator CRect

Převede CD2DRectF na objekt CRect.

```
operator CRect();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální hodnota obdélníku D2D

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)
