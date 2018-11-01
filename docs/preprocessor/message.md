---
title: – zpráva
ms.date: 11/04/2016
f1_keywords:
- message_CPP
- vc-pragma.message
helpviewer_keywords:
- message pragma
- pragmas, message
ms.assetid: 67414f25-ed47-4079-a5dc-21d9d1a39754
ms.openlocfilehash: a55721fb954cf9383022b4fc8e84327ea4c772e7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50627380"
---
# <a name="message"></a>– zpráva
Odešle řetězcový literál na standardní výstup bez ukončení kompilace.

## <a name="syntax"></a>Syntaxe

```
#pragma message( messagestring )
```

## <a name="remarks"></a>Poznámky

Typické použití **zpráva** – Direktiva pragma je zobrazení informačních zpráv během kompilace.

*Messagestring* parametr může být makro, které se rozbalí na řetězcový literál a lze zřetězit s řetězcovými literály v libovolné kombinaci těchto maker.

Pokud použijete předdefinované makro v **zpráva** – Direktiva pragma, makro by měla vrátit řetězec, jinak bude nutné výstup makra převést na řetězec.

Následující fragment kódu používá **zpráva** – Direktiva pragma pro zobrazení zpráv během kompilace:

```cpp
// pragma_directives_message1.cpp
// compile with: /LD
#if _M_IX86 >= 500
#pragma message("_M_IX86 >= 500")
#endif

#pragma message("")

#pragma message( "Compiling " __FILE__ )
#pragma message( "Last modified on " __TIMESTAMP__ )

#pragma message("")

// with line number
#define STRING2(x) #x
#define STRING(x) STRING2(x)

#pragma message (__FILE__ "[" STRING(__LINE__) "]: test")

#pragma message("")
```

## <a name="see-also"></a>Viz také

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)