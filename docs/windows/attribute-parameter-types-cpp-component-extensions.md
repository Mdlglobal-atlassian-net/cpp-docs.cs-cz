---
title: "Atribut typy parametrů (C++ Component Extensions) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: custom attributes, parameter types
ms.assetid: d9f127a3-7f08-456f-acc6-256805632712
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 95e7ec4d1a4a6b473419c23b3565fcce9d5afed6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="attribute-parameter-types--c-component-extensions"></a>Typy parametrů atributů (rozšíření komponent C++)
Hodnoty předaný atributy musí být známo kompilátoru v době kompilace.  Parametry atributu může být z následujících typů:  
  
-   `bool`  
  
-   `char`, `unsigned char`  
  
-   `short`, `unsigned short`  
  
-   `int`, `unsigned int`  
  
-   `long`, `unsigned long`  
  
-   `__int64`, `unsigned __int64`  
  
-   `float`, `double`  
  
-   `wchar_t`  
  
-   `char*`nebo `wchar_t*` nebo`System::String*`  
  
-   `System::Type ^`  
  
-   `System::Object ^`  
  
-   `enum`  
  
## <a name="example"></a>Příklad  
  
### <a name="code"></a>Kód  
  
```  
// attribute_parameter_types.cpp  
// compile with: /clr /c  
using namespace System;  
ref struct AStruct {};  
  
[AttributeUsage(AttributeTargets::ReturnValue)]  
ref struct Attr : public Attribute {  
   Attr(AStruct ^ i){}  
   Attr(bool i){}  
   Attr(){}  
};  
  
ref struct MyStruct {  
   static AStruct ^ x = gcnew AStruct;  
   [returnvalue:Attr(x)] int Test() { return 0; }   // C3104  
   [returnvalue:Attr] int Test2() { return 0; }   // OK  
   [returnvalue:Attr(true)] int Test3() { return 0; }   // OK  
};  
```  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Při zadávání atributy, všechny nepojmenované argumenty (poziční) musí předcházet všechny pojmenované argumenty.  
  
### <a name="code"></a>Kód  
  
```  
// extending_metadata_c.cpp  
// compile with: /clr /c  
using namespace System;  
[AttributeUsage(AttributeTargets::Class)]  
ref class MyAttr : public Attribute {  
public:  
   MyAttr() {}  
   MyAttr(int i) {}  
   property int Priority;  
   property int Version;  
};  
  
[MyAttr]   
ref class ClassA {};   // No arguments  
  
[MyAttr(Priority = 1)]   
ref class ClassB {};   // Named argument  
  
[MyAttr(123)]   
ref class ClassC {};   // Positional argument  
  
[MyAttr(123, Version = 1)]   
ref class ClassD {};   // Positional and named  
```  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Parametry atributu může být jednorozměrné pole předchozí typů.  
  
### <a name="code"></a>Kód  
  
```  
// extending_metadata_d.cpp  
// compile with: /clr /c  
using namespace System;  
  
[AttributeUsage(AttributeTargets::Class)]  
public ref struct ABC : public Attribute {  
   ABC(array<int>^){}  
   array<double> ^ param;  
};  
  
[ABC( gcnew array<int> {1,2,3}, param = gcnew array<double>{2.71, 3.14})]   
ref struct AStruct{};  
```  
  
## <a name="see-also"></a>Viz také  
 [Uživatelsky definované atributy](../windows/user-defined-attributes-cpp-component-extensions.md)