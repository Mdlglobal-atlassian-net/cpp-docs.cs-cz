---
title: 'Postupy: použití regulárních výrazů k vyhledávání a nahrazení (C + +/ CLI) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- search and replace
- Replace method
- regular expressions [C++], search and replace
ms.assetid: 12fe3e18-fe10-4b25-a221-19dc5eab3821
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: feb64670accef1cdcc5eedf9aa2b081dc41615b6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-regular-expressions-to-search-and-replace-ccli"></a>Postupy: Použití regulárních výrazů k vyhledávání a nahrazení (C++/CLI)
Následující příklad kódu ukazuje, jak třída regulárního výrazu <xref:System.Text.RegularExpressions.Regex> slouží k vyhledávání a nahrazování. To lze provést pomocí <xref:System.Text.RegularExpressions.Regex.Replace%2A> metoda. Je verze použitá přebírá dva řetězce jako vstup: řetězec, který má být změněn a řetězec, který má být vložen namísto oddílů (pokud existuje) odpovídající vzor zadané <xref:System.Text.RegularExpressions.Regex> objektu.  
  
 Tento kód nahradí všechny číslice v řetězci podtržítka (_) a ty prázdný řetězec, znamenalo vyjmutí je pak nahradí. Stejného efektu dosáhnete v jediném kroku, ale dva kroky se zde používají pro demonstrační účely.  
  
## <a name="example"></a>Příklad  
  
```  
// regex_replace.cpp  
// compile with: /clr  
#using <System.dll>  
using namespace System::Text::RegularExpressions;  
using namespace System;  
  
int main()  
{  
   String^ before = "The q43uick bro254wn f0ox ju4mped";  
   Console::WriteLine("original  : {0}", before);  
  
   Regex^ digitRegex = gcnew Regex("(?<digit>[0-9])");  
   String^ after = digitRegex->Replace(before, "_");  
   Console::WriteLine("1st regex : {0}", after);  
  
   Regex^ underbarRegex = gcnew Regex("_");  
   String^ after2 = underbarRegex->Replace(after, "");  
   Console::WriteLine("2nd regex : {0}", after2);  
  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Regulární výrazy rozhraní .NET framework](/dotnet/standard/base-types/regular-expressions)   
 [Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)