---
title: "Třída CD2DRectU | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DRectU
- AFXRENDERTARGET/CD2DRectU
- AFXRENDERTARGET/CD2DRectU::CD2DRectU
- AFXRENDERTARGET/CD2DRectU::IsNull
dev_langs: C++
helpviewer_keywords:
- CD2DRectU [MFC], CD2DRectU
- CD2DRectU [MFC], IsNull
ms.assetid: a62f17d1-011d-4867-8f51-fd7e7c00561d
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2bf261f31f470862a506466a8815daef796743f6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cd2drectu-class"></a>CD2DRectU – třída
Obálka pro `D2D1_RECT_U`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CD2DRectU : public D2D1_RECT_U;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DRectU::CD2DRectU](#cd2drectu)|Přetíženo. Vytvoří `CD2DRectU` objektu z `D2D1_RECT_U` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DRectU::IsNull](#isnull)|Vrátí `boolean` hodnotu, která určuje, zda výraz neobsahuje žádná platná data ( `null`).|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DRectU::Operator CRect](#operator_crect)|Převede `CD2DRectU` k `CRect` objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `D2D1_RECT_U`  
  
 `CD2DRectU`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxrendertarget.h  
  
##  <a name="cd2drectu"></a>CD2DRectU::CD2DRectU  
 Vytvoří objekt CD2DRectU z CRect objektu.  
  
```  
CD2DRectU(const CRect& rect);  
CD2DRectU(const D2D1_RECT_U& rect);  
  CD2DRectU(const D2D1_RECT_U* rect);

 
CD2DRectU(
    UINT32 uLeft = 0,  
    UINT32 uTop = 0,  
    UINT32 uRight = 0,  
    UINT32 uBottom = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `rect`  
 Zdroj obdélníku  
  
 `uLeft`  
 levou souřadnici zdroje  
  
 `uTop`  
 horní souřadnici zdroje  
  
 `uRight`  
 Zdroj právo souřadnic  
  
 `uBottom`  
 souřadnice dolního zdroje  
  
##  <a name="isnull"></a>CD2DRectU::IsNull  
 Vrátí logickou hodnotu, která určuje, zda výraz neobsahuje žádná platná data (Null).  
  
```  
BOOL IsNull() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud jsou všechny rovna 0; horní obdélníku, vlevo, dolní a pravé hodnoty jinak hodnota FALSE.  
  
##  <a name="operator_crect"></a>CD2DRectU::Operator CRect  
 Převede CD2DRectU CRect objektu.  
  
```  
operator CRect();
```   
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální hodnota D2D obdélník.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
