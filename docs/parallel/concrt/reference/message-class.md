---
title: "Třída zprávy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- message
- AGENTS/concurrency::message
- AGENTS/concurrency::message::message
- AGENTS/concurrency::message::add_ref
- AGENTS/concurrency::message::msg_id
- AGENTS/concurrency::message::remove_ref
- AGENTS/concurrency::message::payload
dev_langs: C++
helpviewer_keywords: message class
ms.assetid: 3e1f3505-6c0c-486c-8191-666d0880ec62
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5f0c62e8b783b7d97a6158a3f4a55501ed4450b7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="message-class"></a>message – třída
Obálku základní zprávu obsahující datovou předávány mezi bloky zasílání zpráv.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>
class message : public ::Concurrency::details::_Runtime_object;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Datový typ datové části v rámci zprávy.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`type`|Typ aliasu pro `T`.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[zpráva](#ctor)|Přetíženo. Vytvoří `message` objektu.|  
|[~ message – destruktor](#dtor)|Zničí `message` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[add_ref –](#add_ref)|Přidá do počet odkazů pro `message` objektu. Použít pro bloky zpráv, které je třeba určit životnosti zpráva při počítání referencí.|  
|[msg_id –](#msg_id)|Vrátí ID `message` objektu.|  
|[remove_ref –](#remove_ref)|Odečítá od počet odkazů pro `message` objektu. Použít pro bloky zpráv, které je třeba určit životnosti zpráva při počítání referencí.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[datová část](#payload)|Datovou část `message` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `message`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** agents.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="add_ref"></a>add_ref – 

 Přidá do počet odkazů pro `message` objektu. Použít pro bloky zpráv, které je třeba určit životnosti zpráva při počítání referencí.  
  
```
long add_ref();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nová hodnota počet odkazů.  
  
##  <a name="ctor"></a>zpráva 

 Vytvoří `message` objektu.  
  
```
message(
    T const& _P);

message(
    T const& _P,
    runtime_object_identity _Id);

message(
    message const& _Msg);

message(
    _In_ message const* _Msg);
```  
  
### <a name="parameters"></a>Parametry  
 `_P`  
 Datová část této zprávy.  
  
 `_Id`  
 Jedinečný Identifikátor této zprávy.  
  
 `_Msg`  
 Odkaz nebo ukazatel na `message` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Konstruktor, který přebírá ukazatel `message` objektu jako argument, vyvolá [invalid_argument](../../../standard-library/invalid-argument-class.md) výjimka Pokud parametr `_Msg` je `NULL`.  
  
##  <a name="dtor"></a>~ zpráv 

 Zničí `message` objektu.  
  
```
virtual ~message();
```  
  
##  <a name="msg_id"></a>msg_id – 

 Vrátí ID `message` objektu.  
  
```
runtime_object_identity msg_id() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `runtime_object_identity` z `message` objektu.  
  
##  <a name="payload"></a>datová část 

 Datovou část `message` objektu.  
  
```
T const payload;
```  
  
##  <a name="remove_ref"></a>remove_ref – 

 Odečítá od počet odkazů pro `message` objektu. Použít pro bloky zpráv, které je třeba určit životnosti zpráva při počítání referencí.  
  
```
long remove_ref();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nová hodnota počet odkazů.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)
