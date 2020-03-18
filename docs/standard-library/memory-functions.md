---
title: funkce &lt;paměti&gt;
ms.date: 08/05/2019
f1_keywords:
- memory/std::addressof
- memory/std::align
- memory/std::allocate_shared
- memory/std::const_pointer_cast
- memory/std::declare_no_pointers
- memory/std::declare_reachable
- memory/std::default_delete
- memory/std::dynamic_pointer_cast
- memory/std::get_deleter
- memory/std::get_pointer_safety
- memory/std::get_temporary_buffer
- xmemory/std::get_temporary_buffer
- memory/std::make_shared
- memory/std::make_unique
- memory/std::owner_less
- memory/std::reinterpret_pointer_cast
- memory/std::return_temporary_buffer
- xmemory/std::return_temporary_buffer
- memory/std::static_pointer_cast
- memory/std::swap
- memory/std::undeclare_no_pointers
- memory/std::undeclare_reachable
- memory/std::uninitialized_copy
- memory/std::uninitialized_copy_n
- memory/std::uninitialized_fill
- memory/std::uninitialized_fill_n
- memory/std::get_temporary_buffer
- memory/std::return_temporary_buffer
ms.assetid: 3e1898c2-44b7-4626-87ce-84962e4c6f1a
helpviewer_keywords:
- std::addressof [C++]
- std::align [C++]
- std::allocate_shared [C++]
- std::const_pointer_cast [C++]
- std::declare_no_pointers [C++]
- std::declare_reachable [C++]
- std::default_delete [C++]
- std::dynamic_pointer_cast [C++]
- std::get_deleter [C++]
- std::get_pointer_safety [C++]
- std::get_temporary_buffer [C++]
- std::make_shared [C++]
- std::make_unique [C++]
- std::owner_less [C++]
- std::return_temporary_buffer [C++]
- std::static_pointer_cast [C++]
- std::swap [C++]
- std::undeclare_no_pointers [C++]
- std::undeclare_reachable [C++]
- std::uninitialized_copy [C++]
- std::uninitialized_copy_n [C++]
- std::uninitialized_fill [C++]
- std::uninitialized_fill_n [C++]
- std::addressof [C++]
- std::align [C++]
- std::allocate_shared [C++]
- std::const_pointer_cast [C++]
- std::declare_no_pointers [C++]
- std::declare_reachable [C++]
- std::default_delete [C++]
- std::dynamic_pointer_cast [C++]
- std::get_deleter [C++]
- std::get_pointer_safety [C++]
- std::get_temporary_buffer [C++]
- std::make_shared [C++]
- std::make_unique [C++]
- std::owner_less [C++]
- std::return_temporary_buffer [C++]
- std::static_pointer_cast [C++]
- std::undeclare_no_pointers [C++]
- std::undeclare_reachable [C++]
- std::uninitialized_copy [C++]
- std::uninitialized_copy_n [C++]
- std::uninitialized_fill [C++]
- std::uninitialized_fill_n [C++]
ms.openlocfilehash: 2aceb96fcda49df8a1fd40a1bd8011170dccd8ef
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419936"
---
# <a name="ltmemorygt-functions"></a>funkce &lt;paměti&gt;

## <a name="addressof"></a>AddressOf

Získá adresu true objektu.

```cpp
template <class T>
T* addressof(
    T& value) noexcept;    // before C++17

template <class T>
constexpr T* addressof(
    T& value) noexcept;    // C++17

template <class T>
const T* addressof(
    const T&& value) = delete;   // C++17
```

### <a name="parameters"></a>Parametry

*hodnota*\
Objekt nebo funkce, pro které chcete získat adresu true.

### <a name="return-value"></a>Návratová hodnota

Skutečná adresa objektu nebo funkce, na kterou odkazuje *hodnota*, i když existuje přetížený `operator&()`.

### <a name="remarks"></a>Poznámky

## <a name="align"></a>vztahují

Zahodí úložiště dané velikosti, zarovnané podle konkrétní specifikace zarovnání, do první možné adresy daného úložiště.

```cpp
void* align(
    size_t alignment, // input
    size_t size,      // input
    void*& ptr,       // input/output
    size_t& space     // input/output
);
```

### <a name="parameters"></a>Parametry

\ *Zarovnání*
Zarovnání čekající na pokus.

*velikost*\
Velikost v bajtech pro zarovnané úložiště.

\ *PTR*
Počáteční adresa dostupného nepřetržitého fondu úložiště, který chcete použít. Tento parametr je také výstupní parametr a je nastaven tak, aby obsahoval novou počáteční adresu, pokud je zarovnání úspěšné. Pokud je `align()` neúspěšná, tento parametr se neupraví.

\ *mezer*
Celkové místo dostupné pro `align()`, které se má použít při vytváření zarovnaného úložiště. Tento parametr je také výstupní parametr a obsahuje zbývající upravené místo ve vyrovnávací paměti úložiště po odečtení zarovnaného úložiště a veškeré přidružené režie.

Pokud je `align()` neúspěšná, tento parametr se neupraví.

### <a name="return-value"></a>Návratová hodnota

Ukazatel s hodnotou null, pokud se požadovaná zarovnaná vyrovnávací paměť nevejde do dostupného místa; v opačném případě nová hodnota *PTR*.

### <a name="remarks"></a>Poznámky

Upravené parametry *PTR* a *space* umožňují volat `align()` opakovaně ve stejné vyrovnávací paměti, případně s různými hodnotami pro *Zarovnání* a *Velikost*. Následující fragment kódu ukazuje jedno použití `align()`.

```cpp
#include <type_traits> // std::alignment_of()
#include <memory>
//...
char buffer[256]; // for simplicity
size_t alignment = std::alignment_of<int>::value;
void * ptr = buffer;
std::size_t space = sizeof(buffer); // Be sure this results in the true size of your buffer

while (std::align(alignment, sizeof(MyObj), ptr, space)) {
    // You now have storage the size of MyObj, starting at ptr, aligned on
    // int boundary. Use it here if you like, or save off the starting address
    // contained in ptr for later use.
    // ...
    // Last, move starting pointer and decrease available space before
    // the while loop restarts.
    ptr = reinterpret_cast<char*>(ptr) + sizeof(MyObj);
    space -= sizeof(MyObj);
}
// At this point, align() has returned a null pointer, signaling it is not
// possible to allow more aligned storage in this buffer.
```

## <a name="allocate_shared"></a>allocate_shared

