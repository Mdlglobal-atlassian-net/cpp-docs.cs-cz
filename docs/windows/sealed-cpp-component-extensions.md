---
title: "zapečetěné (rozšíření komponent C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sealed_cpp
- sealed
dev_langs:
- C++
helpviewer_keywords:
- sealed keyword [C++]
ms.assetid: 3d0d688a-41aa-45f5-a25a-65c44206521e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bb8a8b7ea695d878235898a8741adf04ba91748c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="sealed--c-component-extensions"></a>sealed (rozšíření komponent C++)
`sealed`kontextové klíčové slovo pro ref třídy, které určuje, že nebylo možné přepsat člena virtuální nebo že typu nelze použít jako základní typ je.  
  
> [!NOTE]
>  ISO C ++ 11 standardní jazyk má [konečné](../cpp/final-specifier.md) – klíčové slovo, který není podporován v sadě Visual Studio. Použití `final` na standardní třídy a `sealed` na ref třídy.  
  
## <a name="all-runtimes"></a>Všechny moduly runtime  
  
## <a name="syntax"></a>Syntaxe
  
```  
ref class identifier sealed {...};  
virtual return-type identifier() sealed {...};  
```  
  
### <a name="parameters"></a>Parametry  
  
 *identifikátor*  
 Název třídy nebo funkce.  
  
 *Návratový typ*  
 Typ, který je vrácené funkcí.  
  
## <a name="remarks"></a>Poznámky  
  
 V prvním příkladu syntaxe je zapečetěná třídu. V druhém příkladu je zapečetěná virtuální funkce.  
  
 `sealed` – Klíčové slovo je platný pro nativní cíle a také pro prostředí Windows Runtime a modul CLR (CLR). Další informace najdete v tématu [specifikátory Override a nativní kompilace](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).  
  
 V době kompilace může zjistit, zda je typ zapečetěná pomocí `__is_sealed(type)` typ znak. Další informace najdete v tématu [podpora kompilátoru pro typové vlastnosti](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
 `sealed`je kontextová – klíčové slovo.  Další informace najdete v tématu [klíčová slova Context-Sensitive](../windows/context-sensitive-keywords-cpp-component-extensions.md).  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
 V tématu [Ref třídy a struktury](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx).  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: **/ZW**  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime)  
 (Existují žádné poznámky pro tuto funkci jazyka, která se týkají jenom modul common language runtime).  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru:   **/CLR**  
  
### <a name="examples"></a>Příklady  
 Tento příklad kódu ukazuje účinek `sealed` na člena virtuální.  
  
```cpp  
// sealed_keyword.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
   virtual void g();  
};  
  
ref class X : I1 {  
public:  
   virtual void f() {  
      System::Console::WriteLine("X::f override of I1::f");  
   }  
  
   virtual void g() sealed {  
      System::Console::WriteLine("X::f override of I1::g");  
   }  
};  
  
ref class Y : public X {  
public:  
   virtual void f() override {  
      System::Console::WriteLine("Y::f override of I1::f");  
   }  
  
   /*  
   // the following override generates a compiler error  
   virtual void g() override {  
      System::Console::WriteLine("Y::g override of I1::g");  
   }    
   */  
};  
  
int main() {  
   I1 ^ MyI = gcnew X;  
   MyI -> f();  
   MyI -> g();  
  
   I1 ^ MyI2 = gcnew Y;  
   MyI2 -> f();  
}  
```  
  
```Output  
X::f override of I1::f  
X::f override of I1::g  
Y::f override of I1::f  
```  
  
 Další příklad kódu ukazuje, jak označit jako zapečetěné třídy.  
  
```cpp  
// sealed_keyword_2.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
ref class X sealed : I1 {  
public:  
   virtual void f() override {}  
};  
  
ref class Y : public X {   // C3246 base class X is sealed  
public:  
   virtual void f() override {}  
};  
```  
  
## <a name="see-also"></a>Viz také  
 [Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)