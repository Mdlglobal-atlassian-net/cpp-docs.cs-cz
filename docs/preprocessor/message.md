---
title: "zpráva | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fb998ef084f259601478ea9614a2bd8dc3da0d68
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
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