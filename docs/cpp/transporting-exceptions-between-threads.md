---
title: Převod výjimek mezi vlákny
ms.date: 11/04/2016
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
ms.openlocfilehash: f403b1448855b60f323ed582794a00c3e6ae1b3a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464440"
---
# <a name="transporting-exceptions-between-threads"></a>Převod výjimek mezi vlákny

Visual C++ podporuje *přenos výjimek* z jednoho vlákna do druhého. Přenos výjimek umožňuje zachytit výjimku v jednom vlákně a následně nechat výjimku vypadat, jako by byla vyvolána v jiném vlákně. Například je možné tuto funkci použít pro napsání vícevláknové aplikace, kde primární vlákno zpracovává všechny výjimky vyvolané sekundárními vlákny. Přenos výjimek je užitečný především pro vývojáře, kteří vytvářejí paralelní programovací knihovny nebo systémy. Pro implementaci přenosu výjimek poskytuje jazyk Visual C++ [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) typ a [current_exception](../standard-library/exception-functions.md#current_exception), [rethrow_exception](../standard-library/exception-functions.md#rethrow_exception), a [make_ exception_ptr](../standard-library/exception-functions.md#make_exception_ptr) funkce.

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
|*Tento parametr zadán*|Neurčená vnitřní třída, která se používá k implementaci `exception_ptr` typu.|
|*p*|`exception_ptr` Objekt, který odkazuje na výjimku.|
|*E*|Třída, která představuje výjimku.|
|*e*|Instance třídy parametru `E` třídy.|

## <a name="return-value"></a>Návratová hodnota

`current_exception` Vrací funkce `exception_ptr` objekt, který odkazuje na výjimku, která je aktuálně v průběhu. Pokud žádná výjimka neprobíhá, vrací funkce `exception_ptr` objekt, který není přidružen k žádné výjimce.

`make_exception_ptr` Vrací funkce `exception_ptr` , který odkazuje na výjimku zadanou parametrem *e* parametru.

## <a name="remarks"></a>Poznámky

### <a name="scenario"></a>Scénář

Představte si, že je třeba vytvořit aplikaci, která může škálovat pro zpracování různého množství práce. K dosažení tohoto cíle je možné navrhnout vícevláknovou aplikaci, kde původní primární vlákno vytvoří tolik sekundárních vláken, kolik jich je pro práci potřebných. Sekundární vlákna pomohou primárnímu vláknu spravovat prostředky, vyvažovat zatížení a zvýšit propustnost. Díky distribuci práce poskytuje vícevláknová aplikace lepší výkon než jednovláknová aplikace.

Avšak pokud sekundární vlákno vyvolá výjimku, mělo by ji primární vlákno zpracovat. To proto, aby aplikace zpracovávala výjimky konzistentním způsobem bez ohledu na počet sekundárních vláken.

### <a name="solution"></a>Řešení

Pro zvládnutí předchozího scénáře podporuje standard jazyka C++ přenos výjimek mezi vlákny. Pokud sekundární vlákno vyvolá výjimku, tato výjimka se stane *aktuální výjimku*. Podle analogie reálné je označen jako aktuální výjimka *za pochodu*. Aktuální výjimka je v letu od okamžiku jejího vyvolání po návrat obslužné rutiny výjimky, která ji zachytila.

Sekundární vlákno může zachytit aktuální výjimku v **catch** blokovat a poté zavolejte `current_exception` funkci pro uložení výjimky do `exception_ptr` objektu. `exception_ptr` Objekt musí být k dispozici jak sekundárnímu vláknu a tak primárnímu vláknu. Například `exception_ptr` objekt může být globální proměnnou, jejíž přístup je řízen mutexem. Termín *přenést výjimku* znamená, že výjimka z jednoho vlákna může být převeden na formulář, který je přístupný jinému vláknu.

Dále primární vlákno volá `rethrow_exception` funkce, která extrahuje a následně vyvolává výjimku z `exception_ptr` objektu. Jakmile je výjimka vyvolána, stane se v primárním vlákně aktuální výjimkou. A tak se zdá, že výjimka pochází z primárního vlákna.

Nakonec může primární vlákno zachytit aktuální výjimku v **catch** blokovat a pak ji zpracovat nebo ji vyvolat pro obslužnou rutinu vyšší úrovně. Nebo může primární vlákno výjimku ignorovat a dovolit procesu skončit.

Většina aplikací nepotřebuje přenášet výjimky mezi vlákny. Nicméně tato funkce je užitečná v paralelních výpočetních systémech, protože systém může rozdělit práci mezi sekundární vlákna, procesory nebo jádra. V prostředí paralelních výpočtů může jedno vyhrazené vlákno zpracovávat všechny výjimky ze sekundárních vláken a poskytnout konzistentní model zpracování výjimek pro jakoukoli aplikaci.

Pro další informace o návrhu komise standardu jazyka C++ vyhledejte na internetu dokument s číslem N2179 a názvem „Language Support for Transporting Exceptions between Threads“.

### <a name="exception-handling-models-and-compiler-options"></a>Modely zpracování výjimek a možnosti kompilátoru

Model zpracování výjimek v aplikaci určuje, zda lze zachytit a přenést výjimku. Jazyk Visual C++ podporuje tři modely, kterými lze zpracovávat výjimky jazyka C++, výjimky strukturovaného zpracování výjimek (SEH) a výjimky modulu CLR. Použití [/EH](../build/reference/eh-exception-handling-model.md) a [/CLR](../build/reference/clr-common-language-runtime-compilation.md) – možnosti kompilátoru pro určení modelu zpracování výjimek vaší aplikace.

Pouze následující kombinace možností kompilátoru a programovacích příkazů může přenést výjimku. Další kombinace buď nemohou zachytit výjimky, nebo je mohou zachytit, ale nemohou přenést.

- **/EHa** – možnost kompilátoru a **catch** příkaz mohou přenášet SEH a výjimky jazyka C++.

- **/EHa**, **/EHS**, a **/EHsc** – možnosti kompilátoru a **catch** příkaz mohou přenášet výjimky jazyka C++.

- **/CLR** – možnost kompilátoru a **catch** příkaz mohou přenášet výjimky jazyka C++. **/CLR** – možnost kompilátoru znamená specifikace **/EHa** možnost. Je dobré si zapamatovat, že kompilátor nepodporuje přenos spravovaných výjimek. Důvodem je, že spravované výjimky, které jsou odvozeny z [třídy System.Exception](../standard-library/exception-class.md), už jsou objekty, které lze přesunout mezi vlákny pomocí zařízení prostředků modulu CLR.

   > [!IMPORTANT]
   > Doporučujeme vám, že zadáte **/EHsc** – možnost kompilátoru a catch pouze výjimky jazyka C++. Zpřístupníte sami bezpečnostní hrozbu používáte **/EHa** nebo **/CLR** – možnost kompilátoru a **catch** příkazu se třemi tečkami  *deklarace výjimky* (`catch(...)`). By měl používat **catch** příkaz pro zachycení několika specifických výjimek. Ale `catch(...)` příkaz zachytí výjimky všechny C++ a SEH, včetně neočekávaných, které mohou být závažné. Ignorováním nebo nesprávným zpracováním neočekávané výjimky může být dán prostor škodlivému kódu k ohrožení zabezpečení aplikace.

## <a name="usage"></a>Použití

Následující části popisují způsob přenášení výjimky pomocí `exception_ptr` typ a `current_exception`, `rethrow_exception`, a `make_exception_ptr` funkce.

## <a name="exceptionptr-type"></a>Typ exception_ptr

Použití `exception_ptr` pro odkázání na aktuální výjimku nebo instanci uživatelské výjimky. V implementaci společnosti Microsoft, je reprezentována výjimku [EXCEPTION_RECORD](/windows/desktop/api/winnt/ns-winnt-_exception_record) struktury. Každý `exception_ptr` objekt obsahuje referenční pole výjimky, která odkazuje na kopii `EXCEPTION_RECORD` struktura, která představuje výjimku.

Pokud deklarujete `exception_ptr` proměnné, proměnná není přidružen k žádné výjimce. Tedy referenční pole výjimky je NULL. Tyto `exception_ptr` objekt, se nazývá *nulový exception_ptr*.

Použití `current_exception` nebo `make_exception_ptr` funkce pro přiřazení výjimky do `exception_ptr` objektu. Při přiřazení výjimky do `exception_ptr` proměnné, referenční pole výjimky proměnné odkazuje na kopii výjimky. Pokud není dostatek paměti pro zkopírování výjimky, referenční pole výjimky odkazuje na kopii [std::bad_alloc](../standard-library/bad-alloc-class.md) výjimky. Pokud `current_exception` nebo `make_exception_ptr` funkce nemůže zkopírovat výjimku z jiného důvodu, zavolá funkce [ukončit](../c-runtime-library/reference/terminate-crt.md) funkce, která se ukončila aktuální proces.

Bez ohledu na její název `exception_ptr` objektu je sám není ukazatel. Nedodržuje sémantiku ukazatele a nelze použít s přístup ke členu ukazatel (`->`) nebo dereference (`*`) operátory. `exception_ptr` Objekt nemá žádné veřejné datové členy a členské funkce.

### <a name="comparisons"></a>Porovnání

Můžete použít rovnosti (`==`) a není rovno (`!=`) operátory pro porovnání dvou `exception_ptr` objekty. Operátory neporovnávají binární hodnoty (bitový vzor) z `EXCEPTION_RECORD` struktury, které představují výjimky. Místo toho operátory porovnávají adresy v referenčním poli výjimky z `exception_ptr` objekty. V důsledku toho s hodnotou null `exception_ptr` a hodnota NULL rovnají.

## <a name="currentexception-function"></a>Funkce current_exception

Volání `current_exception` fungovat v **catch** bloku. Je-li výjimka v letu a **catch** bloku může zachytit výjimku, `current_exception` vrací funkce `exception_ptr` objekt, který na výjimku odkazuje. V opačném případě vrátí hodnotu null `exception_ptr` objektu.

### <a name="details"></a>Podrobnosti

`current_exception` Funkce zachytí výjimku, která je v letu, bez ohledu na to, zda **catch** příkaz určuje, [deklarace výjimky](../cpp/try-throw-and-catch-statements-cpp.md) příkazu.

Na konci je volán destruktor aktuální výjimky **catch** blokovat, pokud není výjimka znovu. Ale i v případě, že zavoláte `current_exception` fungovat v destruktoru vrátí funkce hodnotu `exception_ptr` objekt, který odkazuje na aktuální výjimku.

Následná volání `current_exception` funkce vrátit `exception_ptr` objekty, které odkazují na různé kopie aktuální výjimky. V důsledku toho se objekty při porovnání jeví jako nerovné, protože odkazují na jiné kopie, i přesto, že kopie mají stejné binární hodnoty.

### <a name="seh-exceptions"></a>Výjimky SEH

Pokud používáte **/EHa** – možnost kompilátoru, můžete zachytit výjimku SEH v C++ **catch** bloku. `current_exception` Vrací funkce `exception_ptr` objekt, který odkazuje na výjimku SEH. A `rethrow_exception` funkce vyvolá výjimku SEH při volání s thetransported `exception_ptr` objektu jako svůj argument.

`current_exception` Funkce vrátí hodnotu null `exception_ptr` při volání v SEH **__finally** obslužné rutiny ukončení **__except** obslužné rutiny výjimky nebo **__except**výraz filtru.

Přenesená výjimka nepodporuje vnořené výjimky. Vnořená výjimka nastane, pokud je při zpracování výjimky vyvolána jiná výjimka. Při zachycení vnořené výjimky `EXCEPTION_RECORD.ExceptionRecord` datový člen odkazuje na řetězec `EXCEPTION_RECORD` struktury, které popisují přidružené výjimky. `current_exception` Funkce nepodporuje vnořené výjimky, protože se vrátí `exception_ptr` jehož `ExceptionRecord` datový člen je vynulován.

Při zachycení výjimky SEH, je nutné spravovat paměť odkazovanou ukazateli v `EXCEPTION_RECORD.ExceptionInformation` poli datového členu. Je nutné zaručit, že paměť je platná po celou dobu životnosti odpovídajícího `exception_ptr` objektu a zda je paměť uvolněna při `exception_ptr` objekt odstranit.

Spolu s možností přenosu výjimek je možné použít funkce překladatele strukturovaných výjimek (SE). Pokud je výjimka SEH přeložena do výjimky jazyka C++, `current_exception` vrací funkce `exception_ptr` odkazující na přeloženou výjimku namísto původní výjimky SEH. `rethrow_exception` Funkce následně vyvolá přeloženou výjimku, nikoli původní výjimku. Další informace o funkcích překladače najdete v tématu [_set_se_translator](../c-runtime-library/reference/set-se-translator.md).

## <a name="rethrowexception-function"></a>Funkce rethrow_exception

Po uložení zachycené výjimky v `exception_ptr` objektu, může primární vlákno zpracovat objektu. V primárním vlákně, zavolejte `rethrow_exception` společně s funkcí `exception_ptr` objektu jako svůj argument. `rethrow_exception` Extrahuje výjimku z funkce `exception_ptr` objekt a potom vyvolá výjimku v kontextu primárního vlákna. Pokud *p* parametr `rethrow_exception` nulový `exception_ptr`, funkce vyvolá [std::bad_exception](../standard-library/bad-exception-class.md).

Extrahovaná výjimka je nyní aktuální výjimkou v primárním vlákně a je možné ji zpracovávat stejně jako jakoukoli jinou výjimku. Při zachycení výjimky, můžete ji okamžitě zpracovat nebo použít **throw** příkazu k odeslání obslužné rutině vyšší úrovně. Jinak není třeba dělat nic a je možné nechat výchozí obslužnou rutinu systému ukončit proces.

## <a name="makeexceptionptr-function"></a>Funkce make_exception_ptr

`make_exception_ptr` Funkce přijímající instanci třídy jako svůj argument a vrátí `exception_ptr` , která odkazuje na instanci. Obvykle, zadejte [třída výjimky](../standard-library/exception-class.md) jako argument pro objekt `make_exception_ptr` fungovat, i když jakýkoli objekt třídy může být argumentem.

Volání `make_exception_ptr` funkce je ekvivalentní k vyvolání výjimky jazyka C++, jejímu zachycení v **catch** bloku a následným voláním `current_exception` funkce, která se vrátí `exception_ptr` objekt, který na výjimku odkazuje. Implementace společnosti Microsoft `make_exception_ptr` funkce je efektivnější než vyvolávání a následné zachycování výjimky.

Aplikace obvykle nevyžaduje, aby `make_exception_ptr` funkce a zabraňte jejich použití.

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

**Záhlaví:** \<výjimky >

## <a name="see-also"></a>Viz také:

[Zpracování výjimek](../cpp/exception-handling-in-visual-cpp.md)<br/>
[/EH (model ošetření výjimek)](../build/reference/eh-exception-handling-model.md)<br/>
[/clr (kompilace modulu Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md)