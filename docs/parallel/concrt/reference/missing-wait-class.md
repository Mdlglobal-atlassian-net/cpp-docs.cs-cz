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
ms.openlocfilehash: 68d24d710eec4fd602e64cc3cbde810db2b1a495
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409964"
---
# <a name="missingwait-class"></a>missing_wait – třída

Tato třída popisuje výjimku vyvolanou při stále naplánované úlohy `task_group` nebo `structured_task_group` objektu v době tento objekt destruktor. Tato výjimka bude vyvolána nikdy destruktor při dosažení z důvodu výjimky v důsledku uvolnění zásobníku.

## <a name="syntax"></a>Syntaxe

```
class missing_wait : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[missing_wait –](#ctor)|Přetíženo. Vytvoří `missing_wait` objektu.|

## <a name="remarks"></a>Poznámky

Chybějící výjimka toku, zodpovídáte za volání buď `wait` nebo `run_and_wait` metodu `task_group` nebo `structured_task_group` objekt předtím, než tento objekt k destrukci. Modul runtime vyvolá tuto výjimku jako znamením, že jste zapomněli volání `wait` nebo `run_and_wait` metody.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`missing_wait`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

**Namespace:** souběžnosti

##  <a name="ctor"></a> missing_wait –

Vytvoří `missing_wait` objektu.

```
explicit _CRTIMP missing_wait(_In_z_ const char* _Message) throw();

missing_wait() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popisná zpráva chyby.

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[task_group – třída](task-group-class.md)<br/>
[Počkej](task-group-class.md)<br/>
[run_and_wait](task-group-class.md)<br/>
[structured_task_group – třída](structured-task-group-class.md)
