---
title: Vylepšení shody c++
ms.date: 03/16/2020
description: Microsoft C++ v sadě Visual Studio postupuje směrem k úplné shodě s jazykovým standardem C++20.
ms.technology: cpp-language
ms.openlocfilehash: 2309e79acb4784cd2e79b4f3f6fffb29e8d5dea8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353540"
---
# <a name="c-conformance-improvements-in-visual-studio"></a>Vylepšení shody C++ se sadou Visual Studio

Microsoft C++ provádí vylepšení shody a opravy chyb v každé verzi. Tento článek uvádí vylepšení podle hlavní verze, pak podle verze. Obsahuje také seznam hlavních oprav chyb podle verze. Chcete-li přejít přímo na změny pro konkrétní verzi, použijte v seznamu **V tomto článku.**

::: moniker range="vs-2019"

## <a name="conformance-improvements-in-visual-studio-2019-rtw-version-160"></a><a name="improvements_160"></a>Vylepšení shody ve Visual Studiu 2019 RTW (verze 16.0)

Visual Studio 2019 RTW obsahuje následující vylepšení shody, opravy chyb a změny chování v kompilátoru Microsoft C++ (MSVC)

**Poznámka:** Funkce jazyka C++20 budou `/std:c++latest` k dispozici v režimu, dokud nebude dokončena implementace jazyka C++20 pro kompilátor i technologie IntelliSense. V té době `/std:c++20` bude zaveden režim kompilátoru.

### <a name="improved-modules-support-for-templates-and-error-detection"></a>Vylepšená podpora modulů pro šablony a detekci chyb

