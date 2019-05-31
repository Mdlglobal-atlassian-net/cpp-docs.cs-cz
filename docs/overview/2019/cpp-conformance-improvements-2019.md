---
title: Vylepšení shody C++
ms.date: 05/16/2019
description: Microsoft C++ v aplikaci Visual Studio 2019 postupujte směrem k plný soulad se standardem 20 jazyka C++.
ms.technology: cpp-language
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 02b778f10ad94342c922a4e79a856cc2a7d53076
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66451215"
---
# <a name="c-conformance-improvements-in-visual-studio-2019-rtw-and-version-161improvements161"></a>C++vylepšení ve verzi RTW 2019 Visual Studio a verze [16.1](#improvements_161)

## <a name="improvements-in-visual-studio-2019-rtw"></a>Vylepšení ve verzi RTW 2019 Visual Studio

Visual Studio 2019 RTW obsahuje následující vylepšení, oprav chyb a změny chování v kompilátoru C++ společnosti Microsoft (MSVC).

**Poznámka:** 20 funkce c ++ bude k dispozici v `/std:c++latest` režimu až do dokončení provádění 20 C ++ pro kompilátor a technologie IntelliSense. V tu chvíli `/std:c++20` režim kompilátoru se bude zavádět.

### <a name="improved-modules-support-for-templates-and-error-detection"></a>Moduly Vylepšená podpora pro šablony a detekce chyb

