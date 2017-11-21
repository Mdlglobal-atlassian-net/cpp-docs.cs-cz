---
title: "Postupy: výčet datových typů pomocí reflexe (C + +/ CLI) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- assemblies [C++], enumerating data types in
- public types [C++]
- reflection [C++], external assemblies
- assemblies [C++]
- data types [C++], enumerating
- public members [C++]
ms.assetid: c3578e6d-bb99-4599-80e1-ab795305f878
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d89324e49cb08014892d08a046221b9a1e28d2e7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-enumerate-data-types-in-assemblies-using-reflection-ccli"></a>Postupy: Výčet datových typů v sestaveních pomocí reflexe (C++/CLI)
Následující kód ukazuje výčet veřejných typů a členů pomocí <xref:System.Reflection>.  
  
 Zadaný název sestavení, v místním adresáři nebo v mezipaměti GAC, následující kód pokusí otevřít sestavení a načíst popisy. Pokud bylo úspěšné, zobrazí se každý typ s jeho veřejné členy.  
  
 Všimněte si, že <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> vyžaduje, aby se používala bez přípony souboru. Proto použití "mscorlib.dll" jako argument příkazového řádku se nezdaří, při použití jenom "mscorlib" způsobí zobrazení typů rozhraní .NET Framework. Pokud je zadaný žádný název sestavení, kód rozpozná a typů v rámci aktuální sestavení sestav (EXE, vyplývající z tohoto kódu).  
  
## <a name="example"></a>Příklad  
  
```  
// self_reflection.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Reflection;  
using namespace System::Collections;  
  
public ref class ExampleType {  
public:  
   ExampleType() {}  
   void Func() {}  
};  
  
int main() {  
   String^ delimStr = " ";  
   array<Char>^ delimiter = delimStr->ToCharArray( );  
   array<String^>^ args = Environment::CommandLine->Split( delimiter );  
  
// replace "self_reflection.exe" with an assembly from either the local  
// directory or the GAC  
   Assembly^ a = Assembly::LoadFrom("self_reflection.exe");  
   Console::WriteLine(a);  
  
   int count = 0;  
   array<Type^>^ types = a->GetTypes();  
   IEnumerator^ typeIter = types->GetEnumerator();  
  
   while ( typeIter->MoveNext() ) {  
      Type^ t = dynamic_cast<Type^>(typeIter->Current);  
      Console::WriteLine("   {0}", t->ToString());  
  
      array<MemberInfo^>^ members = t->GetMembers();  
      IEnumerator^ memberIter = members->GetEnumerator();  
      while ( memberIter->MoveNext() ) {  
         MemberInfo^ mi = dynamic_cast<MemberInfo^>(memberIter->Current);  
         Console::Write("      {0}", mi->ToString( ) );  
         if (mi->MemberType == MemberTypes::Constructor)  
            Console::Write("   (constructor)");  
  
         Console::WriteLine();  
      }  
      count++;  
   }  
   Console::WriteLine("{0} types found", count);  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Reflexe (C + +/ CLI)](../dotnet/reflection-cpp-cli.md)