Moduly jsou nyní oficiálně ve standardu C++20. Vylepšená podpora byla přidána ve Visual Studiu 2017 verze 15.9. Další informace naleznete [v tématu Lepší podpora šablon a zjišťování chyb v modulech C++ s MSVC 2017 verze 15.9](https://devblogs.microsoft.com/cppblog/better-template-support-and-error-detection-in-c-modules-with-msvc-2017-version-15-9/).

### <a name="modified-specification-of-aggregate-type"></a>Upravená specifikace souhrnného typu

Specifikace typu agregace se v jazyce C++20 změnila (viz [Zakázat agregace s konstruktory deklarovanými uživatelem).](https://wg21.link/p1008r1) V sadě Visual Studio 2019, v části `/std:c++latest`, třída s libovolným konstruktorem deklarovaným uživatelem (například včetně deklarovaného `= default` konstruktoru nebo `= delete`) není agregace. Dříve pouze konstruktory poskytované uživatelem by diskvalifikovat třídy z agregace. Tato změna klade další omezení na to, jak tyto typy mohou být inicializovány.

Následující kód zkompiluje bez chyb v Sadě Visual Studio 2017, ale vyvolá chyby C2280 a C2440 v Sadě Visual Studio 2019 v části `/std:c++latest`:

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

### <a name="partial-support-for-operator-"></a>Částečná podpora`operator <=>`

[P0515R3](https://wg21.link/p0515r3) C++20 zavádí `<=>` třícestný operátor pro porovnávání, známý také jako "kosmický operátor". Visual Studio 2019 v `/std:c++latest` režimu zavádí částečnou podporu pro operátor vyvoláním chyb pro syntaxi, která je nyní zakázána. Například následující kód zkompiluje bez chyb v Sadě Visual Studio 2017, ale vyvolá více chyb v Sadě Visual Studio 2019 v části `/std:c++latest`:

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

Chcete-li se vyhnout chybám, vložte mezeru do `U<&S::operator<= > u;`problematické čáry před konečnou úhlovou závorku: .

### <a name="references-to-types-with-mismatched-cv-qualifiers"></a>Odkazy na typy s neodpovídající cv-kvalifikátory

Dříve MSVC povoleno přímé vazby odkazu z typu s neodpovídající cv kvalifikátory pod nejvyšší úroveň. Tato vazba by mohla umožnit změnu údajně const data uvedená odkazem. Kompilátor nyní vytvoří dočasné, jak to vyžaduje standard. V sadě Visual Studio 2017 se bez upozornění zkompiluje následující kód. V sadě Visual Studio 2019 kompilátor vyvolá *upozornění C4172: \<func:#1 "?PData@X @@QBEABQBXXZ"> vracející se adresu místní proměnné nebo dočasné*.

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

Argument `reinterpret_cast` do není jedním z kontextů, ve kterém je povolena adresa přetížené funkce. Následující kód zkompiluje bez chyb v Sadě Visual Studio 2017, ale v Visual Studiu 2019 vyvolá *C2440: nelze převést z "přetížené funkce" na 'fp'*:

```cpp
int f(int) { return 1; }
int f(float) { return .1f; }
using fp = int(*)(int);

int main()
{
    fp r = reinterpret_cast<fp>(&f);
}
```

Chcete-li se vyhnout chybě, použijte povolené přetypované pro tento scénář:

```cpp
int f(int);
int f(float);
using fp = int(*)(int);

int main()
{
    fp r = static_cast<fp>(&f); // or just &f;
}
```

### <a name="lambda-closures"></a>Uzávěry Lambda

V jazyce C++ 14 lambda typy uzavření nejsou literály. Primárním důsledkem tohoto pravidla je, že lambda nemusí být přiřazena k proměnné **constexpr.** Následující kód zkompiluje bez chyb v Sadě Visual Studio 2017, ale v Visual Studiu 2019 vyvolává *C2127: 'l': neplatná inicializace 'constexpr' entity s nekonstantní výraz*:

```cpp
int main()
{
    constexpr auto l = [] {}; // C2127 in VS2019
}
```

Chcete-li se vyhnout chybě, odeberte kvalifikátor **constexpr** nebo změňte režim shody na `/std:c++17`.

### <a name="stdcreate_directory-failure-codes"></a>`std::create_directory`chybové kódy

Implementována [P1164](https://wg21.link/p1164r1) z C ++ 20 bezpodmínečně. Tím `std::create_directory` se změní kontrola, zda cíl byl již adresář na selhání. Dříve byly všechny chyby typu ERROR_ALREADY_EXISTS převedeny na kódy s úspěchem, ale adresářem, které nebyly vytvořeny.

### `operator<<(std::ostream, nullptr_t)`

Za [LWG 2221](https://cplusplus.github.io/LWG/issue2221), přidán pro `operator<<(std::ostream, nullptr_t)` zápis nullptrs do datových proudů.

### <a name="additional-parallel-algorithms"></a>Další paralelní algoritmy

Nové paralelní verze `is_sorted` `is_sorted_until`, `is_partitioned` `set_difference`, `set_intersection` `is_heap`, `is_heap_until`, a .

### <a name="atomic-initialization"></a>atomová inicializace

[P0883 "Oprava atomické inicializace"](https://wg21.link/p0883r1) změní `std::atomic` na hodnotu inicializovat obsažené T spíše než výchozí inicializace. Oprava je povolena při použití Clang/LLVM se standardní knihovnou společnosti Microsoft. Aktuálně je zakázánpro kompilátor Microsoft C++jako řešení chyby při zpracování **constexpr.**

### <a name="remove_cvref-and-remove_cvref_t"></a>`remove_cvref` a `remove_cvref_t`

`remove_cvref` Implementováno `remove_cvref_t` a typové vlastnosti z [P0550](https://wg21.link/p0550r2). Tyto odstranit reference a cv-kvalifikace z typu bez rozkládající se `std::decay` funkce `std::decay_t`a pole na ukazatele (na rozdíl od a ).

### <a name="feature-test-macros"></a>Makra testování funkcí

[P0941R2 - makra testu funkcí](https://wg21.link/p0941r2) je `__has_cpp_attribute`dokončena s podporou . Makra testu funkcí jsou podporována ve všech standardních režimech.

### <a name="prohibit-aggregates-with-user-declared-constructors"></a>Zakázat agregace s konstruktory deklarovanými uživatelem

[C++ 20 P1008R1 - zákaz agregace s konstruktory deklarovanými uživatelem](https://wg21.link/p1008r1) je dokončena.

## <a name="conformance-improvements-in-161"></a><a name="improvements_161"></a>Zlepšení shody v 16.1

### <a name="char8_t"></a>char8_t

[P0482r6](https://wg21.link/p0482r6). C++ 20 přidá nový typ znaku, který se používá k reprezentaci jednotek kódu UTF-8. `u8`řetězcové literály v jazyce `const char8_t[N]` C++20 mají typ namísto `const char[N]`, což byl předchozí případ. Podobné změny byly navrženy pro normu C v [N2231](https://wg14.link/n2231). Návrhy `char8_t` na zpětnou kompatibilitu nápravy jsou uvedeny v [P1423r3](https://wg21.link/p1423r3). Kompilátor Microsoft C++ `char8_t` přidá podporu v sadě Visual Studio 2019 verze 16.1 při zadání možnosti kompilátoru **/Zc:char8_t.** V budoucnu bude podporován [/std:c++latest](../build/reference/std-specify-language-standard-version.md), které lze vrátit k chování Jazyka C++17 prostřednictvím **/Zc:char8_t-**. Kompilátor EDG, který pohání IntelliSense, jej ještě nepodporuje, takže uvidíte falešné chyby pouze intelliSense, které nemají vliv na skutečnou kompilaci.

#### <a name="example"></a>Příklad

```cpp
const char* s = u8"Hello"; // C++17
const char8_t* s = u8"Hello"; // C++20
```

### <a name="stdtype_identity-metafunction-and-stdidentity-function-object"></a>std::type_identity metafunkce a std::objekt funkce identity

[P0887R1 type_identity](https://wg21.link/p0887r1). Zastaralé rozšíření šablony `std::identity` třídy bylo odebráno a nahrazeno metafunkčním `std::type_identity` a `std::identity` funkčním objektem c++20. Obě jsou k dispozici pouze pod [/std:c++latest](../build/reference/std-specify-language-standard-version.md).

Následující příklad vytváří upozornění na vyřazení C4996 pro `std::identity` (definované v \<type_traits>) v sadě Visual Studio 2017:

```cpp
#include <type_traits>

using T = std::identity<int>::type;
T x, y = std::identity<T>{}(x);
int i = 42;
long j = std::identity<long>{}(i);
```

Následující příklad ukazuje, jak `std::identity` používat nový \<(definovaný ve funkční>) spolu s novým `std::type_identity`:

```cpp
#include <type_traits>
#include <functional>

using T = std::type_identity<int>::type;
T x, y = std::identity{}(x);
int i = 42;
long j = static_cast<long>(i);
```

### <a name="syntax-checks-for-generic-lambdas"></a>Kontroly syntaxe obecných lambdů

Nový procesor lambda umožňuje některé syntaktické kontroly režimu shody v obecných lambdách, v části [/std:c++latest](../build/reference/std-specify-language-standard-version.md) nebo v jiném jazykovém režimu s **/experimental:newLambdaProcessor**.

V Sadě Visual Studio 2017 se tento kód zkompiluje bez upozornění, ale v Visual Studiu 2019 způsobí chybu *syntaxe C2760: neočekávaný token '\<id-expr>', očekávaný výraz id :*

```cpp
void f() {
    auto a = [](auto arg) {
        decltype(arg)::Type t;
    };
}
```

Následující příklad ukazuje správnou syntaxi, kterou nyní kompilátor vynucuje:

```cpp
void f() {
    auto a = [](auto arg) {
        typename decltype(arg)::Type t;
    };
}
```

### <a name="argument-dependent-lookup-for-function-calls"></a>Vyhledávání pro volání funkcí závislé na argumentech

[P0846R0](https://wg21.link/p0846r0) (C++20) Zvýšena schopnost najít šablony funkcí pomocí vyhledávání závislého na argumentech pro výrazy volání funkce s explicitními argumenty šablony. Vyžaduje **/std:c++latest**.

### <a name="designated-initialization"></a>Určená inicializace

[P0329R4](https://wg21.link/p0329r4) (C++20) Určená inicializace umožňuje výběr určitých `Type t { .member = expr }` členů v souhrnné inicializaci pomocí syntaxe. Vyžaduje **/std:c++latest**.

### <a name="new-and-updated-standard-library-functions-c20"></a>Nové a aktualizované standardní funkce knihovny (C++20)

- `starts_with()`a `ends_with()` `basic_string` pro `basic_string_view`a .
- `contains()` pro asociativní kontejnery.
- `remove()`, `remove_if()` a `unique()` pro `list` a `forward_list` teď vrací `size_type`.
- `shift_left()`a `shift_right()` přidány \<do> algoritmu.

## <a name="conformance-improvements-in-162"></a><a name="improvements_162"></a>Zlepšení shody v 16.2

### <a name="noexcept-constexpr-functions"></a>noexcept constexpr funkce

Constexpr funkce již nejsou považovány za **noexcept** ve výchozím nastavení při použití v konstantní výraz. Tato změna chování pochází z rozlišení [CWG 1351](https://wg21.link/cwg1351) a je povolena v [/tolerantní-](../build/reference/permissive-standards-conformance.md). Následující příklad zkompiluje ve Visual Studiu 2019 verze 16.1 a starší, ale produkuje C2338 v Visual Studiu 2019 verze 16.2:

```cpp
constexpr int f() { return 0; }

int main() {
    static_assert(noexcept(f()), "f should be noexcept"); // C2338 in 16.2
}
```

Chcete-li chybu opravit, přidejte výraz **noexcept** do deklarace funkce:

```cpp
constexpr int f() noexcept { return 0; }

int main() {
    static_assert(noexcept(f()), "f should be noexcept");
}
```

### <a name="binary-expressions-with-different-enum-types"></a>Binární výrazy s různými typy výčtu

Možnost použít obvyklé aritmetické převody na operandy, kde jeden je typu výčtu a druhý je jiného typu výčtu nebo typ s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou třídou je v jazyce C++20 ([P1120R0](https://wg21.link/p1120r0)) zastaral. V sadě Visual Studio 2019 verze 16.2 a novější, následující kód vytváří úroveň 4 upozornění, pokud je povolena možnost [/std:c++nejnovější](../build/reference/std-specify-language-standard-version.md) kompilátor:

```cpp
enum E1 { a };
enum E2 { b };
int main() {
    int i = a | b; // warning C5054: operator '|': deprecated between enumerations of different types
}
```

Chcete-li se vyhnout upozornění, použijte [static_cast](../cpp/static-cast-operator.md) převést druhý operand:

```cpp
enum E1 { a };
enum E2 { b };
int main() {
  int i = a | static_cast<int>(b);
}
```

### <a name="binary-expressions-with-enumeration-and-floating-point-types"></a>Binární výrazy s výčtem a typy s plovoucí desetinnou táhou

Možnost použít obvyklé aritmetické převody na operandy, kde jeden je typu výčtu a druhý je jiného typu výčtu nebo typ s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou třídou je v jazyce C++20 ([P1120R0](https://wg21.link/p1120r0)) zastaral. Jinými slovy, použití binární operace mezi výčtem a typem s plovoucí desetinnou desetinnou hodnou je nyní upozorněním, pokud je povolena možnost kompilátoru [/std:c++:](../build/reference/std-specify-language-standard-version.md)

```cpp
enum E1 { a };
int main() {
  double i = a * 1.1;
}
```

Chcete-li se vyhnout upozornění, použijte [static_cast](../cpp/static-cast-operator.md) převést druhý operand:

```cpp
enum E1 { a };
int main() {
   double i = static_cast<int>(a) * 1.1;
}
```

### <a name="equality-and-relational-comparisons-of-arrays"></a>Rovnost a relační porovnání polí

Rovnost a relační porovnání mezi dvěma operandy typu pole jsou zastaralé v Jazyce C++20 ([P1120R0).](https://wg21.link/p1120r0) Jinými slovy, operace porovnání mezi dvěma poli (bez ohledu na pořadí a rozsah podobnosti) je nyní upozornění. Počínaje Visual Studio 2019 verze 16.2, následující kód vytváří *C5056: operátor '==': zastaralé pro typy polí,* pokud je povolena možnost [/std:c++latest](../build/reference/std-specify-language-standard-version.md) kompilátor:

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

Chcete-li zjistit, zda je obsah dvou polí stejný, použijte funkci [std::equal:](../standard-library/algorithm-functions.md#equal)

```cpp
std::equal(std::begin(a), std::end(a), std::begin(b), std::end(b));
```

### <a name="effect-of-defining-spaceship-operator-on--and-"></a>Vliv definování kosmické lodi na == a !=

Definice samotného provozovatele kosmické**<=>** lodi ( ) již nebude **==** přepisovat výrazy zahrnující nebo **!=** pokud není provozovatel kosmické lodi označen jako `= default` ([P1185R2](https://wg21.link/p1185r2)). Následující příklad zkompiluje v Sadě Visual Studio 2019 RTW a verze 16.1, ale produkuje C2678 v Visual Studio 2019 verze 16.2:

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

Chcete-li se vyhnout chybě, definujte operátor== nebo jej deklarujte jako výchozí:

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

### <a name="standard-library-improvements"></a>Standardní vylepšení knihovny

- \<charconv `to_chars()`> s pevnou/vědeckou přesností. (Obecná přesnost je v současné době plánována na 16.4.)
- [P0020R6](https://wg21.link/p0020r6):\<atomová\<plováková>, atomová dvojitá>, atomová\<dlouhá dvojitá>
- [P0463R1](https://wg21.link/p0463r1): endian
- [P0482R6](https://wg21.link/p0482r6): Podpora knihovny pro char8_t
- [P0600R1](https://wg21.link/p0600r1):\[[ nodiscard]] Pro STL, část 1
- [P0653R2](https://wg21.link/p0653r2): to_address()
- [P0754R2](https://wg21.link/p0754r2) \<: verze>
- [P0771R1](https://wg21.link/p0771r1): noexcept For std::function's move constructor

## <a name="conformance-improvements-in-visual-studio-2019-version-163"></a><a name="improvements_163"></a>Vylepšení shody ve Visual Studiu 2019 verze 16.3

### <a name="stream-extraction-operators-for-char-removed"></a>Operátory extrakce datového proudu pro znak* odstraněny

Operátory extrakce datového proudu pro ukazatele na znaky byly odebrány a nahrazeny operátory extrakce pro pole znaků (na [P0487R1).](https://wg21.link/p0487r1) WG21 považuje odstraněné přetížení za nebezpečné. V [/std:c++latest](../build/reference/std-specify-language-standard-version.md) režimu, následující příklad nyní produkuje *C2679: binární '>>': žádný operátor nalezen,\*který má pravé operand typu 'char ' (nebo není přijatelný převod)*:

```cpp
   char x[42];
   char* p = x;
   std::cin >> std::setw(42);
   std::cin >> p;
```

Chcete-li se vyhnout chybě, použijte operátor extrakce s proměnnou char[] :

```cpp
char x[42];
std::cin >> x;
```

### <a name="new-keywords-requires-and-concept"></a>Nová klíčová slova **vyžaduje** a **koncept**

Nová klíčová slova **vyžaduje** a **koncept** byly přidány do kompilátoru Microsoft C++. Pokud se pokusíte použít jeden z nich jako identifikátor v [/std:c++latest](../build/reference/std-specify-language-standard-version.md) režimu, kompilátor vyvolá *C2059: syntaktická chyba*.

### <a name="constructors-as-type-names-disallowed"></a>Konstruktory jako názvy typů zakázány

Názvy konstruktorů již nejsou považovány za vložené názvy tříd, pokud se zobrazí v kvalifikovaném názvu za alias specializace šablony třídy. To dříve umožnilo použití konstruktorů jako názvu typu k deklarování jiných entit. Následující příklad nyní vytváří *C3646: 'TotalDuration': neznámý specifikátor přepsání*:

```cpp
#include <chrono>

class Foo {
   std::chrono::milliseconds::duration TotalDuration{};
};

```

Chcete-li se `TotalDuration` vyhnout chybě, deklarujte, jak je znázorněno zde:

```cpp
#include <chrono>

class Foo {
  std::chrono::milliseconds TotalDuration {};
};
```

### <a name="stricter-checking-of-extern-c-functions"></a>Přísnější kontrola extern "C" funkcí

Pokud **extern "C"** funkce byla deklarována v různých oborech názvů, předchozí verze kompilátoru Microsoft C++ nekontroloval, zda deklarace byly kompatibilní. Ve Visual Studiu 2019 verze 16.3 kompilátor provede takovou kontrolu. V [/tolerantní-](../build/reference/permissive-standards-conformance.md) režimu následující kód vytváří *C2371 : předefinování; různé základní typy* a *C2733 nelze přetížení funkce s C propojení*:

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

Chcete-li se vyhnout chybám v předchozím příkladu, použijte **bool** místo **BOOL** konzistentně v obou deklaracích `f`.

### <a name="standard-library-improvements"></a>Standardní vylepšení knihovny

Nestandardní hlavičky \<stdexcpt.h> \<a typeinfo.h> byly odebrány. Kód, který je obsahuje, by \<měl \<místo toho obsahovat výjimku standardních záhlaví> a typeinfo>.

## <a name="conformance-improvements-in-visual-studio-2019-version-164"></a><a name="improvements_164"></a>Vylepšení shody ve Visual Studiu 2019 verze 16.4

### <a name="better-enforcement-of-two-phase-name-lookup-for-qualified-ids-in-permissive-"></a>Lepší vynucování dvoufázového vyhledávání názvů pro kvalifikované idy v /tolerantní-

Dvoufázové vyhledávání názvů vyžaduje, aby nezávislé názvy používané v tělech šablony byly viditelné pro šablonu v době definice. Dříve tyto názvy mohly být nalezeny při vytvoření instance šablony. Tato změna usnadňuje zápis přenosné, konformní kód v MSVC pod [/tolerantní-](../build/reference/permissive-standards-conformance.md) příznak.

V sadě Visual Studio 2019 verze 16.4 s **/tolerantní-** příznak set, `N::f` následující příklad vytvoří `f<T>` chybu, protože není viditelná, když je definována šablona:

```cpp
template <class T>
int f() {
    return N::f() + T{}; // error C2039: 'f': is not a member of 'N'
}

namespace N {
    int f() { return 42; }
}
```

Obvykle to lze opravit zahrnutím chybějících hlaviček nebo funkcí nebo proměnných deklarování dopředu, jak je znázorněno v následujícím příkladu:

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

### <a name="implicit-conversion-of-integral-constant-expressions-to-null-pointer"></a>Implicitní převod integrálních konstantních výrazů na ukazatel null

Kompilátor MSVC nyní implementuje [CWG Issue 903](https://wg21.link/cwg903) v režimu shody (/tolerantní-). Toto pravidlo zakazuje implicitní převod integrálních konstantních výrazů (s výjimkou celého literálu '0') na konstanty ukazatele null. Následující příklad vytváří C2440 v režimu shody:

```cpp
int* f(bool* p) {
    p = false; // error C2440: '=': cannot convert from 'bool' to 'bool *'
    p = 0; // OK
    return false; // error C2440: 'return': cannot convert from 'bool' to 'int *'
}
```

Chcete-li chybu opravit, použijte **nullptr** místo **false**. Všimněte si, že literál 0 je stále povolen:

```cpp
int* f(bool* p) {
    p = nullptr; // OK
    p = 0; // OK
    return nullptr; // OK
}
```

### <a name="standard-rules-for-types-of-integer-literals"></a>Standardní pravidla pro typy literál celéčíslo

V režimu shody (povoleno [/tolerantní-](../build/reference/permissive-standards-conformance.md)), MSVC používá standardní pravidla pro typy celočíselných literál. Dříve desetinné literály příliš velké, aby se vešly do podepsané 'int' dostali typ 'nepodepsané int'. Nyní jsou tyto literály uvedeny další největší podepsaný typ celého čísla, "dlouhý dlouhý". Kromě toho literály s příponou 'll', které jsou příliš velké, aby se vešly do podepsaného typu jsou uvedeny typu 'nepodepsané dlouho'.

To může vést k generování různých diagnostik varování a rozdíly v chování pro aritmetické operace prováděné na literály.

Následující příklad ukazuje nové chování v Sadě Visual Studio 2019, verze 16.4. Proměnná `i` je typu **nepodepsané int** a proto je aktivována upozornění. Bity vyššího řádu proměnné `j` jsou nastaveny na 0.

```cpp
void f(int r) {
    int i = 2964557531; // warning C4309: truncation of constant value
    long long j = 0x8000000000000000ll >> r; // literal is now unsigned, shift will fill high-order bits with 0
}
```

Následující příklad ukazuje, jak zachovat staré chování a vyhnout se tedy upozornění a změně chování za běhu:

```cpp
void f(int r) {
int i = 2964557531u; // OK
long long j = (long long)0x8000000000000000ll >> r; // shift will keep high-order bits
}
```

### <a name="function-parameters-that-shadow-template-parameters"></a>Parametry funkce, které parametry stínové šablony

Kompilátor MSVC nyní vyvolá chybu, když parametr funkce stíny parametr šablony:

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

### <a name="user-provided-specializations-of-type-traits"></a>Uživatelsky poskytované specializace typových vlastností

V souladu s *meta.rqmts* podklauzule standardu, Kompilátor MSVC nyní vyvolá chybu, když narazí na `type_traits` uživatelem `std` definovanou specializaci jedné ze zadaných šablon v oboru názvů. Není-li uvedeno jinak, tyto specializace za následek nedefinované chování. Následující příklad má nedefinované chování, protože porušuje `static_assert` pravidlo a selže s chybou **C2338**.

```cpp
#include <type_traits>
struct S;

template<>
struct std::is_fundamental<S> : std::true_type {};

static_assert(std::is_fundamental<S>::value, "fail");
```

Chcete-li se vyhnout chybě, definujte strukturu, která dědí z upřednostňované `type_trait`, a specializovat, že:

```cpp
#include <type_traits>

struct S;

template<typename T>
struct my_is_fundamental : std::is_fundamental<T> {};

template<>
struct my_is_fundamental<S> : std::true_type { };

static_assert(my_is_fundamental<S>::value, "fail");
```

### <a name="changes-to-compiler-provided-comparison-operators"></a>Změny operátorů porovnání poskytovaných kompilátorem

Kompilátor MSVC nyní implementuje následující změny operátorů porovnání na [P1630R1,](https://wg21.link/p1630r1) pokud je [povolena /std:c++latest](../build/reference/std-specify-language-standard-version.md) option:

Kompilátor již nepřepisuje `operator==` výrazy pomocí, pokud zahrnují návratový typ, který není **bool**. Následující kód nyní vytváří *chybu C2088: '!=': illegal pro strukturu*:

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

Chcete-li se vyhnout chybě, je nutné explicitně definovat potřebný operátor:

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

Kompilátor již definuje výchozí operátor porovnání, pokud je členem třídy podobné sjednocení. Následující příklad nyní produkuje *C2120: 'void' nezákonné se všemi typy*:

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

Chcete-li se vyhnout chybě, definujte tělo pro operátora:

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

Kompilátor již nebude definovat výchozí operátor porovnání, pokud třída obsahuje referenční člen. Následující kód nyní vytváří *chybu C2120: 'void' nezákonné se všemi typy*:

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

Chcete-li se vyhnout chybě, definujte tělo pro operátora:

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

## <a name="conformance-improvements-in-visual-studio-2019-version-165"></a><a name="improvements_165"></a>Vylepšení shody ve Visual Studiu 2019 verze 16.5

### <a name="explicit-specialization-declaration-without-an-initializer-is-not-a-definition"></a>Explicitní specializační deklarace bez inicializátoru není definice

V `/permissive-`rámci , MSVC nyní vynucuje standardní pravidlo, že explicitní specializace deklarace bez inicializace nejsou definice. Dříve deklarace by být považovány za definici s výchozí inicializátor. Efekt je pozorovatelný v době propojení, protože program v závislosti na tomto chování může nyní mít nevyřešené symboly. Tento příklad má nyní za následek chybu:

```cpp
template <typename> struct S {
    static int a;
};

// In permissive-, this declaration is not a definition and the program will not link.
template <> int S<char>::a;

int main() {
    return S<char>::a;
}
```

```Output
error LNK2019: unresolved external symbol "public: static int S<char>::a" (?a@?$S@D@@2HA) referenced in function _main
at link time.
```

Chcete-li problém vyřešit, přidejte inicializátor:

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

### <a name="preprocessor-output-preserves-newlines"></a>Výstup preprocesoru zachovává nové řádky

Experimentální preprocesor nyní zachovává nové řádky `/P` a `/E` `/experimental:preprocessor`mezery při použití nebo s . Tuto změnu lze `/d1experimental:preprocessor:oldWhitespace`zakázat pomocí aplikace .

Vzhledem k tomuto příkladu zdroje,

```cpp
#define m()
line m(
) line
```

Předchozí výstup `/E` byl:

```Output
line line
#line 2
```

Nový výstup `/E` je nyní:

```Output
line
 line
```

### <a name="import-and-module-keywords-are-context-dependent"></a>Klíčová slova "import" a "modul" jsou závislá na kontextu

Podle P1857R1, import a modul preprocesordirekty mají další omezení na jejich syntaxi. Tento příklad již nekompiluje:

```cpp
import // Invalid
m;
```

Vytvoří následující chybovou zprávu:

```Output
error C2146: syntax error: missing ';' before identifier 'm'
```

Chcete-li problém vyřešit, ponechte import na stejném řádku:

```cpp
import m; // OK
```

### <a name="removal-of-stdweak_equality-and-stdstrong_equality"></a>Odstranění std::weak_equality a std::strong_equality

Sloučení P1959R0 vyžaduje kompilátor odebrat chování a `std::weak_equality` `std::strong_equality` odkazy na a typy.

Kód v tomto příkladu již nezkompiluje:

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

Příklad nyní vede k těmto chybám:

```Output
error C2039: 'strong_equality': is not a member of 'std'
error C2143: syntax error: missing ';' before '<=>'
error C4430: missing type specifier - int assumed. Note: C++ does not support default-int
error C4430: missing type specifier - int assumed. Note: C++ does not support default-int
error C7546: binary operator '<=>': unsupported operand types 'nullptr' and 'nullptr'
error C7546: binary operator '<=>': unsupported operand types 'void (__cdecl *)(void)' and 'void (__cdecl *)(void)'
error C7546: binary operator '<=>': unsupported operand types 'int (__thiscall S::* )(const S &) const' and 'int (__thiscall S::* )(const S &) const'
```

Chcete-li tento problém vyřešit, aktualizujte, abyste dali přednost integrovaným relačním operátorům a nahraďte odebrané typy:

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

### <a name="tls-guard-changes"></a>Změny tls guard

Dříve nebyly proměnné místního vlákna v knihovnách DLL správně inicializovány před prvním použitím v podprocesech, které existovaly před načtením knihovny DLL, kromě vlákna, které načetlo knihovnu DLL. Tato vada byla nyní opravena.
Místní proměnné podprocesu v takové dll jsou inicializovány bezprostředně před jejich prvním použitím v těchto vláknech.

Toto nové chování testování inicializace při použití lokálních proměnných podprocesu může být zakázáno pomocí přepínače kompilátoru. `/Zc:tlsGuards-` Nebo přidáním `[[msvc:no_tls_guard]]` atributu do určité hovlákna místní proměnné.

### <a name="better-diagnosis-of-call-to-deleted-functions"></a>Lepší diagnostika volání na smazané funkce

Náš kompilátor byl více tolerantní o volání odstraněné funkce dříve. Například pokud volání došlo v kontextu těla šablony, bychom diagnostikovat volání. Navíc pokud existuje více instancí volání odstraněných funkcí, bychom vydat pouze jednu diagnostiku. Nyní vydáváme diagnostiku pro každou z nich.

Jeden důsledek nového chování může způsobit malé porušení změny: Kód, který volal odstraněné funkce by se dostat diagnostikována, pokud nikdy nebylo potřeba pro generování kódu. Teď to diagnostikujeme předem.

Tento příklad ukazuje kód, který nyní vytváří chybu:

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

Chcete-li problém vyřešit, odeberte volání odstraněných funkcí:

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

## <a name="bug-fixes-and-behavior-changes-in-visual-studio-2019"></a><a name="update_160"></a>Opravy chyb a změny chování ve Visual Studiu 2019

### <a name="reinterpret_cast-in-a-constexpr-function"></a>Reinterpret_cast ve funkci constexpr

Reinterpret_cast **reinterpret_cast** je ve funkci **constexpr** nezákonná. Kompilátor Microsoft C++ by dříve odmítnout **reinterpret_cast** pouze v případě, že byly použity v kontextu **constexpr.** V sadě Visual Studio 2019 ve všech režimech jazykových standardů kompilátor správně diagnostikuje **reinterpret_cast** v definici funkce **constexpr.** Následující kód nyní vytváří *C3615: constexpr funkce 'f' nemůže mít za následek konstantní výraz*.

```cpp
long long i = 0;
constexpr void f() {
    int* a = reinterpret_cast<int*>(i);
}
```

Chcete-li se vyhnout chybě, odeberte modifikátor **constexpr** z deklarace funkce.

### <a name="correct-diagnostics-for-basic_string-range-constructor"></a>Správná diagnostika pro konstruktor basic_string rozsahu

V sadě Visual Studio 2019 konstruktor `basic_string` rozsahu již potlačuje diagnostiku kompilátoru s `static_cast`. Následující kód zkompiluje bez upozornění v sadě Visual Studio `wchar_t` 2017, `out`i přes možnou ztrátu dat z **char** při inicializaci :

```cpp
std::wstring ws = /* … */;
std::string out(ws.begin(), ws.end());
```

Visual Studio 2019 správně vyvolává *C4244: 'argument': převod z 'wchar_t' na 'const _Elem', možné ztráty dat*. Chcete-li se vyhnout upozornění, můžete inicializovat std::string, jak je znázorněno v tomto příkladu:

```cpp
std::wstring ws = L"Hello world";
std::string out;
for (wchar_t ch : ws)
{
    out.push_back(static_cast<char>(ch));
}
```

### <a name="incorrect-calls-to--and---under-clr-or-zw-are-now-correctly-detected"></a>Nesprávné volání += a -= pod /clr nebo /ZW jsou nyní správně rozpoznány

V sadě Visual Studio 2017 byla zavedena chyba, která způsobila, že kompilátor tiše ignoroval `/clr` chyby a negeneroval žádný kód pro neplatná volání na += a -= pod nebo `/ZW`. Následující kód zkompiluje bez chyb v Sadě Visual Studio 2017, ale v Sadě Visual Studio 2019 správně vyvolá *chybu C2845: 'System::String ^': ukazatel aritmetika není povoleno u tohoto typu*:

```cpp
public enum class E { e };

void f(System::String ^s)
{
    s += E::e; // C2845 in VS2019
}
```

Chcete-li se vyhnout chybě v tomto příkladu, použijte `s += E::e.ToString();`operátor s ToString() metoda: .

### <a name="initializers-for-inline-static-data-members"></a>Inicializátory pro včleněné statické datové členy

Neplatné členské přístupy v rámci **inline** a **statické constexpr** inicializátory jsou nyní správně zjištěny. Následující příklad zkompiluje bez chyby v Sadě Visual Studio 2017, ale v Visual Studio 2019 v režimu `/std:c++17` vyvolá chybu *C2248: nelze získat přístup k soukromému člendeklarované ve třídě "X"*.

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

Chcete-li se vyhnout `X::c` chybě, deklarujte člen jako chráněný:

```cpp
struct X
{
    protected:
        static inline const int c = 1000;
};
```

### <a name="c4800-reinstated"></a>C4800 obnoven

MSVC míval upozornění na výkon C4800 o implicitní převod na **bool**. Bylo to příliš hlučné a nelze je potlačit, což nás vedlo k jeho odebrání v sadě Visual Studio 2017. Během životního cyklu Visual Studia 2017 jsme však získali spoustu zpětné vazby o užitečných případech, které řešil. Přinášíme zpět v Visual Studio 2019 pečlivě na míru C4800, spolu s vysvětlující C4165. Obě tato upozornění lze snadno potlačit pomocí explicitního přetypování nebo porovnání s 0 příslušného typu. C4800 je upozornění úrovně 4 mimo výchozí úroveň a C4165 je upozornění úrovně 3 mimo výchozí úroveň 3. Oba jsou zjistitelné `/Wall` pomocí možnosti kompilátoru.

Následující příklad vyvolá C4800 a C4165 pod `/Wall`:

```cpp
bool test(IUnknown* p)
{
    bool valid = p; // warning C4800: Implicit conversion from 'IUnknown*' to bool. Possible information loss
    IDispatch* d = nullptr;
    HRESULT hr = p->QueryInterface(__uuidof(IDispatch), reinterpret_cast<void**>(&d));
    return hr; // warning C4165: 'HRESULT' is being converted to 'bool'; are you sure this is what you want?
}
```

Chcete-li se vyhnout upozornění v předchozím příkladu, můžete napsat kód takto:

```cpp
bool test(IUnknown* p)
{
    bool valid = p != nullptr; // OK
    IDispatch* d = nullptr;
    HRESULT hr = p->QueryInterface(__uuidof(IDispatch), reinterpret_cast<void**>(&d));
    return SUCCEEDED(hr);  // OK
}
```

### <a name="local-class-member-function-doesnt-have-a-body"></a>Funkce člena místní třídy nemá tělo

V sadě Visual Studio 2017 *C4822: Místní členská funkce třídy* nemá `/w14822` tělo je aktivována pouze v případě, že je explicitně nastavena možnost kompilátoru; není zobrazena s `/Wall`. V sadě Visual Studio 2019 C4822 je upozornění mimo výchozí nastavení, což je zjistitelné pod `/Wall` bez nutnosti explicitně nastavit. `/w14822`

```cpp
void example()
{
    struct A
        {
            int boo(); // warning C4822
        };
}
```

### <a name="function-template-bodies-containing-constexpr-if-statements"></a>Těla šablony funkce obsahující constexpr if příkazy

Těla funkcí šablony obsahující **příkazy constexpr** mají povoleny některé kontroly související s analýzou [/permising.](../build/reference/permissive-standards-conformance.md) Například v sadě Visual Studio 2017 následující kód vytvoří *C7510: "Typ": použití závislého názvu typu musí být předponou s 'typename'* pouze v **případě, že /tolerantní-** možnost není nastavena. V Visual Studiu 2019 stejný kód vyvolá chyby i v případě, že je nastavena možnost **/tolerantní:**

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

Chcete-li se této chybě vyhnout, přidejte `typename T::Type a;`klíčové slovo**typename** do deklarace : `a`.

### <a name="inline-assembly-code-isnt-supported-in-a-lambda-expression"></a>Kód inline sestavení není ve výrazu lambda podporován.

Tým Microsoft C++ byl nedávno informován o problému se zabezpečením, ve kterém použití inline assembleru `ebp` v rámci lambda může vést k poškození (registr zpáteční adresy) za běhu. Útočník se zlými úmysly by mohl tento scénář využít. Vzhledem k povaze problému, skutečnost, že inline assembler je podporován pouze na x86 a špatné interakce mezi inline assembler a zbytek kompilátoru, nejbezpečnější řešení tohoto problému bylo zakázat inline assembler v rámci lambda výraz.

Jediné použití inline assembleru v lambda výrazu, který jsme našli "ve volné přírodě", bylo zachytit zpáteční adresu. V tomto scénáři můžete zachytit zpáteční adresu na všech platformách jednoduše `_ReturnAddress()`pomocí vnitřní kompilátoru .

Následující kód vytváří *C7552: vložená assembler není podporována v lambda* v obou Visual Studio 2017 15.9 a Visual Studio 2019:

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

Chcete-li se vyhnout chybě, přesuňte kód sestavení do pojmenované funkce, jak je znázorněno v následujícím příkladu:

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

Funkce ladění iterátoru byla vyučována `std::move_iterator`správně rozbalit . Například `std::copy(std::move_iterator<std::vector<int>::iterator>, std::move_iterator<std::vector<int>::iterator>, int*)` nyní může `memcpy` zapojit rychlou cestu.

### <a name="fixes-for-xkeycheckh-keyword-enforcement"></a>Opravy \<pro vynucení klíčových slov xkeycheck.h>

Makro standardní knihovny nahrazující vynucení klíčových slov \<xkeycheck.h> bylo opraveno tak, aby vyzařovaly zjištěné klíčové slovo skutečného problému, nikoli obecnou zprávu. Podporuje také klíčová slova Jazyka C++20 a vyhýbá se podvádění technologie IntelliSense, aby řekla, že náhodná klíčová slova jsou makra.

### <a name="allocator-types-no-longer-deprecated"></a>Typy přidělování již nejsou zastaralé.

`std::allocator<void>`, `std::allocator::size_type`a `std::allocator::difference_type` již nejsou zastaralé.

### <a name="correct-warning-for-narrowing-string-conversions"></a>Správné upozornění na zužující se převody řetězců

Z programu byla `static_cast` odstraněna falešná, která nebyla požadována standardem, který `std::string`náhodně potlačil varování před zúžením C4244 . Pokus o `std::string::string(const wchar_t*, const wchar_t*)` volání bude nyní správně vyzařovat *C4244 "zúžení wchar_t do char."*

### <a name="various-filesystem-correctness-fixes"></a>Různé \<opravy správnosti> souborového systému

- Opraveno `std::filesystem::last_write_time` selhání při pokusu o změnu času posledního zápisu adresáře.
- Konstruktor `std::filesystem::directory_entry` nyní ukládá neúspěšný výsledek, spíše než vyvolání výjimky, pokud je zadána neexistující cílová cesta.
- `std::filesystem::create_directory` Dvouparametrová verze byla změněna tak, aby volala `CreateDirectoryExW` verzi `copy_symlink` 1 `existing_p` parametrů, protože základní funkce by se použila, když byl symlink.
- `std::filesystem::directory_iterator`již selže, pokud je nalezen a zlomený symlink.
- `std::filesystem::space`nyní přijímá relativní cesty.
- `std::filesystem::path::lexically_relative`již není zaměňována koncovými lomítky, hlášená jako [LWG 3096](https://cplusplus.github.io/LWG/issue3096).
- Zpracováno `CreateSymbolicLinkW` kolem odmítnutí cesty s `std::filesystem::create_symlink`lomítka mizející v .
- Pracoval kolem funkce režimu `delete` mazání POSIX existující v systému Windows 10 LTSB 1609, ale ve skutečnosti není schopen odstranit soubory.
- `std::boyer_moore_searcher`a `std::boyer_moore_horspool_searcher`'s kopie konstruktory a kopírovat operátory přiřazení nyní skutečně kopírovat věci.

### <a name="parallel-algorithms-on-windows-8-and-later"></a>Paralelní algoritmy ve Windows 8 a novějších

Knihovna paralelních algoritmů nyní `WaitOnAddress` správně používá skutečnou rodinu v systému Windows 8 a novějších, spíše než vždy používat windows 7 a starší falešné verze.

### <a name="stdsystem_categorymessage-whitespace"></a>`std::system_category::message()`Mezery

`std::system_category::message()`Nyní ořízne koncové mezery z vrácené zprávy.

### <a name="stdlinear_congruential_engine-divide-by-zero"></a>`std::linear_congruential_engine`vydělit nulou

Některé podmínky, `std::linear_congruential_engine` které by způsobily spuštění dělení 0 byly opraveny.

### <a name="fixes-for-iterator-unwrapping"></a>Opravy pro rozbalení iterátoru

Zařízení pro rozbalení iterátoru, které bylo poprvé vystaveno pro integraci programátorů a uživatelů v sadě Visual Studio 2017 15.8, jak je popsáno v článku C++ Team Blog [STL Funkce a opravy ve VS 2017 15.8](https://devblogs.microsoft.com/cppblog/stl-features-and-fixes-in-vs-2017-15-8/), již nerozbaluje iterátory odvozené od standardních knihovnických iterátorů. Například uživatel, který je `std::vector<int>::iterator` odvozen z a pokusí se přizpůsobit chování nyní získá jejich vlastní chování při volání standardní knihovny algoritmy, nikoli chování ukazatele.

Neuspořádaná `reserve` funkce kontejneru nyní skutečně rezervuje n elementy, jak je popsáno v [LWG 2156](https://cplusplus.github.io/LWG/issue2156).

### <a name="time-handling"></a>Manipulace s časem

- Dříve by některé časové hodnoty, které byly předány knihovně `condition_variable::wait_for(seconds::max())`souběžnosti, přetekly, například . Nyní opraveno, přetečení změnilo chování ve zdánlivě náhodném 29denním cyklu (když uint32_t milisekundy přijaté základními win32 api přetečením).

- \<Hlavička ctime> nyní `timespec` `timespec_get` správně deklaruje a v oboru `std` názvů kromě deklarování v globálním oboru názvů.

### <a name="various-fixes-for-containers"></a>Různé opravy pro kontejnery

- Mnoho standardních funkcí interního kontejneru knihovny bylo soukromé pro lepší prostředí Technologie IntelliSense. Další opravy označit členy jako soukromé se očekává v novějších verzích MSVC.

- Byly opraveny problémy s správností `list`bezpečnosti `map`výjimek, kdy byly opraveny kontejnery založené na uzlu jako , , a `unordered_map` budou poškozeny. Během `propagate_on_container_copy_assignment` operace `propagate_on_container_move_assignment` nebo přeřazení bychom uvolnit sentinel uzlu kontejneru se starým přidělování, provést přiřazení POCCA/POCMA přes staré přidělování a pak se pokusit získat uzel sentinel z nového alokátoru. Pokud se toto přidělení nezdařilo, kontejner byl poškozen a nemohl být ani zničen, protože vlastnictví sentinelového uzlu je tvrdá datová struktura invariantní. Tento kód byl opraven pro přidělení nového uzlu sentinelu z přidělování zdrojového kontejneru před zničením existujícího uzlu sentinelu.

- Kontejnery byly upevněny `propagate_on_container_copy_assignment`tak, aby vždy kopírovaly/stěhovaly/vyměňovaly alokátory podle , `propagate_on_container_move_assignment`a , a `propagate_on_container_swap`to i pro deklarované `is_always_equal`alokátory .

- Přidáno přetížení pro sloučení kontejnerů a extrahovat členské funkce, které přijímají kontejnery rvalue na [P0083 "Splicing mapy a sady"](https://wg21.link/p0083r3)

### <a name="stdbasic_istreamread-processing-of-rn--n"></a>`std::basic_istream::read`zpracování \\r\\n \\=> n

`std::basic_istream::read`bylo upevněno tak, aby dočasně nezapisovalo do částí dodané vyrovnávací paměti jako součást \\r\\n => \\n zpracování. Tato změna poskytuje některé výhody výkonu, která byla získána v sadě Visual Studio 2017 15.8 pro čtení větší než 4kB velikost. Zlepšení efektivity z vyhnout se tři virtuální volání na znak jsou však stále k dispozici.

### <a name="stdbitset-constructor"></a>`std::bitset`Konstruktor

Konstruktor `std::bitset` již nečte jedničky a nuly v opačném pořadí pro velké bitové sady.

### <a name="stdpairoperator-regression"></a>`std::pair::operator=`Regrese

Opravena regrese `std::pair`v operátoru přiřazení společnosti 's zavedená při implementaci [LWG 2729 "Missing SFINAE on std::pair::operator=";](https://cplusplus.github.io/LWG/issue2729). Nyní správně přijímá typy `std::pair` konvertibilní znovu.

### <a name="non-deduced-contexts-for-add_const_t"></a>Neodvozené kontexty pro`add_const_t`

Opravena chyba vlastností menšího typu, kde `add_const_t` a související funkce mají být kontextem bez odvození. Jinými slovy, `add_const_t` by měl `typename add_const<T>::type`být `const T`alias pro , ne .

## <a name="bug-fixes-and-behavior-changes-in-162"></a><a name="update_162"></a>Opravy chyb a změny chování v 16.2

### <a name="const-comparators-for-associative-containers"></a>Const komparátory pro asociativní kontejnery

Kód pro vyhledávání a vkládání v [sadě](../standard-library/set-class.md), [mapa](../standard-library/map-class.md), [multiset](../standard-library/multiset-class.md)a [multimap](../standard-library/multimap-class.md) byl sloučen pro zmenšenou velikost kódu. Operace vložení nyní volat méně než porovnání na **const** porovnání functor, stejným způsobem, že operace hledání již dříve. Následující kód zkompiluje ve Visual Studiu 2019 verze 16.1 a starší, ale vyvolá C3848 v Visual Studiu 2019 verze 16.2:

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

Chcete-li se vyhnout chybě, proveďte operátor porovnání **const**:

```cpp
struct Comparer  {
   bool operator() (K a, K b) const {
      return a.a < b.a;
   }
};

```

::: moniker-end

::: moniker range="vs-2017"

## <a name="conformance-improvements-in-visual-studio-2017-rtw-version-150"></a><a name="improvements_150"></a>Vylepšení shody ve Visual Studiu 2017 RTW (verze 15.0)

S podporou generalizované **constexpr** a nestatické data členské inicializace (NSDMI) pro agregace, Kompilátor Microsoft C++ v Sadě Visual Studio 2017 je nyní kompletní pro funkce přidané ve standardu C ++ 14. Kompilátor však stále postrádá několik funkcí z c++ 11 a C ++ 98 standardy. Tabulka [shody jazyka Microsoft C++](../visual-cpp-language-conformance.md) naleznete v tabulce, která zobrazuje aktuální stav kompilátoru.

### <a name="c11-expression-sfinae-support-in-more-libraries"></a>C++11: Podpora výrazu SFINAE ve více knihovnách

Kompilátor pokračuje ve zlepšování své podpory výrazu SFINAE, který je vyžadován pro odpočet a nahrazení argumentů šablony, kde se výrazy **decltype** a **constexpr** mohou zobrazit jako parametry šablony. Další informace naleznete [v tématu Výraz SFINAE vylepšení visual studio 2017 RC](https://blogs.msdn.microsoft.com/vcblog/2016/06/07/expression-sfinae-improvements-in-vs-2015-update-3).

### <a name="c14-nsdmi-for-aggregates"></a>C++14: NSDMI pro agregáty

Agregace je pole nebo třída bez konstruktoru za předpokladu uživatele, žádné soukromé nebo chráněné nestatické datové členy, žádné základní třídy a žádné virtuální funkce. Začátek v C++ 14 agregace může obsahovat iniciály členů. Další informace naleznete [v tématu Členské inicializační a agregace](https://wg21.link/n3605).

### <a name="c14-extended-constexpr"></a>C++14: Rozšířený **constexpr**

Výrazy deklarované jako **constexpr** nyní mohou obsahovat určité druhy deklarací, if a switch statements, loop statements a mutace objektů, jejichž životnost začala v rámci vyhodnocení exprese constexpr. Také již není požadavek, že **constexpr** nestatické členské funkce musí být implicitně **const**. Další informace naleznete [v tématu Relaxace omezení na constexpr funkce](https://wg21.link/n3652).

### <a name="c17-terse-static_assert"></a>C++17: Stručné`static_assert`

parametr zprávy `static_assert` pro je volitelný. Další informace naleznete v [tématu Rozšíření static_assert v2](https://wg21.link/n3928).

### <a name="c17-fallthrough-attribute"></a>C++17: `[[fallthrough]]` atribut

V režimu **/std:c++17** lze `[[fallthrough]]` atribut použít v kontextu příkazů switch jako nápovědu kompilátoru, který je určen pro fall-through behavior. Tento atribut zabrání kompilátoru ve vydávání upozornění v takových případech. Další informace naleznete v [tématu Formulaing \[ \[for fallthrough\] \] attribute](https://wg21.link/p0188r0).

### <a name="generalized-range-based-for-loops"></a>Generalizované rozsah-založené pro smyčky

Range-based for smyčky již `begin()` nevyžadují, a `end()` vrátit objekty stejného typu. Tato změna `end()` umožňuje vrátit sentinel, jak je používán rozsahy v [rozsahu v3](https://github.com/ericniebler/range-v3) a dokončené- ale ne zcela publikované rozsahy technické specifikace. Další informace naleznete [v tématu Generalizing the Range-Based For Loop](https://wg21.link/p0184r0).

## <a name="conformance-improvements-in-153"></a><a name="improvements_153"></a>Zlepšení shody v 15.3

### <a name="constexpr-lambdas"></a>constexpr lambdas

Lambda výrazy mohou být nyní použity v konstantní výrazy. Další informace naleznete [v tématu constexpr lambda výrazy v jazyce C++](../cpp/lambda-expressions-constexpr.md).

### <a name="if-constexpr-in-function-templates"></a>**pokud constexpr** v šablonách funkcí

Šablona funkce může obsahovat **příkazy constexpr,** které umožňují větvení v době kompilace. Další informace naleznete v [příkazech constexpr](../cpp/if-else-statement-cpp.md#if_constexpr).

### <a name="selection-statements-with-initializers"></a>Příkazy výběru s inicializátory

If **if** prohlášení může obsahovat inicializátor, který zavádí proměnnou v oboru bloku v rámci samotného příkazu. Další informace naleznete v [případě, že příkazy s inicializátorem](../cpp/if-else-statement-cpp.md#if_with_init).

### <a name="maybe_unused-and-nodiscard-attributes"></a>`[[maybe_unused]]`a `[[nodiscard]]` atributy

Nový `[[maybe_unused]]` atribut umlčí upozornění, když se entita nepoužívá. Atribut `[[nodiscard]]` vytvoří upozornění, pokud je vrácená hodnota volání funkce zahozena. Další informace naleznete [v tématu Atributy v jazyce C++](../cpp/attributes.md).

### <a name="using-attribute-namespaces-without-repetition"></a>Použití oborů názvů atributů bez opakování

Nová syntaxe umožňující v seznamu atributů pouze jeden identifikátor oboru názvů. Další informace naleznete [v tématu Atributy v jazyce C++](../cpp/attributes.md).

### <a name="structured-bindings"></a>Strukturovaná vazby

Nyní je možné v jedné deklaraci uložit hodnotu s jednotlivými názvy pro jeho `std::tuple` `std::pair`součásti, pokud je hodnota matice, nebo nebo má všechny veřejné nestatické datové členy. Další informace naleznete [v tématu Strukturované vazby](https://wg21.link/p0144r0) a [vrácení více hodnot z funkce](../cpp/functions-cpp.md#multi_val).

### <a name="construction-rules-for-enum-class-values"></a>Pravidla výstavby pro hodnoty **tříd výčtu**

Nyní je implicitní/nezužující převod z základního typu výčtu s rozsahem na samotný výčet, když jeho definice nezavádí žádný čítač výčtu a zdroj používá syntaxi inicializace seznamu. Další informace naleznete [v tématu Pravidla výstavby pro hodnoty třídy výčtu](https://wg21.link/p0138r2) a [výčty](../cpp/enumerations-cpp.md#no_enumerators).

### <a name="capturing-this-by-value"></a>Zachycení `*this` podle hodnoty

Objekt `*this` ve výrazu lambda může být nyní zachycen hodnotou. Tato změna umožňuje scénáře, ve kterých lambda je vyvolána v paralelní a asynchronní operace, zejména na novější architektury počítače. Další informace naleznete v [tématu \*Lambda \[Capture\*\]of this by Value as =, this](https://wg21.link/p0018r3).

### <a name="removing-operator-for-bool"></a>Odstranění `operator++` pro **bool**

`operator++`již není podporována u typů **bool.** Další informace naleznete v [tématu Remove Deprecated operator++(bool)](https://wg21.link/p0002r1).

### <a name="removing-deprecated-register-keyword"></a>Odebrání zastaralého **klíčového** slova registru

Klíčové slovo **register,** dříve zastaralé (a ignorované kompilátorem), je nyní odebráno z jazyka. Další informace naleznete [v tématu Odebrání zastaralého použití klíčového slova registru](https://wg21.link/p0001r1).

## <a name="conformance-improvements-in-155"></a><a name="improvements_155"></a>Zlepšení shody v 15,5

Funkce označené \[14] jsou k dispozici bezpodmínečně i v režimu **/std:c++14.**

### <a name="new-compiler-switch-for-extern-constexpr"></a>Nový přepínač kompilátoru pro **externí constexpr**

V dřívějších verzích sady Visual Studio kompilátor vždy dal **constexpr** proměnné vnitřní propojení i v případě, že proměnná byla označena **extern**. V sadě Visual Studio 2017 verze 15.5 umožňuje nový přepínač kompilátoru [/Zc:externConstexpr](../build/reference/zc-externconstexpr.md)správné chování odpovídající standardům. Další informace naleznete [v tématu extern constexpr linkage](#extern_linkage).

### <a name="removing-dynamic-exception-specifications"></a>Odebrání specifikací dynamických výjimek

[P0003R5](https://wg21.link/p0003r5) Specifikace dynamických výjimek byly v jazyce C++11 zastaralé. funkce je odebrána z c++ 17, ale (stále) zastaralá specifikace je přísně zachována `throw()` jako alias pro `noexcept(true)`. Další informace naleznete v [tématu Dynamické odebrání specifikace výjimky a noexcept](#noexcept_removal).

### `not_fn()`

[P0005R4](https://wg21.link/p0005r4) `not_fn` je `not1` náhrada `not2`a .

### <a name="rewording-enable_shared_from_this"></a>Přeformulování`enable_shared_from_this`

[P0033R1](https://wg21.link/p0033r1) `enable_shared_from_this` byl přidán do C ++11. Standard C++ 17 aktualizuje specifikaci tak, aby lépe zpracovávala určité rohové případy. [14]

### <a name="splicing-maps-and-sets"></a>Spoje map a sad

[P0083R3](https://wg21.link/p0083r3) Tato funkce umožňuje extrakci uzlů z asociativních `set` `unordered_map`kontejnerů (tj. `unordered_set` `map`, , ), které pak lze upravit a vložit zpět do stejného kontejneru nebo jiného kontejneru, který používá stejný typ uzlu. (Běžným případem použití je extrahovat uzel z `std::map`, změnit klíč a znovu vložit.)

### <a name="deprecating-vestigial-library-parts"></a>Zastaralé pozůstatek knihovních dílů

[P0174R2](https://wg21.link/p0174r2) Několik funkcí standardní knihovny Jazyka C++ bylo v průběhu let nahrazeno novějšími funkcemi, jinak nebylo shledáno užitečným nebo problematickým. Tyto funkce jsou v jazyce C++17 oficiálně zastaralé.

### <a name="removing-allocator-support-in-stdfunction"></a>Odebrání podpory přidělování v`std::function`

[P0302R1](https://wg21.link/p0302r1) Před C++ 17 měla `std::function` šablona třídy několik konstruktorů, které přijaly argument přidělování. Použití alokátorů v této souvislosti však bylo problematické a sémantiku bylo nejasné. Problémové kontraktory byly odstraněny.

### <a name="fixes-for-not_fn"></a>Opravy pro`not_fn()`

[P0358R1](https://wg21.link/p0358r1) Nové znění `std::not_fn` pro poskytuje podporu šíření kategorie hodnot při použití v vyvolání obálky.

### <a name="shared_ptrt-shared_ptrtn"></a>`shared_ptr<T[]>`, `shared_ptr<T[N]>`

[P0414R2](https://wg21.link/p0414r2) Sloučení `shared_ptr` změn ze základních knihoven na C++17. [14]

### <a name="fixing-shared_ptr-for-arrays"></a>Upevnění `shared_ptr` polí

[P0497R0](https://wg21.link/p0497r0) Opravy shared_ptr podporu polí. [14]

### <a name="clarifying-insert_return_type"></a>Vyjasnění`insert_return_type`

[P0508R0](https://wg21.link/p0508r0) Asociativní kontejnery s jedinečnými klíči a neuspořádané `insert` kontejnery s jedinečnými klíči mají členovou funkci, která vrací vnořený typ `insert_return_type`. Tento návratový typ je nyní definován jako specializace typu, který je parametrizován na Iterátor a NodeType kontejneru.

### <a name="inline-variables-for-the-standard-library"></a>Vložky pro standardní knihovnu

[P0607R0](https://wg21.link/p0607r0)

### <a name="annex-d-features-deprecated"></a>Příloha D obsahuje zastaralé

Příloha D normy C++ obsahuje všechny prvky, které `shared_ptr::unique()` `<codecvt>`byly `namespace std::tr1`zastaralé, včetně , a . Je-li nastaven přepínač kompilátoru **/std:c++17,** jsou téměř všechny standardní funkce knihovny v příloze D označeny jako zastaralé. Další informace naleznete v tématu [Standardní prvky knihovny v příloze D jsou označeny jako zastaralé](#annex_d).

Obor `std::tr2::sys` názvů `<experimental/filesystem>` v nyní vydává upozornění na vyřazení pod **/std:c++14** ve výchozím nastavení a je nyní odebrán pod **/std:c++17** ve výchozím nastavení.

Vylepšená shoda `<iostream>` v tom, že se vyhnete nestandardnímu rozšíření (explicitní specializace ve své třídě).

Standardní knihovna nyní interně používá šablony proměnných.

Standardní knihovna byla aktualizována v reakci na změny kompilátoru Jazyka C++17, včetně přidání **noexcept** v systému typů a odebrání specifikací dynamické výjimky.

## <a name="conformance-improvements-in-156"></a><a name="improvements_156"></a>Vylepšení shody v 15,6

### <a name="c17-library-fundamentals-v1"></a>Základy knihovny C++17 V1

[P0220R1](https://wg21.link/p0220r1) do standardu začleňuje technické specifikace Základy knihovny pro C++17. Zahrnuje aktualizace \<experimentálních/memory_resource \<>, \<experimentálních/volitelných>, experimentálních/funkčních>, \<experimentálních/jakýchkoli>, \<experimentálních/string_view>, \<experimentálních/paměťových>, \<experimentálních/memory_resource> a \<experimentálních/algoritmových>.

### <a name="c17-improving-class-template-argument-deduction-for-the-standard-library"></a>C++17: Vylepšení odpočtu argumentů šablony třídy pro standardní knihovnu

[P0739R0](https://wg21.link/p0739r0) Přechod `adopt_lock_t` na přední stranu `scoped_lock` seznamu parametrů `scoped_lock`pro povolení konzistentního použití . Povolit `std::variant` konstruktoru účastnit se řešení přetížení ve více případech, povolit přiřazení kopírování.

## <a name="conformance-improvements-in-157"></a><a name="improvements_157"></a>Vylepšení shody v 15.7

### <a name="c17-rewording-inheriting-constructors"></a>C++17: Přeformulování dědění konstruktorů

[P0136R1](https://wg21.link/p0136r1) určuje, že **pomocí** deklarace, která názvy konstruktornyní umožňuje odpovídající konstruktory základní třídy viditelné pro inicializace odvozené třídy, spíše než deklarovat další konstruktory odvozené třídy. Toto přeformulování je změna z C ++ 14. V sadě Visual Studio 2017 verze 15.7 a novější v **režimu /std:c++17** kód platný v jazyce C++14 a používá dědící konstruktory nemusí být platný nebo může mít různé sémantiky.

Následující příklad ukazuje chování c++ 14:

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

Následující příklad ukazuje **chování /std:c++17** v sadě Visual Studio 15.7:

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

Další informace naleznete v tématu [Konstruktory](../cpp/constructors-cpp.md#inheriting_constructors).

### <a name="c17-extended-aggregate-initialization"></a>C++17: Rozšířená agregace inicializace

[P0017R1](https://wg21.link/p0017r1)

Pokud je konstruktor základní třídy neveřejný, ale přístupný odvozené třídě, pak v režimu **/std:c++17** v sadě Visual Studio 2017 verze 15.7 již nelze použít prázdné závorky k inicializaci objektu odvozeného typu.
Následující příklad ukazuje chování konformní ho shody jazyka C++14:

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

V jazyce C++17 `Derived` je nyní považován za agregační typ. To znamená, že `Base` inicializace prostřednictvím soukromého výchozího konstruktoru probíhá přímo jako součást rozšířeného pravidla agregace inicializace. Dříve `Base` byl soukromý konstruktor volán prostřednictvím konstruktoru `Derived` a byl úspěšný z důvodu deklarace friend.
Následující příklad ukazuje chování c++ 17 v sadě Visual Studio verze 15.7 v režimu **/std:c++17:**

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

### <a name="c17-declaring-non-type-template-parameters-with-auto"></a>C++17: Deklarování parametrů netypové šablony s automatickým

[P0127R2](https://wg21.link/p0127r2)

V režimu **/std:c++17** může kompilátor nyní odvodit typ argumentu šablony bez typu, který je deklarován pomocí **automatického**:

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

Jedním z dopadů této nové funkce je, že platný kód C ++ 14 nemusí být platný nebo může mít jinou sémantiku. Například některé přetížení, které byly dříve neplatné jsou nyní platné. Následující příklad ukazuje kód C++ 14, který `example(p)` se `example(void*);`zkompiluje, protože volání je vázáno na . V sadě Visual Studio 2017 verze 15.7 v režimu **/std:c++17** je šablona `example` funkce nejlepší.

```cpp
template <int N> struct A;
template <typename T, T N> int example(A<N>*) = delete;

void example(void *);

void sample(A<0> *p)
{
    example(p); // OK in C++14
}
```

Následující příklad ukazuje kód Jazyka C++17 v sadě Visual Studio 15.7 v režimu **/std:c++17:**

```cpp
template <int N> struct A;
template <typename T, T N> int example(A<N>*);

void example(void *);

void sample(A<0> *p)
{
    example(p); // C2280: 'int example<int,0>(A<0>*)': attempting to reference a deleted function
}
```

### <a name="c17-elementary-string-conversions-partial"></a>C++17: Převody elementárních řetězců (částečné)

[P0067R5](https://wg21.link/p0067r5) Nízkoúrovňové funkce nezávislé na národním prostředí pro převody mezi řetězci a řetězci a mezi čísly s plovoucí desetinnou desetinnou a stringy.

### <a name="c20-avoiding-unnecessary-decay-partial"></a>C++20: Zamezení zbytečnému rozpadu (částečnému)

[P0777R1](https://wg21.link/p0777r1) Přidává diferenciaci mezi pojmem "rozpad" a konceptem jednoduše odstranění mašit nebo referenčních kvalifikátorů.  V některých `remove_reference_t` `decay_t` kontextech se nahradí nový znak typu. Podpora `remove_cvref_t` pro je implementována v sadě Visual Studio 2019.

### <a name="c17-parallel-algorithms"></a>C++17: Paralelní algoritmy

[P0024R2](https://wg21.link/p0024r2) Paralelismus TS je začleněn do standardu, s drobnými úpravami.

### <a name="c17-hypotx-y-z"></a>C++17:`hypot(x, y, z)`

[P0030R1](https://wg21.link/p0030r1) Přidá tři nové `std::hypot`přetížení , pro typy **float**, **double**a **long double**, z nichž každý má tři vstupní parametry.

### <a name="c17-filesystem"></a>C++17: \<> souborového systému

[P0218R1](https://wg21.link/p0218r1) Přijímá souborový systém TS do standardu s několika formulacemi.

### <a name="c17-mathematical-special-functions"></a>C++17: Matematické speciální funkce

[P0226R1](https://wg21.link/p0220r1) Do standardní \<hlavičky cmath> přijímá předchozí technické specifikace pro matematické speciální funkce.

### <a name="c17-deduction-guides-for-the-standard-library"></a>C++17: Odpočet průvodců pro standardní knihovnu

[P0433R2](https://wg21.link/p0433r2) Aktualizace STL využít C ++ 17 přijetí [P0091R3](https://wg21.link/p0091r3), který přidává podporu pro odpočet argument šablony třídy.

### <a name="c17-repairing-elementary-string-conversions"></a>C++17: Oprava převodů elementárních řetězců

[P0682R1](https://wg21.link/p0682r1) Přesuňte nové elementární funkce převodu řetězce z P0067R5 do nové hlavičky \<charconv `std::errc`> `std::error_code`a provést další vylepšení, včetně změny zpracování chyb použít místo .

### <a name="c17-constexpr-for-char_traits-partial"></a>C ++ 17: **constexpr** pro `char_traits` (částečné)

[P0426R1](https://wg21.link/p0426r1) Změny `std::traits_type` členských `length`funkcí `compare`, `find` a `std::string_view` aby bylo použitelné v konstantních výrazech. (Ve Visual Studiu 2017 verze 15.6, podporované pouze pro Clang/LLVM. Ve verzi 15.7 Preview 2 je podpora téměř kompletní i pro ClXX.)

## <a name="conformance-improvements-in-159"></a><a name="improvements_159"></a>Vylepšení shody v 15.9

### <a name="left-to-right-evaluation-order-for-operators-----and-"></a>Pořadí hodnocení zleva doprava pro `->*` `[]`hospodářské `>>`subjekty , , a`<<`

Počínaje jazykem C++17 musí být `->*`operandy operátorů , `[]`, `>>`a `<<` vyhodnocovány v pořadí zleva doprava. Existují dva případy, ve kterých kompilátor není schopen zaručit toto pořadí:

- pokud je jeden z operandských výrazů objektem předaným hodnotou nebo obsahuje objekt předaný hodnotou, nebo

- při kompilaci pomocí **/clr**a jeden z operandů je pole objektu nebo prvku pole.

Kompilátor vydává upozornění [C4866,](https://docs.microsoft.com/cpp/error-messages/compiler-warnings/c4866?view=vs-2017) když nemůže zaručit hodnocení zleva doprava. Kompilátor generuje toto upozornění pouze v **případě, že /std:c++17** nebo novější je zadán, jako požadavek pořadí zleva doprava těchto operátorů byla zavedena v Jazyce C ++ 17.

Chcete-li vyřešit toto upozornění, nejprve zvažte, zda je nutné provést hodnocení operandů zleva doprava, například když hodnocení operandů může způsobit vedlejší účinky závislé na pořadí. V mnoha případech pořadí, ve kterém jsou operandy hodnoceny nemá žádný pozorovatelný účinek. Pokud pořadí hodnocení musí být zleva doprava, zvažte, zda můžete předat operandy const odkaz místo. Tato změna eliminuje upozornění v následující ukázce kódu:

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

## <a name="bug-fixes-in-visual-studio-2017-rtw-version-150"></a><a name="update_150"></a>Opravy chyb ve Visual Studiu 2017 RTW (verze 15.0)

### <a name="copy-list-initialization"></a>Inicializace seznamu kopií

Visual Studio 2017 správně vyvolává chyby kompilátoru související s vytvářením objektů pomocí inicializačníseznamy, které nebyly zachyceny v sadě Visual Studio 2015 a může vést k selhání nebo nedefinované chování za běhu. Podle N4594 13.3.1.7p1 v copy-list-initialization je kompilátor povinen zvážit explicitní konstruktor pro řešení přetížení, ale musí vyvolat chybu, pokud je vybráno toto konkrétní přetížení.

Následující dva příklady zkompilovat v Sadě Visual Studio 2015, ale ne v Sadě Visual Studio 2017.

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

V sadě Visual Studio 2015 kompilátor chybně zachází s inicializace seznamu kopií stejným způsobem jako s pravidelnou inicializací kopírování; považuje pouze převod konstruktory pro rozlišení přetížení. V následujícím příkladu Visual Studio 2015 zvolí MyInt(23), ale Visual Studio 2017 správně vyvolá chybu.

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

Tento příklad je podobný předchozímu, ale vyvolá jinou chybu. Je úspěšná v Sadě Visual Studio 2015 a selže v Sadě Visual Studio 2017 s C2668.

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

### <a name="deprecated-typedefs"></a>Zastaralé typedefs

Visual Studio 2017 nyní vydává správné upozornění pro zastaralé typedefs, které jsou deklarovány ve třídě nebo struktuře. Následující příklad zkompiluje bez upozornění v sadě Visual Studio 2015, ale produkuje C4996 v sadě Visual Studio 2017.

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

Visual Studio 2017 správně vyvolá chybu, když levá operand operace podmíněného vyhodnocení není platný v kontextu constexpr. Následující kód zkompiluje v sadě Visual Studio 2015, ale ne v sadě Visual Studio 2017 (C3615 constexpr funkce 'f' nemůže mít za následek konstantní výraz):

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

Chcete-li chybu opravit, `array::size()` deklarujte funkci jako **constexpr** `f`nebo odeberte kvalifikátor **constexpr** z aplikace .

### <a name="class-types-passed-to-variadic-functions"></a>Typy tříd předaný variadické funkce

V sadě Visual Studio 2017 třídy nebo struktury, které jsou předány variadické funkce, jako je printf musí být triviálně kopírovatelné. Při předávání těchto objektů kompilátor jednoduše provede bitovou kopii a nezavolá konstruktor nebo destruktor.

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

Chcete-li chybu opravit, můžete volat členská funkci, která vrací triviálně kopírovatelný typ,

```cpp
    std::atomic<int> i(0);
    printf("%i\n", i.load());
```

nebo jinak použijte statický přetypovač k převodu objektu před jeho předáním:

```cpp
    struct S {/* as before */} s(0);
    printf("%i\n", static_cast<int>(s))
```

Pro řetězce vytvořené a spravované pomocí CString, za `operator LPCTSTR()` předpokladu, za předpokladu, že by měl být použit k obsazení CString objekt u ukazatelů C očekává formátovací řetězec.

```cpp
CString str1;
CString str2 = _T("hello!");
str1.Format(_T("%s"), static_cast<LPCTSTR>(str2));
```

### <a name="cv-qualifiers-in-class-construction"></a>Cv-kvalifikátory ve třídě konstrukce

V sadě Visual Studio 2015 kompilátor někdy nesprávně ignoruje cv kvalifikátor při generování objektu třídy prostřednictvím volání konstruktoru. Tento problém může potenciálně způsobit selhání nebo neočekávané chování za běhu. Následující příklad zkompiluje v Sadě Visual Studio 2015, ale vyvolá chybu kompilátoru v sadě Visual Studio 2017:

```cpp
struct S
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```

Chcete-li chybu `operator int()` opravit, deklarujte jako **const**.

### <a name="access-checking-on-qualified-names-in-templates"></a>Kontrola kvalifikovaných názvů v šablonách

Předchozí verze kompilátoru nekontrolovaly přístup ke kvalifikovaným názvům v některých kontextech šablony. Tento problém může narušit očekávané chování SFINAE, kde se očekává selhání nahrazení z důvodu nedostupnosti názvu. Mohlo by to způsobit selhání nebo neočekávané chování za běhu, protože kompilátor nesprávně volal nesprávné přetížení operátoru. V sadě Visual Studio 2017 je vyvolána chyba kompilátoru. Konkrétní chyba se může lišit, ale obvykle je to "C2672 žádné odpovídající přetížené funkce nalezena". Následující kód zkompiluje v Sadě Visual Studio 2015, ale vyvolá chybu v Sadě Visual Studio 2017:

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

V sadě Visual Studio 2015 a starší kompilátor nediagnostikoval chybějící seznamy argumentů šablony, když se šablona objevila v seznamu parametrů šablony, například jako součást výchozího argumentu šablony nebo netypového parametru šablony. Tento problém může mít za následek nepředvídatelné chování, včetně selhání kompilátoru nebo neočekávané chování za běhu. Následující kód zkompiluje v sadě Visual Studio 2015, ale vytvoří chybu v sadě Visual Studio 2017.

```cpp
template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;
```

### <a name="expression-sfinae"></a>Výraz-SFINAE

Pro podporu výrazu SFINAE kompilátor nyní analyzuje argumenty **decltype,** když jsou deklarovány šablony, nikoli instance. V důsledku toho pokud je v argumentu decltype nalezena nezávislá specializace, není odložena na dobu instance. Je zpracována okamžitě a všechny výsledné chyby jsou diagnostikovány v té době.

Následující příklad ukazuje takovou chybu kompilátoru, která je vyvolána v okamžiku deklarace:

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

Podle standardu C++ má třída deklarovaná uvnitř anonymního oboru názvů interní propojení, což znamená, že ji nelze exportovat. V sadě Visual Studio 2015 a starší toto pravidlo nebylo vynuceno. V sadě Visual Studio 2017 je pravidlo částečně vynuceno. Následující příklad vyvolá tuto chybu v sadě Visual Studio 2017: "chyba C2201: const anonymní obor názvů::S1::vftable: musí mít externí propojení, aby bylo možné exportovat nebo importovat."

```cpp
struct __declspec(dllexport) S1 { virtual void f() {} }; //C2201
```

### <a name="default-initializers-for-value-class-members-ccli"></a>Výchozí inicializátory pro členy třídy hodnoty (C++/CLI)

V sadě Visual Studio 2015 a starší kompilátor povolil (ale ignoroval) výchozí inicializátor člena pro člena třídy value. Výchozí inicializace třídy hodnoty vždy nula inicializuje členy. Výchozí konstruktor není povolen. V sadě Visual Studio 2017 výchozí člen inicializátory vyvolat chybu kompilátoru, jak je znázorněno v tomto příkladu:

```cpp
value struct V
{
    int i = 0; // error C3446: 'V::i': a default member initializer
               // isn't allowed for a member of a value class
};
```

### <a name="default-indexers-ccli"></a>Výchozí indexery (C++/CLI)

V sadě Visual Studio 2015 a starší kompilátor v některých případech nesprávně identifikoval výchozí vlastnost jako výchozí indexer. Bylo možné problém vyřešit pomocí **výchozího** identifikátoru pro přístup k vlastnosti. Samotné řešení se stalo problematickým po **zavedení výchozího** klíčového slova v jazyce C++11. V sadě Visual Studio 2017 byly opraveny chyby, které vyžadovaly řešení, a kompilátor nyní vyvolá chybu, když se **výchozí** hodnota používá pro přístup k výchozí vlastnosti třídy.

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

V Sadě Visual Studio 2017 můžete přistupovat k oběma vlastnostem Value podle jejich názvu:

```cpp
#using "class1.dll"

void f(ClassLibrary1::Class1 ^r1, ClassLibrary1::Class2 ^r2)
{
       r1->Value;
       r2->Value;
}
```

## <a name="bug-fixes-in-153"></a><a name="update_153"></a>Opravy chyb v 15.3

### <a name="calls-to-deleted-member-templates"></a>Volání odstraněných šablon členů

V předchozích verzích sady Visual Studio kompilátor v některých případech by se nepodařilo vyzařovat chybu pro špatně vytvořená volání odstraněné členské šablony, která by potenciálně způsobila selhání za běhu. Následující kód nyní vytváří C2280, "'int S\<int>::f\<int>(void)': pokus o odkaz na odstraněnou funkci":

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

Chcete-li chybu `i` opravit, deklarujte jako **int**.

### <a name="pre-condition-checks-for-type-traits"></a>Kontroly podmínek pro vlastnosti typu

Visual Studio 2017 verze 15.3 zlepšuje kontroly stavu vlastností typu přesněji dodržovat standard. Jeden takový šek je pro přiřaditelné. Následující kód vytváří C2139 ve Visual Studiu 2017 verze 15.3:

```cpp
struct S;
enum E;

static_assert(!__is_assignable(S, S), "fail"); // C2139 in 15.3
static_assert(__is_convertible_to(E, E), "fail"); // C2139 in 15.3
```

### <a name="new-compiler-warning-and-runtime-checks-on-native-to-managed-marshaling"></a>Nové kontroly upozornění kompilátoru a runtime kontroly nativní-ke spravovanému zařazování

Volání ze spravovaných funkcí do nativních funkcí vyžaduje zařazování. CLR provádí zařazování, ale nerozumí sémantiku Jazyka C++. Pokud předáte nativní objekt podle hodnoty, CLR buď volá konstruktor kopírování objektu nebo používá `BitBlt`, což může způsobit nedefinované chování za běhu.

Nyní kompilátor vydává upozornění, pokud může vědět v době kompilace, že nativní objekt s odstraněnou kopií ctor je předán mezi nativní a spravované hranice podle hodnoty. Pro ty případy, ve kterých kompilátor neví v době kompilace, vloží `std::terminate` runtime kontrolu tak, aby program volá okamžitě, když dojde k špatně vytvořené zařazování. Ve Visual Studio 2017 verze 15.3 následující kód vytváří upozornění C4606 "'A': předávání argument podle hodnoty přes nativní a spravované hranice vyžaduje platný konstruktor kopie. V opačném případě není definováno chování za běhu.

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

Chcete-li opravit chybu, odeberte direktivu `#pragma managed` označit volajícího jako nativní a vyhnout se zařazování.

### <a name="experimental-api-warning-for-winrt"></a>Experimentální API upozornění pro WinRT

WinRT API, které jsou uvolněny pro `Windows.Foundation.Metadata.ExperimentalAttribute`experimentování a zpětnou vazbu jsou zdobeny . Ve Visual Studio 2017 verze 15.3 kompilátor vytvoří upozornění C4698, když narazí na atribut. Několik api v předchozích verzích sady Windows SDK již byly označeny atributem a volání těchto api nyní aktivovat toto upozornění kompilátoru. Novější sady Windows SDK mají atribut odebrán ze všech dodaných typů, ale pokud používáte starší sadu SDK, budete muset potlačit tato upozornění pro všechna volání dodaných typů.

Následující kód vytváří upozornění C4698: "'Windows::Storage::IApplicationDataStatics2::GetForUserAsync' je pouze pro účely vyhodnocení a může být změnit nebo odebrání v budoucích aktualizacích":

```cpp
Windows::Storage::IApplicationDataStatics2::GetForUserAsync(); //C4698
```

Chcete-li upozornění zakázat, přidejte #pragma:

```cpp
#pragma warning(push)
#pragma warning(disable:4698)

Windows::Storage::IApplicationDataStatics2::GetForUserAsync();

#pragma warning(pop)
```

### <a name="out-of-line-definition-of-a-template-member-function"></a>Definice člena šablony mimo řádek

Visual Studio 2017 verze 15.3 vytvoří chybu, když narazí na definici mimo řádek členské funkce šablony, která nebyla deklarována ve třídě. Následující kód nyní vytváří chybu C2039: 'f': není členem 'S':

```cpp
struct S {};

template <typename T>
void S::f(T t) {} //C2039: 'f': is not a member of 'S'
```

Chcete-li chybu opravit, přidejte deklaraci do třídy:

```cpp
struct S {
    template <typename T>
    void f(T t);
};
template <typename T>
void S::f(T t) {}
```

### <a name="attempting-to-take-the-address-of-this-pointer"></a>Pokus o převzetí adresy **tohoto** ukazatele

V jazyce C++ se **jedná** o hodnotu hodnoty typu na X. Nelze vzít adresu **tohoto** nebo svázat s odkazem lvalue. V předchozích verzích sady Visual Studio by kompilátor umožňuje obejít toto omezení pomocí přetypování. Ve Visual Studiu 2017 verze 15.3 kompilátor vytvoří chybu C2664.

### <a name="conversion-to-an-inaccessible-base-class"></a>Převod na nepřístupnou základní třídu

Visual Studio 2017 verze 15.3 vytvoří chybu při pokusu o převod typu na základní třídu, která je nepřístupná. Kompilátor nyní vyvolává "error C2243: 'type cast': převod z 'D *' na 'B *' existuje, ale je nepřístupný". Následující kód je špatně vytvořena a může potenciálně způsobit selhání za běhu. Kompilátor nyní vytváří C2243, když narazí na kód, jako je tento:

```cpp
#include <memory>

class B { };
class D : B { }; // C2243. should be public B { };

void f()
{
   std::unique_ptr<B>(new D());
}
```

### <a name="default-arguments-arent-allowed-on-out-of-line-definitions-of-member-functions"></a>Výchozí argumenty nejsou povoleny mimo definice řádků členských funkcí

Výchozí argumenty nejsou povoleny pro mimořádek definice členských funkcí ve třídách šablon. Kompilátor vydá upozornění pod **/tolerantní**a tvrdou chybu pod [/tolerantní-](../build/reference/permissive-standards-conformance.md).

V předchozích verzích sady Visual Studio následující špatně vytvořený kód může potenciálně způsobit selhání za běhu. Visual Studio 2017 verze 15.3 vytváří upozornění C5034: 'A\<T>::f': out-of-line definice člena šablony třídy nemůže mít výchozí argumenty:

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

### <a name="use-of-offsetof-with-compound-member-designator"></a>Použití `offsetof` s označením složeného člena

V sadě Visual Studio 2017 verze `offsetof(T, m)` 15.3, pomocí kde *m* je "složené členské označení" výsledky upozornění při kompilaci s **/Wall** možnost. Následující kód je špatně vytvořen a může potenciálně způsobit selhání za běhu. Visual Studio 2017 verze 15.3 vytváří "varování C4841: nestandardní rozšíření používané: složené označení člena v offsetof":

```cpp
struct A {
   int arr[10];
};

// warning C4841: non-standard extension used: compound member designator in offsetof
constexpr auto off = offsetof(A, arr[2]);
```

Chcete-li kód opravit, zakažte upozornění pragmou nebo `offsetof`změňte kód tak, aby nepoužíval :

```cpp
#pragma warning(push)
#pragma warning(disable: 4841)
constexpr auto off = offsetof(A, arr[2]);
#pragma warning(pop)
```

### <a name="using-offsetof-with-static-data-member-or-member-function"></a>Použití `offsetof` se statickými datovými členy nebo člennou funkcí

Ve Visual Studiu 2017 verze 15.3, pomocí `offsetof(T, m)` kde *m* odkazuje na statický datový člen nebo členské funkce má za následek chybu. Následující kód vytváří "error C4597: undefined behavior: offsetof applied to member function 'example' a "error C4597: undefined behavior: offsetof applied to static data member 'sample":

```cpp
#include <cstddef>

struct A {
   int ten() { return 10; }
   static constexpr int two = 2;
};

constexpr auto off = offsetof(A, ten);
constexpr auto off2 = offsetof(A, two);
```

Tento kód je špatně vytvořen a může potenciálně způsobit selhání za běhu. Chcete-li chybu opravit, změňte kód tak, aby již vyvolával nedefinované chování. Je to nepřenosný kód, který je zakázán standardem C++.

### <a name="new-warning-on-__declspec-attributes"></a><a name="declspec"></a>Nové upozornění `__declspec` na atributy

Ve Visual Studio 2017 verze 15.3 kompilátor již `__declspec(...)` ignoruje `extern "C"` atributy, pokud je použita před navázání specifikace. Dříve by kompilátor ignoroval atribut, který by mohl mít důsledky běhu. Když jsou nastaveny možnosti **/Wall** a **/WX,** vytvoří následující kód "upozornění C4768: __declspec atributy před odkazem specifikace jsou ignorovány":

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

Chcete-li upozornění `extern "C"` opravit, nejprve vložte:

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

Toto upozornění je vypnuto ve výchozím nastavení v 15.3, ale ve výchozím nastavení v 15.5 a má vliv pouze na kód zkompilovaný s **/Wall** **/WX**.

### <a name="decltype-and-calls-to-deleted-destructors"></a>**decltype** a volání odstraněných destruktorů

V předchozích verzích sady Visual Studio kompilátor nezjistil, kdy došlo k volání odstraněného destruktoru v kontextu výrazu přidruženého k **decltype**. V sadě Visual Studio 2017 verze 15.3 vytvoří následující kód "chyba\<C2280: 'A T>::~A(void)": pokus o odkaz na odstraněnou funkci":

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

Visual Studio 2017 RTW verze měla regrese, ve kterém kompilátor Jazyka C++ by nevydal diagnostiku, pokud **const** proměnná nebyla inicializována. Tato regrese byla opravena ve Visual Studiu 2017 verze 15.3. Následující kód nyní vytváří "upozornění C4132: 'Hodnota': const objekt by měl být inicializován":

```cpp
const int Value; //C4132
```

Chcete-li chybu opravit, `Value`přiřaďte hodnotu společnosti .

### <a name="empty-declarations"></a>Prázdné deklarace

Visual Studio 2017 verze 15.3 teď varuje na prázdné deklarace pro všechny typy, nikoli pouze předdefinované typy. Následující kód nyní vytváří upozornění úrovně 2 C4091 pro všechny čtyři deklarace:

```cpp
struct A {};
template <typename> struct B {};
enum C { c1, c2, c3 };

int;    // warning C4091 : '' : ignored on left of 'int' when no variable is declared
A;      // warning C4091 : '' : ignored on left of 'main::A' when no variable is declared
B<int>; // warning C4091 : '' : ignored on left of 'B<int>' when no variable is declared
C;      // warning C4091 : '' : ignored on left of 'C' when no variable is declared
```

Chcete-li odstranit upozornění, komentář-out nebo odebrat prázdné deklarace. V případech, kdy je nepojmenovaný objekt určen k vedlejšímu účinku (například RAII), by měl mít název.

Upozornění je vyloučeno pod **/Wv:18** a je ve výchozím nastavení zapnuto pod úrovní upozornění W2.

### <a name="stdis_convertible-for-array-types"></a>`std::is_convertible`pro typy polí

Předchozí verze kompilátoru dal nesprávné výsledky pro [std::is_convertible](../standard-library/is-convertible-class.md) pro typy pole. To vyžadovalo zapisovače knihovny pro speciální `std::is_convertible<...>` případ kompilátoru Microsoft C++ při použití vlastnosti typu. V následujícím příkladu statické nepodmíněných výrazů projít v dřívějších verzích sady Visual Studio, ale nezdaří ve Visual Studiu 2017 verze 15.3:

```cpp
#include <type_traits>

using Array = char[1];

static_assert(std::is_convertible<Array, Array>::value);
static_assert(std::is_convertible<const Array, const Array>::value, "");
static_assert(std::is_convertible<Array&, Array>::value, "");
static_assert(std::is_convertible<Array, Array&>::value, "");
```

`std::is_convertible<From, To>`se vypočítá kontrolou, zda je definice imaginární funkce dobře tvarovaná:

```cpp
   To test() { return std::declval<From>(); }
```

### <a name="private-destructors-and-stdis_constructible"></a>Soukromé destruktory a`std::is_constructible`

Předchozí verze kompilátoru ignorovaly, zda byl destruktor soukromý při rozhodování o výsledku [std::is_constructible](../standard-library/is-constructible-class.md). Nyní je zvažuje. V následujícím příkladu statické nepodmíněných výrazů projít v dřívějších verzích sady Visual Studio, ale nezdaří ve Visual Studiu 2017 verze 15.3:

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

Soukromé destruktory způsobit typ nesestavitelné. `std::is_constructible<T, Args...>`se vypočítá tak, jako by bylo napsáno toto prohlášení:

```cpp
   T obj(std::declval<Args>()...)
```

Toto volání znamená destruktor volání.

### <a name="c2668-ambiguous-overload-resolution"></a>C2668: Nejednoznačné rozlišení přetížení

Předchozí verze kompilátoru někdy nepodařilo zjistit nejednoznačnost, když našel více kandidátů pomocí deklarací a vyhledávání závislé na argumentech. Toto selhání může vést k nesprávné přetížení je vybrán a neočekávané chování za běhu. V následujícím příkladu Visual Studio 2017 verze 15.3 správně vyvolá C2668 'f': nejednoznačné volání přetížené funkce:

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

Chcete-li opravit kód, `N::f` odeberte using `::f()`prohlášení, pokud jste chtěli volat .

### <a name="c2660-local-function-declarations-and-argument-dependent-lookup"></a>C2660: deklarace místních funkcí a vyhledávání závislé na argumentech

Deklarace místních funkcí skryjí deklaraci funkce v ohraničujícím oboru a zakáží vyhledávání závislé na argumentech. Předchozí verze kompilátoru však provedly vyhledávání závislé na argumentech v tomto případě, což může vést k nesprávnému přetížení, které je vybráno, a neočekávané mu chování za běhu. Obvykle je chyba z důvodu nesprávného podpisu deklarace místní funkce. V následujícím příkladu Visual Studio 2017 verze 15.3 správně vyvolává C2660 'f': funkce netrvá dva argumenty:

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

Chcete-li problém vyřešit, změňte `f(S)` podpis nebo jej odeberte.

### <a name="c5038-order-of-initialization-in-initializer-lists"></a>C5038: pořadí inicializace v seznamech inicializátoru

Členové třídy jsou inicializováni v pořadí, v jakém jsou deklarováni, nikoli v pořadí, ve které se zobrazují v seznamech inicializačních metod. Předchozí verze kompilátoru nevaroval, když pořadí inicializační ho seznamu se lišilo od pořadí deklarace. Tento problém může vést k nedefinované chování za běhu, pokud inicializace jednoho člena závisí na jiném členu v seznamu, který je již inicializován. V následujícím příkladu Visual Studio 2017 verze 15.3 (s **/Wall**) vyvolá "upozornění C5038: datový člen 'A::y' bude inicializován po datovém prvku 'A::x'":

```cpp
struct A
{
    A(int a) : y(a), x(y) {} // Initialized in reverse, y reused
    int x;
    int y;
};
```

Chcete-li problém vyřešit, uspořádejte seznam inicializátoru tak, aby měl stejné pořadí jako deklarace. Podobné upozornění je aktivována, když jeden nebo oba inicializátory odkazují na členy základní třídy.

Toto upozornění je mimo výchozí nastavení a ovlivňuje pouze kód kompilovaný s **/Wall**.

## <a name="bug-fixes-and-other-behavior-changes-in-155"></a><a name="update_155"></a>Opravy chyb a další změny chování v 15.5

### <a name="partial-ordering-change"></a>Částečná změna pořadí

Kompilátor nyní správně odmítne následující kód a zobrazí správnou chybovou zprávu:

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

Problém ve výše uvedeném příkladu je, že existují dva rozdíly v typech (const vs. non-const a pack vs. non-pack). Chcete-li odstranit chybu kompilátoru, odeberte jeden z rozdílů. To umožňuje kompilátoru jednoznačně objednat funkce.

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

Obslužné rutiny odkazu na typ pole nebo funkce se nikdy neshodují s objektem výjimky. Kompilátor nyní správně respektuje toto pravidlo a zvyšuje úroveň 4 upozornění. Také již neodpovídá obslužné rutině `char*` nebo `wchar_t*` literálu řetězce při použití **/Zc:strictStrings.**

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

Následující kód se této chybě vyhne:

```cpp
catch (int (*)[1]) {}
```

### <a name="stdtr1-namespace-is-deprecated"></a><a name="tr1"></a>`std::tr1` obor názvů je zastaralá

Nestandardní `std::tr1` obor názvů je nyní označen jako zastaralé v režimu C++ 14 i C++17. Ve Visual Studiu 2017 verze 15.5 následující kód vyvolává C4996:

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

### <a name="standard-library-features-in-annex-d-are-marked-as-deprecated"></a><a name="annex_d"></a>Standardní prvky knihovny v příloze D jsou označeny jako zastaralé

Je-li nastaven přepínač kompilátoru režimu **/std:c++17,** jsou téměř všechny standardní funkce knihovny v příloze D označeny jako zastaralé.

Ve Visual Studiu 2017 verze 15.5 následující kód vyvolává C4996:

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

### <a name="unreferenced-local-variables"></a>Neodkazované místní proměnné

V sadě Visual Studio 15.5 upozornění C4189 je emitován ve více případech, jak je znázorněno v následujícím kódu:

```cpp
void f() {
    char s[2] = {0}; // C4189. Either use the variable or remove it.
}
```

```Output
warning C4189: 's': local variable is initialized but not referenced
```

Chcete-li chybu opravit, odeberte nepoužitou proměnnou.

### <a name="single-line-comments"></a>Jednořádkové komentáře

Ve Visual Studio 2017 verze 15.5 upozornění C4001 a C4179 jsou již vydává compiler C. Dříve byly vyzařovány pouze pod přepínačem kompilátoru **/Za.**  Varování již nejsou potřeba, protože jednořádkové komentáře byly součástí standardu C od c99.

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

Pokud kód nemusí být zpětně kompatibilní, můžete se vyhnout upozornění odebráním potlačení C4001/C4179. Pokud kód musí být zpětně kompatibilní, potlačte pouze C4619.

```C

/* C only */

#pragma warning(disable:4619)
#pragma warning(disable:4001)
#pragma warning(disable:4179)

// single line comment
/* single line comment */
```

### <a name="__declspec-attributes-with-extern-c-linkage"></a>`__declspec`atributy `extern "C"` s propojením

V dřívějších verzích sady Visual Studio `__declspec(...)` kompilátor ignoroval atributy, když `__declspec(...)` byl použit před specifikaci `extern "C"` propojení. Toto chování způsobilo, že kód, který měl být generován, který uživatel neměl v úmyslu, s možnými důsledky runtime. Upozornění bylo přidáno ve visual tašti verze 15.3, ale ve výchozím nastavení bylo vypnuto. Ve Visual Studiu 2017 verze 15.5 je upozornění ve výchozím nastavení povoleno.

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

```Output
warning C4768: __declspec attributes before linkage specification are ignored
```

Chcete-li chybu opravit, umístěte specifikaci navázání před atribut __declspec:

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

Toto nové upozornění C4768 je uveden na některých hlavičkách sady Windows SDK, které byly dodány s Visual Studio 2017 15.3 nebo starší (například: verze 10.0.15063.0, také známý jako RS2 SDK). Novější verze hlaviček sady Windows SDK (konkrétně ShlObj.h a ShlObj_core.h) však byly opraveny tak, aby nevytvářely upozornění. Když se zobrazí toto upozornění pocházející ze záhlaví sady Windows SDK, můžete provést tyto akce:

1. Přepněte na nejnovější sadu Windows SDK dodané s visual studio 2017 verze 15.5 verze.

1. Vypněte upozornění kolem #include příkazu záhlaví sady Windows SDK:

```cpp
   #pragma warning (push)
   #pragma warning(disable:4768)
   #include <shlobj.h>
   #pragma warning (pop)
   ```

### <a name="extern-constexpr-linkage"></a><a name="extern_linkage"></a>Extern constexpr propojení

V dřívějších verzích sady Visual Studio kompilátor vždy dal **constexpr** proměnné vnitřní propojení i v případě, že proměnná byla označena **extern**. V sadě Visual Studio 2017 verze 15.5 umožňuje nový přepínač kompilátoru (**/Zc:externConstexpr**) správné chování odpovídající standardům. Nakonec toto chování se stane výchozí.

```cpp
extern constexpr int x = 10;
```

```Output
error LNK2005: "int const x" already defined
```

Pokud soubor záhlaví obsahuje proměnnou deklarovanou **extern constexpr**, musí být označen, `__declspec(selectany)` aby jeho duplicitní deklarace správně zkombinovala:

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

### <a name="typeid-cant-be-used-on-incomplete-class-type"></a>**typeid** nelze použít u neúplného typu třídy.

V dřívějších verzích sady Visual Studio kompilátor nesprávně povolil následující kód, což vedlo k potenciálně nesprávným informacím o typu. Ve Visual Sestudiu 2017 verze 15.5 kompilátor správně vyvolá chybu:

```cpp
#include <typeinfo>

struct S;

void f() { typeid(S); } //C2027 in 15.5
```

```Output
error C2027: use of undefined type 'S'
```

### <a name="stdis_convertible-target-type"></a>`std::is_convertible`cílový typ

`std::is_convertible`vyžaduje, aby cílový typ byl platný návratový typ. V dřívějších verzích sady Visual Studio kompilátor nesprávně povolil abstraktní typy, což může vést k nesprávnému řešení přetížení a neúmyslnému chování za běhu.  Následující kód nyní správně vyvolává C2338:

```cpp
#include <type_traits>

struct B { virtual ~B() = 0; };
struct D : public B { virtual ~D(); };

static_assert(std::is_convertible<D, B>::value, "fail"); // C2338 in 15.5
```

Chcete-li se vyhnout `is_convertible` chybě, při použití byste měli porovnat typy ukazatelů, protože porovnání bez typu ukazatele může selhat, pokud je jeden typ abstraktní:

```cpp
#include <type_traits>

struct B { virtual ~B() = 0; };
struct D : public B { virtual ~D(); };

static_assert(std::is_convertible<D *, B *>::value, "fail");
```

### <a name="dynamic-exception-specification-removal-and-noexcept"></a><a name="noexcept_removal"></a>Odebrání specifikace dynamické výjimky a **noexcept**

V jazyce `throw()` C++17 je alias pro **noexcept**, `throw(<type list>)` a `throw(...)` jsou odebrány a některé typy mohou obsahovat **noexcept**. Tato změna může způsobit problémy s kompatibilitou zdroje s kódem, který odpovídá C ++ 14 nebo starší. Přepínač **/Zc:noexceptTypes-** lze použít k návratu k verzi C++ 14 **noexcept** při použití režimu C++ 17 obecně. Umožňuje aktualizovat zdrojový kód tak, aby odpovídal c++ 17 bez `throw()` nutnosti přepisovat veškerý kód současně.

Kompilátor také nyní diagnostikuje další specifikace neodpovídající výjimky v deklaracích v režimu C++ 17 nebo s [/tolerantní-](../build/reference/permissive-standards-conformance.md) s novým upozorněním C5043.

Následující kód generuje C5043 a C5040 ve Visual Studiu 2017 verze 15.5 při použití přepínače **/std:c++17:**

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

Chcete-li odebrat chyby při stále používající **/std:c++ 17**, přidejte **/Zc:noexceptTypes-** přepnout do příkazového řádku, nebo aktualizujte kód použít **noexcept**, jak je znázorněno v následujícím příkladu:

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

### <a name="inline-variables"></a>Vložky proměnné

Statické constexpr datové členy jsou nyní implicitně v řádkové, což znamená, že jejich deklarace v rámci třídy je nyní jejich definice. Použití definice mimo řádek pro statický datový člen constexpr je redundantní a nyní zastaralé. Ve Visual Sestudiu 2017 verze 15.5 při použití přepínače **/std:c++17** následující kód nyní vytváří upozornění C5041 *'velikost': out-of-line definice pro constexpr statický datový člen není potřeba a je zastaralé v C ++ 17*:

```cpp
struct X {
    static constexpr int size = 3;
};
const int X::size; // C5041
```

### <a name="extern-c-__declspec-warning-c4768-now-on-by-default"></a>`extern "C" __declspec(...)`upozornění C4768 nyní ve výchozím nastavení zapnuto

Upozornění bylo přidáno ve Visual Studiu 2017 verze 15.3, ale ve výchozím nastavení bylo vypnuto. Ve Visual Studiu 2017 verze 15.5 je upozornění ve výchozím nastavení zapnuto. Další informace naleznete [v \_ \_tématu Nové upozornění na atributy declspec](#declspec).

### <a name="defaulted-functions-and-__declspecnothrow"></a>Výchozí funkce a`__declspec(nothrow)`

Kompilátor dříve povoleno výchozí funkce, `__declspec(nothrow)` které mají být deklarovány s když odpovídající základní/členské funkce povolené výjimky. Toto chování je v rozporu se standardem Jazyka C++ a může způsobit nedefinované chování za běhu. Standard vyžaduje, aby tyto funkce byly definovány jako odstraněné, pokud existuje neshoda specifikace výjimky.  V **části /std:c++17**vyvolá následující kód C2280 *a pokouší se odkazovat na odstraněnou funkci. Funkce byla implicitně odstraněna, protože specifikace explicitní výjimky není kompatibilní se specifikací implicitní deklarace.*

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

Chcete-li opravit tento kód, buď odebrat __declspec(nothrow) z výchozí funkce nebo odebrat `= default` a poskytnout definici funkce spolu s všechny požadované zpracování výjimek:

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

### <a name="noexcept-and-partial-specializations"></a>**noexcept** a dílčí specializace

S **noexcept** v systému typu částečné specializace pro odpovídající konkrétní "callable" typy může selhat zkompilovat nebo zvolit primární šablonu z důvodu chybějící částečné specializace pro ukazatele na noexcept-funkce.

V takových případech může být nutné přidat další částečné specializace pro zpracování **noexcept** ukazatele funkce a **noexcept** ukazatele na členské funkce. Tato přetížení jsou pouze legální v **režimu /std:c++17.** Pokud zpětná kompatibilita s C ++ 14 musí být zachována a píšete kód, který `#ifdef` ostatní spotřebovávají, pak byste měli chránit tyto nové přetížení uvnitř direktivy. Pokud pracujete v samostatném modulu, pak místo `#ifdef` použití stráží můžete pouze zkompilovat přepínač **/Zc:noexceptTypes-** .

Následující kód se zkompiluje pod **/std:c++14,** ale selže pod **/std:c++17** s\<chybou C2027:Use undefined typu A T>":

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

Následující kód je úspěšný pod **/std:c++17,** protože kompilátor `A<void (*)() noexcept>`zvolí novou částečnou specializaci :

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

## <a name="bug-fixes-and-other-behavior-changes-in-157"></a><a name="update_157"></a>Opravy chyb a další změny chování v 15.7

### <a name="c17-default-argument-in-the-primary-class-template"></a>C++17: Výchozí argument v šabloně primární třídy

Tato změna chování je předpokladem pro [odpočet argumentů Šablony pro šablony tříd - P0091R3](https://wg21.link/p0091r3).

Dříve kompilátor ignoroval výchozí argument v šabloně primární třídy:

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int = 0) {} // Re-definition necessary
```

V režimu **/std:c++17** ve Visual Studiu 2017 verze 15.7 není výchozí argument ignorován:

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int) {} // Default argument is used
```

### <a name="dependent-name-resolution"></a>Závislé překlad názvů

Tato změna chování je předpokladem pro [odpočet argumentů Šablony pro šablony tříd - P0091R3](https://wg21.link/p0091r3).

V následujícím příkladu kompilátor v sadě Visual Studio `D::type` 15.6 a starší překládá na `B<T>::type` v šabloně primární třídy.

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

Visual Studio 2017 verze 15.7 v **režimu /std:c++17** vyžaduje klíčové slovo**typename** v příkazu **using** v jazyce D. Bez**názvu typu**kompilátor vyvolá upozornění C4346: *"B<T\*>::type": závislý název není typ* a chyba C2061: *syntaktická chyba: identifikátor 'type'*:

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

### <a name="c17-nodiscard-attribute---warning-level-increase"></a>C++17: `[[nodiscard]]` atribut - zvýšení úrovně upozornění

V visual studio 2017 verze 15.7 v **/std:c++17** režimu se zvýší úroveň upozornění C4834 ("zahození vrácená hodnota funkce s atributem nodiscard") z W3 na W1. Upozornění můžete zakázat s obsazením do **void**, nebo předáním **/wd:4834** do kompilátoru

```cpp
[[nodiscard]] int f() { return 0; }

int main() {
    f(); // warning: discarding return value
         // of function with 'nodiscard'
}
```

### <a name="variadic-template-constructor-base-class-initialization-list"></a>Inicializační seznam konstruktéru variadické šablony

V předchozích vydáních sady Visual Studio byl chybně povolen seznam inicializace variadické šablony konstruktoru základní třídy, který chyběl v argumentech šablony bez chyby. Ve Visual Studio 2017 verze 15.7 je vyvolána chyba kompilátoru.

Následující příklad kódu ve Visual Sestudiu 2017 verze 15.7 vyvolává *chybu C2614: D\<int>: neplatná inicializace člena: 'B' není základní nebo člen*

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

Chcete-li chybu opravit, změňte výraz\<B() na B T>().

### <a name="constexpr-aggregate-initialization"></a>**constexpr** agregovaná inicializace

Předchozí verze kompilátoru Jazyka C++nesprávně **zpracovány constexpr** agregace; přijal neplatný kód, ve kterém agregační seznam měl příliš mnoho prvků a produkoval pro něj chybný kód. Následující kód je příkladem takového kódu:

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

V sadě Visual Studio 2017 verze 15.7 aktualizace 3 a novější předchozí příklad nyní vyvolává *C2078 příliš mnoho inicializátory*. Následující příklad ukazuje, jak opravit kód. Při inicializaci `std::array` s vnořené složená závorka-init-seznamy, dát vnitřní pole vyztužený seznam jeho vlastní:

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

## <a name="bug-fixes-and-behavior-changes-in-158"></a><a name="update_158"></a>Opravy chyb a změny chování v 15.8

Změny kompilátoru ve Visual Studiu 2017 verze 15.8 všechny spadají do kategorie opravy chyb a změny chování a jsou uvedeny níže:

### <a name="typename-on-unqualified-identifiers"></a>**typename** na neúplných identifikátorech

V [/tolerantní-](../build/reference/permissive-standards-conformance.md) režim, falešné**typename** klíčová slova na neúplné identifikátory v definicích šablony alias již nejsou přijímány kompilátorem. Následující kód nyní vytváří C7511 *'T': 'typename' klíčové slovo musí následovat kvalifikovaný název*:

```cpp
template <typename T>
using  X = typename T;
```

Chcete-li chybu opravit, změňte druhý řádek na `using  X = T;`.

### <a name="__declspec-on-right-side-of-alias-template-definitions"></a>`__declspec()`na pravé straně definic šablon aliasů

[__declspec](../cpp/declspec.md) již není povoleno na pravé straně definice alias šablony. Tento kód byl dříve přijat, ale ignorován kompilátorem a nikdy by nevedl k upozornění na vyřazení při použití aliasu.

Standardní atribut [ \[ \[\] ](../cpp/attributes.md) C++ zastaralé lze použít místo a je respektována v Sadě Visual Studio 2017 verze 15.6. Následující kód nyní vytváří chybu syntaxe C2760: *neočekávaný token '__declspec', očekávaný specifikátor typu:*

```cpp
template <typename T>
using X = __declspec(deprecated("msg")) T;
```

Chcete-li chybu opravit, změňte na kód na následující (s atributem umístěným před '=' definice aliasu):

```cpp
template <typename T>
using  X [[deprecated("msg")]] = T;
```

### <a name="two-phase-name-lookup-diagnostics"></a>Dvoufázová diagnostika vyhledávání názvů

Dvoufázové vyhledávání názvů vyžaduje, aby nezávislé názvy používané v tělech šablony byly viditelné pro šablonu v době definice. Dříve kompilátor Microsoft C++ by ponechat nenalezený název jako nevyhledávaný až do doby instance. Nyní vyžaduje, aby nezávislé názvy byly vázány v těle šablony.

Jedním ze způsobů, jak to může manifest je s vyhledávání do závislé základní třídy. Dříve kompilátor povolil použití názvů, které jsou definovány v závislých základních třídách, protože by byly vyhledány během doby instance, když jsou vyřešeny všechny typy. Nyní, že kód je považován za chybu. V těchto případech můžete vynutit proměnnou, která má být vyhledána v době instance, tím, že ji `this->` kvalifikujete s typem základní třídy nebo jinak ji učiní závislou, například přidáním ukazatele.

V [/tolerantní-](../build/reference/permissive-standards-conformance.md) režimu následující kód nyní vyvolává C3861: *'base_value': identifikátor nebyl nalezen*:

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

Chcete-li chybu opravit, změňte `return` příkaz na `return this->base_value;`.

**Poznámka:** V knihovně Python boost, tam byl po dlouhou dobu MSVC specifické řešení pro předsunuté deklarace šablony v [unwind_type.hpp](https://github.com/boostorg/python/blame/develop/include/boost/python/detail/unwind_type.hpp). V [/tolerantní-](../build/reference/permissive-standards-conformance.md) režim počínaje Visual Studio 2017 verze 15.8 (_MSC_VER=1915) kompilátor MSVC provádí vyhledávání názvů závislých na argumentech (ADL) správně a je konzistentní s ostatními kompilátory, takže toto řešení ochrana není nutná. Chcete-li se vyhnout chybě *C3861: 'unwind_type': identifikátor nebyl nalezen*, viz [PR 229](https://github.com/boostorg/python/pull/229) v repo boost aktualizovat soubor záhlaví. Balíček [vcpkg](../build/vcpkg.md) Boost jsme již opravili, takže pokud získáte nebo upgradujete zdroje boostů z vcpkg, nemusíte náplast aplikovat samostatně.

### <a name="forward-declarations-and-definitions-in-namespace-std"></a>předávání deklarací a definic v oboru názvů`std`

Standard C++ neumožňuje uživateli přidávat dopředné deklarace nebo `std`definice do oboru názvů . Přidání deklarací nebo definic `std` do oboru názvů nebo `std` do oboru názvů v oboru názvů nyní vede k nedefinovanému chování.

Někdy v budoucnu společnost Microsoft přesune umístění, kde jsou definovány některé standardní typy knihoven. Tato změna přeruší existující kód, který `std`přidá dopředné deklarace do oboru názvů . Nové upozornění, C4643, pomáhá identifikovat tyto problémy se zdrojem. Upozornění je povoleno v **/default** režimu a je ve výchozím nastavení vypnuto. Bude mít vliv na programy, které jsou kompilovány s **/Wall** nebo **/WX**.

Následující kód nyní vyvolává C4643: *Forwarddedeclaring 'vector' v oboru názvů std není povoleno c++ standard*.

```cpp
namespace std {
    template<typename T> class vector;
}
```

Chcete-li chybu opravit, použijte **direktivu include** spíše než dopřednou deklaraci:

```cpp
#include <vector>
```

### <a name="constructors-that-delegate-to-themselves"></a>Konstruktory, které delegují na sebe

Standard Jazyka C++ navrhuje, aby kompilátor vyzařoval diagnostiku, když delegující konstruktor deleguje na sebe. Kompilátor Microsoft C++ v [/std:c++17](../build/reference/std-specify-language-standard-version.md) a [/std:c++latest](../build/reference/std-specify-language-standard-version.md) režimy nyní vyvolává C7535: *'X::X': delegování konstruktoru volá sám*.

Bez této chyby se zkompiluje následující program, ale vygeneruje nekonečnou smyčku:

```cpp
class X {
public:
    X(int, int);
    X(int v) : X(v){}
};
```

Chcete-li se vyhnout nekonečné smyčce, delegujte na jiného konstruktoru:

```cpp
class X {
public:

    X(int, int);
    X(int v) : X(v, 0) {}
};
```

### <a name="offsetof-with-constant-expressions"></a>`offsetof`s konstantními výrazy

[offsetof](../c-runtime-library/reference/offsetof-macro.md) byl tradičně implementován pomocí makra, který vyžaduje [reinterpret_cast](../cpp/reinterpret-cast-operator.md). Toto použití je nezákonné v kontextech, které vyžadují konstantní výraz, ale kompilátor Microsoft C++ jej tradičně povolil. Makro, `offsetof` které je dodáno jako součást standardní knihovny, správně používá vnitřní kompilátor (**__builtin_offsetof**), `offsetof`ale mnoho lidí použilo makro trik k definování vlastního .

Ve Visual Studio 2017 verze 15.8 kompilátor omezuje `reinterpret_cast` oblasti, které tyto operátory se mohou zobrazit ve výchozím režimu, aby kód odpovídal standardnímu chování C++. Pod [/tolerantní-](../build/reference/permissive-standards-conformance.md), omezení jsou ještě přísnější. Použití výsledku `offsetof` v místech, které vyžadují konstantní výrazy může mít za následek kód, který vydává upozornění C4644 *použití vzoru založeného na makru offsetof v konstantní výrazy je nestandardní; použití offsetof definované ve standardní knihovně C++ místo* nebo C2975 *neplatné šablony argument, očekávané kompilace čas konstantní výraz*.

Následující kód vyvolá C4644 v **/default** a **/std:c++17** režimy a C2975 v [/tolerantní-](../build/reference/permissive-standards-conformance.md) režimu:

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

Chcete-li chybu `offsetof` opravit, \<použijte tak, jak je definováno pomocí cstddef>:

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

### <a name="cv-qualifiers-on-base-classes-subject-to-pack-expansion"></a>cv-kvalifikátory na základní třídy, které podléhají rozšíření balení

Předchozí verze kompilátoru Microsoft C++ nezjistily, že základní třída měla cv-qualifiers, pokud byla také předmětem rozšíření balení.

V Visual Studio 2017 verze 15.8 v [/tolerantní-](../build/reference/permissive-standards-conformance.md) režim následující kód vyvolává C3770 *'const S': není platná základní třída*:

```cpp
template<typename... T>
class X : public T... { };

class S { };

int main()
{
    X<const S> x;
}
```

### <a name="template-keyword-and-nested-name-specifiers"></a>**klíčové** slovo šablony a specifikátory vnořených názvů

V [/tolerantní-](../build/reference/permissive-standards-conformance.md) režimkompilátor nyní **vyžaduje,** aby klíčové slovo šablony předcházelo názvu šablony, když přichází po závislém specifikátoru vnořeného názvu.

Následující kód v [/tolerantní-](../build/reference/permissive-standards-conformance.md) režim nyní vyvolává C7510: *'příklad': použití závislé ho názvu šablony musí být předponou 'template'. poznámka: viz odkaz na instanování šablony třídy 'X\<T>' se kompiluje*:

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

Chcete-li chybu opravit, přidejte `Base<T>::example<int>();` do příkazu klíčové slovo **šablony,** jak je znázorněno v následujícím příkladu:

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

## <a name="bug-fixes-and-behavior-changes-in-159"></a><a name="update_159"></a>Opravy chyb a změny chování v 15.9

### <a name="identifiers-in-member-alias-templates"></a>Identifikátory v šablonách aliasů členů

Identifikátor použitý v definici šablony aliasu člena musí být deklarován před použitím.

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

Ve Visual Studio 2017 verze 15.9 v [/tolerantní-](../build/reference/permissive-standards-conformance.md) režimu kompilátor vyvolá C3861: *'from_template': identifikátor nebyl nalezen*.

Chcete-li chybu `from_template` opravit, deklarujte před `from_template_t`.

### <a name="modules-changes"></a>Změny modulů

V sadě Visual Studio 2017 verze 15.9 kompilátor vyvolá C5050 vždy, když možnosti příkazového řádku pro moduly nejsou konzistentní mezi vytvoření modulu a spotřeba modulu strany. V následujícím příkladu existují dva problémy:

- Na straně spotřeby (main.cpp) není zadána možnost **/EHsc.**

- Verze jazyka C++ je **/std:c++17** na straně vytvoření a **/std:c++14** na straně spotřeby.

```cmd
cl /EHsc /std:c++17 m.ixx /experimental:module
cl /experimental:module /module:reference m.ifc main.cpp /std:c++14
```

Kompilátor vyvolá C5050 pro oba tyto případy: *upozornění C5050: Možné nekompatibilní prostředí při importu modulu 'm': neodpovídající verze C++.  Aktuální "201402" verze modulu "201703"*.

Kompilátor také vyvolá C7536 vždy, když byl soubor .ifc zfalšován. Záhlaví rozhraní modulu obsahuje hodnotu hash SHA2 obsahu pod ním. Při importu je soubor .ifc zachycován stejným způsobem a poté zkontrolován proti hash uvedené v záhlaví. Pokud tyto neshodují, je vyvolána chyba C7536: *ifc selhaly kontroly integrity.  Očekávané SHA2: '66d5c8154df0c71d4cab7665bab4a125c7ce5cb9a401a4d8b461b706ddd771c6'*.

### <a name="partial-ordering-involving-aliases-and-non-deduced-contexts"></a>Částečné řazení zahrnující aliasy a neodvozené kontexty

Implementace se liší v pravidlech částečné řazení zahrnující aliasy v neodvozených kontextech. V následujícím příkladu GCC a kompilátor Microsoft C++ (v [/tolerantní-](../build/reference/permissive-standards-conformance.md) režim) vyvolat chybu, zatímco Clang přijímá kód.

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

Implementace divergence je z důvodu regrese ve standardním znění jazyka C++. Řešení základní problém 2235 odebrány některé text, který by umožnil tyto přetížení objednat. Aktuální standard Jazyka C++ neposkytuje mechanismus pro částečné pořadí těchto funkcí, takže jsou považovány za nejednoznačné.

Jako řešení doporučujeme, abyste se k vyřešení tohoto problému nespoléhali na částečné řazení. Místo toho použijte SFINAE k odstranění konkrétní přetížení. V následujícím příkladu používáme pomocnou třídu `IsA` k `Alloc` odstranění prvnípřetížení, když je specializace `A`:

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

### <a name="illegal-expressions-and-non-literal-types-in-templated-function-definitions"></a>Neplatné výrazy a neliterárné typy v definicích šablonovaných funkcí

Nelegální výrazy a typy bez literálu jsou nyní správně diagnostikovány v definicích šablonovaných funkcí, které jsou explicitně specializované. Dříve tyto chyby nebyly vyzařovány pro definici funkce. Nelegální výraz nebo nedoslovný typ by však stále byly diagnostikovány, pokud by byly vyhodnoceny jako součást konstantní výraz.

V předchozích verzích sady Visual Studio se bez upozornění zkompiluje následující kód:

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

Ve Visual Studiu 2017 verze 15.9 kód vyvolává tuto chybu:

```Output
error C3615: constexpr function 'S<int>::f' cannot result in a constant expression.
note: failure was caused by call of undefined function or one not declared 'constexpr'
note: see usage of 'g'.
```

Chcete-li se vyhnout chybě, odeberte kvalifikátor `f()` **constexpr** z explicitní instance funkce .

::: moniker-end

::: moniker range="vs-2015"

## <a name="c-conformance-improvements-in-visual-studio-2015"></a>Vylepšení shody jazyka C++ ve Visual Studiu 2015

Úplný seznam vylepšení shody až do Visual Studio 2015 Update 3, najdete [v tématu Visual C++ Co je nového 2003 až 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015).

::: moniker-end

## <a name="see-also"></a>Viz také

[Tabulka shody jazyků Microsoft C++](../visual-cpp-language-conformance.md)
