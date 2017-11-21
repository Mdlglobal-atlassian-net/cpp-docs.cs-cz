---
title: "typeid (rozšíření komponent C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: typeid keyword [C++]
ms.assetid: e9706cae-e7c4-4d6d-b474-646d73df3e70
caps.latest.revision: "35"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a1d03fd235e1719ac3179cb91b9db5c1bdcec3fb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="typeid--c-component-extensions"></a>typeid (rozšíření komponent C++)
Získá hodnotu, která určuje typ objektu.  
  
> [!WARNING]
>  Toto téma označuje verzi rozšíření komponent C++ typeid. ISO C++ verzi toto klíčové slovo, naleznete v části [typeid – operátor](../cpp/typeid-operator.md).  
  
## <a name="all-runtimes"></a>Všechny moduly runtime  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
T::typeid  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Název typu.  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
Platform::Type^ type = T::typeid;  
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Název typu.  
  
### <a name="remarks"></a>Poznámky  
 V jazyce C + +/ CX, vrátí typeid [Platform::Type](../cppcx/platform-type-class.md) , se vytvářejí na základě informací o typu modulu runtime.  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: **/ZW**  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime) 
 **Syntaxe**  
  
```  
  
type::typeid  
```  
  
 **Parametry**  
  
 *Typ*  
 Název tohoto typu (abstraktní deklarátor), pro které chcete objekt System::Type.  
  
 **Poznámky**  
  
 `typeid`slouží k získání <xref:System.Type> pro typ v době kompilace.  
  
 `typeid`je podobná získávání System::Type pro typ za běhu pomocí <xref:System.Type.GetType%2A> nebo <xref:System.Object.GetType%2A>. Typeid však přijímá jenom název typu jako parametr.  Pokud chcete pomocí instance typu můžete zobrazit jeho System::Type název, použijte GetType.  
  
 `typeid`musí být schopen vyhodnotit název typu (typů) při kompilaci, zatímco GetType vyhodnotí typ určený k vrácení za běhu.  
  
 `typeid`může trvat název nativního typu nebo běžné alias runtime jazyka pro název nativního typu; v tématu [rozhraní .NET Framework – ekvivalenty k nativním typy C++ (C + +/ CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md) Další informace.  
  
 `typeid`taky spolupracuje se službou nativní typy, i když stále vrátí System::Type.  Struktura type_info získáte pomocí [typeid – operátor](../cpp/typeid-operator.md).  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru:   **/CLR**  
  
### <a name="examples"></a>Příklady  
 **Příklad**  
  
 Následující příklad porovnává typeid – klíčové slovo GetType() členu.  
  
```  
// keyword__typeid.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct G {  
   int i;  
};  
  
int main() {  
   G ^ pG = gcnew G;  
   Type ^ pType = pG->GetType();  
   Type ^ pType2 = G::typeid;  
  
   if (pType == pType2)  
      Console::WriteLine("typeid and GetType returned the same System::Type");  
   Console::WriteLine(G::typeid);  
  
   typedef float* FloatPtr;  
   Console::WriteLine(FloatPtr::typeid);  
}  
```  
  
 **Výstup**  
  
```Output  
typeid and GetType returned the same System::Type  
G  
  
System.Single*  
  
```  
  
 **Příklad**  
  
 Následující příklad ukazuje, že proměnná typu System::Type lze získat atributy pro typ.  Také ukazuje, že pro některé typy, budete muset vytvořit typedef používat `typeid`.  
  
```  
// keyword__typeid_2.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Security;  
using namespace System::Security::Permissions;  
  
typedef int ^ handle_to_int;  
typedef int * pointer_to_int;  
  
public ref class MyClass {};  
  
class MyClass2 {};  
  
[attribute(AttributeTargets::All)]  
ref class AtClass {  
public:  
   AtClass(Type ^) {  
      Console::WriteLine("in AtClass Type ^ constructor");  
   }  
};  
  
[attribute(AttributeTargets::All)]  
ref class AtClass2 {  
public:  
   AtClass2() {  
      Console::WriteLine("in AtClass2 constructor");  
   }  
};  
  
// Apply the AtClass and AtClass2 attributes to class B  
[AtClass(MyClass::typeid), AtClass2]     
[AttributeUsage(AttributeTargets::All)]  
ref class B : Attribute {};  
  
int main() {  
   Type ^ MyType = B::typeid;  
  
   Console::WriteLine(MyType->IsClass);  
  
   array<Object^>^ MyArray = MyType -> GetCustomAttributes(true);  
   for (int i = 0 ; i < MyArray->Length ; i++ )  
      Console::WriteLine(MyArray[i]);  
  
   if (int::typeid != pointer_to_int::typeid)  
      Console::WriteLine("int::typeid != pointer_to_int::typeid, as expected");  
  
   if (int::typeid == handle_to_int::typeid)  
      Console::WriteLine("int::typeid == handle_to_int::typeid, as expected");  
}  
```  
  
 **Výstup**  
  
```Output  
True  
  
in AtClass2 constructor  
  
in AtClass Type ^ constructor  
  
AtClass2  
  
System.AttributeUsageAttribute  
  
AtClass  
  
int::typeid != pointer_to_int::typeid, as expected  
  
int::typeid == handle_to_int::typeid, as expected  
```  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)