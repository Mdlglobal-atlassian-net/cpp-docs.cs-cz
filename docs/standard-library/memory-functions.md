---
title: '&lt;funkce&gt; paměti'
ms.date: 02/06/2019
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
- xmemory/std::get_temporary_buffer
- memory/std::make_shared
- memory/std::make_unique
- memory/std::owner_less
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
ms.openlocfilehash: 14818e93e79a0be9960ba67088f81d51d402b717
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448495"
---
# <a name="ltmemorygt-functions"></a>&lt;funkce&gt; paměti

## <a name="addressof"></a>AddressOf

Získá adresu true objektu.

```cpp
template <class T>
    T* addressof(T& Val);
```

### <a name="parameters"></a>Parametry

*Počítává*\
Objekt nebo funkce, pro které chcete získat adresu true.

### <a name="return-value"></a>Návratová hodnota

Skutečná adresa objektu nebo funkce, na kterou odkazuje *Val*, i když `operator&()` existuje přetížený.

### <a name="remarks"></a>Poznámky

## <a name="align"></a>vztahují

Přizpůsobí úložiště určité velikosti, zarovnané danou specifikací zarovnání, do první možné adresy daného úložiště.

```cpp
void* align(
    size_t Alignment, // input
    size_t Size,      // input
    void*& Ptr,        // input/output
    size_t& Space     // input/output
);
```

### <a name="parameters"></a>Parametry

*Bod*\
Zarovnání čekající na pokus.

*Hodnota*\
Velikost v bajtech pro zarovnané úložiště.

*Střed*\
Počáteční adresa dostupného nepřetržitého fondu úložiště, který chcete použít. Tento parametr je také výstupní parametr a je nastaven tak, aby obsahoval novou počáteční adresu, pokud je zarovnání úspěšné. Pokud `align()` je neúspěšná, tento parametr se neupraví.

*Space*\
Celkové místo, které je `align()` dostupné pro použití při vytváření zarovnaného úložiště. Tento parametr je také výstupní parametr a obsahuje zbývající upravené místo ve vyrovnávací paměti úložiště po odečtení zarovnaného úložiště a veškeré přidružené režie.

Pokud `align()` je neúspěšná, tento parametr se neupraví.

### <a name="return-value"></a>Návratová hodnota

Ukazatel s hodnotou null, pokud se požadovaná zarovnaná vyrovnávací paměť nevejde do dostupného místa; v opačném případě nová hodnota *PTR*.

### <a name="remarks"></a>Poznámky

Upravené parametry *PTR* a *Space* umožňují opakované volání `align()` ve stejné vyrovnávací paměti, případně s různými hodnotami pro *Zarovnání* a *Velikost*. Následující fragment kódu ukazuje jedno použití `align()`.

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

`shared_ptr` Vytvoří objekty, které jsou přiděleny a konstruovány pro daný typ pomocí zadaného přidělování. `shared_ptr`Vrátí.

```cpp
template <class Type, class Allocator, class... Types>
    shared_ptr<Type> allocate_shared(Allocator Alloc, Types&&... Args);
```

### <a name="parameters"></a>Parametry

*Vyhrazen*\
Alokátor použitý k vytvoření objektů.

*Argumentů*\
Nula nebo více argumentů, které se stanou objekty.

### <a name="remarks"></a>Poznámky

Funkce vytvoří objekt `shared_ptr<Type>`, ukazatel na `Type(Args...)` přidělený a konstruovaný pomocí *přidělení*.

## <a name="atomic_compare_exchange_strong"></a>atomic_compare_exchange_strong

```cpp
template<class T>
    bool atomic_compare_exchange_strong(shared_ptr<T>* p, shared_ptr<T>* v, shared_ptr<T> w);
```

## <a name="atomic_compare_exchange_weak"></a>atomic_compare_exchange_weak

```cpp
template<class T>
    bool atomic_compare_exchange_weak(shared_ptr<T>* p, shared_ptr<T>* v, shared_ptr<T> w);
```

## <a name="atomic_compare_exchange_strong_explicit"></a>atomic_compare_exchange_strong_explicit

