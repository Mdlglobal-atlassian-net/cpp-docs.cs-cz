---
title: PřetypováníC++(/CX)
ms.date: 06/19/2018
ms.assetid: 5247f6c7-6a0a-4021-97c9-21c868bd9455
ms.openlocfilehash: 6711320fd9ca52360f702e029fdc8e129c90c6cd
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740543"
---
# <a name="casting-ccx"></a>PřetypováníC++(/CX)

Čtyři různé operátory přetypování se vztahují na prostředí Windows Runtime typy: [operátor static_cast](../cpp/static-cast-operator.md), [operátor dynamic_cast](../cpp/dynamic-cast-operator.md), **operátor safe_cast**a [operátor reinterpret_cast](../cpp/reinterpret-cast-operator.md). **safe_cast** a **static_cast** vyvolají výjimku, když převod nelze provést; [operátor static_cast](../cpp/static-cast-operator.md) také provádí kontrolu typu při kompilaci. **dynamic_cast** vrátí **nullptr** , pokud se nezdařilo převést typ. I když **reinterpret_cast** vrací hodnotu, která není null, může být neplatná. Z tohoto důvodu doporučujeme, abyste **přetypování reinterpret_cast** nepoužili, Pokud nevíte, že přetypování bude úspěšné. Kromě toho doporučujeme, abyste v kódu C++/CX nepoužívali přetypování ve stylu jazyka C, protože jsou stejné jako **reinterpret_cast**.

Kompilátor a modul runtime také provádějí implicitní přetypování – například v operacích zabalení, pokud je typ hodnoty nebo předdefinovaný typ předán jako argumenty metodě, jejíž typ parametru je `Object^`. Teoreticky by implicitní přetypování nikdy nezpůsobilo výjimku za běhu; Pokud kompilátor nemůže provést implicitní převod, vyvolá chybu v době kompilace.

Prostředí Windows Runtime je abstrakcí přes model COM, která místo výjimek používá kódy chyb HRESULT. Obecně platí, že [Platform:: InvalidCastException](../cppcx/platform-invalidcastexception-class.md) označuje chybu typu com nízké úrovně E_NOINTERFACE.

## <a name="static_cast"></a>static_cast

**Přetypování static_cast** je kontrolováno v době kompilace, aby bylo zjištěno, zda existuje vztah dědičnosti mezi dvěma typy. Přetypování způsobí chybu kompilátoru, pokud typy nesouvisejí.

**Přetypování static_cast** na referenční třídě také způsobí provedení kontrolního běhu. **Přetypování static_cast** u třídy ref class může předat ověření doby kompilace, ale v době běhu stále selže; v tomto případě `Platform::InvalidCastException` je vyvolána výjimka. Obecně není nutné tyto výjimky zpracovávat, protože téměř vždy označují programové chyby, které lze eliminovat při vývoji a testování.

Použijte **přetypování static_cast** , pokud kód explicitně deklaruje relaci mezi těmito dvěma typy a Vy tedy zajistěte, aby přetypování mělo fungovat.

```cpp
    interface class A{};
    public ref class Class1 sealed : A { };
    // ...
    A^ obj = ref new Class1(); // Class1 is an A
    // You know obj is a Class1. The compiler verifies that this is possible, and in C++/CX a run-time check is also performed.
    Class1^ c = static_cast<Class1^>(obj);
```

## <a name="safe_cast"></a>safe_cast

Operátor **safe_cast** je součástí prostředí Windows Runtime. Provede kontrolu typu za běhu a vyvolá výjimku `Platform::InvalidCastException` , pokud převod neproběhne úspěšně. Použijte **safe_cast** , pokud chyba za běhu indikuje mimořádnou podmínku. Hlavním účelem **safe_cast** je pomáhat identifikovat programové chyby během fází vývoje a testování v místě, kde se vyskytují. Nemusíte zpracovávat výjimku, protože Neošetřená výjimka identifikuje bod selhání.

Použijte safe_cast, pokud kód nedeklaruje vztah, ale jste si jisti, že přetypování by mělo fungovat.

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

## <a name="dynamic_cast"></a>dynamic_cast

