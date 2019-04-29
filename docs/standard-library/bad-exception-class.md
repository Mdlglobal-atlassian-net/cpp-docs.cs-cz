---
title: Třída bad_exception
ms.date: 11/04/2016
f1_keywords:
- exception/std::bad_exception
helpviewer_keywords:
- bad_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
ms.openlocfilehash: 94d1104b66fc6bd84e209caa23ce309cffd9fa85
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377815"
---
# <a name="badexception-class"></a>Třída bad_exception

Tato třída popisuje výjimku, která mohou být vyvolány z neočekávané obslužné rutiny.

## <a name="syntax"></a>Syntaxe

```cpp
class bad_exception    : public exception {};
```

## <a name="remarks"></a>Poznámky

[neočekávané](../standard-library/exception-functions.md#unexpected) vyvolá výjimku `bad_exception` místo ukončení nebo místo volání další funkce zadaným [set_unexpected](../standard-library/exception-functions.md#set_unexpected) Pokud `bad_exception` je součástí seznamu vyvolání výjimky funkce.

Hodnota vrácená `what` je řetězec C definované implementací. Žádná z členské funkce generovat žádné výjimky.

Pro seznam členů děděné `bad_exception` najdete v tématu [tříd výjimek](../standard-library/exception-class.md).

## <a name="example"></a>Příklad

Zobrazit [set_unexpected](../standard-library/exception-functions.md#set_unexpected) příklad použití [neočekávané](../standard-library/exception-functions.md#unexpected) vyvolání `bad_exception`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<výjimky >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[exception – třída](../standard-library/exception-class.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