```cpp
template<class T>
    bool atomic_compare_exchange_strong_explicit(shared_ptr<T>* p, shared_ptr<T>* v, shared_ptr<T> w, memory_order success, memory_order failure);
```

## <a name="atomic_compare_exchange_weak_explicit"></a>atomic_compare_exchange_weak_explicit

```cpp
template<class T>
    bool atomic_compare_exchange_weak_explicit(shared_ptr<T>* p, shared_ptr<T>* v, shared_ptr<T> w, memory_order success, memory_order failure);
```

## <a name="atomic_exchange"></a>atomic_exchange

```cpp
template<class T>
    shared_ptr<T> atomic_exchange(shared_ptr<T>* p, shared_ptr<T> r);
```

## <a name="atomic_exchange_explicit"></a>atomic_exchange_explicit

```cpp
template<class T>
    shared_ptr<T> atomic_exchange_explicit(shared_ptr<T>* p, shared_ptr<T> r, memory_order mo);
```

## <a name="atomic_is_lock_free"></a>atomic_is_lock_free

```cpp
template<class T>
    bool atomic_is_lock_free(const shared_ptr<T>* p);
```

## <a name="atomic_load"></a>atomic_load

```cpp
template<class T>
    shared_ptr<T> atomic_load(const shared_ptr<T>* p);
```

## <a name="atomic_load_explicit"></a>atomic_load_explicit

```cpp
template<class T>
    shared_ptr<T> atomic_load_explicit(const shared_ptr<T>* p, memory_order mo);
```

## <a name="atomic_store"></a>atomic_store

```cpp
template<class T>
    void atomic_store(shared_ptr<T>* p, shared_ptr<T> r);
```

## <a name="atomic_store_explicit"></a>atomic_store_explicit

```cpp
template<class T>
    void atomic_store_explicit(shared_ptr<T>* p, shared_ptr<T> r, memory_order mo);
```

## <a name="const_pointer_cast"></a>const_pointer_cast

Const cast na shared_ptr.

```cpp
template <class Ty, class Other>
    shared_ptr<Ty> const_pointer_cast(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>Parametry

*Ty*\
Typ řízený vráceným sdíleným ukazatelem.

*Jiná*\
Typ řízený sdíleným ukazatelem argumentu.

*Jiná*\
Sdílený ukazatel argumentu.

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí prázdný objekt shared_ptr, `const_cast<Ty*>(sp.get())` Pokud vrátí ukazatel s hodnotou null; v opačném případě vrátí [shared_ptr třídu](../standard-library/shared-ptr-class.md)\<ty > objektu, který `sp`vlastní prostředek, který je vlastněn. Výraz `const_cast<Ty*>(sp.get())` musí být platný.

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
void declare_no_pointers(char* ptr, size_t _Size);
```

### <a name="parameters"></a>Parametry

*střed*\
Adresa prvního znaku, který již neobsahuje sledovací ukazatele.

*_Size*\
Velikost bloku, který začíná na *PTR* , který neobsahuje žádné zjistitelné ukazatele.

### <a name="remarks"></a>Poznámky

Funkce informuje všechny systémy uvolňování paměti, že rozsah adres `[ ptr, ptr + _Size)` již neobsahuje sledovací ukazatele. (Všechny ukazatele na přidělené úložiště se nesmí odkázat, pokud se nedají dosáhnout.)

## <a name="declare_reachable"></a>declare_reachable

Informuje uvolňování paměti, že je uvedena adresa pro přidělení úložištěm a je k dispozici.

```cpp
void declare_reachable(void* ptr);
```

### <a name="parameters"></a>Parametry

*střed*\
Ukazatel na dosažitelnou, přidělenou a platnou oblast úložiště.

### <a name="remarks"></a>Poznámky

Pokud hodnota *PTR* není null, funkce informuje všechny uvolňování paměti, které *PTR* narazí (odkazuje na platné přidělené úložiště).

## <a name="default_delete"></a>default_delete

Odstraní objekty přidělené s **operátorem New**. Vhodný pro použití s `unique_ptr`nástrojem.

