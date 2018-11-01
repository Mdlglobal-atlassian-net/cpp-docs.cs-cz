---
title: Chyba kompilátoru C3850
ms.date: 09/05/2018
f1_keywords:
- C3850
helpviewer_keywords:
- C3850
ms.assetid: 028f3a37-f3ad-4ebc-9168-3cdea47524d4
ms.openlocfilehash: 9cd0428726f92c7347b162f74b46035f99cc2d3c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50572663"
---
# <a name="compiler-error-c3850"></a>Chyba kompilátoru C3850

> "*char*': universal-character-name určuje neplatný znak

## <a name="remarks"></a>Poznámky

Znaky jsou reprezentovány jako univerzální názvy znaků musí představovat platný kódové body sady Unicode v rozsahu 0-10FFFF. Univerzální název znaku nemůže obsahovat hodnotu v rozsahu náhradní Unicode, D800 DFFF nebo kódovaného náhradní pár. Kompilátor generuje náhradní pár platný kód bodu automaticky.

V kódu zkompilovaném jako C, univerzální název znaku nemůže představovat znaku v rozsahu 0000-009F, včetně výjimek 0024 ('$'), 0040 ("\@") a 0060 ('' ').

V kódu zkompilovaném jako C++ univerzální název znaku může používat libovolný platný bod kódu Unicode v řetězci nebo znakový literál. Mimo literál univerzální název znaku nemůže reprezentovat řídicí znak v oblasti 0000 001F nebo 007F 009F, včetně, nebo členem základní zdrojové znakové sady.  Další informace najdete v tématu [znakových sad](../../cpp/character-sets.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3850 a ukazuje, jak ho opravit:

```cpp
// C3850.cpp
int main() {
   int \u0019 = 0;   // C3850, not in allowed range for an identifier
   const wchar_t * wstr_bad  = L"\UD840DC8A"; // C3850, UCN is surrogate pair
   const wchar_t * wstr_good = L"\U0002008A"; // Okay, UCN is valid code point
}
```