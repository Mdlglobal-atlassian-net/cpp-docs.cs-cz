---
title: "Delegát (rozšíření komponent C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- delegate_cpp
- delegate
dev_langs: C++
helpviewer_keywords: delegate keyword [C++]
ms.assetid: 03caf23d-7873-4a23-9b34-becf42aaf429
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 43bab2679e958dbf8ffbd0f76b0d683636ba88de
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="delegate--c-component-extensions"></a>delegate (rozšíření komponent C++)
Deklaruje typ, který reprezentuje ukazatel na funkci.  
  
## <a name="all-runtimes"></a>Všechny moduly runtime  
 Prostředí Windows Runtime i modul common language runtime podporují delegáti.  
  
### <a name="remarks"></a>Poznámky  
 `delegate`je kontextová – klíčové slovo. Další informace najdete v tématu [klíčová slova Context-Sensitive](../windows/context-sensitive-keywords-cpp-component-extensions.md).  
  
 Detekuje v době kompilace, pokud je typem delegáta, použijte `__is_delegate()` typ znak. Další informace najdete v tématu [podpora kompilátoru pro typové vlastnosti](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
 C + +/ CX podporuje delegáti pomocí následující syntaxe.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
access  
delegate  
return-type  
delegate-type-identifier  
(  
[ parameters ]  
)  
  
```  
  
### <a name="parameters"></a>Parametry  
 *přístup*  
 (volitelné) Usnadnění přístupu delegáta, který může být `public` (výchozí) nebo `private`. Prototyp funkce může být také kvalifikovaný pomocí `const` nebo `volatile` klíčová slova.  
  
 *Návratový typ*  
 Návratový typ funkce prototypu.  
  
 *identifikátor typu delegáta*  
 Název typu deklarované delegáta.  
  
 *Parametry*  
 (Volitelné) Typy a identifikátory prototypu funkce.  
  
### <a name="remarks"></a>Poznámky  
 Použití *identifikátor typu delegáta* událost se stejnou prototyp jako delegáta deklarovat. Další informace najdete v tématu [delegáti (C + +/ CX)](../cppcx/delegates-c-cx.md).  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: **/ZW**  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime)  
 Modul common language runtime podporuje delegáti pomocí následující syntaxe.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
access  
delegate  
function_declaration  
  
```  
  
### <a name="parameters"></a>Parametry  
 *přístup*  
 (volitelné) Usnadnění přístupu delegáta mimo sestavení může být veřejné nebo soukromé.  Výchozí hodnota je soukromé.  Uvnitř třídy může mít delegáta žádné usnadnění.  
  
 *function_declaration*  
 Podpis funkce, která mohou být vázány na delegát. Návratový typ delegáta mohou být jakéhokoli typu spravované. Vzájemná funkční spolupráce z důvodů se doporučuje, že návratovým typem delegáta být typu specifikací CLS.  
  
 K definování delegáta nevázaný první parametr v *function_declaration* by měl být typu `this` ukazatele pro objekt. 
  
### <a name="remarks"></a>Poznámky  
 Delegáti jsou vícesměrového vysílání: "ukazatel funkce" může být vázaný na jeden nebo více metod v rámci spravované třídy. **Delegovat** – klíčové slovo definuje typ vícesměrového vysílání delegáta podpisem konkrétní metody.  
  
 Delegát mohou být také vázány na metodu – hodnotová třída, jako je například statickou metodu.  
  
 Delegát má následující vlastnosti:  
  
-   Dědí z **System::MulticastDelegate**.  
  
-   Má konstruktor, který přebírá dva argumenty: ukazatel na spravované třídy nebo **NULL** (v případě vazby ke statickou metodu) a plně kvalifikovaný metodu zadaného typu.  
  
-   Obsahuje metodu s názvem `Invoke`, jejichž podpis odpovídá deklarované podpis delegáta.  
  
 Po vyvolání delegáta je v pořadí, ve kterém byli připojeni jako jeho byly funkce.  
  
 Návratová hodnota delegáta je vrácená hodnota z jeho poslední připojené – členská funkce.  
  
 Delegáti nemohou být přetíženy.  
  
 Delegáti můžete vázaný nebo nevázaných.  
  
 Pokud instanci můžete vytvořit vázané delegáta, první argument musí být odkaz na objekt.  Druhý argument delegáta konkretizaci buď má, být adresa metody objektu spravované třídy nebo ukazatele na metodu typ hodnoty.   Druhý argument delegáta konkretizaci musí název metodu se syntaxí oboru úplné – třída a použít operátor adresy.  
  
 Pokud instanci můžete vytvořit nevázaný delegáta, být prvním argumentem buď adresu metody objektu spravované třídy nebo ukazatele na metodu typ hodnoty.   Argument musí název metodu se syntaxí oboru úplné třídy a použít operátor adresy.  
  
 Při vytváření delegátovi, aby se statickou nebo globální funkce, je vyžadován pouze jeden parametr: funkce (volitelně adresa funkce).  
  
 Další informace o delegáti najdete v tématu  
  
-   [Postupy: definice a používání delegátů (C + +/ CLI)](../dotnet/how-to-define-and-use-delegates-cpp-cli.md)  
  
-   [Obecní delegáti (Visual C++)](../windows/generic-delegates-visual-cpp.md)  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru:   **/CLR**  
  
### <a name="examples"></a>Příklady  
 **Příklad**  
  
 Následující příklad ukazuje, jak deklarovat, inicializace a vyvolání delegáti.  
  
```cpp  
// mcppv2_delegate.cpp  
// compile with: /clr  
using namespace System;  
  
// declare a delegate  
public delegate void MyDel(int i);  
  
ref class A {  
public:  
   void func1(int i) {  
      Console::WriteLine("in func1 {0}", i);  
   }  
  
   void func2(int i) {  
      Console::WriteLine("in func2 {0}", i);  
   }  
  
   static void func3(int i) {  
      Console::WriteLine("in static func3 {0}", i);  
   }  
};  
  
int main () {  
   A ^ a = gcnew A;  
  
   // declare a delegate instance  
   MyDel^ DelInst;  
  
   // test if delegate is initialized  
   if (DelInst)  
      DelInst(7);  
  
   // assigning to delegate  
   DelInst = gcnew MyDel(a, &A::func1);  
  
   // invoke delegate  
   if (DelInst)  
      DelInst(8);  
  
   // add a function  
   DelInst += gcnew MyDel(a, &A::func2);  
  
   DelInst(9);  
  
   // remove a function  
   DelInst -= gcnew MyDel(a, &A::func1);  
  
   // invoke delegate with Invoke  
   DelInst->Invoke(10);  
  
   // make delegate to static function  
   MyDel ^ StaticDelInst = gcnew MyDel(&A::func3);  
   StaticDelInst(11);  
}  
```  
  
 **Výstup**  
  
```Output  
in func1 8  
  
in func1 9  
  
in func2 9  
  
in func2 10  
  
in static func3 11  
```  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)