```cpp
struct default_delete {
   constexpr default_delete() noexcept = default;
   template <class Other, class = typename enable_if<is_convertible<Other*, T*>::value, void>::type>>
        default_delete(const default_delete<Other>&) noexcept;
   void operator()(T* Ptr) const noexcept;
};
```

### <a name="parameters"></a>Parametry

*Střed*\
Ukazatel na objekt, který chcete odstranit.

*Jiná*\
Typ prvků v poli, který má být odstraněn.

### <a name="remarks"></a>Poznámky

Třída Template popisuje `deleter` , které odstraní skalární objekty přidělené **operátorem New**, vhodné pro použití s třídou `unique_ptr`Template. Má také explicitní specializaci `default_delete<Type[]>`.

## <a name="destroy_at"></a>destroy_at

```cpp
template <class T>
    void destroy_at(T* location);
```

Stejné jako `location->~T()`.

## <a name="destroy"></a>způsobit

```cpp
template <class ForwardIterator>
    void destroy(ForwardIterator first, ForwardIterator last);
```

Stejné jako `for (; first!=last; ++first) destroy_at(addressof(*first)); `.

## <a name="destroy_n"></a>destroy_n

```cpp
template <class ForwardIterator, class Size>
    ForwardIterator destroy_n(ForwardIterator first, Size n);
```

Stejné jako `for (; n > 0; (void)++first, --n) destroy_at(addressof(*first)); return first;`.

## <a name="dynamic_pointer_cast"></a>dynamic_pointer_cast

Dynamické přetypování na shared_ptr

```cpp
template <class Ty, class Other>
    shared_ptr<Ty> dynamic_pointer_cast(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>Parametry

*Ty*\
Typ řízený vráceným sdíleným ukazatelem.

*Jiná*\
Typ řízený sdíleným ukazatelem argumentu.

*SP*\
Sdílený ukazatel argumentu.

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí prázdný objekt shared_ptr `dynamic_cast<Ty*>(sp.get())` , pokud vrátí ukazatel s hodnotou null; v opačném případě vrátí [shared_ptr třídu](../standard-library/shared-ptr-class.md)\<ty > objektu, který vlastní prostředek, který je vlastněn *aktualizací SP*. Výraz `dynamic_cast<Ty*>(sp.get())` musí být platný.

### <a name="example"></a>Příklad

```cpp
// std__memory__dynamic_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    virtual ~base() {}
    int val;
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

    sp0->val = 3;
    std::cout << "sp1->val == " << sp1->val << std::endl;

    return (0);
}
```

```Output
sp1->val == 3
```

## <a name="get_deleter"></a>get_deleter

Získat odstranění z shared_ptr.

```cpp
template <class D, class Ty>
    D* get_deleter(const shared_ptr<Ty>& sp);
```

### <a name="parameters"></a>Parametry

*TROJROZMĚRNÉ*\
Typ odstranění.

*Ty*\
Typ řízený sdíleným ukazatelem.

*SP*\
Sdílený ukazatel.

### <a name="remarks"></a>Poznámky

Funkce šablony vrací ukazatel na odstranění typu *D* , který patří do objektu [třídy shared_ptr](../standard-library/shared-ptr-class.md) *SP*. Pokud se v *SP* neodstraní ani když jeho modul pro odstranění není typu *D* , vrátí funkce hodnotu 0.

### <a name="example"></a>Příklad

```cpp
// std__memory__get_deleter.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    int val;
};

struct deleter
{
    void operator()(base *p)
    {
        delete p;
    }
};

