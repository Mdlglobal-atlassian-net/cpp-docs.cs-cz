---
title: Pixel-HIMETRIC Konverze globální funkce
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlHiMetricToPixel
- atlwin/ATL::AtlPixelToHiMetric
ms.assetid: ecb1b1b2-7e9d-4fbc-a855-16252d2d794c
ms.openlocfilehash: 08c72c0d8f3d061950d6945d9fb412c0a16355da
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326148"
---
# <a name="pixelhimetric-conversion-global-functions"></a>Pixel / HIMETRIC Konverze globální funkce

Tyto funkce poskytují podporu pro převod na a z pixela a HIMETRIC jednotky.

> [!IMPORTANT]
> Funkce uvedené v následující tabulce nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

|||
|-|-|
|[AtlHiMetricToPixel](#atlhimetrictopixel)|Převede jednotky HIMETRIC (každá jednotka je 0,01 milimetru) na pixely.|
|[AtlPixelToHiMetric](#atlpixeltohimetric)|Převede obrazové body na jednotky HIMETRIC (každá jednotka je 0,01 milimetru).|

## <a name="atlhimetrictopixel"></a><a name="atlhimetrictopixel"></a>AtlHiMetricToPixel

Převede velikost objektu v jednotkách HIMETRIC (každá jednotka je 0,01 milimetru) na velikost v pixelech na obrazovkovém zařízení.

```
extern void AtlHiMetricToPixel(
    const SIZEL* lpSizeInHiMetric,
    LPSIZEL lpSizeInPix);
```

### <a name="parameters"></a>Parametry

*lpSizeInHiMetric*<br/>
[v] Ukazatel na velikost objektu v jednotkách HIMETRIC.

*lpSizeInPix*<br/>
[out] Ukazatel na místo, kde má být vrácena velikost objektu v pixelech.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#49](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_1.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="atlpixeltohimetric"></a><a name="atlpixeltohimetric"></a>AtlPixelToHiMetric

Převede velikost objektu v pixelech na obrazovkovém zařízení na velikost v jednotkách HIMETRIC (každá jednotka je 0,01 milimetru).

```
extern void AtlPixelToHiMetric(
    const SIZEL* lpSizeInPix,
    LPSIZEL lpSizeInHiMetric);
```

### <a name="parameters"></a>Parametry

*lpSizeInPix*<br/>
[v] Ukazatel na velikost objektu v obrazových bodech.

*lpSizeInHiMetric*<br/>
[out] Ukazatel na místo, kde má být vrácena velikost objektu v jednotkách HIMETRIC.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#51](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_2.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="see-also"></a>Viz také

[Functions](../../atl/reference/atl-functions.md)
