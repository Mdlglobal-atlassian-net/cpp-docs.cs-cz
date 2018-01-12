---
title: "Postupy: použití regulárních výrazů ke změně uspořádání dat (C + +/ CLI) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- regular expressions [C++], rearranging data
- data [C++], rearranging
ms.assetid: 5f91e777-9471-424e-ba75-dca3d1b49e42
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: bf60fff6c15313a6f7df1104f67c1f043f885eac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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