Vytvoří [shared_ptr](shared-ptr-class.md) pro objekty, které jsou přiděleny a sestaveny pro daný typ pomocí zadaného přidělování. Vrátí `shared_ptr`.

```cpp
template <class T, class Allocator, class... Args>
shared_ptr<T> allocate_shared(
    Allocator alloc,
    Args&&... args);
```

### <a name="parameters"></a>Parametry

\ *přidělení*
Alokátor použitý k vytvoření objektů.

\ *argumentů*
Nula nebo více argumentů, které se stanou objekty.

### <a name="remarks"></a>Poznámky

Funkce vytvoří objekt `shared_ptr<T>`, ukazatel na `T(args...)` přidělený a konstruovaný pomocí *přidělení*.

## <a name="atomic_compare_exchange_strong"></a>atomic_compare_exchange_strong

```cpp
template<class T>
bool atomic_compare_exchange_strong(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w);
```

## <a name="atomic_compare_exchange_weak"></a>atomic_compare_exchange_weak

```cpp
template<class T>
bool atomic_compare_exchange_weak(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w);
```

## <a name="atomic_compare_exchange_strong_explicit"></a>atomic_compare_exchange_strong_explicit

```cpp
template<class T>
bool atomic_compare_exchange_strong_explicit(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w,
    memory_order success,
    memory_order failure);
```

## <a name="atomic_compare_exchange_weak_explicit"></a>atomic_compare_exchange_weak_explicit

```cpp
template<class T>
bool atomic_compare_exchange_weak_explicit(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w,
    memory_order success,
    memory_order failure);
```

## <a name="atomic_exchange"></a>atomic_exchange

```cpp
template<class T>
shared_ptr<T> atomic_exchange(
    shared_ptr<T>* u,
    shared_ptr<T> r);
```

## <a name="atomic_exchange_explicit"></a>atomic_exchange_explicit

```cpp
template<class T>
shared_ptr<T> atomic_exchange_explicit(
    shared_ptr<T>* u,
    shared_ptr<T> r,
    memory_order mo);
```

## <a name="atomic_is_lock_free"></a>atomic_is_lock_free

```cpp
template<class T>
bool atomic_is_lock_free(
    const shared_ptr<T>* u);
```

## <a name="atomic_load"></a>atomic_load

```cpp
template<class T>
shared_ptr<T> atomic_load(
    const shared_ptr<T>* u);
```

## <a name="atomic_load_explicit"></a>atomic_load_explicit

```cpp
template<class T>
shared_ptr<T> atomic_load_explicit(
    const shared_ptr<T>* u,
    memory_order mo);
```

## <a name="atomic_store"></a>atomic_store

```cpp
template<class T>
void atomic_store(
    shared_ptr<T>* u,
    shared_ptr<T> r);
```

## <a name="atomic_store_explicit"></a>atomic_store_explicit

```cpp
template<class T>
void atomic_store_explicit(
    shared_ptr<T>* u,
    shared_ptr<T> r,
    memory_order mo);
```

## <a name="const_pointer_cast"></a>const_pointer_cast

Const cast na [shared_ptr](shared-ptr-class.md).

```cpp
template <class T, class Other>
shared_ptr<T> const_pointer_cast(
    const shared_ptr<Other>& sp) noexcept;

template <class T, class Other>
shared_ptr<T> const_pointer_cast(
    shared_ptr<Other>&& sp) noexcept;
```

### <a name="parameters"></a>Parametry

*T*\
Typ řízený vráceným sdíleným ukazatelem.

*Jiné*\
Typ řízený sdíleným ukazatelem argumentu.

\ *SP*
Sdílený ukazatel argumentu.

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí prázdný objekt `shared_ptr`, pokud `const_cast<T*>(sp.get())` vrací ukazatel s hodnotou null; v opačném případě vrátí objekt `shared_ptr<T>`, který vlastní prostředek, který je vlastníkem *SP*. Výraz `const_cast<T*>(sp.get())` musí být platný.

### <a name="example"></a>Příklad

```cpp
// std__memory__const_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int);
    std::shared_ptr<const int> sp1 =
        std::const_pointer_cast<const int>(sp0);

    *sp0 = 3;
    std::cout << "sp1 == " << *sp1 << std::endl;

    return (0);
}
```

```Output
sp1 == 3
```

## <a name="declare_no_pointers"></a>declare_no_pointers

Informuje uvolňování paměti, že znaky v bloku paměti definované ukazatelem základní adresy a velikostí bloku neobsahují žádné ukazatele Trace.

```cpp
void declare_no_pointers(
    char* ptr,
    size_t size);
```

### <a name="parameters"></a>Parametry

\ *PTR*
Adresa prvního znaku, který již neobsahuje sledovací ukazatele.

*velikost*\
Velikost bloku, který začíná na *PTR* , který neobsahuje žádné zjistitelné ukazatele.

### <a name="remarks"></a>Poznámky

Funkce informuje všechny systémy uvolňování paměti, že adresy v rozsahu `[ ptr, ptr + size)` již neobsahují sledovací ukazatele. (Všechny ukazatele na přidělené úložiště se nesmí odkázat, pokud se nedají dosáhnout.)

## <a name="declare_reachable"></a>declare_reachable

Informuje uvolňování paměti, že je uvedena adresa pro přidělení úložištěm a je k dispozici.

```cpp
void declare_reachable(
    void* ptr);
```

### <a name="parameters"></a>Parametry

\ *PTR*
Ukazatel na dosažitelnou, přidělenou a platnou oblast úložiště.

### <a name="remarks"></a>Poznámky

Pokud *PTR* není null, funkce informuje všechny uvolňování paměti, které *PTR* je teď dostupné, to znamená, že odkazuje na platné přidělené úložiště.

## <a name="default_delete"></a>default_delete

Odstraní objekty přidělené s **operátorem New**. Vhodné pro použití s [unique_ptr](unique-ptr-class.md).

```cpp
struct default_delete
{
    constexpr default_delete() noexcept = default;

    template <class Other, class = typename enable_if<is_convertible<Other*, T*>::value, void>::type>>
    default_delete(const default_delete<Other>&) noexcept;

    void operator()(T* ptr) const noexcept;
};
```

### <a name="parameters"></a>Parametry

\ *PTR*
Ukazatel na objekt, který chcete odstranit.

*Jiné*\
Typ prvků v poli, který má být odstraněn.

### <a name="remarks"></a>Poznámky

Šablona třídy popisuje odstranění, které odstraní skalární objekty přidělené **operátorem New**, vhodné pro použití s šablonou třídy `unique_ptr`. Má také explicitní `default_delete<T[]>`specializace.

