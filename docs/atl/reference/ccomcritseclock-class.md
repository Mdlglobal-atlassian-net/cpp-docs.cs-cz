---
title: Třída CComCritSecLock | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComCritSecLock
- ATLBASE/ATL::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::Lock
- ATLBASE/ATL::CComCritSecLock::Unlock
dev_langs:
- C++
helpviewer_keywords:
- CComCritSecLock class
ms.assetid: 223152a1-86c3-4ef9-89a7-f455fe791b0e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 98b6eb7a8e6df16134573b55a7c9666befe4e4a1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358883"
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
  
##  <a name="ctor"></a>  CComCritSecLock::CComCritSecLock  
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
  
##  <a name="dtor"></a>  CComCritSecLock:: ~ CComCritSecLock  
 Destruktor.  
  
```
~CComCritSecLock() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Odemkne objekt kritická sekce.  
  
##  <a name="lock"></a>  CComCritSecLock::Lock  
 Volejte tuto metodu za účelem zamknout objekt kritická sekce.  
  
```
HRESULT Lock() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK, pokud objekt má úspěšně uzamčen nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Pokud není objekt uzamčen, dojde k chybě vyhodnocení v sestavení pro ladění.  
  
##  <a name="unlock"></a>  CComCritSecLock::Unlock  
 Volejte tuto metodu k odemknutí objekt kritická sekce.  
  
```
void Unlock() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud již odemknutý objekt, dojde k chybě vyhodnocení v sestavení pro ladění.  
  
## <a name="see-also"></a>Viz také  
 [CComCriticalSection – třída](../../atl/reference/ccomcriticalsection-class.md)   
 [CComAutoCriticalSection – třída](../../atl/reference/ccomautocriticalsection-class.md)
