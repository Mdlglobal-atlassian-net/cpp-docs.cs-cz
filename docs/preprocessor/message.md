---
title: message – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- message_CPP
- vc-pragma.message
helpviewer_keywords:
- message pragma
- pragmas, message
ms.assetid: 67414f25-ed47-4079-a5dc-21d9d1a39754
ms.openlocfilehash: 48605fbef3b6d81c140e663e950429cd3dcf9b19
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218796"
---
# <a name="message-pragma"></a>message – direktiva pragma

Odešle řetězcový literál na standardní výstup bez ukončení kompilace.

## <a name="syntax"></a>Syntaxe

> **#pragma zpráva (** *zpráva-String* **)**

## <a name="remarks"></a>Poznámky

Typickým použitím direktivy pragma **zprávy** je zobrazení informativních zpráv v době kompilace.

Parametr *řetězce zprávy* může být makro, které se rozbalí do řetězcového literálu, a tato makra můžete zřetězit s řetězcovými literály v libovolné kombinaci.

Použijete-li předdefinované makro v direktivě pragma **zprávy** , musí makro vracet řetězec. V opačném případě bude nutné převést výstup makra na řetězec.

Následující fragment kódu používá direktivu pragma **zprávy** pro zobrazení zpráv během kompilace:

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

## <a name="see-also"></a>Viz také:

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
