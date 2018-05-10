---
title: progress_reporter – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- progress_reporter
- PPLTASKS/concurrency::progress_reporter
- PPLTASKS/concurrency::progress_reporter::progress_reporter
- PPLTASKS/concurrency::progress_reporter::report
dev_langs:
- C++
helpviewer_keywords:
- progress_reporter class
ms.assetid: b836efab-2d05-4649-b6fa-d15236f1f813
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d5d4dc98c4fb411a4d63fdfad5049cf0df723bec
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="progressreporter-class"></a>progress_reporter – třída
Třída průběh zpravodaje, která umožňuje reporting oznámení průběhu určitého typu. Každý objekt progress_reporter je vázána na operaci nebo konkrétní asynchronní akce.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename _ProgressType>
class progress_reporter;
```  
  
#### <a name="parameters"></a>Parametry  
 `_ProgressType`  
 Typ datové části jednotlivých oznámení o průběhu nahlášené prostřednictvím ohlašování průběh.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[progress_reporter](#ctor)||  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Sestava](#report)|Odešle zprávu o průběhu asynchronní akce nebo operace, ke kterému je tento průběh ohlašování vázán.|  
  
## <a name="remarks"></a>Poznámky  
 Tento typ se pouze k dispozici pro aplikace Windows Runtime.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `progress_reporter`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ppltasks.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="ctor"></a> progress_reporter 

```
progress_reporter();
```  
  
##  <a name="report"></a> Sestava 

 Odešle zprávu o průběhu asynchronní akce nebo operace, ke kterému je tento průběh ohlašování vázán.  
  
```
void report(const _ProgressType& val) const;
```  
  
### <a name="parameters"></a>Parametry  
 `val`  
 Datová část sestavy prostřednictvím oznámení o průběhu.  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