Moduly jsou nyní oficiálně v C ++ 20 standard. Vylepšená podpora byl přidán v sadě Visual Studio 2017 verze 15.9. Další informace najdete v tématu [lepší podporu a Chyba zjišťování šablony v moduly C++ s MSVC 2017 verzi 15.9](https://devblogs.microsoft.com/cppblog/better-template-support-and-error-detection-in-c-modules-with-msvc-2017-version-15-9/).

### <a name="modified-specification-of-aggregate-type"></a>Změny specifikace požadovaný typ agregace

Specifikace agregační typ se změnil v C ++ 20 (viz [zakázat agregace s uživatelem deklarované konstruktory](https://wg21.link/p1008r1)). V aplikaci Visual Studio 2019 pod `/std:c++latest`, třída s atributem žádné uživatelem deklarovaným konstruktorem (například včetně konstruktor deklarovat `= default` nebo `= delete`) není agregační. Předtím jenom uživatelem zadané konstruktory by vyřadit třídy z se agregace. Tato změna vloží další omezení na tom, jak lze inicializovat tyto typy.

Následující kód zkompiluje bez chyb v sadě Visual Studio 2017, ale vyvolává chyby C2280 a C2440 v aplikaci Visual Studio 2019 pod `/std:c++latest`:

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

### <a name="partial-support-for-operator-"></a>Částečně se podporuje <> = – operátor

[P0515R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0515r3.pdf) zavádí C ++ 20 `<=>` operátor porovnání trojcestných, označované také jako "kosmické lodě operátor". Visual Studio 2019 v `/std:c++latest` režimu zavádí částečně se podporuje pro operátor vyvoláním chyby syntaxe, která je teď zakázaná. Například následující kód zkompiluje bez chyb v sadě Visual Studio 2017, ale vyvolá více chyb v aplikaci Visual Studio 2019 pod `/std:c++latest`:

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

Aby nedošlo k chybám, vložte mezeru v problematický řádek před posledním závorky: `U<&S::operator<= > u;`.

### <a name="references-to-types-with-mismatched-cv-qualifiers"></a>Odkazy na typy s neodpovídající kvalifikátory cv

MSVC dříve povolen přímé vazby odkazu z typu s neodpovídající kvalifikátory cv níže nejvyšší úrovně. To by mohlo znamenat úpravy údajně const dat, na které odkazuje odkaz, a kompilátor nyní vytvoří dočasnou znamének podle standardu. V sadě Visual Studio 2017 následující kód zkompiluje bez upozornění. V aplikaci Visual Studio 2019, kompilátor vyvolá *upozornění C4172: \<func: č. 1 "?PData@X @@QBEABQBXXZ"> vrací adresu lokální proměnné nebo dočasné*.

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
### <a name="reinterpretcast-from-an-overloaded-function"></a>`reinterpret_cast` z přetížené funkce

Argument `reinterpret_cast` není jedním z kontextu, ve kterých je povolená adresa přetíženou funkci. Následující kód se zkompiluje bez chyb v sadě Visual Studio 2017, ale v aplikaci Visual Studio 2019 vyvolá *C2440: nelze převést z "přetížené funkce" na "fp"* :

```cpp
int f(int) { return 1; }
int f(float) { return .1f; }
using fp = int(*)(int);

int main()
{
    fp r = reinterpret_cast<fp>(&f);
}
```

Aby se zabránilo chybu, použijte povolených přetypování pro tento scénář:

```cpp
int f(int);
int f(float);
using fp = int(*)(int);

int main()
{
    fp r = static_cast<fp>(&f); // or just &f;
}
```

### <a name="lambda-closures"></a>Uzávěry lambda

V C ++ 14 nejsou typy uzávěru lambda literálu. Primární důsledkem tohoto pravidla je, že výraz lambda nemůže být přiřazeno k `constexpr` proměnné. Následující kód zkompiluje bez chyb v sadě Visual Studio 2017, ale v aplikaci Visual Studio 2019 ho vyvolá *C2127: "l": Neplatná inicializace entity 'constexpr' se nekonstantní výraz* :

```cpp
int main()
{
    constexpr auto l = [] {}; // C2127 in VS2019
}
```

Aby se zabránilo chybě, buď odeberte `constexpr` kvalifikátor, jinak změnit režim přizpůsobení na `/std:c++17`.

### <a name="stdcreatedirectory-failure-codes"></a>Kódy selhání std::create_directory

Implementovat [P1164](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1164r1.pdf) z C ++ 20 nepodmíněně. Tím se změní `std::create_directory` ke kontrole, zda cíl byl již adresář při selhání. Dříve byly všechny chyby typu ERROR_ALREADY_EXISTS převedena na úspěch ale – adresář not vytvořené kódy.

### <a name="operatorstdostream-nullptrt"></a>Operator < <(std::ostream, nullptr_t)

Za [LWG 2221](https://cplusplus.github.io/LWG/issue2221)přidali `operator<<(std::ostream, nullptr_t)` pro zápis nullptrs datových proudů. 

### <a name="additional-parallel-algorithms"></a>Další paralelní algoritmy

Nové paralelní verze `is_sorted`, `is_sorted_until`, `is_partitioned`, `set_difference`, `set_intersection`, `is_heap`, a `is_heap_until`.

### <a name="atomic-initialization"></a>Atomic inicializace

[P0883 "řešení atomic inicializace"](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0883r1.pdf) změny `std::atomic` hodnota inicializace omezením T spíše než výchozí-jeho inicializaci. Oprava zapnutý, při použití Clang/LLVM pomocí standardní knihovny Microsoft. Pro Microsoft je aktuálně zakázaný C++ kompilátoru jako alternativní řešení pro chybu při zpracování constexpr.

### <a name="removecvref-and-removecvreft"></a>remove_cvref a remove_cvref_t

Implementováno `remove_cvref` a `remove_cvref_t` zadejte vlastnosti z [P0550](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0550r2.pdf). Tím odpadne odkaz ness a cv kvalifikace z typu bez Slábnoucí funkce a pole ukazatelů (na rozdíl od `std::decay` a `std::decay_t`).

### <a name="feature-test-macros"></a>Makra testu funkcí

[P0941R2 – makra testu funkcí](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0941r2.html) je kompletní s podporou `__has_cpp_attribute`. Makra testu funkcí jsou podporovány ve všech režimech Standard.

### <a name="prohibit-aggregates-with-user-declared-constructors"></a>Zakázat agregace s uživatelem deklarované konstruktory

[C ++ 20 P1008R1 – zákaz agregace s uživatelem deklarované konstruktory](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p1008r1.pdf) je dokončena.

## <a name="improvements_161"></a> Vylepšení v aplikaci Visual Studio 2019 verze 16.1

### <a name="char8t"></a>char8_t

[P0482r6](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0482r6.html). C ++ 20 přidá nový typ znaku, který se používá k reprezentování jednotkami kódu kódování UTF-8. U8 řetězcové literály v C ++ 20 mít typ `const char8_t[N]` místo `const char[N]`, která dříve byla případu. Podobné změny byly navrženy pro Standard C v [N2231](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2231.htm). Návrhům na odstranění problému char8_t zpětné kompatibility jsou uvedeny v [P1423r0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1423r0.html). Microsoft C++ kompilátor přidává podporu pro char8_t v aplikaci Visual Studio 2019 verze 16.1 při zadávání **/Zc:char8_t** – možnost kompilátoru. V budoucnu se bude podporovat s [/std: c ++ nejnovější](../../build/reference/std-specify-language-standard-version.md), která se vrátí zpátky na C ++ 17 chování prostřednictvím **/Zc:char8_t-** . Zaměstnance EDG kompilátoru, který využívá technologie IntelliSense zatím nepodporuje, proto uvidíte detekováno falešné pouze technologie IntelliSense chyby, které nemají vliv na skutečné kompilace.

#### <a name="example"></a>Příklad

```cpp
const char* s = u8"Hello"; // C++17
const char8_t* s = u8"Hello"; // C++20
```

### <a name="stdtypeidentity-metafunction-and-stdidentity-function-object"></a>objekt std::type_identity metafunkcí a std::identity – funkce

[P0887R1 type_identity](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0887r1.pdf). Zastaralá `std::identity` rozšíření pro třídu šablony má byl odebrán a nahrazen parametrem 20 C ++ `std::type_identity` metafunkcí a `std::identity` objektu funkce. Obě jsou k dispozici pouze v rámci [/std: c ++ nejnovější](../../build/reference/std-specify-language-standard-version.md). 

Následující příklad generuje upozornění C4996 pro vyřazení `std::identity` (definované v \<type_traits >) v sadě Visual Studio 2017: 

```cpp
#include <type_traits>

using T = std::identity<int>::type;
T x, y = std::identity<T>{}(x);
int i = 42;
long j = std::identity<long>{}(i);
```

Následující příklad ukazuje způsob použití nového `std::identity` (definované v \<funkční >) společně s novou `std::type_identity`:

```cpp
#include <type_traits>
#include <functional>

using T = std::type_identity<int>::type;
T x, y = std::identity{}(x);
int i = 42;
long j = static_cast<long>(i);
```

### <a name="syntax-checks-for-generic-lambdas"></a>Kontroly syntaxe pro obecné výrazy lambda

Nový procesor lambda umožňuje některé syntaktické kontroly režim přizpůsobení v obecné výrazy lambda v části [/std: c ++ nejnovější](../../build/reference/std-specify-language-standard-version.md) nebo v jiné jazykové režimu s **/ experimentální: newLambdaProcessor**. 

V sadě Visual Studio 2017, tento kód zkompiluje bez upozornění, ale v aplikaci Visual Studio 2019 způsobil chybu *C2760 Chyba syntaxe: Neočekávaný token "\<id expr >", 'id výraz' byl očekáván*:

```cpp
void f() {
    auto a = [](auto arg) {
        decltype(arg)::Type t;
    };
}
```

Následující příklad ukazuje správná syntaxe nyní vynucena kompilátorem:

```cpp
void f() {
    auto a = [](auto arg) {
        typename decltype(arg)::Type t;
    };
}
```

### <a name="argument-dependent-lookup-for-function-calls"></a>Vyhledávání závislé na argumentu pro volání funkce

[P0846R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0846r0.html) (C ++ 20) zvýšila schopnost najít šablony funkcí přes vyhledávání závislé na argumentu pro výrazy volání funkce s explicitní argumenty šablony. Vyžaduje **/std: c ++ nejnovější**.

### <a name="designated-initialization"></a>Určené inicializace

[P0329R4](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0329r4.pdf) (C ++ 20) určené inicializace umožňuje členy, kteří mají být vybrány v inicializace agregace pomocí `Type t { .member = expr }` syntaxe. Vyžaduje **/std: c ++ nejnovější**.

### <a name="new-and-updated-standard-library-functions-c20"></a>Nové a aktualizované funkce standardní knihovny (C ++ 20)

- `starts_with()` a `ends_with()` pro `basic_string` a `basic_string_view`.
- `contains()` pro asociativní kontejnery.
- `remove()`, `remove_if()`, a `unique()` pro` list` a `forward_list` se teď vrátit `size_type`.
- `shift_left()` a `shift_right()` přidán do \<algoritmus >.

## <a name="bug-fixes-and-behavior-changes-in-visual-studio-2019-rtw"></a>Opravy chyb a změny chování v aplikaci Visual Studio. 2019 RTW

### <a name="correct-diagnostics-for-basicstring-range-constructor"></a>Správné diagnostiky basic_string rozsahu konstruktoru

V aplikaci Visual Studio 2019 `basic_string` rozsahu konstruktoru už potlačí diagnostiky kompilátoru s `static_cast`. Následující kód se zkompiluje bez upozornění v sadě Visual Studio 2017, bez ohledu na může dojít ke ztrátě dat z `wchar_t` k `char` při inicializaci `out`:

```cpp
std::wstring ws = /* … */;
std::string out(ws.begin(), ws.end());
```

Visual Studio 2019 správně vyvolá *C4244: 'argument': převod z "wchar_t" na "const _Elem", může dojít ke ztrátě dat*. Aby se zabránilo upozornění, můžete inicializovat std::string jak je znázorněno v tomto příkladu:

```cpp
std::wstring ws = L"Hello world";
std::string out;
for (wchar_t ch : ws)
{
    out.push_back(static_cast<char>(ch));
}
```

### <a name="incorrect-calls-to--and---under-clr-or-zw-are-now-correctly-detected"></a>Nesprávné volání += a-= pod parametrem/CLR nebo /ZW jsou nyní správně rozpozná

Chyba byla zavedena v aplikaci Visual Studio 2017, která způsobila kompilátor tiše ignorovat chyby a vygenerovat žádný kód pro neplatné volání += a-= pod `/clr` nebo `/ZW`. Následující kód se zkompiluje bez chyb v sadě Visual Studio 2017, ale v aplikaci Visual Studio 2019 správně vyvolá *chyba C2845: "System::String ^': aritmetika ukazatele není povolené pro tento typ*:

```cpp
public enum class E { e };

void f(System::String ^s)
{
    s += E::e; // C2845 in VS2019
}
```

Aby se zabránilo chybě v tomto příkladu, použijte operátor pomocí metody ToString(): `s += E::e.ToString();`.

### <a name="initializers-for-inline-static-data-members"></a>Inicializátory pro vložené statické datové členy

Neplatný člen přistupuje k v rámci `inline` a `static constexpr` inicializátory jsou nyní správně rozpozná. Následující příklad se zkompiluje bez chyb v sadě Visual Studio 2017, ale Visual Studio 2019 pod `/std:c++17` režimu vyvolá *chyba C2248: přístup privátního člena nelze deklarovat v třídě 'X'* .

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

Aby se zabránilo chybě deklarovat člen `X::c` jako chráněný:

```cpp
struct X
{
    protected:
        static inline const int c = 1000;
};
```

### <a name="c4800-reinstated"></a>C4800 obnoveny

MSVC mívali výkon upozornění C4800 o implicitní převod na celočíselnou hodnotu, která byla příliš aktivní nebo insuppressible, vedoucí nám odebrat v sadě Visual Studio 2017. Nicméně přes životního cyklu sady Visual Studio 2017 nám dává spoustu zpětné vazby na užitečné případy, které se řešení. Jsme vrácení Visual Studio 2019 pečlivě míru C4800 spolu s jeho související C4165, které jde snadno potlačit explicitní přetypování nebo porovnání 0 příslušného typu. C4800 se o varování mimo výchozí úroveň 4 a C4165 se o varování mimo výchozí úroveň 3. Obě jsou zjistitelné pomocí `/Wall` – možnost kompilátoru.

V následujícím příkladu vyvolává C4800 a C4165 pod `/Wall`:

```cpp
bool test(IUnknown* p)
{
    bool valid = p; // warning C4800: Implicit conversion from 'IUnknown*' to bool. Possible information loss
    IDispatch* d = nullptr;
    HRESULT hr = p->QueryInterface(__uuidof(IDispatch), reinterpret_cast<void**>(&d));
    return hr; // warning C4165: 'HRESULT' is being converted to 'bool'; are you sure this is what you want?
}
```

Aby se zabránilo upozornění v předchozím příkladu, můžete napsat kód následujícím způsobem:

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

In Visual Studio 2017, *C4822: Členská funkce lokální třídy nemá tělo* je vyvolána pouze tehdy, když – možnost kompilátoru `/w14822` je explicitně nastaveno; není zobrazen s `/Wall`. V aplikaci Visual Studio 2019 C4822 je vypnuto výchozím upozornění, díky tomu zjistitelný v rámci `/Wall` bez nutnosti nastavení `/w14822` explicitně.

```cpp
void foo()
{
    struct A
        {
            int boo(); // warning C4822
        };
}
```

### <a name="function-template-bodies-containing-constexpr-if-statements"></a>Funkce šablony těla obsahující constexpr, pokud příkazy

Těla funkcí šablony obsahující `if constexpr` příkazy mají některé `/permissive-` povoleny kontroly související s analýza kódu. Například v sadě Visual Studio 2017 vytváří následující kód jazyka C*7510: 'Type': použití názvu závislého typu musí být předponou 'typename'* pouze tehdy, pokud `/permissive-` není nastaven. V aplikaci Visual Studio 2019 stejný kód vyvolává chyby určuje, jestli `/permissive-` je nastavena možnost:

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

Chcete-li chybě zabránit, přidejte `typename` – klíčové slovo do deklarace `a`: `typename T::Type a;`.

### <a name="inline-assembly-code-is-not-supported-in-a-lambda-expression"></a>Vložený kód sestavení není podporován ve výrazu lambda

Týmu Visual C++ byla nedávno informováni o bezpečnostní riziko, ve kterém se použití inline assembleru v rámci výrazu lambda může vést k poškození ebp"(zpáteční adresu register) za běhu. Se zlými úmysly může být možné využít tento scénář. Vzhledem k povaze problému, skutečnost, že vložený assembler je podporována pouze na x86 a špatné interakce vložený assembler se zbytkem kompilátoru, které bylo považováno za, nejbezpečnější řešení tohoto problému bylo zakázat vložený assembler v rámci výrazu lambda výraz.

Poznámka: pouze použití inline assembleru v rámci výrazu lambda, který jsme narazili v "reálném světě" bylo použití, ve kterém cílem bylo k zachycení zpáteční adresu. V tomto scénáři můžete zachytit zpáteční adresa pro všechny platformy jednoduše tak, že pomocí vnitřní kompilátor `_ReturnAddress()`.

Následující kód vytvoří *C7552: vložený assembler není podporován ve výrazu lambda* v obou Visual Studio 2017 15.9 a Visual Studio 2019:

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

Aby se zabránilo chybě, přesune sestavení kód do pojmenované funkce, jak je znázorněno v následujícím příkladu:

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

### <a name="iterator-debugging-and-stdmoveiterator"></a>Iterační ladění a std::move_iterator

Iterační ladění funkce má byla museli k rozbalení správně `std::move_iterator`. Například `std::copy(std::move_iterator<std::vector<int>::iterator>, std::move_iterator<std::vector<int>::iterator>, int*)` teď můžete zapojit `memcpy` rychlou cestu.

### <a name="fixes-for-xkeycheckh-keyword-enforcement"></a>Opravy \<xkeycheck.h > Vynucení – klíčové slovo

Standardní knihovna – makro ized – klíčové slovo vynucení \<xkeycheck.h > byl nastaven na generování skutečný problém – klíčové slovo zjištěno místo obecná zpráva. Také podporuje C ++ 20 klíčová slova a zabraňuje, přičemž technologie IntelliSense do o tom, že náhodné klíčová slova jsou makra.

### <a name="allocator-types-un-deprecated"></a>Typy přidělování zrušení zastaralé

`std::allocator<void>`, `std::allocator::size_type`, a `std::allocator::difference_type` byly zrušení zastaralé.

### <a name="correct-warning-for-narrowing-string-conversions"></a>Opravit upozornění pro zužující převody řetězců

Nesprávné `static_cast` není volán podle standardu omylem Potlačené C4244 zúžení upozornění byla odebrána z std::string. Pokus o volání `std::string::string(const wchar_t*, const wchar_t*)` bude nyní správně generovat *C4244 "zúžení wchar_t do typu char."*

### <a name="various-filesystem-correctness-fixes"></a>Různé \<filesystem > řeší správnost

- Oprava `std::filesystem::last_write_time` selhání při pokusu o změnu adresáře vaší poslední čas zápisu.
- `std::filesystem::directory_entry` Konstruktoru nyní ukládá neúspěšných výsledků namísto vyvolání výjimky, pokud je zadán neexistující cílovou cestu.
- `std::filesystem::create_directory` Verze 2 parametr byl změněn na volání verze 1 parametr, jako základní `CreateDirectoryExW` bude provádět funkce `copy_symlink` kdy byla existing_p symlink.
- `std::filesystem::directory_iterator` už selže, pokud dochází k porušení symlink.
- `std::filesystem::space` nyní přijímá relativní cesty.
- `std::filesystem::path::lexically_relative` je již nerozumíte koncových lomítek, označení [LWG 3096](https://cplusplus.github.io/LWG/issue3096).
- Pracoval kolem `CreateSymbolicLinkW` odmítnutí cesty s lomítkem se v `std::filesystem::create_symlink`.
- Pracoval kolem režimu odstranění POSIX `delete` fungovat existující na Windows 10 LTSB 1609, ale nejsou ve skutečnosti jsou schopny odstraňování souborů.
- `std::boyer_moore_searcher` a `std::boyer_moore_horspool_searcher`je kopírovací konstruktory a operátory přiřazení kopie teď skutečně zkopírujte věci.

### <a name="parallel-algorithms-on-windows-8-and-later"></a>Paralelní algoritmy ve Windows 8 a novějších verzích

Knihovna paralelních algoritmů nyní správně používá skutečné `WaitOnAddress` řady ve Windows 8 a novějších verzích, ne vždy používat Windows 7 a starší falešné.

### <a name="stdsystemcategorymessage-whitespace"></a>std::system_category::message() whitespace

`std::system_category::message()` Nyní ořízne koncové mezery z hodnoty vrácené zprávy.

### <a name="stdlinearcongruentialengine-divide-by-zero"></a>std::linear_congruential_engine dělení nulou

Některé podmínky, které by mohly způsobit `std::linear_congruential_engine` k aktivaci jsme opravili dělení hodnotou 0.

### <a name="fixes-for-iterator-unwrapping"></a>Opravy pro rozbalení iterátoru

Iterátor rozbalení strojů, která byla vystavena nejprve pro integraci uživatele programátora ve Visual Studio 2017 15.8 (jak je popsáno v https://devblogs.microsoft.com/cppblog/stl-features-and-fixes-in-vs-2017-15-8/ ) už rozbalí iterátory odvozený od iterátorů standardní knihovny. Například uživatel, který je odvozen od `std::vector<int>::iterator` a pokusí se nyní přizpůsobit chování získá jejich vlastní chování při volání metody algoritmů standardní knihovny, spíše než chování ukazatel.
Funkce rezervy Neseřazený kontejneru teď skutečně rezervuje pro N prvků, jak je popsáno v [LWG 2156](https://cplusplus.github.io/LWG/issue2156).

### <a name="time-handling"></a>Doba zpracování

- Dříve, některé časové hodnoty, které byly předány do knihovny concurrency přetečení, například `condition_variable::wait_for(seconds::max())`. Tyto přetečení opravená, změnilo chování zdánlivě náhodné cyklu 29 dnů (když uint32_t milisekund přijal základní rozhraní API systému Win32 došlo k přetečení).

- <ctime> Záhlaví nyní správně deklaruje timespec a timespec_get v oboru názvů std kromě deklarace v globálním oboru názvů.

### <a name="various-fixes-for-containers"></a>Různé opravy pro kontejnery

- Mnoho funkce standardní knihovny interní kontejneru byly provedeny privátní pro vylepšení prostředí IntelliSense. Další opravy označte členy jako soukromého se očekává v dalších verzích MSVC.

- Problémy správnosti bezpečnost výjimek, ve které jako jsou kontejnery založené na uzlu `list`, `map`, a `unordered_map` by dojít k poškození jsme vyřešili. Během `propagate_on_container_copy_assignment` nebo `propagate_on_container_move_assignment` operace opětovného přiřazení jsme by zdarma kontejneru ověřovací uzel s původní allocator, proveďte přiřazení POCCA/POCMA přes staré přidělování a pak zkuste získat ověřovací uzel z nové alokátoru. Pokud toto přidělení se nezdařilo, kontejneru je poškozený a nelze dokonce zničit, jako vlastní že ověřovací uzel je neutrální pevné datové struktury. Tato chyba byla opravena přiřadit nový ověřovací uzel z alokátoru zdrojového kontejneru před zničení stávající ověřovací uzel.

- Kontejnery jsou opravená k vždy kopírování a přesun/prohození alokátorů podle `propagate_on_container_copy_assignment`, `propagate_on_container_move_assignment`, a `propagate_on_container_swap`, dokonce i pro deklarované alokátorů `is_always_equal`.

- Přidat přetížení pro kontejner sloučení a extrahovat členské funkce, které přijímají rvalue kontejnerů na [P0083 "Spojení map a sad"](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf)

### <a name="stdbasicistreamread-processing-of-rn--n"></a>zpracování std::basic_istream::Read \r\n = > \n

`std::basic_istream::read` byl nastaven na nelze zapsat do částí poskytnutá vyrovnávací paměť dočasně jako součást \r\n = > \n zpracování. Díky tomu si některé z výhod výkonu, získané v aplikaci Visual Studio 2017 15.8 pro čtení, které jsou větší než 4 kB, ale vylepšení efektivity od vyhnout 3 virtuální volání za znak jsou stále k dispozici.

### <a name="stdbitset-constructor"></a>std::bitset konstruktor

`std::bitset`pro konstruktor už načte ty a program je zaměřen v obráceném pořadí pro velké bitsets.

### <a name="stdpairoperator-regression"></a>std::Pair::Operator = regrese

Oprava Regrese v `std::pair`uživatele operátor přiřazení zavedená, při implementaci [. LWG 2729 "chybí SFINAE na std::pair::operator =";](https://cplusplus.github.io/LWG/issue2729). Nyní správně přijímá lze převést na typ typy `std::pair` znovu.

### <a name="non-deduced-contexts-for-addconstt"></a>Odvodit jiné kontexty pro add_const_t

Je opravená chyba, dílčí typ vlastnosti, kde `add_const_t` a související funkce jsou by měl být kontext odvodit. Jinými slovy `add_const_t` by měl být alias pro `typename add_const<T>::type`, nikoli `const T`.

## <a name="see-also"></a>Viz také:

[Co je nového ve Visual Studio 2019](../what-s-new-for-visual-cpp-in-visual-studio.md)