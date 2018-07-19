---
title: Ccomautocriticalsection – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComCriticalSection
- ATLCORE/ATL::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::Init
- ATLCORE/ATL::CComCriticalSection::Lock
- ATLCORE/ATL::CComCriticalSection::Term
- ATLCORE/ATL::CComCriticalSection::Unlock
- ATLCORE/ATL::CComCriticalSection::m_sec
dev_langs:
- C++
helpviewer_keywords:
- CComCriticalSection class
ms.assetid: 44e1edd2-90be-4bfe-9739-58e8b419e7d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5926f92ae636a13c1e5241792790151ee48ceddc
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884867"
---
# <a name="ccomcriticalsection-class"></a>Ccomautocriticalsection – třída
Tato třída poskytuje metody pro získání a uvolnění vlastnictví objektu kritický oddíl.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CComCriticalSection
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComCriticalSection::CComCriticalSection](#ccomcriticalsection)|Konstruktor|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComCriticalSection::Init](#init)|Vytvoří a inicializuje objekt kritický oddíl.|  
|[CComCriticalSection::Lock](#lock)|Získá vlastnictví objektu kritický oddíl.|  
|[CComCriticalSection::Term](#term)|Uvolní prostředky systému použité objektem kritický oddíl.|  
|[CComCriticalSection::Unlock](#unlock)|Uvolní vlastnictví objektu kritický oddíl.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CComCriticalSection::m_sec](#m_sec)|Critical_section – objekt.|  
  
## <a name="remarks"></a>Poznámky  
 `CComCriticalSection` je podobný třídě [ccomautocriticalsection –](../../atl/reference/ccomautocriticalsection-class.md), s tím rozdílem, že je nutné explicitně inicializovat a release kritický oddíl.  
  
 Obvykle použijete `CComCriticalSection` prostřednictvím **typedef** název [criticalsection –](ccommultithreadmodel-class.md#criticalsection). Tento název se odkazuje `CComCriticalSection` při [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) je používán.  

  
 Zobrazit [ccomcritseclock – třída](../../atl/reference/ccomcritseclock-class.md) pro bezpečnější způsob, jak použít tuto třídu než volání `Lock` a `Unlock` přímo.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcore.h  
  
##  <a name="ccomcriticalsection"></a>  CComCriticalSection::CComCriticalSection  
 Konstruktor  
  
```
CComCriticalSection() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Nastaví [m_sec](#m_sec) datový člen na hodnotu NULL.  
  
##  <a name="init"></a>  CComCriticalSection::Init  
 Volá funkci Win32 [InitializeCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms683472), který inicializuje objekt kritický oddíl součástí [m_sec](#m_sec) datový člen.  
  
```
HRESULT Init() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu S_OK při úspěchu, E_OUTOFMEMORY nebo E_FAIL při selhání.  
  
##  <a name="lock"></a>  CComCriticalSection::Lock  
 Volá funkci Win32 [EnterCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682608), které počká, dokud vlákno může převzít vlastnictví kritický oddíl objektů obsažených v [m_sec](#m_sec) datový člen.  
  
```
HRESULT Lock() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu S_OK při úspěchu, E_OUTOFMEMORY nebo E_FAIL při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Objekt kritický oddíl musí nejprve inicializovat pomocí volání [Init](#init) metody. Po dokončení provádění chráněné kódu vlákna musí volat [odemknout](#unlock) uvolnit vlastnictví kritický oddíl.  
  
##  <a name="m_sec"></a>  CComCriticalSection::m_sec  
 Obsahuje objekt kritický oddíl, který se používá ve všech `CComCriticalSection` metody.  
  
```
CRITICAL_SECTION m_sec;
```  
  
##  <a name="term"></a>  CComCriticalSection::Term  
 Volá funkci Win32 [DeleteCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682552), což uvolní všechny prostředky používané objektem kritický oddíl součástí [m_sec](#m_sec) datový člen.  
  
```
HRESULT Term() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu S_OK.  
  
### <a name="remarks"></a>Poznámky  
 Jednou `Term` byla volána, důležité části může již nebude používán k synchronizaci.  
  
##  <a name="unlock"></a>  CComCriticalSection::Unlock  
 Volá funkci Win32 [LeaveCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms684169), která uvolní vlastnictví objektu kritický oddíl součástí [m_sec](#m_sec) datový člen.  
  
```
HRESULT Unlock() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu S_OK.  
  
### <a name="remarks"></a>Poznámky  
 Nejdřív získat vlastnictví, musí volat vlákno [Zámek](#lock) metody. Každé volání `Lock` vyžaduje odpovídající volání `Unlock` uvolnit vlastnictví kritický oddíl.  
  
## <a name="see-also"></a>Viz také  
 [Ccomfakecriticalsection – třída](../../atl/reference/ccomfakecriticalsection-class.md)   
 [Přehled tříd](../../atl/atl-class-overview.md)   
 [CComCritSecLock – třída](../../atl/reference/ccomcritseclock-class.md)
