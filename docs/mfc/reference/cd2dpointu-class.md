---
title: CD2DPointU Class
ms.date: 08/29/2019
f1_keywords:
- CD2DPointU
- AFXRENDERTARGET/CD2DPointU
- AFXRENDERTARGET/CD2DPointU::CD2DPointU
helpviewer_keywords:
- CD2DPointU [MFC], CD2DPointU
ms.assetid: 04733f96-b6de-4a89-82e3-caad1e8087a9
ms.openlocfilehash: 6289d33aa0672d1ee423d91b11527dccfc868da7
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177175"
---
# <a name="cd2dpointu-class"></a>CD2DPointU Class

Obálka pro `D2D1_POINT_2U`.

## <a name="syntax"></a>Syntaxe

```
class CD2DPointU : public D2D1_POINT_2U;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CD2DPointU::CD2DPointU](#cd2dpointu)|Přetíženo. `CD2DPointU` Vytvoří objekt`D2D1_POINT_2U` z objektu Object.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CD2DPointU::operator CPoint](#operator_cpoint)|Převede `CD2DPointU` na`CPoint` objekt.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`D2D1_POINT_2U`

`CD2DPointU`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget. h

##  <a name="cd2dpointu"></a>CD2DPointU::CD2DPointU

Vytvoří objekt CD2DPointU z objektu CPoint.

```
CD2DPointU(const CPoint& pt);
CD2DPointU(const D2D1_POINT_2U& pt);
CD2DPointU(const D2D1_POINT_2U* pt);
CD2DPointU(UINT32 uX = 0, UINT32 uY = 0);
```

### <a name="parameters"></a>Parametry

*bodů*<br/>
zdrojový bod

*uX*<br/>
zdrojový znak X

*uY*<br/>
zdrojový Y

##  <a name="operator_cpoint"></a>CD2DPointU:: operator CPoint

Převede CD2DPointU na objekt CPoint.

```
operator CPoint();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální hodnota bodu D2D

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)
