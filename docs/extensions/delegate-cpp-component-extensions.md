---
title: Delegate (C++/CLI a C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- delegate_cpp
- delegate
helpviewer_keywords:
- delegate keyword [C++]
ms.assetid: 03caf23d-7873-4a23-9b34-becf42aaf429
ms.openlocfilehash: 388ccb28c9311b4727199e6b7324771c24c2906d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172435"
---
# <a name="delegate--ccli-and-ccx"></a>Delegate (C++/CLI a C++/CX)

Deklaruje typ, který reprezentuje ukazatel na funkci.

## <a name="all-runtimes"></a>Všechny moduly runtime

Prostředí Windows Runtime i modul Common Language Runtime podporují delegáty.

### <a name="remarks"></a>Poznámky

**delegát** je kontextově závislé klíčové slovo. Další informace najdete v tématu [Kontextově závislá klíčová slova](context-sensitive-keywords-cpp-component-extensions.md).

Chcete-li zjistit v době kompilace, pokud je typ delegát, použijte vlastnost typu `__is_delegate()`. Další informace naleznete v tématu [Podpora kompilátoru pro typové vlastnosti](compiler-support-for-type-traits-cpp-component-extensions.md).

## <a name="windows-runtime"></a>prostředí Windows Runtime

C++/CX podporuje delegáty s následující syntaxí.

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

*stoupit*<br/>
volitelné Přístupnost delegáta, který může být **veřejný** (výchozí) nebo **soukromý**. Prototyp funkce může být také kvalifikován pomocí klíčových slov **const** nebo **volatile** .

*návratový typ*<br/>
Návratový typ prototypu funkce.

*Delegate – identifikátor typu*<br/>
Název deklarovaného typu delegáta.

*parameters*<br/>
Volitelné Typy a identifikátory prototypu funkce.

### <a name="remarks"></a>Poznámky

Pomocí *identifikátoru typu delegáta* deklarujete událost se stejným prototypem jako delegát. Další informace naleznete v tématu [DelegatesC++(/CX)](../cppcx/delegates-c-cx.md).

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

Modul CLR (Common Language Runtime) podporuje delegáty s následující syntaxí.

### <a name="syntax"></a>Syntaxe

```cpp
access
delegate
function_declaration
```

### <a name="parameters"></a>Parametry

*stoupit*<br/>
volitelné Přístupnost delegáta mimo sestavení může být veřejná nebo soukromá.  Výchozí hodnota je Private.  V rámci třídy může delegát mít jakoukoli přístupnost.

*function_declaration*<br/>
Signatura funkce, která může být svázána s delegátem. Návratový typ delegáta může být jakýkoli spravovaný typ. Z důvodů interoperability je doporučeno, aby návratový typ delegáta byl typu CLS.

Chcete-li definovat nevázaný delegát, první parametr v *function_declaration* by měl být typem **tohoto** ukazatele pro objekt.

### <a name="remarks"></a>Poznámky

Delegáti jsou vícesměrové vysílání: "ukazatel na funkci" může být vázán na jednu nebo více metod v rámci spravované třídy. Klíčové slovo **Delegate** definuje typ delegáta vícesměrového vysílání s konkrétním podpisem metody.

Delegát může být také svázán s metodou hodnotové třídy, jako je například statická metoda.

Delegát má následující vlastnosti:

- Dědí z `System::MulticastDelegate`.

- Má konstruktor, který přijímá dva argumenty: ukazatel na spravovanou třídu nebo hodnotu NULL (v případě vazby na statickou metodu) a plně kvalifikovanou metodu zadaného typu.

- Obsahuje metodu s názvem `Invoke`, jejíž signatura odpovídá deklarovanému podpisu delegáta.

Když je vyvolán delegát, funkce jsou volány v pořadí, v jakém byly připojeny.

Návratová hodnota delegáta je návratovou hodnotou z poslední připojené členské funkce.

Delegáty nemohou být přetíženy.

Delegáty můžou být vázané nebo nevázané.

Při vytváření instance vázaného delegáta musí být prvním argumentem odkaz na objekt. Druhý argument instance delegáta musí být buď adresa metody objektu spravované třídy, nebo ukazatel na metodu typu hodnoty. Druhý argument instance delegáta musí pojmenovat metodu s úplnou syntaxí oboru třídy a použít operátor address-of.

Při vytváření instance nevázaného delegáta musí být prvním argumentem buď adresa metody objektu spravované třídy, nebo ukazatel na metodu typu hodnoty. Argument musí pojmenovat metodu s úplnou syntaxí oboru třídy a použít operátor address-of.

Při vytváření delegáta statických nebo globálních funkcí je vyžadován pouze jeden parametr: funkce (volitelně adresa funkce).

Další informace o delegátech naleznete v tématu.

- [Postupy: Definice a používání delegátů (C++/CLI)](../dotnet/how-to-define-and-use-delegates-cpp-cli.md)

- [Obecní delegáti (C++/CLI)](generic-delegates-visual-cpp.md)

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/clr`

### <a name="examples"></a>Příklady

Následující příklad ukazuje, jak deklarovat, inicializovat a vyvolat delegáty.

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

```Output
in func1 8

in func1 9

in func2 9

in func2 10

in static func3 11
```

## <a name="see-also"></a>Viz také

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)
