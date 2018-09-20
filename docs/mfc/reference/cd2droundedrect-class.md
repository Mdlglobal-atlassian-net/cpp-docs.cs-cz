---
title: Cd2droundedrect – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DRoundedRect
- AFXRENDERTARGET/CD2DRoundedRect
- AFXRENDERTARGET/CD2DRoundedRect::CD2DRoundedRect
dev_langs:
- C++
helpviewer_keywords:
- CD2DRoundedRect [MFC], CD2DRoundedRect
ms.assetid: 06207fb5-e92b-41c0-bceb-b45d8f466531
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2037a00eb00fac1a14eca50031d213a5827ac425
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46448022"
---
# <a name="cd2droundedrect-class"></a>Cd2droundedrect – třída

Obálka pro `D2D1_ROUNDED_RECT`.

## <a name="syntax"></a>Syntaxe

```
class CD2DRoundedRect : public D2D1_ROUNDED_RECT;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CD2DRoundedRect::CD2DRoundedRect](#cd2droundedrect)|Přetíženo. Vytvoří `CD2DRoundedRect` objektu z `D2D1_ROUNDED_RECT` objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`D2D1_ROUNDED_RECT`

[Cd2droundedrect –](../../mfc/reference/cd2droundedrect-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

##  <a name="cd2droundedrect"></a>  CD2DRoundedRect::CD2DRoundedRect

Vytvoří objekt cd2droundedrect – z cd2drectf – objektu.

```
CD2DRoundedRect(
    const CD2DRectF& rectIn,
    const CD2DSizeF& sizeRadius);

CD2DRoundedRect(const D2D1_ROUNDED_RECT& rectIn);
CD2DRoundedRect(const D2D1_ROUNDED_RECT* rectIn);
```

### <a name="parameters"></a>Parametry

*rectIn*<br/>
zdrojového obdélníku

*sizeRadius*<br/>
velikost protokolu RADIUS

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
