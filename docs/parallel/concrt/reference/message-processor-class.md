---
title: "message_processor – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- message_processor
- AGENTS/concurrency::message_processor
- AGENTS/concurrency::message_processor::async_send
- AGENTS/concurrency::message_processor::sync_send
- AGENTS/concurrency::message_processor::wait
- AGENTS/concurrency::message_processor::process_incoming_message
dev_langs:
- C++
helpviewer_keywords:
- message_processor class
ms.assetid: 23afb052-daa7-44ed-bf24-d2513db748da
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a7646020bd30b817957cea87dad8ec5c7f3aa8ed
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="messageprocessor-class"></a>message_processor – třída
`message_processor` Třída je abstraktní základní třída pro zpracování `message` objekty. Neexistuje žádná záruka řazení zpráv v.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>
class message_processor;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Datový typ datové části v rámci zpráv zpracovávají to `message_processor` objektu.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`type`|Typ aliasu pro `T`.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[async_send](#async_send)|Při přepisu v odvozené třídě, umístí zprávy asynchronně do bloku.|  
|[sync_send](#sync_send)|Při přepisu v odvozené třídě, umístí zprávy synchronně do bloku.|  
|[wait](#wait)|Při přepisu v odvozené třídě, čeká na dokončení všech asynchronních operací.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[process_incoming_message](#process_incoming_message)|Při přepisu v odvozené třídě, provede dopředného zpracování zpráv do bloku. Volá se jednou pokaždé, když je přidána nové zprávy a fronty se zjistí, být prázdný.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `message_processor`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** agents.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="async_send"></a> async_send – 

 Při přepisu v odvozené třídě, umístí zprávy asynchronně do bloku.  
  
```
virtual void async_send(_Inout_opt_ message<T>* _Msg) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_Msg`  
 A `message` objekt, který chcete odeslat asynchronně.  
  
### <a name="remarks"></a>Poznámky  
 Implementace zpracovatelů by měly přepsat tuto metodu.  
  
##  <a name="process_incoming_message"></a> process_incoming_message – 

 Při přepisu v odvozené třídě, provede dopředného zpracování zpráv do bloku. Volá se jednou pokaždé, když je přidána nové zprávy a fronty se zjistí, být prázdný.  
  
```
virtual void process_incoming_message() = 0;
```  
  
### <a name="remarks"></a>Poznámky  
 Implementace bloku zpráv by měly přepsat tuto metodu.  
  
##  <a name="sync_send"></a> sync_send – 

 Při přepisu v odvozené třídě, umístí zprávy synchronně do bloku.  
  
```
virtual void sync_send(_Inout_opt_ message<T>* _Msg) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_Msg`  
 A `message` objekt, který chcete odeslat synchronně.  
  
### <a name="remarks"></a>Poznámky  
 Implementace zpracovatelů by měly přepsat tuto metodu.  
  
##  <a name="wait"></a> Počkej 

 Při přepisu v odvozené třídě, čeká na dokončení všech asynchronních operací.  
  
```
virtual void wait() = 0;
```  
  
### <a name="remarks"></a>Poznámky  
 Implementace zpracovatelů by měly přepsat tuto metodu.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [ordered_message_processor – třída](ordered-message-processor-class.md)
