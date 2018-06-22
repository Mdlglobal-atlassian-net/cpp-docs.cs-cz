---
title: Přetypování (C + +/ CX) | Microsoft Docs
ms.custom: ''
ms.date: 06/19/2018
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 5247f6c7-6a0a-4021-97c9-21c868bd9455
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 66c0e6bc9d987c400c709e74586e6e37ccc0b715
ms.sourcegitcommit: 301bb19056e5bae84ff50f7d1df1e546efe225ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/21/2018
ms.locfileid: "36305992"
---
# <a name="casting-ccx"></a>Přetypování (C + +/ CX)

Použít čtyři operátory přetypování různé typy prostředí Windows Runtime: [static_cast – operátor](../cpp/static-cast-operator.md), [dynamic_cast – operátor](../cpp/dynamic-cast-operator.md), **safe_cast operátor**, a [ reinterpret_cast – operátor](../cpp/reinterpret-cast-operator.md). **safe_cast** a **static_cast** způsobí výjimku, pokud převod nelze provést; [static_cast – operátor](../cpp/static-cast-operator.md) také provádí kontrola typu v kompilaci. **dynamic_cast** vrátí **nullptr** Pokud se nepodaří typ převést. I když **reinterpret_cast** vrátí nenulovou hodnotu, může to být neplatný. Z tohoto důvodu doporučujeme nepoužívat **reinterpret_cast** Pokud si nejste jisti, že bude úspěšné přetypování. Kromě toho doporučujeme používat přetypování ve stylu jazyka C ve vašem C + +/ CX kódu, protože jsou identické **reinterpret_cast**.

Modul runtime a kompilátor také provést implicitní přetypování – například v zabalení operace, když typ hodnoty nebo předdefinovaný typ jsou předány jako argumenty pro metodu jejichž parametr typu je `Object^`. Teoreticky by nikdy implicitní přetypování způsobit výjimku při provádění. Pokud kompilátor nelze provést implicitní převod, vyvolá chybu při kompilaci.

Prostředí Windows Runtime je abstrakci přes modelu COM, která používá kódy chyb HRESULT místo výjimky. Obecně [Platform::InvalidCastException](../cppcx/platform-invalidcastexception-class.md) značí chybu nízké úrovně COM z E_NOINTERFACE.

## <a name="staticcast"></a>static_cast –

A **static_cast** je zaškrtnuté políčko, v době kompilace k určení, zda je mezi těmito dvěma typy vztah dědičnosti. Přetypování způsobí chybu kompilátoru, pokud nejsou související typy.

A **static_cast** v ref třída také způsobí, že kontrola běhu provést. A **static_cast** na ref třída projít ověřením doba kompilace ale stále selhat v době běhu; v tomto případě `Platform::InvalidCastException` je vyvolána výjimka. Obecně platí nemusíte tyto výjimky zpracovat, protože téměř vždy označují programovací chyby, které můžete eliminovat během vývoje a testování.

Použití **static_cast** Pokud kód deklaruje explicitně vztahu mezi těmito dvěma typy, a proto víte, že by měla fungovat přetypování.

```cpp
    interface class A{};
    public ref class Class1 sealed : A { };
    // ...
    A^ obj = ref new Class1(); // Class1 is an A
    // You know obj is a Class1. The compiler verifies that this is possible, and in C++/CX a run-time check is also performed.
    Class1^ c = static_cast<Class1^>(obj);
```

## <a name="safecast"></a>safe_cast

**Safe_cast** operátor je součástí prostředí Windows Runtime. Ji provede kontrolu typu běhu a vyvolá výjimku `Platform::InvalidCastException` Pokud převod selže. Použití **safe_cast** při selhání spuštění označuje podmínku výjimečně vysoké počty. Primárním účelem **safe_cast** je k identifikaci programovací chyby během vývoje a testování fáze v okamžiku, kdy k nim dojde. Nemáte účelem ošetření výjimky, protože neošetřenou výjimkou samotné identifikuje bod selhání.

Používání operátoru safe_cast, pokud kód nedeklaruje relace, ale jste si jisti, že by měla fungovat přetypování.

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

