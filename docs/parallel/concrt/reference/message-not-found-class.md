---
title: message_not_found – třída
ms.date: 11/04/2016
f1_keywords:
- message_not_found
- CONCRT/concurrency::message_not_found
- CONCRT/concurrency::message_not_found::message_not_found
helpviewer_keywords:
- message_not_found class
ms.assetid: a96b9995-5ad7-4600-83c8-c15e329ff10e
ms.openlocfilehash: da0a44b90346959756c1ef7c685bef234fe6e46a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394413"
---
# <a name="messagenotfound-class"></a>message_not_found – třída

Tato třída popisuje výjimku vyvolanou při blok zpráv se nepodařilo najít požadovaný zprávu.

## <a name="syntax"></a>Syntaxe

```
class message_not_found : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[message_not_found](#ctor)|Přetíženo. Vytvoří `message_not_found` objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`message_not_found`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

**Namespace:** souběžnosti

##  <a name="ctor"></a> message_not_found –

Vytvoří `message_not_found` objektu.

```
explicit _CRTIMP message_not_found(_In_z_ const char* _Message) throw();

message_not_found() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popisná zpráva chyby.

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[Asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md)
