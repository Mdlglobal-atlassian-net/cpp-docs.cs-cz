---
title: Třída CD2DSizeF | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::IsNull
dev_langs:
- C++
helpviewer_keywords:
- CD2DSizeF [MFC], CD2DSizeF
- CD2DSizeF [MFC], IsNull
ms.assetid: f486a1e1-997d-4286-8cb9-26369dc82055
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e939d189d991ef234e940b272291c2da6c931684
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954475"
---
# <a name="cd2dsizef-class"></a>CD2DSizeF – třída
Obálka pro D2D1_SIZE_F.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CD2DSizeF : public D2D1_SIZE_F;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DSizeF::CD2DSizeF](#cd2dsizef)|Přetíženo. Vytvoří `CD2DSizeF` objektu z `D2D1_SIZE_F` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DSizeF::IsNull](#isnull)|Vrátí **boolean** hodnotu, která určuje, zda výraz neobsahuje žádná platná data ( **null**).|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DSizeF::Operator CSize](#operator_csize)|Převede `CD2DSizeF` k `CSize` objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `D2D1_SIZE_F`  
  
 [CD2DSizeF](../../mfc/reference/cd2dsizef-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxrendertarget.h  
  
##  <a name="cd2dsizef"></a>  CD2DSizeF::CD2DSizeF  
 Vytvoří objekt CD2DSizeF z CSize objektu.  
  
```  
CD2DSizeF(const CSize& size);  
CD2DSizeF(const D2D1_SIZE_F& size);  
  CD2DSizeF(const D2D1_SIZE_F* size);

 
CD2DSizeF(
    FLOAT cx = 0.,  
    FLOAT cy = 0.);
```  
  
### <a name="parameters"></a>Parametry  
 *Velikost*  
 velikost zdroje  
  
 *CX*  
 Šířka zdroje  
  
 *CY*  
 výška zdroje  
  
##  <a name="isnull"></a>  CD2DSizeF::IsNull  
 Vrátí logickou hodnotu, která určuje, zda výraz neobsahuje žádná platná data (Null).  
  
```  
BOOL IsNull() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud jsou prázdné; šířku a výšku. jinak hodnota FALSE.  
  
##  <a name="operator_csize"></a>  CD2DSizeF::Operator CSize  
 Převede CD2DSizeF CSize objektu.  
  
```  
operator CSize();
```   
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální hodnota velikosti D2D.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
