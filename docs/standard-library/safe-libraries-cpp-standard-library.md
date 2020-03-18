---
title: 'Bezpečné knihovny: standardní knihovna C++'
ms.date: 11/04/2016
helpviewer_keywords:
- Safe Libraries
- Safe Libraries, C++ Standard Library
- Safe C++ Standard Library
ms.assetid: 3993340f-1f29-4d81-b3f5-52a52bc8e148
ms.openlocfilehash: e352489ca12b5815aab5517defc72571abe177fb
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446094"
---
# <a name="safe-libraries-c-standard-library"></a>Bezpečné knihovny: standardní knihovna C++

Pro knihovny dodávané s Microsoftem C++, včetně C++ standardní knihovny, bylo provedeno několik vylepšení, které jim umožní bezpečnější zabezpečení.

Několik metod ve C++ standardní knihovně bylo označeno jako potenciálně nebezpečné, protože by mohlo způsobit přetečení vyrovnávací paměti nebo jiná vada kódu. Použití těchto metod se nedoporučuje a jsou vytvořeny nové a bezpečnější metody, které je nahrazují. Tyto nové metody končí `_s`.

Pro zvýšení zabezpečení iterátorů a algoritmů bylo také provedeno několik vylepšení. Další informace najdete v tématech [kontrolované iterátory](../standard-library/checked-iterators.md), [Podpora iterátoru ladění](../standard-library/debug-iterator-support.md) a [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).

## <a name="remarks"></a>Poznámky

V následující tabulce jsou uvedeny C++ standardní metody knihovny, které jsou potenciálně nebezpečné, a také jejich bezpečnější ekvivalent:

|Potenciálně nebezpečná metoda|Bezpečnější ekvivalent|
|-------------------------------|----------------------|
|[kopií](../standard-library/basic-string-class.md#copy)|[basic_string:: _Copy_s](../standard-library/basic-string-class.md#copy_s)|
|[kopií](../standard-library/char-traits-struct.md#copy)|[char_traits:: _Copy_s](../standard-library/char-traits-struct.md#copy_s)|

Pokud voláte jednu z potenciálně nebezpečných metod nebo pokud používáte iterátory nesprávně, kompilátor vygeneruje [Upozornění kompilátoru (úroveň 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Informace o tom, jak tato upozornění zakázat, najdete v tématu [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).

## <a name="in-this-section"></a>V tomto oddílu

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)

[_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)

[Checked – iterátory](../standard-library/checked-iterators.md)

[Podpora ladění iterátorů](../standard-library/debug-iterator-support.md)

## <a name="see-also"></a>Viz také

[Standardní knihovna C++ – přehled](../standard-library/cpp-standard-library-overview.md)
