---
title: Výjimky (C++/CX)
ms.date: 07/02/2019
ms.assetid: 6cbdc1f1-e4d7-4707-a670-86365146432f
ms.openlocfilehash: 93a3c096c79140787a46dcbd0ae6ec7edc0bf2e4
ms.sourcegitcommit: 9b904e490b1e262293a602bd1291a8f3045e755b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2019
ms.locfileid: "67552183"
---
# <a name="exceptions-ccx"></a>Výjimky (C++/CX)

Zpracování chyb v C++/CX založené na výjimkách. Na nejzákladnější úrovni součástí prostředí Windows Runtime umožňuje nahlásit chyby jako hodnoty HRESULT. V C++/CX, tyto hodnoty se převedou na silného typu výjimky, které obsahují hodnotu HRESULT a popis řetězec, který můžete přistupovat prostřednictvím kódu programu.  Výjimky jsou implementovány jako `ref class` , která je odvozena z `Platform::Exception`.  `Platform` Obor názvů definuje různé výjimky třídy pro nejběžnější hodnoty HRESULT; všechny ostatní hodnoty jsou hlášeny prostřednictvím `Platform::COMException` třídy. Všechny výjimky třídy mají [Exception::HResult](platform-exception-class.md#hresult) pole, které můžete použít k načtení původní hodnota HRESULT. Můžete také zkontrolovat informace o zásobníku volání pro uživatelský kód v ladicím programu, které mohou pomoci přesně určit původní příčiny výjimek, i v případě, vytvoří se v kódu napsaného v jiném jazyce než v C++.

## <a name="exceptions"></a>Výjimky

Ve svém programu C++ lze vyvolat a zachytit výjimku, která pochází z operaci Windows Runtime, výjimka, která je odvozena od `std::exception`, nebo typ definovaný uživatelem. Je nutné vyvolat výjimku při běhu Windows pouze v případě, že ho překročí aplikace binární rozhraní (ABI) hranici, například když kód, který zachytává výjimky je napsaná v JavaScriptu. Když bez – Windows modul Runtime C++ výjimka dosáhne hranici ABI, výjimka je přeložit na `Platform::FailureException` výjimku, která představuje E_FAIL HRESULT. Další informace o ABI, naleznete v tématu [vytváření komponent Windows Runtime v jazyce C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

Je možné deklarovat [Platform::Exception](platform-exception-class.md) pomocí jedné z dva konstruktory, které přijímají parametr HRESULT nebo pomocí parametru HRESULT a [Platform::String](platform-string-class.md)^ parametr, který může být předán přes ABI do všech prostředí Windows Runtime aplikací, která ji zpracovává. Nebo výjimku lze deklarovat s použitím jednoho ze dvou [Exception::CreateException metoda](platform-exception-class.md#createexception) přetížení, která přijímají parametr HRESULT nebo pomocí parametru HRESULT a `Platform::String^` parametru.

## <a name="standard-exceptions"></a>Standardních výjimek

C++/CX podporuje sadu standardních výjimek, které představují typické chyby HRESULT. Každý standardní výjimka je odvozena z [Platform::COMException –](platform-comexception-class.md), která je dále odvozeno z `Platform::Exception`. Při vyvolání výjimky, hranice ABI, musíte vyvolat jednu ze standardních výjimek.

Nelze odvodit typ vlastní výjimky z `Platform::Exception`. Pokud chcete vyvolat vlastní výjimku, použijte hodnotu HRESULT uživatelem definované k vytvoření `COMException` objektu.

V následující tabulce jsou uvedeny standardních výjimek.

|Name|Základní hodnota HRESULT|Popis|
|----------|------------------------|-----------------|
|COMException|*uživatelem definované hresult*|Vyvolána, když je nerozpoznaný HRESULT vrácená z volání metody COM.|
|AccessDeniedException|ELEKTRONICKÉ\_ACCESSDENIED|Vyvolána, když byl odepřen přístup k prostředku nebo funkce.|
|ChangedStateException|ELEKTRONICKÉ\_ZMĚNĚNÉ\_STAVU|Vyvolána výjimka při volání metody iterátoru shromažďování nebo zobrazení kolekce po změně nadřazené kolekce, a proto už není platná výsledky metody.|
|ClassNotRegisteredException|REGDB\_E\_CLASSNOTREG|Vyvolána, když třída modelu COM není zaregistrovaný.|
|DisconnectedException|RPC\_E\_ODPOJENO|Vyvolána, když je objekt odpojen od svých klientů.|
|FailureException|ELEKTRONICKÉ\_SELHÁNÍ|Vyvolána, pokud se operace nezdaří.|
|InvalidArgumentException|ELEKTRONICKÉ\_INVALIDARG|Vyvolána, když jeden z argumentů, které jsou k dispozici k metodě není platný.|
|InvalidCastException|ELEKTRONICKÉ\_NOINTERFACE|Vyvolána, když typ nelze převést na jiného typu.|
|NotImplementedException|ELEKTRONICKÉ\_NOTIMPL|Vyvolána, pokud se neimplementoval metodu rozhraní na třídě.|
|NullReferenceException|ELEKTRONICKÉ\_UKAZATELE|Vyvolána výjimka při pokusu o zrušení odkazovat odkaz na objekt s hodnotou null.|
|ObjectDisposedException|RO\_E\_UZAVŘENO|Vyvolána výjimka při provádění operace na smazaném objektu.|
|OperationCanceledException|ELEKTRONICKÉ\_PŘERUŠENÍ|Vyvolána, pokud je operace přerušena.|
|OutOfBoundsException|ELEKTRONICKÉ\_HRANICE|Vyvolána, když se pokusí získat přístup k datům mimo platný rozsah operace.|
|OutOfMemoryException|ELEKTRONICKÉ\_OUTOFMEMORY|Vyvolána, když není dostatek paměti k dokončení operace.|
|WrongThreadException|RPC\_E\_NESPRÁVNÉ\_VLÁKNA|Vyvolána, když vlákno volá prostřednictvím ukazatele rozhraní, které je objekt proxy serveru, který nepatří do objektu apartment vlákna.|

## <a name="hresult-and-message-properties"></a>Vlastnosti HResult a zprávu

Mají všechny výjimky [HResult](platform-comexception-class.md#hresult) vlastnost a [zpráva](platform-comexception-class.md#message) vlastnost. [Exception::HResult](platform-exception-class.md#hresult) vlastnost získá výjimky základní číselná hodnota HRESULT. [Exception::Message](platform-exception-class.md#message) vlastnost získá řetězec poskytnuté systémem, který popisuje výjimku. Zpráva v systému Windows 8, je k dispozici pouze v ladicím programu a je jen pro čtení. To znamená, že ho nelze změnit po znovu vyvolejte výjimku. Ve Windows 8.1 můžete používat řetězec zprávy prostřednictvím kódu programu a zadejte novou zprávu, pokud je výjimka znovu vyvolána. Lepší informace o zásobníku volání je také k dispozici v ladicím programu, včetně zásobníky volání pro volání asynchronní metody.

### <a name="examples"></a>Příklady

Tento příklad ukazuje, jak vyvolat výjimku modulu Windows Runtime pro synchronní operace:

[!code-cpp[cx_exceptions#01](codesnippet/CPP/exceptiontest/class1.cpp#01)]

Následující příklad ukazuje, jak zachytit výjimku.

[!code-cpp[cx_exceptions#02](codesnippet/CPP/exceptiontest/class1.cpp#02)]

Zachytit výjimky, které jsou vyvolány během asynchronní operace, použijte třídu úloh a přidejte pokračování pro zpracování chyb. Zpracování chyb pokračování zařazuje výjimky, které jsou vyvolány v jiných vláknech zpět do volajícího vlákna tak, aby bylo možné zpracovat všechny potenciální výjimky v jednom místě v kódu. Další informace najdete v tématu [asynchronní programování v jazyce C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps).

## <a name="unhandlederrordetected-event"></a>UnhandledErrorDetected události

Ve Windows 8.1 můžete odebírat [Windows::ApplicationModel::Core::CoreApplication::UnhandledErrorDetected](/uwp/api/windows.applicationmodel.core.icoreapplicationunhandlederror.unhandlederrordetected) statické událost, která poskytuje přístup k neošetřené chyby, které se chystáte snížilo procesu. Bez ohledu na to, odkud pochází chybu, dosáhne této obslužné rutiny jako [Windows::ApplicationModel::Core::UnhandledError](/uwp/api/windows.applicationmodel.core.unhandlederror) objekt, který se předává pomocí argumenty události. Při volání `Propagate` objektu, vytváří a vyvolává `Platform::*Exception` typu, který odpovídá kódu chyby. V blocích catch, můžete uložit stav uživatele v případě potřeby a pak buď umožnit, voláním ukončení procesu `throw`, nebo udělat něco, co je program vrátit do známého stavu. Následující příklad zobrazuje základní vzor:

V app.xaml.h:

```cpp
void OnUnhandledException(Platform::Object^ sender, Windows::ApplicationModel::Core::UnhandledErrorDetectedEventArgs^ e);
```

In app.xaml.cpp:

```cpp
// Subscribe to the event, for example in the app class constructor:
Windows::ApplicationModel::Core::CoreApplication::UnhandledErrorDetected += ref new EventHandler<UnhandledErrorDetectedEventArgs^>(this, &App::OnUnhandledException);

// Event handler implementation:
void App::OnUnhandledException(Platform::Object^ sender, Windows::ApplicationModel::Core::UnhandledErrorDetectedEventArgs^ e)
{
    auto err = e->UnhandledError;

    if (!err->Handled) //Propagate has not been called on it yet.
{
    try
    {
        err->Propagate();
    }
    // Catch any specific exception types if you know how to handle them
    catch (AccessDeniedException^ ex)
    {
        // TODO: Log error and either take action to recover
        // or else re-throw exception to continue fail-fast
    }
}
```

### <a name="remarks"></a>Poznámky

C++/CX nepoužívá `finally` klauzuli.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka Visual C++](visual-c-language-reference-c-cx.md)<br/>
[Referenční informace o oborech názvů](namespaces-reference-c-cx.md)
