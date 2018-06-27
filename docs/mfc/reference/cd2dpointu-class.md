---
title: Třída CD2DPointU | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 81c61eec099be90099e5cb0a28355d0037c92774
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956629"
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
  
##  <a name="cd2dpointu"></a>  CD2DPointU::CD2DPointU  
 Vytvoří objekt CD2DPointU z CPoint objektu.  
  
```  
CD2DPointU(const CPoint& pt);  
CD2DPointU(const D2D1_POINT_2U& pt);  
  CD2DPointU(const D2D1_POINT_2U* pt);  
CD2DPointU(UINT32 uX = 0, UINT32 uY = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *PT*  
 zdrojový bod  
  
 *uX*  
 Zdroj X  
  
 *uY*  
 Zdroj Y  
  
##  <a name="operator_cpoint"></a>  CD2DPointU::Operator CPoint  
 Převede CD2DPointU CPoint objektu.  
  
```  
operator CPoint();
```   
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální hodnota D2D bodu.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
