---
title: improper_lock – třída
ms.date: 11/04/2016
f1_keywords:
- improper_lock
- CONCRT/concurrency::improper_lock
- CONCRT/concurrency::improper_lock::improper_lock
helpviewer_keywords:
- improper_lock class
ms.assetid: 8f494942-7748-4a2a-8de2-23414bfe6346
ms.openlocfilehash: 886444f3e856234be010715a8ee0c707cf919bb4
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142402"
---
# <a name="improper_lock-class"></a>improper_lock – třída

Tato třída popisuje výjimku vyvolanou při nesprávném získání zámku.

## <a name="syntax"></a>Syntaxe

```cpp
class improper_lock : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[improper_lock](#ctor)|Přetíženo. Vytvoří `improper_lock exception`.|

## <a name="remarks"></a>Poznámky

Tato výjimka je obvykle vyvolána, když se provede pokus o získání rekurzivního uzamčení bez opětovného využití ve stejném kontextu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`improper_lock`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h

**Obor názvů:** souběžnost

## <a name="ctor"></a>improper_lock

Vytvoří `improper_lock exception`.

```cpp
explicit _CRTIMP improper_lock(_In_z_ const char* _Message) throw();

improper_lock() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popisná zpráva o chybě

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[critical_section – třída](critical-section-class.md)<br/>
[reader_writer_lock – třída](reader-writer-lock-class.md)
