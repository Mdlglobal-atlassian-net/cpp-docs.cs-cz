---
title: zpráva | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- message_CPP
- vc-pragma.message
dev_langs:
- C++
helpviewer_keywords:
- message pragma
- pragmas, message
ms.assetid: 67414f25-ed47-4079-a5dc-21d9d1a39754
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a3ce9091fe380f7d255dd321dbb9eb5ca7134b8d
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42465386"
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