## <a name="destroy_at"></a>destroy_at

```cpp
template <class T>
void destroy_at(
    T* location);
```

Stejné jako `location->~T()`.

## <a name="destroy"></a>způsobit

```cpp
template <class ForwardIterator>
void destroy(
    ForwardIterator first,
    ForwardIterator last);
```

Stejné jako:

```cpp
for (; first != last; ++first)
    destroy_at(addressof(*first));
```

## <a name="destroy_n"></a>destroy_n

```cpp
template <class ForwardIterator, class Size>
ForwardIterator destroy_n(
    ForwardIterator first,
    Size count);
```

Stejné jako:

```cpp
for (; count > 0; (void)++first, --count)
    destroy_at(addressof(*first));
return first;
```

## <a name="dynamic_pointer_cast"></a>dynamic_pointer_cast

Dynamické přetypování na [shared_ptr](shared-ptr-class.md).

```cpp
template <class T, class Other>
shared_ptr<T> dynamic_pointer_cast(
    const shared_ptr<Other>& sp) noexcept;

template <class T, class Other>
shared_ptr<T> dynamic_pointer_cast(
    shared_ptr<Other>&& sp) noexcept;
```

### <a name="parameters"></a>Parametry

*T*\
Typ řízený vráceným sdíleným ukazatelem.

*Jiné*\
Typ řízený sdíleným ukazatelem argumentu.

\ *SP*
Sdílený ukazatel argumentu.

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí prázdný objekt `shared_ptr`, pokud `dynamic_cast<T*>(sp.get())` vrací ukazatel s hodnotou null; v opačném případě vrátí objekt `shared_ptr<T>`, který vlastní prostředek, který je vlastníkem *SP*. Výraz `dynamic_cast<T*>(sp.get())` musí být platný.

### <a name="example"></a>Příklad

```cpp
// std__memory__dynamic_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    virtual ~base() {}
    int value;
};

struct derived
    : public base
{
};

int main()
{
    std::shared_ptr<base> sp0(new derived);
    std::shared_ptr<derived> sp1 =
        std::dynamic_pointer_cast<derived>(sp0);

    sp0->value = 3;
    std::cout << "sp1->value == " << sp1->value << std::endl;

    return (0);
}
```

```Output
sp1->value == 3
```

## <a name="get_deleter"></a>get_deleter

Získat z [shared_ptr](shared-ptr-class.md)odstranit.

```cpp
template <class Deleter, class T>
Deleter* get_deleter(
    const shared_ptr<T>& sp) noexcept;
```

### <a name="parameters"></a>Parametry

\ *odstranění*
Typ odstranění.

*T*\
Typ řízený sdíleným ukazatelem.

\ *SP*
Sdílený ukazatel.

### <a name="remarks"></a>Poznámky

Funkce šablony vrací ukazatel na odstranění typu *Odstranit* , který patří do `shared_ptr`ho objektu *SP*. Pokud v nástroji *SP* není odstraněn nebo pokud jeho odstranění není typu *Delete*, vrátí funkce hodnotu 0.

### <a name="example"></a>Příklad

```cpp
// std__memory__get_deleter.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    int value;
};

struct deleter
{
    void operator()(base *pb)
    {
        delete pb;
    }
};

int main()
{
    std::shared_ptr<base> sp0(new base);

    sp0->value = 3;
    std::cout << "get_deleter(sp0) != 0 == " << std::boolalpha
        << (std::get_deleter<deleter>(sp0) != 0) << std::endl;

    std::shared_ptr<base> sp1(new base, deleter());

    sp0->value = 3;
    std::cout << "get_deleter(sp1) != 0 == " << std::boolalpha
        << (std::get_deleter<deleter>(sp1) != 0) << std::endl;

    return (0);
}
```

```Output
get_deleter(sp0) != 0 == false
get_deleter(sp1) != 0 == true
```

## <a name="get_pointer_safety"></a>get_pointer_safety

Vrátí typ zabezpečení ukazatele uvedený v rámci uvolňování paměti.

```cpp
pointer_safety get_pointer_safety() noexcept;
```

### <a name="remarks"></a>Poznámky

Funkce vrátí typ zabezpečení ukazatele, který předpokládá jakékoli automatické uvolňování paměti.

## <a name="get_temporary_buffer"></a>get_temporary_buffer

Přidělí dočasné úložiště pro sekvenci prvků, které nepřekračují zadaný počet prvků.

```cpp
template <class T>
pair<T *, ptrdiff_t> get_temporary_buffer(
    ptrdiff_t count);
```

### <a name="parameters"></a>Parametry

*počet*\
Maximální počet prvků požadovaných pro přidělení paměti.

### <a name="return-value"></a>Návratová hodnota

`pair`, jehož první součást je ukazatel na přidělenou paměť a jejíž druhá součást poskytuje velikost vyrovnávací paměti, která označuje největší počet prvků, které by mohly být uloženy.

### <a name="remarks"></a>Poznámky

Funkce vytvoří požadavek na paměť a nemusí být úspěšná. Pokud není přidělena žádná vyrovnávací paměť, funkce vrátí dvojici s druhou komponentou rovnající se nule a první komponentou, která se rovná nulovému ukazateli.

Tuto funkci lze použít pouze pro paměť, která je dočasná.

### <a name="example"></a>Příklad

```cpp
// memory_get_temp_buf.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

int main( )
{
    // Create an array of ints
    int intArray [] = { 10, 20, 30, 40, 100, 200, 300, 1000, 2000 };
    int count = sizeof ( intArray ) / sizeof ( int );
    cout << "The number of integers in the array is: "
        << count << "." << endl;

    pair<int *, ptrdiff_t> resultPair;
    resultPair = get_temporary_buffer<int>( count );

    cout << "The number of elements that the allocated memory\n"
        << "could store is given by: resultPair.second = "
        << resultPair.second << "." << endl;
}
```

```Output
The number of integers in the array is: 9.
The number of elements that the allocated memory
could store is given by: resultPair.second = 9.
```

## <a name="make_shared"></a>make_shared

Vytvoří a vrátí [shared_ptr](shared-ptr-class.md) , který odkazuje na přidělené objekty, které jsou vytvořené z nuly nebo více argumentů pomocí výchozího přidělování. Přidělí a sestaví jak objekt zadaného typu, tak `shared_ptr` pro správu sdíleného vlastnictví objektu a vrátí `shared_ptr`.

```cpp
template <class T, class... Args>
shared_ptr<T> make_shared(
    Args&&... args);
```