int main()
{
    std::shared_ptr<base> sp0(new base);

    sp0->val = 3;
    std::cout << "get_deleter(sp0) != 0 == " << std::boolalpha
        << (std::get_deleter<deleter>(sp0) != 0) << std::endl;

    std::shared_ptr<base> sp1(new base, deleter());

    sp0->val = 3;
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
pointer_safety get_pointer_safety();
```

### <a name="remarks"></a>Poznámky

Funkce vrátí typ zabezpečení ukazatele, který předpokládá jakékoli automatické uvolňování paměti.

## <a name="get_temporary_buffer"></a>get_temporary_buffer

Přidělí dočasné úložiště pro řadu prvků, která není větší než zadaný počet prvků.

```cpp
template <class Type>
    pair<Type *, ptrdiff_t> get_temporary_buffer(ptrdiff_t count);
```

### <a name="parameters"></a>Parametry

*výpočtu*\
Maximální počet prvků požadovaných pro přidělení paměti.

### <a name="return-value"></a>Návratová hodnota

`pair` Jehož první součást je ukazatel na přidělenou paměť a jejíž druhá součást poskytuje velikost vyrovnávací paměti, která označuje největší počet prvků, které by mohly být uloženy.

### <a name="remarks"></a>Poznámky

Funkce vytvoří požadavek na paměť a nemusí být úspěšná. Pokud není přidělena žádná vyrovnávací paměť, funkce vrátí dvojici s druhou komponentou rovnající se nule a první komponentou, která se rovná nulovému ukazateli.

Tato funkce by měla být použita pouze pro paměť, která je dočasná.

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
   int intArray [ ] = { 10, 20, 30, 40, 100, 200, 300, 1000, 2000 };
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

Vytváří a vrací `shared_ptr` odkazující na alokované objekty vytvořené z nuly nebo více argumentů pomocí výchozího alokátoru. Přidělí a sestaví jak objekt zadaného typu `shared_ptr` , tak pro správu sdíleného vlastnictví objektu a `shared_ptr`vrátí.

```cpp
template <class Type, class... Types>
    shared_ptr<Type> make_shared(Types&&... _Args);
```

### <a name="parameters"></a>Parametry

*_Args*\
Nula nebo více argumentů konstruktoru. Funkce odvodí, které přetížení konstruktoru bude vyvoláno na základě poskytnutých argumentů.

### <a name="remarks"></a>Poznámky

Používejte `make_shared` jako jednoduchý a efektivnější způsob, jak vytvořit objekt `shared_ptr` a ke správě sdíleného přístupu k objektu ve stejnou dobu. Sémanticky uvedené dva příkazy jsou ekvivalentní:

```cpp
auto sp = std::shared_ptr<Example>(new Example(argument));
auto msp = std::make_shared<Example>(argument);
```

První příkaz však vytvoří dvě přidělení, a pokud přidělení `shared_ptr` po úspěšném přidělení `Example` objektu dojde k chybě, není `Example` objekt bez názvu vrácen. Příkaz, který používá `make_shared` , je jednodušší, protože je zapojeno pouze jedno volání funkce. Je efektivnější, protože knihovna může vytvořit jedno přidělení pro objekt i inteligentní ukazatel. To je rychlejší a vede k menší fragmentaci paměti a nedochází k výjimce při jednom přidělení, ale ne k druhému. Výkon je vylepšený o lepší národní prostředí pro kód, který odkazuje na objekt a aktualizuje počty odkazů v inteligentním ukazateli.

Zvažte použití [make_unique](../standard-library/memory-functions.md#make_unique) , pokud nepotřebujete sdílený přístup k objektu. [Allocate_shared](../standard-library/memory-functions.md#allocate_shared) použijte, pokud potřebujete zadat vlastní přidělování pro objekt. Nemůžete `make_shared` použít, pokud objekt vyžaduje vlastní odstranění, protože neexistuje žádný způsob, jak odstranit modul pro odstranění jako argument.

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

void CreateSharedPointers() {
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
   for (auto&& sp : playlist) {
      std::wcout << L"Playing " << sp->title_ <<
         L" by " << sp->artist_ << L", use count: " <<
         sp.use_count() << std::endl;
   }
}

int main() {
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

Vytvoří a vrátí [unique_ptr](../standard-library/unique-ptr-class.md) objektu zadaného typu, který je vytvořen pomocí zadaných argumentů.

```cpp
// make_unique<T>
template <class T, class... Types>
    unique_ptr<T> make_unique(Types&&... Args)
    {
        return (unique_ptr<T>(new T(forward<Types>(Args)...)));
    }

// make_unique<T[]>
template <class T>
    make_unique(size_t Size)
    {
        return (unique_ptr<T>(new Elem[Size]()));
    }

// make_unique<T[N]> disallowed
template <class T, class... Types>
    typename enable_if<extent<T>::value != 0, void>::type make_unique(Types&&...) = delete;
```

### <a name="parameters"></a>Parametry

*Š*\
Typ objektu, na který `unique_ptr` bude odkazovat.

*Druhy*\
Typy argumentů konstruktoru určené *argumenty.*

*Argumentů*\
Argumenty, které mají být předány konstruktoru objektu typu *T*.

*Elem*\
Pole prvků typu *T*.

*Hodnota*\
Počet prvků pro přidělení prostoru v novém poli.

### <a name="remarks"></a>Poznámky

První přetížení se používá pro jednotlivé objekty, druhé přetížení je vyvoláno pro pole a třetí přetížení zabrání v určení velikosti pole v argumentu typu (make_unique\<T [N] >); Tato konstrukce není podporována aktuálním standardní. Použijete `make_unique` -li k `unique_ptr` vytvoření pro pole, je nutné inicializovat prvky pole samostatně. Pokud zvažujete toto přetížení, možná lepší volbou je použití [std:: Vector](../standard-library/vector-class.md).

Vzhledem `make_unique` k tomu, že je pečlivě implementována pro bezpečnost výjimek, `make_unique` doporučujeme použít místo přímého `unique_ptr` volání konstruktorů.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít `make_unique`. Další příklady naleznete v tématu [How to: Vytvořte a používejte instance](../cpp/how-to-create-and-use-unique-ptr-instances.md)unique_ptr.

[!code-cpp[stl_smart_pointers#214](../cpp/codesnippet/CPP/memory-functions_1.cpp)]

Když se v souvislosti s a `unique_ptr`zobrazí chyba C2280, je téměř jistě, protože se pokoušíte vyvolat svůj kopírovací konstruktor, což je Odstraněná funkce.

## <a name="owner_less"></a>owner_less

Umožňuje smíšené porovnání sdílených a slabých ukazatelů na základě vlastnictví. Vrátí **hodnotu true** , pokud je levý parametr seřazen před pravým parametrem členské `owner_before`funkce.

```cpp
template <class Type>
    struct owner_less; // not defined

template <class Type>
struct owner_less<shared_ptr<Type>> {
    bool operator()(
    const shared_ptr<Type>& left,
    const shared_ptr<Type>& right);

    bool operator()(
    const shared_ptr<Type>& left,
    const weak_ptr<Type>& right);

    bool operator()(
    const weak_ptr<Type>& left,
    const shared_ptr<Type>& right);
};

template <class Type>
struct owner_less<weak_ptr<Type>>
    bool operator()(
    const weak_ptr<Type>& left,
    const weak_ptr<Type>& right);

    bool operator()(
    const weak_ptr<Type>& left,
    const shared_ptr<Ty>& right);

    bool operator()(
    const shared_ptr<Type>& left,
    const weak_ptr<Type>& right);
};
```

### <a name="parameters"></a>Parametry

*_left*\
Sdílený nebo slabý ukazatel.

*Kliknutím*\
Sdílený nebo slabý ukazatel.

### <a name="remarks"></a>Poznámky

Třídy šablon definují všechny své členské operátory jako vracené `left.owner_before(right)`.

## <a name="return_temporary_buffer"></a>return_temporary_buffer

Zruší přidělení dočasné paměti, která byla přidělena pomocí `get_temporary_buffer` funkce šablony.

```cpp
template <class Type>
    void return_temporary_buffer(Type* _Pbuf);
