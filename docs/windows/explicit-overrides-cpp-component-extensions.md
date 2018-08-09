---
title: Explicitní přepsání (rozšíření komponent C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- overriding, override [C++]
ms.assetid: 4ec3eaf5-163b-4df8-8f16-7a2ec04c3d0f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1dcf129f551900792638018fa846557120e53e96
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644349"
---
# <a name="explicit-overrides--c-component-extensions"></a>Explicitní přepsání (rozšíření komponent C++)
Toto téma popisuje postup explicitní přepsání člena základní třídy nebo rozhraní. Pojmenované přepsání (explicitně) by měla sloužit pouze k přepsání metody s Odvozená metoda, která má jiný název.  
  
## <a name="all-runtimes"></a>Všechny moduly runtime  
### <a name="syntax"></a>Syntaxe
  
```cpp  
overriding-function-declarator = type::function [,type::function] { overriding-function-definition }  
overriding-function-declarator = function { overriding-function-definition }  
```  

### <a name="parameters"></a>Parametry 
 *přepsání deklarátorem funkce*  
 Návratový typ, název a argumentu seznamu přepisující funkce.  Všimněte si, že není nutné mít stejný název jako funkce přepsání přepisující funkce.  
  
 *Typ*  
 Základní typ, který obsahuje funkci, kterou chcete přepsat.  
  
 *– funkce*  
 Čárkami oddělený seznam jednoho nebo více názvy funkcí, které chcete přepsat.  
  
 *přepsání definice funkce*  
 Příkazy tělo funkce, které definují přepisující funkce.  
  
### <a name="remarks"></a>Poznámky
  
 Použijte explicitní přepsání k vytvoření zástupce pro podpis metody a poskytují tak různé implementace pro pole stejnou signaturu metody.  
  
 Informace o úpravách chování se děděné typy a členy zděděných typů najdete v tématu [specifikátory přepisu](../windows/override-specifiers-cpp-component-extensions.md).  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: `/ZW`  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime) 
### <a name="remarks"></a>Poznámky
  
 Informace o explicitních přepsáních ve nativní kód nebo kód zkompilovaný s `/clr:oldSyntax`, naleznete v tématu [explicitní přepsání](../cpp/explicit-overrides-cpp.md).  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: `/clr`  
  
### <a name="examples"></a>Příklady   
  
 Následující příklad kódu ukazuje, jednoduché a implicitní přepsání a implementace členu základní rozhraní bez použití explicitní přepsání.  
  
```cpp  
// explicit_override_1.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
ref class X : public I1 {  
public:  
   virtual void f() {  
      System::Console::WriteLine("X::f override of I1::f");  
   }  
};  
  
int main() {  
   I1 ^ MyI = gcnew X;  
   MyI -> f();  
}  
```  
  
```Output  
X::f override of I1::f  
```  
  
 Následující příklad kódu ukazuje, jak implementovat všechny členy rozhraní s podpisem běžné pomocí syntaxe explicitního přepsání.  
  
```cpp  
// explicit_override_2.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
interface struct I2 {  
   virtual void f();  
};  
  
ref struct X : public I1, I2 {  
   virtual void f() = I1::f, I2::f {  
      System::Console::WriteLine("X::f override of I1::f and I2::f");  
   }  
};  
  
int main() {  
   I1 ^ MyI = gcnew X;  
   I2 ^ MyI2 = gcnew X;  
   MyI -> f();  
   MyI2 -> f();  
}  
```  
  
```Output  
X::f override of I1::f and I2::f  
X::f override of I1::f and I2::f  
```  
  
 Následující příklad kódu ukazuje, jak přepsat funkce může mít jiný název funkce, které implementuje.  
  
```cpp  
// explicit_override_3.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
ref class X : public I1 {  
public:  
   virtual void g() = I1::f {  
      System::Console::WriteLine("X::g");  
   }  
};  
  
int main() {  
   I1 ^ a = gcnew X;  
   a->f();  
}  
```  
  
```Output  
X::g  
```  
  
 Následující příklad kódu ukazuje explicitní implementací rozhraní, která implementuje kolekce bezpečného typu.  
  
```cpp  
// explicit_override_4.cpp  
// compile with: /clr /LD  
using namespace System;  
ref class R : ICloneable {  
   int X;  
  
   virtual Object^ C() sealed = ICloneable::Clone {  
      return this->Clone();  
   }  
  
public:  
   R() : X(0) {}  
   R(int x) : X(x) {}  
  
   virtual R^ Clone() {  
      R^ r = gcnew R;  
      r->X = this->X;  
      return r;  
   }  
};  
```  
  
## <a name="see-also"></a>Viz také  
 [Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)