Použití **dynamic_cast** při přetypování objektu (přesněji řečeno, hat **^**) na více odvozený typ očekáváte, že buď, cílový objekt může být v některých případech **nullptr** nebo který přetypování může dojít k selhání, a vy chcete zpracovávat jako regulární kódové cestě místo výjimku této podmínky. Například v **prázdná aplikace (univerzální pro Windows)** šablony projektu, `OnLaunched` metoda v app.xamp.cpp používá **dynamic_cast** k ověření, zda má okna aplikace na obsah. Není chybu pokud nemá obsahu; je očekávané podmínku. `Windows::Current::Content` je `Windows::UI::XAML::UIElement` a převod `Windows::UI.XAML::Controls::Frame`, což je více odvozený typ v hierarchii dědičnosti.

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

Použití jiné **dynamic_cast** je testovat `Object^` k určení, zda obsahuje typ zabalené hodnoty. V takovém případě pokus `dynamic_cast<Platform::Box>` nebo `dynamic_cast<Platform::IBox>`.

## <a name="dynamiccast-and-tracking-references-"></a>dynamic_cast a sledování odkazů na (%)

Můžete taky použít **dynamic_cast** sledovací odkaz, ale v tomto případě přetypování chová jako **safe_cast**. Vyvolá `Platform::InvalidCastException` na selhání protože sledovací odkaz nemůže mít hodnotu **nullptr**.

## <a name="reinterpretcast"></a>reinterpret_cast

Doporučujeme nepoužívat [reinterpret_cast](../cpp/reinterpret-cast-operator.md) protože je prováděna kontrola kompilaci ani kontrolu běhu. V nejhorším případě **reinterpret_cast** umožňuje programování chyby pokračovat nezjištěné v době vývoje a způsobit jemně nebo závažné chyby v chování vašeho programu. Proto doporučujeme použít **reinterpret_cast** pouze v těchto výjimečných případech, kdy musíte vysílat mezi nesouvisejícími typy a víte, že bude úspěšné přetypování. Je například výjimečných použití prostředí Windows Runtime typ převést na jeho zdrojovým typem ABI – to znamená, že trvá ovládací prvek odkazu počítání pro objekt. Chcete-li to provést, doporučujeme použít [ComPtr – třída](../cpp/com-ptr-t-class.md) chytré ukazatele. Jinak musí konkrétně volat verze na rozhraní. Následující příklad ukazuje, jak lze převést třídu ref na `IInspectable*`.

```cpp
#include <wrl.h>
using namespace Microsoft::WRL;
auto winRtObject = ref new SomeWinRTType();
ComPtr<IInspectable> inspectable = reinterpret_cast<IInspectable*>(winRtObject);
// ...
```

Pokud používáte **reinterpret_cast** převést z modulu Runtime rozhraní oneWindows do druhého, způsobit objekt, který má být vydané dvakrát. Proto pouze použijte toto přetypování při převodu do jinou hodnotu než[!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] rozhraní.

## <a name="abi-types"></a>Typy ABI

- Typy ABI za provozu v hlavičkách ve Windows SDK. Pohodlně, jsou pojmenované hlavičky po obory názvů – například `windows.storage.h`.

- Typy ABI za provozu v speciální oboru názvů ABI – například `ABI::Windows::Storage::Streams::IBuffer*`.

- Převody mezi typem rozhraní prostředí Windows Runtime a jeho ekvivalentní ABI typu jsou bezpečné vždy – to znamená, `IBuffer^` k `ABI::IBuffer*`.

- Prostředí Windows Runtime runtime třídy mají být převedeny vždy na `IInspectable*` nebo jeho výchozí rozhraní, pokud je který znám.

- Po převodu na typy ABI vlastní doba života typu a musí se řídit pravidly COM. Doporučujeme vám, že používáte `WRL::ComPtr` zjednodušit správu životního cyklu ABI ukazatele.

Následující tabulka shrnuje v případech, ve kterých je bezpečně používat **reinterpret_cast**. V každém případě je bezpečné v obou směrech přetypování.

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
