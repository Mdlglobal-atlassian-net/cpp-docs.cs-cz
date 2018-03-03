---
title: "Třída CD2DBrushProperties | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties::CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties::CommonInit
dev_langs:
- C++
helpviewer_keywords:
- CD2DBrushProperties [MFC], CD2DBrushProperties
- CD2DBrushProperties [MFC], CommonInit
ms.assetid: c77d717f-0a16-4d74-b2ce-0ae1766ed6f9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 011ea92e24be73aa51e29bab327bfa1ccdf7ed9a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cd2dbrushproperties-class"></a>CD2DBrushProperties – třída
Obálka pro `D2D1_BRUSH_PROPERTIES`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CD2DBrushProperties : public D2D1_BRUSH_PROPERTIES;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DBrushProperties::CD2DBrushProperties](#cd2dbrushproperties)|Přetíženo. Vytvoří `CD2D_BRUSH_PROPERTIES` struktura|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DBrushProperties::CommonInit](#commoninit)|Inicializuje objekt|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `D2D1_BRUSH_PROPERTIES`  
  
 `CD2DBrushProperties`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxrendertarget.h  
  
##  <a name="cd2dbrushproperties"></a>CD2DBrushProperties::CD2DBrushProperties  
 Vytvoří struktura CD2D_BRUSH_PROPERTIES  
  
```  
CD2DBrushProperties();  
CD2DBrushProperties(FLOAT _opacity);

 
CD2DBrushProperties(
    D2D1_MATRIX_3X2_F _transform,  
    FLOAT _opacity = 1.);
```  
  
### <a name="parameters"></a>Parametry  
 `_opacity`  
 Základní krytí stopy. Výchozí hodnota je 1.0.  
  
 `_transform`  
 Transformace, které chcete použít pro štětce  
  
##  <a name="commoninit"></a>CD2DBrushProperties::CommonInit  
 Inicializuje objekt  
  
```  
void CommonInit();
```  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
