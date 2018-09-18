---
title: progress_reporter – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 6d4a1b76966216a6dc7b2e7249bddb1ac629376f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016764"
---
# <a name="progressreporter-class"></a>progress_reporter – třída
Třída zpravodaj pokroku umožňuje vykazování průběhu oznámení určitého typu. Každý objekt progress_reporter je vázán na konkrétní asynchronní akci nebo operaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename _ProgressType>
class progress_reporter;
```  
  
#### <a name="parameters"></a>Parametry  
*_ProgressType*<br/>
Typ datové části každého oznámení o pokroku vykázaného prostřednictvím.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[progress_reporter](#ctor)||  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Sestavy](#report)|Odešle zprávu o pokroku asynchronní akce nebo operace, ke kterému je vázán tento zpravodaj pokroku.|  
  
## <a name="remarks"></a>Poznámky  
 Tento typ je pouze k dispozici pro aplikace Windows Runtime.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `progress_reporter`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ppltasks.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="ctor"></a> progress_reporter – 

```
progress_reporter();
```  
  
##  <a name="report"></a> Sestavy 

 Odešle zprávu o pokroku asynchronní akce nebo operace, ke kterému je vázán tento zpravodaj pokroku.  
  
```
void report(const _ProgressType& val) const;
```  
  
### <a name="parameters"></a>Parametry  
*Val*<br/>
Datové zprávy prostřednictvím oznámení postupu.  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
