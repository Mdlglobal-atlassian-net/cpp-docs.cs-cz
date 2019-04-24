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
ms.openlocfilehash: 121e61447775cdcb5d7f5f1187c5d4cc6b7d68b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62262902"
---
# <a name="improperschedulerreference-class"></a>improper_scheduler_reference – třída

Tato třída popisuje výjimku vyvolána, když `Reference` metoda je volána na `Scheduler` objekt, který se vypíná, z kontextu, který není součástí tohoto plánovače.

## <a name="syntax"></a>Syntaxe

```
class improper_scheduler_reference : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[improper_scheduler_reference](#ctor)|Přetíženo. Vytvoří `improper_scheduler_reference` objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`improper_scheduler_reference`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

**Namespace:** souběžnosti

##  <a name="ctor"></a> improper_scheduler_reference

Vytvoří `improper_scheduler_reference` objektu.

```
explicit _CRTIMP improper_scheduler_reference(_In_z_ const char* _Message) throw();

improper_scheduler_reference() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popisná zpráva chyby.

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[Scheduler – třída](scheduler-class.md)
