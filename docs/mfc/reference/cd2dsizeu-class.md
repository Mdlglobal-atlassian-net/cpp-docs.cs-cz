---
title: CD2DSizeU – třída
ms.date: 08/29/2019
f1_keywords:
- CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::IsNull
helpviewer_keywords:
- CD2DSizeU [MFC], CD2DSizeU
- CD2DSizeU [MFC], IsNull
ms.assetid: 6e679ba8-2112-43c3-8275-70b660856f02
ms.openlocfilehash: 45625331d0c1be8ca7c663d12c53516dc7bd77c7
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177182"
---
# <a name="cd2dsizeu-class"></a>CD2DSizeU – třída

Obálka pro D2D1_SIZE_U.

## <a name="syntax"></a>Syntaxe

```
class CD2DSizeU : public D2D1_SIZE_U;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CD2DSizeU::CD2DSizeU](#cd2dsizeu)|Přetíženo. Vytvoří objekt z `D2D1_SIZE_U`objektu. `CD2DSizeU`|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CD2DSizeU::IsNull](#isnull)|Vrací **logickou** hodnotu, která označuje, zda výraz neobsahuje žádná platná data (null).|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CD2DSizeU:: operator CSize](#operator_csize)|Převede `CD2DSizeU` na`CSize` objekt.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`D2D1_SIZE_U`

[CD2DSizeU](../../mfc/reference/cd2dsizeu-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget. h

##  <a name="cd2dsizeu"></a>CD2DSizeU::CD2DSizeU

Vytvoří objekt CD2DSizeU z objektu CSize.

```
CD2DSizeU(const CSize& size);
CD2DSizeU(const D2D1_SIZE_U& size);
CD2DSizeU(const D2D1_SIZE_U* size);

CD2DSizeU(
    UINT32 cx = 0,
    UINT32 cy = 0);
```

### <a name="parameters"></a>Parametry

*hodnota*<br/>
velikost zdroje

*cx*<br/>
Šířka zdroje

*kr*<br/>
Výška zdroje

##  <a name="isnull"></a>CD2DSizeU:: IsNull

Vrací logickou hodnotu, která označuje, zda výraz neobsahuje žádná platná data (null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je šířka a výška prázdná; v opačném případě FALSE.

##  <a name="operator_csize"></a>CD2DSizeU:: operator CSize

Převede CD2DSizeU na objekt CSize.

```
operator CSize();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální hodnota velikosti D2D

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)
