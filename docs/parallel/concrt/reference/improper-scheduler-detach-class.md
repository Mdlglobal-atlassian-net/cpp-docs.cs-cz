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
ms.openlocfilehash: 2f5ad16893a898d4258762b25fea3d557607a3f8
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141154"
---
# <a name="improper_scheduler_detach-class"></a>improper_scheduler_detach – třída

Tato třída popisuje výjimku vyvolanou při volání metody `CurrentScheduler::Detach` v kontextu, který nebyl připojen k žádnému plánovači pomocí metody `Attach` objektu `Scheduler`.

## <a name="syntax"></a>Syntaxe

```cpp
class improper_scheduler_detach : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[improper_scheduler_detach](#ctor)|Přetíženo. Vytvoří objekt `improper_scheduler_detach`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`improper_scheduler_detach`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h

**Obor názvů:** souběžnost

## <a name="ctor"></a>improper_scheduler_detach

Vytvoří objekt `improper_scheduler_detach`.

```cpp
explicit _CRTIMP improper_scheduler_detach(_In_z_ const char* _Message) throw();

improper_scheduler_detach() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popisná zpráva o chybě

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[Scheduler – třída](scheduler-class.md)