```

### <a name="parameters"></a>Parametry

*_Pbuf*\
Ukazatel na paměť, která se má uvolnit

### <a name="remarks"></a>Poznámky

Tato funkce by měla být použita pouze pro paměť, která je dočasná.

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
   int intArray [ ] = { 10, 20, 30, 40, 100, 200, 300 };
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
   return_temporary_buffer ( tempBuffer );
}
```

```Output
The number of integers in the array is: 7.
The number of elements that the allocated memory
could store is given by: resultPair.second = 7.
```

## <a name="static_pointer_cast"></a>static_pointer_cast

Statické přetypování na shared_ptr.

```cpp
template <class Ty, class Other>
    shared_ptr<Ty> static_pointer_cast(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>Parametry

*Ty*\
Typ řízený vráceným sdíleným ukazatelem.

*Jiná*\
Typ řízený sdíleným ukazatelem argumentu.

*Jiná*\
Sdílený ukazatel argumentu.

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí prázdný objekt shared_ptr `sp` , pokud je prázdný `shared_ptr` objekt; v opačném případě vrátí [třídu](../standard-library/shared-ptr-class.md)\<shared_ptr pro objekt `sp`>, který vlastní prostředek, který je vlastněn. Výraz `static_cast<Ty*>(sp.get())` musí být platný.

### <a name="example"></a>Příklad

```cpp
// std__memory__static_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    int val;
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

    sp0->val = 3;
    std::cout << "sp1->val == " << sp1->val << std::endl;

    return (0);
}
```

```Output
sp1->val == 3
```

## <a name="swap"></a>adresu

Proměňte dva objekty shared_ptr nebo weak_ptr.

```cpp
template <class Ty, class Other>
    void swap(shared_ptr<Ty>& left, shared_ptr<Other>& right);

