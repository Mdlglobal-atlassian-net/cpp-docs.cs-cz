---
title: Delegate (C++vyhodnocovací a C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- delegate_cpp
- delegate
helpviewer_keywords:
- delegate keyword [C++]
ms.assetid: 03caf23d-7873-4a23-9b34-becf42aaf429
ms.openlocfilehash: 29bf305ed5e4845437b90ed672d1ab0c0de9ced6
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59036949"
---
# <a name="delegate--ccli-and-ccx"></a>Delegate (C++vyhodnocovací a C++/CX)

Deklaruje typ, který představuje ukazatel na funkci.

## <a name="all-runtimes"></a>Všechny moduly runtime

Prostředí Windows Runtime i modul common language runtime podporuje delegátů.

### <a name="remarks"></a>Poznámky

**Delegovat** je kontextové klíčové slovo. Další informace najdete v tématu [Context-Sensitive Keywords](context-sensitive-keywords-cpp-component-extensions.md).

Chcete-li zjistit v době kompilace, pokud typ je delegát, použijte `__is_delegate()` typovou vlastnost. Další informace najdete v tématu [podpora kompilátoru pro typové vlastnosti](compiler-support-for-type-traits-cpp-component-extensions.md).

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

*access*<br/>
(volitelné) Usnadnění delegáta, který může být **veřejné** (výchozí) nebo **privátní**. Prototyp funkce může také být kvalifikován s **const** nebo **volatile** klíčová slova.

*Návratový typ*<br/>
Návratový typ prototypu funkce.

*delegate-type-identifier*<br/>
Název typu deklarovaného delegáta.

*parameters*<br/>
(Volitelné) Typy a identifikátory prototypu funkce.

### <a name="remarks"></a>Poznámky

Použití *identifikátor typu delegáta* deklarovat událost s stejný prototyp jako delegát. Další informace najdete v tématu [delegátů (C++/CX)](../cppcx/delegates-c-cx.md).

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

Modul common language runtime podporuje delegáty s následující syntaxí.

### <a name="syntax"></a>Syntaxe

```cpp
access
delegate
function_declaration
```

### <a name="parameters"></a>Parametry

*access*<br/>
(volitelné) Usnadnění delegáta mimo sestavení může být veřejné nebo soukromé.  Výchozí hodnota je privátní.  Uvnitř třídy může mít delegáta jakoukoliv přístupností.

*function_declaration*<br/>
Signatura funkce, která může být vázána na delegáta. Návratový typ delegátu, může být jakékoli spravovaného typu. Vzájemná funkční spolupráce z důvodů se doporučuje, návratový typ delegátu být typ kompatibilní se Specifikací.

Chcete-li definovat delegáta bez vazby, první parametr v *function_declaration* by měl být typu **to** ukazatel objektu.

### <a name="remarks"></a>Poznámky

Delegáti jsou vícesměrového vysílání: ukazatel"funkce" může být vázaný na jednu nebo více metod v rámci spravované třídy. **Delegovat** – klíčové slovo definuje typ vícesměrového vysílání delegáta s podpisem konkrétní metody.

Delegát mohou také být vázány na metodu hodnotová třída, jako je například statické metody.

Delegát má následující vlastnosti:

- Dědí z `System::MulticastDelegate`.

- Má konstruktor, který přebírá dva argumenty: ukazatel na spravovanou třídu nebo hodnotu NULL (v případě vazby na statickou metodu) a plně kvalifikovaný metoda zadaného typu.

- Obsahuje metodu nazvanou `Invoke`, jehož předpis odpovídá deklarované signatura delegáta.

Při vyvolání delegáta jeho funkce jsou volány v pořadí, ve kterém byla připojena.

Návratový typ delegáta je návratová hodnota z jeho poslední připojené členskou funkci.

Delegáti nemohou být přetíženy.

Delegáty lze vázané nebo nevázaných.

Když vytvoříte instanci delegátu vázaný, první argument musí být odkaz na objekt. Druhý argument delegáta instance buď musí, být adresa metoda spravovanou třídu objektu nebo ukazatele na metodu hodnotového typu. Druhý argument delegáta instance musí pojmenujte metodu se syntaxí oboru úplné třídy a použití operátoru address-of.

Při vytváření instance delegáta bez vazby prvního argumentu musí být buď adresa metody spravovanou třídu objektu nebo ukazatele na metodu hodnotového typu. Argument musí pojmenujte metodu se syntaxí oboru úplné třídy a použití operátoru address-of.

Při vytvoření delegáta, kterého globální nebo statické funkce, se vyžaduje jenom jeden parametr: – funkce (volitelně adresu funkce).

Další informace o delegátech naleznete v tématu

- [Postupy: Definice a používání delegátů (C++/CLI)](../dotnet/how-to-define-and-use-delegates-cpp-cli.md)

- [Obecní delegáti (C++/CLI)](generic-delegates-visual-cpp.md)

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/clr`

### <a name="examples"></a>Příklady

Následující příklad ukazuje, jak deklarovat a inicializovat, vyvoláte.

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

## <a name="see-also"></a>Viz také:

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)