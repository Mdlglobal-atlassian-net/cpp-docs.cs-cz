---
title: "Třída CD2DGradientBrush | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DGradientBrush
- AFXRENDERTARGET/CD2DGradientBrush
- AFXRENDERTARGET/CD2DGradientBrush::CD2DGradientBrush
- AFXRENDERTARGET/CD2DGradientBrush::Destroy
- AFXRENDERTARGET/CD2DGradientBrush::m_arGradientStops
- AFXRENDERTARGET/CD2DGradientBrush::m_colorInterpolationGamma
- AFXRENDERTARGET/CD2DGradientBrush::m_extendMode
- AFXRENDERTARGET/CD2DGradientBrush::m_pGradientStops
dev_langs: C++
helpviewer_keywords:
- CD2DGradientBrush [MFC], CD2DGradientBrush
- CD2DGradientBrush [MFC], Destroy
- CD2DGradientBrush [MFC], m_arGradientStops
- CD2DGradientBrush [MFC], m_colorInterpolationGamma
- CD2DGradientBrush [MFC], m_extendMode
- CD2DGradientBrush [MFC], m_pGradientStops
ms.assetid: 5bf133e6-16b7-4e3a-845d-0ce63fafe5ec
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c03d489b3059ddadf5783719f297371433a599e6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cd2dgradientbrush-class"></a>CD2DGradientBrush – třída
Základní třída CD2DLinearGradientBrush a CD2DRadialGradientBrush tříd.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CD2DGradientBrush : public CD2DBrush;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DGradientBrush::CD2DGradientBrush](#cd2dgradientbrush)|Vytvoří objekt CD2DGradientBrush.|  
|[CD2DGradientBrush:: ~ CD2DGradientBrush](#cd2dgradientbrush__~cd2dgradientbrush)|Destruktor. Voláno, když je objekt D2D štětce přechodu zničen.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DGradientBrush::Destroy](#destroy)|Zničí CD2DGradientBrush objektu. (Přepisuje [CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DGradientBrush::m_arGradientStops](#m_argradientstops)|Pole D2D1_GRADIENT_STOP struktury.|  
|[CD2DGradientBrush::m_colorInterpolationGamma](#m_colorinterpolationgamma)|Místo, na které barevně se provádí interpolace mezi Přechodové zarážky.|  
|[CD2DGradientBrush::m_extendMode](#m_extendmode)|Chování přechodu mimo normalizovaný rozsah [0, 1].|  
|[CD2DGradientBrush::m_pGradientStops](#m_pgradientstops)|Ukazatel na pole D2D1_GRADIENT_STOP struktury.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 `CD2DGradientBrush`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxrendertarget.h  
  
##  <a name="_dtorcd2dgradientbrush"></a>CD2DGradientBrush:: ~ CD2DGradientBrush  
 Destruktor. Voláno, když je objekt D2D štětce přechodu zničen.  
  
```  
virtual ~CD2DGradientBrush();
```  
  
##  <a name="cd2dgradientbrush"></a>CD2DGradientBrush::CD2DGradientBrush  
 Vytvoří objekt CD2DGradientBrush.  
  
```  
CD2DGradientBrush(
    CRenderTarget* pParentTarget,  
    const D2D1_GRADIENT_STOP* gradientStops,  
    UINT gradientStopsCount,  
    D2D1_GAMMA colorInterpolationGamma = D2D1_GAMMA_2_2,  
    D2D1_EXTEND_MODE extendMode = D2D1_EXTEND_MODE_CLAMP,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentTarget`  
 Ukazatel na cíl vykreslení.  
  
 `gradientStops`  
 Ukazatel na pole D2D1_GRADIENT_STOP struktury.  
  
 `gradientStopsCount`  
 Hodnota větší než nebo rovna 1, která určuje počet Přechodové zarážky v poli gradientStops.  
  
 `colorInterpolationGamma`  
 Místo, na které barevně se provádí interpolace mezi Přechodové zarážky.  
  
 `extendMode`  
 Chování přechodu mimo normalizovaný rozsah [0, 1].  
  
 `pBrushProperties`  
 Ukazatel na krytí a transformace štětce.  
  
 `bAutoDestroy`  
 Označuje, že bude objekt zničí vlastník (pParentTarget).  
  
##  <a name="destroy"></a>CD2DGradientBrush::Destroy  
 Zničí CD2DGradientBrush objektu.  
  
```  
virtual void Destroy();
```  
  
##  <a name="m_argradientstops"></a>CD2DGradientBrush::m_arGradientStops  
 Pole D2D1_GRADIENT_STOP struktury.  
  
```  
CArray<D2D1_GRADIENT_STOP, D2D1_GRADIENT_STOP> m_arGradientStops;  
```  
  
##  <a name="m_colorinterpolationgamma"></a>CD2DGradientBrush::m_colorInterpolationGamma  
 Místo, na které barevně se provádí interpolace mezi Přechodové zarážky.  
  
```  
D2D1_GAMMA m_colorInterpolationGamma;  
```  
  
##  <a name="m_extendmode"></a>CD2DGradientBrush::m_extendMode  
 Chování přechodu mimo normalizovaný rozsah [0, 1].  
  
```  
D2D1_EXTEND_MODE m_extendMode;  
```  
  
##  <a name="m_pgradientstops"></a>CD2DGradientBrush::m_pGradientStops  
 Ukazatel na pole D2D1_GRADIENT_STOP struktury.  
  
```  
ID2D1GradientStopCollection* m_pGradientStops;  
```  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
