---
title: "Třída CComCriticalSection | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
helpviewer_keywords: CComCriticalSection class
ms.assetid: 44e1edd2-90be-4bfe-9739-58e8b419e7d1
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ef8ca542ef9bda72bd89b633d42db727bce3e94a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ccomcriticalsection-class"></a>CComCriticalSection – třída
Tato třída poskytuje metody pro získání a uvolněním vlastnictví objektu kritická sekce.  
  
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
|[CComCriticalSection::Init](#init)|Vytvoří a inicializuje objekt kritická sekce.|  
|[CComCriticalSection::Lock](#lock)|Získá vlastnictví objektu kritická sekce.|  
|[CComCriticalSection::Term](#term)|Uvolní prostředky systému využívané objektem kritická sekce.|  
|[CComCriticalSection::Unlock](#unlock)|Uvolní vlastnictví objektu kritická sekce.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CComCriticalSection::m_sec](#m_sec)|A **CRITICAL_SECTION** objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `CComCriticalSection`je podobná třída [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)kromě toho, že je nutné explicitně inicializaci a verze kritická sekce.  
  
 Obvykle použijete, `CComCriticalSection` prostřednictvím `typedef` název [CriticalSection](ccommultithreadmodel-class.md#criticalsection). Tento název odkazuje `CComCriticalSection` při [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) je používán.  

  
 V tématu [CComCritSecLock třída](../../atl/reference/ccomcritseclock-class.md) pro bezpečnější způsob, jak použít tuto třídu než volání `Lock` a `Unlock` přímo.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcore.h  
  
##  <a name="ccomcriticalsection"></a>CComCriticalSection::CComCriticalSection  
 Konstruktor  
  
```
CComCriticalSection() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Nastaví [m_sec](#m_sec) – datový člen na hodnotu NULL **.**  
  
##  <a name="init"></a>CComCriticalSection::Init  
 Volá funkci Win32 [InitializeCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms683472), který inicializuje objekt kritická sekce součástí [m_sec](#m_sec) – datový člen.  
  
```
HRESULT Init() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` v případě úspěchu **E_OUTOFMEMORY** nebo **E_FAIL** při selhání.  
  
##  <a name="lock"></a>CComCriticalSection::Lock  
 Volá funkci Win32 [EnterCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682608), které počká na vlákno může převzít vlastnictví obsažené v objektu kritická sekce [m_sec](#m_sec) – datový člen.  
  
```
HRESULT Lock() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` v případě úspěchu **E_OUTOFMEMORY** nebo **E_FAIL** při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Objekt kritická sekce se musí nejprve inicializovat pomocí volání [Init](#init) metoda. Po dokončení provádění kód chráněné musí volat vlákno [odemčení](#unlock) k uvolnění vlastnictví kritická sekce.  
  
##  <a name="m_sec"></a>CComCriticalSection::m_sec  
 Obsahuje kritická sekce objekt, který je používán všechny `CComCriticalSection` metody.  
  
```
CRITICAL_SECTION m_sec;
```  
  
##  <a name="term"></a>CComCriticalSection::Term  
 Volá funkci Win32 [DeleteCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682552), což uvolní všechny prostředky používané objektem kritická sekce součástí [m_sec](#m_sec) – datový člen.  
  
```
HRESULT Term() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 Jednou `Term` byla volána, důležité části můžete již nebude používán k synchronizaci.  
  
##  <a name="unlock"></a>CComCriticalSection::Unlock  
 Volá funkci Win32 [LeaveCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms684169), což uvolní vlastnictví obsažené v objektu kritická sekce [m_sec](#m_sec) – datový člen.  
  
```
HRESULT Unlock() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 Nejdřív získat vlastnictví, musí volat vlákno [zámku](#lock) metoda. Každé volání `Lock` vyžaduje odpovídající volání `Unlock` k uvolnění vlastnictví kritická sekce.  
  
## <a name="see-also"></a>Viz také  
 [CComFakeCriticalSection – třída](../../atl/reference/ccomfakecriticalsection-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [CComCritSecLock – třída](../../atl/reference/ccomcritseclock-class.md)