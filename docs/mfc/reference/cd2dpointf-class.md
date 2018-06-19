---
title: Třída CD2DPointF | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DPointF
- AFXRENDERTARGET/CD2DPointF
- AFXRENDERTARGET/CD2DPointF::CD2DPointF
dev_langs:
- C++
helpviewer_keywords:
- CD2DPointF [MFC], CD2DPointF
ms.assetid: 30f72083-1c8a-4f50-adb2-72dbbe3522d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4a6439a25072975d28b98e4c6d88c3a1de8703d6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348703"
---
# <a name="cd2dpointf-class"></a>CD2DPointF – třída
Obálka pro `D2D1_POINT_2F`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CD2DPointF : public D2D1_POINT_2F;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DPointF::CD2DPointF](#cd2dpointf)|Přetíženo. Vytvoří `CD2DPointF` objektu z `D2D1_POINT_2F` objektu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DPointF::Operator CPoint](#operator_cpoint)|Převede `CD2DPointF` k `CPoint` objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `D2D1_POINT_2F`  
  
 `CD2DPointF`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxrendertarget.h  
  
##  <a name="cd2dpointf"></a>  CD2DPointF::CD2DPointF  
 Vytvoří objekt CD2DPointF z CPoint objektu.  
  
```  
CD2DPointF(const CPoint& pt);    
CD2DPointF(const D2D1_POINT_2F& pt);    
CD2DPointF(const D2D1_POINT_2F* pt); 
CD2DPointF(FLOAT fX = 0., FLOAT fY = 0.);
```  
  
### <a name="parameters"></a>Parametry  
 `pt`  
 zdrojový bod  
  
 `fX`  
 Zdroj X  
  
 `fY`  
 Zdroj Y  
  
##  <a name="operator_cpoint"></a>  CD2DPointF::Operator CPoint  
 Převede CD2DPointF CPoint objektu.  
  
```  
operator CPoint();
```   
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální hodnota D2D bodu.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
