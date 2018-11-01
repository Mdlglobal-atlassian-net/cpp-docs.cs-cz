---
title: invalid_multiple_scheduling – třída
ms.date: 11/04/2016
f1_keywords:
- invalid_multiple_scheduling
- CONCRT/concurrency::invalid_multiple_scheduling
- CONCRT/concurrency::invalid_multiple_scheduling::invalid_multiple_scheduling
helpviewer_keywords:
- invalid_multiple_scheduling class
ms.assetid: e9a47cb7-a778-4df7-92b0-3752119fd4c7
ms.openlocfilehash: aa22c9b218b88a8834e8ba474c2aa2c203ea89dc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517114"
---
# <a name="invalidmultiplescheduling-class"></a>invalid_multiple_scheduling – třída

Tato třída popisuje výjimku vyvolána, když `task_handle` objekt je naplánované vícekrát pomocí `run` metodu `task_group` nebo `structured_task_group` objekt bez opětovné volání na buď `wait` nebo `run_and_wait` metody.

## <a name="syntax"></a>Syntaxe

```
class invalid_multiple_scheduling : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[invalid_multiple_scheduling](#ctor)|Přetíženo. Vytvoří `invalid_multiple_scheduling` objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`invalid_multiple_scheduling`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

**Namespace:** souběžnosti

##  <a name="ctor"></a> invalid_multiple_scheduling –

Vytvoří `invalid_multiple_scheduling` objektu.

```
explicit _CRTIMP invalid_multiple_scheduling(_In_z_ const char* _Message) throw();

invalid_multiple_scheduling() throw();
```

### <a name="parameters"></a>Parametry

*_TEXT*<br/>
Popisná zpráva chyby.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[task_handle – třída](task-handle-class.md)<br/>
[task_group – třída](task-group-class.md)<br/>
[Spuštění](task-group-class.md)<br/>
[Počkej](task-group-class.md)<br/>
[run_and_wait](task-group-class.md)<br/>
[structured_task_group – třída](structured-task-group-class.md)
