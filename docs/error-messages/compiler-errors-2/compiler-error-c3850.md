---
title: C3850 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3850
dev_langs:
- C++
helpviewer_keywords:
- C3850
ms.assetid: 028f3a37-f3ad-4ebc-9168-3cdea47524d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bb2068a283fc54a86b09f2af05b177f2151e940b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3850"></a>C3850 chyby kompilátoru
"char": universal znak name určuje neplatný znak  
  
 Znaky reprezentována jako univerzální názvy znaků musí představovat platný body kódu Unicode v rozsahu 0-10FFFF. Univerzální znak název nemůže obsahovat hodnotu v rozsahu náhradní znakové sady Unicode, D800 DFFF nebo dvojici kódovaného náhradní. Kompilátor generuje náhradní pár z platný kód bodu automaticky.  
  
 V kódu kompilovány jako C nemusí název universal znak reprezentovat znak v rozsahu 0000-009F (včetně) s výjimkami 0024 ('$'), 0040 (' @') a 0060 ('' ').  
  
 V kódu kompilovány jako C++ universal znak název použít jakékoli neplatný bod kódování Unicode v řetězec nebo znak literálu. Mimo literál název universal znak nemusí reprezentovat řídicí znak v rozsahy 0000 001F nebo 007F 009F, včetně, nebo nastavte členem znak základní zdroje.  Další informace najdete v tématu [znakových sad](../../cpp/character-sets.md).  
  
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