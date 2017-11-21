---
title: "Postupy: použití regulárních výrazů k extrakci datových polí (C + +/ CLI) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- strings [C++], extracting data from
- formatted strings [C++]
- regular expressions [C++], extracting data fields
- data [C++], extracting from strings
ms.assetid: b581d9b6-630e-48fa-94fe-20b0f7b89b06
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a297ee1676fb3ffbff45d46334d20280beeab078
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-use-regular-expressions-to-extract-data-fields-ccli"></a>Postupy: Použití regulárních výrazů k extrakci datových polí (C++/CLI)
Následující příklad kódu ukazuje použití regulárních výrazů extrahovat data z formátovaný řetězec. Následující příklad kódu používá <xref:System.Text.RegularExpressions.Regex> třída zadat vzor, který odpovídá e-mailovou adresu. Tento vzor zahrnuje identifikátory pole, které lze použít k načtení uživatele a částí názvu hostitele každou e-mailovou adresu. <xref:System.Text.RegularExpressions.Match> Třída se používá k provádění skutečné vzor shody. Pokud daná e-mailová adresa je platná, jsou extrahována a zobrazí uživatelské jméno a názvy hostitelů.  
  
## <a name="example"></a>Příklad  
  
```  
// Regex_extract.cpp  
// compile with: /clr  
#using <System.dll>  
  
using namespace System;  
using namespace System::Text::RegularExpressions;  
  
int main()  
{  
    array<String^>^ address=  
    {  
        "jay@southridgevideo.com",  
        "barry@adatum.com",  
        "treyresearch.net",  
        "karen@proseware.com"  
    };  
  
    Regex^ emailregex = gcnew Regex("(?<user>[^@]+)@(?<host>.+)");  
  
    for (int i=0; i<address->Length; i++)  
    {  
        Match^ m = emailregex->Match( address[i] );  
        Console::Write("\n{0,25}", address[i]);  
  
        if ( m->Success )   
        {  
            Console::Write("   User='{0}'",   
            m->Groups["user"]->Value);  
            Console::Write("   Host='{0}'",   
            m->Groups["host"]->Value);  
        }  
        else   
            Console::Write("   (invalid email address)");  
        }  
  
    Console::WriteLine("");  
    return 0;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Regulární výrazy rozhraní .NET framework](/dotnet/standard/base-types/regular-expressions)   
 [.NET – programování s C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)