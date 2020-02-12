---
title: context_unblock_unbalanced – třída
ms.date: 11/04/2016
f1_keywords:
- context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced::context_unblock_unbalanced
helpviewer_keywords:
- context_unblock_unbalanced class
ms.assetid: a76066c8-19dd-44fa-959a-6941ec1b0d2d
ms.openlocfilehash: 261ec96c1a83fbec423e6dbbfe403c4db53a2962
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143098"
---
# <a name="context_unblock_unbalanced-class"></a>context_unblock_unbalanced – třída

Tato třída popisuje výjimku vyvolanou při volání `Block` a `Unblock` metody objektu `Context` nejsou správně spárovány.

## <a name="syntax"></a>Syntaxe

```cpp
class context_unblock_unbalanced : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[context_unblock_unbalanced](#ctor)|Přetíženo. Vytvoří objekt `context_unblock_unbalanced`.|

## <a name="remarks"></a>Poznámky

Volání metody `Block` a `Unblock` objektu `Context` musí být vždy správně spárována. Concurrency Runtime umožňuje, aby se operace prováděly v libovolném pořadí. Například volání `Block` může následovat po volání `Unblock`nebo naopak. Tato výjimka by se vyvolala v případě, že například dvě volání metody `Unblock` byla provedena v řádku na objektu `Context`, který nebyl zablokován.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`context_unblock_unbalanced`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h

**Obor názvů:** souběžnost

## <a name="ctor"></a>context_unblock_unbalanced

Vytvoří objekt `context_unblock_unbalanced`.

```cpp
explicit _CRTIMP context_unblock_unbalanced(_In_z_ const char* _Message) throw();

context_unblock_unbalanced() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popisná zpráva o chybě

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
