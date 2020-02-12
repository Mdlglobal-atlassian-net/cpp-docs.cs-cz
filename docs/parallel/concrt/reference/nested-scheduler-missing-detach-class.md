---
title: nested_scheduler_missing_detach – třída
ms.date: 11/04/2016
f1_keywords:
- nested_scheduler_missing_detach
- CONCRT/concurrency::nested_scheduler_missing_detach
- CONCRT/concurrency::nested_scheduler_missing_detach::nested_scheduler_missing_detach
helpviewer_keywords:
- nested_scheduler_missing_detach class
ms.assetid: 65d3f277-6d43-4160-97ef-caf8b26c1641
ms.openlocfilehash: 8c9553b036890c4ce28f1060bfe2f58ee1904935
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138855"
---
# <a name="nested_scheduler_missing_detach-class"></a>nested_scheduler_missing_detach – třída

Tato třída popisuje výjimku vyvolanou při Concurrency Runtime zjistí, že jste opomíjeni zavolat metodu `CurrentScheduler::Detach` v kontextu, který je připojen k druhému plánovači pomocí metody `Attach` objektu `Scheduler`.

## <a name="syntax"></a>Syntaxe

```cpp
class nested_scheduler_missing_detach : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[nested_scheduler_missing_detach](#ctor)|Přetíženo. Vytvoří objekt `nested_scheduler_missing_detach`.|

## <a name="remarks"></a>Poznámky

Tato výjimka je vyvolána pouze při vnoření jednoho plánovače do jiného voláním metody `Attach` objektu `Scheduler` v kontextu, který je již vlastněn nebo připojen k jinému plánovači. Concurrency Runtime vyvolá tuto výjimku oportunisticky, když dokáže detekovat scénář jako pomůcku k nalezení problému. Ne každá instance opomíjení volání metody `CurrentScheduler::Detach` je zaručena vyvolat tuto výjimku.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`nested_scheduler_missing_detach`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h

**Obor názvů:** souběžnost

## <a name="ctor"></a>nested_scheduler_missing_detach

Vytvoří objekt `nested_scheduler_missing_detach`.

```cpp
explicit _CRTIMP nested_scheduler_missing_detach(_In_z_ const char* _Message) throw();

nested_scheduler_missing_detach() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popisná zpráva o chybě

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[Scheduler – třída](scheduler-class.md)