Použijte **dynamic_cast** při přetypování objektu (konkrétně na Hat **^** ) na více odvozený typ, očekáváte, že cílový objekt může někdy být **nullptr** nebo že přetypování může selhat a chcete tuto podmínku zpracovat jako místo výjimky regulární cesta kódu. Například v šabloně `OnLaunched` projektu **prázdná aplikace (univerzální pro Windows)** metoda v App. XAMP. cpp používá **přetypování dynamic_cast** k otestování, zda má okno aplikace obsah. Nejedná se o chybu, pokud nemá obsah; je to očekávaná podmínka. `Windows::Current::Content`je a je převod na, což je více odvozený typ v hierarchii dědičnosti. `Windows::UI.XAML::Controls::Frame` `Windows::UI::XAML::UIElement`

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

Dalším použitím **dynamic_cast** je `Object^` zjistit, zda obsahuje zabalený typ hodnoty. V tomto případě se pokusíte `dynamic_cast<Platform::Box>` o `dynamic_cast<Platform::IBox>`nebo.

## <a name="dynamic_cast-and-tracking-references-"></a>odkazy dynamic_cast a sledování (%)

Můžete také použít **přetypování dynamic_cast** na sledovací odkaz, ale v tomto případě se přetypování chová jako **safe_cast**. Vyvolá `Platform::InvalidCastException` se při selhání, protože odkaz sledování nemůže mít hodnotu **nullptr**.

## <a name="reinterpret_cast"></a>reinterpret_cast

Doporučujeme nepoužívat [přetypování reinterpret_cast](../cpp/reinterpret-cast-operator.md) , protože není provedena žádná kontrolní doba kompilace ani kontrolní doba běhu. V nejhorším případě **přetypování reinterpret_cast** umožňuje programovacím chybám jít v době vývoje na nezjištěnou hodnotu a způsobit drobné nebo závažné chyby v chování programu. Proto doporučujeme použít **přetypování reinterpret_cast** pouze ve výjimečných případech, pokud je nutné přetypování mezi nesouvisejícími typy a víte, že přetypování bude úspěšné. Příkladem zřídka používaného použití je převést prostředí Windows Runtime typ na svůj základní typ ABI – to znamená, že přebíráte počítání odkazů pro objekt. K tomu doporučujeme použít inteligentní ukazatel [třídy ComPtr](../cpp/com-ptr-t-class.md) . V opačném případě je nutné volat vydání na rozhraní. Následující příklad ukazuje, jak třída ref class může být převedena na `IInspectable*`.

```cpp
#include <wrl.h>
using namespace Microsoft::WRL;
auto winRtObject = ref new SomeWinRTType();
ComPtr<IInspectable> inspectable = reinterpret_cast<IInspectable*>(winRtObject);
// ...
```

Použijete-li **přetypování reinterpret_cast** k převodu z rozhraní oneWindows runtime na jiný, způsobí to, že se objekt uvolní dvakrát. Proto použijte pouze toto přetypování při převodu na rozhraní rozšíření bezC++ součásti.

## <a name="abi-types"></a>Typy ABI

- Typy ABI jsou v Windows SDK živé v hlavičkách. V praktických případech jsou hlavičky pojmenovány po oborech názvů, `windows.storage.h`například.

- Typy ABI jsou `ABI::Windows::Storage::Streams::IBuffer*`živé ve speciálním oboru názvů ABI – například.

- Převody mezi prostředí Windows Runtime typu rozhraní a jeho ekvivalentním typem ABI jsou vždy bezpečná – tedy `IBuffer^` na. `ABI::IBuffer*`

- Třída prostředí Windows Runtime runtime by měla být vždy převedena `IInspectable*` na nebo její výchozí rozhraní, pokud je známo.

- Po převodu na typy ABI vlastníte dobu života typu a musí následovat pravidla modelu COM. Pro zjednodušení správy životnosti `WRL::ComPtr` ukazatelů ABI doporučujeme použít.

Následující tabulka shrnuje případy, ve kterých je bezpečné použít **přetypování reinterpret_cast**. V každém případě je přetypování v obou směrech bezpečné.

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
- [Referenční zdroje k jazyku C++/CX](../cppcx/visual-c-language-reference-c-cx.md)
- [Referenční informace o oborech názvů](../cppcx/namespaces-reference-c-cx.md)
