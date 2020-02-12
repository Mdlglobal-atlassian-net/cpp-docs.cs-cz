---
title: bad_target – třída
ms.date: 11/04/2016
f1_keywords:
- bad_target
- CONCRT/concurrency::bad_target
- CONCRT/concurrency::bad_target::bad_target
helpviewer_keywords:
- bad_target class
ms.assetid: e6dcddbf-9217-4fac-ac7f-7b8b4781d2f5
ms.openlocfilehash: 023607ff142b7fa39165cc9b5280a8e9345a3645
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142847"
---
# <a name="bad_target-class"></a>bad_target – třída

Tato třída popisuje výjimku vyvolanou v případě, že je bloku zasílání zpráv uveden ukazatel na cíl, který není pro prováděnou operaci platný.

## <a name="syntax"></a>Syntaxe

```cpp
class bad_target : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[bad_target](#ctor)|Přetíženo. Vytvoří objekt `bad_target`.|

## <a name="remarks"></a>Poznámky

Tato výjimka se obvykle vydává z důvodů, jako je například pokus o zpracování zprávy, která je vyhrazena pro jiný cíl, nebo uvolnění rezervace, kterou nedrží.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`bad_target`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h

**Obor názvů:** souběžnost

## <a name="ctor"></a>bad_target

Vytvoří objekt `bad_target`.

```cpp
explicit _CRTIMP bad_target(_In_z_ const char* _Message) throw();

bad_target() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popisná zpráva o chybě

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[Asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md)
