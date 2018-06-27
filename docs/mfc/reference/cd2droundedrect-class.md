---
title: Třída CD2DRoundedRect | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DRoundedRect
- AFXRENDERTARGET/CD2DRoundedRect
- AFXRENDERTARGET/CD2DRoundedRect::CD2DRoundedRect
dev_langs:
- C++
helpviewer_keywords:
- CD2DRoundedRect [MFC], CD2DRoundedRect
ms.assetid: 06207fb5-e92b-41c0-bceb-b45d8f466531
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ab5a43747d258f7482f7de4d61b9da8201c0729b
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36952882"
---
# <a name="cd2droundedrect-class"></a>CD2DRoundedRect – třída
Obálka pro `D2D1_ROUNDED_RECT`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CD2DRoundedRect : public D2D1_ROUNDED_RECT;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DRoundedRect::CD2DRoundedRect](#cd2droundedrect)|Přetíženo. Vytvoří `CD2DRoundedRect` objektu z `D2D1_ROUNDED_RECT` objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `D2D1_ROUNDED_RECT`  
  
 [CD2DRoundedRect](../../mfc/reference/cd2droundedrect-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxrendertarget.h  
  
##  <a name="cd2droundedrect"></a>  CD2DRoundedRect::CD2DRoundedRect  
 Vytvoří objekt CD2DRoundedRect z CD2DRectF objektu.  
  
```  
CD2DRoundedRect(
    const CD2DRectF& rectIn,  
    const CD2DSizeF& sizeRadius);  
  
CD2DRoundedRect(const D2D1_ROUNDED_RECT& rectIn);  
CD2DRoundedRect(const D2D1_ROUNDED_RECT* rectIn);
```  
  
### <a name="parameters"></a>Parametry  
 *rectIn*  
 Zdroj obdélníku  
  
 *sizeRadius*  
 velikost protokolu RADIUS  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
