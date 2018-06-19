---
title: Třída bad_exception | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- exception/std::bad_exception
dev_langs:
- C++
helpviewer_keywords:
- bad_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 41b30763f1382b7a12f68cd6a45b87960f623649
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33842674"
---
# <a name="badexception-class"></a>Třída bad_exception

Třída popisuje výjimku, která může být vyvolána z neočekávané obslužné rutiny.

## <a name="syntax"></a>Syntaxe

```cpp
class bad_exception    : public exception {};
```

## <a name="remarks"></a>Poznámky

[neočekávané](../standard-library/exception-functions.md#unexpected) vyvolá výjimku `bad_exception` místo ukončení nebo namísto volání jinou funkci zadaným [set_unexpected –](../standard-library/exception-functions.md#set_unexpected) Pokud `bad_exception` je uveden v seznamu throw funkce.

Hodnoty vrácené **co** je řetězec definované implementací C. Žádná z členské funkce throw jakékoli výjimky.

Pro seznam členů zdědí `bad_exception` třídy najdete v tématu [třída exception](../standard-library/exception-class.md).

## <a name="example"></a>Příklad

V tématu [set_unexpected –](../standard-library/exception-functions.md#set_unexpected) příklad použití [neočekávané](../standard-library/exception-functions.md#unexpected) vyvolání `bad_exception`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<výjimka >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[exception – třída](../standard-library/exception-class.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
