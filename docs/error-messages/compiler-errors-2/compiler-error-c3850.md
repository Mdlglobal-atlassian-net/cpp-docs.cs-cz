---
title: "C3850 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3850
dev_langs:
- C++
helpviewer_keywords:
- C3850
ms.assetid: 028f3a37-f3ad-4ebc-9168-3cdea47524d4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fe77bb54a72c340a2fbf2a986a4346397cff11fb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3850"></a>C3850 chyby kompilátoru
"char": universal znak name určuje neplatný znak  
  
 Znaky reprezentována jako univerzální názvy znaků musí představovat platný body kódu Unicode v rozsahu 0-10FFFF. Univerzální znak název nemůže obsahovat hodnotu v rozsahu náhradní znakové sady Unicode, D800 DFFF nebo dvojici kódovaného náhradní. Kompilátor generuje náhradní pár z platný kód bodu automaticky.  
  
 V kódu kompilovány jako C nemusí název universal znak reprezentovat znak v rozsahu 0000-009F (včetně) s výjimkami 0024 ('$'), 0040 (' @') a 0060 ('' ').  
  
 V kódu kompilovány jako C++ universal znak název použít jakékoli neplatný bod kódování Unicode v řetězec nebo znak literálu. Mimo literál název universal znak nemusí reprezentovat řídicí znak v rozsahy 0000 001F nebo 007F 009F, včetně, nebo nastavte členem znak základní zdroje.  Další informace najdete v tématu [znakových sad](../../cpp/character-sets2.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3850 a ukazuje, jak to opravit:  
  
```cpp  
// C3850.cpp  
int main() {  
   int \u0019 = 0;   // C3850, not in allowed range for an identifier  
   const wchar_t * wstr_bad  = L"\UD840DC8A"; // C3850, UCN is surrogate pair  
   const wchar_t * wstr_good = L"\U0002008A"; // Okay, UCN is valid code point  
}  
```