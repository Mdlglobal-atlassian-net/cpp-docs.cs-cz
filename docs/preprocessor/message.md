---
title: zpráva | Microsoft Docs
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
ms.openlocfilehash: 47b9fd580d1ebabf4352104fe49f1d3c982a49e7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33846360"
---
# <a name="message"></a>– zpráva
Odešle řetězcový literál na standardní výstup bez ukončení kompilace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#pragma message( messagestring )  
```  
  
## <a name="remarks"></a>Poznámky  
 Typické použití **zpráva** – Direktiva pragma je zobrazit informační zprávy v době kompilace.  
  
 *Messagestring* parametr může být makro, které zasahuje do řetězcový literál a můžete zřetězení těchto makra s textové literály v libovolné kombinace.  
  
 Pokud použijete předdefinovanou makro v **zpráva** – Direktiva pragma, makro by měla vrátit řetězec, jinak bude mít výstup makro převést na řetězec.  
  
 Používá následující fragment kódu **zpráva** – Direktiva pragma pro zobrazení zpráv během kompilace:  
  
```  
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