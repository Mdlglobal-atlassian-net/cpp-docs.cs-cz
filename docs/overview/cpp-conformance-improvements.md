---
title: Vylepšení shody C++
ms.date: 05/18/2020
description: Jazyk Microsoft C++ v aplikaci Visual Studio směřuje k plnému dodržování standardu standardu C++ 20.
ms.technology: cpp-language
ms.openlocfilehash: c7c93de8b0e4c266290b858c76e7b34fccc0cabd
ms.sourcegitcommit: 3f91111c0350c0237fddb82766c290307f20e659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83630504"
---
# <a name="c-conformance-improvements-in-visual-studio"></a>Vylepšení shody C++ se sadou Visual Studio

Microsoft C++ zajišťuje vylepšení shody a opravy chyb v každé verzi. V tomto článku jsou uvedená vylepšení podle hlavní verze a pak podle verze. Také uvádí hlavní opravy chyb podle verze. Chcete-li přejít přímo na změny konkrétní verze, použijte seznam **v tomto článku** .

::: moniker range="vs-2019"

## <a name="conformance-improvements-in-visual-studio-2019-rtw-version-160"></a><a name="improvements_160"></a>Vylepšení shody v aplikaci Visual Studio 2019 RTW (verze 16,0)

Visual Studio 2019 RTW obsahuje následující vylepšení shody, opravy chyb a změny chování v kompilátoru Microsoft C++ (MSVC).

**Poznámka:** Funkce c++ 20 budou zpřístupněny v **`/std:c++latest`** režimu, dokud není dokončena implementace c++ 20 pro kompilátor i IntelliSense. V tomto okamžiku **`/std:c++20`** bude zaveden režim kompilátoru.

### <a name="improved-modules-support-for-templates-and-error-detection"></a>Vylepšená podpora modulů pro šablony a zjišťování chyb

