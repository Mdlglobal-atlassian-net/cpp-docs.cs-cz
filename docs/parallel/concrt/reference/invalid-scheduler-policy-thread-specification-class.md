---
title: invalid_scheduler_policy_thread_specification – třída
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::invalid_scheduler_policy_thread_specification
helpviewer_keywords:
- invalid_scheduler_policy_thread_specification class
ms.assetid: 2d0fafb2-18f8-4284-8040-3db640d33303
ms.openlocfilehash: b74439d1fca9ea990258ca5f7e36c865a2c49455
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491335"
---
# <a name="invalidschedulerpolicythreadspecification-class"></a>invalid_scheduler_policy_thread_specification – třída

Tato třída popisuje výjimku vyvolanou při pokusu o nastavení omezení souběžnosti `SchedulerPolicy` objektu tak, aby hodnota `MinConcurrency` klíč je menší než hodnota `MaxConcurrency` klíč.

## <a name="syntax"></a>Syntaxe

```
class invalid_scheduler_policy_thread_specification : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-value-class.md#ctor|Přetíženo. Vytvoří `invalid_scheduler_policy_value` objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`invalid_scheduler_policy_thread_specification`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

**Namespace:** souběžnosti
##  <a name="ctor"></a> invalid_scheduler_policy_thread_specification –

Vytvoří `invalid_scheduler_policy_value` objektu.

```
explicit _CRTIMP invalid_scheduler_policy_thread_specification(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_thread_specification() throw();
```

### <a name="parameters"></a>Parametry

*_TEXT*<br/>
Popisná zpráva chyby.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[SchedulerPolicy – třída](schedulerpolicy-class.md)
