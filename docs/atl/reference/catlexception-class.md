---
title: Třída CAtlException | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlException
- ATLEXCEPT/ATL::CAtlException
- ATLEXCEPT/ATL::CAtlException::CAtlException
- ATLEXCEPT/ATL::CAtlException::m_hr
dev_langs:
- C++
helpviewer_keywords:
- CAtlException class
ms.assetid: 3fd7b041-f70d-4292-b947-0d70781d95a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aaafdf42d218e2c3bca1e8ee28c27898f80bcf40
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357867"
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
  
##  <a name="catlexception"></a>  CAtlException::CAtlException  
 Konstruktor  
  
```
CAtlException(HRESULT hr) throw();
CAtlException() throw();
```  
  
### <a name="parameters"></a>Parametry  
 `hr`  
 `HRESULT` Kód chyby.  
  
##  <a name="operator_hresult"></a>  CAtlException::operator HRESULT 
 Vrhá aktuální objekt, který má hodnotu HRESULT.  
  
```  
operator HRESULT() const throw ();
```  
  
##  <a name="m_hr"></a>  CAtlException::m_hr  
 `HRESULT` – Datový člen.  
  
```
HRESULT m_hr;
```  
  
### <a name="remarks"></a>Poznámky  
 Data člena, který ukládá chybový stav. Hodnota HRESULT je nastavena pomocí konstruktoru, [CAtlException::CAtlException](#catlexception).  
  
## <a name="see-also"></a>Viz také  
 [AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)   
 [Přehled třídy](../../atl/atl-class-overview.md)