### <a name="parameters"></a>Parametry

\ *argumentů*
Nula nebo více argumentů konstruktoru. Funkce odvodí, které přetížení konstruktoru bude vyvoláno na základě poskytnutých argumentů.

### <a name="remarks"></a>Poznámky

Použijte `make_shared` jako jednoduchý a efektivnější způsob, jak vytvořit objekt a `shared_ptr` ke správě sdíleného přístupu k objektu ve stejnou dobu. Sémanticky uvedené dva příkazy jsou ekvivalentní:

```cpp
auto sp = std::shared_ptr<Example>(new Example(argument));
auto msp = std::make_shared<Example>(argument);
```

První příkaz však vytvoří dvě přidělení a pokud přidělení `shared_ptr` selžou po úspěšném přidělení `Example` objektu, není objekt bez názvu `Example` vrácen. Příkaz, který používá `make_shared`, je jednodušší, protože je zapojeno pouze jedno volání funkce. Je efektivnější, protože knihovna může vytvořit jedno přidělení pro objekt i inteligentní ukazatel. Tato funkce je rychlejší a vede k menší fragmentaci paměti a nedochází k výjimce při jednom přidělení, ale ne k druhému. Výkon je vylepšený o lepší národní prostředí pro kód, který odkazuje na objekt a aktualizuje počty odkazů v inteligentním ukazateli.

