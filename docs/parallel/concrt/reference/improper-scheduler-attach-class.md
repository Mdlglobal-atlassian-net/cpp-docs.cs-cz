---
title: improper_scheduler_attach – třída
ms.date: 11/04/2016
f1_keywords:
- improper_scheduler_attach
- CONCRT/concurrency::improper_scheduler_attach
- CONCRT/concurrency::improper_scheduler_attach::improper_scheduler_attach
helpviewer_keywords:
- improper_scheduler_attach class
ms.assetid: 5a76da0a-091b-4748-8f62-b3a28f674f9e
ms.openlocfilehash: 2d6a7b53269d305c976bcc596fe85dc018442332
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62262473"
---
# <a name="improperschedulerattach-class"></a>improper_scheduler_attach – třída

Tato třída popisuje výjimku vyvolána, když `Attach` metoda je volána na `Scheduler` objekt, který je již připojen k aktuálním kontextu.

## <a name="syntax"></a>Syntaxe

```
class improper_scheduler_attach : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[improper_scheduler_attach](#ctor)|Přetíženo. Vytvoří `improper_scheduler_attach` objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`improper_scheduler_attach`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

**Namespace:** souběžnosti

##  <a name="ctor"></a> improper_scheduler_attach

Vytvoří `improper_scheduler_attach` objektu.

```
explicit _CRTIMP improper_scheduler_attach(_In_z_ const char* _Message) throw();

improper_scheduler_attach() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popisná zpráva chyby.

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[Scheduler – třída](scheduler-class.md)
