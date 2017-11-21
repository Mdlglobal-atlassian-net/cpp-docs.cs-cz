---
title: "Třída CAtlException | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlException
- ATLEXCEPT/ATL::CAtlException
- ATLEXCEPT/ATL::CAtlException::CAtlException
- ATLEXCEPT/ATL::CAtlException::m_hr
dev_langs: C++
helpviewer_keywords: CAtlException class
ms.assetid: 3fd7b041-f70d-4292-b947-0d70781d95a8
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b0a22b1918f255290ae6b47604aa57ef484a9527
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="catlexception-class"></a>CAtlException – třída
Tato třída definuje výjimku ATL.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CAtlException
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlException::CAtlException](#catlexception)|Konstruktor|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlException::operator HRESULT](#operator_hresult)|Vrhá aktuální objekt, který má hodnotu HRESULT.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlException::m_hr](#m_hr)|Proměnná typu HRESULT vytvořený objekt a používat k ukládání chybový stav.|  
  
## <a name="remarks"></a>Poznámky  
 A `CAtlException` objekt představuje podmínku výjimky související s ATL operace. `CAtlException` Třída zahrnuje veřejná data člena, který ukládá stavový kód označující důvod výjimku a operátor přetypování, který vám umožní zacházet s výjimkou, jako by šlo HRESULT.  
  
 Obecně platí, zavolá `AtlThrow` místo vytvoření `CAtlException` objektu přímo.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlexcept.h  
  
##  <a name="catlexception"></a>CAtlException::CAtlException  
 Konstruktor  
  
```
CAtlException(HRESULT hr) throw();
CAtlException() throw();
```  
  
### <a name="parameters"></a>Parametry  
 `hr`  
 `HRESULT` Kód chyby.  
  
##  <a name="operator_hresult"></a>CAtlException::operator HRESULT 
 Vrhá aktuální objekt, který má hodnotu HRESULT.  
  
```  
operator HRESULT() const throw ();
```  
  
##  <a name="m_hr"></a>CAtlException::m_hr  
 `HRESULT` – Datový člen.  
  
```
HRESULT m_hr;
```  
  
### <a name="remarks"></a>Poznámky  
 Data člena, který ukládá chybový stav. Hodnota HRESULT je nastavena pomocí konstruktoru, [CAtlException::CAtlException](#catlexception).  
  
## <a name="see-also"></a>Viz také  
 [AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)   
 [Přehled třídy](../../atl/atl-class-overview.md)
