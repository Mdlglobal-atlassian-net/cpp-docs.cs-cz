---
title: Cd2dellipse – třída
ms.date: 11/04/2016
f1_keywords:
- CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse::CD2DEllipse
helpviewer_keywords:
- CD2DEllipse [MFC], CD2DEllipse
ms.assetid: e9f02f54-acf2-427e-b349-db50cd9a77df
ms.openlocfilehash: 3abf0736884840be7bdcfcd55cb18a0bc8e69195
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270818"
---
# <a name="cd2dellipse-class"></a>Cd2dellipse – třída

Obálka pro `D2D1_ELLIPSE`.

## <a name="syntax"></a>Syntaxe

```
class CD2DEllipse : public D2D1_ELLIPSE;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CD2DEllipse::CD2DEllipse](#cd2dellipse)|Přetíženo. Vytvoří `CD2DEllipse` objektu z `D2D1_ELLIPSE` objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`D2D1_ELLIPSE`

`CD2DEllipse`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

##  <a name="cd2dellipse"></a>  CD2DEllipse::CD2DEllipse

Vytvoří objekt cd2dellipse – z cd2drectf – objektu.

```
CD2DEllipse(const CD2DRectF& rect);
CD2DEllipse(const D2D1_ELLIPSE& ellipse);
  CD2DEllipse(const D2D1_ELLIPSE* ellipse);

CD2DEllipse(
    const CD2DPointF& ptCenter,
    const CD2DSizeF& sizeRadius);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
zdrojového obdélníku

*tři tečky*<br/>
Zdroj elipsa

*ptCenter*<br/>
Středový bod elipsy.

*sizeRadius*<br/>
Poloměr X a Y poloměr elipsy.

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)
