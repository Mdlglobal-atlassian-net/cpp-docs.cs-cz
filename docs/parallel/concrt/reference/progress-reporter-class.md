---
title: "progress_reporter – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- progress_reporter
- PPLTASKS/concurrency::progress_reporter
- PPLTASKS/concurrency::progress_reporter::progress_reporter
- PPLTASKS/concurrency::progress_reporter::report
dev_langs: C++
helpviewer_keywords: progress_reporter class
ms.assetid: b836efab-2d05-4649-b6fa-d15236f1f813
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a72250bcb35b625276d0b8692ce1ec9d13a20ade
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 Tento typ se pouze k dispozici pro aplikace pro Windows Store.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `progress_reporter`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ppltasks.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="ctor"></a>progress_reporter 

```
progress_reporter();
```  
  
##  <a name="report"></a>Sestava 

 Odešle zprávu o průběhu asynchronní akce nebo operace, ke kterému je tento průběh ohlašování vázán.  
  
```
void report(const _ProgressType& val) const;
```  
  
### <a name="parameters"></a>Parametry  
 `val`  
 Datová část sestavy prostřednictvím oznámení o průběhu.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)
