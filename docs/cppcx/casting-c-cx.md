---
title: Přetypování (C + +/ CX)
ms.date: 06/19/2018
ms.assetid: 5247f6c7-6a0a-4021-97c9-21c868bd9455
ms.openlocfilehash: 65d489d14c91b462e5a2bbe8bd60fce2657904a7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454818"
---
# <a name="casting-ccx"></a>Přetypování (C + +/ CX)

Čtyři operátory různých přetypování se vztahují na typy Windows Runtime: [static_cast – operátor](../cpp/static-cast-operator.md), [dynamic_cast – operátor](../cpp/dynamic-cast-operator.md), **operátoru safe_cast**, a [ reinterpret_cast – operátor](../cpp/reinterpret-cast-operator.md). **safe_cast** a **static_cast** vyvolat výjimku, pokud převod nelze provést; [static_cast – operátor](../cpp/static-cast-operator.md) také provede kontrolu typů za kompilace. **přetypování dynamic_cast** vrátí **nullptr** , pokud se typ převést nepodaří. I když **reinterpret_cast** vrátí nenulovou hodnotu, může být neplatný. Z tohoto důvodu doporučujeme je velmi riskantní používat **reinterpret_cast** Pokud si nejste jisti, že bude úspěšné přetypování. Kromě toho doporučujeme je velmi riskantní používat přetypování ve stylu jazyka C ve vaší C + +/ CX kódu, protože jsou stejné jako **reinterpret_cast**.

Kompilovacími a běhovými také provést implicitní přetypování – například v operace zabalení, když typ hodnoty nebo předdefinovaný typ jsou předány jako argumenty metody parametr, jehož typ je `Object^`. Teoreticky by měla implicitní přetypování nikdy nezpůsobí výjimku za běhu; Pokud kompilátor nemůže provést implicitní převod, vyvolá chybu v době kompilace.

Prostředí Windows Runtime je abstrakcí modelu COM, který používá kódy chyb HRESULT místo výjimek. Obecně platí [Platform::InvalidCastException –](../cppcx/platform-invalidcastexception-class.md) označuje chybu nízké úrovně modelu COM z E_NOINTERFACE.

## <a name="staticcast"></a>static_cast

A **static_cast** je zaškrtnuté políčko v době kompilace k určení, zda je mezi těmito dvěma typy vztah dědičnosti. Přetypování způsobí chybu kompilátoru, pokud nejsou související typy.

A **static_cast** na ref třídy také způsobí, že kontrola běhu, která se má provést. A **static_cast** na ref třída projít ověřením čas kompilace ale nezdaří za běhu; v tomto případě `Platform::InvalidCastException` je vyvolána výjimka. Obecně platí nemusíte tyto výjimky zpracovat, protože téměř vždy označují programové chyby, které se můžete vyloučit během vývoje a testování.

Použití **static_cast** Pokud kód deklaruje explicitně relaci mezi těmito dvěma typy a jste proto si jisti, že by měl fungovat přetypování.

```cpp
    interface class A{};
    public ref class Class1 sealed : A { };
    // ...
    A^ obj = ref new Class1(); // Class1 is an A
    // You know obj is a Class1. The compiler verifies that this is possible, and in C++/CX a run-time check is also performed.
    Class1^ c = static_cast<Class1^>(obj);
```

## <a name="safecast"></a>safe_cast

**Safe_cast** operátor je součástí prostředí Windows Runtime. Provede kontrolu typu za běhu a vyvolá výjimku `Platform::InvalidCastException` Pokud převod selže. Použití **safe_cast** po selhání za běhu naznačuje výjimečné podmínce. Hlavním účelem **safe_cast** je vám pomůže identifikovat programové chyby během vývoje a testování, fáze v místě, kde k nim dojde. Není nutné zpracovat výjimku, protože neošetřená výjimka, samotný identifikuje bod selhání.

Používání operátoru safe_cast, pokud kód nedeklaruje relace, ale jste si jisti, že by měl fungovat přetypování.

```cpp
    // A and B are not related
    interface class A{};
    interface class B{};
    public ref class Class1 sealed : A, B { };
    // ...
    A^ obj = ref new Class1();

    // You know that obj’s backing type implements A and B, but
    // the compiler can’t tell this by comparing A and B. The run-time type check succeeds.
    B^ obj2 = safe_cast<B^>(obj);
```

## <a name="dynamiccast"></a>dynamic_cast

Použití **dynamic_cast** při přetypování objektu (přesněji řečeno, hat **^**) na více odvozený typ, očekáváte, že buď cílový objekt může být někdy **nullptr** nebo, který může selhat přetypování a vy chcete zpracovávat jako regulární kódové cestě místo výjimku tuto podmínku. Například v **prázdná aplikace (Universal Windows)** šablony projektu, `OnLaunched` metoda používá app.xamp.cpp **dynamic_cast** k ověření, zda má obsah okna aplikace. Není chyba Pokud nemá obsahu; jde o očekávané stav. `Windows::Current::Content` je `Windows::UI::XAML::UIElement` a převod `Windows::UI.XAML::Controls::Frame`, což je více odvozený typ v hierarchii dědičnosti.

