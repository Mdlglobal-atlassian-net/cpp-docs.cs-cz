---
title: CD2DPointF – třída
ms.date: 11/04/2016
f1_keywords:
- CD2DPointF
- AFXRENDERTARGET/CD2DPointF
- AFXRENDERTARGET/CD2DPointF::CD2DPointF
helpviewer_keywords:
- CD2DPointF [MFC], CD2DPointF
ms.assetid: 30f72083-1c8a-4f50-adb2-72dbbe3522d4
ms.openlocfilehash: 5d66c31289f9e17df99df4681cff1d5cf6a0ec86
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369163"
---
# <a name="cd2dpointf-class"></a>CD2DPointF – třída

Obálka pro `D2D1_POINT_2F`.

## <a name="syntax"></a>Syntaxe

```
class CD2DPointF : public D2D1_POINT_2F;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DPointF::CD2DPointF](#cd2dpointf)|Přetíženo. Vytvoří `CD2DPointF` objekt z `D2D1_POINT_2F` objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DPointF::operátor CPoint](#operator_cpoint)|Převede `CD2DPointF` `CPoint` na objekt.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`D2D1_POINT_2F`

`CD2DPointF`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

## <a name="cd2dpointfcd2dpointf"></a><a name="cd2dpointf"></a>CD2DPointF::CD2DPointF

Vytvoří objekt CD2DPointF z objektu CPoint.

```
CD2DPointF(const CPoint& pt);
CD2DPointF(const D2D1_POINT_2F& pt);
CD2DPointF(const D2D1_POINT_2F* pt);
CD2DPointF(FLOAT fX = 0., FLOAT fY = 0.);
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
zdrojový bod

*Fx*<br/>
zdroj X

*Fy*<br/>
zdroj Y

## <a name="cd2dpointfoperator-cpoint"></a><a name="operator_cpoint"></a>CD2DPointF::operátor CPoint

Převede objekt CD2DPointF na objekt CPoint.

```
operator CPoint();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální hodnota bodu D2D.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
