---
title: "Rozhraní IWorkerThreadClient | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IWorkerThreadClient
- ATLUTIL/ATL::IWorkerThreadClient
- ATLUTIL/ATL::CloseHandle
- ATLUTIL/ATL::Execute
dev_langs: C++
helpviewer_keywords: IWorkerThreadClient interface
ms.assetid: 56f4a2f5-007e-4a33-9e20-05187629f715
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 86b0578b3fbe16d21a12edf2ac5eb91528419e83
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="iworkerthreadclient-interface"></a>IWorkerThreadClient rozhraní
`IWorkerThreadClient`představuje rozhraní implementované klienty [CWorkerThread](../../atl/reference/cworkerthread-class.md) třídy.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
__interface IWorkerThreadClient
```  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Funkce CloseHandle](#closehandle)|Implementujte tuto metodu zavřít popisovač přidružené k tomuto objektu.|  
|[Spuštění](#execute)|Implementujte tuto metodu ke spouštění kódu, když se změní na signál popisovač přidružené k tomuto objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní implementujte, když máte kód, který je potřeba spustit na pracovní vlákno v reakci na signál, aby se aktivovala popisovač.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlutil.h  
  
##  <a name="closehandle"></a>IWorkerThreadClient::CloseHandle  
 Implementujte tuto metodu zavřít popisovač přidružené k tomuto objektu.  
  
```
HRESULT CloseHandle(HANDLE  hHandle);
```  
  
### <a name="parameters"></a>Parametry  
 *hHandle*  
 Popisovač bude uzavřen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK na úspěch nebo Chyba HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Popisovač předaná této metodě je dříve spojené s tímto objektem voláním [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).  
  
### <a name="example"></a>Příklad  
 Následující kód ukazuje jednoduchou implementaci `IWorkerThreadClient::CloseHandle`.  
  
 [!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iworkerthreadclient-interface_1.cpp)]  
  
##  <a name="execute"></a>IWorkerThreadClient::Execute  
 Implementujte tuto metodu ke spouštění kódu, když se změní na signál popisovač přidružené k tomuto objektu.  
  
```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```  
  
### <a name="parameters"></a>Parametry  
 `dwParam`  
 Tento parametr.  
  
 `hObject`  
 Obslužná rutina, který má být signál.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK na úspěch nebo Chyba HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Popisovač a DWORD/ukazatele předaná této metodě byly dříve přidružená k tomuto objektu voláním [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).  
  
### <a name="example"></a>Příklad  
 Následující kód ukazuje jednoduchou implementaci `IWorkerThreadClient::Execute`.  
  
 [!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iworkerthreadclient-interface_2.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../atl/reference/atl-classes.md)   
 [CWorkerThread – třída](../../atl/reference/cworkerthread-class.md)