Moduly jsou nyní oficiálně ve standardu C++ 20. Vylepšená podpora byla přidána v aplikaci Visual Studio 2017 verze 15,9. Další informace najdete v tématech [lepší podpora šablon a detekce chyb v modulech C++ s MSVC 2017 verze 15,9](https://devblogs.microsoft.com/cppblog/better-template-support-and-error-detection-in-c-modules-with-msvc-2017-version-15-9/).

### <a name="modified-specification-of-aggregate-type"></a>Upravená specifikace agregačního typu

Specifikace agregovaného typu se v C++ 20 změnila (viz [zakazuje agregace s uživatelsky deklarovanými konstruktory](https://wg21.link/p1008r1)). V aplikaci Visual Studio 2019 v části **`/std:c++latest`** , třída s jakýmkoli uživatelsky deklarovaným konstruktorem (například, včetně konstruktoru deklarovaného `= default` nebo `= delete` ) není agregace. Dříve pouze uživatelsky zadané konstruktory vyřadí třídu jako agregaci. Tato změna přináší další omezení způsobu, jakým lze tyto typy inicializovat.

Následující kód zkompiluje bez chyb v aplikaci Visual Studio 2017, ale vyvolává chyby C2280 a C2440 v aplikaci Visual Studio 2019 pod **`/std:c++latest`** :

```cpp
struct A
{
    A() = delete; // user-declared ctor
};

struct B
{
    B() = default; // user-declared ctor
    int i = 0;
};

A a{}; // ill-formed in C++20, previously well-formed
B b = { 1 }; // ill-formed in C++20, previously well-formed
```

### <a name="partial-support-for-operator-"></a>Částečná podpora pro`operator <=>`

[P0515R3](https://wg21.link/p0515r3) C++ 20 zavádí `<=>` obousměrný operátor porovnávání, označovaný také jako "operátor" prostorů ". Visual Studio 2019 v **`/std:c++latest`** režimu zavádí částečnou podporu pro operátor tím, že vyvolává chyby pro syntaxi, která je teď zakázaná. Například následující kód kompiluje bez chyb v aplikaci Visual Studio 2017, ale vyvolává více chyb v aplikaci Visual Studio 2019 pod **`/std:c++latest`** :

```cpp
struct S
{
    bool operator<=(const S&) const { return true; }
};

template <bool (S::*)(const S&) const>
struct U { };

int main(int argc, char** argv)
{
    U<&S::operator<=> u; // In Visual Studio 2019 raises C2039, 2065, 2146.
}
```

Chcete-li se vyhnout chybám, vložte mezeru do problematické linky před poslední ostrou závorkou: `U<&S::operator<= > u;` .

### <a name="references-to-types-with-mismatched-cv-qualifiers"></a>Odkazy na typy s neodpovídajícími kvalifikátory cv

Dřív MSVC povolen přímý odkaz na odkaz z typu s neodpovídajícími kvalifikátory cv pod nejvyšší úrovní. Tato vazba by mohla umožňovat úpravu s předpokládanými konstantními daty, na která odkazuje odkaz. Kompilátor nyní vytvoří dočasný, jak to vyžaduje standard. V aplikaci Visual Studio 2017 se následující kód zkompiluje bez upozornění. V aplikaci Visual Studio 2019 vyvolá kompilátor upozornění C4172: `<func:#1 "?PData@X@@QBEABQBXXZ"> returning address of local variable or temporary.` :

```cpp
struct X
{
    const void* const& PData() const
    {
        return _pv;
    }

    void* _pv;
};

int main()
{
    X x;
    auto p = x.PData(); // C4172
}
```

### <a name="reinterpret_cast-from-an-overloaded-function"></a>`reinterpret_cast`z přetížené funkce

Argument `reinterpret_cast` není jedním z kontextů, ve kterém je povolena adresa přetížené funkce. Následující kód zkompiluje bez chyb v aplikaci Visual Studio 2017, ale v aplikaci Visual Studio 2019 vyvolá chybu C2440: `cannot convert from 'overloaded-function' to 'fp'` :

```cpp
int f(int) { return 1; }
int f(float) { return .1f; }
using fp = int(*)(int);

int main()
{
    fp r = reinterpret_cast<fp>(&f);
}
```

Chcete-li se této chybě vyhnout, použijte povolené přetypování pro tento scénář:

```cpp
int f(int);
int f(float);
using fp = int(*)(int);

int main()
{
    fp r = static_cast<fp>(&f); // or just &f;
}
```

### <a name="lambda-closures"></a>Uzavření lambda

V jazyce C++ 14 nejsou typy uzavření lambda literály. Primárním pořadím tohoto pravidla je, že výraz lambda nesmí být přiřazen proměnné **constexpr** . Následující kód zkompiluje bez chyb v aplikaci Visual Studio 2017, ale v aplikaci Visual Studio 2019 vyvolá chybu C2127: `'l': illegal initialization of 'constexpr' entity with a non-constant expression` :

```cpp
int main()
{
    constexpr auto l = [] {}; // C2127 in VS2019
}
```

Chcete-li se této chybě vyhnout, buď odstraňte kvalifikátor **constexpr** , nebo změňte režim shody na `/std:c++17` .

### <a name="stdcreate_directory-failure-codes"></a>`std::create_directory`kódy chyb

Implementovali jsme [P1164](https://wg21.link/p1164r1) z c++ 20 nepodmíněně. Tato změna `std::create_directory` ověří, zda byl cíl již adresářem při selhání. Dříve byly všechny chyby typu ERROR_ALREADY_EXISTS přepnuly na úspěšné, ale v adresáři nebyly vytvořeny.

### `operator<<(std::ostream, nullptr_t)`

Za [LWG 2221](https://cplusplus.github.io/LWG/issue2221)bylo přidáno `operator<<(std::ostream, nullptr_t)` pro zápis nullptr do datových proudů.

### <a name="additional-parallel-algorithms"></a>Další paralelní algoritmy

Nové paralelní verze systémů `is_sorted` , `is_sorted_until` , `is_partitioned` , `set_difference` , `set_intersection` , a `is_heap` `is_heap_until` .

### <a name="atomic-initialization"></a>atomická inicializace

[P0883 "Oprava atomické inicializace"](https://wg21.link/p0883r1) `std::atomic` se změní na hodnotu-Initialized (nepoužívá se) místo výchozí inicializace. Oprava je povolena při použití Clang/LLVM s standardní knihovnou společnosti Microsoft. V současné době je zakázána pro kompilátor jazyka Microsoft C++ jako alternativní řešení chyby při zpracování **constexpr** .

### <a name="remove_cvref-and-remove_cvref_t"></a>`remove_cvref` a `remove_cvref_t`

Byly implementovány `remove_cvref` `remove_cvref_t` vlastnosti typu a z [P0550](https://wg21.link/p0550r2). Tyto odebrány reference-Ness a CV-kvalifikace z typu bez selhání funkcí a polí do ukazatelů (na rozdíl od `std::decay` a `std::decay_t` ).

### <a name="feature-test-macros"></a>Makra pro testování funkcí

[Makra P0941R2-Feature-test](https://wg21.link/p0941r2) jsou dokončená s podporou pro `__has_cpp_attribute` . Makra pro testování funkcí jsou podporovaná ve všech režimech Standard.

### <a name="prohibit-aggregates-with-user-declared-constructors"></a>Zakázat agregace s uživatelsky deklarovanými konstruktory

[C++ 20 P1008R1 – zakázání agregací s uživatelsky deklarovanými konstruktory](https://wg21.link/p1008r1) je dokončeno.

## <a name="conformance-improvements-in-161"></a><a name="improvements_161"></a>Vylepšení shody v 16,1

### <a name="char8_t"></a>char8_t

[P0482r6](https://wg21.link/p0482r6). C++ 20 přidá nový typ znaku, který se používá k reprezentaci jednotek kódu v kódování UTF-8. `u8`řetězcové literály v C++ 20 mají typ `const char8_t[N]` místo `const char[N]` , což byl případ dřív. V [N2231](https://wg14.link/n2231)se navrhly podobné změny pro Standard C. Návrhy na `char8_t` nápravu zpětné kompatibility jsou uvedené v [P1423r3](https://wg21.link/p1423r3). Kompilátor jazyka Microsoft C++ přidá podporu pro `char8_t` v aplikaci Visual Studio 2019 verze 16,1 při zadání **`/Zc:char8_t`** Možnosti kompilátoru. V budoucnu bude podporován s [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) , což může být vráceno na chování c++ 17 prostřednictvím **`/Zc:char8_t-`** . Kompilátor EDG pro technologii IntelliSense ho ještě nepodporuje, takže uvidíte jenom chyby spurious IntelliSense, které nemají vliv na skutečnou kompilaci.

#### <a name="example"></a>Příklad

```cpp
const char* s = u8"Hello"; // C++17
const char8_t* s = u8"Hello"; // C++20
```

### <a name="stdtype_identity-metafunction-and-stdidentity-function-object"></a>std:: type_identity metafunkcí a std:: identity – objekt funkce

[P0887R1 type_identity](https://wg21.link/p0887r1). Vystaralá `std::identity` přípona šablony třídy se odebrala a nahradila se `std::type_identity` metafunkcí `std::identity` objektem funkce c++ 20. Obě jsou k dispozici pouze v rámci [/std: c + + nejnovější](../build/reference/std-specify-language-standard-version.md).

Následující příklad vytvoří upozornění na vyřazení C4996 pro `std::identity` (definované v \<> type_traits) v aplikaci Visual Studio 2017:

```cpp
#include <type_traits>

using T = std::identity<int>::type;
T x, y = std::identity<T>{}(x);
int i = 42;
long j = std::identity<long>{}(i);
```

Následující příklad ukazuje, jak použít nový `std::identity` (definovaný ve \< funkční>) společně s novým `std::type_identity` :

```cpp
#include <type_traits>
#include <functional>

using T = std::type_identity<int>::type;
T x, y = std::identity{}(x);
int i = 42;
long j = static_cast<long>(i);
```

### <a name="syntax-checks-for-generic-lambdas"></a>Kontroly syntaxe pro obecné výrazy lambda

Nový procesor lambda umožňuje v obecných výrazech lambda v části [/std: c + + nejnovější](../build/reference/std-specify-language-standard-version.md) nebo v jakémkoli jiném jazykovém režimu s pomocí používat některé syntaktické kontroly shody **`/experimental:newLambdaProcessor`** .

V aplikaci Visual Studio 2017 je tento kód zkompilován bez upozornění, ale v aplikaci Visual Studio 2019 vytvoří chybu C2760 `syntax error: unexpected token '\<id-expr>', expected 'id-expression'` :

```cpp
void f() {
    auto a = [](auto arg) {
        decltype(arg)::Type t;
    };
}
```

Následující příklad ukazuje správnou syntaxi, nyní vynutil kompilátor:

```cpp
void f() {
    auto a = [](auto arg) {
        typename decltype(arg)::Type t;
    };
}
```

### <a name="argument-dependent-lookup-for-function-calls"></a>Vyhledávání závislých na argumentech pro volání funkcí

[P0846R0](https://wg21.link/p0846r0) (c++ 20) zvýšila se schopnost najít šablony funkcí prostřednictvím vyhledávání závislého na argumentu pro výrazy volání funkce s explicitními argumenty šablony. Vyžaduje **`/std:c++latest`** .

### <a name="designated-initialization"></a>Určená inicializace

[P0329R4](https://wg21.link/p0329r4) (c++ 20) určená inicializace umožňuje vybrat konkrétní členy v agregační inicializaci pomocí `Type t { .member = expr }` syntaxe. Vyžaduje **`/std:c++latest`** .

### <a name="new-and-updated-standard-library-functions-c20"></a>Nové a aktualizované funkce standardní knihovny (C++ 20)

- `starts_with()`a `ends_with()` pro `basic_string` a `basic_string_view` .
- `contains()` pro asociativní kontejnery.
- `remove()`, `remove_if()` a `unique()` pro `list` a `forward_list` teď vrací `size_type`.
- `shift_left()`a `shift_right()` přidány do \< algoritmu>.

## <a name="conformance-improvements-in-162"></a><a name="improvements_162"></a>Vylepšení shody v 16,2

### <a name="noexcept-constexpr-functions"></a>s výjimkou funkcí constexpr

Funkce constexpr již nejsou považovány za, **s výjimkou** standardně při použití v konstantním výrazu. Tato změna chování přichází z řešení [CWG 1351](https://wg21.link/cwg1351) a je povolená v [/Permissive-](../build/reference/permissive-standards-conformance.md). Následující příklad kompiluje v aplikaci Visual Studio 2019 verze 16,1 a starší, ale vytváří C2338 v aplikaci Visual Studio 2019 verze 16,2:

```cpp
constexpr int f() { return 0; }

int main() {
    static_assert(noexcept(f()), "f should be noexcept"); // C2338 in 16.2
}
```

Chcete-li chybu opravit, přidejte do deklarace funkce výraz **s výjimkou** :

```cpp
constexpr int f() noexcept { return 0; }

int main() {
    static_assert(noexcept(f()), "f should be noexcept");
}
```

### <a name="binary-expressions-with-different-enum-types"></a>Binární výrazy s různými typy výčtů

Možnost použít pro operandy běžné aritmetické převody, kde jeden je výčtový typ a druhý je jiný typ výčtu nebo typ s plovoucí desetinnou čárkou, je zastaralá v C++ 20 ([P1120R0](https://wg21.link/p1120r0)).

V aplikaci Visual Studio 2019 verze 16,2 a novější následující kód vytvoří upozornění úrovně 4, pokud je povolená možnost [/std: c + + nejnovější](../build/reference/std-specify-language-standard-version.md) kompilátor:

```cpp
enum E1 { a };
enum E2 { b };
int main() {
    int i = a | b; // warning C5054: operator '|': deprecated between enumerations of different types
}
```

Chcete-li se vyhnout upozornění, použijte [static_cast](../cpp/static-cast-operator.md) k převedení druhého operandu:

```cpp
enum E1 { a };
enum E2 { b };
int main() {
  int i = a | static_cast<int>(b);
}
```

Použití binární operace mezi výčtem a typem s plovoucí desetinnou čárkou je nyní upozornění, když [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) je možnost kompilátoru povolena:

```cpp
enum E1 { a };
int main() {
  double i = a * 1.1;
}
```

Chcete-li se vyhnout upozornění, použijte [static_cast](../cpp/static-cast-operator.md) k převedení druhého operandu:

```cpp
enum E1 { a };
int main() {
   double i = static_cast<int>(a) * 1.1;
}
```

### <a name="equality-and-relational-comparisons-of-arrays"></a>Rovnost a relační porovnání polí

Rovnost a relační porovnání mezi dvěma operandy typu pole jsou zastaralé v C++ 20 ([P1120R0](https://wg21.link/p1120r0)). Jinými slovy, operace porovnání dvou polí (navzdory pořadí a podobnosti rozsahu) je nyní upozornění. Počínaje verzí Visual Studio 2019 verze 16,2 následující kód vytvoří C5056: `operator '==': deprecated for array types` když je povolená možnost [/std: c + + nejnovější](../build/reference/std-specify-language-standard-version.md) kompilátor:

```cpp
int main() {
    int a[] = { 1, 2, 3 };
    int b[] = { 1, 2, 3 };
    if (a == b) { return 1; }
}
```

Chcete-li se vyhnout upozornění, můžete porovnat adresy prvních prvků:

```cpp
int main() {
    int a[] = { 1, 2, 3 };
    int b[] = { 1, 2, 3 };
    if (&a[0] == &b[0]) { return 1; }
}
```

Chcete-li určit, zda je obsah dvou polí stejný, použijte funkci [std:: EQUAL](../standard-library/algorithm-functions.md#equal) :

```cpp
std::equal(std::begin(a), std::end(a), std::begin(b), std::end(b));
```

### <a name="effect-of-defining-spaceship-operator-on--and-"></a>Efekt definování operátoru pro vytváření mezer na `==` a`!=`

Definice operátoru kosmického přiP1185R2ho **`<=>`** výrazu () už nebude přepisovat výrazy týkající se **`==`** nebo, **`!=`** Pokud operátor prostorového využití není označený jako **`= default`** ([P1185R2](https://wg21.link/p1185r2)). Následující příklad kompiluje v aplikaci Visual Studio 2019 RTW a verze 16,1, ale vytváří C2678 v aplikaci Visual Studio 2019 verze 16,2:

```cpp
#include <compare>

struct S {
  int a;
  auto operator<=>(const S& rhs) const {
    return a <=> rhs.a;
  }
};
bool eq(const S& lhs, const S& rhs) {
  return lhs == rhs;
}
bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs;
}
```

Chcete-li se této chybě vyhnout, definujte operátor = = nebo ho deklarujte jako výchozí:

```cpp
#include <compare>

struct S {
  int a;
  auto operator<=>(const S& rhs) const {
    return a <=> rhs.a;
  }
  bool operator==(const S&) const = default;
};
bool eq(const S& lhs, const S& rhs) {
  return lhs == rhs;
}
bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs;
}
```

### <a name="standard-library-improvements"></a>Vylepšení standardní knihovny

- \<charconv> `to_chars()` s pevnou/vědeckou přesností. (Obecná přesnost je aktuálně plánována pro 16,4.)
- [P0020R6](https://wg21.link/p0020r6): atomic \< float>, atomická \< Dvojitá>, atomická \< dlouhá dvojitá>
- [P0463R1](https://wg21.link/p0463r1): endian
- [P0482R6](https://wg21.link/p0482r6): podpora knihovny pro char8_t
- [P0600R1](https://wg21.link/p0600r1): [ \[ Zrušit zahození]] pro STL, část 1
- [P0653R2](https://wg21.link/p0653r2): to_address ()
- [P0754R2](https://wg21.link/p0754r2): \< verze>
- [P0771R1](https://wg21.link/p0771r1): s výjimkou konstruktoru Move std:: Function

## <a name="conformance-improvements-in-visual-studio-2019-version-163"></a><a name="improvements_163"></a>Vylepšení shody v aplikaci Visual Studio 2019 verze 16,3

### <a name="stream-extraction-operators-for-char-removed"></a>Odebrané operátory extrakce streamu pro char *

Operátory extrakce streamu pro ukazatele na znaky se odebraly a nahradily operátory extrakce pro pole znaků (na [P0487R1](https://wg21.link/p0487r1)). WG21 považuje odebrané přetížení za nebezpečné. V [/std: c + + nejnovější](../build/reference/std-specify-language-standard-version.md) režim teď následující příklad vytvoří C2679: `binary '>>': no operator found which takes a right-hand operand of type 'char*' (or there is no acceptable conversion)` :

```cpp
   char x[42];
   char* p = x;
   std::cin >> std::setw(42);
   std::cin >> p;
```

Chcete-li se vyhnout této chybě, použijte operátor extrakce s proměnnou Char []:

```cpp
char x[42];
std::cin >> x;
```

### <a name="new-keywords-requires-and-concept"></a>Nová klíčová slova **`requires`** a**`concept`**

Nová klíčová slova **`requires`** a **`concept`** byla přidána do kompilátoru Microsoft C++. Pokud se pokusíte použít buď jednu jako identifikátor v [/std: c + + nejnovější](../build/reference/std-specify-language-standard-version.md) režim, kompilátor vyvolá C2059: `syntax error` .

### <a name="constructors-as-type-names-disallowed"></a>Konstruktory jako názvy typů nejsou povoleny.

Názvy konstruktorů se už nepovažují za vložené – názvy tříd, když se objeví v kvalifikovaném názvu za aliasem pro specializaci šablony třídy. Dřív umožnila použití konstruktorů jako názvu typu k deklaraci jiných entit. Následující příklad nyní vytvoří C3646: `'TotalDuration': unknown override specifier` :

```cpp
#include <chrono>

class Foo {
   std::chrono::milliseconds::duration TotalDuration{};
};

```

Chcete-li se této chybě vyhnout, deklarujte, `TotalDuration` jak je znázorněno zde:

```cpp
#include <chrono>

class Foo {
  std::chrono::milliseconds TotalDuration {};
};
```

### <a name="stricter-checking-of-extern-c-functions"></a>Přísnější kontrola `extern "C"` funkcí

Pokud **`extern "C"`** byla funkce deklarována v různých oborech názvů, předchozí verze kompilátoru Microsoft C++ nezkontrolovaly, zda deklarace byly kompatibilní. V aplikaci Visual Studio 2019 verze 16,3 kompilátor provede takovou kontrolu. V [`/permissive-`](../build/reference/permissive-standards-conformance.md) režimu generuje následující kód chyby C2371 `redefinition; different basic types` a C2733 `you cannot overload a function with C linkage` :

```cpp
using BOOL = int;

namespace N
{
   extern "C" void f(int, int, int, bool);
}

void g()
{
   N::f(0, 1, 2, false);
}

extern "C" void f(int, int, int, BOOL){}
```

Chcete-li se vyhnout chybám v předchozím příkladu, použijte **`bool`** místo `BOOL` konzistentní v obou deklaracích `f` .

### <a name="standard-library-improvements"></a>Vylepšení standardní knihovny

Nestandardní hlavičky \< stdexcpt. h> a \< TypeInfo. h> byly odebrány. Kód, který obsahuje, by měl místo toho zahrnovat standardní hlavičky \< exception> a \< TypeInfo>, v uvedeném pořadí.

## <a name="conformance-improvements-in-visual-studio-2019-version-164"></a><a name="improvements_164"></a>Vylepšení shody v aplikaci Visual Studio 2019 verze 16,4

### <a name="better-enforcement-of-two-phase-name-lookup-for-qualified-ids-in-permissive-"></a>Lepší vynucování dvou fází vyhledávání názvů pro kvalifikované identifikátory v`/permissive-`

Dvoustupňové vyhledávání názvů vyžaduje, aby se nezávisle používané názvy v subjektech šablony zobrazovaly v šabloně v době definice. Dříve se tyto názvy mohly najít při vytváření instance šablony. Tato změna usnadňuje zápis přenositelného a vyhovujícího kódu v MSVC pod [`/permissive-`](../build/reference/permissive-standards-conformance.md) vlajkou.

V sadě Visual Studio 2019 verze 16,4 s **`/permissive-`** nastaveným příznakem vyvolá následující příklad chybu, protože `N::f` není zobrazena, je-li `f<T>` Šablona definována:

```cpp
template <class T>
int f() {
    return N::f() + T{}; // error C2039: 'f': is not a member of 'N'
}

namespace N {
    int f() { return 42; }
}
```

Tato chyba se obvykle dá opravit zahrnutím chybějících hlaviček nebo předávajících funkcí nebo proměnných, jak je znázorněno v následujícím příkladu:

```cpp
namespace N {
    int f();
}

template <class T>
int f() {
    return N::f() + T{};
}

namespace N {
    int f() { return 42; }
}
```

### <a name="implicit-conversion-of-integral-constant-expressions-to-null-pointer"></a>Implicitní převod celočíselných konstantních výrazů na ukazatel s hodnotou null

Kompilátor MSVC nyní implementuje [CWG problém 903](https://wg21.link/cwg903) v režimu shoda ( **`/permissive-`** ). Toto pravidlo nepovoluje implicitní převod integrálních konstantních výrazů (s výjimkou celočíselného literálu 0) na konstanty ukazatele s hodnotou null. Následující příklad vytvoří C2440 v režimu shody:

```cpp
int* f(bool* p) {
    p = false; // error C2440: '=': cannot convert from 'bool' to 'bool *'
    p = 0; // OK
    return false; // error C2440: 'return': cannot convert from 'bool' to 'int *'
}
```

Chcete-li chybu opravit, použijte **nullptr** místo **false**. Literál 0 je stále povolen:

```cpp
int* f(bool* p) {
    p = nullptr; // OK
    p = 0; // OK
    return nullptr; // OK
}
```

### <a name="standard-rules-for-types-of-integer-literals"></a>Standardní pravidla pro typy literálů Integer

V režimu shoda (povolený pomocí [`/permissive-`](../build/reference/permissive-standards-conformance.md) ) MSVC používá standardní pravidla pro typy literálů Integer. Desítkové literály jsou moc velké, aby se vešly do přihlášeného **`int`** typu. dřív byl daný typ **`unsigned int`** . Těmto literálům se teď dává další největší typ signed integer, **`long long`** . Navíc literály s příponou "je příliš velká, aby se vešly do typu se znaménkem" jsou předány typu **`unsigned long long`** .

Tato změna může vést k vygenerování jiné diagnostiky upozornění a rozdíly v chování pro aritmetické operace s literály.

Následující příklad ukazuje nové chování v aplikaci Visual Studio 2019 verze 16,4. `i`Proměnná je nyní typu **`unsigned int`** . To je důvod, proč je vyvoláno upozornění. Horního řádu bitů proměnné `j` jsou nastaveny na hodnotu 0.

```cpp
void f(int r) {
    int i = 2964557531; // warning C4309: truncation of constant value
    long long j = 0x8000000000000000ll >> r; // literal is now unsigned, shift will fill high-order bits with 0
}
```

Následující příklad ukazuje, jak zachovat staré chování a vyhnout se změně chování při spuštění:

```cpp
void f(int r) {
int i = 2964557531u; // OK
long long j = (long long)0x8000000000000000ll >> r; // shift will keep high-order bits
}
```

### <a name="function-parameters-that-shadow-template-parameters"></a>Parametry funkce, které parametry šablony stínových šablon

Kompilátor MSVC nyní vyvolá chybu, když parametr funkce Stínuje parametr šablony:

```cpp
template<typename T>
void f(T* buffer, int size, int& size_read);

template<typename T, int Size>
void f(T(&buffer)[Size], int& Size) // error C7576: declaration of 'Size' shadows a template parameter
{
    return f(buffer, Size, Size);
}
```

Chcete-li chybu opravit, změňte název jednoho z parametrů:

```cpp
template<typename T>
void f(T* buffer, int size, int& size_read);

template<typename T, int Size>
void f(T (&buffer)[Size], int& size_read)
{
    return f(buffer, Size, size_read);
}
```

### <a name="user-provided-specializations-of-type-traits"></a>Uživatelsky zadané specializace typů vlastností

V souladu s podklauzulí *meta. Rqmts* Standard, kompilátor MSVC nyní vyvolá chybu, pokud narazí na uživatelsky definovanou specializaci jedné ze zadaných `type_traits` šablon v `std` oboru názvů. Pokud není uvedeno jinak, Tyto specializace mají za následek nedefinované chování. Následující příklad má nedefinované chování, protože je v rozporu s pravidlem a `static_assert` dojde k chybě C2338.

```cpp
#include <type_traits>
struct S;

template<>
struct std::is_fundamental<S> : std::true_type {};

static_assert(std::is_fundamental<S>::value, "fail");
```

Chcete-li se této chybě vyhnout, definujte strukturu, která dědí z preferovaného `type_trait` a specializace:

```cpp
#include <type_traits>

struct S;

template<typename T>
struct my_is_fundamental : std::is_fundamental<T> {};

template<>
struct my_is_fundamental<S> : std::true_type { };

static_assert(my_is_fundamental<S>::value, "fail");
```

### <a name="changes-to-compiler-provided-comparison-operators"></a>Změny relačních operátorů poskytnutých kompilátorem

Kompilátor MSVC nyní implementuje následující změny relačních operátorů na [P1630R1](https://wg21.link/p1630r1) , pokud [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) je možnost povolena:

Kompilátor již nepřepisuje výrazy pomocí `operator==` , pokud obsahují návratový typ, který není typu **bool**. Následující kód nyní vytvoří chybu C2088: `'!=': illegal for struct` :

```cpp
struct U {
    operator bool() const;
};

struct S {
    U operator==(const S&) const;
};

bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs;
}
```

Chcete-li se této chybě vyhnout, je nutné explicitně definovat potřebný operátor:

```cpp
struct U {
    operator bool() const;
};

struct S {
    U operator==(const S&) const;
    U operator!=(const S&) const;
};

bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs;
}
```

Kompilátor již nedefinuje výchozí relační operátor, pokud je členem třídy typu Union. Následující příklad nyní vytvoří chybu C2120: `'void' illegal with all types` :

```cpp
#include <compare>

union S {
    int a;
    char b;
    auto operator<=>(const S&) const = default;
};

bool lt(const S& lhs, const S& rhs) {
    return lhs < rhs;
}
```

Chcete-li se této chybě vyhnout, definujte tělo pro operátor:

```cpp
#include <compare>

union S {
    int a;
    char b;
    auto operator<=>(const S&) const { ... }
};

bool lt(const S& lhs, const S& rhs) {
    return lhs < rhs;
}
```

Kompilátor již nebude definovat výchozí relační operátor, pokud třída obsahuje odkazový člen. Následující kód nyní vytvoří chybu C2120: `'void' illegal with all types` :

```cpp
#include <compare>

struct U {
    int& a;
    auto operator<=>(const U&) const = default;
};

bool lt(const U& lhs, const U& rhs) {
    return lhs < rhs;
}
```

Chcete-li se této chybě vyhnout, definujte tělo pro operátor:

```cpp
#include <compare>

struct U {
    int& a;
    auto operator<=>(const U&) const { ... };
};

bool lt(const U& lhs, const U& rhs) {
    return lhs < rhs;
}
```

## <a name="conformance-improvements-in-visual-studio-2019-version-165"></a><a name="improvements_165"></a>Vylepšení shody v aplikaci Visual Studio 2019 verze 16,5

### <a name="explicit-specialization-declaration-without-an-initializer-isnt-a-definition"></a>Explicitní deklarace specializace bez inicializátoru není definicí.

V rámci `/permissive-` MSVC nyní vynutilo standardní pravidlo, že explicitní deklarace specializace bez inicializátorů nejsou definice. Dřív by deklarace byla považována za definici s výchozím inicializátorem. Účinek je v době propojování pozorovatelný, protože program v závislosti na tomto chování teď může mít nevyřešené symboly. V tomto příkladu teď dojde k chybě:

```cpp
template <typename> struct S {
    static int a;
};

// In permissive-, this declaration isn't a definition, and the program won't link.
template <> int S<char>::a;

int main() {
    return S<char>::a;
}
```

```Output
error LNK2019: unresolved external symbol "public: static int S<char>::a" (?a@?$S@D@@2HA) referenced in function _main
at link time.
```

Chcete-li tento problém vyřešit, přidejte inicializátor:

```cpp
template <typename> struct S {
    static int a;
};

// Add an initializer for the declaration to be a definition.
template <> int S<char>::a{};

int main() {
    return S<char>::a;
}
```

### <a name="preprocessor-output-preserves-newlines"></a>Výstup preprocesoru zachovává newlines

Experimentální preprocesor nyní zachovává newlines a prázdné znaky při použití `/P` nebo `/E` s `/experimental:preprocessor` . Tato změna se dá zakázat pomocí `/d1experimental:preprocessor:oldWhitespace` .

V tomto ukázkovém zdroji,

```cpp
#define m()
line m(
) line
```

Předchozí výstup `/E` :

```Output
line line
#line 2
```

Nový výstup aplikace `/E` je nyní:

```Output
line
 line
```

### <a name="import-and-module-keywords-are-context-dependent"></a>Klíčová slova import a Module jsou závislá na kontextu.

Za P1857R1, direktivy preprocesoru a moduly preprocesoru mají další omezení na jejich syntaxi. Tento příklad již není zkompilován:

```cpp
import // Invalid
m;
```

Vytvoří se tato chybová zpráva:

```Output
error C2146: syntax error: missing ';' before identifier 'm'
```

Chcete-li tento problém vyřešit, zachovejte import na stejném řádku:

```cpp
import m; // OK
```

### <a name="removal-of-stdweak_equality-and-stdstrong_equality"></a>Odebrání std:: weak_equality a std:: strong_equality

Sloučení P1959R0 vyžaduje, aby kompilátor odebral chování a odkazy na `std::weak_equality` `std::strong_equality` typy a.

Kód v tomto příkladu již není zkompilován:

```cpp
#include <compare>

struct S {
    std::strong_equality operator<=>(const S&) const = default;
};

void f() {
    nullptr<=>nullptr;
    &f <=> &f;
    &S::operator<=> <=> &S::operator<=>;
}
```

Tento příklad nyní vede k těmto chybám:

```Output
error C2039: 'strong_equality': is not a member of 'std'
error C2143: syntax error: missing ';' before '<=>'
error C4430: missing type specifier - int assumed. Note: C++ does not support default-int
error C4430: missing type specifier - int assumed. Note: C++ does not support default-int
error C7546: binary operator '<=>': unsupported operand types 'nullptr' and 'nullptr'
error C7546: binary operator '<=>': unsupported operand types 'void (__cdecl *)(void)' and 'void (__cdecl *)(void)'
error C7546: binary operator '<=>': unsupported operand types 'int (__thiscall S::* )(const S &) const' and 'int (__thiscall S::* )(const S &) const'
```

Chcete-li problém vyřešit, aktualizujte, aby dávaly předdefinované relační operátory a nahradily odebrané typy:

```cpp
#include <compare>

struct S {
    std::strong_ordering operator<=>(const S&) const = default; // prefer 'std::strong_ordering'
};

void f() {
    nullptr != nullptr; // use pre-existing builtin operator != or ==.
    &f != &f;
    &S::operator<=> != &S::operator<=>;
}
```

### <a name="tls-guard-changes"></a>Změny ochrany TLS Guard

Předtím byly proměnné místního vlákna v knihovnách DLL nesprávně inicializovány před prvním použitím na vláknech, které existovaly před nahráním knihovny DLL, kromě vlákna, které knihovnu DLL načetla. Tato vada se teď opravila.
Proměnné místního vlákna v takové knihovně DLL jsou inicializovány bezprostředně před prvním použitím v takových vláknech.

Toto nové chování při testování pro inicializaci na použití proměnných místních vláken může být zakázáno pomocí `/Zc:tlsGuards-` přepínače kompilátoru. Nebo, přidáním `[[msvc:no_tls_guard]]` atributu pro konkrétní Thread Local proměnné.

### <a name="better-diagnosis-of-call-to-deleted-functions"></a>Lepší diagnóza volání odstraněných funkcí

Náš kompilátor byl více opravňující o volání odstraněných funkcí dříve. Například pokud volání proběhla v kontextu těla šablony, nemůžeme diagnostikovat volání. Kromě toho, pokud došlo k několika instancím volání odstraněných funkcí, vydáváme jenom jednu diagnostiku. Teď pro každý z nich vydáváme diagnostiku.

Jedním z důsledků nového chování může být vytvoření malé zásadní změny: kód, který volal odstraněnou funkci, by nebyl diagnostikován, pokud nebyl nikdy pro generování kódu potřebný. Nyní Diagnostikujte IT vpřed.

Tento příklad ukazuje kód, který teď vytvoří chybu:

```cpp
struct S {
  S() = delete;
  S(int) { }
};

struct U {
  U() = delete;
  U(int i): s{ i } { }

  S s{};
};

U u{ 0 };
```

```Output
error C2280: 'S::S(void)': attempting to reference a deleted function
note: see declaration of 'S::S'
note: 'S::S(void)': function was explicitly deleted
```

Chcete-li tento problém vyřešit, odeberte volání odstraněných funkcí:

```cpp
struct S {
  S() = delete;
  S(int) { }
};

struct U {
  U() = delete;
  U(int i): s{ i } { }

  S s;  // Do not call the deleted ctor of 'S'.
};

U u{ 0 };
```

## <a name="conformance-improvements-in-visual-studio-2019-version-166"></a><a name="improvements_166"></a>Vylepšení shody v aplikaci Visual Studio 2019 verze 16,6

### <a name="standard-library-streams-reject-insertions-of-mis-encoded-character-types"></a>Proudy standardních knihoven odmítnou vkládání nešifrovaných typů znaků

Tradičně vložením `wchar_t` do a `std::ostream` vložením `char16_t` nebo `char32_t` do `std::ostream` nebo vytvoří `std::wostream` výstup své integrální hodnoty. Vložení ukazatelů na tyto typy znaků vypíše hodnotu ukazatele. Programátoři nenaleznou žádné případy intuitivní. Často očekávají standardní knihovnu, aby převedla znak nebo řetězec znaků zakončený hodnotou null a vyvedl výstup výsledku.

Návrh C++ 20 [P1423R3](https://wg21.link/p1423r3) přidává k těmto kombinacím typů datových proudů a znaků nebo ukazatelů znaků odstraněné přetížení operátoru vložení datového proudu. V rámci jsou **`/std:c++latest`** přetížení tato vložení nesprávně vytvořená, namísto toho, aby se chovala v tom, co je pravděpodobný neúmyslný způsob. Kompilátor vyvolá chybu C2280, když se nalezne. Můžete definovat makro "řídicí šrafování", aby `_HAS_STREAM_INSERTION_OPERATORS_DELETED_IN_CXX20` se `1` obnovilo původní chování. (Návrh také odstraní operátory vkládání datových proudů pro `char8_t` . Naše standardní knihovna implementovala podobná přetížení, když jsme přidali `char8_t` podporu, takže chování "nesprávné" nebylo nikdy k dispozici pro `char8_t` .)

V této ukázce se zobrazuje chování s touto změnou:

```cpp
#include <iostream>
int main() {
    const wchar_t cw = L'x', *pw = L"meow";
    const char16_t c16 = u'x', *p16 = u"meow";
    const char32_t c32 = U'x', *p32 = U"meow";
    std::cout << cw << ' ' << pw << '\n';
    std::cout << c16 << ' ' << p16 << '\n';
    std::cout << c32 << ' ' << p32 << '\n';
    std::wcout << c16 << ' ' << p16 << '\n';
    std::wcout << c32 << ' ' << p32 << '\n';
}
```

Kód nyní vytváří tyto diagnostické zprávy:

```Output
error C2280: 'std::basic_ostream<char,std::char_traits<char>> &std::<<<std::char_traits<char>>(std::basic_ostream<char,std::char_traits<char>> &,wchar_t)': attempting to reference a deleted function
error C2280: 'std::basic_ostream<char,std::char_traits<char>> &std::<<<std::char_traits<char>>(std::basic_ostream<char,std::char_traits<char>> &,char16_t)': attempting to reference a deleted function
error C2280: 'std::basic_ostream<char,std::char_traits<char>> &std::<<<std::char_traits<char>>(std::basic_ostream<char,std::char_traits<char>> &,char32_t)': attempting to reference a deleted function
error C2280: 'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::<<<std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,char16_t)': attempting to reference a deleted function
error C2280: 'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::<<<std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,char32_t)': attempting to reference a deleted function
```

Můžete dosáhnout účinku starého chování ve všech jazykových režimech převodem typů znaků na `unsigned int` typy, nebo ukazatelů na typ znaku na `const void*` :

```c++
#include <iostream>
int main() {
    const wchar_t cw = L'x', *pw = L"meow";
    const char16_t c16 = u'x', *p16 = u"meow";
    const char32_t c32 = U'x', *p32 = U"meow";
    std::cout << (unsigned)cw << ' ' << (const void*)pw << '\n'; // Outputs "120 0052B1C0"
    std::cout << (unsigned)c16 << ' ' << (const void*)p16 << '\n'; // Outputs "120 0052B1CC"
    std::cout << (unsigned)c32 << ' ' << (const void*)p32 << '\n'; // Outputs "120 0052B1D8"
    std::wcout << (unsigned)c16 << ' ' << (const void*)p16 << '\n'; // Outputs "120 0052B1CC"
    std::wcout << (unsigned)c32 << ' ' << (const void*)p32 << '\n'; // Outputs "120 0052B1D8"
}
```

### <a name="changed-return-type-of-stdpow-for-stdcomplex"></a>Změněný návratový typ `std::pow()` pro`std::complex`

Dříve byla implementace MSVC pravidla povýšení pro návratový typ šablony funkce `std::pow()` nesprávná. Například dříve `pow(complex<float>, int)` vráceno `complex<float>` . Nyní správně vrátí `complex<double>` . Oprava byla pro všechny režimy standardů v aplikaci Visual Studio 2019 verze 16,6 bezpodmínečně implementována.

Tato změna může způsobit chyby kompilátoru. Dříve jste například mohli vynásobit `pow(complex<float>, int)` **`float`** . Protože `complex<T> operator*` očekává argumenty stejného typu, následující příklad nyní vygeneruje chybu kompilátoru C2676: `binary '*': 'std::complex<double>' does not define this operator or a conversion to a type acceptable to the predefined operator` :

```cpp
// pow_error.cpp
// compile by using: cl /EHsc /nologo /W4 pow_error.cpp
#include <complex>

int main() {
    std::complex<float> cf(2.0f, 0.0f);
    (void) (std::pow(cf, -1) * 3.0f);
}
```

Existuje mnoho možných oprav:

- Změňte typ **`float`** multiplicand na **`double`** . Tento argument lze převést přímo na `complex<double>` typ tak, aby odpovídal typu, který `pow` vrátil.

- Zužte výsledek `pow` pro `complex<float>` podle vyslovení `complex<float>{pow(ARG, ARG)}` . Pak můžete pokračovat vynásobením **`float`** hodnotou.

- Předat **`float`** místo **`int`** do `pow` . Tato operace může být pomalejší.

- V některých případech se můžete vyhnout `pow` zcela. Například `pow(cf, -1)` lze nahradit pomocí dělení.

### <a name="switch-related-warnings-for-c"></a>Upozornění související s přepínači pro C

Počínaje verzí Visual Studio 2019 verze 16,6 kompilátor implementuje některá dříve existující upozornění jazyka C++ pro kód kompilovaný jako C. Následující upozornění jsou teď povolená na různých úrovních: C4060, C4061, C4062, C4063, C4064, C4065, C4808 a C4809. Upozornění C4065 a C4060 jsou ve výchozím nastavení v jazyce C zakázaná.

Upozornění se aktivují u chybějících **`case`** příkazů, nedefinovaných **`enum`** a špatných **`bool`** přepínačů (tj. těch, které obsahují příliš mnoho případů). Například:

```c
#include <stdbool.h>

int main() {
    bool b = true;
    switch (b) {
        case true: break;
        case false: break;
        default: break; // C4809: switch statement has redundant 'default' label;
                        // all possible 'case' labels are given
    }
}
```

Chcete-li tento kód opravit, odeberte redundantní **`default`** případ:

```c
#include <stdbool.h>

int main() {
    bool b = true;
    switch (b) {
        case true: break;
        case false: break;
    }
}
```

### <a name="unnamed-classes-in-typedef-declarations"></a>Nepojmenované třídy v `typedef` deklaracích

Počínaje verzí Visual Studio 2019 16,6 bylo chování `typedef` deklarací omezeno na [P1766R1](https://wg21.link/P1766R1). V této aktualizaci nejmenované třídy v rámci `typedef` deklarace nemohou mít jiné členy než:

- nestatické datové členy,
- třídy členů,
- výčty členů,
- a výchozí Inicializátory členů.

Stejná omezení se aplikují rekurzivně na každou vnořenou třídu. Omezení je určeno k zajištění jednoduchosti struktur, které mají `typedef` názvy pro účely propojení. Musí být dostatečně snadné, aby žádné výpočty propojení nemusely být před tím, než se kompilátor přiřadí k `typedef` názvu pro propojení.

Tato změna ovlivní všechny režimy standardů kompilátoru. Ve výchozím nastavení ( **`/std:c++14`** ) a v **`/std:c++17`** režimech generuje kompilátor upozornění C5208 pro nevyhovující kód. **`/permissive-`** Je-li parametr zadán, kompilátor vygeneruje upozornění C5208 jako chybu v **`/std:c++14`** a generuje chybu C7626 v rámci **`/std:c++17`** . Kompilátor generuje při zadání nevyhovujícího kódu chybu C7626 **`/std:c++latest`** .

Následující příklad ukazuje konstrukce, které již nejsou povoleny v nepojmenovaných strukturách. V závislosti na zadaném režimu standardů jsou generovány chyby nebo upozornění C5208 nebo C7626:

```cpp
struct B { };
typedef struct : B { // inheriting from 'B'; ill-formed
    void f(); // ill-formed
    static int i; // ill-formed
    struct U {
        void f(); // nested class has non-data member; ill-formed
    };
    int j = 10; // default member initializer; ill-formed
} S;
```

Výše uvedený kód se dá opravit tak, že se Nepojmenovaná Třída uvede název:

```cpp
struct B { };
typedef struct S_ : B {
    void f();
    static int i;
    struct U {
        void f();
    };
    int j = 10;
} S;
```

### <a name="default-argument-import-in-ccli"></a>Import výchozího argumentu v jazyce C++/CLI

Z důvodu rostoucího počtu rozhraní API, které mají výchozí argumenty v rozhraní .NET Core, teď podporujeme výchozí import argumentů v jazyce C++/CLI. Tato změna může přerušit existující kód, kde je deklarováno více přetížení, jako v tomto příkladu:

```cpp
public class R {
    public void Func(string s) {}   // overload 1
    public void Func(string s, string s2 = "") {} // overload 2;
}
```

Pokud je tato třída importována do jazyka C++/CLI, volání jednoho z přetížení způsobuje chybu:

```cpp
    (gcnew R)->Func("abc"); // error C2668: 'R::Func' ambiguous call to overloaded function
```

Kompilátor generuje chybu C2668, protože obě přetížení odpovídají tomuto seznamu argumentů. Ve druhém přetížení je druhý argument vyplněn výchozím argumentem. Chcete-li tento problém obejít, můžete odstranit redundantní přetížení (1). Nebo použijte úplný seznam argumentů a explicitně zadejte výchozí argumenty.

## <a name="bug-fixes-and-behavior-changes-in-visual-studio-2019"></a><a name="update_160"></a>Opravy chyb a změny chování v aplikaci Visual Studio 2019

### <a name="reinterpret_cast-in-a-constexpr-function"></a>Reinterpret_cast ve funkci constexpr

Ve funkci **constexpr** je **reinterpret_cast** neplatný. Kompilátor jazyka Microsoft C++ dříve zamítl **reinterpret_cast** pouze v případě, že byl použit v kontextu **constexpr** . V aplikaci Visual Studio 2019 ve všech režimech jazykových standardů kompilátor správně diagnostikuje **reinterpret_cast** v definici funkce **constexpr** . Následující kód teď vytvoří C3615: `constexpr function 'f' cannot result in a constant expression` .

```cpp
long long i = 0;
constexpr void f() {
    int* a = reinterpret_cast<int*>(i);
}
```

Chcete-li se této chybě vyhnout, odeberte modifikátor **constexpr** z deklarace funkce.

### <a name="correct-diagnostics-for-basic_string-range-constructor"></a>Oprava diagnostiky pro konstruktor rozsahu basic_string

V aplikaci Visual Studio 2019 `basic_string` konstruktor rozsahu již potlačuje diagnostiku kompilátoru pomocí `static_cast` . Následující kód zkompiluje bez upozornění v aplikaci Visual Studio 2017, navzdory možné ztrátě dat z `wchar_t` na **char** při inicializaci `out` :

```cpp
std::wstring ws = /* … */;
std::string out(ws.begin(), ws.end());
```

Visual Studio 2019 správně vyvolává Upozornění C4244: `'argument': conversion from 'wchar_t' to 'const _Elem', possible loss of data` . Chcete-li se vyhnout upozornění, můžete inicializovat std:: String, jak je znázorněno v následujícím příkladu:

```cpp
std::wstring ws = L"Hello world";
std::string out;
for (wchar_t ch : ws)
{
    out.push_back(static_cast<char>(ch));
}
```

### <a name="incorrect-calls-to--and---under-clr-or-zw-are-now-correctly-detected"></a>Jsou teď správně zjištěna nesprávná volání + = a-= v rámci/CLR nebo/ZW.

V aplikaci Visual Studio 2017 byla zjištěna chyba, která způsobila, že kompilátor tiše ignoruje chyby a negeneruje žádný kód pro neplatná volání + = a-= v rámci `/clr` nebo `/ZW` . Následující kód zkompiluje bez chyb v aplikaci Visual Studio 2017, ale v aplikaci Visual Studio 2019 správně vyvolává chybu C2845: `'System::String ^': pointer arithmetic not allowed on this type` :

```cpp
public enum class E { e };

void f(System::String ^s)
{
    s += E::e; // C2845 in VS2019
}
```

Chcete-li se vyhnout chybě v tomto příkladu, použijte operátor s metodou ToString (): `s += E::e.ToString();` .

### <a name="initializers-for-inline-static-data-members"></a>Inicializátory pro vložené statické datové členy

V rámci **vložených** a **statických** inicializátorů constexpr se teď správně zjistily neplatné přístupy členů. Následující příklad zkompiluje bez chyb v aplikaci Visual Studio 2017, ale v aplikaci Visual Studio 2019 v **`/std:c++17`** režimu vyvolá chybu C2248: `cannot access private member declared in class 'X'` .

```cpp
struct X
{
    private:
        static inline const int c = 1000;
};

struct Y : X
{
    static inline int d = c; // C2248 in Visual Studio 2019
};
```

Chcete-li se vyhnout této chybě, deklarujte člena `X::c` jako chráněného:

```cpp
struct X
{
    protected:
        static inline const int c = 1000;
};
```

### <a name="c4800-reinstated"></a>C4800 obnoveno

MSVC používá k upozornění výkonu C4800 implicitního převodu na **bool**. Bylo příliš vysoké a nedalo se ho potlačit, protože nám ho můžete odebrat v aplikaci Visual Studio 2017. V průběhu životního cyklu sady Visual Studio 2017 ale máme spoustu názoru na užitečné případy, které vyhodnotila. Vrátíme se do sady Visual Studio 2019 pečlivě přizpůsobených C4800 spolu s vysvětlujícím C4165. Obě tato upozornění lze snadno potlačit: buď pomocí explicitního přetypování, nebo porovnáním s 0 z příslušného typu. C4800 je nestandardní upozornění na úrovni 4 a C4165 je upozornění na úroveň 3 ve výchozím nastavení. Obě jsou Zjistitelnější pomocí `/Wall` Možnosti kompilátoru.

Následující příklad vyvolává C4800 a C4165 pod `/Wall` :

```cpp
bool test(IUnknown* p)
{
    bool valid = p; // warning C4800: Implicit conversion from 'IUnknown*' to bool. Possible information loss
    IDispatch* d = nullptr;
    HRESULT hr = p->QueryInterface(__uuidof(IDispatch), reinterpret_cast<void**>(&d));
    return hr; // warning C4165: 'HRESULT' is being converted to 'bool'; are you sure this is what you want?
}
```

Chcete-li se vyhnout varováním v předchozím příkladu, můžete napsat kód takto:

```cpp
bool test(IUnknown* p)
{
    bool valid = p != nullptr; // OK
    IDispatch* d = nullptr;
    HRESULT hr = p->QueryInterface(__uuidof(IDispatch), reinterpret_cast<void**>(&d));
    return SUCCEEDED(hr);  // OK
}
```

### <a name="local-class-member-function-doesnt-have-a-body"></a>Členská funkce lokální třídy nemá tělo.

V sadě Visual Studio 2017 se upozornění C4822: `Local class member function doesn't have a body` vyvolá pouze v případě `/w14822` , že je explicitně nastavena možnost kompilátoru. Není zobrazen s `/Wall` . V sadě Visual Studio 2019 je C4822 ve výchozím nastavení upozornění, které umožňuje zjistitelnost `/Wall` bez nutnosti `/w14822` explicitně nastavit.

```cpp
void example()
{
    struct A
        {
            int boo(); // warning C4822
        };
}
```

### <a name="function-template-bodies-containing-constexpr-if-statements"></a>Těla šablony funkce obsahující příkazy constexpr if

Tělo funkce šablony obsahující, pokud jsou v příkazech **constexpr** povoleny některé kontroly související s analýzou [/Permissive-](../build/reference/permissive-standards-conformance.md) . Například v sadě Visual Studio 2017 následující kód generuje C7510: `'Type': use of dependent type name must be prefixed with 'typename'` pouze pokud **`/permissive-`** možnost není nastavena. V sadě Visual Studio 2019 stejný kód vyvolává chyby i v případě, že **`/permissive-`** je nastavena možnost:

```cpp
template <typename T>

int f()
{
    T::Type a; // error C7510

    if constexpr (T::val)
    {
        return 1;
    }
    else
    {
        return 2;
    }
}

struct X
{
    using Type = X;
    constexpr static int val = 1;
};

int main()
{
    return f<X>();
}
```

Chcete-li se této chybě vyhnout, přidejte klíčové slovo **TypeName** do deklarace `a` : `typename T::Type a;` .

### <a name="inline-assembly-code-isnt-supported-in-a-lambda-expression"></a>Kód vloženého sestavení není podporován ve výrazu lambda.

Tým Microsoft C++ se nedávno dozvěděl o potížích se zabezpečením, kdy použití vloženého assembleru v rámci výrazu lambda by mohlo vést k poškození `ebp` (registraci návratové adresy) za běhu. Škodlivý útočník by mohl využít tento scénář. Inline assembler je podporován pouze v x86 a interakce mezi vloženým assemblerem a zbytkem kompilátoru je špatná. Vzhledem k těmto skutečnostem a povaze problému bylo nejbezpečnější řešení tohoto problému, které zakazuje vloženému assembleru v rámci výrazu lambda.

Jediné použití vloženého assembleru v rámci výrazu lambda, který jsme našli na zástupný, bylo zachytit zpáteční adresu. V tomto scénáři můžete zachytit zpáteční adresu na všech platformách jednoduše pomocí vnitřního kompilátoru `_ReturnAddress()` .

Následující kód vytvoří C7552: `inline assembler is not supported in a lambda` v aplikaci Visual studio 2017 15,9 i v aplikaci Visual Studio 2019:

```cpp
#include <cstdio>

int f()
{
    int y = 1724;
    int x = 0xdeadbeef;

    auto lambda = [&]
    {
        __asm {

            mov eax, x
            mov y, eax
        }
    };

    lambda();
    return y;
}
```

Chcete-li se této chybě vyhnout, přesuňte kód sestavení do pojmenované funkce, jak je znázorněno v následujícím příkladu:

```cpp
#include <cstdio>

void g(int& x, int& y)
{
    __asm {
        mov eax, x
        mov y, eax
    }
}

int f()
{
    int y = 1724;
    int x = 0xdeadbeef;
    auto lambda = [&]
    {
        g(x, y);
    };
    lambda();
    return y;
}

int main()
{
    std::printf("%d\n", f());
}
```

### <a name="iterator-debugging-and-stdmove_iterator"></a>Ladění iterátoru a`std::move_iterator`

Funkce ladění iterátoru byla výuková k řádnému rozbalení `std::move_iterator` . `std::copy(std::move_iterator<std::vector<int>::iterator>, std::move_iterator<std::vector<int>::iterator>, int*)`Teď může například `memcpy` rychlá cesta začít.

### <a name="fixes-for-xkeycheckh-keyword-enforcement"></a>Opravy pro \< xkeycheck. h> vynucování klíčového slova

Makro standardní knihovny nahrazující klíčové slovo vynucení \< xkeycheck. h> bylo opraveno tak, aby bylo vygenerováno skutečné klíčové slovo problému, nikoli obecná zpráva. Podporuje také klíčová slova C++ 20 a vyhnout se přehlasům IntelliSense při vyslovení náhodných klíčových slov jsou makra.

### <a name="allocator-types-no-longer-deprecated"></a>Typy přidělování už nejsou zastaralé.

`std::allocator<void>`, `std::allocator::size_type` a `std::allocator::difference_type` již nejsou zastaralé.

### <a name="correct-warning-for-narrowing-string-conversions"></a>Správné upozornění pro zúžené převody řetězců

Odebrali jste spurious `static_cast` z `std::string` , který se pro standard nevolal, a náhodně potlačila C4244 upozornění. Pokusy o volání `std::string::string(const wchar_t*, const wchar_t*)` nyní budou správně Generovat C4244 `narrowing a wchar_t into a char` .

### <a name="various-filesystem-correctness-fixes"></a>Různé \< opravy správnosti> systému souborů

- `std::filesystem::last_write_time`Při pokusu o změnu času posledního zápisu v adresáři se nezdařila aktualizace.
- V `std::filesystem::directory_entry` konstruktoru nyní je uložen neúspěšný výsledek, namísto vyvolání výjimky, pokud byla zadána neexistující cílová cesta.
- `std::filesystem::create_directory`Verze 2-parametru byla změněna tak, aby volala verzi 1 parametru, protože podkladová `CreateDirectoryExW` funkce by používala `copy_symlink` při `existing_p` symlink.
- `std::filesystem::directory_iterator`Po nalezení poškozeného symlink již neproběhne.
- `std::filesystem::space`nyní přijímá relativní cesty.
- `std::filesystem::path::lexically_relative`již není zaměňována koncovými lomítky, které jsou hlášeny jako [LWG 3096](https://cplusplus.github.io/LWG/issue3096).
- Pracovalo kolem `CreateSymbolicLinkW` odmítání cest s lomítkem v `std::filesystem::create_symlink` .
- Pracovala se kolem funkce režimu odstranění POSIX `delete` , která existovala ve Windows 10 LTSB 1609, ale nedala by ve skutečnosti odstraňovat soubory.
- `std::boyer_moore_searcher`a kopírovací `std::boyer_moore_horspool_searcher` konstruktory a operátory přiřazení pro kopírování teď kopírují věci.

### <a name="parallel-algorithms-on-windows-8-and-later"></a>Paralelní algoritmy ve Windows 8 a novějších verzích

Knihovna paralelních algoritmů teď používá skutečnou `WaitOnAddress` rodinu v systému Windows 8 a novějším, místo toho, aby vždycky používala Windows 7 a starší falešné verze.

### <a name="stdsystem_categorymessage-whitespace"></a>`std::system_category::message()`typy

`std::system_category::message()`nyní ořízne v vrácené zprávě koncovou mezeru.

### <a name="stdlinear_congruential_engine-divide-by-zero"></a>`std::linear_congruential_engine`dělení nulou

Některé podmínky, které by mohly způsobit, že by `std::linear_congruential_engine` se aktivovaly dělení 0, byly opraveny.

### <a name="fixes-for-iterator-unwrapping"></a>Opravy pro rozbalení iterátoru

Některá zařízení pro odbalení iterátoru byla poprvé vystavena pro integraci programátora a uživatele v sadě Visual Studio 2017 15,8, jak je popsáno v článku článek o týmu v jazyce C++ [funkce STL a opravy v sadě VS 2017 15,8](https://devblogs.microsoft.com/cppblog/stl-features-and-fixes-in-vs-2017-15-8/). Tato strojní zařízení již nadále nebalí iterátory odvozené ze standardních iterátorů knihovny. Například uživatel, který je odvozen z `std::vector<int>::iterator` a pokus o přizpůsobení chování, nyní získá vlastní chování při volání algoritmů standardní knihovny, nikoli chování ukazatele.

Neuspořádaná funkce kontejneru `reserve` nyní vyhrazuje pro N prvků, jak je popsáno v [LWG 2156](https://cplusplus.github.io/LWG/issue2156).

### <a name="time-handling"></a>Zpracování času

- Dříve některé časové hodnoty, které byly předány do knihovny souběžnosti, by byly přetečení například `condition_variable::wait_for(seconds::max())` . Nyní se nahodilé změny nazměnily na zdánlivě náhodný cyklus (při uint32_t milisekund přijatých základními rozhraními Win32 API přetečení).

- \<Hlavička> CTime – nyní správně deklaruje `timespec` a `timespec_get` v oboru názvů `std` , kromě toho, že je deklarována v globálním oboru názvů.

### <a name="various-fixes-for-containers"></a>Různé opravy pro kontejnery

- Mnoho interních kontejnerových funkcí standardní knihovny bylo pro vylepšené prostředí IntelliSense navázáno jako soukromé. Další opravy, které označují členy jako soukromé, jsou v pozdějších verzích MSVC očekávány.

- Problémy s chybou správnosti zabezpečení při rozbalení kontejnerů založených na uzlech `list` , jako jsou, `map` a `unordered_map` by mohly být poškozené. Během `propagate_on_container_copy_assignment` operace nebo `propagate_on_container_move_assignment` opětovného přiřazení jsme uvolnili uzel Sentinel kontejneru k starému přidělování, provedete přiřazení POCCA/POCMA přes starý Alokátor a pak se pokusíte získat ověřovací uzel z nového přidělování. Pokud toto přidělení neproběhlo úspěšně, kontejner byl poškozen a nemohl být ani zničen, protože vlastnící uzel Sentinel je invariantní struktura pevné datové struktury. Tento kód byl opraven pro přidělení nového uzlu Sentinel od přidělování zdrojového kontejneru před zničením stávajícího uzlu Sentinel.

- Kontejnery byly vyřešeny tak, aby vždy kopírovaly/přesunuly nebo přehozeny přidělování podle `propagate_on_container_copy_assignment` , `propagate_on_container_move_assignment` a `propagate_on_container_swap` i pro přihlášené přidělování `is_always_equal` .

- Přidání přetížení pro sloučení kontejnerů a extrakce členských funkcí, které přijímají kontejnery rvalue na [P0083 "spojování map a sad"](https://wg21.link/p0083r3) za sekundu "

### <a name="stdbasic_istreamread-processing-of-rn--n"></a>`std::basic_istream::read`zpracování \\ r \\ n => \\ n

`std::basic_istream::read`byla opravena, aby dočasně nepsala do částí poskytnuté vyrovnávací paměti jako součást \\ r \\ n => \\ n zpracování. Tato změna poskytuje některé z výhod výkonu, které byly získány v aplikaci Visual Studio 2017 15,8 pro čtení větší než 4K velikost. Nicméně jsou stále k dispozici vylepšení efektivity zabraňující třem virtuálním voláním na jeden znak.

### <a name="stdbitset-constructor"></a>`std::bitset`BeginRequestEventArgs

`std::bitset`Konstruktor již nenačítá ty a nuly v obráceném pořadí pro velké Bitsets.

### <a name="stdpairoperator-regression"></a>`std::pair::operator=`nevýhody

Opravili jsme operátor přiřazení regrese v `std::pair` případě, že se implementuje [LWG 2729. chybějící SFINAE na std::p Air:: operator = ";](https://cplusplus.github.io/LWG/issue2729). Nyní správně přijímá typy převoditelné na typ `std::pair` .

### <a name="non-deduced-contexts-for-add_const_t"></a>Neodvozený kontext pro`add_const_t`

Opravili jsme chybu vedlejších vlastností typu, kde `add_const_t` a související funkce by měly být neodvozený kontext. Jinými slovy `add_const_t` by měl být alias pro `typename add_const<T>::type` , nikoli `const T` .

## <a name="bug-fixes-and-behavior-changes-in-162"></a><a name="update_162"></a>Opravy chyb a změny chování v 16,2

### <a name="const-comparators-for-associative-containers"></a>Const komparátorů pro asociativní kontejnery

Kód pro hledání a vložení v [Nastavení](../standard-library/set-class.md), [mapování](../standard-library/map-class.md), [multiset](../standard-library/multiset-class.md)a [multimap](../standard-library/multimap-class.md) byl sloučen za účelem snížení velikosti kódu. Operace vložení nyní volají méně než porovnání u funktor porovnání **const** stejným způsobem, jako jste předtím provedli operace hledání. Následující kód je zkompilován v aplikaci Visual Studio 2019 verze 16,1 a starší, ale vyvolává C3848 v aplikaci Visual Studio 2019 verze 16,2:

```cpp
#include <iostream>
#include <map>

using namespace std;

struct K
{
   int a;
   string b = "label";
};

struct Comparer  {
   bool operator() (K a, K b) {
      return a.a < b.a;
   }
};

map<K, double, Comparer> m;

K const s1{1};
K const s2{2};
K const s3{3};

int main() {

   m.emplace(s1, 1.08);
   m.emplace(s2, 3.14);
   m.emplace(s3, 5.21);

}
```

Chcete-li se této chybě vyhnout, udělejte operátor porovnání **const**:

```cpp
struct Comparer  {
   bool operator() (K a, K b) const {
      return a.a < b.a;
   }
};

```

::: moniker-end

::: moniker range="vs-2017"

## <a name="conformance-improvements-in-visual-studio-2017-rtw-version-150"></a><a name="improvements_150"></a>Vylepšení shody v aplikaci Visual Studio 2017 RTW (verze 15,0)

S podporou pro zobecněnou inicializaci **constexpr** a nestatických inicializací datových členů (NSDMI) pro agregace je kompilátor Microsoft C++ v aplikaci Visual Studio 2017 nyní dokončen pro funkce přidané v standardu C++ 14. Nicméně kompilátor stále nemá několik funkcí z standardů C++ 11 a C++ 98. Tabulku, která ukazuje aktuální stav kompilátoru, najdete v [tabulce pro shodu jazyka Microsoft C++](../visual-cpp-language-conformance.md) .

### <a name="c11-expression-sfinae-support-in-more-libraries"></a>C++ 11: podpora výrazu SFINAE ve více knihovnách

Kompilátor i nadále vylepšuje podporu pro Expression SFINAE. Vyžaduje se pro odvození argumentu šablony a nahrazení, kde se výrazy **decltype** a **constexpr** můžou objevit jako parametry šablony. Další informace najdete v tématu [vylepšení SFINAE výrazů v aplikaci Visual Studio 2017 RC](https://blogs.msdn.microsoft.com/vcblog/2016/06/07/expression-sfinae-improvements-in-vs-2015-update-3).

### <a name="c14-nsdmi-for-aggregates"></a>C++ 14: NSDMI pro agregace

Agregace je pole nebo třída bez uživatelsky zadaného konstruktoru, žádné soukromé nebo chráněné nestatické datové členy, žádné základní třídy ani žádné virtuální funkce. Počínaje verzí C++ 14 mohou agregace obsahovat inicializátory členů. Další informace naleznete v tématu [Inicializátory členů a agregace](https://wg21.link/n3605).

### <a name="c14-extended-constexpr"></a>C++ 14: rozšířený **constexpr**

Výrazy deklarované jako **constexpr** mají nyní povoleno obsahovat určité druhy deklarací, if a Switch příkazy, smyčky a mutace objektů, jejichž doba života začala v rámci vyhodnocení výrazu constexpr. Již není nutné, aby byla nestatická členská funkce **constexpr** implicitně **const**. Další informace naleznete v tématu [požadavků Constraints on constexpr Functions](https://wg21.link/n3652).

### <a name="c17-terse-static_assert"></a>C++ 17: stručný`static_assert`

parametr zprávy pro `static_assert` je nepovinný. Další informace najdete v tématu [rozšíření static_assert v2](https://wg21.link/n3928).

### <a name="c17-fallthrough-attribute"></a>C++ 17: `[[fallthrough]]` atribut

V **`/std:c++17`** režimu `[[fallthrough]]` lze atribut použít v kontextu příkazů Switch jako pomocný parametr kompilátoru, který je určen pro chování při průchodu. Tento atribut brání kompilátoru v vydávání upozornění v takových případech. Další informace naleznete v tématu [formuling for \[ \[ fallthrough \] \] attribute](https://wg21.link/p0188r0).

### <a name="generalized-range-based-for-loops"></a>Generalizovaná smyčka for – založený na rozsahu

Smyčky for založené na rozsahu již nevyžadují `begin()` a `end()` vracejí objekty stejného typu. Tato změna umožňuje `end()` vrátit Sentinel, jak je používá rozsahy v [rozsahu od – V3](https://github.com/ericniebler/range-v3) a dokončené, ale nepoměrně publikované rozsahy technické specifikace. Další informace najdete v tématu [generalizace smyčky for na základě rozsahu](https://wg21.link/p0184r0).

## <a name="conformance-improvements-in-153"></a><a name="improvements_153"></a>Vylepšení shody v 15,3

### <a name="constexpr-lambdas"></a>lambda výrazy constexpr

Výrazy lambda se teď dají použít v konstantních výrazech. Další informace naleznete v tématu [lambda výrazy constexpr v jazyce C++](../cpp/lambda-expressions-constexpr.md).

### <a name="if-constexpr-in-function-templates"></a>**if constexpr** v šablonách funkcí

Šablona funkce může obsahovat, **Pokud příkazy constexpr** povolují větvení v době kompilace. Další informace naleznete v tématu [if constexpr Statements](../cpp/if-else-statement-cpp.md#if_constexpr).

### <a name="selection-statements-with-initializers"></a>Příkazy výběru s Inicializátory

Příkaz **if** může zahrnovat inicializátor, který zavádí proměnnou v oboru bloku v rámci příkazu samotného. Další informace naleznete v tématu [if – příkazy s inicializátorem](../cpp/if-else-statement-cpp.md#if_with_init).

### <a name="maybe_unused-and-nodiscard-attributes"></a>`[[maybe_unused]]`a `[[nodiscard]]` atributy

`[[maybe_unused]]`Když se entita nepoužívá, je nový atribut tichá upozornění. `[[nodiscard]]`Atribut vytvoří upozornění, pokud je návratová hodnota volání funkce zahozena. Další informace naleznete v tématu [atributy v jazyce C++](../cpp/attributes.md).

### <a name="using-attribute-namespaces-without-repetition"></a>Použití oborů názvů atributů bez opakování

Nová syntaxe pro povolení pouze jednoho identifikátoru oboru názvů v seznamu atributů. Další informace naleznete v tématu [atributy v jazyce C++](../cpp/attributes.md).

### <a name="structured-bindings"></a>Strukturované vazby

Je možné, že je nyní v jedné deklaraci uložena hodnota s jednotlivými názvy pro své komponenty, pokud je hodnota pole, `std::tuple` nebo nebo `std::pair` má všechny veřejné nestatické datové členy. Další informace najdete v tématu [strukturované vazby](https://wg21.link/p0144r0) a [vracení více hodnot z funkce](../cpp/functions-cpp.md#multi_val).

### <a name="construction-rules-for-enum-class-values"></a>Pravidla vytváření pro hodnoty **třídy výčtu**

Nyní je implicitní a nezúžený převod z nadřízeného typu výčtu na samotný výčet. Převod je k dispozici, pokud jeho definice nezavádí enumerátor, a pokud zdroj používá syntaxi Inicializace seznamu. Další informace najdete v tématu [pravidla vytváření pro hodnoty](https://wg21.link/p0138r2) a [výčty](../cpp/enumerations-cpp.md#no_enumerators)výčtových tříd.

### <a name="capturing-this-by-value"></a>Zachycení `*this` podle hodnoty

`*this`Objekt ve výrazu lambda se teď dá zachytit podle hodnoty. Tato změna umožňuje scénáře, ve kterých je výraz lambda vyvolán paralelně a asynchronních operací, zejména u novějších architektur počítače. Další informace naleznete v tématu [lambda zachycení \* tohoto podle hodnoty jako \[ =, \* This \] ](https://wg21.link/p0018r3).

### <a name="removing-operator-for-bool"></a>Odebírá se `operator++` pro **bool** .

`operator++`již není podporován na **logických** typech. Další informace najdete v tématu [Odebrání zastaralého operátoru + + (bool)](https://wg21.link/p0002r1).

### <a name="removing-deprecated-register-keyword"></a>Odebírá se zastaralá klíčová slova **Register** .

Klíčové slovo **Register** , dříve zastaralé (a ignorováno kompilátorem), je nyní odebráno z jazyka. Další informace najdete v tématu [Odebrání zastaralého použití klíčového slova Register](https://wg21.link/p0001r1).

## <a name="conformance-improvements-in-155"></a><a name="improvements_155"></a>Vylepšení shody v 15,5

Funkce označené \[ 14] jsou k dispozici nepodmíněně i v **`/std:c++14`** režimu.

### <a name="new-compiler-switch-for-extern-constexpr"></a>Nový přepínač kompilátoru pro **externí constexpr**

V dřívějších verzích sady Visual Studio kompilátor vždy přiřadil vnitřní propojení proměnné **constexpr** , i když byla proměnná označena jako **extern**. V aplikaci Visual Studio 2017 verze 15,5 nový přepínač kompilátoru, [`/Zc:externConstexpr`](../build/reference/zc-externconstexpr.md) umožňuje správné chování při dodržování standardů. Další informace naleznete v tématu [extern vazby constexpr](#extern_linkage).

### <a name="removing-dynamic-exception-specifications"></a>Odebírají se specifikace dynamických výjimek.

[P0003R5](https://wg21.link/p0003r5) Specifikace dynamických výjimek jsou zastaralé v C++ 11. funkce je odebrána z C++ 17, ale (stále) zastaralá `throw()` specifikace je zachovaná výhradně jako alias pro `noexcept(true)` . Další informace naleznete v tématu [odstranění specifikace dynamické výjimky a s výjimkou](#noexcept_removal).

### `not_fn()`

[P0005R4](https://wg21.link/p0005r4) `not_fn` je náhradou `not1` a `not2` .

### <a name="rewording-enable_shared_from_this"></a>Přeformulování`enable_shared_from_this`

[P0033R1](https://wg21.link/p0033r1) `enable_shared_from_this` byl přidán do C++ 11. Standard C++ 17 aktualizuje specifikaci, aby lépe zpracovávala určité rohové případy. \[čtrnáct

### <a name="splicing-maps-and-sets"></a>Spojování map a sad

[P0083R3](https://wg21.link/p0083r3) Tato funkce umožňuje extrakci uzlů z asociativních kontejnerů (tj.,,, `map` `set` ), `unordered_map` `unordered_set` které lze následně upravit a vložit zpět do stejného kontejneru nebo jiného kontejneru, který používá stejný typ uzlu. (Běžný případ použití je extrakce uzlu z a `std::map` , změna klíče a znovu vložení.)

### <a name="deprecating-vestigial-library-parts"></a>Zastaralé části knihovny starší

[P0174R2](https://wg21.link/p0174r2) Několik funkcí standardní knihovny jazyka C++ bylo nahrazeno novějšími funkcemi během let, nebo jinak byly zjištěny jako neužitečné nebo problematické. Tyto funkce jsou oficiálně v C++ 17 zastaralé.

### <a name="removing-allocator-support-in-stdfunction"></a>Odebírá se podpora přidělování v`std::function`

[P0302R1](https://wg21.link/p0302r1) Před C++ 17 měla šablona třídy `std::function` několik konstruktorů, které trvalo argumentu přidělování. Použití přidělování v tomto kontextu bylo ale problematické a sémantika byla nejasná. Problém řadově byl odstraněn.

### <a name="fixes-for-not_fn"></a>Opravy pro`not_fn()`

[P0358R1](https://wg21.link/p0358r1) Nové formulace pro `std::not_fn` poskytuje podporu šíření kategorie hodnot při použití při vyvolání obálky.

### <a name="shared_ptrt-shared_ptrtn"></a>`shared_ptr<T[]>`, `shared_ptr<T[N]>`

[P0414R2](https://wg21.link/p0414r2) Sloučení `shared_ptr` změn z knihovny základy do c++ 17. \[čtrnáct

### <a name="fixing-shared_ptr-for-arrays"></a>Oprava `shared_ptr` pro pole

[P0497R0](https://wg21.link/p0497r0) Opravuje shared_ptr podporu pro pole. \[čtrnáct

### <a name="clarifying-insert_return_type"></a>Objasňováním`insert_return_type`

[P0508R0](https://wg21.link/p0508r0) Asociativní kontejnery s jedinečnými klíči a neuspořádané kontejnery s jedinečnými klíči mají členskou funkci `insert` , která vrací vnořený typ `insert_return_type` . Tento návratový typ je nyní definován jako specializace typu, který je parametrizovan na iterátoru a NodeType kontejneru.

### <a name="inline-variables-for-the-standard-library"></a>Vložené proměnné pro standardní knihovnu

[P0607R0](https://wg21.link/p0607r0)

### <a name="annex-d-features-deprecated"></a>Přílohy D – funkce se už nepoužívají.

Příloha D standardu C++ obsahuje všechny funkce, které jsou zastaralé, včetně `shared_ptr::unique()` , `<codecvt>` a `namespace std::tr1` . Pokud **`/std:c++17`** je nastaven přepínač kompilátoru, skoro všechny funkce standardní knihovny v příloze D jsou označeny jako zastaralé. Další informace najdete v tématu [standardní funkce knihovny v příloze D jsou označeny jako zastaralé](#annex_d).

`std::tr2::sys`Obor názvů `<experimental/filesystem>` teď ve výchozím nastavení vygeneruje upozornění na vyřazení a ve výchozím nastavení **`/std:c++14`** je teď odebraný **`/std:c++17`** .

Vylepšení `<iostream>` dodržování standardů pomocí zamezení nestandardního rozšíření (explicitní specializace ve třídě).

Standardní knihovna nyní používá šablony proměnných interně.

Standardní knihovna byla aktualizována v reakci na změny kompilátoru C++ 17. Aktualizace zahrnují přidání knihovny **s výjimkou** v systému typů a odebrání vlastností Dynamic-Exception-Specification.

## <a name="conformance-improvements-in-156"></a><a name="improvements_156"></a>Vylepšení shody v 15,6

### <a name="c17-library-fundamentals-v1"></a>C++ – základy knihoven verze V1

[P0220R1](https://wg21.link/p0220r1) zahrnuje technickou specifikaci základních specifikací pro c++ 17 na úrovni Standard. Pokrývá aktualizace \< experimentálních nebo řazených kolekcí> členů, \< experimentálních/volitelných>, \< experimentálních nebo funkčních>, \< experimentálních nebo \< string_viewch>, experimentálních/>>, \< experimentálních/paměťových memory_resource, \< experimentálních/>> a \< experimentálních/Algorithm.

### <a name="c17-improving-class-template-argument-deduction-for-the-standard-library"></a>C++ 17: vylepšení srážky argumentu šablony třídy pro standardní knihovnu

[P0739R0](https://wg21.link/p0739r0) Přejít `adopt_lock_t` na začátek seznamu parametrů pro `scoped_lock` , aby bylo možné povolit konzistentní použití `scoped_lock` . Povolte `std::variant` , aby se konstruktor účastnil řešení přetížení ve více případech, aby bylo možné povolit přiřazení kopírování.

## <a name="conformance-improvements-in-157"></a><a name="improvements_157"></a>Vylepšení shody v 15,7

### <a name="c17-rewording-inheriting-constructors"></a>C++ 17: přeformulování děděných konstruktorů

[P0136R1](https://wg21.link/p0136r1) určuje, že deklarace **using** s názvem konstruktoru nyní zpřístupňuje odpovídající konstruktory základní třídy pro inicializaci odvozené třídy namísto deklarace dalších konstruktorů odvozené třídy. Toto přeformulování se změní z C++ 14. V aplikaci Visual Studio 2017 verze 15,7 a novější v **`/std:c++17`** režimu, kód, který je platný v jazyce c++ 14 a používá děděné konstruktory, nemusí být platné nebo mohou mít různou sémantiku.

Následující příklad ukazuje chování C++ 14:

```cpp
struct A {
    template<typename T>
    A(T, typename T::type = 0);
    A(int);
};

struct B : A {
    using A::A;
    B(int n) = delete; // Error C2280
};

B b(42L); // Calls B<long>(long), which calls A(int)
          //  due to substitution failure in A<long>(long).
```

Následující příklad ukazuje **`/std:c++17`** chování v aplikaci Visual Studio 15,7:

```cpp
struct A {
    template<typename T>
    A(T, typename T::type = 0);
    A(int);
};

struct B : A {
    using A::A;
    B(int n)
    {
        //do something
    }
};

B b(42L); // now calls B(int)
```

Další informace naleznete v tématu [konstruktory](../cpp/constructors-cpp.md#inheriting_constructors).

### <a name="c17-extended-aggregate-initialization"></a>C++ 17: Rozšířená inicializace agregace

[P0017R1](https://wg21.link/p0017r1)

Pokud je konstruktor základní třídy neveřejný, ale přístupný pro odvozenou třídu, pak v **`/std:c++17`** režimu v rámci sady Visual Studio 2017 verze 15,7 již nelze použít prázdné složené závorky k inicializaci objektu odvozeného typu.
Následující příklad ukazuje vyhovující chování C++ 14:

```cpp
struct Derived;
struct Base {
    friend struct Derived;
private:
    Base() {}
};

struct Derived : Base {};
Derived d1; // OK. No aggregate init involved.
Derived d2 {}; // OK in C++14: Calls Derived::Derived()
               // which can call Base ctor.
```

V C++ 17 `Derived` se teď považuje za agregovaný typ. To znamená, že inicializace `Base` přes privátní výchozí konstruktor se stane přímo v rámci rozšířeného agregovaného inicializačního pravidla. Dříve `Base` byl privátní konstruktor volán prostřednictvím `Derived` konstruktoru a byl úspěšný z důvodu deklarace typu Friend.
Následující příklad ukazuje chování C++ 17 v aplikaci Visual Studio verze 15,7 v **`/std:c++17`** režimu:

```cpp
struct Derived;
struct Base {
    friend struct Derived;
private:
    Base() {}
};
struct Derived : Base {
    Derived() {} // add user-defined constructor
                 // to call with {} initialization
};
Derived d1; // OK. No aggregate init involved.
Derived d2 {}; // error C2248: 'Base::Base': cannot access
               // private member declared in class 'Base'
```

### <a name="c17-declaring-non-type-template-parameters-with-auto"></a>C++ 17: deklarace parametrů šablony bez typu s automatickým

[P0127R2](https://wg21.link/p0127r2)

V **`/std:c++17`** režimu může kompilátor nyní odvodit typ argumentu šablony bez typu, který je deklarován pomocí **auto**:

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

Jeden dopad této nové funkce je, že platný kód C++ 14 nemusí být platný nebo může mít různou sémantiku. Například některá přetížení, která byla dříve neplatná, jsou nyní platná. Následující příklad ukazuje kód C++ 14, který se zkompiluje, protože volání `example(p)` je vázáno na `example(void*);` . V aplikaci Visual Studio 2017 verze 15,7 **`/std:c++17`** je v režimu `example` nejlepší shoda šablony funkce.

```cpp
template <int N> struct A;
template <typename T, T N> int example(A<N>*) = delete;

void example(void *);

void sample(A<0> *p)
{
    example(p); // OK in C++14
}
```

Následující příklad ukazuje kód C++ 17 v aplikaci Visual Studio 15,7 v **`/std:c++17`** režimu:

```cpp
template <int N> struct A;
template <typename T, T N> int example(A<N>*);

void example(void *);

void sample(A<0> *p)
{
    example(p); // C2280: 'int example<int,0>(A<0>*)': attempting to reference a deleted function
}
```

### <a name="c17-elementary-string-conversions-partial"></a>C++ 17: základní převody řetězců (částečné)

[P0067R5](https://wg21.link/p0067r5) Funkce nezávislé na národním prostředí pro převody mezi celými čísly a řetězci a mezi čísly a řetězci s plovoucí desetinnou čárkou.

### <a name="c20-avoiding-unnecessary-decay-partial"></a>C++ 20: zamezení zbytečných Decay (částečné)

[P0777R1](https://wg21.link/p0777r1) Přidá odlišnosti mezi pojmem "Decay" a pouhým odebráním kvalifikátorů const nebo reference.  Nový typ vlastnosti `remove_reference_t` je `decay_t` v některých kontextech nahrazen. Podpora pro `remove_cvref_t` je implementována v aplikaci Visual Studio 2019.

### <a name="c17-parallel-algorithms"></a>C++ 17: paralelní algoritmy

[P0024R2](https://wg21.link/p0024r2) Paralelismus TS je začleněn do standardu s menšími úpravami.

### <a name="c17-hypotx-y-z"></a>C++ 17:`hypot(x, y, z)`

[P0030R1](https://wg21.link/p0030r1) Přidá tři nová přetížení do `std::hypot` , pro typy **float**, **Double**a **Long Double**, z nichž každý má tři vstupní parametry.

### <a name="c17-filesystem"></a>C++ 17: \<> systému souborů

[P0218R1](https://wg21.link/p0218r1) Předá do standardu systém souborů TS v rámci několika textových úprav.

### <a name="c17-mathematical-special-functions"></a>C++ 17: matematické speciální funkce

[P0226R1](https://wg21.link/p0220r1) Přijímá předchozí technické specifikace pro matematické speciální funkce do standardní \< hlavičky cmath>.

### <a name="c17-deduction-guides-for-the-standard-library"></a>C++ 17: Průvodce odpočty pro standardní knihovnu

[P0433R2](https://wg21.link/p0433r2) Aktualizace STL pro využití výhod C++ 17 přijetí [P0091R3](https://wg21.link/p0091r3), které přidává podporu pro odvození argumentu šablony třídy.

### <a name="c17-repairing-elementary-string-conversions"></a>C++ 17: Oprava základních převodů řetězců

[P0682R1](https://wg21.link/p0682r1) Přesuňte nové základní funkce pro převod řetězce z P0067R5 do nové hlavičky \< charconv> a udělejte další vylepšení, včetně změny zpracování chyb, která se má použít `std::errc` místo `std::error_code` .

### <a name="c17-constexpr-for-char_traits-partial"></a>C++ 17: **constexpr** pro `char_traits` (částečný)

[P0426R1](https://wg21.link/p0426r1) Změny `std::traits_type` členských funkcí `length` , `compare` a lze je `find` `std::string_view` použít v konstantních výrazech. (V aplikaci Visual Studio 2017 verze 15,6 je podporována pouze pro Clang/LLVM. Ve verzi 15,7 Preview 2 je podpora skoro dokončená i pro ClXX.)

## <a name="conformance-improvements-in-159"></a><a name="improvements_159"></a>Vylepšení shody v 15,9

### <a name="left-to-right-evaluation-order-for-operators-----and-"></a>Pořadí vyhodnocování zleva doprava pro operátory `->*` , `[]` , `>>` a`<<`

Počínaje c++ 17 se operandy operátorů `->*` ,, `[]` `>>` a `<<` musí vyhodnotit v pořadí zleva doprava. Existují dva případy, kdy kompilátor nemůže zaručit toto pořadí:

- je-li jeden z výrazů operandů objekt předaný hodnotou nebo obsahuje objekt předaný hodnotou nebo

- při kompilaci pomocí **`/clr`** a jeden z operandů je pole objektu nebo prvku pole.

Kompilátor vygeneruje upozornění [C4866](https://docs.microsoft.com/cpp/error-messages/compiler-warnings/c4866?view=vs-2017) , když nemůže zaručit vyhodnocení zleva doprava. Kompilátor vygeneruje toto upozornění pouze **`/std:c++17`** v případě, že je zadán nebo novější, protože požadavek zleva-doprava těchto operátorů byl představen v c++ 17.

Chcete-li vyřešit toto upozornění, nejprve zvažte, zda je nutné vyhodnocování zleva doprava u operandů. Například může být nutné, když vyhodnocení operandů může způsobit vedlejší účinky závislé na objednávkách. Pořadí, ve kterém jsou vyhodnocovány operandy, nemá v mnoha případech žádný pozorovatelný účinek. Pokud musí být pořadí vyhodnocování zleva doprava, zvažte, zda lze předat operandy odkazem const. Tato změna eliminuje upozornění v následující ukázce kódu:

```cpp
// C4866.cpp
// compile with: /w14866 /std:c++17

class HasCopyConstructor
{
public:
    int x;

    HasCopyConstructor(int x) : x(x) {}
    HasCopyConstructor(const HasCopyConstructor& h) : x(h.x) { }
};

int operator>>(HasCopyConstructor a, HasCopyConstructor b) { return a.x >> b.x; }

// This version of operator>> does not trigger the warning:
// int operator>>(const HasCopyConstructor& a, const HasCopyConstructor& b) { return a.x >> b.x; }

int main()
{
    HasCopyConstructor a{ 1 };
    HasCopyConstructor b{ 2 };

    a>>b;        // C4866 for call to operator>>
};
```

## <a name="bug-fixes-in-visual-studio-2017-rtw-version-150"></a><a name="update_150"></a>Opravy chyb v aplikaci Visual Studio 2017 RTW (verze 15,0)

### <a name="copy-list-initialization"></a>Kopírovat seznam – inicializace

Visual Studio 2017 správně vyvolává chyby kompilátoru související s vytvářením objektů pomocí seznamů inicializátorů. Tyto chyby nebyly zachyceny v aplikaci Visual Studio 2015 a mohly by vést k chybám nebo nedefinovanému chování modulu runtime. Podle N4594 13.3.1.7 P1, v případě Inicializace kopírování seznamu, je kompilátor nutný k zvážení explicitního konstruktoru pro řešení přetížení, ale musí vyvolat chybu, pokud je zvoleno konkrétní přetížení.

Následující dva příklady jsou zkompilovány v aplikaci Visual Studio 2015, ale ne v aplikaci Visual Studio 2017.

```cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    A a1 = { 1 }; // error C3445: copy-list-initialization of 'A' cannot use an explicit constructor
    const A& a2 = { 1 }; // error C2440: 'initializing': cannot convert from 'int' to 'const A &'

}
```

Chcete-li chybu opravit, použijte přímou inicializaci:

```cpp
A a1{ 1 };
const A& a2{ 1 };
```

V sadě Visual Studio 2015 kompilátor chybně zpracoval inicializaci kopírováním seznamu, stejně jako při normální inicializaci kopírování; považuje se za převádění pouze konstruktorů pro řešení přetížení. V následujícím příkladu Visual Studio 2015 zvolí MyInt (23), ale Visual Studio 2017 správně vyvolá chybu.

```cpp
// From http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_closed.html#1228
struct MyStore {
    explicit MyStore(int initialCapacity);
};

struct MyInt {
    MyInt(int i);
};

struct Printer {
    void operator()(MyStore const& s);
    void operator()(MyInt const& i);
};

void f() {
    Printer p;
    p({ 23 }); // C3066: there are multiple ways that an object of this type can be called with these arguments
}
```

Tento příklad je podobný předchozímu, ale vyvolá jinou chybu. Je úspěch v aplikaci Visual Studio 2015 a selže v aplikaci Visual Studio 2017 s C2668.

```cpp
struct A {
    explicit A(int) {}
};

struct B {
    B(int) {}
};

void f(const A&) {}
void f(const B&) {}

int main()
{
    f({ 1 }); // error C2668: 'f': ambiguous call to overloaded function
}
```

### <a name="deprecated-typedefs"></a>Zastaralé Definice TypeDef

Visual Studio 2017 nyní vydává správné upozornění pro zastaralé Definice TypeDef, které jsou deklarovány ve třídě nebo struktuře. Následující příklad kompiluje bez upozornění v aplikaci Visual Studio 2015, ale vytváří C4996 v aplikaci Visual Studio 2017.

```cpp
struct A
{
    // also for __declspec(deprecated)
    [[deprecated]] typedef int inttype;
};

int main()
{
    A::inttype a = 0; // C4996 'A::inttype': was declared deprecated
}
```

### <a name="constexpr"></a>**constexpr**

Pokud levý operand podmíněného vyhodnocení operace v kontextu constexpr není platný, Visual Studio 2017 správně vyvolá chybu. Následující kód je zkompilován v aplikaci Visual Studio 2015, ale ne v aplikaci Visual Studio 2017, kde vyvolává C3615 `constexpr function 'f' cannot result in a constant expression` :

```cpp
template<int N>
struct array
{
    int size() const { return N; }
};

constexpr bool f(const array<1> &arr)
{
    return arr.size() == 10 || arr.size() == 11; // C3615
}
```

Chcete-li chybu opravit, deklarujte `array::size()` funkci jako **constexpr** nebo odstraňte kvalifikátor **constexpr** z `f` .

### <a name="class-types-passed-to-variadic-functions"></a>Typy tříd předané do variadické funkcí

V aplikaci Visual Studio 2017 třídy nebo struktury, které jsou předány funkci variadické, například, `printf` musí být triviální kopie. Při předání takových objektů kompilátor jednoduše vytvoří bitovou kopii a nevolá konstruktor nebo destruktor.

```cpp
#include <atomic>
#include <memory>
#include <stdio.h>

int main()
{
    std::atomic<int> i(0);
    printf("%i\n", i); // error C4839: non-standard use of class 'std::atomic<int>'
                        // as an argument to a variadic function.
                        // note: the constructor and destructor will not be called;
                        // a bitwise copy of the class will be passed as the argument
                        // error C2280: 'std::atomic<int>::atomic(const std::atomic<int> &)':
                        // attempting to reference a deleted function

    struct S {
        S(int i) : i(i) {}
        S(const S& other) : i(other.i) {}
        operator int() { return i; }
    private:
        int i;
    } s(0);
    printf("%i\n", s); // warning C4840 : non-portable use of class 'main::S'
                      // as an argument to a variadic function
}
```

Chcete-li chybu opravit, můžete zavolat členskou funkci, která vrací triviální kopírovací typ,

```cpp
    std::atomic<int> i(0);
    printf("%i\n", i.load());
```

nebo jinak použijte statické přetypování pro převod objektu před jeho předáním:

```cpp
    struct S {/* as before */} s(0);
    printf("%i\n", static_cast<int>(s))
```

Pro řetězce sestavené a spravované pomocí CString `operator LPCTSTR()` by měly být k dispozici použití k přetypování objektu CString na ukazatel jazyka C, který je očekáván formátovacím řetězcem.

```cpp
CString str1;
CString str2 = _T("hello!");
str1.Format(_T("%s"), static_cast<LPCTSTR>(str2));
```

### <a name="cv-qualifiers-in-class-construction"></a>Kvalifikátory cv v konstrukci třídy

V aplikaci Visual Studio 2015 kompilátor někdy nesprávně ignoruje kvalifikátor CV při generování objektu třídy prostřednictvím volání konstruktoru. Tento problém může potenciálně způsobit selhání nebo neočekávané chování modulu runtime. Následující příklad kompiluje v aplikaci Visual Studio 2015, ale vyvolává chybu kompilátoru v aplikaci Visual Studio 2017:

```cpp
struct S
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```

Chcete-li chybu opravit, deklarujte `operator int()` jako **const**.

### <a name="access-checking-on-qualified-names-in-templates"></a>Kontrola přístupu k kvalifikovaným názvům v šablonách

Předchozí verze kompilátoru nekontrolovaly v některých kontextech šablon přístup k kvalifikovaným názvům. Tento problém může kolidovat s očekávaným SFINAE chováním, kdy se očekává, že náhrada selže kvůli nedostupnosti názvu. Mohla by potenciálně způsobila selhání nebo neočekávané chování za běhu, protože kompilátor nesprávně volal špatné přetížení operátoru. V aplikaci Visual Studio 2017 je vyvolána chyba kompilátoru. Konkrétní chyba se může lišit, ale obvykle se jedná o C2672 `no matching overloaded function found` . Následující kód je zkompilován v aplikaci Visual Studio 2015, ale vyvolává chybu v aplikaci Visual Studio 2017:

```cpp
#include <type_traits>

template <class T> class S {
    typedef typename T type;
};

template <class T, std::enable_if<std::is_integral<typename S<T>::type>::value, T> * = 0>
bool f(T x);

int main()
{
    f(10); // C2672: No matching overloaded function found.
}
```

### <a name="missing-template-argument-lists"></a>Chybějící seznamy argumentů šablony

V aplikaci Visual Studio 2015 a starší kompilátor nediagnostikoval chybějící seznamy argumentů šablony, když se šablona objevila v seznamu parametrů šablony: například v případě, že část výchozího argumentu šablony nebo parametr šablony bez typu chyběla. Tento problém může způsobit nepředvídatelné chování, včetně selhání kompilátoru nebo neočekávaného běhového chování. Následující kód je zkompilován v aplikaci Visual Studio 2015, ale vytvoří chybu v aplikaci Visual Studio 2017.

```cpp
template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;
```

### <a name="expression-sfinae"></a>Výraz – SFINAE

Pro podporu Expression-SFINAE kompilátor nyní analyzuje argumenty **decltype** při deklaraci šablony namísto vytvoření instance. V důsledku toho, pokud je v argumentu decltype Nalezeno nezávislá specializace, není odvoditelné na dobu vytvoření instance. Je zpracována okamžitě a všechny výsledné chyby jsou diagnostikovány v daném čase.

Následující příklad ukazuje chybu kompilátoru, která je vyvolána v bodě deklarace:

```cpp
#include <utility>
template <class T, class ReturnT, class... ArgsT>
class IsCallable
{
public:
    struct BadType {};

    template <class U>
    static decltype(std::declval<T>()(std::declval<ArgsT>()...)) Test(int); //C2064. Should be declval<U>

    template <class U>
    static BadType Test(...);

    static constexpr bool value = std::is_convertible<decltype(Test<T>(0)), ReturnT>::value;
};

constexpr bool test1 = IsCallable<int(), int>::value;
static_assert(test1, "PASS1");
constexpr bool test2 = !IsCallable<int*, int>::value;
static_assert(test2, "PASS2");
```

### <a name="classes-declared-in-anonymous-namespaces"></a>Třídy deklarované v anonymních oborech názvů

Podle standardu C++ má třída deklarovaná uvnitř anonymního oboru názvů vnitřní propojení a to znamená, že se nedá exportovat. V aplikaci Visual Studio 2015 a starších verzích nebylo toto pravidlo vynutilo. V aplikaci Visual Studio 2017 se pravidlo částečně vynutilo. V aplikaci Visual Studio 2017 následující příklad vyvolává chybu C2201:`const anonymous namespace::S1::vftable: must have external linkage in order to be exported/imported.`

```cpp
struct __declspec(dllexport) S1 { virtual void f() {} }; //C2201
```

### <a name="default-initializers-for-value-class-members-ccli"></a>Výchozí inicializátory pro členy hodnotové třídy (C++/CLI)

V aplikaci Visual Studio 2015 a starší kompilátor povolil (ale ignoruje) výchozí inicializátor členu pro člena hodnotové třídy. Výchozí inicializace třídy hodnot vždy nula – inicializuje členy. Výchozí konstruktor není povolený. V aplikaci Visual Studio 2017 vyvolají výchozí Inicializátory členů chybu kompilátoru, jak je znázorněno v následujícím příkladu:

```cpp
value struct V
{
    int i = 0; // error C3446: 'V::i': a default member initializer
               // isn't allowed for a member of a value class
};
```

### <a name="default-indexers-ccli"></a>Výchozí indexery (C++/CLI)

V aplikaci Visual Studio 2015 a starší kompilátor v některých případech chybně identifikoval výchozí vlastnost jako výchozí indexer. Tento problém bylo možné vyřešit pomocí **výchozího** identifikátoru pro přístup k vlastnosti. Alternativní řešení se jako klíčové slovo v C++ 11 stalo problematickým po zavedení **výchozího nastavení** . V aplikaci Visual Studio 2017 byly opraveny chyby, které vyžadovaly alternativní řešení. Kompilátor nyní vyvolá chybu, pokud je použita **Výchozí hodnota** pro přístup k výchozí vlastnosti pro třídu.

```cpp
//class1.cs

using System.Reflection;
using System.Runtime.InteropServices;

namespace ClassLibrary1
{
    [DefaultMember("Value")]
    public class Class1
    {
        public int Value
        {
            // using attribute on the return type triggers the compiler bug
            [return: MarshalAs(UnmanagedType.I4)]
            get;
        }
    }
    [DefaultMember("Value")]
    public class Class2
    {
        public int Value
        {
            get;
        }
    }
}

// code.cpp
#using "class1.dll"

void f(ClassLibrary1::Class1 ^r1, ClassLibrary1::Class2 ^r2)
{
       r1->Value; // error
       r1->default;
       r2->Value;
       r2->default; // error
}
```

V aplikaci Visual Studio 2017 máte přístup k oběma vlastnostem hodnot podle jejich názvu:

```cpp
#using "class1.dll"

void f(ClassLibrary1::Class1 ^r1, ClassLibrary1::Class2 ^r2)
{
       r1->Value;
       r2->Value;
}
```

## <a name="bug-fixes-in-153"></a><a name="update_153"></a>Opravy chyb v 15,3

### <a name="calls-to-deleted-member-templates"></a>Volání odstraněných členských šablon

V předchozích verzích sady Visual Studio kompilátor v některých případech nemohlo vygenerovat chybu pro volání nesprávně naformátované šablony člena. Tato volání by potenciálně způsobila selhání za běhu. Následující kód teď vytvoří C2280 `'int S<int>::f<int>(void)': attempting to reference a deleted function` :

```cpp
template<typename T>
struct S {
   template<typename U> static int f() = delete;
};

void g()
{
   decltype(S<int>::f<int>()) i; // this should fail
}
```

Chcete-li chybu opravit, deklarujte `i` jako **int**.

### <a name="pre-condition-checks-for-type-traits"></a>Kontroly předběžných podmínek u vlastností typu

Visual Studio 2017 verze 15,3 vylepšuje kontrolu před podmíněnými podmínkami pro typové vlastnosti tak, aby se dodržovala podle standardu. Jednu takovou kontrolu je možné přiřadit. Následující kód vytvoří C2139 ve Visual Studiu 2017 verze 15,3:

```cpp
struct S;
enum E;

static_assert(!__is_assignable(S, S), "fail"); // C2139 in 15.3
static_assert(__is_convertible_to(E, E), "fail"); // C2139 in 15.3
```

### <a name="new-compiler-warning-and-runtime-checks-on-native-to-managed-marshaling"></a>Nové upozornění kompilátoru a kontroly za běhu na zařazování z nativního na spravované

Volání ze spravovaných funkcí do nativních funkcí vyžaduje zařazování. Modul CLR zařazování, ale nerozumí sémantikě jazyka C++. Pokud předáte nativní objekt podle hodnoty, CLR buď zavolá kopírovací konstruktor objektu nebo používá `BitBlt` , což může způsobit nedefinované chování za běhu.

Kompilátor nyní vygeneruje upozornění, pokud je určen v době kompilace, že nativní objekt s odstraněným kopírovacím elementem je předán mezi nativním a spravovaným ohraničením podle hodnoty. V případech, kdy kompilátor neví v době kompilace, vloží kontrolu za běhu tak, aby program zavolal `std::terminate` okamžitě, když dojde k zařazování nesprávně formátovaného objektu. V aplikaci Visual Studio 2017 verze 15,3 následující kód generuje upozornění C4606`'A': passing argument by value across native and managed boundary requires valid copy constructor. Otherwise, the runtime behavior is undefined.`

```cpp
class A
{
public:
   A() : p_(new int) {}
   ~A() { delete p_; }

   A(A const &) = delete;
   A(A &&rhs) {
   p_ = rhs.p_;
}

private:
   int *p_;
};

#pragma unmanaged

void f(A a)
{
}

#pragma managed

int main()
{
    f(A()); // This call from managed to native requires marshaling. The CLR doesn't understand C++ and uses BitBlt, which results in a double-free later.
}
```

Chcete-li chybu opravit, odeberte `#pragma managed` direktivu pro označení volajícího jako nativní a zabraňte zařazování.

### <a name="experimental-api-warning-for-winrt"></a>Experimentální upozornění rozhraní API pro WinRT

Rozhraní API WinRT vydaná pro experimentování a zpětnou vazbu se dekorují pomocí `Windows.Foundation.Metadata.ExperimentalAttribute` . V aplikaci Visual Studio 2017 verze 15,3 vyvolá kompilátor upozornění C4698 pro tento atribut. Několik rozhraní API v předchozích verzích Windows SDK již bylo upraveno atributem a volání těchto rozhraní API nyní aktivují toto upozornění kompilátoru. Novější sady Windows SDK mají odebraný atribut ze všech typů dodaných. Pokud používáte starší sadu SDK, budete muset potlačit tato upozornění pro všechna volání expedovaného typu.

Následující kód vytvoří upozornění C4698: `'Windows::Storage::IApplicationDataStatics2::GetForUserAsync' is for evaluation purposes only and is subject to change or removal in future updates` :

```cpp
Windows::Storage::IApplicationDataStatics2::GetForUserAsync(); //C4698
```

Chcete-li zakázat upozornění, přidejte #pragma:

```cpp
#pragma warning(push)
#pragma warning(disable:4698)

Windows::Storage::IApplicationDataStatics2::GetForUserAsync();

#pragma warning(pop)
```

### <a name="out-of-line-definition-of-a-template-member-function"></a>Definice přesahujícího řádku členské funkce šablony

Visual Studio 2017 verze 15,3 vytvoří chybu pro řádek definice členské funkce šablony, která nebyla deklarována ve třídě. Následující kód nyní vytvoří chybu C2039: `'f': is not a member of 'S'` :

```cpp
struct S {};

template <typename T>
void S::f(T t) {} //C2039: 'f': is not a member of 'S'
```

Chcete-li chybu opravit, přidejte do třídy deklaraci:

```cpp
struct S {
    template <typename T>
    void f(T t);
};
template <typename T>
void S::f(T t) {}
```

### <a name="attempting-to-take-the-address-of-this-pointer"></a>Probíhá pokus o převzetí adresy **tohoto** ukazatele.

V jazyce C++ **`this`** je prvalue typu ukazatel na X. Nelze převzít adresu **`this`** nebo ji vytvořit jako odkaz na odkaz lvalue. V předchozích verzích sady Visual Studio, kompilátor vám umožní obejít toto omezení pomocí přetypování. V aplikaci Visual Studio 2017 verze 15,3 vyvolá kompilátor chybu upozornění C2664.

### <a name="conversion-to-an-inaccessible-base-class"></a>Převod na nepřístupnou základní třídu

Pokud se pokusíte převést typ na základní třídu, která je nepřístupná, Visual Studio 2017 verze 15,3 vyvolá chybu. Kompilátor nyní vyvolává chybu C2243: `'type cast': conversion from 'D *' to 'B *' exists, but is inaccessible` . Následující kód je nesprávně vytvořen a může potenciálně způsobit selhání za běhu. Kompilátor teď vytvoří C2243, když se setká s kódem podobným tomuto:

```cpp
#include <memory>

class B { };
class D : B { }; // C2243. should be public B { };

void f()
{
   std::unique_ptr<B>(new D());
}
```

### <a name="default-arguments-arent-allowed-on-out-of-line-definitions-of-member-functions"></a>Výchozí argumenty nejsou povolené u definic na řádcích a u členských funkcí.

Výchozí argumenty nejsou povoleny pro předdefinované definice členských funkcí v třídách šablon. Kompilátor vydá upozornění pod **`/permissive`** a v rámci [/Permissive-](../build/reference/permissive-standards-conformance.md)se objeví tvrdý problém.

V předchozích verzích sady Visual Studio mohl následující nesprávně vytvořený kód způsobit chybu modulu runtime. Visual Studio 2017 verze 15,3 generuje upozornění C5034: `'A\<T>::f': an out-of-line definition of a member of a class template cannot have default arguments` :

```cpp
template <typename T>
struct A {
    T f(T t, bool b = false);
};

template <typename T>
T A<T>::f(T t, bool b = false) // C5034
{
    // ...
}
```

Chcete-li chybu opravit, odeberte `= false` výchozí argument.

### <a name="use-of-offsetof-with-compound-member-designator"></a>Použití `offsetof` se specifikátorem složeného člena

V aplikaci Visual Studio 2017 verze 15,3, `offsetof(T, m)` kde *m* je "označení složeného člena", má za následek upozornění při kompilaci s **`/Wall`** možností. Následující kód je nesprávně vytvořen a může potenciálně způsobit selhání za běhu. Visual Studio 2017 verze 15,3 generuje upozornění C4841: `non-standard extension used: compound member designator in offsetof` :

```cpp
struct A {
   int arr[10];
};

// warning C4841: non-standard extension used: compound member designator in offsetof
constexpr auto off = offsetof(A, arr[2]);
```

Chcete-li opravit kód, buď zakažte upozornění pomocí direktivy pragma, nebo změňte kód tak, aby nepoužíval `offsetof` :

```cpp
#pragma warning(push)
#pragma warning(disable: 4841)
constexpr auto off = offsetof(A, arr[2]);
#pragma warning(pop)
```

### <a name="using-offsetof-with-static-data-member-or-member-function"></a>Použití `offsetof` se statickým datovým členem nebo členskou funkcí

V aplikaci Visual Studio 2017 verze 15,3, `offsetof(T, m)` kde *m* odkazuje na statický datový člen nebo členská funkce, má za následek chybu. Následující kód vytvoří chybu C4597: `undefined behavior: offsetof applied to member function 'example'` a chybu C4597: `undefined behavior: offsetof applied to static data member 'sample'` :

```cpp
#include <cstddef>

struct A {
   int ten() { return 10; }
   static constexpr int two = 2;
};

constexpr auto off = offsetof(A, ten);
constexpr auto off2 = offsetof(A, two);
```

Tento kód je nesprávně vytvořen a může potenciálně způsobit selhání za běhu. Chcete-li chybu opravit, změňte kód tak, aby již nevolal nedefinované chování. Není to přenosový kód, který je zakázán standardem C++.

### <a name="new-warning-on-__declspec-attributes"></a><a name="declspec"></a>Nové upozornění na `__declspec` atributy

V aplikaci Visual Studio 2017 verze 15,3 kompilátor již neignoruje atributy, pokud `__declspec(...)` je použita před `extern "C"` specifikací propojení. Dřív by kompilátor ignoroval atribut, což by mohlo mít dopad na modul runtime. Když **`/Wall`** **`/WX`** jsou nastaveny možnosti a, následující kód vytvoří upozornění C4768: `__declspec attributes before linkage specification are ignored` :

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

Chcete-li opravit upozornění, vložte `extern "C"` první:

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

Toto upozornění je ve výchozím nastavení v 15,3 vypnuto, ale ve výchozím nastavení je v 15,5 a má vliv pouze na kód zkompilovaný pomocí **`/Wall`** **`/WX`** .

### <a name="decltype-and-calls-to-deleted-destructors"></a>**decltype** a volání odstraněných destruktorů

V předchozích verzích sady Visual Studio kompilátor nerozpoznal, když došlo k volání odstraněného destruktoru v kontextu výrazu přidruženého k **decltype**. V aplikaci Visual Studio 2017 verze 15,3 následující kód vytvoří chybu C2280: `'A<T>::~A(void)': attempting to reference a deleted function` :

```cpp
template<typename T>
struct A
{
   ~A() = delete;
};

template<typename T>
auto f() -> A<T>;

template<typename T>
auto g(T) -> decltype((f<T>()));

void h()
{
   g(42);
}
```

### <a name="uninitialized-const-variables"></a>Neinicializované proměnné const

Vydání sady Visual Studio 2017 RTW má regresi: kompilátor C++ by nevydal diagnostiku pro neinicializované proměnné **const** . Tato regrese byla opravena v aplikaci Visual Studio 2017 verze 15,3. Následující kód nyní vytvoří upozornění C4132: `'Value': const object should be initialized` :

```cpp
const int Value; //C4132
```

Chcete-li chybu opravit, přiřaďte hodnotu `Value` .

### <a name="empty-declarations"></a>Prázdné deklarace

Visual Studio 2017 verze 15,3 teď upozorňuje na prázdné deklarace pro všechny typy, ne jenom na předdefinované typy. Následující kód teď vytvoří C4091 upozornění úrovně 2 pro všechny čtyři deklarace:

```cpp
struct A {};
template <typename> struct B {};
enum C { c1, c2, c3 };

int;    // warning C4091 : '' : ignored on left of 'int' when no variable is declared
A;      // warning C4091 : '' : ignored on left of 'main::A' when no variable is declared
B<int>; // warning C4091 : '' : ignored on left of 'B<int>' when no variable is declared
C;      // warning C4091 : '' : ignored on left of 'C' when no variable is declared
```

Chcete-li odstranit upozornění, odkomentujte nebo odeberte prázdné deklarace. V případech, kdy je nepojmenovaný objekt určen pro vedlejší efekt (například RAII), by měl být uveden název.

Upozornění se vyloučí z **`/Wv:18`** a je ve výchozím nastavení zapnuté v části úroveň upozornění W2.

### <a name="stdis_convertible-for-array-types"></a>`std::is_convertible`pro typy polí

Předchozí verze kompilátoru poskytly nesprávné výsledky pro [std:: is_convertible](../standard-library/is-convertible-class.md) pro typy polí. Tato požadovaná zapisovače knihovny se zvláštním případem kompilátorem jazyka Microsoft C++ při použití `std::is_convertible<...>` typové vlastnosti. V následujícím příkladu jsou statické kontrolní výrazy předávány v předchozích verzích sady Visual Studio, ale selžou v aplikaci Visual Studio 2017 verze 15,3:

```cpp
#include <type_traits>

using Array = char[1];

static_assert(std::is_convertible<Array, Array>::value);
static_assert(std::is_convertible<const Array, const Array>::value, "");
static_assert(std::is_convertible<Array&, Array>::value, "");
static_assert(std::is_convertible<Array, Array&>::value, "");
```

`std::is_convertible<From, To>`se vypočítá pomocí zaškrtnutí a zjistí, zda je definice imaginární funkce ve správném formátu:

```cpp
   To test() { return std::declval<From>(); }
```

### <a name="private-destructors-and-stdis_constructible"></a>Soukromé destruktory a`std::is_constructible`

Předchozí verze kompilátoru ignorovaly, zda byl destruktor privátní při rozhodování o výsledku [std:: is_constructible](../standard-library/is-constructible-class.md). Teď je považuje za ně. V následujícím příkladu jsou statické kontrolní výrazy předávány v předchozích verzích sady Visual Studio, ale selžou v aplikaci Visual Studio 2017 verze 15,3:

```cpp
#include <type_traits>

class PrivateDtor {
   PrivateDtor(int) { }
private:
   ~PrivateDtor() { }
};

// This assertion used to succeed. It now correctly fails.
static_assert(std::is_constructible<PrivateDtor, int>::value);
```

Soukromé destruktory způsobují, že typ není constructible. `std::is_constructible<T, Args...>`se počítá jako při zápisu následující deklarace:

```cpp
   T obj(std::declval<Args>()...)
```

Toto volání předpokládá volání destruktoru.

### <a name="c2668-ambiguous-overload-resolution"></a>C2668: dvojznačné rozlišení přetížení

Předchozí verze kompilátoru někdy nedokázaly detekovat nejednoznačnost, když našli více kandidátů prostřednictvím deklarace a vyhledávání závislého na argumentech. Toto selhání může vést k nesprávnému přetížení a neočekávanému chování za běhu. V následujícím příkladu Visual Studio 2017 verze 15,3 správně vyvolává C2668 `'f': ambiguous call to overloaded function` :

```cpp
namespace N {
   template<class T>
   void f(T&, T&);

   template<class T>
   void f();
}

template<class T>
void f(T&, T&);

struct S {};
void f()
{
   using N::f;

   S s1, s2;
   f(s1, s2); // C2668
}
```

Chcete-li opravit kód, odeberte příkaz using, `N::f` Pokud jste chtěli volat `::f()` .

### <a name="c2660-local-function-declarations-and-argument-dependent-lookup"></a>C2660: deklarace místních funkcí a vyhledávání závislé na argumentech

Deklarace místní funkce skrývá deklaraci funkce v ohraničujícím oboru a zakazuje vyhledávání závislé na argumentech. Předchozí verze kompilátoru ale v tomto případě prováděly vyhledávání závislé na argumentech. Může potenciálně vést k nesprávnému vybírání špatného přetížení a neočekávané chování za běhu. Chyba je obvykle způsobena nesprávnou signaturou místní deklarace funkce. V následujícím příkladu Visual Studio 2017 verze 15,3 správně vyvolává C2660 `'f': function does not take two arguments` :

```cpp
struct S {};
void f(S, int);

void g()
{
   void f(S); // C2660 'f': function does not take 2 arguments:
   // or void f(S, int);
   S s;
   f(s, 0);
}
```

Problém vyřešíte tak, že změníte `f(S)` podpis nebo ho odeberete.

### <a name="c5038-order-of-initialization-in-initializer-lists"></a>C5038: pořadí inicializace v seznamech inicializátorů

Členy třídy jsou inicializovány v pořadí, ve kterém jsou deklarovány, nikoli v pořadí, v jakém jsou uvedeny v seznamech inicializátorů. Předchozí verze kompilátoru nezobrazovaly upozornění, když se pořadí seznamu inicializátorů liší od pořadí deklarace. Tento problém by mohl vést k nedefinovanému chování za běhu, pokud je jedna inicializace jednoho člena závislá na jiném členu v seznamu, který už je inicializovaný. V následujícím příkladu Visual Studio 2017 verze 15,3 (s **`/Wall`** ) vyvolává upozornění C5038: `data member 'A::y' will be initialized after data member 'A::x'` :

```cpp
struct A
{
    A(int a) : y(a), x(y) {} // Initialized in reverse, y reused
    int x;
    int y;
};
```

Chcete-li problém vyřešit, uspořádejte seznam inicializátorů tak, aby měl stejné pořadí jako deklarace. Podobné upozornění je vyvolána, když jeden nebo oba Inicializátory odkazují na členy základní třídy.

Toto upozornění je mimo výchozí a má vliv pouze na kód zkompilovaný pomocí **`/Wall`** .

## <a name="bug-fixes-and-other-behavior-changes-in-155"></a><a name="update_155"></a>Opravy chyb a další změny chování v 15,5

### <a name="partial-ordering-change"></a>Částečná změna pořadí

Kompilátor nyní správně odmítne následující kód a poskytne správnou chybovou zprávu:

```cpp
template<typename... T>
int f(T* ...)
{
    return 1;
}

template<typename T>
int f(const T&)
{
    return 2;
}

int main()
{
    int i = 0;
    f(&i);    // C2668
}
```

```Output
t161.cpp
t161.cpp(16): error C2668: 'f': ambiguous call to overloaded function
t161.cpp(8): note: could be 'int f<int*>(const T &)'
        with
        [
            T=int*
        ]
t161.cpp(2): note: or       'int f<int>(int*)'
t161.cpp(16): note: while trying to match the argument list '(int*)'
```

Problémem v předchozím příkladu je, že existují dva rozdíly v typech (const vs. non-const a Pack vs. non-Pack). Chcete-li odstranit chybu kompilátoru, odeberte jednu z rozdílů. Kompilátor pak může jednoznačně seřadit funkce.

```cpp
template<typename... T>
int f(T* ...)
{
    return 1;
}

template<typename T>
int f(T&)
{
    return 2;
}

int main()
{
    int i = 0;
    f(&i);
}
```

### <a name="exception-handlers"></a>Obslužné rutiny výjimek

Obslužné rutiny odkazu na typ pole nebo funkce nikdy neodpovídají žádnému objektu výjimky. Kompilátor teď toto pravidlo správně respektuje a vyvolá upozornění úrovně 4. Zároveň se už neshoduje s obslužnou rutinou `char*` nebo `wchar_t*` do řetězcového literálu, když **`/Zc:strictStrings`** se používá.

```cpp
int main()
{
    try {
        throw "";
    }
    catch (int (&)[1]) {} // C4843 (This should always be dead code.)
    catch (void (&)()) {} // C4843 (This should always be dead code.)
    catch (char*) {} // This should not be a match under /Zc:strictStrings
}
```

```Output
warning C4843: 'int (&)[1]': An exception handler of reference to array or function type is unreachable, use 'int*' instead
warning C4843: 'void (__cdecl &)(void)': An exception handler of reference to array or function type is unreachable, use 'void (__cdecl*)(void)' instead
```

Následující kód vylučuje chybu:

```cpp
catch (int (*)[1]) {}
```

### <a name="stdtr1-namespace-is-deprecated"></a><a name="tr1"></a>`std::tr1`obor názvů je zastaralý.

Nestandardní `std::tr1` obor názvů je teď označený jako zastaralý v režimech c++ 14 a c++ 17. V aplikaci Visual Studio 2017 verze 15,5 následující kód vyvolává C4996:

```cpp
#include <functional>
#include <iostream>
using namespace std;

int main() {
    std::tr1::function<int (int, int)> f = std::plus<int>(); //C4996
    cout << f(3, 5) << std::endl;
    f = std::multiplies<int>();
    cout << f(3, 5) << std::endl;
}
```

```Output
warning C4996: 'std::tr1': warning STL4002: The non-standard std::tr1 namespace and TR1-only machinery are deprecated and will be REMOVED. You can define _SILENCE_TR1_NAMESPACE_DEPRECATION_WARNING to acknowledge that you have received this warning.
```

Chcete-li chybu opravit, odeberte odkaz na `tr1` obor názvů:

```cpp
#include <functional>
#include <iostream>
using namespace std;

int main() {
    std::function<int (int, int)> f = std::plus<int>();
    cout << f(3, 5) << std::endl;
    f = std::multiplies<int>();
    cout << f(3, 5) << std::endl;
}
```

### <a name="standard-library-features-in-annex-d-are-marked-as-deprecated"></a><a name="annex_d"></a>Funkce standardní knihovny v příloze D jsou označené jako zastaralé.

Když **`/std:c++17`** je nastaven přepínač pro kompilátor režimu, skoro všechny standardní funkce knihovny v příloze D jsou označeny jako zastaralé.

V aplikaci Visual Studio 2017 verze 15,5 následující kód vyvolává C4996:

```cpp
#include <iterator>

class MyIter : public std::iterator<std::random_access_iterator_tag, int> {
public:
    // ... other members ...
};

#include <type_traits>

static_assert(std::is_same<MyIter::pointer, int*>::value, "BOOM");
```

```Output
warning C4996: 'std::iterator<std::random_access_iterator_tag,int,ptrdiff_t,_Ty*,_Ty &>::pointer': warning STL4015: The std::iterator class template (used as a base class to provide typedefs) is deprecated in C++17. (The <iterator> header is NOT deprecated.) The C++ standard has never required user-defined iterators to derive from std::iterator. To fix this warning, stop deriving from std::iterator and start providing publicly accessible typedefs named iterator_category, value_type, difference_type, pointer, and reference. Note that value_type is required to be non-const, even for constant iterators. You can define _SILENCE_CXX17_ITERATOR_BASE_CLASS_DEPRECATION_WARNING or _SILENCE_ALL_CXX17_DEPRECATION_WARNINGS to acknowledge that you have received this warning.
```

Chcete-li chybu opravit, postupujte podle pokynů v textu upozornění, jak je znázorněno v následujícím kódu:

```cpp
#include <iterator>

class MyIter {
public:
    typedef std::random_access_iterator_tag iterator_category;
    typedef int value_type;
    typedef ptrdiff_t difference_type;
    typedef int* pointer;
    typedef int& reference;

    // ... other members ...
};

#include <type_traits>

static_assert(std::is_same<MyIter::pointer, int*>::value, "BOOM");
```

### <a name="unreferenced-local-variables"></a>Neodkazované lokální proměnné

V aplikaci Visual Studio 15,5 je ve více případech vygenerováno upozornění C4189, jak je znázorněno v následujícím kódu:

```cpp
void f() {
    char s[2] = {0}; // C4189. Either use the variable or remove it.
}
```

```Output
warning C4189: 's': local variable is initialized but not referenced
```

Chcete-li chybu opravit, odeberte nepoužitou proměnnou.

### <a name="single-line-comments"></a>Jednořádkový komentář

V aplikaci Visual Studio 2017 verze 15,5 jsou upozornění C4001 a C4179 již vygenerována kompilátorem jazyka C. Dříve byly vygenerovány pouze v rámci **`/Za`** přepínače kompilátoru.  Upozornění již nejsou zapotřebí, protože Jednořádkový komentář byl součástí standardu jazyka C od C99.

```cpp
/* C only */
#pragma warning(disable:4001) //C4619
#pragma warning(disable:4179)
// single line comment
//* single line comment */
```

```Output
warning C4619: #pragma warning: there is no warning number '4001'
```

Pokud kód nemusí být zpětně kompatibilní, můžete se tomuto upozornění vyhnout odebráním potlačení C4001/C4179. Pokud je kód nutné zpětně kompatibilní, potlačit pouze C4619.

```C

/* C only */

#pragma warning(disable:4619)
#pragma warning(disable:4001)
#pragma warning(disable:4179)

// single line comment
/* single line comment */
```

### <a name="__declspec-attributes-with-extern-c-linkage"></a>`__declspec`atributy s `extern "C"` propojením

V dřívějších verzích sady Visual Studio kompilátor ignoroval atributy, `__declspec(...)` kdy `__declspec(...)` byl použit před `extern "C"` specifikací propojení. Toto chování způsobilo, že se kód vygeneroval tímto uživatelem, a to s možnými důsledky pro modul runtime. Upozornění bylo přidáno v aplikaci Visual Studio verze 15,3, ale bylo vypnuto ve výchozím nastavení. V aplikaci Visual Studio 2017 verze 15,5 je upozornění ve výchozím nastavení povoleno.

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

```Output
warning C4768: __declspec attributes before linkage specification are ignored
```

Chcete-li chybu opravit, umístěte specifikaci propojení před atribut __declspec:

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

Toto nové upozornění C4768 se poskytuje na některých hlavičkách Windows SDK, které byly dodávány se sadou Visual Studio 2017 15,3 nebo starší (například: Version 10.0.15063.0, označovanou také jako RS2 SDK). Nicméně novější verze Windows SDK hlaviček (konkrétně ShlObj. h a ShlObj_core. h) byly vyřešeny, aby nevznikly upozornění. Když se zobrazí toto upozornění z Windows SDK hlaviček, můžete provést tyto akce:

1. Přepněte na nejnovější Windows SDK, které byly součástí verze 15,5 sady Visual Studio 2017.

1. Vypněte upozornění kolem #include příkazu Windows SDK hlavičky:

```cpp
   #pragma warning (push)
   #pragma warning(disable:4768)
   #include <shlobj.h>
   #pragma warning (pop)
   ```

### <a name="extern-constexpr-linkage"></a><a name="extern_linkage"></a>Externí propojení constexpr

V dřívějších verzích sady Visual Studio kompilátor vždy přiřadil vnitřní propojení proměnné **constexpr** i v případě, že proměnná byla označena jako **extern**. V aplikaci Visual Studio 2017 verze 15,5 nový přepínač kompilátoru ( **`/Zc:externConstexpr`** ) umožňuje správné chování vyhovující standardům. Nakonec se toto chování stane výchozím nastavením.

```cpp
extern constexpr int x = 10;
```

```Output
error LNK2005: "int const x" already defined
```

Pokud hlavičkový soubor obsahuje proměnnou deklarovanou **extern constexpr**, je nutné označit, `__declspec(selectany)` aby jejich duplicitní deklarace byly správně kombinovány:

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

### <a name="typeid-cant-be-used-on-incomplete-class-type"></a>**typeid** se nedá použít u nekompletního typu třídy.

V dřívějších verzích sady Visual Studio kompilátor nesprávně povolil následující kód, což má za následek potenciálně nesprávné informace o typu. V aplikaci Visual Studio 2017 verze 15,5 kompilátor správně vyvolá chybu:

```cpp
#include <typeinfo>

struct S;

void f() { typeid(S); } //C2027 in 15.5
```

```Output
error C2027: use of undefined type 'S'
```

### <a name="stdis_convertible-target-type"></a>`std::is_convertible`cílový typ

`std::is_convertible`vyžaduje, aby cílový typ byl platný návratový typ. V dřívějších verzích sady Visual Studio kompilátor nesprávně povolil abstraktní typy, což může vést k nesprávnému rozlišení přetížení a neúmyslnému chování za běhu.  Následující kód nyní správně vyvolává C2338:

```cpp
#include <type_traits>

struct B { virtual ~B() = 0; };
struct D : public B { virtual ~D(); };

static_assert(std::is_convertible<D, B>::value, "fail"); // C2338 in 15.5
```

Chcete-li se vyhnout chybě, při použití byste `is_convertible` měli porovnat typy ukazatelů, protože porovnání typu bez ukazatelů může selhat, pokud je jeden typ abstraktní:

```cpp
#include <type_traits>

struct B { virtual ~B() = 0; };
struct D : public B { virtual ~D(); };

static_assert(std::is_convertible<D *, B *>::value, "fail");
```

### <a name="dynamic-exception-specification-removal-and-noexcept"></a><a name="noexcept_removal"></a>Odebrání specifikace dynamické výjimky a **s výjimkou**

V C++ 17 `throw()` je alias pro, **s výjimkou**, `throw(<type list>)` a `throw(...)` jsou odebrány a některé typy mohou obsahovat **výjimku, s výjimkou**. Tato změna může způsobit problémy s kompatibilitou zdroje s kódem, který odpovídá C++ 14 nebo staršímu. **`/Zc:noexceptTypes-`** Přepínač lze použít pro návrat k verzi c++ 14, **s výjimkou** obecného použití režimu c++ 17. Umožňuje aktualizovat zdrojový kód tak, aby odpovídal C++ 17 bez nutnosti přepsat celý `throw()` kód současně.

Kompilátor také nyní diagnostikuje více neshodných specifikací výjimek v deklaracích v režimu C++ 17 nebo pomocí [/Permissive-](../build/reference/permissive-standards-conformance.md) s novým C5043 upozorněním.

Následující kód generuje C5043 a C5040 v aplikaci Visual Studio 2017 verze 15,5 při **`/std:c++17`** použití přepínače:

```cpp
void f() throw(); // equivalent to void f() noexcept;
void f() {} // warning C5043
void g() throw(); // warning C5040

struct A {
    virtual void f() throw();
};

struct B : A {
    virtual void f() { } // error C2694
};
```

Chcete-li chyby odebrat, pokud je stále používáte **`/std:c++17`** , buď přidejte **`/Zc:noexceptTypes-`** přepínač na příkazový řádek, nebo jinak aktualizujte kód tak, aby používal **s výjimkou**, jak je znázorněno v následujícím příkladu:

```cpp
void f() noexcept;
void f() noexcept { }
void g() noexcept(false);

struct A {
    virtual void f() noexcept;
};

struct B : A {
    virtual void f() noexcept { }
};
```

### <a name="inline-variables"></a>Vložené proměnné

Statické datové členy constexpr jsou nyní implicitně vloženy, což znamená, že jejich deklarace v rámci třídy je nyní jejich definicí. Použití definice mimo řádek pro statický datový člen constexpr je redundantní a teď je zastaralé. V aplikaci Visual Studio 2017 verze 15,5, když **`/std:c++17`** je použit přepínač, nyní následující kód vytvoří upozornění C5041 `'size': out-of-line definition for constexpr static data member is not needed and is deprecated in C++17` :

```cpp
struct X {
    static constexpr int size = 3;
};
const int X::size; // C5041
```

### <a name="extern-c-__declspec-warning-c4768-now-on-by-default"></a>`extern "C" __declspec(...)`Služba Warning C4768 nyní ve výchozím nastavení zapnuta

Upozornění bylo přidáno v aplikaci Visual Studio 2017 verze 15,3, ale ve výchozím nastavení bylo vypnuto. Ve Visual Studiu 2017 verze 15,5 je upozornění ve výchozím nastavení zapnuté. Další informace najdete v tématu [nové upozornění na \_ \_ atributy declspec](#declspec).

### <a name="defaulted-functions-and-__declspecnothrow"></a>Výchozí funkce a`__declspec(nothrow)`

Kompilátor dřív povolil deklaraci výchozích funkcí, `__declspec(nothrow)` Pokud příslušné funkce Base/member povolují výjimky. Toto chování je v rozporu s standardem C++ a může způsobit nedefinované chování za běhu. Standard vyžaduje, aby tyto funkce byly definovány jako odstraněné, pokud existuje neshoda specifikace výjimek.  V rámci **`/std:c++17`** , následující kód vyvolává C2280`attempting to reference a deleted function. Function was implicitly deleted because the explicit exception specification is incompatible with that of the implicit declaration.`

```cpp
struct A {
    A& operator=(const A& other) { // No exception specification; this function may throw.
        ...
    }
};

struct B : public A {
    __declspec(nothrow) B& operator=(const B& other) = default;
};

int main()
{
    B b1, b2;
    b2 = b1; // error C2280
}
```

Chcete-li tento kód opravit, buď odeberte __declspec (nethrow) z výchozí funkce, nebo odeberte `= default` a poskytněte definici funkce spolu s jakýmkoli požadovaným zpracováním výjimek:

```cpp
struct A {
    A& operator=(const A& other) {
        // ...
    }
};

struct B : public A {
    B& operator=(const B& other) = default;
};

int main()
{
    B b1, b2;
    b2 = b1;
}
```

### <a name="noexcept-and-partial-specializations"></a>**s výjimkou** a částečně specializace

S **výjimkou** v systému typů se nemůžou kompilovat částečné specializace pro párové konkrétní typy "volatelné", nebo se nepodaří zvolit primární šablonu, protože chybí Částečná specializace pro ukazatele na funkci s výjimkou funkcí.

V takových případech může být nutné přidat další částečnou specializaci pro zpracování ukazatelů **s výjimkou** ukazatelů na funkce a **s výjimkou** ukazatelů na členské funkce. Tato přetížení jsou platná pouze v **`/std:c++17`** režimu. Pokud je nutné provést zpětnou kompatibilitu s C++ 14 a píšete kód, který používají jiní uživatelé, pak byste měli Tato nová přetížení v rámci `#ifdef` direktiv chránit. Pokud pracujete v samostatném modulu, místo použití `#ifdef` ochranných krytů, které můžete s **`/Zc:noexceptTypes-`** přepínačem kompilovat.

Následující kód je zkompilován v rámci **`/std:c++14`** , ale neprojde **`/std:c++17`** `error C2027: use of undefined type 'A<T>'` :

```cpp
template <typename T> struct A;

template <>
struct A<void(*)()>
{
    static const bool value = true;
};

template <typename T>
bool g(T t)
{
    return A<T>::value;
}

void f() noexcept {}

int main()
{
    return g(&f) ? 0 : 1; // C2027
}
```

Následující kód je úspěšný pod **`/std:c++17`** tím, že kompilátor zvolí novou částečnou specializaci `A<void (*)() noexcept>` :

```cpp
template <typename T> struct A;

template <>
struct A<void(*)()>
{
    static const bool value = true;
};

template <>
struct A<void(*)() noexcept>
{
    static const bool value = true;
};

template <typename T>
bool g(T t)
{
    return A<T>::value;
}

void f() noexcept {}

int main()
{
    return g(&f) ? 0 : 1; // OK
}
```

## <a name="bug-fixes-and-other-behavior-changes-in-157"></a><a name="update_157"></a>Opravy chyb a další změny chování v 15,7

### <a name="c17-default-argument-in-the-primary-class-template"></a>C++ 17: výchozí argument v šabloně primární třídy

Tato změna chování je podmínkou pro odvození [argumentu šablony pro šablony třídy – P0091R3](https://wg21.link/p0091r3).

Dříve kompilátor ignoroval výchozí argument v šabloně primární třídy:

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int = 0) {} // Re-definition necessary
```

V **`/std:c++17`** režimu v aplikaci Visual Studio 2017 verze 15,7 se výchozí argument Neignoruje:

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int) {} // Default argument is used
```

### <a name="dependent-name-resolution"></a>Rozlišení závislých názvů

Tato změna chování je podmínkou pro odvození [argumentu šablony pro šablony třídy – P0091R3](https://wg21.link/p0091r3).

V následujícím příkladu kompilátor v aplikaci Visual Studio 15,6 a dřívější překládá `D::type` na `B<T>::type` v šabloně primární třídy.

```cpp
template<typename T>
struct B {
    using type = T;
};

template<typename T>
struct D : B<T*> {
    using type = B<T*>::type;
};
```

Visual Studio 2017 verze 15,7 v **`/std:c++17`** režimu vyžaduje klíčové slovo **TypeName** v příkazu Using v **jazyce** D. Bez **TypeName**, kompilátor vyvolává upozornění C4346: `'B<T*>::type': dependent name is not a type` a Error C2061: `syntax error: identifier 'type'` :

```cpp
template<typename T>
struct B {
    using type = T;
};

template<typename T>
struct D : B<T*> {
    using type = typename B<T*>::type;
};
```

### <a name="c17-nodiscard-attribute---warning-level-increase"></a>C++ 17: `[[nodiscard]]` zvýšení úrovně upozornění atributu

V systému Visual Studio 2017 verze 15,7 v **`/std:c++17`** režimu se úroveň upozornění C4834 `discarding return value of function with 'nodiscard' attribute` zvýšila z w3 na W1. Upozornění můžete zakázat s přetypováním na **void**nebo předáním kompilátoru. **`/wd:4834`**

```cpp
[[nodiscard]] int f() { return 0; }

int main() {
    f(); // warning: discarding return value
         // of function with 'nodiscard'
}
```

### <a name="variadic-template-constructor-base-class-initialization-list"></a>Seznam inicializace základní třídy variadické Template konstruktoru

V předchozích edicích sady Visual Studio byl inicializační seznam tříd variadické Template konstruktoru, který postrádá argumenty šablony, omylem povolen bez chyby. V aplikaci Visual Studio 2017 verze 15,7 je vyvolána chyba kompilátoru.

Následující příklad kódu v aplikaci Visual Studio 2017 verze 15,7 vyvolává chybu C2614: `D<int>: illegal member initialization: 'B' is not a base or member` .

```cpp
template<typename T>
struct B {};

template<typename T>
struct D : B<T>
{

    template<typename ...C>
    D() : B() {} // C2614. Missing template arguments to B.
};

D<int> d;
```

Chcete-li chybu opravit, změňte výraz B () na B \< T> ().

### <a name="constexpr-aggregate-initialization"></a>agregovaná inicializace **constexpr**

Předchozí verze kompilátoru jazyka C++ nesprávně zpracovaly agregovanou inicializaci **constexpr** . Kompilátor přijal neplatný kód, ve kterém měl souhrnný-init-list příliš mnoho prvků a vytvořil pro něj špatný CodeGen. Následující kód je příkladem takového kódu:

```cpp
#include <array>
struct X {
    unsigned short a;
    unsigned char b;
};

int main() {
    constexpr std::array<X, 2> xs = {
        { 1, 2 },
        { 3, 4 }
    };
    return 0;
}
```

V aplikaci Visual Studio 2017 verze 15,7 Update 3 a novější se v předchozím příkladu nyní vyvolává C2078 `too many initializers` . Následující příklad ukazuje, jak opravit kód. Při inicializaci a `std::array` pomocí vnořených seznamů, které jsou v závorkách, zadejte vnitřní pole do složeného seznamu.

```cpp
#include <array>
struct X {
    unsigned short a;
    unsigned char b;
};

int main() {
    constexpr std::array<X, 2> xs = {{ // note double braces
        { 1, 2 },
        { 3, 4 }
    }}; // note double braces
    return 0;
}
```

## <a name="bug-fixes-and-behavior-changes-in-158"></a><a name="update_158"></a>Opravy chyb a změny chování v 15,8

Změny kompilátoru v aplikaci Visual Studio 2017 verze 15,8 jsou opravy chyb a změny chování. Jsou uvedené níže:

### <a name="typename-on-unqualified-identifiers"></a>**TypeName** u nekvalifikovaných identifikátorů

V [`/permissive-`](../build/reference/permissive-standards-conformance.md) režimu spurious klíčová slova **TypeName** pro nekvalifikované identifikátory v definicích šablon aliasů již kompilátor nepřijímá. Následující kód teď vytvoří C7511 `'T': 'typename' keyword must be followed by a qualified name` :

```cpp
template <typename T>
using  X = typename T;
```

Chcete-li chybu opravit, změňte druhý řádek na `using  X = T;` .

### <a name="__declspec-on-right-side-of-alias-template-definitions"></a>`__declspec()`na pravé straně definice šablon aliasů

[__declspec](../cpp/declspec.md) již není povolen na pravé straně definice šablony aliasu. Dříve kompilátor přijal, ale ignoroval tento kód. V případě použití aliasu nikdy nevzniká upozornění na zastarání.

Místo toho se dá použít standardní atribut C++, který je [ \[ \[ \] \] zastaralý](../cpp/attributes.md) , a je v systému Visual Studio 2017 verze 15,6. Následující kód teď vytvoří C2760 `syntax error: unexpected token '__declspec', expected 'type specifier'` :

```cpp
template <typename T>
using X = __declspec(deprecated("msg")) T;
```

Chcete-li chybu opravit, změňte kód na následující (s atributem umístěným před znakem ' = ' definice aliasu):

```cpp
template <typename T>
using  X [[deprecated("msg")]] = T;
```

### <a name="two-phase-name-lookup-diagnostics"></a>Diagnostika se dvěma fázemi vyhledávání názvů

Dvoustupňové vyhledávání názvů vyžaduje, aby se nezávisle používané názvy v subjektech šablony zobrazovaly v šabloně v době definice. V minulosti by kompilátor jazyka Microsoft C++ nechal název, který nebyl nalezen, dokud nebude čas vytvoření instance vyhledán. Nyní vyžaduje, aby názvy, které nejsou závislé, byly svázané v těle šablony.

Jedním ze způsobů, jak to může manifest, je vyhledávání do závislých základních tříd. Dříve kompilátor povolil použití názvů, které jsou definovány v závislých základních třídách. To je proto, že by se během vytváření instance vyhledaly během doby, kdy jsou všechny typy vyřešeny. Teď, když je kód považován za chybu. V těchto případech můžete vynutit, aby se proměnná prohlédla při vytváření instance tím, že je kvalifikována jako typ základní třídy, nebo jinak, aby byla závislá na tom, například přidáním `this->` ukazatele.

V režimu [/Permissive-](../build/reference/permissive-standards-conformance.md) nyní vyvolá následující kód C3861: `'base_value': identifier not found` :

```cpp
template <class T>
struct Base {
    int base_value = 42;
};

template <class T>
struct S : Base<T> {
    int f() {
        return base_value;
    }
};
```

Chcete-li chybu opravit, změňte `return` příkaz na `return this->base_value;` .

**Poznámka:** V knihovně Pythonu pro zvýšení je MSVC alternativní řešení pro dopřednou deklaraci šablony v [unwind_type. HPP](https://github.com/boostorg/python/blame/develop/include/boost/python/detail/unwind_type.hpp). V [`/permissive-`](../build/reference/permissive-standards-conformance.md) režimu Start v aplikaci Visual Studio 2017 verze 15,8 ( \_ MSC \_ ver = 1915) kompilátor MSVC provede správně vyhledávání názvů (ADL) závislých na argumentech. Je teď v souladu s ostatními kompilátory, takže toto alternativní řešení není zbytečné. Chcete-li se vyhnout chybě C3861: `'unwind_type': identifier not found` , viz [PR 229](https://github.com/boostorg/python/pull/229) v úložišti zvýšení úrovně k aktualizaci hlavičkového souboru. Balíček pro zvýšení [vcpkg](../build/vcpkg.md) už jsme aktualizovali, takže pokud získáváte nebo upgradujete zdroje pro zvýšení úrovně od vcpkg, nemusíte tuto opravu instalovat samostatně.

### <a name="forward-declarations-and-definitions-in-namespace-std"></a>dopředné deklarace a definice v oboru názvů`std`

Standard C++ nepovoluje uživateli přidat do oboru názvů dopředné deklarace nebo definice `std` . Výsledkem přidání deklarací nebo definic do oboru názvů `std` nebo oboru názvů v rámci oboru názvů je `std` nedefinované chování.

V některých případech Microsoft přesune umístění, kde jsou definované některé standardní typy knihoven. Tato změna způsobí přerušení stávajícího kódu, který přidá dopředné deklarace do oboru názvů `std` . Nové upozornění, C4643, pomáhá identifikovat takové problémy se zdrojem. Upozornění je povolené v **`/default`** režimu a ve výchozím nastavení je vypnuté. Bude to mít vliv na programy, které jsou kompilovány pomocí **`/Wall`** nebo **`/WX`** .

Následující kód nyní vyvolává C4643: `Forward declaring 'vector' in namespace std is not permitted by the C++ Standard` .

```cpp
namespace std {
    template<typename T> class vector;
}
```

Chcete-li chybu opravit, použijte direktivu **include** namísto dopředné deklarace:

```cpp
#include <vector>
```

### <a name="constructors-that-delegate-to-themselves"></a>Konstruktory, které jsou delegovány samy na sebe

Standard jazyka C++ naznačuje, že by kompilátor měl vyvolat diagnostiku, když se delegování konstruktoru deleguje sám. Kompilátor Microsoft C++ v [/std: C++ 17](../build/reference/std-specify-language-standard-version.md) a [/std: C + + nejnovější](../build/reference/std-specify-language-standard-version.md) režimy teď vyvolává C7535: `'X::X': delegating constructor calls itself` .

Bez této chyby bude zkompilován následující program, ale vygeneruje nekonečnou smyčku:

```cpp
class X {
public:
    X(int, int);
    X(int v) : X(v){}
};
```

Chcete-li se vyhnout nekonečné smyčce, delegovat na jiný konstruktor:

```cpp
class X {
public:

    X(int, int);
    X(int v) : X(v, 0) {}
};
```

### <a name="offsetof-with-constant-expressions"></a>`offsetof`s konstantními výrazy

[OffsetOf](../c-runtime-library/reference/offsetof-macro.md) se tradičně implementoval pomocí makra, které vyžaduje [reinterpret_cast](../cpp/reinterpret-cast-operator.md). Toto použití je neplatné v kontextech, které vyžadují konstantní výraz, ale kompilátor Microsoft C++ je tradičně povolil. `offsetof`Makro, které je dodáváno jako součást standardní knihovny, správně používá vnitřní (**__builtin_offsetof**) kompilátor, ale mnoho lidí použilo štych makra k definování vlastního `offsetof` .

V aplikaci Visual Studio 2017 verze 15,8 kompilátor omezuje oblasti, které tyto `reinterpret_cast` operátory mohou zobrazit ve výchozím režimu, aby kód mohl vyhovovat standardnímu chování C++. V rámci [/Permissive-](../build/reference/permissive-standards-conformance.md)jsou omezení ještě přísnější. Použití výsledku `offsetof` v místech, které vyžadují konstantní výrazy, může mít za následek kód, který vydává upozornění C4644 `usage of the macro-based offsetof pattern in constant expressions is non-standard; use offsetof defined in the C++ standard library instead` nebo C2975 `invalid template argument, expected compile-time constant expression` .

Následující kód vyvolává C4644 v režimech **`/default`** a a **`/std:c++17`** C2975 v režimu [/Permissive-](../build/reference/permissive-standards-conformance.md) :

```cpp
struct Data {
    int x;
};

// Common pattern of user-defined offsetof
#define MY_OFFSET(T, m) (unsigned long long)(&(((T*)nullptr)->m))

int main()

{
    switch (0) {
    case MY_OFFSET(Data, x): return 0;
    default: return 1;
    }
}
```

Chcete-li chybu opravit, použijte, `offsetof` jak je definováno pomocí \< cstddef>:

```cpp
#include <cstddef>

struct Data {
    int x;
};

int main()
{
    switch (0) {
    case offsetof(Data, x): return 0;
    default: return 1;
    }
}
```

### <a name="cv-qualifiers-on-base-classes-subject-to-pack-expansion"></a>kvalifikátory cv na základních třídách podléhající rozšíření balíčku

Předchozí verze kompilátoru jazyka Microsoft C++ nerozpoznaly, že základní třída měla kvalifikátory CV, pokud byla také předmětem rozšíření balení.

V aplikaci Visual Studio 2017 verze 15,8 v režimu [/Permissive-](../build/reference/permissive-standards-conformance.md) následující kód vyvolává C3770 `'const S': is not a valid base class` :

```cpp
template<typename... T>
class X : public T... { };

class S { };

int main()
{
    X<const S> x;
}
```

### <a name="template-keyword-and-nested-name-specifiers"></a>klíčové slovo **šablony** a specifikátory vnořeného názvu

V režimu [/Permissive-](../build/reference/permissive-standards-conformance.md) kompilátor nyní vyžaduje klíčové slovo **template** , aby předcházel název šablony, když přichází po závislém vnořeném specifikátoru názvu.

Následující kód v režimu [/Permissive-](../build/reference/permissive-standards-conformance.md) nyní vyvolává C7510: `'example': use of dependent template name must be prefixed with 'template'. note: see reference to class template instantiation 'X<T>' being compiled` :

```cpp
template<typename T> struct Base
{
    template<class U> void example() {}
};

template<typename T>
struct X : Base<T>
{
    void example()
    {
        Base<T>::example<int>();
    }
};
```

Chcete-li chybu opravit, přidejte klíčové slovo **template** do `Base<T>::example<int>();` příkazu, jak je znázorněno v následujícím příkladu:

```cpp
template<typename T> struct Base
{
    template<class U> void example() {}
};

template<typename T>
struct X : Base<T>
{
    void example()
    {
        // Add template keyword here:
        Base<T>::template example<int>();
    }
};
```

## <a name="bug-fixes-and-behavior-changes-in-159"></a><a name="update_159"></a>Opravy chyb a změny chování v 15,9

### <a name="identifiers-in-member-alias-templates"></a>Identifikátory v šablonách aliasů členů

Identifikátor, který je použit v definici šablony aliasu člena, musí být deklarován před použitím.

V předchozích verzích kompilátoru byl povolen následující kód:

```cpp
template <typename... Ts>
struct A
{
  public:
    template <typename U>
    using from_template_t = decltype(from_template(A<U>{}));

  private:
    template <template <typename...> typename Type, typename... Args>
    static constexpr A<Args...> from_template(A<Type<Args...>>);
};

A<>::from_template_t<A<int>> a;
```

V aplikaci Visual Studio 2017 verze 15,9 v [`/permissive-`](../build/reference/permissive-standards-conformance.md) režimu vyvolává kompilátor C3861: `'from_template': identifier not found` .

Chcete-li chybu opravit, deklarujte ji `from_template` `from_template_t` .

### <a name="modules-changes"></a>Změny modulů

V aplikaci Visual Studio 2017 verze 15,9 kompilátor vyvolá C5050 vždy, když parametry příkazového řádku pro moduly nejsou konzistentní mezi vytvářením modulů a na straně spotřeby modulu. V následujícím příkladu jsou k dispozici dva problémy:

- Na straně spotřeby (Main. cpp) **`/EHsc`** není možnost určena.

- Verze C++ je **`/std:c++17`** na straně vytváření a **`/std:c++14`** na straně spotřeby.

```cmd
cl /EHsc /std:c++17 m.ixx /experimental:module
cl /experimental:module /module:reference m.ifc main.cpp /std:c++14
```

Kompilátor vyvolává C5050 pro oba tyto případy: `warning C5050: Possible incompatible environment while importing module 'm': mismatched C++ versions.  Current "201402" module version "201703"` .

Kompilátor také vyvolává C7536 vždy, když je soubor. IFC zfalšován. Hlavička rozhraní modulu obsahuje hodnotu hash SHA2 obsahu pod ním. Při importu se soubor. IFC vyhodnotí jako hash a pak se zaškrtne proti hodnotě hash uvedené v hlavičce. Pokud se neshodují, je vyvolána chyba C7536: `ifc failed integrity checks.  Expected SHA2: '66d5c8154df0c71d4cab7665bab4a125c7ce5cb9a401a4d8b461b706ddd771c6'` .

### <a name="partial-ordering-involving-aliases-and-non-deduced-contexts"></a>Částečné řazení zahrnující aliasy a Neodvozená kontextová

Implementace se odchylují v pravidlech částečného řazení, které zahrnují aliasy v neodvozených kontextech. V následujícím příkladu si RSZ a kompilátor Microsoft C++ (v [`/permissive-`](../build/reference/permissive-standards-conformance.md) režimu) vyvolávají chybu, zatímco Clang akceptuje kód.

```cpp
#include <utility>
using size_t = std::size_t;

template <typename T>
struct A {};
template <size_t, size_t>
struct AlignedBuffer {};
template <size_t len>
using AlignedStorage = AlignedBuffer<len, 4>;

template <class T, class Alloc>
int f(Alloc &alloc, const AlignedStorage<T::size> &buffer)
{
    return 1;
}

template <class T, class Alloc>
int f(A<Alloc> &alloc, const AlignedStorage<T::size> &buffer)
{
    return 2;
}

struct Alloc
{
    static constexpr size_t size = 10;
};

int main()
{
    A<void> a;
    AlignedStorage<Alloc::size> buf;
    if (f<Alloc>(a, buf) != 2)
    {
        return 1;
    }

    return 0;
}
```

Předchozí příklad vyvolává C2668:

```Output
partial_alias.cpp(32): error C2668: 'f': ambiguous call to overloaded function
partial_alias.cpp(18): note: could be 'int f<Alloc,void>(A<void> &,const AlignedBuffer<10,4> &)'
partial_alias.cpp(12): note: or       'int f<Alloc,A<void>>(Alloc &,const AlignedBuffer<10,4> &)'
        with
        [
            Alloc=A<void>
        ]
partial_alias.cpp(32): note: while trying to match the argument list '(A<void>, AlignedBuffer<10,4>)'
```

Rozdíl implementace je z důvodu regrese ve standardním dělení jazyka C++. Řešení problému Core 2235 odebralo nějaký text, který by umožňoval řazení těchto přetížení. Aktuální Standard C++ neposkytuje mechanismus pro částečné řazení těchto funkcí, takže jsou považovány za dvojznačné.

Alternativním řešením je, že při řešení tohoto problému doporučujeme nespoléhat na částečné řazení. Místo toho použijte SFINAE k odebrání určitých přetížení. V následujícím příkladu používáme pomocnou třídu `IsA` k odebrání prvního přetížení, pokud `Alloc` je specializace `A` :

```cpp
#include <utility>
using size_t = std::size_t;

template <typename T>
struct A {};
template <size_t, size_t>
struct AlignedBuffer {};
template <size_t len>
using AlignedStorage = AlignedBuffer<len, 4>;

template <typename T> struct IsA : std::false_type {};
template <typename T> struct IsA<A<T>> : std::true_type {};

template <class T, class Alloc, typename = std::enable_if_t<!IsA<Alloc>::value>>
int f(Alloc &alloc, const AlignedStorage<T::size> &buffer)
{
    return 1;
}

template <class T, class Alloc>
int f(A<Alloc> &alloc, const AlignedStorage<T::size> &buffer)
{
    return 2;
}

struct Alloc
{
    static constexpr size_t size = 10;
};

int main()
{
    A<void> a;
    AlignedStorage<Alloc::size> buf;
    if (f<Alloc>(a, buf) != 2)
    {
        return 1;
    }

    return 0;
}
```

### <a name="illegal-expressions-and-non-literal-types-in-templated-function-definitions"></a>Neplatné výrazy a typy bez literálů v definicích šablonových funkcí

Neplatné výrazy a typy, které nejsou literály, jsou nyní správně diagnostikovány v definicích funkcí založených na šablonách, které jsou explicitně specializované. Dříve tyto chyby nebyly vygenerovány pro definici funkce. Neplatný výraz nebo typ bez literálu by však byl stále diagnostikován, pokud je vyhodnocen jako součást konstantního výrazu.

V předchozích verzích sady Visual Studio se následující kód zkompiluje bez upozornění:

```cpp
void g();

template<typename T>
struct S
{
    constexpr void f();
};

template<>
constexpr void S<int>::f()
{
    g(); // C3615 in 15.9
}
```

V aplikaci Visual Studio 2017 verze 15,9 kód vyvolá tuto chybu:

```Output
error C3615: constexpr function 'S<int>::f' cannot result in a constant expression.
note: failure was caused by call of undefined function or one not declared 'constexpr'
note: see usage of 'g'.
```

Chcete-li se této chybě vyhnout, odeberte kvalifikátor **constexpr** z explicitního vytváření instancí funkce `f()` .

::: moniker-end

::: moniker range="vs-2015"

## <a name="c-conformance-improvements-in-visual-studio-2015"></a>Vylepšení shody C++ v aplikaci Visual Studio 2015

Máme úplný seznam vylepšení shody v rámci sady Visual Studio 2015 Update 3. Další informace najdete v tématu [Visual C++ novinky 2003 až 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015).

::: moniker-end

## <a name="see-also"></a>Viz také

[Tabulka shody jazyka Microsoft C++](../visual-cpp-language-conformance.md)
