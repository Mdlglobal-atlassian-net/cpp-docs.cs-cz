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
ms.openlocfilehash: a5b87fe2ddd8fb32ddbbb2884c630952afdb079c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359296"
---
# <a name="cd2dsizeu-class"></a>CD2DSizeU – třída

Obálka pro D2D1_SIZE_U.

## <a name="syntax"></a>Syntaxe

```
class CD2DSizeU : public D2D1_SIZE_U;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DSizeU::CD2DSizeU](#cd2dsizeu)|Přetíženo. Vytvoří `CD2DSizeU` objekt z `D2D1_SIZE_U` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DSizeU::Isnull](#isnull)|Vrátí **logickou** hodnotu, která označuje, zda výraz neobsahuje žádná platná data (NULL).|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CD2DSizeU::operátor CSize](#operator_csize)|Převede `CD2DSizeU` `CSize` na objekt.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`D2D1_SIZE_U`

[CD2DSizeU](../../mfc/reference/cd2dsizeu-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxrendertarget.h

## <a name="cd2dsizeucd2dsizeu"></a><a name="cd2dsizeu"></a>CD2DSizeU::CD2DSizeU

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

*Velikost*<br/>
velikost zdroje

*Cx*<br/>
šířka zdroje

*Cy*<br/>
výška zdroje

## <a name="cd2dsizeuisnull"></a><a name="isnull"></a>CD2DSizeU::Isnull

Vrátí logickou hodnotu, která označuje, zda výraz neobsahuje žádná platná data (Null).

```
BOOL IsNull() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud jsou šířka a výška prázdné; jinak FALSE.

## <a name="cd2dsizeuoperator-csize"></a><a name="operator_csize"></a>CD2DSizeU::operátor CSize

Převede objekt CD2DSizeU na objekt CSize.

```
operator CSize();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální hodnota velikosti D2D.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