template <class Ty, class Other>
    void swap(weak_ptr<Ty>& left, weak_ptr<Other>& right);
```

### <a name="parameters"></a>Parametry

*Ty*\
Typ řízený levým sdíleným a slabým ukazatelem.

*Jiná*\
Typ řízený správným ukazatelem Shared/slabé.

*zbývá*\
Levý ukazatel Shared/slabé.

*Kliknutím*\
Pravý ukazatel Shared/slabé.

### <a name="remarks"></a>Poznámky

Funkce šablon volá `left.swap(right)`.

### <a name="example"></a>Příklad

```cpp
// std__memory__swap.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

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
void undeclare_no_pointers(char* ptr, size_t _Size);
```

### <a name="remarks"></a>Poznámky

Funkce informuje všechny uvolňování paměti, že rozsah adres `[ptr, ptr + _Size)` nyní může obsahovat sledovací ukazatele.

## <a name="undeclare_reachable"></a>undeclare_reachable

Odvolá deklaraci dostupnosti pro zadané umístění v paměti.

```cpp
template <class Type>
    Type *undeclare_reachable(Type* ptr);
```

### <a name="parameters"></a>Parametry

*střed*\
Ukazatel na adresu paměti, která má být deklarována, je nedosažitelný.

### <a name="remarks"></a>Poznámky

Pokud *PTR* není **nullptr**, funkce informuje jakékoli uvolňování paměti, že *PTR* již není dosažitelný. Vrací bezpečně odvozený ukazatel, který porovnává rovný a *PTR*.

## <a name="uninitialized_copy"></a>uninitialized_copy

Zkopíruje objekty ze zadaného zdrojového rozsahu do neinicializovaného cílového rozsahu.

```cpp
template <class InputIterator, class ForwardIterator>
    ForwardIterator uninitialized_copy(InputIterator first, InputIterator last, ForwardIterator dest);
```

### <a name="parameters"></a>Parametry

*první*\
Vstupní iterátor adresující první prvek ve zdrojovém rozsahu.

*posledního*\
Vstupní iterátor adresující poslední prvek ve zdrojovém rozsahu.

*propojovací*\
Dopředný iterátor, který adresuje první prvek v cílovém rozsahu.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor, který adresuje první pozici mimo cílový rozsah, pokud zdrojový rozsah nebyl prázdný.

### <a name="remarks"></a>Poznámky

Tento algoritmus umožňuje zrušení spinové interakce přidělení paměti z konstrukce objektu.

Funkce šablony efektivně provede:

```cpp
while (first != last) {
    new (static_cast<void*>(&* dest++))
        typename iterator_traits<InputIterator>::value_type(*first++);
}
return dest;
```

pokud kód nevyvolá výjimku. V takovém případě jsou všechny vytvořené objekty zničeny a znovu se vyvolá výjimka.

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
    Integer(int x) : val(x) {}
    int get() { return val; }
private:
    int val;
};

int main()
{
    int Array[] = { 10, 20, 30, 40 };
    const int N = sizeof(Array) / sizeof(int);

    int i;
    cout << "The initialized Array contains " << N << " elements: ";
    for (i = 0; i < N; i++)
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
```