Zvažte použití [make_unique](memory-functions.md#make_unique) , pokud nepotřebujete sdílený přístup k objektu. Pokud potřebujete zadat vlastní přidělování pro objekt, použijte [allocate_shared](memory-functions.md#allocate_shared) . `make_shared` nemůžete použít, pokud objekt vyžaduje vlastní odstranění, protože neexistuje žádný způsob, jak odstranit modul pro odstranění jako argument.

Následující příklad ukazuje, jak vytvořit sdílené odkazy na typ vyvoláním konkrétního konstruktoru přetížení.

### <a name="example"></a>Příklad

```cpp
// stl_make_shared.cpp
// Compile by using: cl /W4 /EHsc stl_make_shared.cpp
#include <iostream>
#include <string>
#include <memory>
#include <vector>

class Song {
public:
    std::wstring title_;
    std::wstring artist_;

    Song(std::wstring title, std::wstring artist) : title_(title), artist_(artist) {}
    Song(std::wstring title) : title_(title), artist_(L"Unknown") {}
};

void CreateSharedPointers()
{
    // Okay, but less efficient to have separate allocations for
    // Song object and shared_ptr control block.
    auto song = new Song(L"Ode to Joy", L"Beethoven");
    std::shared_ptr<Song> sp0(song);

    // Use make_shared function when possible. Memory for control block
    // and Song object are allocated in the same call:
    auto sp1 = std::make_shared<Song>(L"Yesterday", L"The Beatles");
    auto sp2 = std::make_shared<Song>(L"Blackbird", L"The Beatles");

    // make_shared infers which constructor to use based on the arguments.
    auto sp3 = std::make_shared<Song>(L"Greensleeves");

    // The playlist vector makes copies of the shared_ptr pointers.
    std::vector<std::shared_ptr<Song>> playlist;
    playlist.push_back(sp0);
    playlist.push_back(sp1);
    playlist.push_back(sp2);
    playlist.push_back(sp3);
    playlist.push_back(sp1);
    playlist.push_back(sp2);
    for (auto&& sp : playlist)
    {
        std::wcout << L"Playing " << sp->title_ <<
            L" by " << sp->artist_ << L", use count: " <<
            sp.use_count() << std::endl;
    }
}

int main()
{
    CreateSharedPointers();
}
```

Příklad vytvoří tento výstup:

```Output
Playing Ode to Joy by Beethoven, use count: 2
Playing Yesterday by The Beatles, use count: 3
Playing Blackbird by The Beatles, use count: 3
Playing Greensleeves by Unknown, use count: 2
Playing Yesterday by The Beatles, use count: 3
Playing Blackbird by The Beatles, use count: 3
```

## <a name="make_unique"></a>make_unique

Vytvoří a vrátí [unique_ptr](unique-ptr-class.md) objektu zadaného typu, který je vytvořen pomocí zadaných argumentů.

```cpp
// make_unique<T>
template <class T, class... Args>
unique_ptr<T> make_unique(Args&&... args);

// make_unique<T[]>
template <class T>
unique_ptr<T> make_unique(size_t size);

// make_unique<T[N]> disallowed
template <class T, class... Args>
/* unspecified */ make_unique(Args&&...) = delete;
```

### <a name="parameters"></a>Parametry

*T*\
Typ objektu, na který bude `unique_ptr` odkazovat.

\ *argumentů*
Typy argumentů konstruktoru určené *argumenty.*

\ *argumentů*
Argumenty, které mají být předány konstruktoru objektu typu *T*.

*prvky*\
Pole prvků typu *T*.

*velikost*\
Počet prvků pro přidělení prostoru v novém poli.

### <a name="remarks"></a>Poznámky

První přetížení se používá pro jednotlivé objekty. Druhé přetížení je vyvoláno pro pole. Třetí přetížení brání v určení velikosti pole v argumentu typu (make_unique\<T [N] >); Tento konstrukcí není podporován aktuálním standardem. Použijete-li `make_unique` k vytvoření `unique_ptr` pole, je nutné inicializovat prvky pole samostatně. Místo použití tohoto přetížení, možná lepší volbou je použití [std:: Vector](vector-class.md).

Vzhledem k tomu, že `make_unique` je pečlivě implementována pro bezpečnost výjimek, doporučujeme používat `make_unique` namísto přímého volání `unique_ptr` konstruktorů.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít `make_unique`. Další příklady naleznete v tématu [How to: Create and Use Unique_ptr Instances](../cpp/how-to-create-and-use-unique-ptr-instances.md).

[!code-cpp[stl_smart_pointers#214](../cpp/codesnippet/CPP/memory-functions_1.cpp)]

Když se v souvislosti s `unique_ptr`zobrazí chyba C2280, je téměř jistě, protože se pokoušíte vyvolat svůj kopírovací konstruktor, což je Odstraněná funkce.

## <a name="owner_less"></a>owner_less

Umožňuje smíšené porovnání sdílených a slabých ukazatelů na základě vlastnictví. Vrátí **hodnotu true** , pokud je levý parametr seřazen před pravým parametrem `owner_before`členské funkce.

```cpp
template <class T>
    struct owner_less; // not defined

template <class T>
struct owner_less<shared_ptr<T>>
{
    bool operator()(
        const shared_ptr<T>& left,
        const shared_ptr<T>& right) const noexcept;

    bool operator()(
        const shared_ptr<T>& left,
        const weak_ptr<T>& right) const noexcept;

    bool operator()(
        const weak_ptr<T>& left,
        const shared_ptr<T>& right) const noexcept;
};

template <class T>
struct owner_less<weak_ptr<T>>
    bool operator()(
        const weak_ptr<T>& left,
        const weak_ptr<T>& right) const noexcept;

    bool operator()(
        const weak_ptr<T>& left,
        const shared_ptr<T>& right) const noexcept;

    bool operator()(
        const shared_ptr<T>& left,
        const weak_ptr<T>& right) const noexcept;
};

template<> struct owner_less<void>
{
    template<class T, class U>
    bool operator()(
        const shared_ptr<T>& left,
        const shared_ptr<U>& right) const noexcept;

    template<class T, class U>
    bool operator()(
        const shared_ptr<T>& left,
        const weak_ptr<U>& right) const noexcept;

    template<class T, class U>
    bool operator()(
        const weak_ptr<T>& left,
        const shared_ptr<U>& right) const noexcept;

    template<class T, class U>
    bool operator()(
        const weak_ptr<T>& left,
        const weak_ptr<U>& right) const noexcept;
};
```

### <a name="parameters"></a>Parametry

*levý*\
Sdílený nebo slabý ukazatel.

*pravé*\
Sdílený nebo slabý ukazatel.

### <a name="remarks"></a>Poznámky

Šablony tříd definují všechny své členské operátory jako vrácení `left.owner_before(right)`.

## <a name="reinterpret_pointer_cast"></a>reinterpret_pointer_cast

Vytvoří nový `shared_ptr` z existujícího sdíleného ukazatele pomocí přetypování.

```cpp
template<class T, class U>
shared_ptr<T> reinterpret_pointer_cast(
    const shared_ptr<U>& ptr) noexcept;

template<class T, class U>
shared_ptr<T> reinterpret_pointer_cast(
    shared_ptr<U>&& ptr) noexcept;
```

### <a name="parameters"></a>Parametry

\ *PTR*
Odkaz na `shared_ptr<U>`.

### <a name="remarks"></a>Poznámky

Pokud je *PTR* prázdné, je nový `shared_ptr` také prázdný, jinak sdílí vlastnictví s *PTR*. Nový sdílený ukazatel je výsledkem vyhodnocení `reinterpret_cast<Y*>(ptr.get())`, kde `Y` je `typename std::shared_ptr<T>::element_type`. Chování není definováno, pokud `reinterpret_cast<T*>((U*)nullptr)` není správně vytvořen.

Funkce šablony, která přebírá odkaz lvalue, je v C++ 17 novinkou. Funkce šablony, která přebírá odkaz rvalue, je v C++ 20 novinkou.

## <a name="return_temporary_buffer"></a>return_temporary_buffer

Zruší přidělení dočasné paměti, která byla přidělena pomocí funkce šablony `get_temporary_buffer`.

```cpp
template <class T>
void return_temporary_buffer(
    T* buffer);
```

### <a name="parameters"></a>Parametry

\ *vyrovnávací paměti*
Ukazatel na paměť, která se má uvolnit

### <a name="remarks"></a>Poznámky

Tuto funkci lze použít pouze pro paměť, která je dočasná.

### <a name="example"></a>Příklad

```cpp
// memory_ret_temp_buf.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

int main( )
{
    // Create an array of ints
    int intArray [] = { 10, 20, 30, 40, 100, 200, 300 };
    int count = sizeof ( intArray ) / sizeof ( int );
    cout << "The number of integers in the array is: "
         << count << "." << endl;

    pair<int *, ptrdiff_t> resultPair;
    resultPair = get_temporary_buffer<int>( count );

    cout << "The number of elements that the allocated memory\n"
         << " could store is given by: resultPair.second = "
         << resultPair.second << "." << endl;

    int* tempBuffer = resultPair.first;

    // Deallocates memory allocated with get_temporary_buffer
    return_temporary_buffer( tempBuffer );
}
```

```Output
The number of integers in the array is: 7.
The number of elements that the allocated memory
could store is given by: resultPair.second = 7.
```

## <a name="static_pointer_cast"></a>static_pointer_cast

Statické přetypování na [shared_ptr](shared-ptr-class.md).

```cpp
template <class T, class Other>
shared_ptr<T> static_pointer_cast(
    const shared_ptr<Other>& sp) noexcept;

template <class T, class Other>
shared_ptr<T> static_pointer_cast(
    shared_ptr<Other>&& sp) noexcept;
```

### <a name="parameters"></a>Parametry

*T*\
Typ řízený vráceným sdíleným ukazatelem.

*Jiné*\
Typ řízený sdíleným ukazatelem argumentu.

\ *SP*
Sdílený ukazatel argumentu.

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí prázdný objekt `shared_ptr`, pokud je *SP* prázdný objekt `shared_ptr`; v opačném případě vrátí objekt `shared_ptr<T>`, který vlastní prostředek, který je vlastníkem *SP*. Výraz `static_cast<T*>(sp.get())` musí být platný.

### <a name="example"></a>Příklad

```cpp
// std__memory__static_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    int value;
};

struct derived
    : public base
{
};

int main()
{
    std::shared_ptr<base> sp0(new derived);
    std::shared_ptr<derived> sp1 =
        std::static_pointer_cast<derived>(sp0);

    sp0->value = 3;
    std::cout << "sp1->value == " << sp1->value << std::endl;

    return (0);
}
```

```Output
sp1->value == 3
```

## <a name="swap"></a>adresu

Proměňte dva objekty [shared_ptr](shared-ptr-class.md), [unique_ptr](unique-ptr-class.md)nebo [weak_ptr](weak-ptr-class.md) .

```cpp
template <class T>
void swap(
    shared_ptr<T>& left,
    shared_ptr<T>& right) noexcept;

template <class T, class Deleter>
void swap(
    unique_ptr<T, Deleter>& left,
    unique_ptr<T, Deleter>& right) noexcept;

template <class T>
void swap(
    weak_ptr<T>& left,
    weak_ptr<T>& right) noexcept;

```

### <a name="parameters"></a>Parametry

*T*\
Typ řízený ukazatelem argumentu.

\ *odstranění*
Odstraní se jedinečný typ ukazatele.

*levý*\
Levý ukazatel.

*pravé*\
Pravý ukazatel.

### <a name="remarks"></a>Poznámky

Funkce šablony volají `left.swap(right)`.

### <a name="example"></a>Příklad

```cpp
// std__memory__swap.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::shared_ptr<int> sp2(new int(10));
    std::cout << "*sp1 == " << *sp1 << std::endl;

    sp1.swap(sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;

    swap(sp1, sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;
    std::cout << std::endl;

    std::weak_ptr<int> wp1(sp1);
    std::weak_ptr<int> wp2(sp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    wp1.swap(wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    swap(wp1, wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    return (0);
}
```

```Output
*sp1 == 5
*sp1 == 10
*sp1 == 5

*wp1 == 5
*wp1 == 10
*wp1 == 5
```

## <a name="undeclare_no_pointers"></a>undeclare_no_pointers

Informuje uvolňování paměti, že některé znaky v bloku paměti definované ukazatelem základní adresy a velikostí bloku mohou nyní obsahovat sledovatelné ukazatele.

```cpp
void undeclare_no_pointers(
    char* ptr,
    size_t size);
```

### <a name="parameters"></a>Parametry

\ *PTR*
Ukazatel na adresu paměti dříve označený pomocí [declare_no_pointers](#declare_no_pointers).

*velikost*\
Počet bajtů v rozsahu paměti. Tato hodnota musí být stejná jako číslo použité ve volání `declare_no_pointers`.

### <a name="remarks"></a>Poznámky

Funkce informuje jakýkoliv systém uvolňování paměti, že rozsah adres `[ptr, ptr + size)` nyní může obsahovat sledovací ukazatele.

## <a name="undeclare_reachable"></a>undeclare_reachable

Odvolá deklaraci dostupnosti pro zadané umístění v paměti.

```cpp
template <class T>
T *undeclare_reachable(
    T* ptr);
```

### <a name="parameters"></a>Parametry

\ *PTR*
Ukazatel na adresu paměti dříve označený pomocí [declare_reachable](#declare_reachable).

### <a name="remarks"></a>Poznámky

Pokud *PTR* není **nullptr**, funkce informuje jakékoli uvolňování paměti, že *PTR* již není dosažitelný. Vrátí bezpečně odvozený ukazatel, který porovnává rovný a *PTR*.

## <a name="uninitialized_copy"></a>uninitialized_copy

Zkopíruje objekty ze zadaného zdrojového rozsahu do neinicializovaného cílového rozsahu.

```cpp
template <class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_copy(
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_copy(
    ExecutionPolicy&& policy,
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);
```

### <a name="parameters"></a>Parametry

\ *zásad*
Zásady spouštění, které se mají použít.

*první*\
Vstupní iterátor adresující první prvek ve zdrojovém rozsahu.

*poslední*\
Vstupní iterátor adresující poslední prvek ve zdrojovém rozsahu.

*cílový*\
Dopředný iterátor, který adresuje první prvek v cílovém rozsahu.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor, který adresuje první pozici mimo cílový rozsah, pokud zdrojový rozsah nebyl prázdný.

### <a name="remarks"></a>Poznámky

Tento algoritmus umožňuje zrušení spinové interakce přidělení paměti z konstrukce objektu.

Funkce šablony efektivně provede:

```cpp
while (first != last)
{
    new (static_cast<void*>(&* dest++))
        typename iterator_traits<InputIterator>::value_type(*first++);
}
return dest;
```

pokud kód nevyvolá výjimku. V takovém případě jsou všechny vytvořené objekty zničeny a znovu se vyvolá výjimka.

Přetížení se zásadami spouštění je v C++ 17 novinkou.

### <a name="example"></a>Příklad

```cpp
// memory_uninit_copy.cpp
// compile with: /EHsc /W3
#include <memory>
#include <iostream>

using namespace std;

class Integer
{
public:
    Integer(int x) : value(x) {}
    int get() { return value; }
private:
    int value;
};

int main()
{
    int Array[] = { 10, 20, 30, 40 };
    const int N = sizeof(Array) / sizeof(int);

    cout << "The initialized Array contains " << N << " elements: ";
    for (int i = 0; i < N; i++)
    {
        cout << " " << Array[i];
    }
    cout << endl;

    Integer* ArrayPtr = (Integer*)malloc(N * sizeof(int));
    Integer* LArrayPtr = uninitialized_copy(
        Array, Array + N, ArrayPtr);  // C4996

    cout << "Address of position after the last element in the array is: "
        << &Array[0] + N << endl;
    cout << "The iterator returned by uninitialized_copy addresses: "
        << (void*)LArrayPtr << endl;
    cout << "The address just beyond the last copied element is: "
        << (void*)(ArrayPtr + N) << endl;

    if ((&Array[0] + N) == (void*)LArrayPtr)
        cout << "The return value is an iterator "
        << "pointing just beyond the original array." << endl;
    else
        cout << "The return value is an iterator "
        << "not pointing just beyond the original array." << endl;

    if ((void*)LArrayPtr == (void*)(ArrayPtr + N))
        cout << "The return value is an iterator "
        << "pointing just beyond the copied array." << endl;
    else
        cout << "The return value is an iterator "
        << "not pointing just beyond the copied array." << endl;

    free(ArrayPtr);

    cout << "Note that the exact addresses returned will vary\n"
        << "with the memory allocation in individual computers."
        << endl;
}
```

## <a name="uninitialized_copy_n"></a>uninitialized_copy_n

Vytvoří kopii zadaného počtu prvků ze vstupního iterátoru. Kopie jsou umístěny v dopředném iterátoru.

```cpp
template <class InputIterator, class Size, class ForwardIterator>
ForwardIterator uninitialized_copy_n(
    InputIterator first,
    Size count,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class Size, class ForwardIterator>
ForwardIterator uninitialized_copy_n(
    ExecutionPolicy&& policy,
    InputIterator first,
    Size count,
    ForwardIterator dest);
```

### <a name="parameters"></a>Parametry

\ *zásad*
Zásady spouštění, které se mají použít.

*první*\
Vstupní iterátor odkazující na objekt, který chcete kopírovat.

*počet*\
Typ celého čísla se znaménkem nebo bez znaménka udávající, kolikrát se má objekt kopírovat.

*cílový*\
Dopředný iterátor odkazující na umístění nových kopií.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor adresující první pozici za cílem. Pokud byl zdrojový rozsah prázdný, iterátor adresy *napřed*.

### <a name="remarks"></a>Poznámky

Funkce šablony efektivně spustí následující kód:

```cpp
    for (; 0 < count; --count)
        new (static_cast<void*>(&* dest++))
            typename iterator_traits<InputIterator>::value_type(*first++);
    return dest;
```

pokud kód nevyvolá výjimku. V takovém případě jsou všechny vytvořené objekty zničeny a znovu se vyvolá výjimka.

Přetížení se zásadami spouštění je v C++ 17 novinkou.

## <a name="uninitialized_default_construct"></a>uninitialized_default_construct

Výchozí konstrukce objekty iterátorů `value_type` v zadaném rozsahu.

```cpp
template <class ForwardIterator>
void uninitialized_default_construct(
    ForwardIterator first,
    ForwardIterator last);

template <class ExecutionPolicy, class ForwardIterator>
void uninitialized_default_construct(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    ForwardIterator last);
```

### <a name="parameters"></a>Parametry

\ *zásad*
Zásady spouštění, které se mají použít.

*první*\
Iterátor adresující první prvek v rozsahu, který se má sestavit.

*poslední*\
Iterátor adresující jeden za poslední prvek v rozsahu, který se má sestavit.

### <a name="remarks"></a>Poznámky

Verze bez zásad spouštění je efektivně stejná jako:

```cpp
for (; first != last; ++first)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type;
```

Pokud je vyvolána výjimka, dříve vytvořené objekty jsou zničeny v nespecifikovaném pořadí.

Verze se zásadami spouštění má stejný výsledek, ale provádí se podle zadaných *zásad*.

Tyto funkce jsou v C++ 17 nové.

## <a name="uninitialized_default_construct_n"></a>uninitialized_default_construct_n

Výchozí vytvoří zadaný počet objektů `value_type`iterátoru počínaje zadaným umístěním.

```cpp
template <class ForwardIterator, class Size>
ForwardIterator uninitialized_default_construct_n(
    ForwardIterator first,
    Size count);

template <class ExecutionPolicy, class ForwardIterator, class Size>
ForwardIterator uninitialized_default_construct_n(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    Size count);
```

### <a name="parameters"></a>Parametry

\ *zásad*
Zásady spouštění, které se mají použít.

*první*\
Iterátor adresující první prvek v cílovém rozsahu, který se má sestavit.

*počet*\
Počet prvků v cílovém rozsahu, který se má sestavit.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor, který adresuje první pozici mimo cílový rozsah, pokud zdrojový rozsah nebyl prázdný.

### <a name="remarks"></a>Poznámky

Verze bez zásad spouštění je efektivně stejná jako:

```cpp
for (; count>0; (void)++first, --count)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type;
return first;
```

Pokud je vyvolána výjimka, dříve vytvořené objekty jsou zničeny v nespecifikovaném pořadí.

Verze se zásadami spouštění má stejný výsledek, ale provádí se podle zadaných *zásad*.

Tyto funkce jsou v C++ 17 nové.

## <a name="uninitialized_fill"></a>uninitialized_fill

Zkopíruje objekty ze zadané hodnoty do neinicializované cílové oblasti.

```cpp
template <class ForwardIterator, class T>
void uninitialized_fill(
    ForwardIterator first,
    ForwardIterator last,
    const T& value);

template <class ExecutionPolicy, class ForwardIterator, class T>
void uninitialized_fill(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    ForwardIterator last,
    const T& value);
```

### <a name="parameters"></a>Parametry

\ *zásad*
Zásady spouštění, které se mají použít.

*první*\
Dopředný iterátor, který adresuje první prvek v cílovém rozsahu, který se má inicializovat.

*poslední*\
Dopředný iterátor, který adresuje poslední prvek v cílovém rozsahu, který se má inicializovat.

*hodnota*\
Hodnota, která má být použita k inicializaci cílového rozsahu.

### <a name="remarks"></a>Poznámky

Tento algoritmus umožňuje zrušení spinové interakce přidělení paměti z konstrukce objektu.

Funkce šablony efektivně provede:

```cpp
while (first != last)
    new (static_cast<void*>(&* first ++))
        typename iterator_traits<ForwardIterator>::value_type (value);
```

pokud kód nevyvolá výjimku. V takovém případě jsou všechny vytvořené objekty zničeny a znovu se vyvolá výjimka.

Přetížení se zásadami spouštění je v C++ 17 novinkou.

### <a name="example"></a>Příklad

```cpp
// memory_uninit_fill.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

class Integer
{
public:
    // No default constructor
    Integer( int x ) : value( x ) {}
    int get() { return value; }
private:
    int value;
};

int main()
{
    const int N = 10;
    Integer value ( 25 );
    Integer* Array = ( Integer* ) malloc( N * sizeof( int ) );
    uninitialized_fill( Array, Array + N, value );
    cout << "The initialized Array contains: ";
    for ( int i = 0; i < N; i++ )
        {
            cout << Array[ i ].get() << " ";
        }
    cout << endl;
}
```

```Output
The initialized Array contains: 25 25 25 25 25 25 25 25 25 25
```

## <a name="uninitialized_fill_n"></a>uninitialized_fill_n

Zkopíruje objekty zadané hodnoty do zadaného počtu prvků neinicializovaného cílového rozsahu.

```cpp
template <class ForwardIterator, class Size, class T>
ForwardIterator uninitialized_fill_n(
    ForwardIterator first,
    Size count,
    const T& value);

template <class ExecutionPolicy, class ForwardIterator, class Size, class T>
ForwardIterator uninitialized_fill_n(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    Size count,
    const T& value);
```

### <a name="parameters"></a>Parametry

\ *zásad*
Zásady spouštění, které se mají použít.

*první*\
Dopředný iterátor, který adresuje první prvek v cílovém rozsahu, který se má inicializovat.

*počet*\
Počet prvků, které mají být inicializovány.

*hodnota*\
Hodnota, která se má použít k inicializaci cílového rozsahu.

### <a name="remarks"></a>Poznámky

Tento algoritmus umožňuje zrušení spinové interakce přidělení paměti z konstrukce objektu.

Funkce šablony efektivně provede:

```cpp
while (0 < count--)
    new (static_cast<void*>(&* first++))
        typename iterator_traits<ForwardIterator>::value_type(value);
return first;
```

pokud kód nevyvolá výjimku. V takovém případě jsou všechny vytvořené objekty zničeny a znovu se vyvolá výjimka.

Přetížení se zásadami spouštění je v C++ 17 novinkou.

### <a name="example"></a>Příklad

```cpp
// memory_uninit_fill_n.cpp
// compile with: /EHsc /W3
#include <memory>
#include <iostream>

using namespace std;

class Integer
{
public:
    // No default constructor
    Integer( int x ) : value( x ) {}
    int get() { return value; }
private:
    int value;
};

int main()
{
    const int N = 10;
    Integer value( 60 );
    Integer* Array = ( Integer* ) malloc( N * sizeof( int ) );
    uninitialized_fill_n( Array, N, value );  // C4996
    cout << "The uninitialized Array contains: ";
    for ( int i = 0; i < N; i++ )
        cout << Array[ i ].get() <<  " ";
}
```

## <a name="uninitialized_move"></a>uninitialized_move

Přesune elementy ze zdrojového rozsahu do neinicializované cílové oblasti paměti.

```cpp
template <class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_move(
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_move(
    ExecutionPolicy&& policy,
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);
```

### <a name="parameters"></a>Parametry

\ *zásad*
Zásady spouštění, které se mají použít.

*první*\
Vstupní iterátor adresující první prvek ve zdrojovém rozsahu, který se má přesunout.

*poslední*\
Vstupní iterátor adresující jedno za poslední prvek ve zdrojovém rozsahu, který se má přesunout.

*cílový*\
Začátek cílového rozsahu.

### <a name="remarks"></a>Poznámky

Verze bez zásad spouštění je efektivně stejná jako:

```cpp
for (; first != last; (void)++dest, ++first)
    ::new (static_cast<void*>(addressof(*dest)))
        typename iterator_traits<ForwardIterator>::value_type(std::move(*first));
return dest;
```

Pokud je vyvolána výjimka, mohou být některé objekty ve zdrojovém rozsahu ponechány v platném, ale neurčeném stavu. Dříve vytvořené objekty jsou zničeny v nespecifikovaném pořadí.

Verze se zásadami spouštění má stejný výsledek, ale provádí se podle zadaných *zásad*.

Tyto funkce jsou v C++ 17 nové.

## <a name="uninitialized_move_n"></a>uninitialized_move_n

Přesune zadaný počet prvků ze zdrojového rozsahu do neinicializované cílové oblasti paměti.

```cpp
template <class InputIterator, class Size, class ForwardIterator>
pair<InputIterator, ForwardIterator> uninitialized_move_n(
    InputIterator first,
    Size count,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class Size, class ForwardIterator>
pair<InputIterator, ForwardIterator> uninitialized_move_n(
    ExecutionPolicy&& policy,
    InputIterator first,
    Size count,
    ForwardIterator dest);
```

### <a name="parameters"></a>Parametry

\ *zásad*
Zásady spouštění, které se mají použít.

*první*\
Vstupní iterátor adresující první prvek ve zdrojovém rozsahu, který se má přesunout.

*počet*\
Počet prvků ve zdrojovém rozsahu, který chcete přesunout.

*cílový*\
Začátek cílového rozsahu.

### <a name="remarks"></a>Poznámky

Verze bez zásad spouštění je efektivně stejná jako:

```cpp
for (; count > 0; ++dest, (void) ++first, --count)
    ::new (static_cast<void*>(addressof(*dest)))
        typename iterator_traits<ForwardIterator>::value_type(std::move(*first));
return {first, dest};
```

Pokud je vyvolána výjimka, mohou být některé objekty ve zdrojovém rozsahu ponechány v platném, ale neurčeném stavu. Dříve vytvořené objekty jsou zničeny v nespecifikovaném pořadí.

Verze se zásadami spouštění má stejný výsledek, ale provádí se podle zadaných *zásad*.

Tyto funkce jsou v C++ 17 nové.

## <a name="uninitialized_value_construct"></a>uninitialized_value_construct

Vytvoří objekty iterátorů `value_type` podle inicializace hodnoty v zadaném rozsahu.

```cpp
template <class ForwardIterator>
void uninitialized_value_construct(
    ForwardIterator first,
    ForwardIterator last);

template <class ExecutionPolicy, class ForwardIterator>
void uninitialized_value_construct(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    ForwardIterator last);
```

### <a name="parameters"></a>Parametry

\ *zásad*
Zásady spouštění, které se mají použít.

*první*\
Iterátor adresující první prvek v rozsahu do hodnoty konstrukce.

*poslední*\
Iterátor adresující jedno za poslední prvek v rozsahu do hodnoty konstrukce.

### <a name="remarks"></a>Poznámky

Verze bez zásad spouštění je efektivně stejná jako:

```cpp
for (; first != last; ++first)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type();
```

Pokud je vyvolána výjimka, dříve vytvořené objekty jsou zničeny v nespecifikovaném pořadí.

Verze se zásadami spouštění má stejný výsledek, ale provádí se podle zadaných *zásad*.

Pokud dojde k chybě přidělení paměti, je vyvolána výjimka `std::bad_alloc`.

Tyto funkce jsou v C++ 17 nové.

## <a name="uninitialized_value_construct_n"></a>uninitialized_value_construct_n

Sestaví zadaný počet objektů `value_type` iterátoru podle hodnoty inicializace, počínaje zadaným umístěním.

```cpp
template <class ForwardIterator, class Size>
ForwardIterator uninitialized_value_construct_n(
    ForwardIterator first,
    Size count);

template <class ExecutionPolicy, class ForwardIterator, class Size>
ForwardIterator uninitialized_value_construct_n(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    Size count);
```

### <a name="parameters"></a>Parametry

\ *zásad*
Zásady spouštění, které se mají použít.

*první*\
Iterátor adresující první prvek v cílovém rozsahu, který se má sestavit.

*počet*\
Počet prvků v cílovém rozsahu, který se má sestavit.

### <a name="remarks"></a>Poznámky

Verze bez zásad spouštění je efektivně stejná jako:

```cpp
for (; count > 0; (void)++first, --count)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type();
return first;
```

Pokud je vyvolána výjimka, dříve vytvořené objekty jsou zničeny v nespecifikovaném pořadí.

Verze se zásadami spouštění má stejný výsledek, ale provádí se podle zadaných *zásad*.

Pokud dojde k chybě přidělení paměti, je vyvolána výjimka `std::bad_alloc`.

Tyto funkce jsou v C++ 17 nové.

## <a name="uses_allocator_v"></a>uses_allocator_v

Pomocná šablona proměnné pro přístup k hodnotě šablony `uses_allocator`.

```cpp
template <class T, class Alloc>
inline constexpr bool uses_allocator_v = uses_allocator<T, Alloc>::value;
```

## <a name="see-also"></a>Viz také

[> \<paměti](memory.md)
