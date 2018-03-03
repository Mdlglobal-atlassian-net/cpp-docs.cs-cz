---
title: "Globální funkce pro převod pixelů HIMETRIC | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlwin/ATL::AtlHiMetricToPixel
- atlwin/ATL::AtlPixelToHiMetric
dev_langs:
- C++
ms.assetid: ecb1b1b2-7e9d-4fbc-a855-16252d2d794c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9d670d667345c233fc499cda42194dfafa185dfe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="pixelhimetric-conversion-global-functions"></a>Globální funkce pro převod pixelu nebo HIMETRIC
Tyto funkce poskytují podporu pro převod do a z pixelů a HIMETRIC jednotky.  
  
> [!IMPORTANT]
>  Funkce uvedené v následující tabulce nelze používat v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
|||  
|-|-|  
|[AtlHiMetricToPixel](#atlhimetrictopixel)|Převede HIMETRIC jednotky (jednotlivých jednotek je 0,01 milimetru) pixelů.|  
|[AtlPixelToHiMetric](#atlpixeltohimetric)|Převede pixelů na HIMETRIC jednotky (jednotlivých jednotek je 0,01 milimetru).|  
  
##  <a name="atlhimetrictopixel"></a>AtlHiMetricToPixel  
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
  
##  <a name="atlpixeltohimetric"></a>AtlPixelToHiMetric  
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
