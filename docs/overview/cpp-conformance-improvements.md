---
title: Vylepšení shody C++
ms.date: 06/14/2019
description: Microsoft C++ v sadě Visual Studio probíhá směrem k plný soulad se standardem 20 jazyka C++.
ms.technology: cpp-language
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 1652c7ab9a48de65b32123b34c3231a0b06a410a
ms.sourcegitcommit: 0ad35b26e405bbde17dc0bd0141e72f78f0a38fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2019
ms.locfileid: "67194767"
---
# <a name="c-conformance-improvements-in-visual-studio"></a>Vylepšení shody C++ se sadou Visual Studio

Microsoft C++ díky vylepšení a opravy chyb v každé verzi. Tento článek uvádí vylepšení podle hlavní verze, pak podle verze. Také uvádí hlavní opravy chyb podle verze. Chcete-li přejít přímo na změny na konkrétní verzi, použijte **v tomto článku** seznamu.

::: moniker range=">=vs-2019"

## <a name="improvements_160"></a> Vylepšení v aplikaci Visual Studio RTW 2019 (verze 16.0)

Visual Studio 2019 RTW obsahuje následující vylepšení, oprav chyb a změny chování v Microsoftu C++ kompilátor (MSVC).

**Poznámka:** 20 funkce c ++ bude k dispozici v `/std:c++latest` režimu až do dokončení provádění 20 C ++ pro kompilátor a technologie IntelliSense. V tu chvíli `/std:c++20` režim kompilátoru se bude zavádět.

### <a name="improved-modules-support-for-templates-and-error-detection"></a>Moduly Vylepšená podpora pro šablony a detekce chyb

