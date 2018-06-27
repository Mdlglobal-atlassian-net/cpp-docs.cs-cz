---
title: Třída CD2DRectF | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DRectF
- AFXRENDERTARGET/CD2DRectF
- AFXRENDERTARGET/CD2DRectF::CD2DRectF
- AFXRENDERTARGET/CD2DRectF::IsNull
dev_langs:
- C++
helpviewer_keywords:
- CD2DRectF [MFC], CD2DRectF
- CD2DRectF [MFC], IsNull
ms.assetid: 87c12d87-9d18-4a19-ba14-0f51d6b6835a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c7dc518832dd84bf5ca91765211f96934ea0b4f0
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956444"
---
# <a name="cd2drectf-class"></a>CD2DRectF – třída
Obálka pro `D2D1_RECT_F`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CD2DRectF : public D2D1_RECT_F;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DRectF::CD2DRectF](#cd2drectf)|Přetíženo. Vytvoří `CD2DRectF` objektu z `D2D1_RECT_F` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DRectF::IsNull](#isnull)|Vrátí **boolean** hodnotu, která určuje, zda výraz neobsahuje žádná platná data ( **null**).|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DRectF::Operator CRect](#operator_crect)|Převede `CD2DRectF` k `CRect` objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `D2D1_RECT_F`  
  
 `CD2DRectF`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxrendertarget.h  
  
##  <a name="cd2drectf"></a>  CD2DRectF::CD2DRectF  
 Vytvoří objekt CD2DRectF z CRect objektu.  
  
```  
CD2DRectF(const CRect& rect);  
CD2DRectF(const D2D1_RECT_F& rect);  
  CD2DRectF(const D2D1_RECT_F* rect);

 
CD2DRectF(
    FLOAT fLeft = 0.,  
    FLOAT fTop = 0.,  
    FLOAT fRight = 0.,  
    FLOAT fBottom = 0.);
```  
  
### <a name="parameters"></a>Parametry  
 *Rect –*  
 Zdroj obdélníku  
  
 *fLeft*  
 levou souřadnici zdroje  
  
 *fTop*  
 horní souřadnici zdroje  
  
 *fRight*  
 Zdroj právo souřadnic  
  
 *fBottom*  
 souřadnice dolního zdroje  
  
##  <a name="isnull"></a>  CD2DRectF::IsNull  
 Vrátí logickou hodnotu, která určuje, zda výraz neobsahuje žádná platná data (Null).  
  
```  
BOOL IsNull() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud jsou všechny rovna 0; horní obdélníku, vlevo, dolní a pravé hodnoty jinak hodnota FALSE.  
  
##  <a name="operator_crect"></a>  CD2DRectF::Operator CRect  
 Převede CD2DRectF CRect objektu.  
  
```  
operator CRect();
```   
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální hodnota D2D obdélník.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
