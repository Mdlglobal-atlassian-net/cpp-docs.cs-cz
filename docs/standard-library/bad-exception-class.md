---
title: Třída bad_exception
ms.date: 11/04/2016
f1_keywords:
- exception/std::bad_exception
helpviewer_keywords:
- bad_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
ms.openlocfilehash: 1795a44d2d31cfbad964b41ef03e4bf65b401352
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246197"
---
# <a name="badexception-class"></a>Třída bad_exception

Tato třída popisuje výjimku, která mohou být vyvolány z neočekávané obslužné rutiny.

## <a name="syntax"></a>Syntaxe

```cpp
class bad_exception : public exception {};

bad_exception();
bad_exception(const bad_exception&);
bad_exception& operator=(const bad_exception&);
const char* what() const override;
```

## <a name="remarks"></a>Poznámky

[neočekávané](../standard-library/exception-functions.md#unexpected) vyvolá výjimku `bad_exception` místo ukončení nebo místo volání další funkce zadaným [set_unexpected](../standard-library/exception-functions.md#set_unexpected) Pokud `bad_exception` je součástí seznamu vyvolání výjimky funkce.

Hodnota vrácená `what` je řetězec C definované implementací. Žádná z členské funkce generovat žádné výjimky.

Pro seznam členů děděné `bad_exception` najdete v tématu [tříd výjimek](../standard-library/exception-class.md).

## <a name="example"></a>Příklad

Zobrazit [set_unexpected](../standard-library/exception-functions.md#set_unexpected) příklad použití [neočekávané](../standard-library/exception-functions.md#unexpected) vyvolání `bad_exception`.