Moduly jsou nyní oficiálně v C ++ 20 standard. Vylepšená podpora byl přidán v sadě Visual Studio 2017 verze 15.9. Další informace najdete v tématu [lepší podporu a Chyba zjišťování šablony v moduly C++ s MSVC 2017 verzi 15.9](https://devblogs.microsoft.com/cppblog/better-template-support-and-error-detection-in-c-modules-with-msvc-2017-version-15-9/).

### <a name="modified-specification-of-aggregate-type"></a>Změny specifikace požadovaný typ agregace

Specifikace agregační typ se změnil v C ++ 20 (viz [zakázat agregace s uživatelem deklarované konstruktory](https://wg21.link/p1008r1)). V aplikaci Visual Studio 2019 pod `/std:c++latest`, třída s atributem žádné uživatelem deklarovaným konstruktorem (například deklarován včetně konstruktor `= default` nebo `= delete`) není agregační. Předtím jenom uživatelem zadané konstruktory by vyřadit třídy z se agregace. Tato změna vloží další omezení na tom, jak lze inicializovat tyto typy.

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

### <a name="partial-support-for-operator-"></a>Částečně se podporuje `operator <=>`

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

Aby nedošlo k chybám, vložte mezeru v problematický řádek před posledním ostré závorky: `U<&S::operator<= > u;`.

### <a name="references-to-types-with-mismatched-cv-qualifiers"></a>Odkazy na typy s neodpovídající kvalifikátory cv

Dříve MSVC povoleno přímé vazby odkazu z typu s neodpovídající kvalifikátory cv níže nejvyšší úrovně. Tato vazba umožňuje úpravy údajně const dat, na které odkazuje odkaz. Kompilátor nyní vytvoří dočasný, jak vyžaduje standard. V sadě Visual Studio 2017 následující kód zkompiluje bez upozornění. V aplikaci Visual Studio 2019, kompilátor vyvolá *upozornění C4172: \<func: č. 1 "?PData@X @@QBEABQBXXZ"> vrací adresu lokální proměnné nebo dočasné*.

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

Argument `reinterpret_cast` není jeden z kontextu, ve kterých je povolená adresa přetíženou funkci. Následující kód se zkompiluje bez chyb v sadě Visual Studio 2017, ale v aplikaci Visual Studio 2019 vyvolá *C2440: nelze převést z "přetížené funkce" na "fp"* :

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

V C ++ 14 typy uzávěru lambda nejsou literály. Primární důsledkem tohoto pravidla je, že výraz lambda nemůže být přiřazeno k `constexpr` proměnné. Následující kód se zkompiluje bez chyb v sadě Visual Studio 2017, ale v aplikaci Visual Studio 2019 vyvolá *C2127: "l": Neplatná inicializace entity 'constexpr' se nekonstantní výraz*:

```cpp
int main()
{
    constexpr auto l = [] {}; // C2127 in VS2019
}
```

Aby se zabránilo chybě, buď odeberte `constexpr` kvalifikátor, jinak změnit režim přizpůsobení na `/std:c++17`.

### <a name="stdcreatedirectory-failure-codes"></a>`std::create_directory` Kód selhání

Implementovat [P1164](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1164r1.pdf) z C ++ 20 nepodmíněně. Tím se změní `std::create_directory` ke kontrole, zda cíl byl již adresář při selhání. Dříve byly všechny chyby typu ERROR_ALREADY_EXISTS převedena na úspěch ale – adresář not vytvořené kódy.

### `operator<<(std::ostream, nullptr_t)`

Za [LWG 2221](https://cplusplus.github.io/LWG/issue2221)přidali `operator<<(std::ostream, nullptr_t)` pro zápis nullptrs datových proudů.

### <a name="additional-parallel-algorithms"></a>Další paralelní algoritmy

Nové paralelní verze `is_sorted`, `is_sorted_until`, `is_partitioned`, `set_difference`, `set_intersection`, `is_heap`, a `is_heap_until`.

### <a name="atomic-initialization"></a>Atomic inicializace

[P0883 "řešení atomic inicializace"](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0883r1.pdf) změny `std::atomic` hodnota inicializace omezením T spíše než výchozí-jeho inicializaci. Oprava zapnutý, při použití Clang/LLVM pomocí standardní knihovny Microsoft. Pro Microsoft je aktuálně zakázaný C++ kompilátoru jako alternativní řešení pro chyby v `constexpr` zpracování.

### <a name="removecvref-and-removecvreft"></a>`remove_cvref` a `remove_cvref_t`

Implementováno `remove_cvref` a `remove_cvref_t` zadejte vlastnosti z [P0550](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0550r2.pdf). Tím odpadne odkaz ness a cv kvalifikace z typu bez Slábnoucí funkce a pole ukazatelů (na rozdíl od `std::decay` a `std::decay_t`).

### <a name="feature-test-macros"></a>Makra testu funkcí

[P0941R2 – makra testu funkcí](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0941r2.html) je kompletní s podporou `__has_cpp_attribute`. Makra testu funkcí jsou podporovány ve všech režimech standard.

### <a name="prohibit-aggregates-with-user-declared-constructors"></a>Zakázat agregace s uživatelem deklarované konstruktory

[C ++ 20 P1008R1 – zákaz agregace s uživatelem deklarované konstruktory](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p1008r1.pdf) je dokončena.

## <a name="improvements_161"></a> Vylepšení v aplikaci Visual Studio 2019 verze 16.1

### <a name="char8t"></a>char8_t

[P0482r6](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0482r6.html). C ++ 20 přidá nový typ znaku, který se používá k reprezentování jednotkami kódu kódování UTF-8. `u8` textové literály v C ++ 20 mít typ `const char8_t[N]` místo `const char[N]`, která dříve byla případu. Podobné změny byly navrženy pro jazyk C standard v [N2231](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2231.htm). Návrhy pro `char8_t` nápravy zpětné kompatibility jsou uvedeny v [P1423r0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1423r0.html). Microsoft C++ kompilátor přidává podporu pro `char8_t` v aplikaci Visual Studio 2019 verze 16.1 při zadávání **/Zc:char8_t** – možnost kompilátoru. V budoucnu se bude podporovat s [/std: c ++ nejnovější](../build/reference/std-specify-language-standard-version.md), která se vrátí zpátky na C ++ 17 chování prostřednictvím **/Zc:char8_t-** . Kompilátor zaměstnance EDG, která je základem technologie IntelliSense zatím nepodporuje, takže uvidíte detekováno falešné chyby pouze technologie IntelliSense, které nebudou mít vliv na skutečné kompilace.

#### <a name="example"></a>Příklad

```cpp
const char* s = u8"Hello"; // C++17
const char8_t* s = u8"Hello"; // C++20
```

### <a name="stdtypeidentity-metafunction-and-stdidentity-function-object"></a>objekt std::type_identity metafunkcí a std::identity – funkce

[P0887R1 type_identity](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0887r1.pdf). Zastaralá `std::identity` rozšíření pro třídu šablony má byl odebrán a nahrazen parametrem 20 C ++ `std::type_identity` metafunkcí a `std::identity` objektu funkce. Obě jsou k dispozici pouze v rámci [/std: c ++ nejnovější](../build/reference/std-specify-language-standard-version.md).

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

Nový procesor lambda umožňuje některé syntaktické kontroly režim přizpůsobení v obecné výrazy lambda v části [/std: c ++ nejnovější](../build/reference/std-specify-language-standard-version.md) nebo v jiné jazykové režimu s **/ experimentální: newLambdaProcessor**.

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

### <a name="new-and-updated-standard-library-functions-c20"></a>Funkce nové a aktualizované standardní knihovny (C ++ 20)

- `starts_with()` a `ends_with()` pro `basic_string` a `basic_string_view`.
- `contains()` pro asociativní kontejnery.
- `remove()`, `remove_if()` a `unique()` pro `list` a `forward_list` teď vrací `size_type`.
- `shift_left()` a `shift_right()` přidán do \<algoritmus >.

## <a name="bug-fixes-and-behavior-changes-in-visual-studio-2019"></a>Opravy chyb a změny chování v aplikaci Visual Studio 2019

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

Chyba byla zavedena v sadě Visual Studio 2017, která způsobila kompilátor tiše ignorovat chyby a vygenerovat žádný kód pro neplatné volání += a-= pod `/clr` nebo `/ZW`. Následující kód se zkompiluje bez chyb v sadě Visual Studio 2017, ale v aplikaci Visual Studio 2019 správně vyvolá *chyba C2845: "System::String ^': aritmetika ukazatele není povolené pro tento typ*:

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

MSVC mívali výkon upozornění C4800 o implicitní převod na `bool`. Je příliš Rušený. a nemohlo být potlačeno, vedoucí nám odebrat v sadě Visual Studio 2017. Nicméně přes životního cyklu sady Visual Studio 2017 nám dává spoustu zpětné vazby na užitečné případy, které se řešení. Jsme vrácení Visual Studio 2019 pečlivě míru C4800, spolu s vysvětlující C4165. Obě tato upozornění jde snadno potlačit s buď explicitní přetypování, nebo porovnání 0 příslušného typu. C4800 se o varování mimo výchozí úroveň 4 a C4165 se o varování mimo výchozí úroveň 3. Obě jsou zjistitelné pomocí `/Wall` – možnost kompilátoru.

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
void example()
{
    struct A
        {
            int boo(); // warning C4822
        };
}
```

### <a name="function-template-bodies-containing-constexpr-if-statements"></a>Funkce šablony těla obsahující constexpr, pokud příkazy

Těla funkcí šablony obsahující `if constexpr` příkazy mají některé `/permissive-` povoleny kontroly související s analýza kódu. Například v sadě Visual Studio 2017 vytváří následující kód jazyka C*7510: 'Type': použití názvu závislého typu musí být předponou 'typename'* pouze tehdy, pokud `/permissive-` není nastaven. V aplikaci Visual Studio 2019 stejné vyvolává chyby kódu i v případě `/permissive-` je nastavena možnost:

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

### <a name="inline-assembly-code-isnt-supported-in-a-lambda-expression"></a>Vložený kód sestavení není podporován ve výrazu lambda

Vizuál C++ týmu byl nedávno informováni o bezpečnostní riziko, ve kterém se použití inline assembleru v rámci výrazu lambda mohlo způsobit poškození `ebp` (zpáteční adresu register) za běhu. Se zlými úmysly může potenciálně využít tento scénář. Vzhledem k povaze problému, skutečnost, že tento vložený assembler je jenom na podporovaných x86 a špatné interakce mezi vložený assembler a zbytek kompilátor, nejbezpečnější řešení tohoto problému bylo zakázat vložený assembler v rámci výrazu lambda.

Pouze použití inline assembleru v rámci výrazu lambda, která jsme našli "v reálném světě" bylo k zachycení zpáteční adresu. V tomto scénáři můžete zachytit zpáteční adresa pro všechny platformy jednoduše tak, že pomocí vnitřní kompilátor `_ReturnAddress()`.

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

### <a name="iterator-debugging-and-stdmoveiterator"></a>Iterační ladění a `std::move_iterator`

Iterační ladění funkce má byla museli k rozbalení správně `std::move_iterator`. Například `std::copy(std::move_iterator<std::vector<int>::iterator>, std::move_iterator<std::vector<int>::iterator>, int*)` teď můžete zapojit `memcpy` rychlou cestu.

### <a name="fixes-for-xkeycheckh-keyword-enforcement"></a>Opravy \<xkeycheck.h > Vynucení – klíčové slovo

Standardní knihovna – makro, nahraďte vynucení – klíčové slovo \<xkeycheck.h > byl nastaven na generování skutečný problém – klíčové slovo zjištěno místo obecná zpráva. Také podporuje C ++ 20 klíčová slova a zabraňuje, přičemž technologie IntelliSense do o tom, že náhodné klíčová slova jsou makra.

### <a name="allocator-types-no-longer-deprecated"></a>Typy přidělování již zastaralé.

`std::allocator<void>`, `std::allocator::size_type`, a `std::allocator::difference_type` jsou už zastaralé.

### <a name="correct-warning-for-narrowing-string-conversions"></a>Opravit upozornění pro zužující převody řetězců

Nesprávné `static_cast` není volán podle standardu omylem Potlačené C4244 zúžení upozornění byla odebrána z `std::string`. Pokus o volání `std::string::string(const wchar_t*, const wchar_t*)` bude nyní správně generovat *C4244 "zúžení wchar_t do typu char."*

### <a name="various-filesystem-correctness-fixes"></a>Různé \<filesystem > řeší správnost

- Oprava `std::filesystem::last_write_time` selhání při pokusu o změnu adresáře vaší poslední čas zápisu.
- `std::filesystem::directory_entry` Konstruktoru nyní ukládá neúspěšných výsledků namísto vyvolání výjimky, pokud je zadán neexistující cílovou cestu.
- `std::filesystem::create_directory` Verze 2 parametr byl změněn na volání verze 1 parametr, jako základní `CreateDirectoryExW` byste použili funkci `copy_symlink` při `existing_p` byl symlink.
- `std::filesystem::directory_iterator` už selže při nalezení symlink nefunkční.
- `std::filesystem::space` nyní přijímá relativní cesty.
- `std::filesystem::path::lexically_relative` je již nerozumíte koncových lomítek, označení [LWG 3096](https://cplusplus.github.io/LWG/issue3096).
- Pracoval kolem `CreateSymbolicLinkW` odmítnutí cesty s lomítkem se v `std::filesystem::create_symlink`.
- Pracoval kolem režimu odstranění POSIX `delete` fungovat existující na Windows 10 LTSB 1609, ale nejsou ve skutečnosti nebudou moct odstraňovat soubory.
- `std::boyer_moore_searcher` a `std::boyer_moore_horspool_searcher`je kopírovací konstruktory a operátory přiřazení kopie teď skutečně zkopírujte věci.

### <a name="parallel-algorithms-on-windows-8-and-later"></a>Paralelní algoritmy ve Windows 8 a novějších verzích

Knihovna paralelních algoritmů nyní správně používá skutečné `WaitOnAddress` řady ve Windows 8 a novějších verzích, ne vždy používat Windows 7 a starší falešné.

### <a name="stdsystemcategorymessage-whitespace"></a>`std::system_category::message()` Prázdné znaky

`std::system_category::message()` Nyní ořízne koncové mezery z hodnoty vrácené zprávy.

### <a name="stdlinearcongruentialengine-divide-by-zero"></a>`std::linear_congruential_engine` dělení nulou

Některé podmínky, které by mohly způsobit `std::linear_congruential_engine` k aktivaci jsme opravili dělení hodnotou 0.

### <a name="fixes-for-iterator-unwrapping"></a>Opravy pro rozbalení iterátoru

Iterátor rozbalení strojních zařízení, která byla vystavena nejprve pro integraci uživatele programátora ve Visual Studio 2017 15.8, jak je popsáno v C++ článek blogu týmu [STL funkce a opravy ve VS 2017 15.8](https://devblogs.microsoft.com/cppblog/stl-features-and-fixes-in-vs-2017-15-8/), už rozbalí iterátorů odvozený od iterátorů standardní knihovny. Například uživatel, který je odvozen od `std::vector<int>::iterator` a pokusí se nyní přizpůsobit chování získá jejich vlastní chování při volání metody algoritmů standardní knihovny, spíše než chování ukazatel.

Neseřazený kontejneru `reserve` funkce nyní skutečně rezervy pro N prvků, jak je popsáno v [LWG 2156](https://cplusplus.github.io/LWG/issue2156).

### <a name="time-handling"></a>Doba zpracování

- Dříve, některé časové hodnoty, které byly předány do knihovny concurrency přetečení, například `condition_variable::wait_for(seconds::max())`. Teď pevně daná, a přetečení změnilo chování zdánlivě náhodné cyklu 29 dnů (když uint32_t milisekund přijal základní rozhraní API systému Win32 došlo k přetečení).

- <ctime> Záhlaví nyní správně deklaruje `timespec` a `timespec_get` v oboru názvů `std` kromě deklarace v globálním oboru názvů.

### <a name="various-fixes-for-containers"></a>Různé opravy pro kontejnery

- Mnoho funkce standardní knihovny interní kontejneru byly provedeny privátní pro vylepšení prostředí IntelliSense. Další opravy označte členy jako soukromého se očekává v pozdějších verzích MSVC.

- Problémy správnosti bezpečnost výjimek, ve které jako jsou kontejnery založené na uzlu `list`, `map`, a `unordered_map` by dojít k poškození jsme vyřešili. Během `propagate_on_container_copy_assignment` nebo `propagate_on_container_move_assignment` operace opětovného přiřazení jsme by zdarma kontejneru ověřovací uzel s původní allocator, proveďte přiřazení POCCA/POCMA přes staré přidělování a pak zkuste získat ověřovací uzel z nové alokátoru. Pokud toto přidělení se nezdařilo, kontejneru byl poškozen a nelze dokonce zničit, jako vlastní že ověřovací uzel je neutrální pevné datové struktury. Tento kód byl opraven přiřadit nový ověřovací uzel z alokátoru zdrojového kontejneru před zničení stávající ověřovací uzel.

- Kontejnery jsou opravená k vždy kopírování a přesun/prohození alokátorů podle `propagate_on_container_copy_assignment`, `propagate_on_container_move_assignment`, a `propagate_on_container_swap`, dokonce i pro deklarované alokátorů `is_always_equal`.

- Přidat přetížení pro kontejner sloučení a extrahovat členské funkce, které přijímají rvalue kontejnerů na [P0083 "Spojení map a sad"](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf)

### <a name="stdbasicistreamread-processing-of-rn--n"></a>`std::basic_istream::read` zpracování \\r\\n = > \\n

`std::basic_istream::read` byla opravena nelze zapisovat do částí poskytnutá vyrovnávací paměť dočasně jako součást \\r\\n = > \\n zpracování. Tato změna umožňuje některé výhody výkonu, získané v aplikaci Visual Studio 2017 15.8 pro čtení, které jsou větší než 4 kB. Vylepšení efektivity od vyhnout tři virtuální volání na znak jsou však stále k dispozici.

### <a name="stdbitset-constructor"></a>`std::bitset` Konstruktor

`std::bitset` Konstruktor už načte ty a program je zaměřen v obráceném pořadí pro velké bitsets.

### <a name="stdpairoperator-regression"></a>`std::pair::operator=` Regrese

Oprava Regrese v `std::pair`uživatele operátor přiřazení zavedená, při implementaci [. LWG 2729 "chybí SFINAE na std::pair::operator =";](https://cplusplus.github.io/LWG/issue2729). Nyní správně přijímá lze převést na typ typy `std::pair` znovu.

### <a name="non-deduced-contexts-for-addconstt"></a>Odvodit jiné kontexty pro `add_const_t`

Je opravená chyba, dílčí typ vlastnosti, kde `add_const_t` a související funkce jsou by měl být kontext odvodit. Jinými slovy `add_const_t` by měl být alias pro `typename add_const<T>::type`, nikoli `const T`.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="improvements_150"></a> Vylepšení v aplikaci Visual Studio 2017 ve verzi RTW (verze 15.0)

Podporu pro generalizovaný `constexpr` a nestatický datový člen inicializace (NSDMI) pro agregace, Microsoft C++ kompilátoru v sadě Visual Studio 2017 je teď kompletní pro funkce přidané C ++ 14 standard. Nicméně v kompilátoru stále chybí několik funkcí z C ++ 11 a C ++ 98 standardy. Zobrazit [shoda jazyka Visual C++](../visual-cpp-language-conformance.md) pro tabulku, která se zobrazuje aktuální stav kompilátoru.

### <a name="c11-expression-sfinae-support-in-more-libraries"></a>C++11: Podpora sfinae u výrazů v další knihovny

Kompilátor neustále zlepšuje podporu pro výraz SFINAE, která je potřebná pro odvození argumentu šablony a nahrazení kde `decltype` a `constexpr` výrazy se může zobrazit jako parametry šablony. Další informace najdete v tématu [vylepšení sfinae u výrazů v sadě Visual Studio 2017 RC](https://blogs.msdn.microsoft.com/vcblog/2016/06/07/expression-sfinae-improvements-in-vs-2015-update-3).

### <a name="c14-nsdmi-for-aggregates"></a>C++14: NSDMI pro agregace

Agregace je pole nebo třída s atributem žádný uživatelem zadaný konstruktor, žádné soukromé nebo chráněné nestatické datové členy, žádné základní třídy a žádné virtuální funkce. Od verze C ++ 14 agregací mohou obsahovat inicializátory členů. Další informace najdete v tématu [inicializátory členů a agregace](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3605.html).

### <a name="c14-extended-constexpr"></a>C++14: Rozšířené `constexpr`

Výrazy deklarován jako `constexpr` nyní mohou obsahovat některé typy deklarací, pokud a přepněte příkazy, příkazy cyklů a mutace objektů, jehož doba života začal v rámci výrazu vyhodnocení constexpr. Také již neplatí požadavek, který `constexpr` nestatická členská funkce musí být implicitně `const`. Další informace najdete v tématu [uvolnit omezení ve funkcích constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3652.html).

### <a name="c17-terse-staticassert"></a>C++17: Stručný `static_assert`

Parametr zpráva `static_assert` je volitelný. Další informace najdete v tématu [rozšíření static_assert, v2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3928.pdf).

### <a name="c17-fallthrough-attribute"></a>C ++ 17: `[[fallthrough]]` atribut

V **/std: c ++ 17** režimu, `[[fallthrough]]` atribut lze použít v kontextu příkazů přepínače jako pomocný parametr kompilátoru, že je určena propuštěním chování. Tento atribut brání vydávání upozornění v těchto případech kompilátor. Další informace najdete v tématu [formulaci pro \[ \[fallthrough\] \] atribut](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0188r0.pdf).

### <a name="generalized-range-based-for-loops"></a>Zobecněný, na základě rozsahu smyček for

Založený na rozsahu pro smyčky už nevyžadují, který `begin()` a `end()` vrátí objekty stejného typu. Tato změna umožňuje `end()` vrátit sentinel jako rozsahy v [rozsah v3](https://github.com/ericniebler/range-v3) a dokončit, ale not-ještě nejsme u konce publikované společností technické specifikace rozsahy. Další informace najdete v tématu [zobecňuje Range-Based pro smyčky](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html).

## <a name="improvements_153"></a> Vylepšení v sadě Visual Studio 2017 verze 15.3

### <a name="constexpr-lambdas"></a>constexpr lambdas

Může se teď dá výrazy lambda v konstantních výrazech. Další informace najdete v tématu [constexpr výrazy lambda v jazyce C++](../cpp/lambda-expressions-constexpr.md).

### <a name="if-constexpr-in-function-templates"></a>`if constexpr` v rámci šablony funkce

Šablona funkce může obsahovat `if constexpr` příkazy Povolit větvení v době kompilace. Další informace najdete v tématu [Pokud constexpr příkazy](../cpp/if-else-statement-cpp.md#if_constexpr).

### <a name="selection-statements-with-initializers"></a>Příkazy výběru s inicializátory

`if` Příkaz může zahrnovat inicializátoru, který představuje proměnnou v oboru bloku v rámci příkazu samotný. Další informace najdete v tématu [Pokud příkazy s inicializátorem](../cpp/if-else-statement-cpp.md#if_with_init).

### <a name="maybeunused-and-nodiscard-attributes"></a>`[[maybe_unused]]` a `[[nodiscard]]` atributy

Nový atribut `[[maybe_unused]]` vypne upozornění, když se nepoužívá entity. `[[nodiscard]]` Atribut vytvoří upozornění, pokud se zruší vrácenou hodnotu volání funkce. Další informace najdete v tématu [atributy v jazyce C++](../cpp/attributes.md).

### <a name="using-attribute-namespaces-without-repetition"></a>Použití atributu oboru názvů bez opakování

Novou syntaxi povolit pouze identifikátor jednoho oboru názvů v seznamu atributů. Další informace najdete v tématu [atributy v jazyce C++](../cpp/attributes.md).

### <a name="structured-bindings"></a>Strukturované vazby

Nyní je možné v jedné deklaraci k uložení hodnoty se jednotlivé názvy pro součásti, pokud je hodnota pole, `std::tuple` nebo `std::pair`, nebo má všechny veřejné nestatické datové členy. Další informace najdete v tématu [strukturovaných vazeb](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0144r0.pdf) a [vrácení více hodnot z funkce](../cpp/functions-cpp.md#multi_val).

### <a name="construction-rules-for-enum-class-values"></a>Vytváření pravidel pro `enum class` hodnoty

Nyní převod implicitní/bez zúžení z podkladový typ výčet s oborem pro výčet, pokud se žádný čítač zavádí jeho definici a zdroji pomocí syntaxe Inicializace seznamu. Další informace najdete v tématu [konstrukce pravidla pro výčet tříd hodnoty](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0138r2.pdf) a [výčty](../cpp/enumerations-cpp.md#no_enumerators).

### <a name="capturing-this-by-value"></a>Zachytávání `*this` podle hodnoty

`*this` Objektu ve výrazu lambda teď může být zachyceno hodnotou. Tato změna umožňuje scénáře, ve kterých je vyvolán výrazu lambda v paralelní a asynchronní operace, zejména na novějších architektury počítačů. Další informace najdete v tématu [zachycení Lambda \*tím, že jako hodnotu \[=,\*to\]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0018r3.html).

### <a name="removing-operator-for-bool"></a>Odebrání `operator++` pro `bool`

`operator++` už není podporovaná na `bool` typy. Další informace najdete v tématu [odebrat zastaralé operator++(bool)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0002r1.html).

### <a name="removing-deprecated-register-keyword"></a>Odebrat zastaralé `register` – klíčové slovo

`register` – Klíčové slovo, dříve zastaralé (a ignorovány kompilátorem), teď Odebereme z jazyka. Další informace najdete v tématu [odebrat zastaralé použití register – klíčové slovo](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0001r1.html).

## <a name="improvements_155"></a> Vylepšení v sadě Visual Studio 2017 verze 15.5

Funkce označené \[14] jsou k dispozici bezpodmínečně i při **/std: c ++ 14** režimu.

### <a name="new-compiler-switch-for-extern-constexpr"></a>Nový přepínač kompilátoru pro `extern constexpr`

V dřívějších verzích sady Visual Studio, kompilátor vždy přiřadil `constexpr` proměnné vnitřní propojení, i když byla označena jako proměnná `extern`. V sadě Visual Studio 2017 verze 15.5, nový přepínač kompilátoru [/Zc: externconstexpr](../build/reference/zc-externconstexpr.md), umožňuje správné chování vyhovující standardům. Další informace najdete v tématu [extern constexpr propojení](#extern_linkage).

### <a name="removing-dynamic-exception-specifications"></a>Odebrání specifikace dynamických výjimek

[P0003R5](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html) specifikace dynamických výjimek byla vyřazena jako zastaralá v C ++ 11. Tato funkce bude odebrána z C ++ 17, ale (nadále) zastaralé `throw()` specifikace zůstane výhradně jako aliasu pro `noexcept(true)`. Další informace najdete v tématu [odebrání specifikace dynamických výjimek a noexcept](#noexcept_removal).

### `not_fn()`

[P0005R4](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0005r4.html) `not_fn` je nahrazení `not1` a `not2`.

### <a name="rewording-enablesharedfromthis"></a>Přeformulování `enable_shared_from_this`

[P0033R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0033r1.html) `enable_shared_from_this` bylo přidáno v C ++ 11. Standardu C ++ 17 aktualizuje specifikace pro lepší zpracování některých krajní případy. [14]

### <a name="splicing-maps-and-sets"></a>Spojení map a sad

[P0083R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf) tato funkce umožňuje extrakce uzlů z asociativní kontejnery (to znamená `map`, `set`, `unordered_map`, `unordered_set`) který pak se dají upravit a vložit zpět do stejného kontejneru nebo jiné kontejner, který používá stejný typ uzlu. (Běžným případem použití je extrakce uzlu z `std::map`, změňte klíč a vložte.)

### <a name="deprecating-vestigial-library-parts"></a>Vyřazení zbytkových součástí knihovny

[P0174R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0174r2.html) řadu funkcí aplikace C++ standardní knihovna byla nahrazena novější funkce v průběhu let, jinak nebyly nalezeny není užitečné nebo problematické. Tyto funkce jsou oficiálně zastaralé v C ++ 17.

### <a name="removing-allocator-support-in-stdfunction"></a>Odebrání podpory pro allocator v `std::function`

[P0302R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0302r1.html) před C ++ 17, šablonu třídy `std::function` má několik konstruktorů, které mají argument allocator. Však byla problematický použití alokátory: v tomto kontextu a sémantika byly jasné. Odebrali jsme contructors problém.

### <a name="fixes-for-notfn"></a>Opravy `not_fn()`

[P0358R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0358r1.html) Nová formulace pro `std::not_fn` poskytuje podporu pro šíření kategorií hodnot při použití v vyvolání obálky.

### <a name="sharedptrt-sharedptrtn"></a>`shared_ptr<T[]>`, `shared_ptr<T[N]>`

[P0414R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0414r2.html) slučování `shared_ptr` změní z Library Fundamentals do C ++ 17. [14]

### <a name="fixing-sharedptr-for-arrays"></a>Oprava `shared_ptr` pro pole

[P0497R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0497r0.html) oprav shared_ptr – podpora pro pole. [14]

### <a name="clarifying-insertreturntype"></a>Bylo zcela zřejmé `insert_return_type`

[P0508R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0508r0.html) asociativní kontejnery s jedinečnými klíči a neseřazené kontejnery s jedinečnými klíči mají členské funkce `insert` , které vrací vnořený typ `insert_return_type`. Návratový typ je teď definovaný jako specializaci typu, který je parametrizované u iterátoru a NodeType kontejneru.

### <a name="inline-variables-for-the-standard-library"></a>Vložené proměnné pro standardní knihovnu

[P0607R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0607r0.html)

### <a name="annex-d-features-deprecated"></a>Příloha D zastaralé funkce

Příloha D standardu jazyka C++ obsahuje všechny funkce, které jsou zastaralé, včetně `shared_ptr::unique()`, `<codecvt>`, a `namespace std::tr1`. Když **/std: c ++ 17** je nastaven přepínač kompilátoru, téměř všechny funkce standardní knihovny v příloze D jsou označené jako zastaralé. Další informace najdete v tématu [funkce standardní knihovny v příloze D jsou označené jako zastaralé](#annex_d).

`std::tr2::sys` Obor názvů v `<experimental/filesystem>` nyní generuje upozornění na vyřazení v rámci **/std: c ++ 14** ve výchozím nastavení a teď Odebereme pod **/std: c ++ 17** ve výchozím nastavení.

Vylepšené dodržování standardu `<iostream>` zabráněním nestandardní rozšíření (explicitní specializace ve třídě).

Standardní knihovna teď používá variabilní šablony interně.

Aktualizovali jsme standardní knihovny v reakci na C ++ 17 kompilátoru změny, včetně přidání `noexcept` systému typů a odebrání specifikace dynamických výjimek.

## <a name="improvements_156"></a> Vylepšení v sadě Visual Studio 2017 verze 15.6

### <a name="c17-library-fundamentals-v1"></a>C ++ 17 Library Fundamentals V1

[P0220R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html) zahrnuje Library Fundamentals technické specifikace do standardu C ++ 17. Zahrnuje aktualizace \<experimentální/řazené kolekce členů >, \<experimentální a volitelné >, \<experimentální/funkční >, \<experimentální/any >, \<experimentální/string_view >, \<experimentální nebo paměti >, \<experimentální/memory_resource >, a \<experimentální/algoritmus >.

### <a name="c17-improving-class-template-argument-deduction-for-the-standard-library"></a>C++17: Zlepšení odvození argumentu šablony třídy pro standardní knihovnu

[P0739R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0739r0.html) přesunout `adopt_lock_t` na začátku seznamu parametrů pro `scoped_lock` umožňuje konzistentním použitím `scoped_lock`. Povolit `std::variant` konstruktor součástí řešení přetížení ve více případech umožňuje přiřazení kopie.

## <a name="improvements_157"></a> Vylepšení v sadě Visual Studio 2017 verze 15.7

### <a name="c17-rewording-inheriting-constructors"></a>C++17: Přeformulování zděděné konstruktory

[P0136R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0136r1.html) Určuje, že **pomocí** deklarace, který pojmenovává konstruktor nyní vytvoří odpovídající základní třídy konstruktory, které jsou viditelné pro inicializace odvozené třídy, namísto deklarování další odvozené konstruktor třídy. Tato přeformulování se mění z C ++ 14. V sadě Visual Studio 2017 verze 15.7 nebo novější, v **/std: c ++ 17** režimu, kód, který je platný v C ++ 14 a používá dědění konstruktorů jsou pravděpodobně neplatná nebo může mít různou sémantiku.

Následující příklad ukazuje C ++ 14 chování:

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

Následující příklad ukazuje **/std: c ++ 17** chování v aplikaci Visual Studio 15.7:

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

Další informace najdete v tématu [konstruktory](../cpp/constructors-cpp.md#inheriting_constructors).

### <a name="c17-extended-aggregate-initialization"></a>C++17: Rozšířené inicializace agregace

[P0017R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0017r1.html)

Pokud konstruktor základní třídy je neveřejné ale přístupná na odvozenou třídu, pak **/std: c ++ 17** režimu v sadě Visual Studio verze 15.7, kterou již nebudete používat prázdné závorky k inicializaci objektu odvozeného typu.

Následující příklad ukazuje chování C ++ 14 splňující podmínky:

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

V C ++ 17 `Derived` se teď považuje za typ agregace. To znamená, že inicializace `Base` přes privátní výchozí konstruktor se stane přímo, jako součást pravidla rozšířené agregační inicializace. Dříve `Base` soukromého konstruktoru byla volána prostřednictvím `Derived` konstruktor který úspěšně z důvodu deklarace typu friend.

Následující příklad ukazuje v sadě Visual Studio verze 15.7 v C ++ 17 chování **/std: c ++ 17** režimu:

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

### <a name="c17-declaring-non-type-template-parameters-with-auto"></a>C++17: Parametry šablony bez typu s automatickým deklarace

[P0127R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r2.html)

V **/std: c ++ 17** režimu, může kompilátor nově odvodit typ argumentu šablony bez typu, který je deklarován s **automaticky**:

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

Jeden tuto novou funkci se, že platný C ++ 14 kódu jsou pravděpodobně neplatná nebo může mít různou sémantiku. Některá přetížení, které byly dříve neplatné jsou například nyní platné. Následující příklad ukazuje C ++ 14 kód, který zkompiluje, protože volání `example(p)` je vázán na `example(void*);`. V sadě Visual Studio 2017 verze 15.7 v **/std: c ++ 17** režimu, `example` šablony funkce je nejlepší shodu.

```cpp
template <int N> struct A;
template <typename T, T N> int example(A<N>*) = delete;

void example(void *);

void sample(A<0> *p)
{
    example(p); // OK in C++14
}
```

Následující příklad ukazuje C ++ 17 kódu ve Visual Studio 15.7 v **/std: c ++ 17** režimu:

```cpp
template <int N> struct A;
template <typename T, T N> int example(A<N>*);

void example(void *);

void sample(A<0> *p)
{
    example(p); // C2280: 'int example<int,0>(A<0>*)': attempting to reference a deleted function
}
```

### <a name="c17-elementary-string-conversions-partial"></a>C++17: základní řetězec převody (částečná podpora)

[P0067R5](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0067r5.html) nízké úrovně, nezávislý na národním prostředí funkce pro převod mezi celá čísla a řetězce a mezi čísla s plovoucí desetinnou čárkou a řetězce.

### <a name="c20-avoiding-unnecessary-decay-partial"></a>C ++ 20: Jak se vyhnout zbytečným decay (částečné)

[P0777R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0777r1.pdf) přidá rozlišovat pojmu "decay" a, která jednoduše odebrání konstantu nebo kvalifikátory odkaz.  Nové vlastnosti typu `remove_reference_t` nahradí `decay_t` v některých kontextech. Podpora pro `remove_cvref_t` je implementován v aplikaci Visual Studio 2019.

### <a name="c17-parallel-algorithms"></a>C++17: Paralelní algoritmy

[P0024R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0024r2.html) The paralelismu TS je součástí standardu s malými změnami.

### <a name="c17-hypotx-y-z"></a>C++17: `hypot(x, y, z)`

[P0030R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0030r1.pdf) přidává tři nová přetížení `std::hypot`, pro typy **float**, **double**, a **long double**, z nichž každá má tři vstupní parametry.

### <a name="c17-filesystem"></a>C ++ 17: \<filesystem >

[P0218R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0218r1.html) přijme TS systému souborů do standardních s několik změn znění.

### <a name="c17-mathematical-special-functions"></a>C++17: speciální matematické funkce

[P0226R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html) přijme předchozí technických specifikací pro speciální matematické funkce do standardu \<cmath > záhlaví.

### <a name="c17-deduction-guides-for-the-standard-library"></a>C++17: Průvodce dedukcí pro standardní knihovnu

[P0433R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0433r2.html) aktualizace STL výhod C ++ 17 přijetí [P0091R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html), který přidává podporu pro odvození argumentu šablony třídy.

### <a name="c17-repairing-elementary-string-conversions"></a>C++17: Oprava základní řetězec převody

[P0682R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0682r1.html) přesunutí nové funkce pro převod základní řetězec z P0067R5 do nového záhlaví \<charconv > a dalších vylepšení, včetně změny zpracování chyb, které použijte `std::errc` místo `std::error_code`.

### <a name="c17-constexpr-for-chartraits-partial"></a>C ++ 17: `constexpr` pro `char_traits` (částečné)

[P0426R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0426r1.html) změny `std::traits_type` členské funkce `length`, `compare`, a `find` aby `std::string_view` použít v konstantních výrazech. (V sadě Visual Studio 2017 verze 15.6 podporovaná Clang/LLVM jenom pro. Ve verzi 15.7 Preview 2, podpora je téměř dokončení pro ClXX stejně.)

## <a name="improvements_159"></a> Vylepšení v sadě Visual Studio 2017 verze 15.9

### <a name="left-to-right-evaluation-order-for-operators-----and-"></a>Pořadí vyhodnocování zleva doprava pro operátory `->*`, `[]`, `>>`, a `<<`

Od verze C ++ 17, operandy operátory `->*`, `[]`, `>>`, a `<<` musí vyhodnocují v pořadí zleva doprava. Existují dva případy, ve kterých kompilátor nedokáže zaručit toto pořadí:

- Pokud jeden z výrazů operand je objekt, předán podle hodnoty nebo obsahuje objekt, předán podle hodnoty, nebo

- Při kompilaci pomocí **/CLR**, a jeden z operandů je pole objektu nebo k elementu pole.

Kompilátor vydá upozornění [C4866](https://docs.microsoft.com/cpp/error-messages/compiler-warnings/c4866?view=vs-2017) při nezaručuje vyhodnocování zleva doprava. Kompilátor generuje toto upozornění pouze tehdy, pokud **/std: c ++ 17** nebo vyšší není zadán, jak z těchto operátorů požadavek na pořadí zleva doprava byla zavedena v C ++ 17.

Pokud chcete vyřešit toto varování, nejprve vezměte v úvahu, jestli je nezbytné, například při vyhodnocování operandů může vrátit vedlejší účinky závislé na pořadí vyhodnocení operandů zleva doprava. V mnoha případech pořadí, ve kterém jsou vyhodnoceny operandy nemá žádný pozorovatelných vliv. Pokud musí pořadí vyhodnocování zleva doprava, zvažte, zda lze předat operandy podle odkazu const místo. Tato změna eliminuje upozornění v následujícím příkladu kódu:

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

## <a name="update_150"></a> Opravy chyb v aplikaci Visual Studio 2017 ve verzi RTW (verze 15.0)

### <a name="copy-list-initialization"></a>Inicializace kopírování seznamu

Visual Studio 2017 správně vyvolává chyby při kompilaci vztahující se k vytvoření objektu pomocí inicializační seznamy, které nebyly byla zachycena v sadě Visual Studio 2015 a může způsobit selhání nebo nedefinované chování za běhu. Podle N4594 13.3.1.7p1 v kopírování Inicializace seznamu kompilátor je potřeba vzít v úvahu explicitní konstruktor pro řešení přetížení, ale musí vyvolat chybu, pokud je zvolená tohoto konkrétního přetížení.

Následující dva příklady zkompilovat ve Visual Studiu 2015 ale není v sadě Visual Studio 2017.

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

Chcete-li opravit chybu, použijte přímé inicializace:

```cpp
A a1{ 1 };
const A& a2{ 1 };
```

V sadě Visual Studio 2015 kompilátor nesprávně zpracovávají Inicializace kopírování seznamu v stejným způsobem jako regulární Inicializace kopírování; za to, převod pouze konstruktory pro řešení přetížení. V následujícím příkladu vybere Visual Studio 2015 MyInt(23), ale Visual Studio 2017 správně vyvolá chybu.

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

Tento příklad je podobný předchozímu, ale vyvolává různé chyby. Úspěšné v sadě Visual Studio 2015 a v sadě Visual Studio 2017 s C2668 se nezdaří.

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

### <a name="deprecated-typedefs"></a>Nepoužívané – definice TypeDef

Visual Studio 2017 teď vydá správné upozornění pro zastaralé definice typedefs jazyka, které jsou deklarovány ve třídě nebo struktuře. Následující příklad zkompiluje bez upozornění v sadě Visual Studio 2015, ale vytváří C4996 v sadě Visual Studio 2017.

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

### `constexpr`

Visual Studio 2017 správně vyvolá chybu, pokud operand na levé straně podmíněně vyhodnocování operace není platná v kontextu constexpr. Následující kód se zkompiluje ve Visual Studiu 2015 ale není v sadě Visual Studio 2017 (C3615 v konstantním výrazu nemůže způsobit funkce constexpr 'f'):

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

Chcete-li chybu opravit, buď deklarovat `array::size()` fungovat jako `constexpr` nebo odebrat `constexpr` kvalifikátor z `f`.

### <a name="class-types-passed-to-variadic-functions"></a>Typy tříd, které jsou předány variadické funkce

V sadě Visual Studio 2017 musí být třídy nebo struktury, které jsou předány variadické funkce, jako je například printf snadno kopírovatelná. Při předávání těchto objektů, kompilátor jednoduše vytvoří bitové kopie a nebude volat konstruktor nebo destruktor.

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

Chcete-li opravit chybu, můžete volat členské funkce, která vrací triviálně kopírovatelné typu

```cpp
    std::atomic<int> i(0);
    printf("%i\n", i.load());
```

Jinak použijte statické přetypování převést objekt před jeho odesláním:

```cpp
    struct S {/* as before */} s(0);
    printf("%i\n", static_cast<int>(s))
```

Pro řetězce vytvořené a spravují s použitím CString poskytnutého `operator LPCTSTR()` má použít pro přetypování objektu CString na ukazatel C očekává formátovacím řetězcem.

```cpp
CString str1;
CString str2 = _T("hello!");
str1.Format(_T("%s"), static_cast<LPCTSTR>(str2));
```

### <a name="cv-qualifiers-in-class-construction"></a>Kvalifikátory CV v konstrukci třídy

V sadě Visual Studio 2015 kompilátor někdy nesprávně ignoruje kvalifikátor cv-qualifier při generování objektu třídy prostřednictvím volání konstruktoru. Tento problém může způsobit selhání nebo neočekávané chování za běhu. Následující příklad zkompiluje ve Visual Studiu 2015 ale vyvolá kompilátor chybu v sadě Visual Studio 2017:

```cpp
struct S
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```

Chcete-li chybu opravit, deklarujte `operator int()` jako `const`.

### <a name="access-checking-on-qualified-names-in-templates"></a>Kontroluje se kvalifikované názvy v šablonách přístup

Předchozí verze kompilátoru nekontrolovaly se přístup k kvalifikované názvy v některých kontextech šablony. Tento problém může narušovat očekávané chování SFINAE, kde se očekává selhat z důvodu inaccessibility název nahrazení. To může potenciálně způsobit selhání nebo neočekávané chování za běhu vzhledem k tomu, že kompilátor volá se nesprávně nesprávné přetížení operátoru. V sadě Visual Studio 2017 se vyvolá chybu kompilátoru. Konkrétní chyba se může lišit, ale obvykle je to "C2672 žádná odpovídající Přetížená funkce Najít". Následující kód zkompiluje ve Visual Studiu 2015 ale vyvolá chybu v sadě Visual Studio 2017:

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

V sadě Visual Studio 2015 a starší kompilátor není Diagnostika chybějící seznamy argumentů šablony šablony zobrazené v seznamu parametrů šablony, například jako součást výchozí argument šablony nebo parametr šablony bez typu. Tento problém může způsobit neočekávané chování, včetně kompilátoru selhání nebo neočekávané chování za běhu. Následující kód se zkompiluje v sadě Visual Studio 2015, ale dojde k chybě v sadě Visual Studio 2017.

```cpp
template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;
```

### <a name="expression-sfinae"></a>Výraz SFINAE

Výraz SFINAE účelem kompilátor nyní analyzuje `decltype` argumenty při šablony jsou deklarovány, nikoli vytvořena instance. V důsledku toho pokud nezávislé specializace je nalezena v decltype argument, to není odložena na čas vytvoření instance. Zpracovává se okamžitě a všechny případné chyby jsou zjištěna v daném čase.

Následující příklad ukazuje takový chybu kompilátoru, která je vyvolána v okamžiku deklarace:

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

### <a name="classes-declared-in-anonymous-namespaces"></a>Třídy deklarované v anonymních obory názvů

Podle C++ na úrovni standard třídy deklarované uvnitř anonymní obory názvů má vnitřní propojení, a to znamená, že není možné exportovat. V sadě Visual Studio 2015 a starší se vynutí toto pravidlo. V sadě Visual Studio 2017 se částečně vynucuje pravidla. Následující příklad vyvolá tuto chybu v sadě Visual Studio 2017: "Chyba C2201: const anonymní namespace::S1::vftable: musí mít externí propojení dalo Importovat/exportovat."

```cpp
struct __declspec(dllexport) S1 { virtual void f() {} }; //C2201
```

### <a name="default-initializers-for-value-class-members-ccli"></a>Výchozí inicializátory pro hodnotu členy třídy (C++vyhodnocovací)

V sadě Visual Studio 2015 a starší kompilátor povoleno (ale ignorovat) výchozí inicializátor členu pro člena třídy value class. Výchozí inicializace hodnotová třída vždy nula inicializuje členy. Výchozí konstruktor není povolená. V sadě Visual Studio 2017 výchozí inicializátory členů vyvolat chybu kompilátoru, jak je znázorněno v tomto příkladu:

```cpp
value struct V
{
    int i = 0; // error C3446: 'V::i': a default member initializer
               // isn't allowed for a member of a value class
};
```

### <a name="default-indexers-ccli"></a>Výchozí indexery (C++vyhodnocovací)

V sadě Visual Studio 2015 a starší kompilátor v některých případech misidentified výchozí vlastnost jako výchozí indexeru. Bylo možné tento problém obejít, s použitím identifikátoru `default` pro přístup k vlastnosti. Alternativní řešení, samotný začal být problematické po `default` byla zavedená jako klíčové slovo v C ++ 11. V sadě Visual Studio 2017, které jsme opravili chyby, které vyžaduje řešení, a kompilátor nyní vyvolá chybu při `default` se používá pro přístup k výchozí vlastnost pro třídu.

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

V sadě Visual Studio 2017 dostanete obě hodnotu vlastnosti podle názvu:

```cpp
#using "class1.dll"

void f(ClassLibrary1::Class1 ^r1, ClassLibrary1::Class2 ^r2)
{
       r1->Value;
       r2->Value;
}
```

## <a name="update_153"></a> Opravy chyb v sadě Visual Studio 2017 verze 15.3

### <a name="calls-to-deleted-member-templates"></a>Volání odstraněného člena šablony

V předchozích verzích sady Visual Studio selže v některých případech kompilátor generuje chybu pro nesprávném volání odstraněného člena šablony, která by potenciálně způsobit chyby za běhu. Následující kód vytvoří nyní C2280, "" int S\<int >:: f\<int > (void)': Pokus o odkazování na odstraněnou funkci ":

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

Chcete-li chybu opravit, deklarujte `i` jako `int`.

### <a name="pre-condition-checks-for-type-traits"></a>Předběžná podmínka zkontroluje pro typové vlastnosti

Visual Studio 2017 verze 15.3 zlepšuje předběžné podmínky kontroly pro typové více striktně dodržovat standardní. Jeden takový kontrola je pro přiřadit. Následující kód vytvoří C2139 v sadě Visual Studio 2017 verze 15.3:

```cpp
struct S;
enum E;

static_assert(!__is_assignable(S, S), "fail"); // C2139 in 15.3
static_assert(__is_convertible_to(E, E), "fail"); // C2139 in 15.3
```

### <a name="new-compiler-warning-and-runtime-checks-on-native-to-managed-marshaling"></a>Nová upozornění kompilátoru a modulu runtime kontroly nativního spravovaného zařazování

Volání nativních funkcí ze spravované funkce vyžaduje zařazování. Modul CLR provede zařazování, ale nebude pochopit C++ sémantiku. Pokud předáte nativní objekt podle hodnoty, CLR volá konstruktor copy objektu, nebo využívá `BitBlt`, což může způsobit nedefinované chování za běhu.

Kompilátor nyní generuje upozornění, pokud můžete vědět v době kompilace, která je předána nativní objekt s konstruktor copy odstraněný mezi nativním a spravovaným kódem podle hodnoty. Pro případy, ve kterých neví, kompilátor v době kompilace, ho vkládá kontrolu za běhu programu tak, že program volá `std::terminate` okamžitě chybný formát zařazování dojde. V sadě Visual Studio 2017 verze 15.3, následující kód vytvoří upozornění C4606 ""A": předání argumentů hodnotou mezi nativním a spravovaným kódem vyžaduje platný kopírovací konstruktor. V opačném případě nedefinované chování za běhu.

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

Chcete-li chybu opravit, odeberte `#pragma managed` – direktiva označit jako nativní volající a vyhnout se zařazování.

### <a name="experimental-api-warning-for-winrt"></a>Experimentální upozornění rozhraní API pro WinRT

Rozhraní API WinRT, která jsou vydána pro experimentování ve službě a zpětnou vazbu jsou vybaveny `Windows.Foundation.Metadata.ExperimentalAttribute`. V sadě Visual Studio 2017 verze 15.3 kompilátor vytvoří upozornění C4698, pokud se setká s atributem. Několik rozhraní API v předchozích verzích Windows SDK mají byl již upravené pomocí atributu a volání těchto rozhraní API teď aktivuje toto upozornění kompilátoru. Novější sady SDK pro Windows mají atribut odebrat ze všech typů odeslání, ale pokud používáte starší sada SDK, budete potřebovat k potlačení tato upozornění pro všechna volání dodané typy.

Následující kód vytvoří upozornění C4698: "" Windows:: úložiště:: IApplicationDataStatics2::GetForUserAsync"je pro účely vyhodnocení pouze a může změnit v budoucích aktualizacích nebo odebrání":

```cpp
Windows::Storage::IApplicationDataStatics2::GetForUserAsync(); //C4698
```

Pokud chcete toto upozornění zakážete, přidejte #pragma:

```cpp
#pragma warning(push)
#pragma warning(disable:4698)

Windows::Storage::IApplicationDataStatics2::GetForUserAsync();

#pragma warning(pop)
```

### <a name="out-of-line-definition-of-a-template-member-function"></a>Definice mimo řádek šablony členské funkce

Visual Studio 2017 verze 15.3 způsobí chybu, pokud se setká s definici mimo řádek šablony členské funkce, která nebyla deklarována ve třídě. Následující kód nyní generuje chybu C2039: 'f': není členem uživatele ":

```cpp
struct S {};

template <typename T>
void S::f(T t) {} //C2039: 'f': is not a member of 'S'
```

Chcete-li vyřešit chybu, přidejte do třídy deklaraci:

```cpp
struct S {
    template <typename T>
    void f(T t);
};
template <typename T>
void S::f(T t) {}
```

### <a name="attempting-to-take-the-address-of-this-pointer"></a>Pokus o převzetí adresy `this` ukazatele

V C++ `this` je hodnota, která není typu ukazatele do X. Nejde převzít adresu proměnné `this` nebo vázat na odkaz na lvalue. V předchozích verzích sady Visual Studio kompilátor by bylo možné toto omezení obejít použitím přetypování. V sadě Visual Studio 2017 verze 15.3 kompilátor vytvoří Chyba upozornění C2664.

### <a name="conversion-to-an-inaccessible-base-class"></a>Konverze na nepřístupnou základní třídu

Visual Studio 2017 verze 15.3 způsobí chybu při pokusu o převod typu na základní třídu, která je nedostupný. Nyní vyvolá kompilátor "Chyba C2243:"přetypování": měl převod z *' k ' B *' existuje, ale je nedostupný". Následující kód je chybně vytvořený a může potenciálně způsobit chyby za běhu. Kompilátor nyní vytvoří C2243, pokud se setká kód následujícím způsobem:

```cpp
#include <memory>

class B { };
class D : B { }; // C2243. should be public B { };

void f()
{
   std::unique_ptr<B>(new D());
}
```

### <a name="default-arguments-arent-allowed-on-out-of-line-definitions-of-member-functions"></a>Výchozí argumenty nejsou povolené u mimo řádek definice členské funkce

Výchozí argumenty nejsou povolené u definice mimo řádek členské funkce tříd šablon. Kompilátor vygeneruje upozornění v části **/ permissive**a závažná chyba pod **/ permissive-** .

V předchozích verzích sady Visual Studio následující chybně vytvořený kód může potenciálně způsobit selhání modulu runtime. Visual Studio 2017 verze 15.3 vygeneruje upozornění C5034: "A\<T >:: f': definice mimo řádek člena šablony třídy nemůže mít výchozí argumenty:

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

### <a name="use-of-offsetof-with-compound-member-designator"></a>Použití `offsetof` s složené označení člena.

V sadě Visual Studio 2017 verze 15.3, pomocí `offsetof(T, m)` kde *m* je "složené označení člena" výsledkem upozornění při kompilaci s **/Wall** možnost. Následující kód je chybně vytvořený a může potenciálně způsobit chyby za běhu. Vytvoří Visual Studio 2017 verze 15.3 "upozornění C4841: nestandardní rozšíření: složené označení člena. v offsetof":

```cpp
struct A {
   int arr[10];
};

// warning C4841: non-standard extension used: compound member designator in offsetof
constexpr auto off = offsetof(A, arr[2]);
```

Pokud chcete kód opravit, toto upozornění se pragma zakážete nebo změňte kód, který není použije `offsetof`:

```cpp
#pragma warning(push)
#pragma warning(disable: 4841)
constexpr auto off = offsetof(A, arr[2]);
#pragma warning(pop)
```

### <a name="using-offsetof-with-static-data-member-or-member-function"></a>Pomocí `offsetof` statický datový člen nebo členskou funkci

V sadě Visual Studio 2017 verze 15.3, pomocí `offsetof(T, m)` kde *m* odkazuje na statický datový člen nebo člen funkce dojde k chybě. Následující kód vytvoří "Chyba C4597: nedefinované chování: se použil offsetof na členskou funkci 'Příklad:" a "Chyba C4597: nedefinované chování: na statický datový člen"ukázkový"offsetof":

```cpp
#include <cstddef>

struct A {
   int ten() { return 10; }
   static constexpr int two = 2;
};

constexpr auto off = offsetof(A, ten);
constexpr auto off2 = offsetof(A, two);
```

Tento kód má chybný formát a může potenciálně způsobit chyby za běhu. Oprava chyby, změňte kód, který už má být vyvolán nedefinované chování. Je nepřenosné kód, který je zakázáno C++ standard.

### <a name="declspec"></a> Nová upozornění na `__declspec` atributy

V sadě Visual Studio 2017 verze 15.3 kompilátor už ignoruje atributy Pokud `__declspec(...)` je použit před `extern "C"` specifikace propojení. Dříve by kompilátor ignorovat atribut, což by mohlo mít vliv na modul runtime. Když **/Wall** a **/WX** jsou nastavené možnosti, následující kód vytvoří "upozornění C4768: atributy __declspec před specifikací propojení se ignorují.":

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

Chcete-li opravit toto upozornění, umístěte `extern "C"` první:

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

Toto upozornění je vypnuto ve výchozím nastavení v 15.3, ale na ve výchozí ve verzi 15.5, a pouze důsledky pro kód zkompilovaný s **/Wall** **/WX**.

### <a name="decltype-and-calls-to-deleted-destructors"></a>`decltype` a volání odstraněné destruktorů

V předchozích verzích sady Visual Studio, kompilátor nezjistili, kdy došlo k volání odstraněné destruktoru v kontextu výraz přidružený k `decltype`. V sadě Visual Studio 2017 verze 15.3, následující kód vytvoří "Chyba C2280: "A\<T >:: ~ A(void)': Pokus o odkazování na odstraněnou funkci":

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

Verze sady Visual Studio 2017 ve verzi RTW měl regrese, ve kterém C++ kompilátor by vystavovat diagnostických if `const` nebyla inicializována proměnná. Tento regresní chyba byla opravena v sadě Visual Studio 2017 verze 15.3. Následující kód vytvoří nyní "C4132 upozornění: 'Value': je třeba inicializovat objekt const ":

```cpp
const int Value; //C4132
```

Oprava chyby, přiřaďte hodnotu `Value`.

### <a name="empty-declarations"></a>Prázdná deklarace

Visual Studio 2017 verze 15.3 teď vás upozorní na prázdný deklarace pro všechny typy, stačí předdefinovaných typů. Následující kód nyní vygeneruje upozornění úrovně 2 C4091 pro všechny čtyři deklarace:

```cpp
struct A {};
template <typename> struct B {};
enum C { c1, c2, c3 };

int;    // warning C4091 : '' : ignored on left of 'int' when no variable is declared
A;      // warning C4091 : '' : ignored on left of 'main::A' when no variable is declared
B<int>; // warning C4091 : '' : ignored on left of 'B<int>' when no variable is declared
C;      // warning C4091 : '' : ignored on left of 'C' when no variable is declared
```

Odebrat upozornění, okomentujte nebo odeberte prázdné deklarace. V případech, kdy nepojmenované objektu má mít vliv na straně (například RAII) by měly mít název.

Upozornění je vyloučena pod **/WV: 18** a je ve výchozím v části upozornění úrovně W2.

### <a name="stdisconvertible-for-array-types"></a>`std::is_convertible` pro typy polí

Předchozí verze kompilátoru zadali nesprávné výsledky pro [std::is_convertible](../standard-library/is-convertible-class.md) pro typy polí. Tato oprávnění vyžadují knihovny autorům zvláštní případy Microsoft C++ kompilátoru při použití `std::is_convertible<...>` typovou vlastnost. V následujícím příkladu statické nepodmíněné výrazy pass v dřívějších verzích sady Visual Studio, ale selže v sadě Visual Studio 2017 verze 15.3:

```cpp
#include <type_traits>

using Array = char[1];

static_assert(std::is_convertible<Array, Array>::value);
static_assert(std::is_convertible<const Array, const Array>::value, "");
static_assert(std::is_convertible<Array&, Array>::value, "");
static_assert(std::is_convertible<Array, Array&>::value, "");
```

`std::is_convertible<From, To>` se vypočte tak, že kontroluje se, pokud definice imaginární funkce je ve správném:

```cpp
   To test() { return std::declval<From>(); }
```

### <a name="private-destructors-and-stdisconstructible"></a>Privátní destruktory a `std::is_constructible`

Předchozí verze kompilátoru ignorovat, jestli destruktor byl privátní při rozhodování o výsledek [std::is_constructible](../standard-library/is-constructible-class.md). Nyní je považuje za. V následujícím příkladu statické nepodmíněné výrazy pass v dřívějších verzích sady Visual Studio, ale selže v sadě Visual Studio 2017 verze 15.3:

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

Privátní destruktory způsobit, že typ bude bez constructible. `std::is_constructible<T, Args...>` se počítá jako kdyby byly vytvořeny následující deklarace:

```cpp
   T obj(std::declval<Args>()...)
```

Toto volání znamená volání destruktoru.

### <a name="c2668-ambiguous-overload-resolution"></a>C2668: Řešení nejednoznačných přetížení

Předchozí verze kompilátoru. někdy se nepodařilo rozpoznat nejednoznačnosti, kdy se našel více kandidáty prostřednictvím obě pomocí deklarací a vyhledávání závislé na argumentu. Toto selhání může vést nesprávné přetížení vybraným a neočekávané chování za běhu. V následujícím příkladu, Visual Studio 2017 verze 15.3 správně vyvolá C2668 'f': nejednoznačné volání přetížené funkce:

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

Pokud chcete kód opravit, odebrat, pomocí `N::f` příkazu, pokud máte v úmyslu volání `::f()`.

### <a name="c2660-local-function-declarations-and-argument-dependent-lookup"></a>C2660: lokální funkce deklarace a vyhledávání závislého na argumentech

Deklarace lokální funkce skrýt deklarace funkce v nadřazeném oboru a zakažte vyhledávání závislé na argumentu. Ale předchozí verze kompilátoru provést vyhledávání závislého na argumentech v takovém případě by mohlo vést k vybraným nesprávné přetížení a neočekávané chování za běhu. Chyba je obvykle kvůli nesprávným podpisem deklarace lokální funkce. V následujícím příkladu, Visual Studio 2017 verze 15.3 správně vyvolá C2660 'f': funkci nejde používat dva argumenty:

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

Chcete-li problém vyřešit, buď změňte `f(S)` podpis nebo jej odeberte.

### <a name="c5038-order-of-initialization-in-initializer-lists"></a>C5038: pořadí inicializace v seznamy inicializátorů

Členy třídy jsou inicializovány v pořadí, ve kterém jsou deklarovány, není pořadí, ve kterém se zobrazují v seznamy inicializátorů. Předchozí verze kompilátoru neměli upozornit, když pořadí položek v seznamu inicializátorů se liší od pořadí deklarace. Tento problém může vést k modulu runtime nedefinované chování, pokud inicializace jednoho člena závisí na jiného člena v seznamu již inicializován. V následujícím příkladu, Visual Studio 2017 verze 15.3 (s **/Wall**) vyvolá "upozornění C5038: datový člen 'A::y' bude inicializován po datovém členu"A::x"":

```cpp
struct A
{
    A(int a) : y(a), x(y) {} // Initialized in reverse, y reused
    int x;
    int y;
};
```

Chcete-li problém vyřešit, uspořádejte seznam inicializátorů mít stejném pořadí jako deklarace. Podobně jako upozornění je vyvoláno, když jeden nebo oba inicializátory odkazovat na členy základní třídy.

Toto upozornění je mimo výchozí a jediný ovlivňuje kód zkompilovaný s **/Wall**.

## <a name="update_155"></a> Opravy chyb a další změny chování v sadě Visual Studio 2017 verze 15.5

### <a name="partial-ordering-change"></a>Částečné řazení změnit

Kompilátor nyní správně odmítne následující kód a poskytuje správné chybová zpráva:

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

Problém v předchozím příkladu je, že jsou dva rozdíly v typech (konstantní nebo nekonstantní a aktualizací Service pack a bez aktualizací Service pack). Chyba kompilátoru eliminovat, odeberte jednu z rozdíly. To umožňuje kompilátoru jednoznačně řazení funkce.

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

Obslužné rutiny odkazu na pole nebo typ funkce se nikdy hodí pro libovolný objekt výjimky. Kompilátor teď správně respektuje toto pravidlo a vyvolá upozornění úrovně 4. Také již se neshoduje obslužnou rutinu `char*` nebo `wchar_t*` na řetězec literálu při **/Zc: strictstrings** se používá.

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

Následující kód se vyhnete chybu:

```cpp
catch (int (*)[1]) {}
```

### <a name="tr1"></a> `std::tr1` obor názvů je zastaralý.

Nestandardní `std::tr1` obor názvů je nyní označeny jako zastaralé v C ++ 14 a C ++ 17 režimy. Následující kód v sadě Visual Studio 2017 verze 15.5 vyvolává C4996:

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

Oprava chyby, odeberte odkaz na `tr1` obor názvů:

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

### <a name="annex_d"></a> Funkce standardní knihovny v příloze D jsou označené jako zastaralé

Když **/std: c ++ 17** přepínač kompilátoru režim je nastaven, téměř všechny funkce standardní knihovny v příloze D jsou označené jako zastaralé.

Následující kód v sadě Visual Studio 2017 verze 15.5 vyvolává C4996:

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

Oprava chyby, postupujte podle pokynů v upozornění textu, jak je ukázáno v následujícím kódu:

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

### <a name="unreferenced-local-variables"></a>Neodkazovaná lokální proměnné

V sadě Visual Studio 15.5 je vygenerován upozornění C4189 ve více případech, jak je znázorněno v následujícím kódu:

```cpp
void f() {
    char s[2] = {0}; // C4189. Either use the variable or remove it.
}
```

```Output
warning C4189: 's': local variable is initialized but not referenced
```

Chcete-li chybu opravit, odeberte nepoužívanou proměnnou.

### <a name="single-line-comments"></a>Jednořádkové komentáře

V sadě Visual Studio 2017 verze 15.5 upozornění C4001 a C4179 jsou již, protože ho vygeneroval kompilátor jazyka C. Dřív, byly jenom generované v části **/Za** přepínač kompilátoru.  Upozornění už nejsou potřeba, protože Jednořádkové komentáře byly součástí standardu C od C99.

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

Pokud kód nemusí být zpětně kompatibilní, můžete upozornění předejít tak, že odeberete C4001/C4179 potlačení. Pokud kód potřebuje zpětnou kompatibilitu, pak pouze potlačit C4619.

```C

/* C only */

#pragma warning(disable:4619)
#pragma warning(disable:4001)
#pragma warning(disable:4179)

// single line comment
/* single line comment */
```

### <a name="declspec-attributes-with-extern-c-linkage"></a>`__declspec` atributy s `extern "C"` propojení

V dřívějších verzích sady Visual Studio, kompilátor ignoruje `__declspec(...)` atributy při `__declspec(...)` bylo použito před `extern "C"` specifikace propojení. Toto chování způsobila kód je generován, který uživatel nechtěli s runtime možné důsledky. Upozornění bylo přidáno v sadě Visual Studio verze 15.3, ale bylo vypnuto ve výchozím nastavení. V sadě Visual Studio 2017 verze 15.5 upozornění je povolená ve výchozím nastavení.

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

```Output
warning C4768: __declspec attributes before linkage specification are ignored
```

Oprava chyby, vložte před atribut __declspec specifikací propojení:

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

Toto nové upozornění C4768 je uvedeno na záhlaví Windows SDK, které byly dodány s Visual Studio 2017 15.3 nebo starší (například: verzi 10.0.15063.0, označované také jako RS2 SDK). Novější verze sady Windows SDK hlavičky (konkrétně ShlObj.h a ShlObj_core.h) jsme opravili, ale tak, aby se nevytvářejí upozornění. Když se zobrazí toto upozornění z hlavičky Windows SDK, můžete provést tyto akce:

1. Přepnout na nejnovější sadu Windows SDK, která byla součástí verze sady Visual Studio 2017 verze 15.5.

1. Vypnout varování týkající #include příkazu záhlaví Windows SDK:

```cpp
   #pragma warning (push)
   #pragma warning(disable:4768)
   #include <shlobj.h>
   #pragma warning (pop)
   ```

### <a name="extern_linkage"></a>Extern constexpr propojení

V dřívějších verzích sady Visual Studio, kompilátor vždy přiřadil `constexpr` proměnné vnitřní propojení, i když byla označena jako proměnná `extern`. V sadě Visual Studio 2017 verze 15.5, nový přepínač kompilátoru ( **/Zc: externconstexpr**) umožňuje správné chování vyhovující standardům. Toto chování se nakonec stanou výchozí.

```cpp
extern constexpr int x = 10;
```

```Output
error LNK2005: "int const x" already defined
```

Pokud soubor hlavičky obsahuje proměnné deklarované `extern constexpr`, musí být označen `__declspec(selectany)` mít jeho duplicitní deklarace kombinovat správně:

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

### <a name="typeid-cant-be-used-on-incomplete-class-type"></a>`typeid` nelze použít na nekompletní typ třídy

V dřívějších verzích sady Visual Studio kompilátor nesprávně povoleny následující kód, což vede k potenciálně nesprávný typ informací. V sadě Visual Studio 2017 verze 15.5 správně kompilátor vyvolá chybu:

```cpp
#include <typeinfo>

struct S;

void f() { typeid(S); } //C2027 in 15.5
```

```Output
error C2027: use of undefined type 'S'
```

### <a name="stdisconvertible-target-type"></a>`std::is_convertible` Cílový typ

`std::is_convertible` Typ cíle na platný návratový typ vyžaduje. V dřívějších verzích sady Visual Studio kompilátor nesprávně povolená abstraktní typy, které by mohly vést k nesprávné přetížení a chování za běhu nežádoucí.  Následující kód nyní správně vyvolává C2338:

```cpp
#include <type_traits>

struct B { virtual ~B() = 0; };
struct D : public B { virtual ~D(); };

static_assert(std::is_convertible<D, B>::value, "fail"); // C2338 in 15.5
```

Aby se zabránilo chybě, při použití `is_convertible` protože porovnání ukazatele typu může selhat, pokud je jeden typ abstraktní porovnejte typy ukazatelů:

```cpp
#include <type_traits>

struct B { virtual ~B() = 0; };
struct D : public B { virtual ~D(); };

static_assert(std::is_convertible<D *, B *>::value, "fail");
```

### <a name="noexcept_removal"></a> Odebrání specifikace dynamických výjimek a `noexcept`

V C ++ 17 `throw()` je alias pro `noexcept`, `throw(<type list>)` a `throw(...)` se odeberou, a může taky obsahovat určité typy `noexcept`. Tato změna může způsobit problémy s kompatibilitou zdroje s kódem, který odpovídá do C ++ 14 nebo dřívější. **/Zc:noexceptTypes-** přepínač je možné vrátit zpět do C ++ 14 verze `noexcept` přitom C ++ 17 režim obecně. To vám umožní aktualizovat váš zdrojový kód tak, aby odpovídal C ++ 17, aniž byste museli přepsat všechny vaše `throw()` kódu ve stejnou dobu.

Kompilátor nyní také diagnostikuje další specifikace neodpovídající výjimek v deklaracích v C ++ 17 režimu nebo s **/ permissive-** pomocí nového upozornění C5043.

Následující kód vygeneruje C5043 a C5040 v sadě Visual Studio 2017 verze 15.5 při **/std: c ++ 17** použít přepínač:

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

Odebrat chyby stále přitom **/std: c ++ 17**, buď přidejte **/Zc:noexceptTypes-** přepínat do příkazového řádku, jinak aktualizovat kód Refaktorovat pro použití `noexcept`, jak je znázorněno v následujícím příkladu:

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

Constexpr statické datové členy se teď implicitně vloženě, což znamená, že jejich deklarace v rámci třídy je nyní jejich definice. Pomocí definice mimo řádek pro constexpr statický datový člen je redundantní a je nyní zastaralé. V sadě Visual Studio 2017 verze 15.5 když **/std: c ++ 17** přepínače se použije následující kód nyní generuje upozornění C5041 *"velikost": definice mimo řádek pro statický datový člen constexpr nevyžaduje a je zastaralá v C ++ 17*:

```cpp
struct X {
    static constexpr int size = 3;
};
const int X::size; // C5041
```

### <a name="extern-c-declspec-warning-c4768-now-on-by-default"></a>`extern "C" __declspec(...)` upozornění C4768 na teď ve výchozím nastavení

Upozornění bylo přidáno v sadě Visual Studio 2017 verze 15.3, ale bylo vypnuto ve výchozím nastavení. V sadě Visual Studio 2017 verze 15.5 je ve výchozím nastavení upozornění. Další informace najdete v tématu [nové upozornění na \_ \_declspec atributy](#declspec).

### <a name="defaulted-functions-and-declspecnothrow"></a>Nastavena výchozí hodnota funkce a `__declspec(nothrow)`

Kompilátor dříve povolené výchozí funkce deklarován s `__declspec(nothrow)` při odpovídající funkce base/member povolené výjimky. Toto chování je contrary C++ standardní a může způsobit nedefinované chování za běhu. Standardní vyžaduje tyto funkce k být definovaný jako odstraněný, pokud dojde neshoda specifikace výjimek.  V části **/std: c ++ 17**, následující kód vyvolá C2280 *pokus o odkazování na odstraněnou funkci. Funkce se implicitně odstranila, protože specifikace explicitní výjimky není kompatibilní se specifikací v implicitní deklaraci.*

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

Chcete-li tento kód opravit, buď odeberte __declspec(nothrow) z nastavený na výchozí hodnotu funkce, nebo odeberte `= default` a poskytnout definici pro funkce spolu s jakékoli zpracování požadované výjimky:

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

### <a name="noexcept-and-partial-specializations"></a>`noexcept` a částečné specializace

S `noexcept` v systému typů částečné specializace pro odpovídající konkrétní "volatelný" typy se nemusí podařit sestavit nebo zvolte primární šablony z důvodu chybějící částečnou specializaci pro ukazatele na noexcept funkce.

V takovém případě budete muset přidat další částečné specializace ke zpracování `noexcept` ukazatele funkcí a `noexcept` ukazatelů na členské funkce. Tato přetížení jsou pouze platné v **/std: c ++ 17** režimu. Pokud je třeba udržovat zpětné kompatibility s C ++ 14 a psaní kódu, který ostatní využívat, pak by měl ochranu těchto nová přetížení uvnitř `#ifdef` direktivy. Pokud pracujete v samostatné modulu, pak namísto použití `#ifdef` chrání můžete pouze kompilovat s **/Zc:noexceptTypes-** přepnout.

Následující kód se zkompiluje podle **/std: c ++ 14** , ale selže v rámci **/std: c ++ 17** s "chyba C2027:use nedefinovaného typu" A\<T > "":

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

Následující kód úspěšné pod **/std: c ++ 17** vzhledem k tomu, že kompilátor volí nový částečná specializace `A<void (*)() noexcept>`:

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

## <a name="update_157"></a> Opravy chyb a další změny chování v sadě Visual Studio 2017 verze 15.7

### <a name="c17-default-argument-in-the-primary-class-template"></a>C++17: Výchozí argument v šabloně primární třídy

Tato změna chování je předpokladem pro [odvození argumentu šablony pro šablony třídy – P0091R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html).

Dříve Kompilátor ignoruje výchozí argument v šabloně primární třídy:

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int = 0) {} // Re-definition necessary
```

V **/std: c ++ 17** režimu v aplikaci Visual Studio 2017 verze 15.7, výchozí argument není ignorována:

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int) {} // Default argument is used
```

### <a name="dependent-name-resolution"></a>Závislé překlad

Tato změna chování je předpokladem pro [odvození argumentu šablony pro šablony třídy – P0091R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html).

V následujícím příkladu se přeloží kompilátor v aplikaci Visual Studio 15.6 a starších verzích `D::type` k `B<T>::type` v šabloně primární třídy.

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

Visual Studio 2017 verze 15.7, v **/std: c ++ 17** režim, vyžaduje `typename` – klíčové slovo v `using` příkaz v D. Bez `typename`, kompilátor vyvolá upozornění C4346: *' B < T\*>:: typu ': závislý název není typ* a chyba C2061: *Chyba syntaxe: identifikátor 'type'* :

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

### <a name="c17-nodiscard-attribute---warning-level-increase"></a>C ++ 17: `[[nodiscard]]` atribut – zvýšení úrovně upozornění

V sadě Visual Studio 2017 verze 15.7 v **/std: c ++ 17** režimu, úroveň upozornění c4834 (zahazuje se návratová hodnota funkce s atributem nodiscard.") zvýšila z W3 na W1. Můžete zakázat upozornění pomocí přetypování na `void`, nebo předáním **/wd:4834** kompilátoru

```cpp
[[nodiscard]] int f() { return 0; }

int main() {
    f(); // warning: discarding return value
         // of function with 'nodiscard'
}
```

### <a name="variadic-template-constructor-base-class-initialization-list"></a>Variadické šablony konstruktor základní třídy inicializačního seznamu

V předchozích verzích sady Visual Studio byla chybně variadické šablony konstruktor základní třídy Inicializace seznamu, který chybí argumenty šablony povolena bez chyb. V sadě Visual Studio 2017 verze 15.7 se vyvolá chybu kompilátoru.

Následující příklad kódu v sadě Visual Studio 2017 verze 15.7 vyvolá *chyba C2614: D\<int >: Neplatná inicializace členu: "B" není základní nebo členský*

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

Oprava chyby, změnit výraz B() b\<T > ().

### <a name="constexpr-aggregate-initialization"></a>`constexpr` Inicializace agregace

Předchozí verze C++ kompilátor správně zpracovává `constexpr` inicializace agregace; it přijat neplatný kód, ve kterém agregace init-list má příliš mnoho prvků a vytváří nesprávná funkce codegen pro něj. Následující kód je příkladem takového kódu:

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

V sadě Visual Studio 2017 verze 15.7 s aktualizací 3 nebo novější, nyní z předchozího příkladu vyvolává *C2078 moc velký počet inicializátorů*. Následující příklad ukazuje, jak kód opravit. Při inicializaci `std::array` s vnořených závorek init-lists poskytnout vnitřní pole braced seznam vlastní:

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

## <a name="update_158"></a> Opravy chyb a změny chování v sadě Visual Studio 2017 verze 15.8

Změny kompilátoru v sadě Visual Studio 2017 verze 15.8 všechny spadají pod kategorii opravy chyb a změny chování a jsou uvedeny níže:

### <a name="typename-on-unqualified-identifiers"></a>`typename` na neúplný identifikátory

V [/ permissive-](../build/reference/permissive-standards-conformance.md) režimu detekováno falešné `typename` klíčová slova na neúplný identifikátory v definicích šablon alias už akceptuje kompilátor. Následující kód vytvoří nyní C7511 *'T': 'typename' – klíčové slovo musí následovat kvalifikovaný název*:

```cpp
template <typename T>
using  X = typename T;
```

Oprava chyby, změňte druhý řádek na `using  X = T;`.

### <a name="declspec-on-right-side-of-alias-template-definitions"></a>`__declspec()` na pravé straně definice šablony aliasů

[__declspec](../cpp/declspec.md) už můžou běžet na pravé straně definice šablony aliasu. Tento kód byl dříve přijali službu, ale ignoruje kompilátor a by nikdy výsledek v upozornění zastarání při aliasem, který byl použit.

Standardní C++ atribut [ \[ \[zastaralé\] \] ](../cpp/attributes.md) mohou být použity místo toho a dodržovat je i v sadě Visual Studio 2017 verze 15.6. Následující kód vytvoří nyní C2760 *Chyba syntaxe: Neočekávaný token '__declspec' Očekávalo se specifikátor typu*:

```cpp
template <typename T>
using X = __declspec(deprecated("msg")) T;
```

Oprava chyby, změňte kód takto (s atributem umístěn před '=' Definice aliasu):

```cpp
template <typename T>
using  X [[deprecated("msg")]] = T;
```

### <a name="two-phase-name-lookup-diagnostics"></a>Název pro dvoufázové vyhledávání diagnostiky

Dvoufázové vyhledávání názvů vyžaduje, že v době definice musí být viditelná pro šablonu bez závislých názvů používaných v těla šablony. Dříve, Microsoft C++ kompilátoru zůstane nenalezeným elementem název jako není looked až čas vytvoření instance. Nyní vyžaduje nezávislé názvy jsou navázány v těle šablony.

Jedním ze způsobů, který to můžete manifest se vyhledávání na závislé základní třídy. Dříve kompilátor povolené použití názvy, které jsou definovány v závislé základních tříd, vzhledem k tomu, že by vyhledávat během doby vytváření instancí, když jsou překládány všechny typy. Teď, když kód je považováno za chybu. V těchto případech můžete vynutit proměnnou pro kvalifikaci typu základní třídy nebo jinak tak závislé, například přidáním vyhledávat v době vytváření instancí `this->` ukazatele.

V **/ permissive-** režimu, následující vyvolá nyní kód C3861: *'base_value': identifikátor se nenašel*:

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

Chcete-li chybu opravit, změňte `return` příkazu `return this->base_value;`.

**Poznámka:** V knihovně python Boost došlo po dlouhou dobu konkrétní MSVC alternativní řešení pro dopředné deklarace šablony v [unwind_type.hpp](https://github.com/boostorg/python/blame/develop/include/boost/python/detail/unwind_type.hpp). V části [/ permissive-](../build/reference/permissive-standards-conformance.md) režimu od verze Visual Studio 2017 verze 15.8 (_MSC_VER = 1915), a kompilátorem MSVC správně provede vyhledávání názvu závislého na argumentu (ADL) a je konzistentní s jinými kompilátory, vytváření tohoto řešení guard zbytečné. Aby se zabránilo chybě *C3861: 'unwind_type': identifikátor se nenašel*, naleznete v tématu [229 žádosti o přijetí změn](https://github.com/boostorg/python/pull/229) v úložišti Boost k aktualizaci souboru hlaviček. Už jsme opravy [vcpkg](../build/vcpkg.md) Boost balíčku, tak pokud získat nebo upgrade zdroje Boost z vcpkg pak není nutné samostatně opravy.

### <a name="forward-declarations-and-definitions-in-namespace-std"></a>Dopředné deklarace a definice v oboru názvů `std`

Standard jazyka C++ neumožňuje uživateli přidat dopředné deklarace nebo definice do oboru názvů `std`. Přidání definice nebo deklarace do oboru názvů `std` nebo do oboru názvů v rámci oboru názvů `std` nyní způsobí nedefinované chování.

Někdy v budoucnu Microsoft přesune umístění, kde jsou definovány některé typy standardní knihovny. Tato změna přeruší stávající kód, který přidá dopředné deklarace do oboru názvů `std`. Nová upozornění, C4643, pomáhá identifikovat problémy tyto zdroje. Upozornění je povolená v **/výchozí** režimu a je vypnuto ve výchozím nastavení. Bude to mít vliv programy, které jsou kompilovány pomocí **/Wall** nebo **/WX**.

Následující kód teď vyvolává C4643: *Předat dál deklarace 'vektorové' v oboru názvů std není povolen podle standardu jazyka C++* .

```cpp
namespace std {
    template<typename T> class vector;
}
```

Chcete-li chybu opravit, použijte **zahrnují** direktiv místo Dopředná deklarace:

```cpp
#include <vector>
```

### <a name="constructors-that-delegate-to-themselves"></a>Konstruktory, které delegovat na sebe

C++ Standard naznačuje, že kompilátor by měly vydávat Diagnostika při Delegující konstruktor deleguje na sebe sama. Kompilátor C++ společnosti Microsoft v [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md) a [/std: c ++ nejnovější](../build/reference/std-specify-language-standard-version.md) režimy nyní vyvolá C7535: *'X::X': delegování konstruktorů zavolá sama sebe*.

Bez této chyby následující program zkompiluje, ale bude generovat nekonečná smyčka:

```cpp
class X {
public:
    X(int, int);
    X(int v) : X(v){}
};
```

Aby se zabránilo nekonečnou smyčku, delegovat na jiný konstruktor:

```cpp
class X {
public:

    X(int, int);
    X(int v) : X(v, 0) {}
};
```

### <a name="offsetof-with-constant-expressions"></a>`offsetof` pomocí výrazů konstant

[offsetof](../c-runtime-library/reference/offsetof-macro.md) tradičně byl implementován použití makra, která vyžaduje [reinterpret_cast](../cpp/reinterpret-cast-operator.md). Toto použití je neplatný v kontextech, které vyžadují konstantní výraz, ale Microsoft C++ kompilátoru tradičně povolil ho. `offsetof` – Makro, který je dodáván jako součást standardní knihovny správně používá vnitřní kompilátor ( **__builtin_offsetof**), ale mnoho lidí použilo zdvih – makro definovat vlastní `offsetof`.

V sadě Visual Studio 2017 verze 15.8 kompilátor omezí oblastí podporovaných těmito `reinterpret_cast` operátory mohou objevit ve výchozím režimu, abychom kód se řídí standardem C++ chování. V části [/ permissive-](../build/reference/permissive-standards-conformance.md), omezení jsou ještě přísnější. Pomocí výsledek `offsetof` na místech, které vyžadují konstantní výrazy mohou způsobit kód, který vydá upozornění C4644 *využití modelu na základě – makro offsetof v konstantních výrazech je nestandardní; použití offsetof definované v C++ Standardní knihovna místo toho* nebo C2975 *neplatný argument šablony, očekávané době kompilace konstantní výraz*.

Následující kód vyvolá C4644 v **/výchozí** a **/std: c ++ 17** režimech a C2975 v **/ permissive-** režimu:

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

Chcete-li chybu opravit, použijte `offsetof` definované prostřednictvím \<cstddef – >:

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

### <a name="cv-qualifiers-on-base-classes-subject-to-pack-expansion"></a>Kvalifikátory CV na základní třídy v souladu s rozšíření balíčku

Předchozí verze agenta Microsoft C++ kompilátoru nezjistilo, že má základní třída měli kvalifikátory cv, pokud byl také v souladu s rozšíření balíčku.

V sadě Visual Studio 2017 verze 15.8 v **/ permissive-** režimu následující kód vyvolá C3770 *'const S': není platnou základní třídu*:

```cpp
template<typename... T>
class X : public T... { };

class S { };

int main()
{
    X<const S> x;
}
```

### <a name="template-keyword-and-nested-name-specifiers"></a>`template` klíčové slovo a vnořené specifikátory názvů

V **/ permissive-** režim, kompilátor nyní vyžaduje `template` – klíčové slovo předcházet název šablony, pokud jde o po závislé vnořené název specifier.

Následující kód na **/ permissive-** režimu nyní vyvolá C7510: *'Příklad:: použití závislé šablony názvu musí obsahovat předponu "Šablona". Poznámka: Přečtěte si referenční informace k vytvoření instance šablony třídy ' X<T>"se zkompilovat*:

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

Oprava chyby, přidejte `template` – klíčové slovo chcete `Base<T>::example<int>();` příkaz, jak je znázorněno v následujícím příkladu:

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

## <a name="update_159"></a> Opravy chyb a změny chování v sadě Visual Studio 2017 verze 15.9

### <a name="identifiers-in-member-alias-templates"></a>Identifikátory v členské šablony aliasů

Identifikátor používán členem definice šablony aliasu musí být deklarované před použitím.

V předchozích verzích kompilátoru byla povolena následující kód:

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

V sadě Visual Studio 2017 verze 15.9 v **/ permissive-** režimu, vyvolá kompilátor C3861: *'from_template': identifikátor se nenašel*.

Chcete-li chybu opravit, deklarujte `from_template` před `from_template_t`.

### <a name="modules-changes"></a>Změny modulů

V sadě Visual Studio 2017 verze 15.9, kompilátor vyvolá C5050 pokaždé, když nejsou konzistentní mezi vytváření modulu a modulu spotřeby strany možnosti příkazového řádku pro moduly. V následujícím příkladu jsou dva problémy:

- Na straně spotřebu (main.cpp), možnost **/EHsc** není zadán.

- C++ Verze je **/std: c ++ 17** na straně vytváření a **/std: c ++ 14** na straně spotřeby.

```cmd
cl /EHsc /std:c++17 m.ixx /experimental:module
cl /experimental:module /module:reference m.ifc main.cpp /std:c++14
```

Kompilátor vyvolá C5050 u obou těchto případech: *upozornění C5050: Teď je to možné kompatibilní prostředí při importování modulu ': Neshoda verze jazyka C++.  Aktuální verze modulu "201402" "201703"* .

Kompilátor také vyvolává C7536 pokaždé, když se soubor .ifc bylo manipulováno. Záhlaví rozhraní modulu obsahuje SHA2 potvrzovaného obsahu pod ní. Při importu je soubor .ifc mají hodnotu hash stejným způsobem a potom zkontrolován poskytnutá v záhlaví hodnota hash. Pokud tyto neodpovídají, je vyvolána chyba C7536: *ifc nepovedlo kontroly integrity.  Byl očekáván SHA2: '66d5c8154df0c71d4cab7665bab4a125c7ce5cb9a401a4d8b461b706ddd771c6'* .

### <a name="partial-ordering-involving-aliases-and-non-deduced-contexts"></a>Částečné řazení zahrnující aliasů a -odvodit kontextů

Implementace odchýlit částečné pořadí pravidel zahrnující aliasů v kontextech odvodit. V následujícím příkladu, GCC a kompilátor C++ společnosti Microsoft (v **/ permissive-** režimu) vyvolá chybu, zatímco Clang přijímá kód.

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

V předchozím příkladu vyvolává C2668:

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

Implementace odchylkami je z důvodu regrese v C++ standardní znění. Řešení problému s jádrem 2235 odebrat nějaký text, který umožňoval tato přetížení příkazu. Aktuální C++ standard neposkytuje mechanismus pro částečně pořadí těchto funkcí, takže budou považovány za nejednoznačné.

Jako alternativní řešení je doporučeno, že není využívají částečné řazení pro vyřešení problému. Místo toho použijte SFINAE odebrat konkrétní přetížení. V následujícím příkladu používáme pomocná třída `IsA` odebrat první přetížení, kdy `Alloc` je specializací `A`:

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

### <a name="illegal-expressions-and-non-literal-types-in-templated-function-definitions"></a>Neplatné výrazy a typy literálu v definicích šablon funkce

Neplatné výrazy a typy literálu jsou teď správně zjistit, v definicích šablony funkce, které jsou explicitně specializovaný. Dříve nebyly tyto chyby generované pro definici funkce. Však neplatný výraz nebo neliterálního typu by stále mít byla zjištěna při vyhodnocení konstantního výrazu v rámci.

V předchozích verzích sady Visual Studio následující kód zkompiluje bez upozornění:

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

Kód v sadě Visual Studio 2017 verze 15.9 vyvolá tuto chybu:

```Output
error C3615: constexpr function 'S<int>::f' cannot result in a constant expression.
note: failure was caused by call of undefined function or one not declared 'constexpr'
note: see usage of 'g'.
```

Aby se zabránilo chybě, odeberte `constexpr` kvalifikátor z explicitní vytváření instancí funkce `f()`.

::: moniker-end

## <a name="c-conformance-improvements-in-visual-studio-2015"></a>C++vylepšení v sadě Visual Studio 2015

Úplný seznam vylepšení nahoru přes Visual Studio 2015 Update 3, naleznete v tématu [Visual C++ co na nový 2003 – 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015).

## <a name="see-also"></a>Viz také:

[Shoda jazyka Visual C++](../visual-cpp-language-conformance.md)
