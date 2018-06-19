---
title: task_options – třída (Concurrency Runtime) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- ppltasks/concurrency::task_options
dev_langs:
- C++
ms.assetid: f93d146b-70f7-46ec-8c2f-c33b8bb0af69
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b01d9d5308590bead126cd623b7da0468f0df60f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688190"
---
# <a name="taskoptions-class-concurrency-runtime"></a>task_options – třída (Concurrency Runtime)
Představuje povolené možnosti pro vytvoření úlohy  
  
## <a name="syntax"></a>Syntaxe  
  
```
class task_options;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[task_options::task_options – konstruktor (Concurrency Runtime)](#ctor)|Přetíženo. Výchozí seznam možnosti vytvoření úlohy|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[task_options::get_cancellation_token – metoda (Concurrency Runtime)](#get_cancellation_token)|Vrátí token zrušení|  
|[task_options::get_continuation_context – metoda (Concurrency Runtime)](#get_continuation_context)|Vrátí kontext pokračování|  
|[task_options::get_scheduler – metoda (Concurrency Runtime)](#get_scheduler)|Vrátí plánovače|  
|[task_options::has_cancellation_token – metoda (Concurrency Runtime)](#has_cancellation_token)|Udává, zda byl token zrušení zadat uživatelem.|  
|[task_options::has_scheduler – metoda (Concurrency Runtime)](#has_scheduler)|Udává, zda byl uživatel zadat n plánovače|  
|[task_options::set_cancellation_token – metoda (Concurrency Runtime)](#set_cancellation_token)|Nastaví daný token v možnostech nástroje|  
|[task_options::set_continuation_context – metoda (Concurrency Runtime)](#set_continuation_context)|Nastaví kontext dané pokračování v možnostech nástroje|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `task_options`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ppltasks.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="get_cancellation_token"></a>  task_options::get_cancellation_token – metoda (Concurrency Runtime)  
 Vrátí token zrušení  
  
```
cancellation_token get_cancellation_token() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
##  <a name="get_continuation_context"></a>  task_options::get_continuation_context – metoda (Concurrency Runtime)  
 Vrátí kontext pokračování  
  
```
task_continuation_context get_continuation_context() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
##  <a name="get_scheduler"></a>  task_options::get_scheduler – metoda (Concurrency Runtime)  
 Vrátí plánovače  
  
```
scheduler_ptr get_scheduler() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
##  <a name="has_cancellation_token"></a>  task_options::has_cancellation_token – metoda (Concurrency Runtime)  
 Udává, zda byl token zrušení zadat uživatelem.  
  
```
bool has_cancellation_token() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
##  <a name="has_scheduler"></a>  task_options::has_scheduler – metoda (Concurrency Runtime)  
 Udává, zda byl uživatel zadat n plánovače  
  
```
bool has_scheduler() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
##  <a name="set_cancellation_token"></a>  task_options::set_cancellation_token – metoda (Concurrency Runtime)  
 Nastaví daný token v možnostech nástroje  
  
```
void set_cancellation_token(cancellation_token _Token);
```  
  
### <a name="parameters"></a>Parametry  
 `_Token`  
  
##  <a name="set_continuation_context"></a>  task_options::set_continuation_context – metoda (Concurrency Runtime)  
 Nastaví kontext dané pokračování v možnostech nástroje  
  
```
void set_continuation_context(task_continuation_context _ContinuationContext);
```  
  
### <a name="parameters"></a>Parametry  
 `_ContinuationContext`  
  
##  <a name="ctor"></a>  task_options::task_options – konstruktor (Concurrency Runtime)  
 Výchozí seznam možnosti vytvoření úlohy  
  
```
task_options();

task_options(
    cancellation_token _Token);

task_options(
    task_continuation_context _ContinuationContext);

task_options(
    cancellation_token _Token,
    task_continuation_context _ContinuationContext);

template<typename _SchedType>
task_options(
    std::shared_ptr<_SchedType> _Scheduler);

task_options(
    scheduler_interface& _Scheduler);

task_options(
    scheduler_ptr _Scheduler);

task_options(
    const task_options& _TaskOptions);
```  
  
### <a name="parameters"></a>Parametry  
 `_SchedType`  
 `_Token`  
 `_ContinuationContext`  
 `_Scheduler`  
 `_TaskOptions`  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
