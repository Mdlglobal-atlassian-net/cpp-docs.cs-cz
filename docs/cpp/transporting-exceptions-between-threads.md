---
title: Převod výjimek mezi vlákny | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- std::current_exception
- transporting exceptions between threads
- std::copy_exception
- exception_ptr
- std::exception_ptr
- std::rethrow_exception
- current_exception
- transport exceptions between threads
- copy_exception
- rethrow_exception
- move exceptions between threads
ms.assetid: 5c95d57b-acf5-491f-8122-57c5df0edd98
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c1066da6545a2e0689fbfed33be466e001142dc9
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704643"
---
# <a name="transporting-exceptions-between-threads"></a>Převod výjimek mezi vlákny

Visual C++ podporuje *převod výjimku* z jedno vlákno na jiný. Přenos výjimek umožňuje zachytit výjimku v jednom vlákně a následně nechat výjimku vypadat, jako by byla vyvolána v jiném vlákně. Například je možné tuto funkci použít pro napsání vícevláknové aplikace, kde primární vlákno zpracovává všechny výjimky vyvolané sekundárními vlákny. Přenos výjimek je užitečný především pro vývojáře, kteří vytvářejí paralelní programovací knihovny nebo systémy. Pokud chcete implementovat přenosovou výjimky, poskytuje Visual C++ [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) typu a [current_exception](../standard-library/exception-functions.md#current_exception), [rethrow_exception](../standard-library/exception-functions.md#rethrow_exception), a [make_ exception_ptr](../standard-library/exception-functions.md#make_exception_ptr) funkce.

## <a name="syntax"></a>Syntaxe

```cpp
namespace std
{
   typedef unspecified exception_ptr;
   exception_ptr current_exception();
   void rethrow_exception(exception_ptr p);
   template<class E>
       exception_ptr make_exception_ptr(E e) noexcept;
}
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Tento parametr*|Neurčené interní třída, která se používá k implementaci `exception_ptr` typu.|
|*p*|`exception_ptr` Objekt, který odkazuje na výjimku.|
|*E*|Třída, která představuje výjimku.|
|*e*|Instance parametru `E` třídy.|

## <a name="return-value"></a>Návratová hodnota

`current_exception` Funkce vrátí `exception_ptr` objekt, který odkazuje na výjimku, která právě probíhá. Pokud žádná výjimka je v průběhu, funkce vrátí hodnotu `exception_ptr` objekt, který není spojen s všechny výjimky.

`make_exception_ptr` Funkce vrátí `exception_ptr` objekt, který odkazuje na výjimku určeného *e* parametr.

## <a name="remarks"></a>Poznámky

### <a name="scenario"></a>Scénář

Představte si, že je třeba vytvořit aplikaci, která může škálovat pro zpracování různého množství práce. K dosažení tohoto cíle je možné navrhnout vícevláknovou aplikaci, kde původní primární vlákno vytvoří tolik sekundárních vláken, kolik jich je pro práci potřebných. Sekundární vlákna pomohou primárnímu vláknu spravovat prostředky, vyvažovat zatížení a zvýšit propustnost. Díky distribuci práce poskytuje vícevláknová aplikace lepší výkon než jednovláknová aplikace.

Avšak pokud sekundární vlákno vyvolá výjimku, mělo by ji primární vlákno zpracovat. To proto, aby aplikace zpracovávala výjimky konzistentním způsobem bez ohledu na počet sekundárních vláken.

### <a name="solution"></a>Řešení

Pro zvládnutí předchozího scénáře podporuje standard jazyka C++ přenos výjimek mezi vlákny. Pokud jiného vlákna, vyvolá výjimku, stane se této výjimky *aktuální výjimku*. Obdobně pro praxi, aktuální výjimky se říká, že *na cestě*. Aktuální výjimka je v letu od okamžiku jejího vyvolání po návrat obslužné rutiny výjimky, která ji zachytila.

Sekundární vlákno může zachytit aktuální výjimky v `catch` blokovat a pak zavolají `current_exception` funkce k uložení výjimka v `exception_ptr` objektu. `exception_ptr` Objekt musí být k dispozici sekundární vlákno a na primární vlákno. Například `exception_ptr` objekt může být globální proměnné, jejichž přístup řídí mutex. Termín *přenosu výjimku* znamená výjimka v jedno vlákno lze převést na formulář, který je přístupný pomocí jiné vlákno.

V dalším kroku primární vlákno volá `rethrow_exception` funkci, která extrahuje a potom vyvolá výjimku z `exception_ptr` objektu. Jakmile je výjimka vyvolána, stane se v primárním vlákně aktuální výjimkou. A tak se zdá, že výjimka pochází z primárního vlákna.

Nakonec můžete primární vlákno catch aktuální výjimky v `catch` blokovat a pak ji zpracovat nebo throw na obslužnou rutinu vyšší úrovně výjimka. Nebo může primární vlákno výjimku ignorovat a dovolit procesu skončit.

Většina aplikací nepotřebuje přenášet výjimky mezi vlákny. Nicméně tato funkce je užitečná v paralelních výpočetních systémech, protože systém může rozdělit práci mezi sekundární vlákna, procesory nebo jádra. V prostředí paralelních výpočtů může jedno vyhrazené vlákno zpracovávat všechny výjimky ze sekundárních vláken a poskytnout konzistentní model zpracování výjimek pro jakoukoli aplikaci.

Pro další informace o návrhu komise standardu jazyka C++ vyhledejte na internetu dokument s číslem N2179 a názvem „Language Support for Transporting Exceptions between Threads“.

### <a name="exception-handling-models-and-compiler-options"></a>Modely zpracování výjimek a možnosti kompilátoru

Model zpracování výjimek v aplikaci určuje, zda lze zachytit a přenést výjimku. Jazyk Visual C++ podporuje tři modely, kterými lze zpracovávat výjimky jazyka C++, výjimky strukturovaného zpracování výjimek (SEH) a výjimky modulu CLR. Použití [/EH](../build/reference/eh-exception-handling-model.md) a [/CLR](../build/reference/clr-common-language-runtime-compilation.md) – možnosti kompilátoru k určení model zpracování výjimek vaší aplikace.

Pouze následující kombinace možností kompilátoru a programovacích příkazů může přenést výjimku. Další kombinace buď nemohou zachytit výjimky, nebo je mohou zachytit, ale nemohou přenést.

- **/EHa** – možnost kompilátoru a `catch` příkaz můžete přenosu SEH a C++ výjimky.

- **/EHa**, **/EHs**, a **/EHsc** – možnosti kompilátoru a `catch` příkaz můžete přenosu výjimky jazyka C++.

- **/CLR** – možnost kompilátoru a `catch` příkaz můžete přenosu výjimky jazyka C++. **/CLR** – možnost kompilátoru znamená specifikaci **/EHa** možnost. Je dobré si zapamatovat, že kompilátor nepodporuje přenos spravovaných výjimek. Důvodem je, že se spravovanými výjimkami, které jsou odvozeny od [System.Exception třída](../standard-library/exception-class.md), už jsou objekty, které můžete přesunout mezi vlákny pomocí zařízení společného languange modulu runtime.

   > [!IMPORTANT]
   > Doporučujeme vám, zda jste zadali **/EHsc** – možnost kompilátoru a catch pouze výjimky jazyka C++. Vystavit sami ohrožení zabezpečení Pokud použijete **/EHa** nebo **/CLR** – možnost kompilátoru a **catch** příkaz se třemi tečkami  *Výjimka – deklarace* (`catch(...)`). Chcete pravděpodobně používat `catch` příkaz zaznamenat několik specifických výjimek. Ale `catch(...)` příkaz zaznamená všechny C++ a SEH výjimky, včetně neočekávané ty, které by měly být závažná. Ignorováním nebo nesprávným zpracováním neočekávané výjimky může být dán prostor škodlivému kódu k ohrožení zabezpečení aplikace.

## <a name="usage"></a>Použití

Následující části popisují postup přenosu výjimky pomocí `exception_ptr` typ a `current_exception`, `rethrow_exception`, a `make_exception_ptr` funkce.

## <a name="exceptionptr-type"></a>Typ exception_ptr

Použijte `exception_ptr` objekt, který má odkazovat na aktuální výjimky nebo instanci výjimka zadaného uživatelem. V implementaci společnosti Microsoft, je reprezentována výjimku [EXCEPTION_RECORD](https://msdn.microsoft.com/library/windows/desktop/aa363082) struktury. Každý `exception_ptr` objekt zahrnuje pole odkazu výjimka, která odkazuje na kopii `EXCEPTION_RECORD` struktura, která představuje výjimku.

Když je deklarovat `exception_ptr` proměnné, proměnné není přidružen k žádné výjimky. Tedy referenční pole výjimky je NULL. Takové `exception_ptr` objektu se říká *null exception_ptr*.

Použití `current_exception` nebo `make_exception_ptr` funkce přiřadit výjimku `exception_ptr` objektu. Přiřadíte-li výjimku `exception_ptr` proměnné, pole výjimka odkazu proměnnou odkazuje na kopii této výjimky. Pokud není k dispozici dostatek paměti pro kopírování výjimku, pole výjimka odkazu odkazuje na kopii [std::bad_alloc](../standard-library/bad-alloc-class.md) výjimka. Pokud `current_exception` nebo `make_exception_ptr` funkce nelze zkopírovat výjimku z jiného důvodu, volání funkce [ukončit](../c-runtime-library/reference/terminate-crt.md) funkce ukončíte aktuálním procesu.

Bez ohledu na jeho název `exception_ptr` objektu není sám sebe. je zde ukazatel. Ho neřídí sémantika ukazatele a nelze jej použít s přístup ke členu ukazatele (`->`) nebo indirection (`*`) operátory. `exception_ptr` Objekt nemá žádné členy veřejná data nebo členské funkce.

### <a name="comparisons"></a>Porovnání

Můžete rovno (`==`) a není rovno (`!=`) operátory k porovnání dvou `exception_ptr` objekty. Operátory porovnání není binární hodnotu (bitový) `EXCEPTION_RECORD` struktury, které představují výjimky. Místo toho operátory porovnání adresy v poli výjimka odkazu `exception_ptr` objekty. V důsledku toho s hodnotou null `exception_ptr` a porovnání jako rovnocenné hodnotu NULL.

## <a name="currentexception-function"></a>Funkce current_exception

Volání `current_exception` v fungovat `catch` bloku. Pokud je k výjimce v cestě a `catch` výjimku, můžete zachytit bloku `current_exception` funkce vrátí `exception_ptr` objekt, který odkazuje na výjimku. Funkce, jinak vrátí hodnotu null `exception_ptr` objektu.

### <a name="details"></a>Podrobnosti

`current_exception` Funkce zaznamená výjimka, která je na cestě bez ohledu na to, jestli `catch` Určuje příkaz [výjimka deklarace](../cpp/try-throw-and-catch-statements-cpp.md) příkaz.

Na konci se nazývá destruktor pro aktuální výjimky `catch` blokování, pokud není opětovné výjimku. Ale i v případě, že zavoláte `current_exception` fungovat v destruktoru, funkce vrátí hodnotu `exception_ptr` objekt, který odkazuje na aktuální výjimku.

Následná volání `current_exception` funkce vrátí `exception_ptr` objekty, které odkazují na různé kopie aktuální výjimku. V důsledku toho se objekty při porovnání jeví jako nerovné, protože odkazují na jiné kopie, i přesto, že kopie mají stejné binární hodnoty.

### <a name="seh-exceptions"></a>Výjimky SEH

Pokud použijete **/EHa** – možnost kompilátoru, můžete zachytit výjimku SEH v jazyka C++ `catch` bloku. `current_exception` Funkce vrátí `exception_ptr` objekt, který odkazuje na SEH výjimku. A `rethrow_exception` funkce vyvolá výjimku SEH při volání s thetransported `exception_ptr` objektu jako její argument.

`current_exception` Funkce vrátí hodnotu null `exception_ptr` při volání v SEH `__finally` obslužné rutiny ukončení, `__except` obslužná rutina výjimky, nebo `__except` výrazu filtru.

Přenesená výjimka nepodporuje vnořené výjimky. Vnořená výjimka nastane, pokud je při zpracování výjimky vyvolána jiná výjimka. Pokud zachytit vnořené výjimky, `EXCEPTION_RECORD.ExceptionRecord` – datový člen odkazuje na řetězec `EXCEPTION_RECORD` struktury, které popisují přidružené výjimky. `current_exception` Funkce nepodporuje vnořené výjimky, protože vrátí `exception_ptr` objekt, jehož `ExceptionRecord` – datový člen je dojde k vynulování.

Pokud jste zachycení výjimek SEH, musí spravovat odkazuje žádné ukazatel v paměti `EXCEPTION_RECORD.ExceptionInformation` data člena pole. Musí zaručit, že paměť je platný po dobu životnosti odpovídající `exception_ptr` objekt, a že je paměť uvolněna při `exception_ptr` je odstraněn objekt.

Spolu s možností přenosu výjimek je možné použít funkce překladatele strukturovaných výjimek (SE). Pokud je výjimku SEH převedeny na výjimky C++, `current_exception` funkce vrátí `exception_ptr` přeložený výjimka místo původní výjimka SEH, který odkazuje. `rethrow_exception` Funkce následně vyvolá přeložený výjimka, není původní výjimka. Další informace o funkcích jihovýchodní překladač najdete v tématu [_set_se_translator –](../c-runtime-library/reference/set-se-translator.md).

## <a name="rethrowexception-function"></a>Funkce rethrow_exception

Po uložení zachycená výjimka v `exception_ptr` objektu primární vlákno může zpracovat objekt. Ve vaší primární vláknu volání `rethrow_exception` fungovat společně s `exception_ptr` objektu jako její argument. `rethrow_exception` Extrahuje výjimky z funkce `exception_ptr` objekt a potom v kontextu primární vlákno vyvolá výjimku. Pokud `p` parametr `rethrow_exception` s hodnotou null je funkce `exception_ptr`, funkce vyvolá [std::bad_exception](../standard-library/bad-exception-class.md).

Extrahovaná výjimka je nyní aktuální výjimkou v primárním vlákně a je možné ji zpracovávat stejně jako jakoukoli jinou výjimku. Pokud jste zachycení výjimky, můžete ji okamžitě zpracovávat nebo použít `throw` příkaz pro odesílání pro obslužnou rutinu vyšší úrovně výjimka. Jinak není třeba dělat nic a je možné nechat výchozí obslužnou rutinu systému ukončit proces.

## <a name="makeexceptionptr-function"></a>Funkce make_exception_ptr

`make_exception_ptr` Funkce použije instance třídy jako její argument a potom se vrátí `exception_ptr` instance, který odkazuje. Obvykle, zadejte [třídy výjimek](../standard-library/exception-class.md) jako argument pro objekt `make_exception_ptr` fungovat, i když všechny třídy objektu může být argument.

Volání `make_exception_ptr` funkce je ekvivalentní volání vyvolání k výjimce C++ v zachytávání `catch` blok a pak volání `current_exception` funkci vrátíte `exception_ptr` objekt, který odkazuje na výjimku. Implementace společnosti Microsoft `make_exception_ptr` funkce je efektivnější než vyvolání a potom zachytávání výjimku.

Aplikace obvykle nevyžaduje, aby `make_exception_ptr` funkce a budeme bránit jeho použití.

## <a name="example"></a>Příklad

V následujícím příkladu je standardní výjimka jazyka C++ a vlastní výjimka jazyka C++ přenesena z jednoho vlákna do druhého.

```cpp
// transport_exception.cpp
// compile with: /EHsc /MD
#include <windows.h>
#include <stdio.h>
#include <exception>
#include <stdexcept>

using namespace std;

// Define thread-specific information.
#define THREADCOUNT 2
exception_ptr aException[THREADCOUNT];
int           aArg[THREADCOUNT];

DWORD WINAPI ThrowExceptions( LPVOID );

// Specify a user-defined, custom exception.
// As a best practice, derive your exception
// directly or indirectly from std::exception.
class myException : public std::exception {
};
int main()
{
    HANDLE aThread[THREADCOUNT];
    DWORD ThreadID;

    // Create secondary threads.
    for( int i=0; i < THREADCOUNT; i++ )
    {
        aArg[i] = i;
        aThread[i] = CreateThread(
            NULL,       // Default security attributes.
            0,          // Default stack size.
            (LPTHREAD_START_ROUTINE) ThrowExceptions,
            (LPVOID) &aArg[i], // Thread function argument.
            0,          // Default creation flags.
            &ThreadID); // Receives thread identifier.
        if( aThread[i] == NULL )
        {
            printf("CreateThread error: %d\n", GetLastError());
            return -1;
        }
    }

    // Wait for all threads to terminate.
    WaitForMultipleObjects(THREADCOUNT, aThread, TRUE, INFINITE);
    // Close thread handles.
    for( int i=0; i < THREADCOUNT; i++ ) {
        CloseHandle(aThread[i]);
    }

    // Rethrow and catch the transported exceptions.
    for ( int i = 0; i < THREADCOUNT; i++ ) {
        try {
            if (aException[i] == NULL) {
                printf("exception_ptr %d: No exception was transported.\n", i);
            }
            else {
                rethrow_exception( aException[i] );
            }
        }
        catch( const invalid_argument & ) {
            printf("exception_ptr %d: Caught an invalid_argument exception.\n", i);
        }
        catch( const myException & ) {
            printf("exception_ptr %d: Caught a  myException exception.\n", i);
        }
    }
}
// Each thread throws an exception depending on its thread
// function argument, and then ends.
DWORD WINAPI ThrowExceptions( LPVOID lpParam )
{
    int x = *((int*)lpParam);
    if (x == 0) {
        try {
            // Standard C++ exception.
            // This example explicitly throws invalid_argument exception.
            // In practice, your application performs an operation that
            // implicitly throws an exception.
            throw invalid_argument("A C++ exception.");
        }
        catch ( const invalid_argument & ) {
            aException[x] = current_exception();
        }
    }
    else {
        // User-defined exception.
        aException[x] = make_exception_ptr( myException() );
    }
    return TRUE;
}
```

```Output
exception_ptr 0: Caught an invalid_argument exception.
exception_ptr 1: Caught a  myException exception.
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<výjimka >

## <a name="see-also"></a>Viz také:

- [Zpracování výjimek](../cpp/exception-handling-in-visual-cpp.md)
- [/EH (model ošetření výjimek)](../build/reference/eh-exception-handling-model.md)
- [/clr (kompilace modulu Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md)
