---
title: invalid_scheduler_policy_key – třída
ms.date: 11/04/2016
f1_keywords:
- invalid_scheduler_policy_key
- CONCRT/concurrency::invalid_scheduler_policy_key
- CONCRT/concurrency::invalid_scheduler_policy_key::invalid_scheduler_policy_key
helpviewer_keywords:
- invalid_scheduler_policy_key class
ms.assetid: 6a7c42fe-9bc4-4a02-bebb-99fe9ef9817d
ms.openlocfilehash: 1bc2f1cffdeba5f81bd96932ecef23a563fac351
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274060"
---
# <a name="invalidschedulerpolicykey-class"></a>invalid_scheduler_policy_key – třída

Tato třída popisuje výjimku vyvolanou při neplatný nebo je předán neznámý klíč `SchedulerPolicy` konstruktor objektu nebo `SetPolicyValue` metodu `SchedulerPolicy` objekt je předán klíč, který musí být změněno pomocí jiným způsobem, jako `SetConcurrencyLimits` – metoda.

## <a name="syntax"></a>Syntaxe

```
class invalid_scheduler_policy_key : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[invalid_scheduler_policy_key](#ctor)|Přetíženo. Vytvoří `invalid_scheduler_policy_key` objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`invalid_scheduler_policy_key`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

**Namespace:** souběžnosti

##  <a name="ctor"></a> invalid_scheduler_policy_key –

Vytvoří `invalid_scheduler_policy_key` objektu.

```
explicit _CRTIMP invalid_scheduler_policy_key(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_key() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popisná zpráva chyby.

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[SchedulerPolicy – třída](schedulerpolicy-class.md)
