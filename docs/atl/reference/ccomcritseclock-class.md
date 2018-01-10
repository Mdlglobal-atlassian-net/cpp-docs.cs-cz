---
title: "Třída CComCritSecLock | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComCritSecLock
- ATLBASE/ATL::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::Lock
- ATLBASE/ATL::CComCritSecLock::Unlock
dev_langs: C++
helpviewer_keywords: CComCritSecLock class
ms.assetid: 223152a1-86c3-4ef9-89a7-f455fe791b0e
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1cb07c2cca9394c23c6c3db156e205749f62e3f9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ccomcritseclock-class"></a>CComCritSecLock – třída
Tato třída poskytuje metody pro zamykání a odemykání objekt kritická sekce.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class TLock> class CComCritSecLock
```  
  
#### <a name="parameters"></a>Parametry  
 *TLock*  
 Objekt, který má být uzamčena a odemkne.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComCritSecLock::CComCritSecLock](#ctor)|Konstruktor|  
|[CComCritSecLock:: ~ CComCritSecLock](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComCritSecLock::Lock](#lock)|Volejte tuto metodu za účelem zamknout objekt kritická sekce.|  
|[CComCritSecLock::Unlock](#unlock)|Volejte tuto metodu k odemknutí objekt kritická sekce.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída slouží k zamknutí a odemknutí objekty způsobem bezpečnější než s [CComCriticalSection třída](../../atl/reference/ccomcriticalsection-class.md) nebo [CComAutoCriticalSection třída](../../atl/reference/ccomautocriticalsection-class.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
##  <a name="ctor"></a>CComCritSecLock::CComCritSecLock  
 Konstruktor  
  
```
CComCritSecLock(TLock& cs, bool bInitialLock = true);
```  
  
### <a name="parameters"></a>Parametry  
 *cs*  
 Objekt kritická sekce.  
  
 `bInitialLock`  
 Stav počáteční zámku: **true** znamená uzamčena.  
  
### <a name="remarks"></a>Poznámky  
 Inicializuje objekt kritická sekce.  
  
##  <a name="dtor"></a>CComCritSecLock:: ~ CComCritSecLock  
 Destruktor.  
  
```
~CComCritSecLock() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Odemkne objekt kritická sekce.  
  
##  <a name="lock"></a>CComCritSecLock::Lock  
 Volejte tuto metodu za účelem zamknout objekt kritická sekce.  
  
```
HRESULT Lock() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK, pokud objekt má úspěšně uzamčen nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Pokud není objekt uzamčen, dojde k chybě vyhodnocení v sestavení pro ladění.  
  
##  <a name="unlock"></a>CComCritSecLock::Unlock  
 Volejte tuto metodu k odemknutí objekt kritická sekce.  
  
```
void Unlock() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud již odemknutý objekt, dojde k chybě vyhodnocení v sestavení pro ladění.  
  
## <a name="see-also"></a>Viz také  
 [CComCriticalSection – třída](../../atl/reference/ccomcriticalsection-class.md)   
 [CComAutoCriticalSection – třída](../../atl/reference/ccomautocriticalsection-class.md)
