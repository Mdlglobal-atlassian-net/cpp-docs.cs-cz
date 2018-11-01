---
title: Cd2dsizef – třída
ms.date: 11/04/2016
f1_keywords:
- CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::IsNull
helpviewer_keywords:
- CD2DSizeF [MFC], CD2DSizeF
- CD2DSizeF [MFC], IsNull
ms.assetid: f486a1e1-997d-4286-8cb9-26369dc82055
ms.openlocfilehash: e9c8d77a9f84abe9a483a0f100e1f52b8768202b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557466"
---
# <a name="cd2dsizef-class"></a>Cd2dsizef – třída

Obálka pro D2D1_SIZE_F.

## <a name="syntax"></a>Syntaxe

```
class CD2DSizeF : public D2D1_SIZE_F;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CD2DSizeF::CD2DSizeF](#cd2dsizef)|Přetíženo. Vytvoří `CD2DSizeF` objektu z `D2D1_SIZE_F` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CD2DSizeF::IsNull](#isnull)|Vrátí **logická** hodnotu, která určuje, zda výraz neobsahuje žádná platná data (NULL).|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CD2DSizeF::Operator CSize](#operator_csize)|Převede `CD2DSizeF` k `CSize` objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`D2D1_SIZE_F`

[Cd2dsizef –](../../mfc/reference/cd2dsizef-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

##  <a name="cd2dsizef"></a>  CD2DSizeF::CD2DSizeF

Vytvoří objekt cd2dsizef – z CSize objektu.

```
CD2DSizeF(const CSize& size);
CD2DSizeF(const D2D1_SIZE_F& size);
  CD2DSizeF(const D2D1_SIZE_F* size);

CD2DSizeF(
    FLOAT cx = 0.,
    FLOAT cy = 0.);
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
velikost zdroje

*CX*<br/>
Šířka zdroje

*CY*<br/>
výška zdroje

##  <a name="isnull"></a>  CD2DSizeF::IsNull

Vrátí logickou hodnotu, která určuje, zda výraz neobsahuje žádná platná data (Null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud šířky a výšky jsou prázdná. v opačném případě FALSE.

##  <a name="operator_csize"></a>  CD2DSizeF::Operator CSize

Převede cd2dsizef – CSize objektu.

```
operator CSize();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální hodnota velikosti D2D.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
