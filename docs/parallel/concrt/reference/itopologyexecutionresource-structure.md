---
title: Itopologyexecutionresource – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetId
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetNext
dev_langs:
- C++
helpviewer_keywords:
- ITopologyExecutionResource structure
ms.assetid: e36756f7-4cd9-4fa6-ba60-23fea58ef2bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: adb456315b2c6d15b7a3696df9a6845a2bd2b899
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="itopologyexecutionresource-structure"></a>ITopologyExecutionResource – struktura
Rozhraní k provádění prostředku definovaným pomocí Správce prostředků.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct ITopologyExecutionResource;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Itopologyexecutionresource::getid –](#getid)|Vrací jedinečný identifikátor tohoto provádění prostředku správce prostředků.|  
|[Itopologyexecutionresource::GetNext –](#getnext)|Vrátí rozhraní k další provádění prostředku v pořadí výčtu.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní je obvykle využité vás topologii tohoto systému jako zjištěnými Resource Manager.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `ITopologyExecutionResource`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrtrm.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="getid"></a>  Itopologyexecutionresource::getid – metoda  
 Vrací jedinečný identifikátor tohoto provádění prostředku správce prostředků.  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Správce prostředků jedinečný identifikátor pro tento prostředek provádění.  
  
##  <a name="getnext"></a>  Itopologyexecutionresource::GetNext – metoda  
 Vrátí rozhraní k další provádění prostředku v pořadí výčtu.  
  
```
virtual ITopologyExecutionResource *GetNext() const = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Rozhraní k další provádění prostředku v pořadí výčtu. Pokud nejsou žádné další uzly v pořadí výčtu uzlu, ke kterému patří tohoto provádění prostředku, tato metoda vrátí hodnotu `NULL`.  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
