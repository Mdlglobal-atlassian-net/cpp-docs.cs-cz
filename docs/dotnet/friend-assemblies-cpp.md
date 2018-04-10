---
title: Přátelská sestavení (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- friend assemblies, Visual C++
ms.assetid: 8d55fee0-b7c2-4fbe-a23b-dfe424dc71cd
caps.latest.revision: 27
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6646306092844f11819b81ee076c54db840c618b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="friend-assemblies-c"></a>Přátelská sestavení (C++)
Pro příslušné runtimes *přátelských sestavení* typy, které jsou v oboru názvů nebo globálního oboru v komponentě sestavení, která je přístupná na jeden nebo více sestavení klienta nebo .netmodules díky funkci jazyka.  
  
## <a name="all-runtimes"></a>Všechny moduly runtime  
 **Poznámky**  
  
 (Tato funkce jazyka nepodporuje všechny moduly runtime.)  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
 **Poznámky**  
  
 (Tento jazyk funkce není podporována v prostředí Windows Runtime).  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: **/ZW**  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime) 
 **Poznámky**  
  
#### <a name="to-make-types-at-namespace-scope-or-global-scope-in-an-assembly-component-accessible-to-a-client-assembly-or-netmodule"></a>Aby typy v oboru názvů nebo globálního oboru v komponentu sestavení na sestavení klienta nebo .netmodule  
  
1.  V komponentě, zadejte atribut sestavení <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>a předat název sestavení klienta nebo .netmodule, který bude přístup k typům v oboru názvů nebo globálního oboru v součásti.  Můžete zadat více sestavení klienta nebo .netmodules tak, že zadáte další atributy.  
  
