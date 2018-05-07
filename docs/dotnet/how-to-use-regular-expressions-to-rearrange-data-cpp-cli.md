---
title: 'Postupy: použití regulárních výrazů ke změně uspořádání dat (C + +/ CLI) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- regular expressions [C++], rearranging data
- data [C++], rearranging
ms.assetid: 5f91e777-9471-424e-ba75-dca3d1b49e42
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 72c72721aa68417ff13905fdf96f8d2a48b310cd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-regular-expressions-to-rearrange-data-ccli"></a>Postupy: Použití regulárních výrazů ke změně uspořádání dat (C++/CLI)
Následující příklad kódu ukazuje, jak podporu regulárního výrazu rozhraní .NET Framework slouží k uspořádání nebo přeformátování data. Následující příklad kódu používá <xref:System.Text.RegularExpressions.Regex> a <xref:System.Text.RegularExpressions.Match> třídy k extrahování jména a příjmení z řetězce a následně se zobrazí tyto prvky název v obráceném pořadí.  
  
 <xref:System.Text.RegularExpressions.Regex> Třída se používá pro konstrukci regulární výraz, který popisuje aktuální formát data. Tyto názvy se předpokládá, že do čárkami oddělených a můžete použít libovolného počtu mezer kolem čárkou. <xref:System.Text.RegularExpressions.Match> Metoda se pak použije k analýze každý řetězec. V případě úspěšného jména a příjmení jsou načteny z <xref:System.Text.RegularExpressions.Match> objektu a zobrazit.  
  
## <a name="example"></a>Příklad  
  
```  
// regex_reorder.cpp  
// compile with: /clr  
#using <System.dll>  
using namespace System;  
using namespace Text::RegularExpressions;  
  
int main()  
{  
   array<String^>^ name =   
   {  
      "Abolrous, Sam",   
      "Berg,Matt",   
      "Berry , Jo",  
      "www.contoso.com"  
   };  
  
   Regex^ reg = gcnew Regex("(?<last>\\w*)\\s*,\\s*(?<first>\\w*)");  
  
   for ( int i=0; i < name->Length; i++ )  
   {  
      Console::Write( "{0,-20}", name[i] );  
      Match^ m = reg->Match( name[i] );  
      if ( m->Success )  
      {  
         String^ first = m->Groups["first"]->Value;  
         String^ last = m->Groups["last"]->Value;  
         Console::WriteLine("{0} {1}", first, last);  
      }  
      else  
         Console::WriteLine("(invalid)");  
   }  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Regulární výrazy rozhraní .NET framework](/dotnet/standard/base-types/regular-expressions)   
 [Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)