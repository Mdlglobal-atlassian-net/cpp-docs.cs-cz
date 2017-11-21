---
title: "Třída CComSimpleThreadAllocator | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator::GetThread
dev_langs: C++
helpviewer_keywords:
- threading [ATL], selecting threads
- ATL threads
- CComSimpleThreadAllocator class
- ATL threads, allocating
ms.assetid: 66b2166a-8c50-49fd-b8e4-7f293470327d
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 150abb28f84d31e1ef6785f9109844529f10276d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ccomsimplethreadallocator-class"></a>CComSimpleThreadAllocator – třída
Tato třída spravuje výběr vlákno pro třídu `CComAutoThreadModule`.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CComSimpleThreadAllocator
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComSimpleThreadAllocator::GetThread](#getthread)|Vybere vlákna.|  
  
## <a name="remarks"></a>Poznámky  
 `CComSimpleThreadAllocator`spravuje přístup z více vláken výběr [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md). `CComSimpleThreadAllocator::GetThread`jednoduše procházení každé vlákno a vrátí následuje v sekvenci.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
##  <a name="getthread"></a>CComSimpleThreadAllocator::GetThread  
 Vybere vlákna tak, že zadáte další vlákno v pořadí.  
  
```
int GetThread(CComApartment* /* pApt */, int nThreads);
```  
  
### <a name="parameters"></a>Parametry  
 `pApt`  
 Nepoužívá se v ATL pro výchozí implementace.  
  
 `nThreads`  
 Maximální počet vláken v modulu EXE.  
  
### <a name="return-value"></a>Návratová hodnota  
 Celé číslo mezi nulou a ( `nThreads` - 1). Označuje jeden vláken v modulu EXE.  
  
### <a name="remarks"></a>Poznámky  
 Můžete přepsat `GetThread` zadat jinou metodu výběru nebo chcete-li použít `pApt` parametr.  
  
 `GetThread`je volána metodou [CComAutoThreadModule::CreateInstance](../../atl/reference/ccomautothreadmodule-class.md#createinstance).  
  
## <a name="see-also"></a>Viz také  
 [CComApartment – třída](../../atl/reference/ccomapartment-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
