---
title: improper_scheduler_detach – třída
ms.date: 11/04/2016
f1_keywords:
- improper_scheduler_detach
- CONCRT/concurrency::improper_scheduler_detach
- CONCRT/concurrency::improper_scheduler_detach::improper_scheduler_detach
helpviewer_keywords:
- improper_scheduler_detach class
ms.assetid: 30132102-c900-4951-a470-b63b4e3aa2d2
ms.openlocfilehash: b2fc90656051be62528d0aac600fad67485c81f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643284"
---
# <a name="improperschedulerdetach-class"></a>improper_scheduler_detach – třída

Tato třída popisuje výjimku vyvolána, když `CurrentScheduler::Detach` metoda je volána u objektu context, která nebyla připojena k žádné scheduleru pomocí `Attach` metodu `Scheduler` objektu.

## <a name="syntax"></a>Syntaxe

```
class improper_scheduler_detach : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[improper_scheduler_detach](#ctor)|Přetíženo. Vytvoří `improper_scheduler_detach` objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`improper_scheduler_detach`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

**Namespace:** souběžnosti

##  <a name="ctor"></a> improper_scheduler_detach –

Vytvoří `improper_scheduler_detach` objektu.

```
explicit _CRTIMP improper_scheduler_detach(_In_z_ const char* _Message) throw();

improper_scheduler_detach() throw();
```

### <a name="parameters"></a>Parametry

*_TEXT*<br/>
Popisná zpráva chyby.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[Scheduler – třída](scheduler-class.md)
