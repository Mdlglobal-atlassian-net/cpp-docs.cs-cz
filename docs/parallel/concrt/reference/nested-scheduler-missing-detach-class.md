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
ms.openlocfilehash: db51f7b083cc0cbd9337fbbe5c672d190208f328
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394387"
---
# <a name="nestedschedulermissingdetach-class"></a>nested_scheduler_missing_detach – třída

Tato třída popisuje výjimku vyvolanou při modulu Runtime souběžnosti zjistí, že opominul volání `CurrentScheduler::Detach` metody u objektu context, který připojuje k druhé pomocí plánovače `Attach` metodu `Scheduler` objektu.

## <a name="syntax"></a>Syntaxe

```
class nested_scheduler_missing_detach : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[nested_scheduler_missing_detach](#ctor)|Přetíženo. Vytvoří `nested_scheduler_missing_detach` objektu.|

## <a name="remarks"></a>Poznámky

Tato výjimka je vyvolána pouze v případě, že byste vnořit jeden Plánovač uvnitř jiného voláním `Attach` metodu `Scheduler` objektu v kontextu, který je již vlastněn nebo připojené k jiné plánovače. Modul Concurrency Runtime vyvolá tuto výjimku tj při scénáři může zjistit jako vodítko k vyhledání problém. Ne každá instance zanedbání volat `CurrentScheduler::Detach` je zaručeno, že metoda vyvolávají tuto výjimku.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`nested_scheduler_missing_detach`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

**Namespace:** souběžnosti

##  <a name="ctor"></a> nested_scheduler_missing_detach

Vytvoří `nested_scheduler_missing_detach` objektu.

```
explicit _CRTIMP nested_scheduler_missing_detach(_In_z_ const char* _Message) throw();

nested_scheduler_missing_detach() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popisná zpráva chyby.

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[Scheduler – třída](scheduler-class.md)
