---
title: "Itopologyexecutionresource – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetId
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetNext
dev_langs: C++
helpviewer_keywords: ITopologyExecutionResource structure
ms.assetid: e36756f7-4cd9-4fa6-ba60-23fea58ef2bf
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9ffe0e2d8f4c26274a71082bec2cecaf19acb1af
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
  
##  <a name="getid"></a>Itopologyexecutionresource::getid – metoda  
 Vrací jedinečný identifikátor tohoto provádění prostředku správce prostředků.  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Správce prostředků jedinečný identifikátor pro tento prostředek provádění.  
  
##  <a name="getnext"></a>Itopologyexecutionresource::GetNext – metoda  
 Vrátí rozhraní k další provádění prostředku v pořadí výčtu.  
  
```
virtual ITopologyExecutionResource *GetNext() const = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Rozhraní k další provádění prostředku v pořadí výčtu. Pokud nejsou žádné další uzly v pořadí výčtu uzlu, ke kterému patří tohoto provádění prostředku, tato metoda vrátí hodnotu `NULL`.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)
