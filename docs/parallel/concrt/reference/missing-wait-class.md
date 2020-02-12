---
title: missing_wait – třída
ms.date: 11/04/2016
f1_keywords:
- missing_wait
- CONCRT/concurrency::missing_wait
- CONCRT/concurrency::missing_wait::missing_wait
helpviewer_keywords:
- missing_wait class
ms.assetid: ff981875-bd43-47e3-806f-b03c9f418b18
ms.openlocfilehash: cf81d1ee6c144da210da5b1f37aca7910ae37bc8
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142380"
---
# <a name="missing_wait-class"></a>missing_wait – třída

Tato třída popisuje výjimku vyvolanou v případě, že jsou úlohy stále naplánovány na `task_group` nebo `structured_task_group` objekt v době, kdy se spustí destruktor objektu. Tato výjimka nebude nikdy vyvolána, pokud je dosaženo destruktoru z důvodu zrušení zásobníku v důsledku výjimky.

## <a name="syntax"></a>Syntaxe

```cpp
class missing_wait : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[missing_wait](#ctor)|Přetíženo. Vytvoří objekt `missing_wait`.|

## <a name="remarks"></a>Poznámky

Nepřítomen tok výjimky, zodpovídáte za volání metody `wait` nebo `run_and_wait` objektu `task_group` nebo `structured_task_group` před tím, než povolíte tomuto objektu destrukci. Modul runtime tuto výjimku vyvolá jako indikaci, že jste zapomněli volat metodu `wait` nebo `run_and_wait`.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`missing_wait`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h

**Obor názvů:** souběžnost

## <a name="ctor"></a>missing_wait

Vytvoří objekt `missing_wait`.

```cpp
explicit _CRTIMP missing_wait(_In_z_ const char* _Message) throw();

missing_wait() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popisná zpráva o chybě

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[task_group – třída](task-group-class.md)<br/>
[Počkej](task-group-class.md)<br/>
[run_and_wait](task-group-class.md)<br/>
[structured_task_group – třída](structured-task-group-class.md)
