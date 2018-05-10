---
title: Vylepšení shoda C++ | Microsoft Docs
ms.custom: ''
ms.date: 03/11/2018
ms.technology:
- cpp-language
ms.topic: conceptual
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1fd640b838c10e010cf2ea028d5f693cd2e5ba14
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="c-conformance-improvements-in-visual-studio-2017-versions-150-153improvements153-155improvements155-156improvements156-and-157improvements157"></a>Vylepšení shoda C++ verze Visual Studio 2017 15.0, [15.3](#improvements_153), [15,5](#improvements_155), [15,6 operací](#improvements_156), a [15.7](#improvements_157)

Podpora pro zobecněný constexpr a NSDMI pro agregace Microsoft Visual C++ compiler je u konce pro funkce přidané do C ++ 14 Standard. Mějte na paměti, že v kompilátoru stále chybí několik funkcí ze standardů C++11 a C++98. V tématu [přizpůsobení jazyka Visual C++](visual-cpp-language-conformance.md) pro tabulku, která se zobrazuje aktuální stav kompilátoru.

## <a name="c11"></a>C ++ 11

### <a name="expression-sfinae-support-in-more-libraries"></a>Podpora sfinae u výrazů výrazu v dalších knihoven

Kompilátor dál vylepšit jeho podporu pro výraz sfinae u výrazů, což je vyžadováno pro odvození argumentu šablony a nahrazení, kde může výrazy decltype a constexpr se zobrazí jako parametry šablony. Další informace najdete v tématu [vylepšení výraz sfinae u výrazů v sadě Visual Studio 2017 RC](https://blogs.msdn.microsoft.com/vcblog/2016/06/07/expression-sfinae-improvements-in-vs-2015-update-3).

## <a name="c-14"></a>C++ 14

### <a name="nsdmi-for-aggregates"></a>NSDMI pro agregace

Agregace je pole nebo třídy nebyl zadaný uživatelem konstruktor, žádné datové nestatické soukromé nebo chráněné členy, žádné základní třídy a bez virtuální funkce. Od verze C ++ 14 agregace může obsahovat inicializátory člen. Další informace najdete v tématu [inicializátory člen a agreguje](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3605.html).

### <a name="extended-constexpr"></a>Rozšířené constexpr

Výrazy deklarovaných jako constexpr nyní mohou obsahovat určité typy deklarací, je-li a přepínače příkazy, příkazy smyčky a mutace objekty, jejichž doba platnosti začal v rámci vyhodnocení výrazu constexpr. Navíc se již požadavek, aby se implicitně const nestatické členské funkce constexpr. Další informace najdete v tématu [uvolnit omezení na constexpr funkce](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3652.html).

## <a name="c17"></a>C ++ 17

### <a name="terse-staticassert"></a>Ve formátu Terse zasílaná static_assert

Parametr zpráva pro static_assert je volitelné. Další informace najdete v tématu [Extending static_assert, v2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3928.pdf).

### <a name="fallthrough-attribute"></a>[[fallthrough]] atributu

V **/std: c ++ 17** režimu, můžete jako nápovědu pro kompilátor, že je určený chování patří prostřednictvím použit atribut [[fallthrough]] v kontextu příkazů přepínače. Kompilátor zabrání vydání upozornění v takových případech. Další informace najdete v tématu [formulaci pro atribut [[fallthrough]]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0188r0.pdf).

### <a name="generalized-range-based-for-loops"></a>Zobecněn na základě rozsahu smyčky for

Na základě rozsahu pro smyčky už nevyžadují, aby begin() a end() vrátí objekty stejného typu. To umožňuje end() vrátit sentinel jako použít podle rozsahů v [rozsah v3](https://github.com/ericniebler/range-v3) a dokončit, ale není – konce publikován technických specifikací rozsahy. Další informace najdete v tématu [generalizací založený na rozsahu pro smyčky](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html).

## <a name="improvements_153"></a> Vylepšení v nástroji Visual Studio 2017 verze 15.3

### <a name="constexpr-lambdas"></a>constexpr lambdas

Lambda – výrazy lze nyní v konstantní výrazy. Další informace najdete v tématu [Constexpr Lambda](http://open-std.org/JTC1/SC22/WG21/docs/papers/2015/n4487.pdf).

### <a name="if-constexpr-in-function-templates"></a>Pokud constexpr v šablonách – funkce

Šablonu funkce může obsahovat `if constexpr` příkazy umožňující vytvoření větve kompilaci. Další informace najdete v tématu [Pokud constexpr](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0128r1.html).

### <a name="selection-statements-with-initializers"></a>Příkazy výběru s inicializátory

`if` Příkaz může zahrnovat inicializátoru zavádí proměnné v oboru bloku v rámci příkazu sám sebe. Další informace najdete v tématu [příkazy výběru s inicializátoru](http://www.open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0305r1.html).

### <a name="maybeunused-and-nodiscard-attributes"></a>[[maybe_unused]] a [[nodiscard]] atributy

Nové atributy ticho upozornění, když se nepoužívá entity, nebo vytvořte upozornění, pokud budou zahozeny vrácené hodnoty volání funkce. Další informace najdete v tématu [formulaci pro atribut maybe_unused](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0212r0.pdf) a [návrh nevyužité, nodiscard a fallthrough atributů](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0068r0.pdf).

### <a name="using-attribute-namespaces-without-repetition"></a>Použití oboru názvů atribut bez opakování

Nové syntaxe Povolit jenom identifikátor jeden obor názvů v seznamu atributů. Další informace najdete v tématu [atributy v jazyce C++](cpp/attributes.md).

### <a name="structured-bindings"></a>Strukturované vazby

Nyní je možné v jediné deklaraci uložit hodnotu s jednotlivé názvy pro součásti své při hodnota pole, std::tuple nebo std::pair nebo má všechny veřejná data nestatické členy. Další informace najdete v tématu [strukturovaných vazby](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0144r0.pdf).

### <a name="construction-rules-for-enum-class-values"></a>Vytváření pravidel pro hodnoty výčtu – třída

Nyní převod implicitní nebo jiných zužující z podkladovým typem výčtu oboru na výčtu samostatně, pokud nastane jeho definice zavádí žádné enumerátor a zdroj používá syntaxí seznamu inicializace. Další informace najdete v tématu [vytváření pravidel pro příkaz enum třídy hodnoty](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0138r2.pdf).

### <a name="capturing-this-by-value"></a>Zaznamenání * to podle hodnoty

`*this` Objekt ve výrazu lambda mohou být zachyceny teď hodnotou. To umožňuje scénáře, ve kterých je volána argument lambda v paralelní a asynchronní operace, zejména u novější architektury počítačů. Další informace najdete v tématu [Lambda zaznamenat z \*to podle hodnoty jako [=,\*to]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0018r3.html).

### <a name="removing-operator-for-bool"></a>Odebrání operator ++ pro bool

`operator++` již není podporována na `bool` typy. Další informace najdete v tématu [odebrat zastaralé operator++(bool)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0002r1.html).

### <a name="removing-deprecated-register-keyword"></a>Odebrání zastaralé "register" – klíčové slovo

`register` – Klíčové slovo, dříve zastaralé (a ignoruje kompilátorem), je teď odebrané od jazyka. Další informace najdete v tématu [odebrat zastaralé použití register – klíčové slovo](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0001r1.html).

Úplný seznam vylepšení shoda se prostřednictvím Visual Studio 2015 Update 3 najdete v tématu [Visual C++ Co je nového 2003 až 2015](https://msdn.microsoft.com/en-us/library/mt723604.aspx).

## <a name="improvements_155"></a>  Vylepšení v nástroji Visual Studio 2017 verze 15,5

Funkce, které jsou označené jako [14] jsou k dispozici bezpodmínečně i při **/std: c ++ 14** režimu.

### <a name="new-compiler-switch-for-extern-constexpr"></a>Nové kompilátoru přepínač pro extern constexpr

V dřívějších verzích sady Visual Studio, kompilátor vždy Dal `constexpr` proměnné vnitřní propojení i v případě, že byla označena jako proměnnou `extern`. V aplikaci Visual Studio 2017 verze 15,5 nového přepínače kompilátoru [/Zc:externConstexpr](build/reference/zc-externconstexpr.md), umožňuje správné chování podle standardů. Další informace najdete v tématu [extern constexpr propojení](#extern_linkage).

### <a name="removing-dynamic-exception-specifications"></a>Odebrání specifikace dynamické výjimek

[P0003R5](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html) specifikace dynamické výjimek byly zastaralé v C ++ 11. Tato funkce se odebere z C ++ 17, ale nepoužívá (stále) `throw()` specifikace se uchovávají výhradně jako alias pro `noexcept(true)`. Další informace najdete v tématu [odebrání specifikace dynamické výjimky a noexcept](#noexcept_removal).

### <a name="notfn"></a>not_fn()

[P0005R4](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0005r4.html) `not_fn` je nahrazení `not1` a `not2`.

### <a name="rewording-enablesharedfromthis"></a>Enable_shared_from_this rozdělit

[P0033R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0033r1.html) `enable_shared_from_this` se přidal ve C ++ 11. C ++ 17 Standard aktualizuje specifikace pro lepší zpracování určitých případech rohu. [14]

### <a name="splicing-maps-and-sets"></a>Splétání Maps a sad

[P0083R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf) tato funkce umožňuje extrakce uzlů z asociativní kontejnery (například mapy, nastavit, neuspořádané\_mapy, neuspořádané\_nastavit) které pak se dají upravit a vložit zpět do kontejneru stejné nebo jiné kontejner, který používá stejný typ uzlu. (Je běžně používá k extrakci uzlu z `std::map`, změňte klíč a znovu vložit.)

### <a name="deprecating-vestigial-library-parts"></a>Místo začne částí Vestigial knihovny

[P0174R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0174r2.html) několik funkcí standardní knihovně C++ bylo nahrazeno funkcemi novější průběhu let, jinak byly zjištěny být velmi užitečná nebo způsobovat problémy. Tyto funkce jsou zastaralé oficiálně součástí C ++ 17.

### <a name="removing-allocator-support-in-stdfunction"></a>Odebrání std::function Allocator podpory v

[P0302R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0302r1.html) před C ++ 17 šablona třídy `std::function` měl několik konstruktorů, které trvalo allocator argument. Ale použití alokátorů v tomto kontextu byl problematická a sémantiky byly jasné. Proto tyto contructors byly odebrány.

### <a name="fixes-for-notfn"></a>Opravy pro not_fn()

[P0358R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0358r1.html) nové znění `std::not_fn` poskytuje podporu šíření kategorie hodnota v případě vyvolání obálku.

### <a name="sharedptrt-sharedptrtn"></a>shared_ptr\<[] – T >, shared_ptr\<T [N] >

[P0414R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0414r2.html) sloučení `shared_ptr` změny z knihovny Základy C ++ 17. [14]

### <a name="fixing-sharedptr-for-arrays"></a>Oprava shared_ptr pro pole

[P0497R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0497r0.html) opravy pro podporu shared_ptr pro pole. [14]

### <a name="clarifying-insertreturntype"></a>Insert_return_type, které toto vyjasňují

[P0508R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0508r0.html) asociativní kontejnery s jedinečné klíče a neuspořádaného kontejnery s jedinečné klíče mají členské funkce `insert` vnořeného typu, který vrací `insert_return_type`. Který návratový typ je nyní definována jako specializace typu, který je parametry na Iterator a NodeType kontejneru.

### <a name="inline-variables-for-the-stl"></a>Vložené proměnné pro STL

[P0607R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0607r0.html)

### <a name="annex-d-features-deprecated"></a>Příloha D funkce zastaralé

Příloha D C++ standard obsahuje všechny funkce, které jsou zastaralé, včetně `shared_ptr::unique()`, `<codecvt>`, a `namespace std::tr1`. Když **/std: c ++ 17** přepínače kompilátoru nastavena, téměř všechny funkce standardní knihovny v příloze D jsou označeny jako zastaralé. Další informace najdete v tématu [funkce standardní knihovny v příloze D jsou označeny jako zastaralé](#annex_d).

`std::tr2::sys` Oboru názvů v `<experimental/filesystem>` nyní vydá upozornění vyřazení pod **/std: c ++ 14** ve výchozím nastavení a je teď odebrané v části **/std: c ++ 17** ve výchozím nastavení.

Vylepšené shoda v iostreams vyhnout nestandardní rozšíření (explicitní specializací ve své třídě).

Standardní knihovna teď používá proměnné šablony interně.

Standardní knihovna se aktualizovalo v reakci na C ++ 17 změny v kompilátoru, včetně přidání noexcept systém typů a odebrání dynamické specifikace výjimek.

## <a name="improvements_156"></a>  Vylepšení v nástroji Visual Studio 2017 verze 15,6 operací

### <a name="c17-library-fundamentals-v1"></a>C ++ 17 knihovny základy V1

[P0220R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html) začleňuje technické specifikaci knihovny základy pro C ++ 17 do standardní. Obsahuje aktualizace \<experimentální nebo řazené kolekce členů >, \<experimentální, volitelné >, \<experimentální/funkční >, \<experimentální/libovolný >, \<experimentální/string_view >, \<experimentální či paměti >, \<experimentální/memory_resource >, a \<experimentální/algoritmus >.

### <a name="c17-improving-class-template-argument-deduction-for-the-stl"></a>C ++ 17 zlepšení třída odvození argumentu šablony pro STL

[P0739R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0739r0.html) přesunout `adopt_lock_t` dopředu seznam parametrů pro `scoped_lock` povolení konzistentní použití `scoped_lock`. Povolit `std::variant` konstruktor se účastnit rozlišení přetížení v případech, další, aby bylo možné kopírovat přiřazení.

## <a name="improvements_157"></a> Vylepšení v nástroji Visual Studio 2017 verze 15.7

### <a name="c17-rewording-inheriting-constructors"></a>C ++ 17 Rewording dědičných konstruktory

[P0136R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0136r1.html) Určuje, že **pomocí** prohlášení, že názvy konstruktor teď umožňuje odpovídající místo další deklarování odvozených základní třída konstruktory viditelné pro inicializacích odvozené třídy Třída konstruktory. Jedná se o změnu z C ++ 14. V aplikaci Visual Studio 2017 verze 15.7 a novější, v **/std: c ++ 17** režimu, kód, který je platný v C ++ 14 a použije dědění konstruktory nemusí být platný, nebo může mít různé sémantiku.

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

### <a name="c17-extended-aggregate-initialization"></a>C ++ 17 Extended inicializace agregace

[P0017R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0017r1.html)

Pokud je konstruktor základní třídy neveřejný, ale přístupné do odvozené třídy, pak v části **/std: c ++ 17** režimu v sadě Visual Studio verze 15.7 už můžete prázdný složené závorky k chybě při inicializaci objektu odvozeného typu.

Následující příklad ukazuje C ++ 14 vyhovující chování:

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

Součástí C ++ 17 `Derived` nyní považuje za agregace typu; proto inicializace `Base` prostřednictvím privátní výchozí konstruktor se stane přímo jako součást pravidla rozšířené inicializace agregace. Dříve `Base` soukromý konstruktor byla volána prostřednictvím `Derived` konstruktor a úspěšné kvůli friend deklaraci.

Následující příklad ukazuje C ++ 17 chování v sadě Visual Studio verzi 15.7 v **/std: c ++ 17** režimu:

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

### <a name="c17-declaring-non-type-template-parameters-with-auto"></a>C ++ 17 deklarovat bez typu parametry šablony s automatickým

[P0127R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r2.html)

V **/std: c ++ 17** režimu, kompilátor můžete nyní odvodit typ argumentu jiný typ šablony, který je deklarovaný s **automaticky**:

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

Jeden dopad tato nová funkce je, že platný C ++ 14 kód nemusí být platný, nebo může mít různé sémantiku. Některé přetížení, které byly dříve neplatné jsou například nyní platné. Následující příklad ukazuje C ++ 14 kód, který kompiluje, protože volání `foo(p)` je vázán k `foo(void*);`. V aplikaci Visual Studio 2017 verze 15.7 v **/std: c ++ 17** režimu, `foo` funkce šablona je nejlepší shodu.

```cpp
template <int N> struct A;
template <typename T, T N> int foo(A<N>*) = delete;

void foo(void *);

void bar(A<0> *p)
{
    foo(p); // OK in C++14
}
```

Následující příklad ukazuje C ++ 17 kódu ve Visual Studio 15.7 v **/std: c ++ 17** režimu:

```cpp
template <int N> struct A;
template <typename T, T N> int foo(A<N>*);

void foo(void *);

void bar(A<0> *p)
{
    foo(p); // C2280: 'int foo<int,0>(A<0>*)': attempting to reference a deleted function
}
```

### <a name="c17-elementary-string-conversions-partial"></a>C ++ 17 základní řetězec převody (částečné)

[P0067R5](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0067r5.html) nízké úrovně, národní prostředí nezávislé funkce pro převod mezi celá čísla a řetězce a mezi čísla s plovoucí desetinnou čárkou a řetězce. (Pro Visual Studio 15.7 Preview 2, pro jenom celá čísla podporována.)

### <a name="c20-avoiding-unnecessary-decay-partial"></a>C ++ 20 vyloučení nepotřebných decay (částečné)

[P0777R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0777r1.pdf) přidá rozlišovat konceptu "decay" a že jednoduše odebrání const nebo kvalifikátory odkaz.  Nový typ znak `remove_reference_t` nahrazuje `decay_t` v některých kontextech. Podpora pro `remove_cvref_t` ještě není implementováno od verze Visual Studio 2017 15.7 Preview 2.

### <a name="c17-parallel-algorithms"></a>C ++ 17 paralelní algoritmy

[P0024R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0024r2.html) The paralelismus TS je součástí standardní s menšími změnami.

### <a name="c17-hypotx-y-z"></a>C ++ 17 hypot – (x, y, z)

[P0030R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0030r1.pdf) přidá tři nové přetížení pro `std::hypot`, pro typy **float**, **dvojité**, a **long double**, z nichž každá má tři vstupní parametry.

### <a name="c17-filesystem"></a>C ++ 17 \<filesystem >

[P0218R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0218r1.html) přijme TS systému souborů do standard s pár slov úpravy.

### <a name="c17-mathematical-special-functions"></a>C ++ 17 matematické speciální funkce

[P0226R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html) přijme předchozí technických specifikací pro matematické speciální funkce do standardní \<cmath – > záhlaví.

### <a name="c17-deduction-guides-for-the-stl"></a>C ++ 17 odvození příručky pro STL

[P0433R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0433r2.html) aktualizace STL využívat výhod C ++ 17 přijetí [P0091R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html), který přidává podporu pro odvození argumentu šablony třídy.

### <a name="c17-repairing-elementary-string-conversions"></a>C ++ 17 opravu základní řetězec převody

[P0682R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0682r1.html) přesunutí nové funkce pro převod základní řetězce z P0067R5 do novou hlavičkou \<charconv > a dalších vylepšení, včetně změny zpracování chyb používat použití `std::errc` místo `std::error_code`.

### <a name="c17-constexpr-for-chartraits-partial"></a>C ++ 17 constexpr pro char_traits – (částečné)

[P0426R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0426r1.html) změny `std::traits_type` členské funkce `length`, `compare`, a `find` aby bylo možné provést `std::string_view` použitelné v konstantní výrazy. (Ve Visual Studio 2017 verze 15,6 operací, podporovaná Clang/LLVM jenom pro. Ve verzi Preview 15.7 2, podporu je téměř dokončena pro ClXX také)

## <a name="bug-fixes-in-visual-studio-versions-150-153update153-155update155-and-157update157"></a>Opravy chyb ve verzích sady Visual Studio 15.0, [15.3](#update_153), [15,5](#update_155), a [15.7](#update_157)

### <a name="copy-list-initialization"></a>Kopie – seznam – inicializace

Visual Studio 2017 správně vyvolá chyby kompilátoru vztahující se k vytvoření objektu pomocí inicializátoru seznamů, které nebyly provedeny v sadě Visual Studio 2015 a může způsobit selhání nebo modul runtime chování není definován. Podle N4594 13.3.1.7p1 v kopírování seznamu inicializace kompilátor je potřeba vzít v úvahu explicitní konstruktor pro rozlišení přetížení, ale musíte zvýšit chybu, pokud je ve skutečnosti vybrali této přetížení.

Následující dva příklady kompilovat v sadě Visual Studio 2015, ale není v Visual Studio 2017.

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

Chcete-li chybu opravit, použijte přímé inicializace:

```cpp
A a1{ 1 };
const A& a2{ 1 };
```

V sadě Visual Studio 2015 kompilátor chybnou informací považovat kopírování. seznam inicializace stejným způsobem jako regulární kopie inicializace; považuje za pouze převod konstruktory pro rozlišení přetížení. V následujícím příkladu Visual Studio 2015 zvolí MyInt(23) ale Visual Studio 2017 správně vyvolá chybu.

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

V tomto příkladu je podobný předchozímu, ale vyvolá jiné chybě. Je úspěšné v sadě Visual Studio 2015 a v aplikaci Visual Studio 2017 s C2668 selže.

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

### <a name="deprecated-typedefs"></a>Zastaralé definice TypeDef

Visual Studio 2017 nyní vydává správné upozornění pro zastaralé definice TypeDef, které jsou deklarované v třídě nebo struktuře. Následující příklad zkompiluje bez upozornění v sadě Visual Studio 2015, ale vytváří C4996 v Visual Studio 2017.

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

### <a name="constexpr"></a>constexpr

Visual Studio 2017 vyvolá chybu správně, je-li levé operand podmíněně vyhodnocování operace není platná v kontextu constexpr. Následující kód zkompiluje v sadě Visual Studio 2015, ale není v aplikaci Visual Studio 2017 (C3615 constexpr funkce 'f' nemůže mít za následek konstantní výraz):

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

Chcete-li k chybě, buď deklarovat `array::size()` fungovat jako `constexpr` nebo odebrat `constexpr` kvalifikátor z `f`.

### <a name="class-types-passed-to-variadic-functions"></a>Typy tříd, které se předají funkcím variadická

V aplikaci Visual Studio 2017 musí být trivially kopírovatelná třídy nebo struktury, která jsou předaný funkci variadická například printf. Při předávání tyto objekty, kompilátor jednoduše vytvoří bitové kopie a nevyvolá konstruktoru nebo destruktor.

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

Chcete-li chybu opravit, můžete zavolat členské funkce, která vrátí hodnotu typu trivially kopírovatelná

```cpp
    std::atomic<int> i(0);
    printf("%i\n", i.load());
```

jinak provést statické přetypování převést objekt před jeho odesláním:

```cpp
    struct S {/* as before */} s(0);
    printf("%i\n", static_cast<int>(s))
```

Pro řetězce vytvořené a spravují pomocí CStringW poskytnutého `operator LPCWSTR()` se má použít pro objekt CStringW na očekávaný řetězec formátu C ukazatele přetypování.

```cpp
CStringW str1;
CStringW str2;
str1.Format(L"%s", static_cast<LPCWSTR>(str2));
```

### <a name="cv-qualifiers-in-class-construction"></a>Kvalifikátory odchylka nákladů ve vytváření – třída

V sadě Visual Studio 2015 kompilátor někdy nesprávně ignoruje kvalifikátor odchylka nákladů při generování objektu třídy prostřednictvím volání konstruktoru. To může potenciálně způsobit havárie nebo neočekávané modul runtime chování. Následující příklad zkompiluje v sadě Visual Studio 2015, ale vyvolá chybu kompilátoru ve Visual Studio 2017:

```cpp
struct S
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```

Chcete-li k chybě, deklarovat `operator int()` jako `const`.

### <a name="access-checking-on-qualified-names-in-templates"></a>Probíhá kontrola v kvalifikované názvy v šablonách přístup

Předchozí verze kompilátoru nebyla provedena kontrola na kvalifikované názvy v některých kontextech šablony přístup. To může narušovat očekávané chování sfinae u výrazů, kde je očekávána nahrazování selhání kvůli inaccessibility názvu. To může potenciálně způsobit selhání nebo neočekávané chování za běhu z důvodu kompilátoru nesprávně volání nesprávný přetížení operátoru. V aplikaci Visual Studio 2017 je vyvolána chyba kompilátoru. Konkrétní chyba se může lišit, ale obvykle je to "C2672 neexistuje odpovídající přetížený funkce Najít". Následující kód zkompiluje v sadě Visual Studio 2015, ale vyvolá chybu v aplikaci Visual Studio 2017:

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

### <a name="missing-template-argument-lists"></a>Seznamy argumentů chybí šablony

V sadě Visual Studio 2015 a starší kompilátor není diagnostikovat seznamy argumentů chybí šablona šablony zobrazené v seznamu parametrů šablony (například jako součást výchozí šablonu argumentu nebo parametru šablony bez typu). To může způsobit nepředvídatelné chování, včetně dojde k chybě kompilátoru nebo neočekávané modul runtime chování. Následující kód zkompiluje v sadě Visual Studio 2015, ale vytváří chyby ve Visual Studio 2017.

```cpp
template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;
```

### <a name="expression-sfinae"></a>Výraz sfinae u výrazů

Pro podporu výraz sfinae u výrazů, kompilátor teď analyzuje decltype argumenty při šablony jsou deklarovaný místo vytvoření instance. V důsledku toho pokud nezávislých specializace najde v argumentu decltype, to není odložení času vytváření instancí a okamžitě zpracování a případné chyby jsou zjištěna v daném čase.

Následující příklad ukazuje takové chybu kompilátoru, která se vyvolá v místě deklarace:

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

### <a name="classes-declared-in-anonymous-namespaces"></a>Třídy, které jsou deklarované v anonymní obory názvů

Podle standard C++ třídu deklarovat uvnitř anonymní obor názvů má vnitřní propojení a proto nelze exportovat. V sadě Visual Studio 2015 a starší nebyl vynucuje toto pravidlo. V aplikaci Visual Studio 2017 pravidlo částečně vynucované. Následující příklad vyvolá této chyby ve Visual Studio 2017: "Chyba C2201: const anonymní namespace::S1::vftable: musí mít externí propojení, aby byla exportovat nebo importovat."

```cpp
struct __declspec(dllexport) S1 { virtual void f() {} }; //C2201
```

### <a name="default-initializers-for-value-class-members-ccli"></a>Výchozí inicializátory pro hodnotu třídy členové (C + +/ CLI)

V sadě Visual Studio 2015 a starší kompilátor povolené (ale ignoruje) inicializátoru výchozího člena pro člena třídy hodnotu. Výchozí inicializace – hodnotová třída vždy nula inicializuje členy; výchozí konstruktor není povoleno. Visual Studio 2017 vyvolávají výchozí člen inicializátory Chyba kompilátoru, jak je uvedeno v následujícím příkladu:

```cpp
value struct V
{
    int i = 0; // error C3446: 'V::i': a default member initializer
               // is not allowed for a member of a value class
};
```

### <a name="default-indexers-ccli"></a>Výchozí indexery (C + +/ CLI)

V sadě Visual Studio 2015 a starší kompilátor v některých případech misidentified výchozí vlastnost jako výchozí indexer. Bylo možné tento problém obejít, pomocí identifikátor `default` pro přístup k vlastnosti. Alternativní řešení, samotné se aktivovala problematické po `default` byla zavedena jako klíčové slovo v C ++ 11. Proto je v aplikaci Visual Studio 2017 byly opraveny chyby, které vyžaduje alternativní řešení a kompilátor nyní vyvolá chybu při `default` se používá pro přístup k výchozí vlastnost pro třídu.

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

V aplikaci Visual Studio 2017 se můžete dostat obě hodnoty vlastnosti podle názvu jejich:

```cpp
#using "class1.dll"

void f(ClassLibrary1::Class1 ^r1, ClassLibrary1::Class2 ^r2)
{
       r1->Value;
       r2->Value;
}
```

## <a name="update_153"></a> Opravy chyb v aplikaci Visual Studio 2017 verze 15.3

### <a name="calls-to-deleted-member-templates"></a>Volání odstraněného člena šablon

V předchozích verzích sady Visual Studio by nepodaří kompilátoru v některých případech vygeneruje chybu pro nedůvěryhodný volání odstraněného člena šablonu, která by jste potenciálně způsobila dojde k chybě za běhu. Následující kód vytvoří teď C2280, "'int S\<int >:: f\<int > (void)': Při pokusu o odkazu na funkci odstraněné":

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

Postup řešení chyby, deklarovat i jako `int`.

### <a name="pre-condition-checks-for-type-traits"></a>Předběžná podmínka kontroluje pro typové vlastnosti

Visual Studio 2017 verze 15.3 zlepšuje kontroly předběžné podmínky pro typové vlastnosti více striktně dodržovat standardní. Jeden takový kontrola je pro přiřadit. Následující kód vytvoří C2139 ve Visual Studio 2017 verze 15.3:

```cpp
struct S;
enum E;

static_assert(!__is_assignable(S, S), "fail"); // C2139 in 15.3
static_assert(__is_convertible_to(E, E), "fail"); // C2139 in 15.3
```

### <a name="new-compiler-warning-and-runtime-checks-on-native-to-managed-marshaling"></a>Nové upozornění kompilátoru a prostředí runtime kontroly v nativní spravované zařazování

Volání ze spravovaných funkcí na nativní funkce vyžaduje zařazování. Modul CLR provádí zařazování ale nerozumí sémantiku C++. Pokud předáte objekt nativní hodnotou, CLR buď volá konstruktor copy objektu nebo využívá přenos bitových bloků, které můžou způsobit nedefinované chování za běhu.

Kompilátor nyní vydává upozornění, pokud může vědět při kompilaci předaný objekt nativní s odstraněné konstruktor copy mezi nativní a spravovaná hranic podle hodnoty. Pro případy, ve kterých není známo kompilátoru v době kompilace, se vloží kontrolu běhového prostředí tak, že program volá `std::terminate` okamžitě nesprávně formátovaných zařazování v případech. Ve Visual Studio 2017 verze 15.3, následující kód vytvoří upozornění C4606 ""A": předání argumentů hodnotou mezi nativní a spravovaná hranic vyžaduje platný kopírovacího konstruktoru. V opačném případě modul runtime chování není definováno".

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
    f(A()); // This call from managed to native requires marshalling. The CLR doesn't understand C++ and uses BitBlt, which results in a double-free later.
}
```

Chcete-li chybu opravit, odeberte `#pragma managed` – direktiva označit volající jako nativní a zamezit tak zařazování.

### <a name="experimental-api-warning-for-winrt"></a>Experimentální upozornění rozhraní API pro WinRT

Rozhraní API WinRT, které jsou vydané pro experimentování a zpětné vazby jsou označených pomocí `Windows.Foundation.Metadata.ExperimentalAttribute`. Ve Visual Studio 2017 verze 15.3 kompilátor vytvoří upozornění C4698, pokud se setká s atribut. Jste již byla dekorované několik rozhraní API v předchozích verzích Windows SDK s atributem a volání tato rozhraní API nyní aktivovat toto upozornění kompilátoru. Novější sady Windows SDK atribut odebrat ze všech typů uvidíte, ale pokud používáte starší SDK, budete muset potlačit tato upozornění pro všechna volání uvidíte typy.

Následující kód vytvoří upozornění C4698: "" Windows:: úložiště:: IApplicationDataStatics2::GetForUserAsync, je pro zkušební účely pouze a mohou podléhat změnám nebo odebrání v budoucích aktualizací":

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

### <a name="out-of-line-definition-of-a-template-member-function"></a>--Line definice šablony členské funkce

Visual Studio 2017 verze 15.3 vytvoří chybu, pokud se setká s definici z přesahujících členské funkce šablony, který nebyl deklarován v třídě. Následující kód vytvoří nyní chyba C2039: 'f': není členem je ':

```cpp
struct S {};

template <typename T>
void S::f(T t) {} //C2039: 'f': is not a member of 'S'
```

Opravte chybu, přidejte deklaraci pro třídu:

```cpp
struct S {
    template <typename T>
    void f(T t);
};
template <typename T>
void S::f(T t) {}
```

### <a name="attempting-to-take-the-address-of-this-pointer"></a>Probíhá pokus o trvat adresu ukazatele "this"

V jazyce C++ `this` je prvalue typ ukazatel na X. Nelze převést na adresu `this` nebo navázat jej odkazu lvalue. V předchozích verzích sady Visual Studio kompilátor by umožňují toto omezení obejít provedením přetypování. Ve Visual Studio 2017 verze 15.3 kompilátor vytvoří chyba C2664.

### <a name="conversion-to-an-inaccessible-base-class"></a>Převod na nepřístupný základní třída

Visual Studio 2017 verze 15.3 vyvolá chybu při pokusu převést typ na základní třídu, která je nedostupná. Kompilátor nyní vyvolá "Chyba C2243: 'přetypování.: měl převod z *' do ' B *' existuje, ale je nedostupný". Následující kód je nesprávně vytvořen a může dojít k chybě za běhu. Kompilátor nyní vytvoří C2243, pokud se setká s kód takto:

```cpp
#include <memory>

class B { };
class D : B { }; // C2243. should be public B { };

void f()
{
   std::unique_ptr<B>(new D());
}
```

### <a name="default-arguments-are-not-allowed-on-out-of-line-definitions-of-member-functions"></a>Výchozí argumenty nejsou povoleny na mimo řádek definice členské funkce

Výchozí argumenty nejsou povoleny na--line definice členské funkce ve třídách šablony kompilátor vydá upozornění v části **/ projektovou**a závažná chyba pod **/ projektovou-**.

V předchozích verzích sady Visual Studio následující kód nesprávně formátovaných může potenciálně způsobit selhání modulu runtime. Visual Studio 2017 verze 15.3 vytvoří upozornění C5034: ' A\<T >:: f': definici z přesahujících člena třídy šablony nemůže mít výchozí argumenty:

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

### <a name="use-of-offsetof-with-compound-member-designator"></a>Použití offsetof – s označením složené člena

V aplikaci Visual Studio 2017 verze 15.3, pomocí `offsetof(T, m)` kde *m* je "složené člen označení" výsledkem upozornění, když kompilujete s **/horní** možnost. Následující kód je nesprávně vytvořen a může dojít k chybě za běhu. Visual Studio 2017 verze 15.3 vytváří "upozornění C4841: nestandardní rozšíření používané: označení složené člen v offsetof –":

```cpp
struct A {
   int arr[10];
};

// warning C4841: non-standard extension used: compound member designator in offsetof
constexpr auto off = offsetof(A, arr[2]);
```

Pokud chcete vyřešit kód, buď zakažte upozornění s pragma nebo změnit kód nechcete použít `offsetof`:

```cpp
#pragma warning(push)
#pragma warning(disable: 4841)
constexpr auto off = offsetof(A, arr[2]);
#pragma warning(pop)
```

### <a name="using-offsetof-with-static-data-member-or-member-function"></a>Offsetof – pomocí statických dat člena nebo – členská funkce

V aplikaci Visual Studio 2017 verze 15.3, pomocí `offsetof(T, m)` kde *m* odkazuje na členy statických dat nebo členem funkce dojde k chybě. Následující kód vytváří "Chyba C4597: není definována chování: offsetof – členská funkce"foo"u" a "Chyba C4597: není definována chování: offsetof – u statických dat člena"bar"":

```cpp
#include <cstddef>

struct A {
   int foo() { return 10; }
   static constexpr int bar = 0;
};

constexpr auto off = offsetof(A, foo);
constexpr auto off2 = offsetof(A, bar);
```

Tento kód má chybný formát a může dojít k chybě za běhu. Opravte chybu, změňte kód, který už vyvolání nedefinované chování. Toto je jiný přenositelností kód, který je zakázány na úrovni C++ standard.

### <a name="declspec"></a> Nové upozornění na declspec atributy

Ve Visual Studio 2017 verze 15.3, kompilátor už ignoruje atributy Pokud `__declspec(...)` je použit před `extern "C"` specifikaci propojení. Kompilátor by dříve, ignorovat atribut, který může mít dopad modulu runtime. Když **/horní** a **wdn** jsou nastavené možnosti, následující kód vytvoří "upozornění C4768: atributy __declspec před specifikaci propojení se ignorují":

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

Pokud chcete vyřešit upozornění, put nejprve extern "C":

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

Toto upozornění je vypnutá ve výchozím nastavení v 15.3, ale na ve výchozí 15,5 a jenom ovlivňuje kód kompilovat s **/horní** **wdn**.

### <a name="decltype-and-calls-to-deleted-destructors"></a>Destruktory odstranit decltype a volání

V předchozích verzích sady Visual Studio kompilátor nenajde při volání odstraněné destruktor došlo k chybě v kontextu výrazu přidruženého 'decltype'. Ve Visual Studio 2017 verze 15.3, následující kód vytváří "Chyba C2280: ' A\<T >:: ~ A(void)': Probíhá pokus o odkazu na funkci odstraněné":

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

### <a name="uninitialized-const-variables"></a>Neinicializovaný const proměnné

Visual Studio 2017 RTW verze obsahovala regrese, ve kterém C++ compiler by vystavovat Diagnostika Pokud proměnnou 'const' nebyl inicializován. Toto přepsání byl opraven v aplikaci Visual Studio 2017 verze 15.3. Následující kód nyní vytváří "upozornění C4132: 'Hodnota': const objekt by měl být inicializován":

```cpp
const int Value; //C4132
```

Opravte chybu, přiřaďte mu hodnotu na `Value`.

### <a name="empty-declarations"></a>Prázdný deklarace

Visual Studio 2017 verze 15.3 nyní upozorní na prázdný deklarace pro všechny typy, právě vestavěné typy. Následující kód nyní vyvolá upozornění úrovně 2 C4091 pro všechny čtyři deklarace:

```cpp
struct A {};
template <typename> struct B {};
enum C { c1, c2, c3 };

int;    // warning C4091 : '' : ignored on left of 'int' when no variable is declared
A;      // warning C4091 : '' : ignored on left of 'main::A' when no variable is declared
B<int>; // warning C4091 : '' : ignored on left of 'B<int>' when no variable is declared
C;      // warning C4091 : '' : ignored on left of 'C' when no variable is declared
```

Chcete-li odebrat upozornění, jednoduše okomentujte nebo odeberte prázdný deklarace. V případech, kde je záměrem zrušení s názvem objektu tak, aby měl vedlejším účinkem (například RAII) by měly mít název.

Upozornění je vyloučen pod **/Wv:18** a ve výchozím nastavení v části upozornění úrovně W2 zapnutý.

### <a name="stdisconvertible-for-array-types"></a>std::is_convertible pro typy polí

Předchozí verze kompilátoru zadali nesprávné výsledky pro [std::is_convertible](standard-library/is-convertible-class.md) pro typy polí. To vyžaduje knihovny zapisovateli za účelem zvláštní případ Microsoft Visual C++ compiler při použití `std::is_convertible<...>` typ znak. V následujícím příkladu statických vyhodnotí průchodu v dřívějších verzích sady Visual Studio, ale selhání v aplikaci Visual Studio 2017 verze 15.3:

```cpp
#include <type_traits>

using Array = char[1];

static_assert(std::is_convertible<Array, Array>::value);
static_assert(std::is_convertible<const Array, const Array>::value, "");
static_assert(std::is_convertible<Array&, Array>::value, "");
static_assert(std::is_convertible<Array, Array&>::value, "");
```

`std::is_convertible<From, To>` je vypočítána zjišťujeme, pokud definici pomyslná funkce je ve správném formátu:

```cpp
   To test() { return std::declval<From>(); }
```

### <a name="private-destructors-and-stdisconstructible"></a>Privátní destruktory a std::is_constructible

Předchozí verze kompilátoru ignorovány, zda byl destruktor privátní při rozhodování o výsledek [std::is_constructible](standard-library/is-constructible-class.md). Nyní je považuje za. V následujícím příkladu statických vyhodnotí průchodu v dřívějších verzích sady Visual Studio, ale selhání v aplikaci Visual Studio 2017 verze 15.3:

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

Privátní destruktory způsobit typu být není zkonstruovatelný. `std::is_constructible<T, Args...>` se počítá jako kdyby byly napsány následující prohlášení:

```cpp
   T obj(std::declval<Args>()...)
```

Toto volání znamená destruktor volání.

### <a name="c2668-ambiguous-overload-resolution"></a>C2668: Řešení přetížení nejednoznačný

Předchozí verze kompilátoru někdy se nepodařilo rozpoznat nejednoznačnosti, kdy se našel víc kandidáty prostřednictvím i pomocí deklarace a argument závislé vyhledávání. To může vést k chybě přetížení vybrána a neočekávané modul runtime chování. V následujícím příkladu, Visual Studio 2017 verze 15.3 správně vyvolá C2668 f: volání přetížené funkce nejednoznačný:

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

Chcete-li opravit kód, odeberte použití `N::f` příkaz, pokud byste chtěli volání `::f()`.

### <a name="c2660-local-function-declarations-and-argument-dependent-lookup"></a>C2660: deklarace funkcí Místní a závislé vyhledávací argument

Deklarace funkcí místní skrýt deklarace funkce ve vymezeném oboru a zakázat argument závislé vyhledávání. Předchozí verze kompilátoru však provést argument závislé vyhledávání v takovém případě by mohl vést k chybnou přetížení vybrána a neočekávané modul runtime chování. Obvykle je chyba z důvodu nesprávný podpis deklarace místní funkce. V následujícím příkladu, Visual Studio 2017 verze 15.3 správně vyvolá C2660 f: – funkce nemusí provádět žádné 2 argumenty:

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

Chcete-li problém vyřešit, buď změňte `f(S)` podpis nebo ji odeberte.

### <a name="c5038-order-of-initialization-in-initializer-lists"></a>C5038: pořadí inicializace v inicializační seznamy

Členy třídy jsou inicializovány v pořadí, ve kterém jsou deklarovány, není pořadí, ve kterém se zobrazují v inicializační seznamy. Předchozí verze kompilátoru není upozornit, když pořadí položek v seznamu inicializátoru lišil od pořadí deklarace. To může vést k nedefinované modul runtime chování, pokud se inicializace došlo k jedné člena závisí na druhý člen v seznamu již inicializován. V následujícím příkladu, Visual Studio 2017 verze 15.3 (s **/horní**) vyvolá "upozornění C5038: 'A::y' bude inicializován po – datový člen 'A::x' – datový člen":

```cpp
struct A
{
    A(int a) : y(a), x(y) {} // Initialized in reverse, y reused
    int x;
    int y;
};
```

Chcete-li problém vyřešit, uspořádejte seznamu intializer má stejné pořadí jako deklarací. Upozornění podobné se vyvolá, když jeden nebo oba inicializátory odkazovat na členy základní třídy.

Upozorňujeme, že toto upozornění je vypnuto výchozím a ovlivňuje pouze zkompilování kódu s **/horní**.

## <a name="update_155"></a> Opravy chyb a jiné změny chování ve Visual Studio 2017 verze 15,5

### <a name="partial-ordering-change"></a>Částečné řazení změn

Kompilátor nyní správně odmítne následující kód a poskytuje správnou chybovou zprávu:

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

Problém v předchozím příkladu je, že existují dva rozdíly v typy (const oproti bez const a pack oproti bez aktualizací Service pack). Chyba kompilátoru eliminovat, odeberte jeden z rozdíly. To umožňuje kompilátoru jednoznačně pořadí funkcí.

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

Obslužné rutiny odkazu na typ pole nebo funkce nejsou nikdy shoda pro libovolný objekt výjimky. Kompilátor nyní správně ctí toto pravidlo a vyvolá upozornění úrovně 4. Také již neodpovídá obslužnou rutinu `char*` nebo `wchar_t*` na řetězec v případě literálu **/Zc: strictstrings** se používá.

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

Následující kód zabraňuje Chyba:

```cpp
catch (int (*)[1]) {}
```

### <a name="tr1"></a>obor názvů std::tr1 je zastaralý.

Nestandardním `std::tr1` obor názvů je nyní označen jako zastaralý C ++ 14 a C ++ 17 režimy. Následující kód v aplikaci Visual Studio 2017 verze 15,5, vyvolá C4996:

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
warning C4996: 'std::tr1': warning STL4002: The non-Standard std::tr1 namespace and TR1-only machinery are deprecated and will be REMOVED. You can define _SILENCE_TR1_NAMESPACE_DEPRECATION_WARNING to acknowledge that you have received this warning.
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

### <a name="annex_d"></a>Funkce standardní knihovny v příloze D jsou označeny jako zastaralé

Když **/std: c ++ 17** přepínače kompilátoru režim je nastaven, téměř všechny funkce standardní knihovny v příloze D jsou označeny jako zastaralé.

Následující kód v aplikaci Visual Studio 2017 verze 15,5, vyvolá C4996:

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
warning C4996: 'std::iterator<std::random_access_iterator_tag,int,ptrdiff_t,_Ty*,_Ty &>::pointer': warning STL4015: The std::iterator class template (used as a base class to provide typedefs) is deprecated in C++17. (The <iterator> header is NOT deprecated.) The C++ Standard has never required user-defined iterators to derive from std::iterator. To fix this warning, stop deriving from std::iterator and start providing publicly accessible typedefs named iterator_category, value_type, difference_type, pointer, and reference. Note that value_type is required to be non-const, even for constant iterators. You can define _SILENCE_CXX17_ITERATOR_BASE_CLASS_DEPRECATION_WARNING or _SILENCE_ALL_CXX17_DEPRECATION_WARNINGS to acknowledge that you have received this warning.
```

Opravte chybu, postupujte podle pokynů v upozornění textu, jak je ukázáno v následujícím kódu:

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

### <a name="unreferenced-local-variables"></a>Neregistrované lokální proměnné

V aplikaci Visual Studio 15,5 upozornění C4189 vygenerované v další případy, jak je znázorněno v následujícím kódu:

```cpp
void f() {
    char s[2] = {0}; // C4189. Either use the variable or remove it.
}
```

```Output
warning C4189: 's': local variable is initialized but not referenced
```

Postup řešení chyby, odeberte nepoužívané proměnné.

### <a name="single-line-comments"></a>Jeden řádek komentáře

V aplikaci Visual Studio 2017 verze 15,5 jsou už upozornění C4001 a C4179 vygenerované kompilátorem C. Dříve byly jenom vygenerované v části **/Za** přepínače kompilátoru.  Upozornění už nejsou potřeba, protože jeden řádek komentáře byly součástí standardní od C99 C.

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

Pokud kód nemusí být zpětně kompatibilní, se můžete vyhnout upozornění odebráním C4001/C4179 potlačení. Pokud kód musí být zpětně kompatibilní, pak pouze potlačíte C4619.

```C

/* C only */

#pragma warning(disable:4619)
#pragma warning(disable:4001)
#pragma warning(disable:4179)

// single line comment
/* single line comment */
```

### <a name="declspec-attributes-with-extern-c-linkage"></a>atributy __declspec extern "C" propojení

V dřívějších verzích sady Visual Studio, kompilátor Ignorovat `__declspec(...)` atributy při `__declspec(...)` bylo použito před `extern "C"` specifikaci propojení. Toto chování způsobila kódu být vygenerována, která nebyla chcete uživatele s možné runtime důsledky. Upozornění byl přidán v sadě Visual Studio verze 15.3, ale byl ve výchozím nastavení vypnutý. V aplikaci Visual Studio 2017 verze 15,5 se ve výchozím nastavení zapnutá upozornění.

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

```Output
warning C4768: __declspec attributes before linkage specification are ignored
```

Chcete-li opravit chyby, umístěte specifikace propojení před atribut __declspec:

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

Toto nové upozornění C4768 je daný na některé hlavičky Windows SDK, které byly dodány s Visual Studio 2017 15.3 nebo starší (například: verze 10.0.15063.0, také známé jako RS2 SDK). Ale novější verze sady Windows SDK hlavičky (konkrétně ShlObj.h a ShlObj_core.h) bylo opraveno tak, aby nevedou toto upozornění. Když se zobrazí toto upozornění pocházející z Windows SDK hlavičky, můžete provést tyto akce:

1. Přepnout na nejnovější SDK Windows, k vydání verze 15,5 Visual Studio 2017.
2. Vypnout upozornění kolem #include příkaz hlavičky Windows SDK:

```cpp
   #pragma warning (push)
   #pragma warning(disable:4768)
   #include <shlobj.h>
   #pragma warning (pop)
   ```

### <a name="extern_linkage"></a>Extern constexpr propojení

V dřívějších verzích sady Visual Studio, kompilátor vždy Dal `constexpr` proměnné vnitřní propojení i v případě, že byla označena jako proměnnou `extern`. V aplikaci Visual Studio 2017 verze 15,5, nového přepínače kompilátoru (**/Zc:externConstexpr**) umožňuje správné chování podle standardů. Nakonec stane výchozí.

```cpp
extern constexpr int x = 10;
```

```Output
error LNK2005: "int const x" already defined
```

Pokud soubor hlaviček obsahuje proměnná definovaná `extern constexpr`, je nutné označit `__declspec(selectany)` aby bylo možné správně používat jeho duplicitní deklarace kombinaci:

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

### <a name="typeid-cant-be-used-on-incomplete-class-type"></a>typeid nelze použít na typ nedokončené – třída

V dřívějších verzích sady Visual Studio kompilátor nesprávně povoleny následující kód, což vede k potenciálně nesprávný typ informace. V aplikaci Visual Studio 2017 verze 15,5 kompilátor správně vyvolá chybu:

```cpp
#include <typeinfo>

struct S;

void f() { typeid(S); } //C2027 in 15.5
```

```Output
error C2027: use of undefined type 'S'
```

### <a name="stdisconvertible-target-type"></a>std::is_convertible cílový typ.

`std::is_convertible` vyžaduje typ cíle jako platný návratový typ. V dřívějších verzích sady Visual Studio kompilátor nesprávně povolená abstraktní typy, které může vést k nesprávné přetížení řešení a neúmyslné modul runtime chování.  Následující kód nyní správně vyvolá C2338:

```cpp
#include <type_traits>

struct B { virtual ~B() = 0; };
struct D : public B { virtual ~D(); };

static_assert(std::is_convertible<D, B>::value, "fail"); // C2338 in 15.5
```

Abyste se vyhnuli chybě, při použití `is_convertible` byste měli porovnat typy ukazatelů, protože ukazatel typu porovnání může selhat, pokud je jeden typ abstraktní:

```cpp
#include <type_traits>

struct B { virtual ~B() = 0; };
struct D : public B { virtual ~D(); };

static_assert(std::is_convertible<D *, B *>::value, "fail");
```

### <a name="noexcept_removal"></a> Odebrání specifikace dynamické výjimky a noexcept

Součástí C ++ 17 `throw()` je alias `noexcept`, `throw(<type list>)` a `throw(...)` se odeberou, a můžou obsahovat určité typy `noexcept`. To může způsobit problémy s kompatibilitou zdroje s kódem, který vyhovuje C ++ 14 nebo dřívější. **/Zc:noexceptTypes-** se vrátit k C ++ 14 verze lze použít přepínač `noexcept` při použití C ++ 17 režim obecně. To vám umožní aktualizovat vašeho zdrojového kódu tak, aby odpovídala C ++ 17 bez přepsání všechny vaše `throw()` kódu ve stejnou dobu.

Kompilátor diagnostikuje nyní také další specifikace neodpovídající výjimek v deklaracích v C ++ 17 režimu nebo s **/ projektovou-** pomocí nového upozornění C5043.

Následující kód vygeneruje C5043 a C5040 Visual Studio 2017 verze 15,5 při **/std: c ++ 17** přepínač platí:

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

Odebrat chyby při použití stále **/std: c ++ 17**, přidejte **/Zc:noexceptTypes-** přepnout na příkazový řádek, jinak aktualizujte kód a použít `noexcept`, jak je znázorněno v následujícím příkladu:

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

Datové členy statických constexpr jsou nyní implicitně vložené, což znamená, že jejich deklarace v rámci třídy je nyní jejich definice. Použití definici z přesahujících pro člena statické constexpr dat je redundantní a nyní zastaralé. V aplikaci Visual Studio 2017 verze 15,5 při **/std: c ++ 17** použijí přepínače, následující kód vytvoří nyní upozornění C5041 *'size':--line definice pro constexpr statických dat člena není potřebné a je zastaralá součástí C ++ 17*:

```cpp
struct X {
    static constexpr int size = 3;
};
const int X::size; // C5041
```

### <a name="extern-c-declspec-warning-c4768-now-on-by-default"></a>extern "C" __declspec(...) upozornění C4768 nyní na ve výchozím nastavení

Toto upozornění se přidal ve Visual Studio 2017 verze 15.3, ale byl vypnutý ve výchozím nastavení. Ve Visual Studio 2017 verze 15,5 je ve výchozím nastavení zapnutý. V tématu [nové upozornění na atributy declspec](#declspec) Další informace.

### <a name="defaulted-functions-and-declspecnothrow"></a>Uvedena funkce a __declspec(nothrow)

Kompilátor dříve povolen uvedena funkce deklarovat s `__declspec(nothrow)` při odpovídající základní nebo členské funkce povolené výjimky. Toto chování je rozporu s touto C++ Standard a může způsobit nedefinované chování za běhu. Standardní vyžaduje takové funkce být definován jako odstranit, pokud existuje neshoda specifikace k výjimce.  V části **/std: c ++ 17**, následující kód vyvolá C2280 *pokus o odkazu na funkci odstraněné. Funkce byla implicitně odstraněna, protože není kompatibilní s který implicitní deklarace specifikace explicitní výjimka.* :

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

Chcete-li tento kód, buď odeberte __declspec(nothrow) z uvedena funkce, nebo odeberte `= default` a zadejte definici funkce společně s všechny požadované výjimek:

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

### <a name="noexcept-and-partial-specializations"></a>noexcept a částečné specializací

S noexcept v systému typu částečné specializací pro odpovídající konkrétní typy "s" se pravděpodobně nepodaří kompilovat, nebo zvolte primární šablonu z důvodu chybějící částečná specializace ukazatele na noexcept funkcí.

V takových případech musíte přidat další částečné specializací pro zpracování ukazatelů na funkce noexcept a noexcept ukazatele na členské funkce. Tato přetížení jsou jenom právní v **/std: c ++ 17** režimu. Pokud musí být zachovaná zpětné kompatibility s C ++ 14 a psaní kódu, který ostatní využívat, pak by měla chránit tyto nové přetížení uvnitř `#ifdef` direktivy. Pokud pracujete v samostatný modul, a potom místo použití `#ifdef` chrání pouze můžete zkompilovat s **/Zc:noexceptTypes-** přepínače.

Následující kód zkompiluje pod **/std: c ++ 14** ale selže v části **/std: c ++ 17** s "chybu nedefinované typu C2027:use ' A\<T >" ":

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

Následující kód následuje v **/std: c ++ 17** protože kompilátor vybere nový částečná specializace `A<void (*)() noexcept>`:

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

## <a name="update_157"></a> Opravy chyb a jiné změny chování ve Visual Studio 2017 verze 15.7

### <a name="c17-default-argument-in-the-primary-class-template"></a>C ++ 17 výchozí argument v šabloně primární – třída

Tato změna chování je předpokladem pro [odvození argumentu šablony pro šablony třídy - P0091R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html), která je plánovaná plně podporovaný v novější náhled Visual Studio 2017 verze 15.7.

Dříve kompilátor ignorovat argument výchozí v šabloně primární třídou.

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int = 0) {} // Re-definition necessary
```

V **/std: c ++ 17** režimu ve Visual Studio 2017 verze 15.7, výchozí argument není ignorovány:

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int) {} // Default argument is used
```

### <a name="dependent-name-resolution"></a>Závislé překlad

Tato změna chování je předpokladem pro [odvození argumentu šablony pro šablony třídy - P0091R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html), která je plánovaná plně podporovaný v novější náhled Visual Studio 2017 verze 15.7.

V následujícím příkladu se přeloží kompilátoru Visual Studio 15,6 operací a starší `D::type` k `B<T>::type` v šabloně primární třídou.

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

Visual Studio 2017 verze 15.7, v **/std: c ++ 17** režim, vyžaduje, aby `typename` – klíčové slovo v `using` příkaz v D. Bez `typename` kompilátor vyvolá upozornění C4346: *' B < T\*>:: typu ': závislé název není typu* a chyba C2061: *Chyba syntaxe: identifikátor "typ"*:

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

### <a name="c17-nodiscard-attribute---warning-level-increase"></a>C ++ 17 [[nodiscard]] atribut - upozornění zvýšení úrovně

Ve verzi Visual Studio 2017 15.7 v **/std: c ++ 17** režimu, úroveň pro upozornění C4834 ("zahození návratová hodnota funkce s atributem 'nodiscard'") je zvýšena z W3 na W1. Můžete zakázat upozornění s přetypování na `void`, nebo pomocí předání **/wd:4834** kompilátoru

```cpp
[[nodiscard]] int f() { return 0; }

int main() {
    f(); // warning: discarding return value
         // of function with 'nodiscard'
}
```

### <a name="variadic-template-constructor-base-class-initialization-list"></a>Variadické šablony konstruktor základní třída Inicializace seznamu

V předchozích vydáních sady Visual Studio variadické šablony konstruktor základní třída Inicializace seznamu, který chyběl šablony argumenty povolilo chybnou informací bez chyby. V aplikaci Visual Studio 2017 verze 15.7 je vyvolána chyba kompilátoru.

Následující příklad kódu ve Visual Studio 2017 verze 15.7 vyvolá *chyba C2614: D\<int >: Neplatný člen inicializace: "B" není základní nebo člen*

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

Postup řešení chyby, změňte výraz B() b\<T > ().

## <a name="see-also"></a>Viz také

[Shoda jazyka Visual C++](visual-cpp-language-conformance.md)
