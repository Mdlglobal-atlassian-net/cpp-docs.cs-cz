---
title: Ccomsimplethreadallocator – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator::GetThread
dev_langs:
- C++
helpviewer_keywords:
- threading [ATL], selecting threads
- ATL threads
- CComSimpleThreadAllocator class
- ATL threads, allocating
ms.assetid: 66b2166a-8c50-49fd-b8e4-7f293470327d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b2c571733aca48ddbfd881a294786d1de334c7c3
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884662"
---
# <a name="ccomsimplethreadallocator-class"></a>Ccomsimplethreadallocator – třída
Tato třída spravuje výběr vlákna pro třídu `CComAutoThreadModule`.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CComSimpleThreadAllocator
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComSimpleThreadAllocator::GetThread](#getthread)|Vybere vlákno.|  
  
## <a name="remarks"></a>Poznámky  
 `CComSimpleThreadAllocator` spravuje výběr vlákna pro [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md). `CComSimpleThreadAllocator::GetThread` jednoduše projde každé vlákno a vrátí dalším objektem v sekvenci.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
##  <a name="getthread"></a>  CComSimpleThreadAllocator::GetThread  
 Vybere vlákna tak, že zadáte další vlákno v sekvenci.  
  
```
int GetThread(CComApartment* /* pApt */, int nThreads);
```  
  
### <a name="parameters"></a>Parametry  
 *pApt*  
 Nepoužívá se v ATL výchozí implementaci.  
  
 *nThreads*  
 Maximální počet vláken v modulu souboru EXE.  
  
### <a name="return-value"></a>Návratová hodnota  
 Celé číslo mezi nulou a (*nThreads* – 1). Určuje jedno z vláken v modulu souboru EXE.  
  
### <a name="remarks"></a>Poznámky  
 Můžete přepsat `GetThread` nabízejí jiný způsob výběru a vytvoříte využívání *pApt* parametru.  
  
 `GetThread` je volán [CComAutoThreadModule::CreateInstance](../../atl/reference/ccomautothreadmodule-class.md#createinstance).  
  
## <a name="see-also"></a>Viz také  
 [Ccomapartment – třída](../../atl/reference/ccomapartment-class.md)   
 [Přehled tříd](../../atl/atl-class-overview.md)
