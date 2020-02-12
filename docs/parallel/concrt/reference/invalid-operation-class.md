---
title: invalid_operation – třída
ms.date: 11/04/2016
f1_keywords:
- invalid_operation
- CONCRT/concurrency::invalid_operation
- CONCRT/concurrency::invalid_operation::invalid_operation
helpviewer_keywords:
- invalid_operation class
ms.assetid: 26ba07dc-fcdf-44cb-b748-a31d35205b52
ms.openlocfilehash: e17d530569d16ba0084a58bf0be00d4a8423b7f6
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140871"
---
# <a name="invalid_operation-class"></a>invalid_operation – třída

Tato třída popisuje výjimku vyvolanou při provedení neplatné operace, která není přesněji popsána jiným typem výjimky vyvolaným Concurrency Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
class invalid_operation : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[invalid_operation](#ctor)|Přetíženo. Vytvoří objekt `invalid_operation`.|

## <a name="remarks"></a>Poznámky

Různé metody, které vyvolávají tuto výjimku, obvykle dokumentují za to, za jakých okolností je vyvolá.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`invalid_operation`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h

**Obor názvů:** souběžnost

## <a name="ctor"></a>invalid_operation

Vytvoří objekt `invalid_operation`.

```cpp
explicit _CRTIMP invalid_operation(_In_z_ const char* _Message) throw();

invalid_operation() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popisná zpráva o chybě

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
