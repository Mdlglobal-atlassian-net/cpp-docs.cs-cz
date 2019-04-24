---
title: Přístup ke členu
ms.date: 11/04/2016
helpviewer_keywords:
- member-selection operators [C++]
- pointers, smart
- member access, overloaded operators
- operator overloading [C++], member access operators
- smart pointers, definition
- smart pointers
ms.assetid: 8c7b2c43-eb92-4d42-9a8e-61aa37d71333
ms.openlocfilehash: 34527f818b135fd5af629ebb69feaffd03b715fc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301627"
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