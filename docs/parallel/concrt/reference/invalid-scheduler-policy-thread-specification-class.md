---
title: invalid_scheduler_policy_thread_specification – třída
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::invalid_scheduler_policy_thread_specification
helpviewer_keywords:
- invalid_scheduler_policy_thread_specification class
ms.assetid: 2d0fafb2-18f8-4284-8040-3db640d33303
ms.openlocfilehash: b6c2fd853ae19c48ae04d6601eb47e5afcb71944
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143040"
---
# <a name="invalid_scheduler_policy_thread_specification-class"></a>invalid_scheduler_policy_thread_specification – třída

Tato třída popisuje výjimku vyvolanou při pokusu o nastavení omezení souběžnosti objektu `SchedulerPolicy` tak, že hodnota `MinConcurrency` klíč je menší než hodnota klíče `MaxConcurrency`.

## <a name="syntax"></a>Syntaxe

```cpp
class invalid_scheduler_policy_thread_specification : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-value-class.md#ctor|Přetíženo. Vytvoří objekt `invalid_scheduler_policy_value`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`invalid_scheduler_policy_thread_specification`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h

**Obor názvů:** souběžnost

## <a name="ctor"></a>invalid_scheduler_policy_thread_specification

Vytvoří objekt `invalid_scheduler_policy_value`.

```cpp
explicit _CRTIMP invalid_scheduler_policy_thread_specification(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_thread_specification() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popisná zpráva o chybě

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[SchedulerPolicy – třída](schedulerpolicy-class.md)