### <a name="parameters"></a>Parametry

*první*\
Vstupní iterátor odkazující na objekt, který chcete kopírovat.

*výpočtu*\
Typ celého čísla se znaménkem nebo bez znaménka udávající, kolikrát se má objekt kopírovat.

*propojovací*\
Dopředný iterátor odkazující na umístění nových kopií.

### <a name="return-value"></a>Návratová hodnota

Dopředný iterátor adresující první pozici za cílem. Pokud byl zdrojový rozsah prázdný, iterátor adresy napřed .

### <a name="remarks"></a>Poznámky

Funkce šablony efektivně provede následující:

```cpp
    for (; 0 < count; --count)
        new (static_cast<void*>(&* dest++))
            typename iterator_traits<InputIterator>::value_type(*first++);
    return dest;
```

pokud kód nevyvolá výjimku. V takovém případě jsou všechny vytvořené objekty zničeny a znovu se vyvolá výjimka.

## <a name="uninitialized_default_construct"></a>uninitialized_default_construct

```cpp
template <class ForwardIterator>
    void uninitialized_default_construct(ForwardIterator first, ForwardIterator last); 
```

### <a name="remarks"></a>Poznámky

Stejné jako:

```cpp
for (; first != last; ++first)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type;
```

## <a name="uninitialized_default_construct_n"></a>uninitialized_default_construct_n

```cpp
template <class ForwardIterator, class Size>
    ForwardIterator uninitialized_default_construct_n(ForwardIterator first, Size n)
```

### <a name="remarks"></a>Poznámky

Stejné jako:

```cpp
for (; n>0; (void)++first, --n)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type; return first;
```

## <a name="uninitialized_fill"></a>uninitialized_fill

Zkopíruje objekty ze zadané hodnoty do neinicializované cílové oblasti.

```cpp
template <class ForwardIterator, class Type>
    void uninitialized_fill(ForwardIterator first, ForwardIterator last, const Type& val);
```

### <a name="parameters"></a>Parametry

*první*\
Dopředný iterátor, který adresuje první prvek v cílovém rozsahu, který má být zahájen.

*posledního*\
Dopředný iterátor, který adresuje poslední prvek v cílovém rozsahu, který má být zahájen.

*počítává*\
Hodnota, která má být použita k inicializaci cílového rozsahu.

### <a name="remarks"></a>Poznámky

Tento algoritmus umožňuje zrušení spinové interakce přidělení paměti z konstrukce objektu.

Funkce šablony efektivně provede:

```cpp
while (first != last)
    new (static_cast<void*>(&* first ++))
        typename iterator_traits<ForwardIterator>::value_type (val);
```

pokud kód nevyvolá výjimku. V takovém případě jsou všechny vytvořené objekty zničeny a znovu se vyvolá výjimka.

### <a name="example"></a>Příklad

```cpp
// memory_uninit_fill.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

class Integer {         // No default constructor
   public:
      Integer( int x ) : val( x ) {}
      int get( ) { return val; }
   private:
      int val;
};

int main( )
{
   const int N = 10;
   Integer val ( 25 );
   Integer* Array = ( Integer* ) malloc( N * sizeof( int ) );
   uninitialized_fill( Array, Array + N, val );
   int i;
   cout << "The initialized Array contains: ";
      for ( i = 0 ; i < N; i++ )
      {
         cout << Array [ i ].get( ) << " ";
      }
   cout << endl;
}
```

```Output
The initialized Array contains: 25 25 25 25 25 25 25 25 25 25
```

## <a name="uninitialized_fill_n"></a>uninitialized_fill_n

