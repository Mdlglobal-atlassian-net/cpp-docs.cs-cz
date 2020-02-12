---
title: improper_scheduler_reference – třída
ms.date: 11/04/2016
f1_keywords:
- improper_scheduler_reference
- CONCRT/concurrency::improper_scheduler_reference
- CONCRT/concurrency::improper_scheduler_reference::improper_scheduler_reference
helpviewer_keywords:
- improper_scheduler_reference class
ms.assetid: 434a7512-7796-4255-92a7-f3bf71c6a7a7
ms.openlocfilehash: 18536043b0d46a6f27f1e5c60778a22af82ad2d3
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141115"
---
# <a name="improper_scheduler_reference-class"></a>improper_scheduler_reference – třída

Tato třída popisuje výjimku vyvolanou při volání metody `Reference` u objektu `Scheduler`, který se vypíná od kontextu, který není součástí tohoto plánovače.

## <a name="syntax"></a>Syntaxe

```cpp
class improper_scheduler_reference : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[improper_scheduler_reference](#ctor)|Přetíženo. Vytvoří objekt `improper_scheduler_reference`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`improper_scheduler_reference`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h

**Obor názvů:** souběžnost

## <a name="ctor"></a>improper_scheduler_reference

Vytvoří objekt `improper_scheduler_reference`.

```cpp
explicit _CRTIMP improper_scheduler_reference(_In_z_ const char* _Message) throw();

improper_scheduler_reference() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popisná zpráva o chybě

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[Scheduler – třída](scheduler-class.md)
