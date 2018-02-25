---
title: "Itopologynode – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ITopologyNode
- CONCRTRM/concurrency::ITopologyNode
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetExecutionResourceCount
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetFirstExecutionResource
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetId
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetNext
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetNumaNode
dev_langs:
- C++
helpviewer_keywords:
- ITopologyNode structure
ms.assetid: 92e7e032-04f6-4c7c-be36-8f9a35fc4734
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6fcab5f66af46989e0487657e018531423fd5f48
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="itopologynode-structure"></a>ITopologyNode – struktura
Rozhraní pro uzel topologie, jak jsou definovány pomocí Správce prostředků. Uzel obsahuje jeden nebo více prostředků provádění.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct ITopologyNode;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Itopologynode::getexecutionresourcecount –](#getexecutionresourcecount)|Vrátí počet prostředků provádění seskupeny dohromady v rámci tohoto uzlu.|  
|[Itopologynode::getfirstexecutionresource –](#getfirstexecutionresource)|Vrátí první provádění prostředku seskupené v rámci tohoto uzlu v pořadí výčtu.|  
|[Itopologynode::getid –](#getid)|Vrátí správce prostředků jedinečný identifikátor pro tento uzel.|  
|[Itopologynode::GetNext –](#getnext)|Vrátí rozhraní na další uzel topologie v pořadí výčtu.|  
|[ITopologyNode::GetNumaNode](#getnumanode)|Vrátí Windows přiřadit číslo uzlu NUMA, do které patří tento uzel Maanger prostředků.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní je obvykle využité vás topologii tohoto systému jako zjištěnými Resource Manager.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `ITopologyNode`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrtrm.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="getexecutionresourcecount"></a>  Itopologynode::getexecutionresourcecount – metoda  
 Vrátí počet prostředků provádění seskupeny dohromady v rámci tohoto uzlu.  
  
```
virtual unsigned int GetExecutionResourceCount() const = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet prostředků provádění seskupeny v rámci tohoto uzlu.  
  
##  <a name="getfirstexecutionresource"></a>  Itopologynode::getfirstexecutionresource – metoda  
 Vrátí první provádění prostředku seskupené v rámci tohoto uzlu v pořadí výčtu.  
  
```
virtual ITopologyExecutionResource *GetFirstExecutionResource() const = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Na první prostředek provádění seskupené v rámci tohoto uzlu v pořadí výčtu.  
  
##  <a name="getid"></a>  Itopologynode::getid – metoda  
 Vrátí správce prostředků jedinečný identifikátor pro tento uzel.  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Správce prostředků jedinečný identifikátor pro tento uzel.  
  
### <a name="remarks"></a>Poznámky  
 Concurrency Runtime představuje vláken hardwaru systému ve skupinách uzlů procesoru. Uzly jsou obvykle odvozená od hardwarovou topologii systému. Všechny procesory na konkrétní soketu nebo konkrétní uzel NUMA se například může patřit do stejného uzlu procesoru. Resource Manager přiřadí tyto uzly počínaje jedinečné identifikátory `0` včetně `nodeCount - 1`, kde `nodeCount` představuje celkový počet uzlů procesoru v systému.  
  
 Počet uzlů můžete získat z funkce [getprocessornodecount –](concurrency-namespace-functions.md).  
  
##  <a name="getnext"></a>  Itopologynode::GetNext – metoda  
 Vrátí rozhraní na další uzel topologie v pořadí výčtu.  
  
```
virtual ITopologyNode *GetNext() const = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Rozhraní na další uzel v pořadí výčtu. Pokud v pořadí výčtu topologie systému nejsou žádné další uzly, tato metoda vrátí hodnotu `NULL`.  
  
##  <a name="getnumanode"></a>  Itopologynode::getnumanode – metoda  
 Vrátí Windows přiřadit číslo uzlu NUMA, do které patří tento uzel Maanger prostředků.  
  
```
virtual unsigned long GetNumaNode() const = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Windows přiřadit číslo uzlu NUMA, do které patří tento uzel Resource Manager.  
  
### <a name="remarks"></a>Poznámky  
 Vlákno proxy systémem virtuálních procesorů kořenové patřící do tohoto uzlu bude mít spřažení s alespoň na úrovni uzlu NUMA pro uzel NUMA vrácená touto metodou.  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
