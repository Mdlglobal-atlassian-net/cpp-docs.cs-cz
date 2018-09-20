---
title: context_unblock_unbalanced – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced::context_unblock_unbalanced
dev_langs:
- C++
helpviewer_keywords:
- context_unblock_unbalanced class
ms.assetid: a76066c8-19dd-44fa-959a-6941ec1b0d2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8cd35b53db37d51a9feec567fe66c53b1381b4d9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431330"
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
