---
title: 'Bezpečné knihovny: standardní knihovna C++'
ms.date: 11/04/2016
f1_keywords:
- _SCL_SECURE_NO_DEPRECATE
helpviewer_keywords:
- Safe Libraries
- Safe Libraries, C++ Standard Library
- Safe C++ Standard Library
ms.assetid: 3993340f-1f29-4d81-b3f5-52a52bc8e148
ms.openlocfilehash: 340d300efb442fedb18b738c275bc0a79f874991
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630721"
---
# <a name="safe-libraries-c-standard-library"></a>Bezpečné knihovny: standardní knihovna C++

Několik vylepšení byly provedeny na knihovny, které se dodávají s jazykem Visual C++, včetně standardní knihovny C++, aby se daly bezpečnější.

Několik metod ve standardní knihovně C++ byly identifikovány jako potenciálně nebezpečná vzhledem k tomu by mohlo vést k přetečení vyrovnávací paměti nebo jiných vad kódu. Používání těchto metod se nedoporučuje a pokud je Pokud chcete nahradit byly vytvořeny novým a lépe zabezpečeným metody. Tyto nové metody všechny končit `_s`.

Několik vylepšení byly provedeny také kvůli většímu zabezpečení iterátorů a algoritmů. Další informace najdete v tématu [Checked Iterators](../standard-library/checked-iterators.md), [Debug Iterator Support](../standard-library/debug-iterator-support.md) a [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).

## <a name="remarks"></a>Poznámky

Následující tabulka uvádí metody standardní knihovny C++, které mohou být nebezpečné, jakož i jejich bezpečnější ekvivalentní:

|Potenciálně nebezpečné – metoda|Bezpečnější ekvivalent|
|-------------------------------|----------------------|
|[kopírování](../standard-library/basic-string-class.md#copy)|[basic_string::_Copy_s](../standard-library/basic-string-class.md#copy_s)|
|[kopírování](../standard-library/char-traits-struct.md#copy)|[char_traits::_Copy_s](../standard-library/char-traits-struct.md#copy_s)|

Pokud volání jedné z potenciálně nebezpečných metod uvedených výše, nebo pokud nesprávně používáte iterátory, bude kompilátor generovat [upozornění kompilátoru (úroveň 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Informace o tom, jak zakázat tato upozornění najdete v tématu [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).

## <a name="in-this-section"></a>V tomto oddílu

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)

[_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)

[Checked – iterátory](../standard-library/checked-iterators.md)

[Podpora ladění iterátorů](../standard-library/debug-iterator-support.md)

## <a name="see-also"></a>Viz také:

[Standardní knihovna C++ – přehled](../standard-library/cpp-standard-library-overview.md)<br/>