2.  V sestavení klienta nebo .netmodule, když odkazujete sestavení součástí s použitím `#using`, předat `as_friend` atribut.  Pokud zadáte `as_friend` atribut pro sestavení, která neurčuje `InternalsVisibleToAttribute`, bude vyvolána výjimku modulu runtime, pokud se pokusíte přistupovat k typu v oboru názvů nebo globálního oboru v součásti.  
  
 Chyby sestavení dojde, pokud je sestavení, který obsahuje <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut nemá silný název, ale klient sestavení, které používá `as_friend` nemá atribut.  
  
 I když na sestavení klienta nebo .netmodule můžete být známé typy v oboru názvů a globální obor, usnadnění člen je stále v platnosti.  Například nemáte přístup privátního člena.  
  
 Přístup pro všechny typy v sestavení musí být explicitně udělí oprávnění.  Například sestavení C nemá přístup pro všechny typy v sestavení A Pokud sestavení C odkazuje na sestavení B a sestavení B má přístup pro všechny typy v sestavení A.  
  
 Informace o tom, jak podepsat – to znamená, poskytnout silný název – sestavení vytvořené pomocí Visual C++ compiler, najdete v části [sestavení se silným názvem (podepisování sestavení) (C + +/ CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).  
  
 Jako alternativu k použití funkce friend sestavení, můžete použít <xref:System.Security.Permissions.StrongNameIdentityPermission> omezit přístup na jednotlivé typy.  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru:   **/CLR**  
  
### <a name="examples"></a>Příklady  
 Následující příklad kódu definuje komponenty, která určuje sestavení klienta, který má přístup k typům v součásti.  
  
```cpp  
// friend_assemblies.cpp  
// compile by using: /clr /LD  
using namespace System::Runtime::CompilerServices;  
using namespace System;  
// an assembly attribute, not bound to a type  
[assembly:InternalsVisibleTo("friend_assemblies_2")];  
  
ref class Class1 {  
public:  
   void Test_Public() {  
      Console::WriteLine("Class1::Test_Public");  
   }  
};  
```  
  
 Další příklad kódu používá privátní typu v součásti.  
  
```cpp  
// friend_assemblies_2.cpp  
// compile by using: /clr  
#using "friend_assemblies.dll" as_friend  
  
int main() {  
   Class1 ^ a = gcnew Class1;  
   a->Test_Public();  
}  
```  
  
```Output  
Class1::Test_Public  
```  
  
 Další příklad kódu definuje součást, ale neurčuje sestavení klienta, který bude mít přístup k typům v součásti.  
  
 Všimněte si, že součást je propojený s použitím **/ opt: noref**. To zajistí, že privátní typy jsou vygenerované v součásti metadata, která není nutné, když `InternalsVisibleTo` atribut je k dispozici. Další informace najdete v tématu [/OPT (optimalizace)](../build/reference/opt-optimizations.md).  
  
```cpp  
// friend_assemblies_3.cpp  
// compile by using: /clr /LD /link /opt:noref  
using namespace System;  
  
ref class Class1 {  
public:  
   void Test_Public() {  
      Console::WriteLine("Class1::Test_Public");  
   }  
};  
```  
  
 Následující příklad kódu definuje klienta se pokusí o přístup k typu privátní v komponenty, která není poskytnout přístup k jeho privátní typů. Z důvodu chování modulu runtime Pokud chcete zachytit výjimky, musí pokusíte přistupovat k privátní typu v podpůrné funkci.  
  
```cpp  
// friend_assemblies_4.cpp  
// compile by using: /clr  
#using "friend_assemblies_3.dll" as_friend  
using namespace System;  
  
void Test() {  
   Class1 ^ a = gcnew Class1;  
}  
  
int main() {  
   // to catch this kind of exception, use a helper function  
   try {  
      Test();     
   }  
   catch(MethodAccessException ^ e) {  
      Console::WriteLine("caught an exception");  
   }  
}  
```  
  
```Output  
caught an exception  
```
  
 Další příklad kódu ukazuje, jak vytvořit silné jméno – komponenty, která určuje sestavení klienta, který bude mít přístup k typům v součásti.  
  
```cpp  
// friend_assemblies_5.cpp  
// compile by using: /clr /LD /link /keyfile:friend_assemblies.snk  
using namespace System::Runtime::CompilerServices;  
using namespace System;  
// an assembly attribute, not bound to a type  
  
[assembly:InternalsVisibleTo("friend_assemblies_6, PublicKey=00240000048000009400000006020000002400005253413100040000010001000bf45d77fd991f3bff0ef51af48a12d35699e04616f27ba561195a69ebd3449c345389dc9603d65be8cd1987bc7ea48bdda35ac7d57d3d82c666b7fc1a5b79836d139ef0ac8c4e715434211660f481612771a9f7059b9b742c3d8af00e01716ed4b872e6f1be0e94863eb5745224f0deaba5b137624d7049b6f2d87fba639fc5")];  
  
private ref class Class1 {  
public:  
   void Test_Public() {  
      Console::WriteLine("Class1::Test_Public");  
   }  
};  
```  
  
 Všimněte si, že součást musíte zadat svůj veřejný klíč. Doporučujeme, spusťte následující příkazy postupně na příkazovém řádku k vytvoření páru klíčů a získání veřejného klíče:  
  
 **-d friend_assemblies.snk sn**  
  
 **sn -k friend_assemblies.snk**  
  
 **sn -i friend_assemblies.snk friend_assemblies.snk**  
  
 **key.publickey friend_assemblies.snk sn -počítač**  
  
 **-tp key.publickey sn**  
  
 Další příklad kódu používá privátního typu v komponentě silného názvu.  
  
```cpp  
// friend_assemblies_6.cpp  
// compile by using: /clr /link /keyfile:friend_assemblies.snk  
#using "friend_assemblies_5.dll" as_friend  
  
int main() {  
   Class1 ^ a = gcnew Class1;  
   a->Test_Public();  
}  
```  
  
```Output  
Class1::Test_Public  
```  
  
## <a name="see-also"></a>Viz také  
 [Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)