```cpp
void App::OnLaunched(Windows::ApplicationModel::Activation::LaunchActivatedEventArgs^ args)
{
    auto rootFrame = dynamic_cast<Frame^>(Window::Current->Content);

    // Do not repeat app initialization when the window already has content,
    // just ensure that the window is active
    if (rootFrame == nullptr)
    {
        // Create a Frame to act as the navigation context and associate it with
        // a SuspensionManager key
        rootFrame = ref new Frame();
        // ...
    }
}
```

Další používání **dynamic_cast** je testovat `Object^` k určení, zda obsahuje zabalený typ hodnoty. V takovém případě pokus `dynamic_cast<Platform::Box>` nebo `dynamic_cast<Platform::IBox>`.

## <a name="dynamiccast-and-tracking-references-"></a>odkazy přetypování dynamic_cast a sledování (%)

Můžete také použít **dynamic_cast** sledovacímu odkazu, ale v tomto případě přetypování se chová jako **safe_cast**. Vyvolá `Platform::InvalidCastException` při selhání vzhledem k tomu, že sledovací odkaz nemůže mít hodnotu **nullptr**.

## <a name="reinterpretcast"></a>reinterpret_cast

Doporučujeme, abyste je velmi riskantní používat [reinterpret_cast](../cpp/reinterpret-cast-operator.md) protože je prováděna kontrola v době kompilace ani kontrolu za běhu. V nejhorším případě **reinterpret_cast** umožňuje programovací chyby pokračovat nezjištěné po v době vývoje a způsobit drobné nebo katastrofální chyby v chování vašeho programu. Proto doporučujeme použít **reinterpret_cast** pouze v těchto výjimečných případech, kdy musíte přetypovat mezi nesouvisejících typů a víte, že bude úspěšné přetypování. Příklad výjimečných používání je převést typ Windows Runtime na svůj podkladový typ ABI – to znamená, že jsou převzetí kontroly nad pro objekt pro počítání odkazů. K tomuto účelu doporučujeme použít [comptr – třída](../cpp/com-ptr-t-class.md) inteligentního ukazatele. V opačném případě je třeba konkrétně volat verze v rozhraní. Následující příklad ukazuje, jak třídy ref class lze převést na `IInspectable*`.

```cpp
#include <wrl.h>
using namespace Microsoft::WRL;
auto winRtObject = ref new SomeWinRTType();
ComPtr<IInspectable> inspectable = reinterpret_cast<IInspectable*>(winRtObject);
// ...
```

Pokud používáte **reinterpret_cast** pro převod z oneWindows modul Runtime rozhraní do jiného, vám zajistí, že objekt vydávaly dvakrát. Proto pouze používejte toto přetypování při převodu na rozšíření rozhraní komponenty než Visual C++.

## <a name="abi-types"></a>Typy ABI

- Typy ABI živě v záhlaví v sadě Windows SDK. Pohodlná, záhlaví pojmenován v oborech názvů – například `windows.storage.h`.

- Typy ABI živé ve speciální obor názvů ABI – například `ABI::Windows::Storage::Streams::IBuffer*`.

- Převody mezi typem rozhraní Windows Runtime a jeho ekvivalentní typ ABI jsou vždy bezpečné – to znamená `IBuffer^` k `ABI::IBuffer*`.

- Modul runtime třídy Windows Runtime by měla vždy převést na `IInspectable*` nebo výchozí rozhraní, pokud je, který je znám.

- Po převodu na typy ABI vlastní doba života typu a musí dodržovat pravidla COM. Doporučujeme, abyste použili `WRL::ComPtr` ke zjednodušení správy životního cyklu ABI ukazatelů.

Následující tabulka shrnuje případy, ve kterých je bezpečné používat **reinterpret_cast**. V každém případě přetypování je bezpečné v obou směrech.

|||
|-|-|
|`HSTRING`|`String^`|
|`HSTRING*`|`String^*`|
|`IInspectable*`|`Object^`|
|`IInspectable**`|`Object^*`|
|`IInspectable-derived-type*`|`same-interface-from-winmd^`|
|`IInspectable-derived-type**`|`same-interface-from-winmd^*`|
|`IDefault-interface-of-RuntimeClass*`|`same-RefClass-from-winmd^`|
|`IDefault-interface-of-RuntimeClass**`|`same-RefClass-from-winmd^*`|

## <a name="see-also"></a>Viz také:

- [Systém typů](../cppcx/type-system-c-cx.md)
- [Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)
- [Odkaz na obory názvů](../cppcx/namespaces-reference-c-cx.md)
