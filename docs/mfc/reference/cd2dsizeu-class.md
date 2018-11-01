---
title: Cd2dsizeu – třída
ms.date: 11/04/2016
f1_keywords:
- CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::IsNull
helpviewer_keywords:
- CD2DSizeU [MFC], CD2DSizeU
- CD2DSizeU [MFC], IsNull
ms.assetid: 6e679ba8-2112-43c3-8275-70b660856f02
ms.openlocfilehash: bad73a53eabe0a4c75483e9871a4fdc4a361449b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512473"
---
# <a name="cd2dsizeu-class"></a>Cd2dsizeu – třída

Obálka pro D2D1_SIZE_U.

## <a name="syntax"></a>Syntaxe

```
class CD2DSizeU : public D2D1_SIZE_U;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CD2DSizeU::CD2DSizeU](#cd2dsizeu)|Přetíženo. Vytvoří `CD2DSizeU` objektu z `D2D1_SIZE_U` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CD2DSizeU::IsNull](#isnull)|Vrátí **logická** hodnotu, která určuje, zda výraz neobsahuje žádná platná data (NULL).|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CD2DSizeU::Operator CSize](#operator_csize)|Převede `CD2DSizeU` k `CSize` objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`D2D1_SIZE_U`

[Cd2dsizeu –](../../mfc/reference/cd2dsizeu-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

##  <a name="cd2dsizeu"></a>  CD2DSizeU::CD2DSizeU

Vytvoří objekt cd2dsizeu – z CSize objektu.

```
CD2DSizeU(const CSize& size);
CD2DSizeU(const D2D1_SIZE_U& size);
  CD2DSizeU(const D2D1_SIZE_U* size);

CD2DSizeU(
    UINT32 cx = 0,
    UINT32 cy = 0);
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
velikost zdroje

*CX*<br/>
Šířka zdroje

*CY*<br/>
výška zdroje

##  <a name="isnull"></a>  CD2DSizeU::IsNull

Vrátí logickou hodnotu, která určuje, zda výraz neobsahuje žádná platná data (Null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud šířky a výšky jsou prázdná. v opačném případě FALSE.

##  <a name="operator_csize"></a>  CD2DSizeU::Operator CSize

Převede cd2dsizeu – CSize objektu.

```
operator CSize();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální hodnota velikosti D2D.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
