---
title: invalid_scheduler_policy_value – třída
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::invalid_scheduler_policy_value
helpviewer_keywords:
- invalid_scheduler_policy_value class
ms.assetid: 8c533e3f-2774-4192-8616-b2313b859bf7
ms.openlocfilehash: 6a66b2b303a4b3b0cb8c2c7a3c515ac8cd1b33a0
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142996"
---
# <a name="invalid_scheduler_policy_value-class"></a>invalid_scheduler_policy_value – třída

Tato třída popisuje výjimku vyvolanou při nastavení klíče zásad objektu `SchedulerPolicy` na neplatnou hodnotu pro tento klíč.

## <a name="syntax"></a>Syntaxe

```cpp
class invalid_scheduler_policy_value : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[invalid_scheduler_policy_value] (neplatné – Scheduler-Policy-Thread-Specification-Class. MD # ctor|Přetíženo. Vytvoří objekt `invalid_scheduler_policy_value`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`invalid_scheduler_policy_value`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h

**Obor názvů:** souběžnost

## <a name="ctor"></a>invalid_scheduler_policy_value

Vytvoří objekt `invalid_scheduler_policy_value`.

```cpp
explicit _CRTIMP invalid_scheduler_policy_value(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_value() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popisná zpráva o chybě

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[SchedulerPolicy – třída](schedulerpolicy-class.md)
