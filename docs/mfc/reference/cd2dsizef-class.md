---
title: CD2DSizeF – třída
ms.date: 08/29/2019
f1_keywords:
- CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::IsNull
helpviewer_keywords:
- CD2DSizeF [MFC], CD2DSizeF
- CD2DSizeF [MFC], IsNull
ms.assetid: f486a1e1-997d-4286-8cb9-26369dc82055
ms.openlocfilehash: df895c278003e2c71f37a00af6bf14912756701a
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177198"
---
# <a name="cd2dsizef-class"></a>CD2DSizeF – třída

Obálka pro D2D1_SIZE_F.

## <a name="syntax"></a>Syntaxe

```
class CD2DSizeF : public D2D1_SIZE_F;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CD2DSizeF::CD2DSizeF](#cd2dsizef)|Přetíženo. Vytvoří objekt z `D2D1_SIZE_F`objektu. `CD2DSizeF`|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CD2DSizeF:: IsNull](#isnull)|Vrací **logickou** hodnotu, která označuje, zda výraz neobsahuje žádná platná data (null).|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CD2DSizeF:: operator CSize](#operator_csize)|Převede `CD2DSizeF` na`CSize` objekt.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`D2D1_SIZE_F`

[CD2DSizeF](../../mfc/reference/cd2dsizef-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget. h

##  <a name="cd2dsizef"></a>CD2DSizeF::CD2DSizeF

Vytvoří objekt CD2DSizeF z objektu CSize.

```
CD2DSizeF(const CSize& size);
CD2DSizeF(const D2D1_SIZE_F& size);
CD2DSizeF(const D2D1_SIZE_F* size);

CD2DSizeF(
    FLOAT cx = 0.,
    FLOAT cy = 0.);
```

### <a name="parameters"></a>Parametry

*hodnota*<br/>
velikost zdroje

*cx*<br/>
Šířka zdroje

*kr*<br/>
Výška zdroje

##  <a name="isnull"></a>CD2DSizeF:: IsNull

Vrací logickou hodnotu, která označuje, zda výraz neobsahuje žádná platná data (null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je šířka a výška prázdná; v opačném případě FALSE.

##  <a name="operator_csize"></a>CD2DSizeF:: operator CSize

Převede CD2DSizeF na objekt CSize.

```
operator CSize();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální hodnota velikosti D2D

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)
