---
title: Cd2dpointf – třída
ms.date: 11/04/2016
f1_keywords:
- CD2DPointF
- AFXRENDERTARGET/CD2DPointF
- AFXRENDERTARGET/CD2DPointF::CD2DPointF
helpviewer_keywords:
- CD2DPointF [MFC], CD2DPointF
ms.assetid: 30f72083-1c8a-4f50-adb2-72dbbe3522d4
ms.openlocfilehash: 7b9f6634e4b5980d8318557a8822549d226910b5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50559104"
---
# <a name="cd2dpointf-class"></a>Cd2dpointf – třída

Obálka pro `D2D1_POINT_2F`.

## <a name="syntax"></a>Syntaxe

```
class CD2DPointF : public D2D1_POINT_2F;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CD2DPointF::CD2DPointF](#cd2dpointf)|Přetíženo. Vytvoří `CD2DPointF` objektu z `D2D1_POINT_2F` objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CD2DPointF::Operator CPoint](#operator_cpoint)|Převede `CD2DPointF` k `CPoint` objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`D2D1_POINT_2F`

`CD2DPointF`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

##  <a name="cd2dpointf"></a>  CD2DPointF::CD2DPointF

Vytvoří objekt cd2dpointf – z CPoint objektu.

```
CD2DPointF(const CPoint& pt);
CD2DPointF(const D2D1_POINT_2F& pt);
CD2DPointF(const D2D1_POINT_2F* pt);
CD2DPointF(FLOAT fX = 0., FLOAT fY = 0.);
```

### <a name="parameters"></a>Parametry

*PT*<br/>
zdrojový bod

*fX*<br/>
Zdroj X

*FR*<br/>
Zdroj Y

##  <a name="operator_cpoint"></a>  CD2DPointF::Operator CPoint

Převede cd2dpointf – CPoint objektu.

```
operator CPoint();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální hodnota bodu D2D.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
