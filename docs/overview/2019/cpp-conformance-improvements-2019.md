---
title: Vylepšení shody C++
ms.date: 03/22/2019
ms.technology: cpp-language
author: mikeblome
ms.author: mblome
ms.openlocfilehash: e12504d4950c87042cbb030c6c683874f6ffc8b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410120"
---
# <a name="c-conformance-improvements-in-visual-studio-2019"></a>Vylepšení shody C++ Visual Studio 2019

Visual Studio 2019 RTW obsahuje následující vylepšení, oprav chyb a změny chování v kompilátoru C++ společnosti Microsoft (MSVC).

**Poznámka:** 20 funkce c ++ bude k dispozici v `/std:c++latest` režimu až do dokončení provádění 20 C ++ pro kompilátor a technologie IntelliSense. V tu chvíli `/std:c++20` režim kompilátoru se bude zavádět.

## <a name="conformance-improvements"></a>Vylepšení shody

### <a name="improved-modules-support-for-templates-and-error-detection"></a>Moduly Vylepšená podpora pro šablony a detekce chyb

Moduly jsou nyní oficiálně v C ++ 20 standard. Vylepšená podpora byl přidán v sadě Visual Studio 2017 verze 15.9. Další informace najdete v tématu [lepší podporu a Chyba zjišťování šablony v moduly C++ s MSVC 2017 verzi 15.9](https://devblogs.microsoft.com/cppblog/better-template-support-and-error-detection-in-c-modules-with-msvc-2017-version-15-9/).

### <a name="modified-specification-of-aggregate-type"></a>Změny specifikace požadovaný typ agregace

Specifikace agregační typ se změnil v C ++ 20 (viz [zakázat agregace s uživatelem deklarované konstruktory](http://wg21.link/p1008r1)). V aplikaci Visual Studio 2019 pod `/std:c++latest`, třída s atributem žádné uživatelem deklarovaným konstruktorem (například včetně konstruktor deklarovat `= default` nebo `= delete`) není agregační. Předtím jenom uživatelem zadané konstruktory by vyřadit třídy z se agregace. Tato změna vloží další omezení na tom, jak lze inicializovat tyto typy.

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

C ++ 20 zavádí `<=>` operátor porovnání trojcestných, označované také jako "kosmické lodě operátor". Visual Studio 2019 v `/std:c++latest` režimu zavádí částečně se podporuje pro operátor vyvoláním chyby syntaxe, která je teď zakázaná. Například následující kód zkompiluje bez chyb v sadě Visual Studio 2017, ale vyvolá více chyb v aplikaci Visual Studio 2019 pod `/std:c++latest`:

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

Argument `reinterpret_cast` není jedním z kontextu, ve kterých je povolená adresa přetíženou funkci. Následující kód se zkompiluje bez chyb v sadě Visual Studio 2017, ale v aplikaci Visual Studio 2019 vyvolá *C2440: nelze převést z "přetížené funkce" na "fp"*:

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

## <a name="bug-fixes-and-behavior-changes"></a>Opravy chyb a změny chování

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

### <a name="incorrect-calls-to--and---under-clr-or-zw-are-now-correctly-detected"></a>Nyní jsou správně rozpozná nesprávné volání += a-= pod parametrem/CLR nebo /ZW.

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

Neplatný člen přistupuje k v rámci `inline` a `static constexpr` inicializátory jsou nyní správně rozpozná. Následující příklad se zkompiluje bez chyb v sadě Visual Studio 2017, ale Visual Studio 2019 pod `/std:c++17` režimu vyvolá *chyba C2248: přístup privátního člena nelze deklarovat v třídě 'X'*.

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

MSVC mívali výkon upozornění C4800 o implicitní převod na celočíselnou hodnotu, která byla příliš aktivní nebo insuppressible, vedoucí nám odebrat v sadě VS 2017. Však přes životní cyklus sady VS 2017 jsme máte spoustu zpětné vazby na užitečné případy, které se řešení. Jsme vrácení Visual Studio 2019 pečlivě míru C4800 spolu s jeho související C4165, které jde snadno potlačit explicitní přetypování nebo porovnání 0 příslušného typu. C4800 se o varování mimo výchozí úroveň 4 a C4165 se o varování mimo výchozí úroveň 3. Obě jsou zjistitelné pomocí `/Wall` – možnost kompilátoru.

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

### <a name="clr-now-incompatible-with-stdclatest"></a>/ CLR teď kompatibilní s/std: c ++ nejnovější

MSVC zahájení implementace funkce z C ++ 20 standardní návrhu v rámci `/std:c++latest` příznak `/std:c++latest` je teď kompatibilní s `/clr` (všechny typy), `/ZW`, a `/Gm`. V aplikaci Visual Studio 2019 pomocí `/std:c++17` nebo `/std:c++14` režimy při kompilaci s `/clr`, `/ZW` nebo `/Gm`.

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

## <a name="see-also"></a>Viz také:

[Co je nového ve Visual Studio 2019](../what-s-new-for-visual-cpp-in-visual-studio.md)