---
title: Globální funkce pro převod pixelů HIMETRIC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlwin/ATL::AtlHiMetricToPixel
- atlwin/ATL::AtlPixelToHiMetric
dev_langs:
- C++
ms.assetid: ecb1b1b2-7e9d-4fbc-a855-16252d2d794c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 92d84204bdf02e75f1baf64bd52d96eab0b3d271
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="pixelhimetric-conversion-global-functions"></a>Globální funkce pro převod pixelu nebo HIMETRIC
Tyto funkce poskytují podporu pro převod do a z pixelů a HIMETRIC jednotky.  
  
> [!IMPORTANT]
>  Funkce uvedené v následující tabulce nelze používat v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
|||  
|-|-|  
|[AtlHiMetricToPixel](#atlhimetrictopixel)|Převede HIMETRIC jednotky (jednotlivých jednotek je 0,01 milimetru) pixelů.|  
|[AtlPixelToHiMetric](#atlpixeltohimetric)|Převede pixelů na HIMETRIC jednotky (jednotlivých jednotek je 0,01 milimetru).|  
  
##  <a name="atlhimetrictopixel"></a>  AtlHiMetricToPixel  
 Převede velikost objektu v jednotkách HIMETRIC (každá jednotka je 0,01 milimetru) na velikost v pixelech na obrazovkovém zařízení.  
  
 
```
extern void AtlHiMetricToPixel(
  const SIZEL* lpSizeInHiMetric, 
  LPSIZEL lpSizeInPix);
```  
  
### <a name="parameters"></a>Parametry  
 `lpSizeInHiMetric`  
 [v] Ukazatel na velikost objektu v HIMETRIC jednotkách.  
  
 `lpSizeInPix`  
 [out] Ukazatel na to, kde je velikost objektu v pixelech má být vrácen.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_COM#49](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_1.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h  
  
##  <a name="atlpixeltohimetric"></a>  AtlPixelToHiMetric  
 Převede velikost objektu v pixelech na obrazovkovém zařízení na velikost v jednotkách HIMETRIC (každá jednotka je 0,01 milimetru).  
  
```
extern void AtlPixelToHiMetric(
    const SIZEL* lpSizeInPix, 
    LPSIZEL lpSizeInHiMetric);
```  
  
### <a name="parameters"></a>Parametry  
 `lpSizeInPix`  
 [v] Ukazatel na velikost objektu v pixelech.  
  
 `lpSizeInHiMetric`  
 [out] Ukazatel na to, kde je velikost objektu v jednotkách HIMETRIC má být vrácen.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_COM#51](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_2.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h  

## <a name="see-also"></a>Viz také  
 [Funkce](../../atl/reference/atl-functions.md)
