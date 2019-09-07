---
title: Výjimky (C++/CX)
ms.date: 07/02/2019
ms.assetid: 6cbdc1f1-e4d7-4707-a670-86365146432f
ms.openlocfilehash: ade406dc5db6022978f83715555c425caef4375b
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740179"
---
# <a name="exceptions-ccx"></a>Výjimky (C++/CX)

Zpracování chyb v C++systému/CX je založeno na výjimkách. Na nejzákladnější úrovni prostředí Windows Runtime komponenty hlásí chyby jako hodnoty HRESULT. V C++/CX jsou tyto hodnoty převedeny na výjimky silného typu, které obsahují hodnotu HRESULT a popis řetězce, ke kterému můžete přistupovat prostřednictvím kódu programu.  Výjimky jsou implementovány jako `ref class` odvozené z. `Platform::Exception`  Obor názvů definuje různé třídy výjimek pro nejběžnější hodnoty HRESULT. všechny ostatní hodnoty jsou hlášeny `Platform::COMException` prostřednictvím třídy. `Platform` Všechny třídy výjimek mají pole [Exception:: HRESULT](platform-exception-class.md#hresult) , které můžete použít k načtení původní hodnoty HRESULT. Můžete také prostudovat informace o zásobníku volání pro uživatelský kód v ladicím programu, který může usnadnit určení původního zdroje výjimky i v případě, že pochází v kódu, který byl napsán v jiném jazyce než C++.

## <a name="exceptions"></a>Výjimky

V C++ programu můžete vyvolat a zachytit výjimku, která přichází z operace prostředí Windows Runtime, výjimku odvozenou z `std::exception`nebo uživatelsky definovaného typu. Je nutné vyvolat výjimku prostředí Windows Runtime pouze v případě, že bude překročena hranice binárního rozhraní aplikace (ABI), například když kód, který zachytává výjimku, je napsán v jazyce JavaScript. Když výjimka bez prostředí Windows Runtime C++ dosáhne hranice ABI, je výjimka přeložena do `Platform::FailureException` výjimky, která představuje E_FAIL HRESULT. Další informace o ABI naleznete [v tématu Creating prostředí Windows Runtime Components in C++ ](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

Můžete deklarovat [platformu:: Exception](platform-exception-class.md) pomocí jednoho ze dvou konstruktorů, které přijímají buď parametr HRESULT, nebo parametr HRESULT a parametr [Platform:: String](platform-string-class.md)^, který lze předat přes ABI do jakékoli prostředí Windows Runtime aplikace, která ho zpracovává. Nebo můžete deklarovat výjimku pomocí jednoho ze dvou [metod:: CreateException Method](platform-exception-class.md#createexception) Overloads, které přebírají buď parametr HRESULT, nebo parametr HRESULT a `Platform::String^` parametr.

## <a name="standard-exceptions"></a>Standardní výjimky

C++/CX podporuje sadu standardních výjimek, které reprezentují typické chyby HRESULT. Každá standardní výjimka je odvozena z objektu [Platform:: COMException](platform-comexception-class.md), který je zase odvozen `Platform::Exception`z. Pokud vyvoláte výjimku v rámci hranice ABI, je nutné vyvolat jednu ze standardních výjimek.

Z `Platform::Exception`nelze odvodit vlastní typ výjimky. Chcete-li vyvolat vlastní výjimku, použijte uživatelem definovaný HRESULT k vytvoření `COMException` objektu.

V následující tabulce jsou uvedeny standardní výjimky.

|Name|Základní HRESULT|Popis|
|----------|------------------------|-----------------|
|COMException|*uživatelem definovaná hodnota HRESULT*|Vyvolána, pokud se vrátí nerozpoznaný HRESULT z volání metody modelu COM.|
|AccessDeniedException|E\_ACCESSDENIED|Vyvoláno, když je odepřen přístup k prostředku nebo funkci.|
|ChangedStateException|STAV\_E\_ZMĚNĚN|Vyvolána, když jsou volány metody iterátoru kolekce nebo zobrazení kolekce po změně nadřazené kolekce, čímž se neověřují výsledky metody.|
|ClassNotRegisteredException|REGDB\_E\_CLASSNOTREG|Vyvoláno, když nebyla zaregistrována třída COM.|
|DisconnectedException|RPC\_E\_ODPOJEN|Vyvoláno, když je objekt odpojen od klientů.|
|FailureException|CHYBA\_E|Vyvoláno, když dojde k chybě operace.|
|InvalidArgumentException|E\_INVALIDARG|Vyvolána, pokud jeden z argumentů, které jsou k metodě k dispozici, není platný.|
|InvalidCastException|E\_– ROZHRANÍ|Vyvoláno, když typ nelze přetypovat na jiný typ.|
|NotImplementedException|E\_NOTIMPL|Vyvoláno, pokud metoda rozhraní nebyla pro třídu implementována.|
|NullReferenceException|UKAZATEL\_E|Vyvolána, když dojde k pokusu o zrušení odkazu na odkaz na objekt s hodnotou null.|
|ObjectDisposedException|RO\_E\_UZAVŘENO|Vyvoláno, když je operace provedena u uvolněného objektu.|
|OperationCanceledException|E\_PŘERUŠENÍ|Vyvolána, když je operace přerušena.|
|OutOfBoundsException|E\_MEZE|Vyvolá se, když se operace pokusí o přístup k datům mimo platný rozsah.|
|OutOfMemoryException|E\_OUTOFMEMORY|Vyvoláno, pokud k dokončení operace není dostatek paměti.|
|WrongThreadException|RPC\_E\_CHYBNÉVLÁKNO\_|Vyvolána, když vlákno volá přes ukazatel rozhraní, který je pro objekt proxy, který nepatří do objektu apartment vlákna.|

## <a name="hresult-and-message-properties"></a>Vlastnosti HResult a Message

Všechny výjimky mají vlastnost [HRESULT](platform-comexception-class.md#hresult) a vlastnost [Message](platform-comexception-class.md#message) . Vlastnost [Exception:: HRESULT](platform-exception-class.md#hresult) načte základní číselnou hodnotu HRESULT výjimky. Vlastnost [Exception:: Message](platform-exception-class.md#message) Získá řetězec zadaný systémem, který popisuje výjimku. V systému Windows 8 je zpráva k dispozici pouze v ladicím programu a je určena jen pro čtení. To znamená, že nemůžete změnit, když výjimku znovu vyvoláte. V Windows 8.1 můžete k řetězci zprávy přistupovat programově a zadat novou zprávu, pokud výjimku znovu vyvoláte. Lepší informace zásobník volání jsou také k dispozici v ladicím programu, včetně zásobníky volání pro volání asynchronní metody.

### <a name="examples"></a>Příklady

Tento příklad ukazuje, jak vyvolat výjimku prostředí Windows Runtime pro synchronní operace:

[!code-cpp[cx_exceptions#01](codesnippet/CPP/exceptiontest/class1.cpp#01)]

Další příklad ukazuje, jak zachytit výjimku.

[!code-cpp[cx_exceptions#02](codesnippet/CPP/exceptiontest/class1.cpp#02)]

Chcete-li zachytit výjimky, které jsou vyvolány během asynchronní operace, použijte třídu Task a přidejte pokračování v manipulaci s chybami. Pokračování zpracování chyb zařadí výjimky, které jsou vyvolány v jiných vláknech zpět do volajícího vlákna, aby bylo možné zpracovat všechny potenciální výjimky pouze v jednom místě v kódu. Další informace naleznete v tématu [asynchronní programování v C++ ](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps).

## <a name="unhandlederrordetected-event"></a>Událost UnhandledErrorDetected

V Windows 8.1 se můžete přihlásit k odběru statické události [Windows:: ApplicationModel:: Core:: CoreApplication:: UnhandledErrorDetected](/uwp/api/windows.applicationmodel.core.icoreapplicationunhandlederror.unhandlederrordetected) , která poskytuje přístup k neošetřeným chybám, které se chystá tento proces vyvolat. Bez ohledu na to, kde chyba vznikla, dosáhne této obslužné rutiny jako objekt [Windows:: ApplicationModel:: Core:: UnhandledError](/uwp/api/windows.applicationmodel.core.unhandlederror) , který je předán pomocí argumentů události. Při volání `Propagate` na objekt vytvoří a `Platform::*Exception` vyvolá typ, který odpovídá kódu chyby. V blocích catch můžete v případě potřeby ušetřit stav uživatele a potom buď povolit ukončení procesu voláním `throw`, nebo udělat něco, abyste mohli program vrátit zpátky do známého stavu. Následující příklad ukazuje základní vzor:

V souboru App. XAML. h:

```cpp
void OnUnhandledException(Platform::Object^ sender, Windows::ApplicationModel::Core::UnhandledErrorDetectedEventArgs^ e);
```

V souboru App. XAML. cpp:

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

[Referenční zdroje k jazyku C++/CX](visual-c-language-reference-c-cx.md)<br/>
[Referenční informace o oborech názvů](namespaces-reference-c-cx.md)
