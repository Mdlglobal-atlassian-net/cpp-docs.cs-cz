---
title: Cd2drectu – třída
ms.date: 11/04/2016
f1_keywords:
- CD2DRectU
- AFXRENDERTARGET/CD2DRectU
- AFXRENDERTARGET/CD2DRectU::CD2DRectU
- AFXRENDERTARGET/CD2DRectU::IsNull
helpviewer_keywords:
- CD2DRectU [MFC], CD2DRectU
- CD2DRectU [MFC], IsNull
ms.assetid: a62f17d1-011d-4867-8f51-fd7e7c00561d
ms.openlocfilehash: 4bbf7014fc1b612804289dcb647f85b5e7905aeb
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244388"
---
# <a name="cd2drectu-class"></a>Cd2drectu – třída

Obálka pro `D2D1_RECT_U`.

## <a name="syntax"></a>Syntaxe

```
class CD2DRectU : public D2D1_RECT_U;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CD2DRectU::CD2DRectU](#cd2drectu)|Přetíženo. Vytvoří `CD2DRectU` objektu z `D2D1_RECT_U` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CD2DRectU::IsNull](#isnull)|Vrátí **logická** hodnotu, která určuje, zda výraz neobsahuje žádná platná data (NULL).|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[Crect – CD2DRectU::Operator](#operator_crect)|Převede `CD2DRectU` k `CRect` objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`D2D1_RECT_U`

`CD2DRectU`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

##  <a name="cd2drectu"></a>  CD2DRectU::CD2DRectU

Vytvoří objekt cd2drectu – z crect – objektu.

```
CD2DRectU(const CRect& rect);
CD2DRectU(const D2D1_RECT_U& rect);
CD2DRectU(const D2D1_RECT_U* rect);

CD2DRectU(
    UINT32 uLeft = 0,
    UINT32 uTop = 0,
    UINT32 uRight = 0,
    UINT32 uBottom = 0);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
zdrojového obdélníku

*uLeft*<br/>
Levá souřadnice zdroje

*uTop*<br/>
horní souřadnici zdroje

*uRight*<br/>
zdroj přímo souřadnice

*uBottom*<br/>
Dolní souřadnice zdroje

##  <a name="isnull"></a>  CD2DRectU::IsNull

Vrátí logickou hodnotu, která určuje, zda výraz neobsahuje žádná platná data (Null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud jsou všechny rovnat 0; horní části obdélníku, vlevo, dolní a správné hodnoty v opačném případě FALSE.

##  <a name="operator_crect"></a>  Crect – CD2DRectU::Operator

Převede cd2drectu – crect – objektu.

```
operator CRect();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální hodnota obdélníku D2D.

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)
