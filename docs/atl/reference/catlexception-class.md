---
title: Catlexception – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: fed15dc2348fa540c1f33e7742c5cbcda96b5846
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882530"
---
# <a name="catlexception-class"></a>Catlexception – třída
Tato třída definuje ATL výjimky.  
  
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
|[CAtlException::operator HRESULT](#operator_hresult)|Přetypování aktuálního objektu na hodnotu HRESULT.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlException::m_hr](#m_hr)|Proměnné typu HRESULT vytvořil objekt a využívá k ukládání chybového stavu.|  
  
## <a name="remarks"></a>Poznámky  
 A `CAtlException` objekt představuje podmínku výjimky vztahující se k operaci ATL. `CAtlException` Třída zahrnuje data veřejného člena, který ukládá stavový kód označující důvod pro výjimky a operátor přetypování, který umožňuje zpracovávat výjimky, jako by šlo HRESULT.  
  
 Obecně platí, bude volat `AtlThrow` místo vytvoření `CAtlException` objektu přímo.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlexcept.h  
  
##  <a name="catlexception"></a>  CAtlException::CAtlException  
 Konstruktor  
  
```
CAtlException(HRESULT hr) throw();
CAtlException() throw();
```  
  
### <a name="parameters"></a>Parametry  
 *hr*  
 Kód chyby HRESULT.  
  
##  <a name="operator_hresult"></a>  CAtlException::operator HRESULT 
 Přetypování aktuálního objektu na hodnotu HRESULT.  
  
```  
operator HRESULT() const throw ();
```  
  
##  <a name="m_hr"></a>  CAtlException::m_hr  
 Datový člen HRESULT.  
  
```
HRESULT m_hr;
```  
  
### <a name="remarks"></a>Poznámky  
 Datový člen, který ukládá chybového stavu. Konstruktor, je nastavit hodnotu HRESULT [CAtlException::CAtlException](#catlexception).  
  
## <a name="see-also"></a>Viz také  
 [AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)   
 [Přehled tříd](../../atl/atl-class-overview.md)
