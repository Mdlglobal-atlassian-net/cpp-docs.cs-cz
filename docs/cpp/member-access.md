---
title: Přístup ke členu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- member-selection operators [C++]
- pointers, smart
- member access, overloaded operators
- operator overloading [C++], member access operators
- smart pointers, definition
- smart pointers
ms.assetid: 8c7b2c43-eb92-4d42-9a8e-61aa37d71333
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2aadccd883738fe2e6e9f57cc63f67cde6d6a6c4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099936"
---
# <a name="member-access"></a>Přístup ke členu

Přístup ke členům třídy lze řídit přetěžováním operátor přístupu členů (**->**). Tento operátor je v tomto použití považován za unární operátor a funkce přetíženého operátoru musí být členskou funkcí třídy. Deklarace takové funkce je tedy následující:

## <a name="syntax"></a>Syntaxe

```
class-type *operator->()
```

## <a name="remarks"></a>Poznámky

kde *typu třídy* je název třídy, do které tento operátor patří. Funkce operátoru přístupu ke členům musí být nestatickou členskou funkcí.

Tento operátor se používá (často ve spojení s operátorem přesměrování ukazatele) k implementaci „chytrých ukazatelů“, které ověřují ukazatele před použitím přesměrování nebo počtu.

**.** operátor přístupu členů nemohou být přetíženy.

## <a name="see-also"></a>Viz také:

[Přetížení operátoru](../cpp/operator-overloading.md)