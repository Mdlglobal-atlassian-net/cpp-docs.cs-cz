---
title: Třída CD2DSizeU | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::IsNull
dev_langs:
- C++
helpviewer_keywords:
- CD2DSizeU [MFC], CD2DSizeU
- CD2DSizeU [MFC], IsNull
ms.assetid: 6e679ba8-2112-43c3-8275-70b660856f02
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa7c42216f55479050812b559f533829d55162b9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349932"
---
# <a name="cd2dsizeu-class"></a>CD2DSizeU – třída
Obálka pro D2D1_SIZE_U.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CD2DSizeU : public D2D1_SIZE_U;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DSizeU::CD2DSizeU](#cd2dsizeu)|Přetíženo. Vytvoří `CD2DSizeU` objektu z `D2D1_SIZE_U` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DSizeU::IsNull](#isnull)|Vrátí `boolean` hodnotu, která určuje, zda výraz neobsahuje žádná platná data ( `null`).|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CD2DSizeU::Operator CSize](#operator_csize)|Převede `CD2DSizeU` k `CSize` objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `D2D1_SIZE_U`  
  
 [CD2DSizeU](../../mfc/reference/cd2dsizeu-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxrendertarget.h  
  
##  <a name="cd2dsizeu"></a>  CD2DSizeU::CD2DSizeU  
 Vytvoří objekt CD2DSizeU z CSize objektu.  
  
```  
CD2DSizeU(const CSize& size);  
CD2DSizeU(const D2D1_SIZE_U& size);  
  CD2DSizeU(const D2D1_SIZE_U* size);

 
CD2DSizeU(
    UINT32 cx = 0,  
    UINT32 cy = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `size`  
 velikost zdroje  
  
 `cx`  
 Šířka zdroje  
  
 `cy`  
 výška zdroje  
  
##  <a name="isnull"></a>  CD2DSizeU::IsNull  
 Vrátí logickou hodnotu, která určuje, zda výraz neobsahuje žádná platná data (Null).  
  
```  
BOOL IsNull() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud jsou prázdné; šířku a výšku. jinak hodnota FALSE.  
  
##  <a name="operator_csize"></a>  CD2DSizeU::Operator CSize  
 Převede CD2DSizeU CSize objektu.  
  
```  
operator CSize();
```   
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální hodnota velikosti D2D.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