Zkopíruje objekty zadané hodnoty do zadaného počtu prvků do neinicializovaného cílového rozsahu.

```cpp
template <class FwdIt, class Size, class Type>
    void uninitialized_fill_n(ForwardIterator first, Size count, const Type& val);
```

### <a name="parameters"></a>Parametry

*první*\
Dopředný iterátor, který adresuje první prvek v cílovém rozsahu, který má být iniciován.

*výpočtu*\
Počet prvků, které mají být inicializovány.

*počítává*\
Hodnota, která má být použita k inicializaci cílového rozsahu.

### <a name="remarks"></a>Poznámky

Tento algoritmus umožňuje zrušení spinové interakce přidělení paměti z konstrukce objektu.

Funkce šablony efektivně provede:

```cpp
while (0 < count--)
    new (static_cast<void*>(&* first++))
        typename iterator_traits<ForwardIterator>::value_type(val);
```

pokud kód nevyvolá výjimku. V takovém případě jsou všechny vytvořené objekty zničeny a znovu se vyvolá výjimka.

### <a name="example"></a>Příklad

```cpp
// memory_uninit_fill_n.cpp
// compile with: /EHsc /W3
#include <memory>
#include <iostream>

using namespace std;

class Integer {   // No default constructor
public:
   Integer( int x ) : val( x ) {}
   int get( ) { return val; }
private:
   int val;
};

int main() {
   const int N = 10;
   Integer val ( 60 );
   Integer* Array = ( Integer* ) malloc( N * sizeof( int ) );
   uninitialized_fill_n( Array, N, val );  // C4996
   int i;
   cout << "The uninitialized Array contains: ";
   for ( i = 0 ; i < N; i++ )
      cout << Array [ i ].get( ) <<  " ";
}
```

## <a name="uninitialized_move"></a>uninitialized_move

```cpp
template <class InputIterator, class ForwardIterator>
    ForwardIterator uninitialized_move(InputIterator first, InputIterator last, ForwardIterator result); 
```

### <a name="remarks"></a>Poznámky

Stejné jako:

```cpp
for (; first != last; (void)++result, ++first)
    ::new (static_cast<void*>(addressof(*result)))
        typename iterator_traits<ForwardIterator>::value_type(std::move(*first)); 
        return result;
```

Pokud je vyvolána výjimka, mohou být některé objekty v rozsahu ponechány v platném, ale neurčeném stavu.

## <a name="uninitialized_move_n"></a>uninitialized_move_n

```cpp
template <class InputIterator, class Size, class ForwardIterator>
    pair<InputIterator, ForwardIterator> uninitialized_move_n(InputIterator first, Size n, ForwardIterator result);
```

### <a name="remarks"></a>Poznámky

Stejné jako:

```cpp
for (; n > 0; ++result, (void) ++first, --n)
    ::new (static_cast<void*>(addressof(*result)))
        typename iterator_traits<ForwardIterator>::value_type(std::move(*first)); return {first,result};
```

Pokud je vyvolána výjimka, mohou být některé objekty v rozsahu ponechány v platném, ale neurčeném stavu.

## <a name="uninitialized_value_construct"></a>uninitialized_value_construct

```cpp
template <class ForwardIterator>
    void uninitialized_value_construct(ForwardIterator first, ForwardIterator last);
```

### <a name="remarks"></a>Poznámky

Stejné jako:

```cpp
for (; first != last; ++first)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type();
```

## <a name="uninitialized_value_construct_n"></a>uninitialized_value_construct_n

```cpp
template <class ForwardIterator, class Size>
    ForwardIterator uninitialized_value_construct_n(ForwardIterator first, Size n);
```

Stejné jako:
```cpp
for (; n>0; (void)++first, --n)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type(); return first;
```

## <a name="uses_allocator_v"></a>uses_allocator_v

```cpp
template <class T, class Alloc>
    inline constexpr bool uses_allocator_v = uses_allocator<T, Alloc>::value;
```

## <a name="see-also"></a>Viz také:

[\<memory>](../standard-library/memory.md)
