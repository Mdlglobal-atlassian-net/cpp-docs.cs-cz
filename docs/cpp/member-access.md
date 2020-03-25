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
ms.openlocfilehash: 12ea612625e21a8a13021b75e92f3752b0b5ce80
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179416"
---
# <a name="member-access"></a>Přístup ke členu

Přístup ke členu třídy lze ovládat přetížením operátoru přístupu členů ( **->** ). Tento operátor je v tomto použití považován za unární operátor a funkce přetíženého operátoru musí být členskou funkcí třídy. Deklarace takové funkce je tedy následující:

## <a name="syntax"></a>Syntaxe

```
class-type *operator->()
```

## <a name="remarks"></a>Poznámky

kde *Class-Type* je název třídy, do které tento operátor patří. Funkce operátoru přístupu ke členům musí být nestatickou členskou funkcí.

Tento operátor se používá (často ve spojení s operátorem přesměrování ukazatele) k implementaci „chytrých ukazatelů“, které ověřují ukazatele před použitím přesměrování nebo počtu.

Rozhraní **.** operátor přístupu ke členu nemůže být přetížený.

## <a name="see-also"></a>Viz také

[Přetížení operátoru](../cpp/operator-overloading.md)
