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
ms.openlocfilehash: 60d5a57ff9cb33a3d522c14514f5107844216852
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143015"
---
# <a name="invalid_scheduler_policy_key-class"></a>invalid_scheduler_policy_key – třída

Tato třída popisuje výjimku vyvolanou při předání neplatného nebo neznámého klíče do konstruktoru objektu `SchedulerPolicy`, nebo je-li metoda `SetPolicyValue` objektu `SchedulerPolicy`, předána klíč, který musí být změněn pomocí jiných prostředků, jako je například metoda `SetConcurrencyLimits`.

## <a name="syntax"></a>Syntaxe

```cpp
class invalid_scheduler_policy_key : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[invalid_scheduler_policy_key](#ctor)|Přetíženo. Vytvoří objekt `invalid_scheduler_policy_key`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`invalid_scheduler_policy_key`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h

**Obor názvů:** souběžnost

## <a name="ctor"></a>invalid_scheduler_policy_key

Vytvoří objekt `invalid_scheduler_policy_key`.

```cpp
explicit _CRTIMP invalid_scheduler_policy_key(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_key() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popisná zpráva o chybě

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[SchedulerPolicy – třída](schedulerpolicy-class.md)
