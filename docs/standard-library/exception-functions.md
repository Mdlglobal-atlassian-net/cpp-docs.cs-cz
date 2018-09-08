---
title: '&lt;výjimka&gt; funkce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- exception/std::current_exception
- exception/std::get_terminate
- exception/std::get_unexpected
- exception/std::make_exception_ptr
- exception/std::rethrow_exception
- exception/std::set_terminate
- exception/std::set_unexpected
- exception/std::terminate
- exception/std::uncaught_exception
- exception/std::unexpected
ms.assetid: c09ac569-5e35-4fe8-872d-ca5810274dd7
helpviewer_keywords:
- std::current_exception [C++]
- std::get_terminate [C++]
- std::get_unexpected [C++]
- std::make_exception_ptr [C++]
- std::rethrow_exception [C++]
- std::set_terminate [C++]
- std::set_unexpected [C++]
- std::terminate [C++]
- std::uncaught_exception [C++]
- std::unexpected [C++]
ms.openlocfilehash: 9401772e35527c63f47dc10bbb0e501029558825
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44105403"
---
# <a name="ltexceptiongt-functions"></a>&lt;výjimka&gt; funkce

||||
|-|-|-|
|[current_exception](#current_exception)|[get_terminate –](#get_terminate)|[get_unexpected](#get_unexpected)|
|[make_exception_ptr](#make_exception_ptr)|[rethrow_exception](#rethrow_exception)|[set_terminate](#set_terminate)|
|[set_unexpected](#set_unexpected)|[ukončit](#terminate)|[uncaught_exception](#uncaught_exception)|
|[unexpected](#unexpected)|

## <a name="current_exception"></a>  current_exception

Získá inteligentní ukazatel na aktuální výjimku.

```cpp
exception_ptr current_exception();
```

### <a name="return-value"></a>Návratová hodnota

[Exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) ukazující na aktuální výjimku.

### <a name="remarks"></a>Poznámky

Volání `current_exception` funkce v bloku catch. Je-li výjimka v letu a blok catch může zachytit výjimku, `current_exception` vrací funkce `exception_ptr` objekt, který na výjimku odkazuje. V opačném případě vrátí hodnotu null `exception_ptr` objektu.

`current_exception` Funkce zachytí výjimku, která je v letu, bez ohledu na to, zda **catch** příkaz určuje, [deklarace výjimky](../cpp/try-throw-and-catch-statements-cpp.md) příkazu.

Na konci je volán destruktor aktuální výjimky **catch** blokovat, pokud není výjimka znovu. Ale i v případě, že zavoláte `current_exception` fungovat v destruktoru vrátí funkce hodnotu `exception_ptr` objekt, který odkazuje na aktuální výjimku.

Následná volání `current_exception` funkce vrátit `exception_ptr` objekty, které odkazují na různé kopie aktuální výjimky. V důsledku toho se objekty při porovnání jeví jako nerovné, protože odkazují na jiné kopie, i přesto, že kopie mají stejné binární hodnoty.

## <a name="make_exception_ptr"></a>  make_exception_ptr

Vytvoří [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) objekt, který obsahuje kopii výjimky.

```cpp
template <class E>
exception_ptr make_exception_ptr(E Except);
```

### <a name="parameters"></a>Parametry

*S výjimkou*<br/>
Třída s výjimkou pro kopírování Obvykle, zadejte [třída výjimky](../standard-library/exception-class.md) jako argument pro objekt `make_exception_ptr` fungovat, i když jakýkoli objekt třídy může být argumentem.

### <a name="return-value"></a>Návratová hodnota

[Exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) ukazující na kopii aktuální výjimky pro *s výjimkou*.

### <a name="remarks"></a>Poznámky

Volání `make_exception_ptr` funkce je ekvivalentní k vyvolání výjimky jazyka C++, jejímu zachycení v bloku catch a následným voláním [current_exception](../standard-library/exception-functions.md#current_exception) funkce, která se vrátí `exception_ptr` objekt, který na výjimku odkazuje. Implementace společnosti Microsoft `make_exception_ptr` funkce je efektivnější než vyvolávání a následné zachycování výjimky.

Aplikace obvykle nevyžaduje, aby `make_exception_ptr` funkce a zabraňte jejich použití.

## <a name="rethrow_exception"></a>  rethrow_exception

Vyvolá výjimku předanou jako parametr.

```cpp
void rethrow_exception(exception_ptr P);
```

### <a name="parameters"></a>Parametry

*P*<br/>
Zachycená výjimka, kterou chcete znovu vyvolat. Pokud *P* nulový [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr), funkce vyvolá [std::bad_exception](../standard-library/bad-exception-class.md).

### <a name="remarks"></a>Poznámky

Po uložení zachycené výjimky v `exception_ptr` objektu, může primární vlákno zpracovat objektu. V primárním vlákně, zavolejte `rethrow_exception` společně s funkcí `exception_ptr` objektu jako svůj argument. `rethrow_exception` Extrahuje výjimku z funkce `exception_ptr` objekt a potom vyvolá výjimku v kontextu primárního vlákna.

## <a name="get_terminate"></a>  get_terminate –

Získá aktuální `terminate_handler` funkce.

```cpp
terminate_handler get_terminate();
```

## <a name="set_terminate"></a>  set_terminate

Vytvoří novou `terminate_handler` která se má volat při ukončení programu.

```cpp
terminate_handler set_terminate(terminate_handler fnew) throw();
```

### <a name="parameters"></a>Parametry

*fnew*<br/>
Funkce, která se má volat při ukončení.

### <a name="return-value"></a>Návratová hodnota

Adresa předchozí funkci, která se používá k volání při ukončení.

### <a name="remarks"></a>Poznámky

Vytvoří novou funkci [terminate_handler](../standard-library/exception-typedefs.md#terminate_handler) jako funkce * *fnew*. Proto *fnew* nesmí být nulový ukazatel. Funkce vrátí adresu předchozí obslužnou rutinu ukončení.

### <a name="example"></a>Příklad

```cpp
// exception_set_terminate.cpp
// compile with: /EHsc
#include <exception>
#include <iostream>

using namespace std;

void termfunction()
{
    cout << "My terminate function called." << endl;
    abort();
}

int main()
{
    terminate_handler oldHandler = set_terminate(termfunction);

    // Throwing an unhandled exception would also terminate the program
    // or we could explicitly call terminate();

    //throw bad_alloc();
    terminate();
}

```

## <a name="get_unexpected"></a>  get_unexpected –

Získá aktuální `unexpected_handler` funkce.

```cpp
unexpected_handler get_unexpected();
```

## <a name="set_unexpected"></a>  set_unexpected

Vytvoří novou `unexpected_handler` bude při k neočekávané výjimce.

```cpp
unexpected_handler set_unexpected(unexpected_handler fnew) throw();
```

### <a name="parameters"></a>Parametry

*fnew*<br/>
Funkce se volá, když je došlo k neočekávané výjimce.

### <a name="return-value"></a>Návratová hodnota

Adresa předchozí `unexpected_handler`.

### <a name="remarks"></a>Poznámky

*fnew* nesmí být nulový ukazatel.

Standard jazyka C++ vyžaduje, aby `unexpected` se volá, když funkce vyvolá výjimku, která se nenachází ve svém seznamu vyvolání výjimky. Aktuální implementace to nepodporuje. Následující příklad volá `unexpected` přímo, který pak volá `unexpected_handler`.

### <a name="example"></a>Příklad

```cpp
// exception_set_unexpected.cpp
// compile with: /EHsc
#include <exception>
#include <iostream>

using namespace std;

void uefunction()
{
    cout << "My unhandled exception function called." << endl;
    terminate(); // this is what unexpected() calls by default
}

int main()
{
    unexpected_handler oldHandler = set_unexpected(uefunction);

    unexpected(); // library function to force calling the
                  // current unexpected handler
}

```

## <a name="terminate"></a>  ukončit

Zavolá obslužnou rutinu ukončení.

```cpp
void terminate();
```

### <a name="remarks"></a>Poznámky

Funkce volá obslužná rutina ukončení, – funkce typu **void**. Pokud `terminate` přímo volá obslužná rutina ukončení programu je ten poslední nastavení voláním [set_terminate](../standard-library/exception-functions.md#set_terminate). Pokud `terminate` je volána pro některý z několika důvodů během vyhodnocení výraz throw, obslužná rutina ukončení je v platnosti okamžitě po vyhodnocení výraz throw.

Obslužná rutina ukončení nesmí vracet volajícímu. Při spuštění programu, je obslužná rutina ukončení funkce, která volá `abort`.

### <a name="example"></a>Příklad

Zobrazit [set_unexpected](../standard-library/exception-functions.md#set_unexpected) příklad použití `terminate`.

## <a name="uncaught_exception"></a>  uncaught_exception

Vrátí **true** pouze v případě, že je vyvolaná výjimka právě zpracovávána.

```cpp
bool uncaught_exception();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí **true** po dokončení hodnocení výraz throw a před dokončením inicializace deklaraci výjimky v odpovídající obslužná rutina nebo volání [neočekávané](../standard-library/exception-functions.md#unexpected) kvůli výraz throw. Zejména `uncaught_exception` vrátí **true** při volání z destruktoru, který je právě vyvolána při unwind výjimek. Na zařízeních `uncaught_exception` je podporován pouze ve Windows CE 5.00 a vyšších verzích, včetně platforem Windows Mobile 2005.

### <a name="example"></a>Příklad

```cpp
// exception_uncaught_exception.cpp
// compile with: /EHsc
#include <exception>
#include <iostream>
#include <string>

class Test
{
public:
   Test( std::string msg ) : m_msg( msg )
   {
      std::cout << "In Test::Test(\"" << m_msg << "\")" << std::endl;
   }
   ~Test( )
   {
      std::cout << "In Test::~Test(\"" << m_msg << "\")" << std::endl
         << "        std::uncaught_exception( ) = "
         << std::uncaught_exception( )
         << std::endl;
   }
private:
    std::string m_msg;
};

// uncaught_exception will be true in the destructor
// for the object created inside the try block because
// the destructor is being called as part of the unwind.

int main( void )
   {
      Test t1( "outside try block" );
      try
      {
         Test t2( "inside try block" );
         throw 1;
      }
      catch (...) {
   }
}
```

```Output
In Test::Test("outside try block")
In Test::Test("inside try block")
In Test::~Test("inside try block")
        std::uncaught_exception( ) = 1
In Test::~Test("outside try block")
        std::uncaught_exception( ) = 0
```

## <a name="unexpected"></a>  neočekávané

Volá obslužnou rutinu neočekávané.

```cpp
void unexpected();
```

### <a name="remarks"></a>Poznámky

Standard jazyka C++ vyžaduje, aby `unexpected` se volá, když funkce vyvolá výjimku, která se nenachází ve svém seznamu vyvolání výjimky. Aktuální implementace to nepodporuje. Příklad volá `unexpected` přímo, která volá obslužnou rutinu neočekávané.

Funkce vyvolá obslužnou rutinu neočekávané, – funkce typu **void**. Pokud `unexpected` je volán přímo program obslužnou rutinu neočekávané je ten poslední nastavení voláním [set_unexpected](../standard-library/exception-functions.md#set_unexpected).

Obslužnou rutinu neočekávané nemusí vrátí výsledek volajícímu. To může ukončit provádění podle:

- Aktivační objekt typu uvedené v specifikace výjimky nebo objekt jakéhokoli typu, pokud volá obslužnou rutinu neočekávané přímo do programu.

- Aktivační objekt typu [bad_exception –](../standard-library/bad-exception-class.md).

- Volání [ukončit](../standard-library/exception-functions.md#terminate), `abort` nebo **ukončit**(`int`).

Při spuštění programu obslužnou rutinu neočekávané je funkce, která volá [ukončit](../standard-library/exception-functions.md#terminate).

### <a name="example"></a>Příklad

Zobrazit [set_unexpected](../standard-library/exception-functions.md#set_unexpected) příklad použití `unexpected`.

## <a name="see-also"></a>Viz také:

[\<výjimky >](../standard-library/exception.md)<br/>
