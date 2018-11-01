---
title: Cd2dpointu – třída
ms.date: 11/04/2016
f1_keywords:
- CD2DPointU
- AFXRENDERTARGET/CD2DPointU
- AFXRENDERTARGET/CD2DPointU::CD2DPointU
helpviewer_keywords:
- CD2DPointU [MFC], CD2DPointU
ms.assetid: 04733f96-b6de-4a89-82e3-caad1e8087a9
ms.openlocfilehash: 138916efe781d8bef69a1c4eb61a73c5a405be67
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551850"
---
# <a name="cd2dpointu-class"></a>Cd2dpointu – třída

Obálka pro `D2D1_POINT_2U`.

## <a name="syntax"></a>Syntaxe

```
class CD2DPointU : public D2D1_POINT_2U;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CD2DPointU::CD2DPointU](#cd2dpointu)|Přetíženo. Vytvoří `CD2DPointU` z objektu `D2D1_POINT_2U` objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CD2DPointU::Operator CPoint](#operator_cpoint)|Převede `CD2DPointU` k `CPoint` objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`D2D1_POINT_2U`

`CD2DPointU`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

##  <a name="cd2dpointu"></a>  CD2DPointU::CD2DPointU

Vytvoří objekt cd2dpointu – z CPoint objektu.

```
CD2DPointU(const CPoint& pt);
CD2DPointU(const D2D1_POINT_2U& pt);
  CD2DPointU(const D2D1_POINT_2U* pt);
CD2DPointU(UINT32 uX = 0, UINT32 uY = 0);
```

### <a name="parameters"></a>Parametry

*PT*<br/>
zdrojový bod

*uživatelského rozhraní*<br/>
Zdroj X

*uY*<br/>
Zdroj Y

##  <a name="operator_cpoint"></a>  CD2DPointU::Operator CPoint

Převede cd2dpointu – CPoint objektu.

```
operator CPoint();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální hodnota bodu D2D.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
