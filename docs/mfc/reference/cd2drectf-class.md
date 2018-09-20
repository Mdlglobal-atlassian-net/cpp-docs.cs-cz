---
title: Cd2drectf – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DRectF
- AFXRENDERTARGET/CD2DRectF
- AFXRENDERTARGET/CD2DRectF::CD2DRectF
- AFXRENDERTARGET/CD2DRectF::IsNull
dev_langs:
- C++
helpviewer_keywords:
- CD2DRectF [MFC], CD2DRectF
- CD2DRectF [MFC], IsNull
ms.assetid: 87c12d87-9d18-4a19-ba14-0f51d6b6835a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eee19197c4b171cf669c9458ab722240e431bf70
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46398212"
---
# <a name="cd2drectf-class"></a>Cd2drectf – třída

Obálka pro `D2D1_RECT_F`.

## <a name="syntax"></a>Syntaxe

```
class CD2DRectF : public D2D1_RECT_F;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CD2DRectF::CD2DRectF](#cd2drectf)|Přetíženo. Vytvoří `CD2DRectF` objektu z `D2D1_RECT_F` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CD2DRectF::IsNull](#isnull)|Vrátí **logická** hodnotu, která určuje, zda výraz neobsahuje žádná platná data (NULL).|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[Crect – CD2DRectF::Operator](#operator_crect)|Převede `CD2DRectF` k `CRect` objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`D2D1_RECT_F`

`CD2DRectF`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

##  <a name="cd2drectf"></a>  CD2DRectF::CD2DRectF

Vytvoří objekt cd2drectf – z crect – objektu.

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
zdrojového obdélníku

*fLeft*<br/>
Levá souřadnice zdroje

*fTop*<br/>
horní souřadnici zdroje

*fRight*<br/>
zdroj přímo souřadnice

*fBottom*<br/>
Dolní souřadnice zdroje

##  <a name="isnull"></a>  CD2DRectF::IsNull

Vrátí logickou hodnotu, která určuje, zda výraz neobsahuje žádná platná data (Null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud jsou všechny rovnat 0; horní části obdélníku, vlevo, dolní a správné hodnoty v opačném případě FALSE.

##  <a name="operator_crect"></a>  Crect – CD2DRectF::Operator

Převede cd2drectf – crect – objektu.

```
operator CRect();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální hodnota obdélníku D2D.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
