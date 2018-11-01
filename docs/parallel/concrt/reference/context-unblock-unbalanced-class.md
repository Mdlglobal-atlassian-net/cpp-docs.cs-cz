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
ms.openlocfilehash: cc2ef970fa354da4abb7351cb4f1188451887552
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525924"
---
# <a name="contextunblockunbalanced-class"></a>context_unblock_unbalanced – třída

Tato třída popisuje výjimku vyvolanou při volání `Block` a `Unblock` metody `Context` nejsou správně spárované objektu.

## <a name="syntax"></a>Syntaxe

```
class context_unblock_unbalanced : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[context_unblock_unbalanced](#ctor)|Přetíženo. Vytvoří `context_unblock_unbalanced` objektu.|

## <a name="remarks"></a>Poznámky

Volání `Block` a `Unblock` metody `Context` objekt musí být vždy správně párovaný. Modul Concurrency Runtime umožňuje operace v obou pořadí chtěli. Například volání `Block` může být následován volání `Unblock`, nebo naopak. Tato výjimka by být vyvolána, pokud například dvě volání `Unblock` metoda byly provedeny v řádku, na `Context` objekt, který se zablokoval.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`context_unblock_unbalanced`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

**Namespace:** souběžnosti

##  <a name="ctor"></a> context_unblock_unbalanced –

Vytvoří `context_unblock_unbalanced` objektu.

```
explicit _CRTIMP context_unblock_unbalanced(_In_z_ const char* _Message) throw();

context_unblock_unbalanced() throw();
```

### <a name="parameters"></a>Parametry

*_TEXT*<br/>
Popisná zpráva chyby.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
