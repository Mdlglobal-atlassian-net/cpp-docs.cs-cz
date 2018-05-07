---
title: 'Postupy: čtení z textového souboru (C + +/ CLI) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- reading text files
- text files, reading
ms.assetid: 80551c01-d769-4b6d-8db7-fd53bde21b62
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c350ea9cd8b71378d059a93ac80ca808d4f48790
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-read-a-text-file-ccli"></a>Postupy: Čtení z textového souboru (C++/CLI)
Následující příklad kódu ukazuje, jak otevřít a přečíst si text jeden řádek souboru současně, pomocí <xref:System.IO.StreamReader> třídu, která je definována v <xref:System.IO?displayProperty=fullName> oboru názvů. Instance této třídy se používá k otevření textového souboru a potom <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=fullName> metoda se používá k načtení každý řádek.  
  
 Tento příklad kódu přečte soubor, který má název textfile.txt a obsahuje text. Informace o tento druh souborů najdete v tématu [postupy: zápis do textového souboru (C + +/ CLI)](../dotnet/how-to-write-a-text-file-cpp-cli.md).  
  
## <a name="example"></a>Příklad  
  
```  
// text_read.cpp  
// compile with: /clr  
#using<system.dll>  
using namespace System;  
using namespace System::IO;  
  
int main()  
{  
   String^ fileName = "textfile.txt";  
   try   
   {  
      Console::WriteLine("trying to open file {0}...", fileName);  
      StreamReader^ din = File::OpenText(fileName);  
  
      String^ str;  
      int count = 0;  
      while ((str = din->ReadLine()) != nullptr)   
      {  
         count++;  
         Console::WriteLine("line {0}: {1}", count, str );  
      }  
   }  
   catch (Exception^ e)  
   {  
      if (dynamic_cast<FileNotFoundException^>(e))  
         Console::WriteLine("file '{0}' not found", fileName);  
      else  
         Console::WriteLine("problem reading file '{0}'", fileName);  
   }  
  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Souborová služba a datový proud I-O](http://msdn.microsoft.com/Library/4f4a33a9-66b7-4cd7-a285-4ad3e4276cd2)   
 [Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)