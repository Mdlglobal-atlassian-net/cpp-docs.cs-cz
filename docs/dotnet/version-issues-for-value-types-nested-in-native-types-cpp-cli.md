---
title: "Problémy s verzí u typů hodnot vnořených v nativních typech (C + +/ CLI) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- __nogc type declarations
- __value keyword, issues when nesting
ms.assetid: 0a3b1a43-39c6-4b52-be2f-1074690188aa
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a16b6fd7d166b7a997257bfd6cb741b82911c5bd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="version-issues-for-value-types-nested-in-native-types-ccli"></a>Problémy s verzí u typů hodnot vnořených v nativních typech (C++/CLI)
Vezměte v úvahu komponentu sestavení podepsané (silný název) používá k vytvoření klientského sestavení. Součást obsahuje typ hodnoty, který se používá v klientovi jako typ člena skupiny nativní union, třídu nebo pole. Pokud budoucí verze komponenty změní velikost nebo rozložení typ hodnoty, klient musí zopakovat.  
  
 Vytvoření souboru keyfile s [sn.exe](/dotnet/framework/tools/sn-exe-strong-name-tool) (`sn -k mykey.snk`).  
  
## <a name="example"></a>Příklad  
 Následující příklad je součást.  
  
```  
// nested_value_types.cpp  
// compile with: /clr /LD  
using namespace System::Reflection;  
[assembly:AssemblyVersion("1.0.0.*"),   
assembly:AssemblyKeyFile("mykey.snk")];  
  
public value struct S {  
   int i;  
   void Test() {  
      System::Console::WriteLine("S.i = {0}", i);  
   }  
};  
```  
  
## <a name="example"></a>Příklad  
 Tato ukázka je klienta:  
  
```  
// nested_value_types_2.cpp  
// compile with: /clr  
#using <nested_value_types.dll>  
  
struct S2 {  
   S MyS1, MyS2;  
};  
  
int main() {  
   S2 MyS2a, MyS2b;  
   MyS2a.MyS1.i = 5;  
   MyS2a.MyS2.i = 6;  
   MyS2b.MyS1.i = 10;  
   MyS2b.MyS2.i = 11;  
  
   MyS2a.MyS1.Test();  
   MyS2a.MyS2.Test();  
   MyS2b.MyS1.Test();  
   MyS2b.MyS2.Test();  
}  
```  
  
## <a name="output"></a>Výstup  
  
```  
S.i = 5  
S.i = 6  
S.i = 10  
S.i = 11  
```  
  
### <a name="comments"></a>Komentáře  
 Ale pokud přidáte jiného člena pro `struct S` v nested_value_types.cpp (například `double d;`) a znovu zkompiluje komponentu bez nutnosti rekompilace klienta, výsledkem je k neošetřené výjimce (typu <xref:System.IO.FileLoadException?displayProperty=fullName>).  
  
## <a name="see-also"></a>Viz také  
 [Spravované typy (C + +/ CLI)](../dotnet/managed-types-cpp-cli.md)