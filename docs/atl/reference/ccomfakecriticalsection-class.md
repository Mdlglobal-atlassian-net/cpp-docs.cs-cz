---
title: "Třída CComFakeCriticalSection | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection::Init
- ATLCORE/ATL::CComFakeCriticalSection::Lock
- ATLCORE/ATL::CComFakeCriticalSection::Term
- ATLCORE/ATL::CComFakeCriticalSection::Unlock
dev_langs: C++
helpviewer_keywords: CComFakeCriticalSection class
ms.assetid: a4811b97-96bb-493b-ab9f-62822aeddb10
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b0619dc44c630ea272531fdf6ef5f5da3a487d65
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ccomfakecriticalsection-class"></a>CComFakeCriticalSection – třída
Tato třída poskytuje stejné metody jako [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) , ale neposkytuje kritická sekce.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CComFakeCriticalSection
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComFakeCriticalSection::Init](#init)|Neprovede žádnou akci, protože neexistuje žádný kritická sekce.|  
|[CComFakeCriticalSection::Lock](#lock)|Neprovede žádnou akci, protože neexistuje žádný kritická sekce.|  
|[CComFakeCriticalSection::Term](#term)|Neprovede žádnou akci, protože neexistuje žádný kritická sekce.|  
|[CComFakeCriticalSection::Unlock](#unlock)|Neprovede žádnou akci, protože neexistuje žádný kritická sekce.|  
  
## <a name="remarks"></a>Poznámky  
 `CComFakeCriticalSection`Zrcadlí metody nalezen v [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md). Ale `CComFakeCriticalSection` neposkytuje kritická sekce; proto její metody Neprovádět žádnou akci.  
  
 Obvykle použijete, `CComFakeCriticalSection` prostřednictvím `typedef` název buď `AutoCriticalSection` nebo `CriticalSection`. Při použití [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) nebo [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md), obě tyto `typedef` názvy odkaz `CComFakeCriticalSection`. Při použití [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md), že odkaz [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md) a `CComCriticalSection`, v uvedeném pořadí.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcore.h  
  
##  <a name="init"></a>CComFakeCriticalSection::Init  
 Neprovede žádnou akci, protože neexistuje žádný kritická sekce.  
  
```
HRESULT Init() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK.  
  
##  <a name="lock"></a>CComFakeCriticalSection::Lock  
 Neprovede žádnou akci, protože neexistuje žádný kritická sekce.  
  
```
HRESULT Lock() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK.  
  
##  <a name="term"></a>CComFakeCriticalSection::Term  
 Neprovede žádnou akci, protože neexistuje žádný kritická sekce.  
  
```
HRESULT Term() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK.  
  
##  <a name="unlock"></a>CComFakeCriticalSection::Unlock  
 Neprovede žádnou akci, protože neexistuje žádný kritická sekce.  
  
```
HRESULT Unlock() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)
