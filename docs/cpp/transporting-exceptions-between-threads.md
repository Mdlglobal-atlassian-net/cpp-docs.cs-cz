---
title: Převod výjimek mezi vlákny
ms.date: 05/07/2019
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
ms.openlocfilehash: ca6ad9f9b923843d74a3b671691438af6ea5d82b
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68917018"
---
# <a name="transporting-exceptions-between-threads"></a>Převod výjimek mezi vlákny

Kompilátor Microsoft C++ (MSVC) podporuje *přenos výjimky* z jednoho vlákna do druhého. Přenos výjimek umožňuje zachytit výjimku v jednom vlákně a následně nechat výjimku vypadat, jako by byla vyvolána v jiném vlákně. Například je možné tuto funkci použít pro napsání vícevláknové aplikace, kde primární vlákno zpracovává všechny výjimky vyvolané sekundárními vlákny. Přenos výjimek je užitečný především pro vývojáře, kteří vytvářejí paralelní programovací knihovny nebo systémy. Pro implementaci přenosů výjimek poskytuje MSVC typ [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) a funkce [current_exception](../standard-library/exception-functions.md#current_exception), [rethrow_exception](../standard-library/exception-functions.md#rethrow_exception)a [make_exception_ptr](../standard-library/exception-functions.md#make_exception_ptr) .

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
|*neurčené*|Neurčená interní třída, která se používá k implementaci `exception_ptr` typu.|
|*p*|`exception_ptr` Objekt, který odkazuje na výjimku.|
|*E*|Třída, která představuje výjimku.|
|*e*|Instance třídy parametru `E` .|

## <a name="return-value"></a>Návratová hodnota

`current_exception` Funkce`exception_ptr` vrátí objekt, který odkazuje na výjimku, která aktuálně probíhá. Pokud žádná výjimka neprobíhá, funkce vrátí `exception_ptr` objekt, který není přidružen k žádné výjimce.

Funkce vrátí objekt, který odkazuje na výjimku určenou parametrem *e.* `make_exception_ptr` `exception_ptr`

## <a name="remarks"></a>Poznámky

### <a name="scenario"></a>Scénář

Představte si, že je třeba vytvořit aplikaci, která může škálovat pro zpracování různého množství práce. K dosažení tohoto cíle je možné navrhnout vícevláknovou aplikaci, kde původní primární vlákno vytvoří tolik sekundárních vláken, kolik jich je pro práci potřebných. Sekundární vlákna pomohou primárnímu vláknu spravovat prostředky, vyvažovat zatížení a zvýšit propustnost. Díky distribuci práce poskytuje vícevláknová aplikace lepší výkon než jednovláknová aplikace.

Avšak pokud sekundární vlákno vyvolá výjimku, mělo by ji primární vlákno zpracovat. To proto, aby aplikace zpracovávala výjimky konzistentním způsobem bez ohledu na počet sekundárních vláken.

### <a name="solution"></a>Řešení

Pro zvládnutí předchozího scénáře podporuje standard jazyka C++ přenos výjimek mezi vlákny. Pokud sekundární vlákno vyvolá výjimku, bude tato výjimka *aktuální výjimkou*. V případě analogového a reálného světa se aktuální výjimka označuje jako *v letu*. Aktuální výjimka je v letu od okamžiku jejího vyvolání po návrat obslužné rutiny výjimky, která ji zachytila.

Sekundární vlákno může zachytit aktuální výjimku v bloku **catch** a pak zavolat `current_exception` funkci pro uložení výjimky do `exception_ptr` objektu. `exception_ptr` Objekt musí být k dispozici sekundárnímu vláknu a primárnímu vláknu. `exception_ptr` Objekt může být například globální proměnná, jejíž přístup je řízen mutexem. Termín *přenosu výjimky* znamená, že výjimka v jednom vlákně může být převedena do formuláře, který je k dispozici v jiném vlákně.

Dále primární vlákno zavolá `rethrow_exception` funkci, která extrahuje a poté vyvolá výjimku `exception_ptr` z objektu. Jakmile je výjimka vyvolána, stane se v primárním vlákně aktuální výjimkou. A tak se zdá, že výjimka pochází z primárního vlákna.

Nakonec může primární vlákno zachytit aktuální výjimku v bloku **catch** a pak ji zpracovat nebo ji vyvolat do obslužné rutiny výjimky vyšší úrovně. Nebo může primární vlákno výjimku ignorovat a dovolit procesu skončit.

Většina aplikací nepotřebuje přenášet výjimky mezi vlákny. Nicméně tato funkce je užitečná v paralelních výpočetních systémech, protože systém může rozdělit práci mezi sekundární vlákna, procesory nebo jádra. V prostředí paralelních výpočtů může jedno vyhrazené vlákno zpracovávat všechny výjimky ze sekundárních vláken a poskytnout konzistentní model zpracování výjimek pro jakoukoli aplikaci.

Pro další informace o návrhu komise standardu jazyka C++ vyhledejte na internetu dokument s číslem N2179 a názvem „Language Support for Transporting Exceptions between Threads“.

### <a name="exception-handling-models-and-compiler-options"></a>Modely zpracování výjimek a možnosti kompilátoru

Model zpracování výjimek v aplikaci určuje, zda lze zachytit a přenést výjimku. Jazyk Visual C++ podporuje tři modely, kterými lze zpracovávat výjimky jazyka C++, výjimky strukturovaného zpracování výjimek (SEH) a výjimky modulu CLR. Použijte možnosti kompilátoru [/eh](../build/reference/eh-exception-handling-model.md) a [/CLR](../build/reference/clr-common-language-runtime-compilation.md) k určení modelu zpracování výjimek vaší aplikace.

Pouze následující kombinace možností kompilátoru a programovacích příkazů může přenést výjimku. Další kombinace buď nemohou zachytit výjimky, nebo je mohou zachytit, ale nemohou přenést.

- Možnost kompilátoru **/EHa** a příkaz **catch** mohou přenášet SEH a C++ výjimky.

- Možnosti kompilátoru **/EHa**, **/EHS**a **/EHsc** a příkaz **catch** mohou přenášet C++ výjimky.

- Možnost kompilátoru **/CLR** a příkaz **catch** mohou přenášet C++ výjimky. Možnost kompilátoru **/CLR** implikuje specifikaci možnosti **/EHa** . Je dobré si zapamatovat, že kompilátor nepodporuje přenos spravovaných výjimek. Důvodem je, že spravované výjimky, které jsou odvozeny od [třídy System. Exception](../standard-library/exception-class.md), jsou již objekty, které lze přesouvat mezi vlákny pomocí zařízení modulu Common CLR runtime.

   > [!IMPORTANT]
   > Doporučujeme zadat možnost kompilátoru **/EHsc** a zachytit pouze C++ výjimky. Pokud použijete možnost kompilátoru **/EHa** nebo **/CLR** a příkaz **catch** se třemi tečkami *-Declaration* (`catch(...)`), vystavíte se k bezpečnostní hrozbě. Máte pravděpodobně v úmyslu použít příkaz **catch** k zachycení několika specifických výjimek. Příkaz však zachycuje všechny C++ výjimky a SEH, včetně neočekávaných těch, které by měly být závažné. `catch(...)` Ignorováním nebo nesprávným zpracováním neočekávané výjimky může být dán prostor škodlivému kódu k ohrožení zabezpečení aplikace.

## <a name="usage"></a>Použití

Následující části `exception_ptr` popisují, jak přenášet výjimky pomocí typu, `current_exception`a `make_exception_ptr` funkce, `rethrow_exception`a.

## <a name="exception_ptr-type"></a>Typ exception_ptr

`exception_ptr` Použijte objekt pro odkazování na aktuální výjimku nebo instanci uživatelsky definované výjimky. V implementaci společnosti Microsoft je výjimka představována strukturou [EXCEPTION_RECORD](/windows/desktop/api/winnt/ns-winnt-exception_record) . Každý `exception_ptr` objekt obsahuje referenční pole výjimky, které odkazuje na kopii `EXCEPTION_RECORD` struktury, která představuje výjimku.

Pokud deklarujete `exception_ptr` proměnnou, proměnná není přidružena k žádné výjimce. Tedy referenční pole výjimky je NULL. Takový objekt se nazývá exception_ptr s *hodnotou null.* `exception_ptr`

Pomocí funkce `current_exception` or `make_exception_ptr` můžete`exception_ptr` přiřadit výjimku objektu. Pokud přiřadíte výjimku `exception_ptr` proměnné, referenční pole výjimky proměnné odkazuje na kopii výjimky. Pokud není k dispozici dostatek paměti ke zkopírování výjimky, referenční pole výjimky odkazuje na kopii výjimky [std:: bad_alloc](../standard-library/bad-alloc-class.md) . Pokud funkce `make_exception_ptr` nebo nemůže výjimku kopírovat z jakéhokoli jiného důvodu, funkce zavolá funkci ukončení pro ukončení aktuálního procesu. [](../c-runtime-library/reference/terminate-crt.md) `current_exception`

Bez ohledu na jeho název `exception_ptr` objekt není ukazatelem. Nedodržuje sémantiku ukazatele a nelze jej použít s operátory přístupu členů (`->`) a dedirect (`*`) ukazatele. `exception_ptr` Objekt nemá žádné veřejné datové členy ani členské funkce.

### <a name="comparisons"></a>Porovnání

Operátory EQUAL (`==`) a not-equal (`!=`) můžete použít k porovnání dvou `exception_ptr` objektů. Operátory neporovnání binární hodnoty (bitového vzoru) `EXCEPTION_RECORD` struktur, které reprezentují výjimky. Místo toho operátory porovnávají adresy v referenčním poli `exception_ptr` výjimky objektů. V důsledku toho je `exception_ptr` hodnota null a hodnota null porovnána jako shodná.

## <a name="current_exception-function"></a>Funkce current_exception

Volání funkce v bloku **catch.** `current_exception` Je-li výjimka v letu a blok **catch** může výjimku zachytit, `current_exception` funkce vrátí `exception_ptr` objekt, který odkazuje na výjimku. V opačném případě funkce vrátí objekt `exception_ptr` null.

### <a name="details"></a>Podrobnosti

Funkce zachycuje výjimku, která je v letadle bez ohledu na to, zda příkaz **catch** Určuje příkaz [deklarace výjimky.](../cpp/try-throw-and-catch-statements-cpp.md) `current_exception`

Destruktor pro aktuální výjimku je volána na konci bloku **catch** , pokud výjimku nevyvoláte znovu. Nicméně i v případě, že zavoláte `current_exception` funkci v destruktoru, funkce `exception_ptr` vrátí objekt, který odkazuje na aktuální výjimku.

Po sobě jdoucí volání `current_exception` funkce vrátí `exception_ptr` objekty, které odkazují na různé kopie aktuální výjimky. V důsledku toho se objekty při porovnání jeví jako nerovné, protože odkazují na jiné kopie, i přesto, že kopie mají stejné binární hodnoty.

### <a name="seh-exceptions"></a>Výjimky SEH

Použijete-li možnost kompilátoru **/EHa** , můžete zachytit výjimku SEH v C++ bloku **catch** . `current_exception` Funkce`exception_ptr` vrátí objekt, který odkazuje na výjimku SEH. A funkce vyvolá výjimku SEH, pokud ji zavoláte s objektem thetransported `exception_ptr` jako jeho argument. `rethrow_exception`

`exception_ptr` Funkce vrátí hodnotu null, pokud ji zavoláte v obslužné rutině ukončení SEH __finally, obslužné rutiny výjimky __except nebo výrazu filtru __except. `current_exception`

Přenesená výjimka nepodporuje vnořené výjimky. Vnořená výjimka nastane, pokud je při zpracování výjimky vyvolána jiná výjimka. Pokud zachytíte vnořenou výjimku, `EXCEPTION_RECORD.ExceptionRecord` datový člen odkazuje na `EXCEPTION_RECORD` řetězec struktury, které popisují přidružené výjimky. Funkce nepodporuje vnořené výjimky, protože `exception_ptr` vrátí objekt, jehož `ExceptionRecord` datový člen je vypočítán od nuly. `current_exception`

Pokud zachytíte výjimku SEH, musíte spravovat paměť, na kterou odkazuje libovolný ukazatel v `EXCEPTION_RECORD.ExceptionInformation` poli datového člena. Je nutné zaručit, že paměť je platná během životnosti odpovídajícího `exception_ptr` objektu a že je paměť uvolněna `exception_ptr` při odstranění objektu.

Spolu s možností přenosu výjimek je možné použít funkce překladatele strukturovaných výjimek (SE). Pokud je výjimka SEH přeložena na C++ výjimku, `current_exception` funkce vrátí objekt `exception_ptr` , který odkazuje na přeloženou výjimku namísto původní výjimky SEH. `rethrow_exception` Funkce následně vyvolá přeloženou výjimku, nikoli původní výjimku. Další informace o funkcích překladatele se dozvíte v tématu [_set_se_translator](../c-runtime-library/reference/set-se-translator.md).

## <a name="rethrow_exception-function"></a>Funkce rethrow_exception

Po uložení zachycené výjimky v `exception_ptr` objektu může primární vlákno zpracovat objekt. V primárním vlákně zavolejte `rethrow_exception` funkci spolu `exception_ptr` s objektem jako argument. Funkce extrahuje výjimku z objektu a poté vyvolá výjimku v kontextu primárního vlákna. `exception_ptr` `rethrow_exception` Pokud je parametr `rethrow_exception` p funkce null `exception_ptr`, funkce vyvolá [std:: bad_exception](../standard-library/bad-exception-class.md).

Extrahovaná výjimka je nyní aktuální výjimkou v primárním vlákně a je možné ji zpracovávat stejně jako jakoukoli jinou výjimku. Pokud zachytíte výjimku, můžete ji okamžitě zpracovat nebo použít příkaz **throw** k odeslání do obslužné rutiny výjimky vyšší úrovně. Jinak není třeba dělat nic a je možné nechat výchozí obslužnou rutinu systému ukončit proces.

## <a name="make_exception_ptr-function"></a>Funkce make_exception_ptr

Funkce převezme instanci třídy jako argument a poté vrátí objekt `exception_ptr` , který odkazuje na instanci. `make_exception_ptr` Obvykle určíte objekt [třídy výjimky](../standard-library/exception-class.md) jako argument `make_exception_ptr` funkce, i když libovolný objekt třídy může být argumentem.

`exception_ptr` `current_exception` C++ Volání funkce je ekvivalentní k vyvolání výjimky, jejímu zachycení v bloku catch a následným voláním funkce pro vrácení objektu, který na výjimku odkazuje. `make_exception_ptr` Implementace `make_exception_ptr` funkce od Microsoftu je efektivnější než vyvolání a pak zachytí výjimku.

Aplikace obvykle nevyžaduje `make_exception_ptr` funkci a neodrazí se její použití.

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

**Hlavička:** \<> výjimky

## <a name="see-also"></a>Viz také:

[Zpracování výjimek](../cpp/exception-handling-in-visual-cpp.md)<br/>
[/EH (model ošetření výjimek)](../build/reference/eh-exception-handling-model.md)<br/>
[/clr (kompilace modulu Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md)
