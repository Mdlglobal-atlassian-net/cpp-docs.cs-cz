---
title: "Třída CComApartment | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComApartment
- ATLBASE/ATL::CComApartment
- ATLBASE/ATL::CComApartment::CComApartment
- ATLBASE/ATL::CComApartment::Apartment
- ATLBASE/ATL::CComApartment::GetLockCount
- ATLBASE/ATL::CComApartment::Lock
- ATLBASE/ATL::CComApartment::Unlock
- ATLBASE/ATL::CComApartment::m_dwThreadID
- ATLBASE/ATL::CComApartment::m_hThread
- ATLBASE/ATL::CComApartment::m_nLockCnt
dev_langs: C++
helpviewer_keywords:
- apartments in ATL EXE modules
- CComApartment class
ms.assetid: dbc177d7-7ee4-45f2-b563-d578a467ca93
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a3fecd77e93c0c51a37d7363e6ec1472d157d6d1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ccomapartment-class"></a>CComApartment – třída
Tato třída poskytuje podporu pro správu appartment v modulu EXE ve fondu vláken.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CComApartment
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComApartment::CComApartment](#ccomapartment)|Konstruktor|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComApartment::Apartment](#apartment)|Označí vlákna počáteční adresa.|  
|[CComApartment::GetLockCount](#getlockcount)|Vrátí aktuální počet zámků vlákna.|  
|[CComApartment::Lock](#lock)|Zvýší počet zámků vlákna.|  
|[CComApartment::Unlock](#unlock)|Snižuje počet vlákna zámku.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CComApartment::m_dwThreadID](#m_dwthreadid)|Obsahuje identifikátor vlákna.|  
|[CComApartment::m_hThread](#m_hthread)|Obsahuje popisovač vlákna.|  
|[CComApartment::m_nLockCnt](#m_nlockcnt)|Obsahuje aktuální počet zámků vlákna.|  
  
## <a name="remarks"></a>Poznámky  
 `CComApartment`používá [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) ke správě v modulu EXE ve fondu vláken typu apartment. `CComApartment`poskytuje metody pro zvyšování a dekrementace zámek počet na vlákno.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
##  <a name="apartment"></a>CComApartment::Apartment  
 Označí vlákna počáteční adresa.  
  
```
DWORD Apartment();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy 0.  
  
### <a name="remarks"></a>Poznámky  
 Automaticky nastaví během [CComAutoThreadModule::Init](../../atl/reference/ccomautothreadmodule-class.md#init).  
  
##  <a name="ccomapartment"></a>CComApartment::CComApartment  
 Konstruktor  
  
```
CComApartment();
```  
  
### <a name="remarks"></a>Poznámky  
 Inicializuje `CComApartment` datové členy [m_nLockCnt](#m_nlockcnt) a [m_hThread](#m_hthread).  
  
##  <a name="getlockcount"></a>CComApartment::GetLockCount  
 Vrátí aktuální počet zámků vlákna.  
  
```
LONG GetLockCount();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet zámku na vlákno.  
  
##  <a name="lock"></a>CComApartment::Lock  
 Zvýší počet zámků vlákna.  
  
```
LONG Lock();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota, která může být užitečné pro diagnostiku nebo testování.  
  
### <a name="remarks"></a>Poznámky  
 Voláno rozhraním [CComAutoThreadModule::Lock](../../atl/reference/ccomautothreadmodule-class.md#lock).  
  
 Počet zámku na vlákno se používá pro účely statistiky.  
  
##  <a name="m_dwthreadid"></a>CComApartment::m_dwThreadID  
 Obsahuje identifikátor vlákna.  
  
```
DWORD m_dwThreadID;
```  
  
##  <a name="m_hthread"></a>CComApartment::m_hThread  
 Obsahuje popisovač vlákna.  
  
```
HANDLE m_hThread;
```  
  
##  <a name="m_nlockcnt"></a>CComApartment::m_nLockCnt  
 Obsahuje aktuální počet zámků vlákna.  
  
```
LONG m_nLockCnt;
```  
  
##  <a name="unlock"></a>CComApartment::Unlock  
 Snižuje počet vlákna zámku.  
  
```
LONG Unlock();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota, která může být užitečné pro diagnostiku nebo testování.  
  
### <a name="remarks"></a>Poznámky  
 Voláno rozhraním [CComAutoThreadModule::Unlock](../../atl/reference/ccomautothreadmodule-class.md#lock).  
  
 Počet zámku na vlákno se používá pro účely statistiky.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)
