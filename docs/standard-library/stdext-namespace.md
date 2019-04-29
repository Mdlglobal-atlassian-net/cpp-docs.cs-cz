---
title: stdext – obor názvů
ms.date: 09/06/2017
f1_keywords:
- stdext
helpviewer_keywords:
- _DEFINE_DEPRECATED_HASH_CLASSES symbol
- stdext namespace
ms.assetid: 3e94fc89-0584-424f-bc09-081b73379545
ms.openlocfilehash: d40f3f7a99db72784cc9a32a9c37064228597d34
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412420"
---
# <a name="stdext-namespace"></a>stdext – obor názvů

Členové [ \<hash_map >](../standard-library/hash-map.md) a [ \<hash_set >](../standard-library/hash-set.md) hlavičkové soubory nejsou aktuálně součástí ISO C++ standardní. Proto tyto typy a členy byly přesunuté z `std` oboru názvů do oboru názvů `stdext`, zůstane splňující podmínky standardu C++.

Při kompilaci s [/Ze](../build/reference/za-ze-disable-language-extensions.md), což je výchozí, kompilátor zobrazí upozornění týkající se použití `std` členů \<hash_map > a \<hash_set > hlavičkové soubory. Chcete-li toto upozornění zakážete, použijte [upozornění](../preprocessor/warning.md) direktivy pragma.

Aby kompilátor generuje chybu pro použití `std` pro členy programu \<hash_map > a \<hash_set – > hlavičkové soubory s **/Ze**, přidejte následující direktivy před `#include` žádné C++ souborech hlaviček standardní knihovny.

```cpp
#define _DEFINE_DEPRECATED_HASH_CLASSES 0
```

Při kompilaci s **/Za**, kompilátor vygeneruje chybu.

## <a name="see-also"></a>Viz také:

[Standardní knihovna C++ – přehled](../standard-library/cpp-standard-library-overview.md)
