---
title: Chyba kompilátoru C3850
ms.date: 09/05/2018
f1_keywords:
- C3850
helpviewer_keywords:
- C3850
ms.assetid: 028f3a37-f3ad-4ebc-9168-3cdea47524d4
ms.openlocfilehash: 5de7994e8bf46105e94271ab29bf9e27f1da3e76
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165559"
---
# <a name="compiler-error-c3850"></a>Chyba kompilátoru C3850

> *char*: Universal-Character-name určuje neplatný znak.

## <a name="remarks"></a>Poznámky

Znaky reprezentované jako univerzální názvy znaků musí představovat platné body kódu Unicode v rozsahu 0 – 10FFFF. Univerzální název znaku nemůže obsahovat hodnotu v rozsahu nahrazení Unicode, D800-DFFF nebo kódované náhradní páry. Kompilátor vygeneruje náhradní pár z platného bodu kódu automaticky.

V kódu kompilovaném jako C nesmí univerzální název znaku představovat znak v rozsahu 0000-009F (včetně) s výjimkami 0024 ($), 0040 ('\@') a 0060 (' ').

V kódu kompilovaném C++jako, univerzální název znaku může v řetězci nebo znakového literálu použít libovolný platný bod kódu Unicode. Mimo literál nesmí univerzální název znaku představovat řídicí znak v rozsahu 0000-001F nebo 007F-009F, včetně, nebo členu základní zdrojové znakové sady.  Další informace naleznete v tématu [znakové sady](../../cpp/character-sets.md).

## <a name="example"></a>Příklad

Následující ukázka vygeneruje C3850 a ukazuje, jak ji opravit:

```cpp
// C3850.cpp
int main() {
   int \u0019 = 0;   // C3850, not in allowed range for an identifier
   const wchar_t * wstr_bad  = L"\UD840DC8A"; // C3850, UCN is surrogate pair
   const wchar_t * wstr_good = L"\U0002008A"; // Okay, UCN is valid code point
}
```
