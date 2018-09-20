---
title: invalid_operation – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- invalid_operation
- CONCRT/concurrency::invalid_operation
- CONCRT/concurrency::invalid_operation::invalid_operation
dev_langs:
- C++
helpviewer_keywords:
- invalid_operation class
ms.assetid: 26ba07dc-fcdf-44cb-b748-a31d35205b52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9e903a3d5e269a273a191fd733ff8813b75b53a5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416903"
---
# <a name="invalidoperation-class"></a>invalid_operation – třída

Tato třída popisuje výjimku vyvolanou při provádění neplatné operace, která není přesněji popsána jako jiný typ výjimky vyvolané modulem Runtime souběžnost.

## <a name="syntax"></a>Syntaxe

```
class invalid_operation : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[invalid_operation –](#ctor)|Přetíženo. Vytvoří `invalid_operation` objektu.|

## <a name="remarks"></a>Poznámky

Různé metody, které vyvolávají tuto výjimku, většinou dokumentují za jakých okolností se vyvolá ji.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`invalid_operation`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

**Namespace:** souběžnosti

##  <a name="ctor"></a> invalid_operation –

Vytvoří `invalid_operation` objektu.

```
explicit _CRTIMP invalid_operation(_In_z_ const char* _Message) throw();

invalid_operation() throw();
```

### <a name="parameters"></a>Parametry

*_TEXT*<br/>
Popisná zpráva chyby.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
