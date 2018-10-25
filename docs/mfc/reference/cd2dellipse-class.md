---
title: Cd2dellipse – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse::CD2DEllipse
dev_langs:
- C++
helpviewer_keywords:
- CD2DEllipse [MFC], CD2DEllipse
ms.assetid: e9f02f54-acf2-427e-b349-db50cd9a77df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 93fc2b788d450b591ebd20be49f25133c95f22b6
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052846"
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

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
