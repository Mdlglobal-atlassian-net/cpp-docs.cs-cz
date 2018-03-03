---
title: "Třída CD2DPointU | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DPointU
- AFXRENDERTARGET/CD2DPointU
- AFXRENDERTARGET/CD2DPointU::CD2DPointU
dev_langs:
- C++
helpviewer_keywords:
- CD2DPointU [MFC], CD2DPointU
ms.assetid: 04733f96-b6de-4a89-82e3-caad1e8087a9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f5af7ab3327a7c3d2f1afc31ad8cc2bde144eeb3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cd2dpointu-class"></a>CD2DPointU – třída
Obálka pro `D2D1_POINT_2U`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CD2DPointU : public D2D1_POINT_2U;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DPointU::CD2DPointU](#cd2dpointu)|Přetíženo. Vytvoří `CD2DPointU` z objektu `D2D1_POINT_2U` objektu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DPointU::Operator CPoint](#operator_cpoint)|Převede `CD2DPointU` k `CPoint` objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `D2D1_POINT_2U`  
  
 `CD2DPointU`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxrendertarget.h  
  
##  <a name="cd2dpointu"></a>CD2DPointU::CD2DPointU  
 Vytvoří objekt CD2DPointU z CPoint objektu.  
  
```  
CD2DPointU(const CPoint& pt);  
CD2DPointU(const D2D1_POINT_2U& pt);  
  CD2DPointU(const D2D1_POINT_2U* pt);  
CD2DPointU(UINT32 uX = 0, UINT32 uY = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `pt`  
 zdrojový bod  
  
 `uX`  
 Zdroj X  
  
 `uY`  
 Zdroj Y  
  
##  <a name="operator_cpoint"></a>CD2DPointU::Operator CPoint  
 Převede CD2DPointU CPoint objektu.  
  
```  
operator CPoint();
```   
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální hodnota D2D bodu.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
