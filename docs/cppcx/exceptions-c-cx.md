---
title: "Výjimky (C + +/ CX) | Microsoft Docs"
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6cbdc1f1-e4d7-4707-a670-86365146432f
caps.latest.revision: "22"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f578271823b0253dfa3defcb126bec251749a2dc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="exceptions-ccx"></a>Výjimky (C + +/ CX)

Zpracování chyb v jazyce C + +/ CX podle výjimky. Na nejzákladnější úrovni prostředí Windows Runtime součástí zprávy o chybách jako HRESULT hodnoty. V jazyce C + +/ CX, tyto hodnoty se převedou na silného typu výjimky, které obsahují hodnotu HRESULT a popis řetězec, který je k dispozici prostřednictvím kódu programu.  Výjimky jsou implementované jako `ref class` která je odvozena od `Platform::Exception`.  `Platform` Obor názvů definuje třídy odlišné výjimek pro nejběžnější hodnoty HRESULT; všechny ostatní hodnoty jsou nahlášené prostřednictvím programu `Platform::COMException` třídy. Všechny třídy výjimky mají [Exception::HResult](platform-exception-class.md#hresult) pole, které můžete použít k načtení původní HRESULT. Můžete také zkontrolovat informace o zásobník volání pro uživatelský kód v ladicím programu, které mohou pomoci přesně určit původního zdroje výjimky, i když je vytvořena v kódu, která byla zapsána v jiném jazyce než C++.  
  
## <a name="exceptions"></a>Výjimky  
 V programu C++, throw a catch výjimka, která pochází z prostředí Windows Runtime operace, výjimku, která je odvozena z `std::exception`, nebo typ definovaný uživatelem. Budete muset výjimku prostředí Windows Runtime vyvolat jenom v případě, že se překročí aplikace binární rozhraní (ABI) hranici, například když dojde k zapsání kód, který zachytí vaší výjimek v jazyce JavaScript. Když Windows Runtime C++ výjimka dosáhne ABI hranice, výjimka je přeložit na `Platform::FailureException` výjimka, která představuje E_FAIL HRESULT. Další informace o ABI najdete v tématu [vytváření součásti systému Windows Runtime v jazyce C++](/MicrosoftDocs/windows-uwp/blob/docs/windows-apps-src/winrt-components/creating-windows-runtime-components-in-cpp.md).  
  
 Je možné deklarovat [Platform::Exception](platform-exception-class.md) pomocí jedné z dva konstruktory, které provést buď parametru HRESULT, nebo parametr HRESULT a [Platform::String](platform-string-class.md)^ parametr, který může být předán přes ABI do žádné aplikace Windows Store, která ji zpracovává. Nebo můžete pomocí jedné ze dvou deklarovat výjimku [Exception::CreateException metoda](platform-exception-class.md#createexception) přetížení, které provést buď parametru HRESULT, nebo parametr HRESULT a `Platform::String^` parametr.  
  
## <a name="standard-exceptions"></a>Standardní výjimky  
 C + +/ CX podporuje sadu standardní výjimky, které představují typické HRESULT chyby. Každé standardní výjimka je odvozena z [Platform::COMException](platform-comexception-class.md), která je zase odvozena z `Platform::Exception`. Při vyvolat výjimku přes hranice ABI, musí se vyvolat jednu standardní výjimek.  

 Nelze odvodit typ vlastní výjimky z `Platform::Exception`. Vyvolá vlastní výjimky, použít k vytvoření uživatelem definované HRESULT `COMException` objektu.  
  
 Následující tabulka uvádí standardní výjimky.  
  
|Název|Základní HRESULT|Popis|  
|----------|------------------------|-----------------|  
|COMException|*uživatelem definované hresult*|Vyvolá, když je nerozpoznané HRESULT vrácená z volání metody COM.|  
|AccessDeniedException|E_ACCESSDENIED|Vyvolá, když byl odepřen přístup k prostředku nebo funkce.|  
|ChangedStateException|E_CHANGED_STATE|Vyvolá, když jsou volány metody iterator kolekce nebo kolekce zobrazení po změně její nadřazená kolekce, a tím zneplatnění výsledky metody.|  
|ClassNotRegisteredException|REGDB_E_CLASSNOTREG|Vyvolá, když třídy COM není zaregistrován.|  
|DisconnectedException|RPC_E_DISCONNECTED|Vyvolá, když je objekt odpojen od jeho klienty.|  
|FailureException|E_FAIL|Vygeneruje se, když se operace nezdaří.|  
|InvalidArgumentException|E_INVALIDARG|Vyvolá, když jeden z argumentů, které jsou k dispozici na metodu je neplatný.|  
|InvalidCastException|E_NOINTERFACE|Vyvolá, když typ nelze převést na jiný typ.|  
|NotImplementedException –|E_NOTIMPL|Vygeneruje se, pokud není implementovaný pro třídu metodu rozhraní.|  
|NullReferenceException|E_POINTER|Vygeneruje se při pokusu o zrušte referenční odkaz objektu null.|  
|ObjectDisposedException|RO_E_CLOSED|Vygeneruje se při provádění operace v uvolněné objektu.|  
|OperationCanceledException|E_ABORT|Vyvolá, když operace byla přerušena.|  
|OutOfBoundsException|E_BOUNDS|Vygeneruje se, když se operace pokusí o přístup k datům mimo platný rozsah.|  
|OutOfMemoryException|E_OUTOFMEMORY|Vyvolá, když není dostatek paměti pro dokončení operace.|  
|WrongThreadException|RPC_E_WRONG_THREAD|Vyvolá, když vlákno volá prostřednictvím ukazatele rozhraní, což je pro objekt proxy serveru, který nepatří do objektu apartment vlákna.|  
  
## <a name="hresult-and-message-properties"></a>Vlastnosti HResult a zpráv  
 Mají všechny výjimky [HResult](platform-comexception-class.md#hresult) vlastnost a [zpráva](platform-comexception-class.md#message) vlastnost. [Exception::HResult](platform-exception-class.md#hresult) vlastnost získá v výjimky základní číselná hodnota HRESULT. [Exception::Message](platform-exception-class.md#message) vlastnost získá řetězec poskytnuté systémem, která popisuje výjimku. V systému Windows 8 zpráva je k dispozici pouze v ladicím programu a je jen pro čtení. To znamená, že ho nelze změnit při opětovné výjimku. Ve Windows 8.1 můžete přístup řetězec zprávy prostřednictvím kódu programu a zadejte novou zprávu, pokud opětovné výjimku. Lepší zásobník volání informace jsou také k dispozici v ladicím programu, včetně callstacks pro volání asynchronních metod.  
  
### <a name="examples"></a>Příklady  
 Tento příklad ukazuje, jak má být vyvolána výjimka prostředí Windows Runtime pro synchronní operace:  
  
 [!code-cpp[cx_exceptions#01](codesnippet/CPP/exceptiontest/class1.cpp#01)]  
  
 Další příklad ukazuje, jak k zachycení výjimky.  
  
 [!code-cpp[cx_exceptions#02](codesnippet/CPP/exceptiontest/class1.cpp#02)]  
  
 Zachytit výjimky, které jsou vyvolány během asynchronní operace, pomocí třídy úlohy a přidejte pokračování zpracování chyb. Zpracování chyb pokračování zařazuje výjimky, které jsou vyvolány na jiná vlákna zpět do volající vlákno tak, aby bylo možné zpracovat všechny potenciální výjimky v jednom místě v kódu. Další informace najdete v tématu [asynchronní programování v C++](http://msdn.microsoft.com/library/windows/apps/Hh780559.aspx).  
  
## <a name="unhandlederrordetected-event"></a>UnhandledErrorDetected událostí  
 Ve Windows 8.1 můžete odebírat [Windows::ApplicationModel::Core::CoreApplication::UnhandledErrorDetected](http://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.coreapplication.unhandlederrordetected.aspx) statické událost, která poskytuje přístup k neošetřené chyby, které se chystáte přineste ukončení procesu. Bez ohledu na to, kde chyba vytvořena, se dosáhne této obslužné rutiny jako [Windows::ApplicationModel::Core::UnhandledError](http://msdnstage.redmond.corp.microsoft.com/library/windows/apps/windows.applicationmodel.core.unhandlederror.aspx) objekt, který je předán pomocí argumentů události. Při volání `Propagate` na objekt, vytvoří a vyvolá `Platform::*Exception` typu, který odpovídá kódu chyby. V bloků catch můžete uložit stav uživatele v případě potřeby a pak buď umožnit ukončení voláním procesu `throw`, nebo dělat něco program nelze vrátit zpět do známého stavu. Následující příklad ukazuje základní vzor:  
  
```  
  
// In app.xaml.h:  
void OnUnhandledException(Platform::Object^ sender, Windows::ApplicationModel::Core::UnhandledErrorDetectedEventArgs^ e);  
  
// In app.xaml.cpp  
  
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
 C + +/ CX nepoužívá `finally` klauzule.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka Visual C++](visual-c-language-reference-c-cx.md)   
 [Odkaz na obory názvů](namespaces-reference-c-cx.md)