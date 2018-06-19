---
title: 'Postupy: načtení textu ze schránky (C + +/ CLI) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- text, retrieving from Clipboard
- Clipboard, retrieving text
ms.assetid: 99e77ba0-8573-4030-92d8-de8aa7623ee4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ee1b2475e0d32b857ef5adfa2e75fb02e287d42f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33127900"
---
# <a name="how-to-retrieve-text-from-the-clipboard-ccli"></a>Postupy: Načtení textu ze schránky (C++/CLI)
Následující příklad kódu používá <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> – členská funkce vrátit ukazatel <xref:System.Windows.Forms.IDataObject> rozhraní. Toto rozhraní můžete potom dotaz pro formát data a používá se k načtení skutečná data.  
  
## <a name="example"></a>Příklad  
  
```  
// read_clipboard.cpp  
// compile with: /clr  
#using <system.dll>  
#using <system.Drawing.dll>  
#using <system.windows.forms.dll>  
  
using namespace System;  
using namespace System::Windows::Forms;  
  
[STAThread] int main( )  
{  
   IDataObject^ data = Clipboard::GetDataObject( );  
  
   if (data)  
   {  
      if (data->GetDataPresent(DataFormats::Text))   
      {  
         String^ text = static_cast<String^>  
           (data->GetData(DataFormats::Text));  
         Console::WriteLine(text);   
      }  
      else  
         Console::WriteLine("Nontext data is in the Clipboard.");  
   }  
   else   
   {  
      Console::WriteLine("No data was found in the Clipboard.");  
   }  
  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Operace systému Windows (C + +/ CLI)](../dotnet/windows-operations-cpp-cli.md)   
 [Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)