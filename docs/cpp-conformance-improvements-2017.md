---
title: "Vylepšení shoda C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8c0fe11f502fbfedda226e1d699a2822bdfd676a
ms.sourcegitcommit: 78f3f8208d49b7c1d87f4240f4a1496b7c29333e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/17/2017
---
# <a name="c-conformance-improvements-in-visual-studio-2017-versions-150-153improvements153-and-155improvements155"></a>Vylepšení shoda C++ verze Visual Studio 2017 15.0, [15.3](#improvements_153) a [15,5](#improvements_155).


Podpora pro zobecněný constexpr a NSDMI pro agregace kompilátor je u konce pro funkce přidané do C ++ 14 Standard. Mějte na paměti, že v kompilátoru stále chybí několik funkcí ze standardů C++11 a C++98. V tématu [přizpůsobení jazyka Visual C++](visual-cpp-language-conformance.md) pro tabulku, která se zobrazuje aktuální stav kompilátoru.

## <a name="c11"></a>C ++ 11
**Výraz sfinae u výrazů podporovat v dalších knihoven** – kompilátor Visual C++ nadále zlepšit jeho podporu pro výraz sfinae u výrazů, což je vyžadováno pro odvození argumentu šablony a nahrazení, kde může výrazy decltype a constexpr se zobrazí jako Parametry šablony. Další informace najdete v tématu [vylepšení výraz sfinae u výrazů v sadě Visual Studio 2017 RC](https://blogs.msdn.microsoft.com/vcblog/2016/06/07/expression-sfinae-improvements-in-vs-2015-update-3). 


## <a name="c-14"></a>C++ 14
**NSDMI pro agreguje** agregace je pole nebo třídy nebyl zadaný uživatelem konstruktor, žádné datové nestatické soukromé nebo chráněné členy, žádné základní třídy a bez virtuální funkce. Od verze C ++ 14 agregace může obsahovat inicializátory člen. Další informace najdete v tématu [inicializátory člen a agreguje](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3605.html).

**Rozšířené constexpr** výrazy deklarován jako constexpr nyní mohou obsahovat určité typy deklarací, je-li a přepínače příkazy, příkazy smyčky a mutace objekty, jejichž doba platnosti začal v rámci vyhodnocení výrazu constexpr. Navíc se již požadavek, aby se implicitně const nestatické členské funkce constexpr. Další informace najdete v tématu [uvolnit omezení na constexpr funkce](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3652.html). 

## <a name="c17"></a>C ++ 17
**Ve formátu Terse zasílaná static_assert** (k dispozici/std: c ++ 17) C ++ 17 parametr zpráva pro static_assert je volitelné. Další informace najdete v tématu [Extending static_assert, v2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3928.pdf). 

**[[fallthrough]] atribut** (k dispozici/std: c ++ 17) v kontextu příkazů přepínače se jako nápovědu pro kompilátor, že je určený chování patří prostřednictvím použit atribut [[fallthrough]]. Kompilátor zabrání vydání upozornění v takových případech. Další informace najdete v tématu [formulaci pro atribut [[fallthrough]]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0188r0.pdf). 

**Zobecněn na základě rozsahu smyčky for** (žádný kompilátoru přepínač vyžaduje) na základě rozsahu pro smyčky už nevyžadují, aby begin() a end() vrátí objekty stejného typu. To umožňuje end() vrátit sentinel jako použít podle rozsahů v [rozsah v3](https://github.com/ericniebler/range-v3) a dokončit, ale není – konce publikován technických specifikací rozsahy. Další informace najdete v tématu [generalizací založený na rozsahu pro smyčky](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html). 

## <a name="improvements_153"></a>Vylepšení v nástroji Visual Studio 2017 verze 15.3

**constexpr lambdas** výrazy Lambda může být použit v konstantní výrazy. Další informace najdete v tématu [Constexpr Lambda](http://open-std.org/JTC1/SC22/WG21/docs/papers/2015/n4487.pdf).

**Pokud constexpr v šablonách funkce** šablonu funkce může obsahovat `if constexpr` příkazy umožňující vytvoření větve kompilaci. Další informace najdete v tématu [Pokud constexpr](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0128r1.html).

**Příkazy výběru s inicializátory** `if` příkaz může zahrnovat inicializátoru zavádí proměnné v oboru bloku v rámci příkazu sám sebe. Další informace najdete v tématu [příkazy výběru s inicializátoru](http://www.open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0305r1.html).

**[[maybe_unused]] a [[nodiscard]] atributy** nové atributy ticho upozornění, když se nepoužívá entity, nebo vytvořte upozornění, pokud budou zahozeny vrácené hodnoty volání funkce. Další informace najdete v tématu [formulaci pro atribut maybe_unused](http://open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0212r0.pdf) a [návrh nevyužité, nodiscard a fallthrough atributů](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0068r0.pdf).

**Použití oboru názvů atribut bez opakování** nové syntaxe Povolit jenom identifikátor jeden obor názvů v seznamu atributů. Další informace najdete v tématu [atributy v jazyce C++](cpp/attributes2.md).

**Strukturovaná vazby** je nyní možné v jediné deklaraci uložit hodnotu s jednotlivé názvy pro součásti své při hodnota pole, std::tuple nebo std::pair nebo má všechny veřejná data nestatické členy. Další informace najdete v tématu [strukturovaných vazby](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0144r0.pdf).

**Vytváření pravidel pro příkaz enum třídy hodnoty** je nyní převod implicitní nebo jiných zužující z podkladovým typem výčtu oboru na výčtu samostatně, když jeho definice zavádí žádné enumerátor a používá zdroje Inicializace seznamu syntaxe. Další informace najdete v tématu [vytváření pravidel pro příkaz enum třídy hodnoty ](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0138r2.pdf).

**Zaznamenání *tím, že hodnota**  "\*to" objekt ve výrazu lambda mohou být zachyceny teď hodnotou. To umožňuje scénáře, ve kterých bude volána argument lambda v paralelní a asynchronní operace, zejména u novější architektury počítačů. Další informace najdete v tématu [Lambda zaznamenat z \*to podle hodnoty jako [=,\*to]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0018r3.html).

**Odebírání operator ++ pro bool** operator ++ již není podporována na `bool` typy. Další informace najdete v tématu [odebrat zastaralé operator++(bool)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0002r1.html).

**Odebrání zastaralé "register" – klíčové slovo** `register` – klíčové slovo, dříve zastaralé (a ignorovat Visual C++ compiler), je teď odebrané z jazyka. Další informace najdete v tématu [odebrat zastaralé použití register – klíčové slovo](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0001r1.html).

Úplný seznam vylepšení shoda se prostřednictvím Visual Studio 2015 Update 3 najdete v části [Visual C++ Co je nového 2003 až 2015](https://msdn.microsoft.com/en-us/library/mt723604.aspx).

## <a name="improvements_155"></a>Vylepšení v nástroji Visual Studio 2017 verze 15,5
Funkce, které jsou označené jako [14] jsou k dispozici bezpodmínečně i v/std: c ++ 14 režimu.

**Nový přepínač kompilátoru pro extern constexpr** v dřívějších verzích sady Visual Studio, kompilátor vždy Dal `constexpr` proměnné vnitřní propojení i v případě, že byla označena jako proměnnou `extern`. V aplikaci Visual Studio 2017 verze 15,5 nového přepínače kompilátoru [/Zc:externConstexpr](build/reference/zc-externconstexpr.md), umožňuje správné chování podle standardů. Další informace najdete v tématu [extern constexpr propojení](#extern_linkage).

**Odebrání specifikace výjimek dynamické**: [P0003R5](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html). Specifikace výjimek dynamické byla zrušena v C ++ 11. Tato funkce se odebere z C ++ 17, ale nepoužívá (stále) `throw()` specifikace se uchovávají výhradně jako alias pro `noexcept(true)`. Další informace najdete v tématu [odebrání specifikace dynamické výjimky a noexcept](#noexcept_removal). 

**not_fn()** : [P0005R4](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0005r4.html) náhrada not1 – a not2 – není dostupná.

**Rozdělit enable_shared_from_this**: [P0033R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0033r1.html) `enable_shared_from_this` se přidal ve C ++ 11. C ++ 17 Standard aktualizuje specifikace pro lepší zpracování určitých případech rohu. [14]

**Splétání mapy a nastaví**: [P0083R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf). Tato funkce umožňuje extrakce uzlů z asociativní kontejnery (například mapy, sady, unordered_map, unordered_set), které se pak dají upravit a vložit zpět do kontejneru stejný nebo jiný kontejner, který používá stejný typ uzlu. (Běžné případ použití je rozbalte uzel z std::map, změňte klíč a znovu vložit.)

**Místo začne Vestigial knihovny částí**: [P0174R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0174r2.html). Několik funkcí standardní knihovně C++ bylo nahrazeno funkcemi novější průběhu let, jinak byly zjištěny být velmi užitečná nebo způsobovat problémy. Tyto funkce jsou zastaralé oficiálně součástí C ++ 17. 

**Odebrání Allocator podpory v std::function**: [P0302R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0302r1.html). Před C ++ 17 šablona třídy `std::function` měl několik konstruktorů, které trvalo allocator argument. Ale použití alokátorů v tomto kontextu byl problematická a sémantiky byly jasné. Proto tyto contructors byly odebrány.

**Opravy pro not_fn()**: [P0358R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0358r1.html). Pro nové formulaci `std::not_fn` poskytuje podporu šíření kategorie hodnota v případě vyvolání obálku.

**shared_ptr < T [] >, < T [N] > shared_ptr**: [P0414R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0414r2.html). Slučování shared_ptr změny z knihovny Základy C ++ 17. [14]

**Oprava shared_ptr pro pole**: [P0497R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0497r0.html). Opravy pro podporu shared_ptr pro pole. [14]

**Insert_return_type, které toto vyjasňují**: [P0508R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0508r0.html). Členské funkce mají asociativní kontejnery s jedinečné klíče a neuspořádaného kontejnery s jedinečné klíče `insert` vnořeného typu, který vrací `insert_return_type`. Který návratový typ je nyní definována jako specializace typu, který je parametry na Iterator a NodeType kontejneru. 

**Vložené proměnné pro STL**: [P0607R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0607r0.html). 

**Příloha D funkce zastaralé** přílohy D standardní C++ obsahuje všechny funkce, které jsou zastaralé, včetně `shared_ptr::unique()`, `<codecvt>`, a `namespace std::tr1`. Když / std: c ++ 17 přepínače kompilátoru nastavena, téměř všechny funkce standardní knihovny v příloze D jsou označeny jako zastaralé. Další informace najdete v tématu [funkce standardní knihovny v příloze D jsou označeny jako zastaralé](#annex_d).

`std::tr2::sys` Oboru názvů v `<experimental/filesystem>` nyní vydá upozornění vyřazení pod/std: c ++ 14 ve výchozím nastavení a je teď odebrané pod/std: c ++ 17 ve výchozím nastavení.

Vylepšené shoda v iostreams vyhnout nestandardní rozšíření (explicitní specializací ve své třídě).

Standardní knihovna teď používá proměnné šablony interně.

Standardní knihovna se aktualizovalo v reakci na C ++ 17 změny v kompilátoru, včetně přidání noexcept systém typů a odebrání dynamické specifikace výjimek.

## <a name="bug-fixes-in-visual-studio-versions-150-153update153-and-155update155"></a>Opravy chyb ve verzích sady Visual Studio 15.0, [15.3](#update_153), a [15,5](#update_155)
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
Chcete-li k chybě, deklarovat pole:: size() funkce jako constexpr nebo odeberte kvalifikátor constexpr z f. 

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
                        // as an argument to a variadic function
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
Chcete-li k chybě, deklarujte operátor int() jako const. 

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
Pro podporu výraz sfinae u výrazů, kompilátor teď analyzuje decltype argumenty při šablony jsou deklarovaný místo vytvoření instance. V důsledku toho pokud nezávislých specializace najde v argumentu decltype, je termín, vytváření instancí čas a bude zpracován okamžitě a případné chyby bude zjištěna v daném čase.  

Následující příklad ukazuje takové chybu kompilátoru, která se vyvolá v místě deklarace:

```cpp  
#include <utility>
template <class T, class ReturnT, class... ArgsT> class IsCallable
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
V sadě Visual Studio 2015 a starší kompilátor v některých případech misidentified výchozí vlastnost jako výchozí indexer. Bylo možné tento problém obejít, na základě identifikátoru "Výchozí" pro přístup k vlastnosti. Alternativní řešení, samotné se stala problematické po výchozí zavedl jako klíčové slovo v C ++ 11. Proto je ve Visual Studio 2017 byly opraveny chyby, které vyžaduje alternativní řešení a kompilátor nyní vyvolá chybu, pokud "Výchozí" se používá pro přístup k výchozí vlastnost pro třídu.

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

## <a name="update_153"></a>Opravy chyb v aplikaci Visual Studio 2017 verze 15.3
### <a name="calls-to-deleted-member-templates"></a>Volání odstraněného člena šablon
V předchozích verzích sady Visual Studio by nepodaří kompilátoru v některých případech vygeneruje chybu pro nedůvěryhodný volání odstraněného člena šablonu, která by jste potenciálně způsobila dojde k chybě za běhu. Následující kód vytvoří teď C2280, "'int S<int>:: f<int>(void)': Při pokusu o odkazu na funkci odstraněné":
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
Volání ze spravovaných funkcí na nativní funkce vyžaduje zařazování. Modul CLR provádí zařazování ale nerozumí sémantiku C++. Pokud předáte objekt nativní hodnotou, CLR bude volat konstruktor copy objektu nebo použijte přenos bitových bloků, které můžou způsobit nedefinované chování za běhu. 
 
Kompilátor teď bude posílat upozornění, pokud může vědět při kompilaci předaný objekt nativní s odstraněné konstruktor copy mezi nativní a spravovaná hranic podle hodnoty. Pro případy, ve kterých není známo kompilátoru v době kompilace ji vložit kontrolu běhového prostředí tak, aby program zavolá std::terminate okamžitě dojde zařazování nedůvěryhodný. Ve Visual Studio 2017 verze 15.3, následující kód vytvoří C4606 ""A": předání argumentů hodnotou mezi nativní a spravovaná hranic vyžaduje platný kopírovacího konstruktoru. V opačném případě modul runtime chování není definováno".
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
    f(A()); // This call from managed to native requires marshalling. The CLR doesn't understand C++ and uses BitBlt, which will result in a double-free later. 
}
```
Chcete-li chybu opravit, odeberte `#pragma managed` – direktiva označit volající jako nativní a zamezit tak zařazování. 

### <a name="experimental-api-warning-for-winrt"></a>Experimentální upozornění rozhraní API pro WinRT
Rozhraní API WinRT, které jsou vydané pro experimentování a zpětné vazby bude označených pomocí `Windows.Foundation.Metadata.ExperimentalAttribute`. Ve Visual Studio 2017 verze 15.3 kompilátor vygeneruje upozornění C4698 Pokud se setká s atribut. Jste již byla dekorované několik rozhraní API v předchozích verzích Windows SDK s atributem a volání tato rozhraní API se spustí, která aktivuje upozornění kompilátoru. Novější sady Windows SDK bude mít atribut odebrat ze všech typů uvidíte, ale pokud používáte starší SDK, budete muset potlačit tato upozornění pro všechna volání uvidíte typy.
Následující kód vytvoří upozornění C4698: "" Windows:: úložiště:: IApplicationDataStatics2::GetForUserAsync, je pro zkušební účely pouze a mohou podléhat změnám nebo odebrání v budoucích aktualizací":
```cpp
Windows::Storage::IApplicationDataStatics2::GetForUserAsync() //C4698
```

Chcete-li zakázat upozornění, přidejte #pragma:

```cpp
#pragma warning(push) 
#pragma warning(disable:4698) 
 
Windows::Storage::IApplicationDataStatics2::GetForUserAsync() 
 
#pragma warning(pop)
```
### <a name="out-of-line-definition-of-a-template-member-function"></a>--Line definice šablony členské funkce 
**Visual Studio 2017 verze 15.3** vytvoří chybu, pokud se setká s definici z přesahujících členské funkce šablony, který nebyl deklarován v třídě. Následující kód vytvoří nyní chyba C2039: 'f': není členem je ':

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
V jazyce C++ 'to je prvalue typ ukazatel na X. Nelze provést na adresu 'this' nebo navázat jej odkazu lvalue. V předchozích verzích sady Visual Studio kompilátor by umožňují toto omezení obejít provedením přetypování. Ve Visual Studio 2017 verze 15.3 kompilátor vytvoří chyba C2664.

### <a name="conversion-to-an-inaccessible-base-class"></a>Převod na nepřístupný základní třída
**Visual Studio 2017 verze 15.3** vytvoří chybu při pokusu převést typ na základní třídu, která je nedostupná. Kompilátor nyní vyvolá "Chyba C2243: 'přetypování.: měl převod z *' do ' B *' existuje, ale je nedostupný". Následující kód je nesprávně vytvořen a může dojít k chybě za běhu. Kompilátor nyní vytvoří C2243, pokud se setká s kód takto:

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
Výchozí argumenty nejsou povoleny na definice členské funkce tříd šablon kompilátor vydá upozornění v části / projektovou a pevný / došlo k chybě v části projektovou--line-. 

V předchozích verzích sady Visual Studio následující kód nesprávně formátovaných může potenciálně způsobit selhání modulu runtime. Visual Studio 2017 verze 15.3 vytvoří upozornění C5034: ' A<T>:: f': definici z přesahujících člena třídy šablony nemůže mít výchozí argumenty:
```cpp
 
template <typename T> 
struct A { 
    T f(T t, bool b = false); 
}; 
 
template <typename T> 
T A<T>::f(T t, bool b = false) // C5034
{ 
... 
}
```
Chcete-li opravit chyby, odeberte výchozí argument "= false". 

### <a name="use-of-offsetof-with-compound-member-designator"></a>Použití offsetof – s označením složené člena
Ve Visual Studio 2017 verze 15.3 pomocí offsetof – (T, m), kde m je "složené člen označení" bude výsledkem upozornění při kompilaci s parametrem /Wall. Následující kód je nesprávně vytvořen a může dojít k chybě za běhu. Visual Studio 2017 verze 15.3 vytváří "upozornění C4841: nestandardní rozšíření používané: označení složené člen v offseto":

```cpp
  
struct A { 
int arr[10]; 
}; 
 
// warning C4841: non-standard extension used: compound member designator in offsetof 
constexpr auto off = offsetof(A, arr[2]);
```
Pokud chcete vyřešit kód, zakažte upozornění s pragma nebo změnit kód nechcete použít offsetof –: 

```cpp
#pragma warning(push) 
#pragma warning(disable: 4841) 
constexpr auto off = offsetof(A, arr[2]); 
#pragma warning(pop) 
```

### <a name="using-offsetof-with-static-data-member-or-member-function"></a>Offsetof – pomocí statických dat člena nebo – členská funkce
V aplikaci Visual Studio 2017 verze 15.3, pomocí offsetof – (T, m) kde m odkazuje na člena, statických dat nebo členské funkce bude mít za následek chybu. Následující kód vytváří "Chyba C4597: není definována chování: offsetof – členská funkce"foo"u" a "Chyba C4597: není definována chování: offsetof – u statických dat člena"bar"":
```cpp
 
#include <cstddef> 
 
struct A { 
int foo() { return 10; } 
static constexpr int bar = 0; 
}; 
 
constexpr auto off = offsetof(A, foo); 
Constexpr auto off2 = offsetof(A, bar);
```
 
Tento kód má chybný formát a může dojít k chybě za běhu. Opravte chybu, změňte kód, který už vyvolání nedefinované chování. Toto je jiný přenositelností kód, který je zakázány na úrovni C++ standard.

### <a name="declspec"></a>Nové upozornění na declspec atributy
Ve Visual Studio 2017 verze 15.3 kompilátor už ignoruje atributy, pokud __declspec(...) je použit před specifikaci propojení extern "C". Dřív by kompilátor ignorovat attritbute, které by mohly mít dopad modulu runtime. Když `/Wall /WX` je možnost nastavena, následující kód vytvoří "upozornění C4768: atributy __declspec před specifikaci propojení se ignorují":

```cpp
 
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

Pokud chcete vyřešit upozornění, put nejprve extern "C":

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```
Toto upozornění je vypnuto výchozím (na ve výchozím nastavení v 15,5) a ovlivní jenom zkompilování kódu s `/Wall /WX`.

### <a name="decltype-and-calls-to-deleted-destructors"></a>Destruktory odstranit decltype a volání
V předchozích verzích sady Visual Studio kompilátor nenajde při volání odstraněné destruktor došlo k chybě v kontextu výrazu přidruženého 'decltype'. Ve Visual Studio 2017 verze 15.3, následující kód vytváří "Chyba C2280: ' A<T>:: ~ A(void)': Probíhá pokus o odkazu na funkci odstraněné":

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
**Visual Studio 2017 verze 15.3** nyní upozorní na prázdný deklarace pro všechny typy, právě vestavěné typy. Následující kód nyní vyvolá upozornění úrovně 2 C4091 pro všechny čtyři deklarace:

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
 
Upozornění je vyloučena pod /Wv:18 a ve výchozím nastavení v části upozornění úrovně W2 zapnutý.


### <a name="stdisconvertible-for-array-types"></a>std::is_convertible pro typy polí
Předchozí verze kompilátoru zadali nesprávné výsledky pro [std::is_convertible](standard-library/is-convertible-class.md) pro typy polí. To vyžaduje knihovny zapisovateli za účelem zvláštní případ – kompilátor Visual C++ při použití `std::is_convertible<…>` typ znak. V následujícím příkladu statických vyhodnotí průchodu v dřívějších verzích sady Visual Studio, ale selhání v aplikaci Visual Studio 2017 verze 15.3:

```cpp
#include <type_traits>
 
using Array = char[1];
 
static_assert(std::is_convertible<Array, Array>::value);
static_assert(std::is_convertible<const Array, const Array>::value, "");
static_assert(std::is_convertible<Array&, Array>::value, "");
static_assert(std::is_convertible<Array, Array&>::value, "");
```

**std::is_convertible < z možnosti >** je vypočítána zjišťujeme, pokud definici pomyslná funkce je ve správném formátu:
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

Privátní destruktory způsobit typu být není zkonstruovatelný. **std::is_constructible < T, argumentů... >** se počítá jako kdyby byly napsány následující prohlášení:
```cpp 
   T obj(std::declval<Args>()…)
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
Chcete-li opravit kód, odeberte použití N::f příkaz, pokud byste chtěli volání:: f().

### <a name="c2660-local-function-declarations-and-argument-dependent-lookup"></a>C2660: deklarace funkcí Místní a závislé vyhledávací argument
Deklarace funkcí místní skrýt deklarace funkce ve vymezeném oboru a zakázat argument závislé vyhledávání.
Předchozí verze Visual C++ compiler však provést argument závislé vyhledávání v takovém případě by mohl vést k chybnou přetížení vybrána a neočekávané modul runtime chování. Obvykle je chyba z důvodu nesprávný podpis deklarace místní funkce. V následujícím příkladu, Visual Studio 2017 verze 15.3 správně vyvolá C2660 f: – funkce nemusí provádět žádné 2 argumenty:

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

Chcete-li problém vyřešit, buď změňte **f (S)** podpis nebo ji odeberte.

### <a name="c5038-order-of-initialization-in-initializer-lists"></a>C5038: pořadí inicializace v inicializační seznamy
Členy třídy jsou inicializovány v pořadí, ve kterém jsou deklarovány, není pořadí, ve kterém se zobrazují v inicializační seznamy. Předchozí verze kompilátoru není upozornit, když pořadí položek v seznamu inicializátoru lišil od pořadí deklarace. To může vést k nedefinované modul runtime chování, pokud se inicializace došlo k jedné člena závisí na druhý člen v seznamu již inicializován. V následujícím příkladu, Visual Studio 2017 verze 15.3 (s /Wall) vyvolá upozornění C5038: 'A::y' bude inicializován po – datový člen 'A::x' – datový člen:

```cpp
struct A
{
    A(int a) : y(a), x(y) {} // Initialized in reverse, y reused
    int x;
    int y;
};

```
Vyřešte problém uspořádejte seznamu intializer má stejné pořadí jako deklarací. Upozornění podobné se vyvolá, když jeden nebo oba inicializátory odkazovat na členy základní třídy.

Upozorňujeme, že toto upozornění je vypnuto výchozím a ovlivňuje pouze zkompilování kódu s /Wall.

## <a name="update_155"></a>Opravy chyb a jiné změny chování ve Visual Studio 2017 verze 15,5
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
```output
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

```output
warning C4843: 'int (&)[1]': An exception handler of reference to array or function type is unreachable, use 'int*' instead
warning C4843: 'void (__cdecl &)(void)': An exception handler of reference to array or function type is unreachable, use 'void (__cdecl*)(void)' instead
```
Následující kód zabraňuje Chyba:

```cpp
catch (int (*)[1]) {}
```

### <a name="tr1"></a>obor názvů std::tr1 je zastaralý.
Obor názvů std::tr1 nestandardní je nyní označeny jako zastaralé v C ++ 14 a C ++ 17 režimy. Následující kód v aplikaci Visual Studio 2017 verze 15,5, vyvolá C4996:

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

```output
warning C4996: 'std::tr1': warning STL4002: The non-Standard std::tr1 namespace and TR1-only machinery are deprecated and will be REMOVED. You can define _SILENCE_TR1_NAMESPACE_DEPRECATION_WARNING to acknowledge that you have received this warning.
```

Postup řešení chyby, odeberte odkaz na obor názvů tr1:

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


### <a name="annex_d"></a>Funkce standardní knihovny v příloze D jsou označené jako zastaralé.
Když / std: c ++ 17 přepínače kompilátoru režim je nastaven, téměř všechny funkce standardní knihovny v příloze D jsou označeny jako zastaralé.

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

```output
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

```output
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

```output
warning C4619: #pragma warning: there is no warning number '4001'   
```

Pokud kód nemusí být zpětně kompatibilní, se můžete vyhnout upozornění odebráním C4001/C4179 potlačení. Pokud kód musí být zpětně kompatibilní, pak pouze potlačíte C4619.

```cpp
/* C only */

#pragma warning(disable:4619)
#pragma warning(disable:4001)
#pragma warning(disable:4179)

// single line comment
/* single line comment */
```


### <a name="declspec-attributes-with-extern-c-linkage"></a>atributy __declspec extern "C" propojení 

V dřívějších verzích sady Visual Studio, kompilátor Ignorovat `__declspec(…)` atributy při `__declspec(…)` bylo použito před `extern "C"` specifikaci propojení. Toto chování způsobila kódu být vygenerována, která nebyla chcete uživatele s možné runtime důsledky. Upozornění byl přidán v sadě Visual Studio verze 15.3, ale byl ve výchozím nastavení vypnutý. V aplikaci Visual Studio 2017 verze 15,5 se ve výchozím nastavení zapnutá upozornění.

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

```output
warning C4768: __declspec attributes before linkage specification are ignored
```

Chcete-li opravit chyby, umístěte specifikace propojení před atribut __declspec:

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```
Toto nové upozornění C4768 bude daný na některé hlavičky Windows SDK, které byly dodány s Visual Studio 2017 15.3 nebo starší (například: verze 10.0.15063.0, také známé jako RS2 SDK). Ale novější verze sady Windows SDK hlavičky (konkrétně ShlObj.h a ShlObj_core.h) bylo opraveno tak, aby nevedou toto upozornění. Když se zobrazí toto upozornění pocházející z Windows SDK hlavičky, můžete provést tyto akce:
1)  Přepnout na nejnovější SDK Windows dodané s Visual Studio 2017 15,5 verze.
2)  Vypnout upozornění kolem #include příkaz hlavičky Windows SDK:
```cpp
#pragma warning (push) 
#pragma warning(disable:4768)
#include <shlobj.h>
#pragma warning (pop) 
```

### <a name="extern_linkage"></a>Extern constexpr propojení 

V dřívějších verzích sady Visual Studio, kompilátor vždy Dal `constexpr` proměnné vnitřní propojení i v případě, že byla označena jako proměnnou `extern`. V aplikaci Visual Studio 2017 verze 15,5, nového přepínače kompilátoru (nebo Zc:externConstexpr) umožňuje správné chování podle standardů. Nakonec stane výchozí.

```cpp
extern constexpr int x = 10; 
```

```output
error LNK2005: "int const x" already defined
```

Pokud soubor hlaviček obsahuje proměnná definovaná `extern constexpr`, je nutné označit `__declspec(selectany)` aby bylo možné správně používat jeho duplicitní deklarace kombinaci:

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

### <a name="typeid-cant-be-used-on-incomplete-class-type"></a>ID typu nelze použít na typu neúplné třídy.
V dřívějších verzích sady Visual Studio kompilátor nesprávně povoleny následující kód, což vede k potenciálně nesprávný typ informace. V aplikaci Visual Studio 2017 verze 15,5 kompilátor správně vyvolá chybu:

```cpp
#include <typeinfo>

struct S;

void f() { typeid(S); } //C2027 in 15.5
```

```output
error C2027: use of undefined type 'S'
```


### <a name="stdisconvertible-target-type"></a>std::is_convertible cílový typ.

`std::is_convertible`vyžaduje typ cíle jako platný návratový typ. V dřívějších verzích sady Visual Studio kompilátor nesprávně povolená abstraktní typy, které může vést k nesprávné přetížení řešení a neúmyslné modul runtime chování.  Následující kód nyní správně vyvolá C2338:

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
### <a name="noexcept_removal"></a>Odebrání specifikace dynamické výjimky a noexcept
Součástí C ++ 17 `throw()` je alias `noexcept`, `throw(<type list>)` a `throw(…)` se odeberou, a můžou obsahovat určité typy `noexcept`. To může způsobit problémy s kompatibilitou zdroje s kódem, který vyhovuje C ++ 14 nebo dřívější. **/Zc:noexceptTypes-** se vrátit k C ++ 14 verze lze použít přepínač `noexcept` při použití C ++ 17 režim obecně. To vám umožní aktualizovat vašeho zdrojového kódu tak, aby odpovídala C ++ 17 bez přepsání všechny vaše `throw()` kódu ve stejnou dobu.

Kompilátor diagnostikuje nyní také další specifikace neodpovídající výjimek v deklaracích v C ++ 17 režimu nebo s **/ projektovou-** pomocí nového upozornění C5043.

Následující kód vygeneruje C5043 a C5040 Visual Studio 2017 verze 15,5 při / std: c ++ 17 přepínač platí:

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
Datové členy statických constexpr jsou nyní implicitně vložené, což znamená, že jejich deklarace v rámci třídy je nyní jejich definice. Použití definici z přesahujících pro člena statické constexpr dat je redundantní a nyní zastaralé. V aplikaci Visual Studio 2017 verze 15,5 při / std: c ++ 17 přepínače se použije, následující kód vytvoří nyní upozornění C5041 *'size':--line definice pro constexpr statických dat člena není potřebné a je zastaralý součástí C ++ 17*:

```cpp
struct X {
    static constexpr int size = 3;
};
const int X::size; // C5041
```
### <a name="extern-c-declspec-warning-c4768-now-on-by-default"></a>extern "C" __declspec(...) upozornění C4768 nyní na ve výchozím nastavení
Toto upozornění se přidal ve Visual Studio 2017 verze 15.3, ale byl vypnutý ve výchozím nastavení. Ve Visual Studio 2017 verze 15,5 je ve výchozím nastavení zapnutý. V tématu [nové upozornění na atributy declspec](#declspec) Další informace.

### <a name="defaulted-functions-and-declspecnothrow"></a>Uvedena funkce a __declspec(nothrow)
Kompilátor dříve povolen uvedena funkce deklarovat s `__declspec(nothrow)` při odpovídající základní nebo členské funkce povolené výjimky. Toto chování je rozporu s touto C++ Standard a může způsobit nedefinované chování za běhu. Standardní vyžaduje takové funkce být definován jako odstranit, pokud existuje neshoda specifikace k výjimce.  V části/std: c ++ 17, následující kód vyvolá C2280 *pokus o odkazu na funkci odstraněné. Funkce byla implicitně odstraněna, protože není kompatibilní s který implicitní deklarace specifikace explicitní výjimka.* :


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
        ...
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

V takových případech musíte přidat další částečné specializací pro zpracování ukazatelů na funkce noexcept a noexcept ukazatele na členské funkce. Tato přetížení jsou jenom právní v/std: c ++ 17 režimu. Pokud musí být zachovaná zpětné kompatibility s C ++ 14 a psaní kódu, který bude využívat jiné, pak by měla chránit tyto nové přetížení uvnitř `#ifdef` direktivy. Pokud pracujete v samostatný modul, a potom místo použití `#ifdef` chrání pouze můžete zkompilovat s **/Zc:noexceptTypes-** přepínače. 

Následující kód zkompiluje pod/std: c ++ 14 ale selže v části/std: c ++ 17 s chybou C2027:*použít nedefinované typu ' A<T>'*:

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

Následující kód úspěšné pod/std: c ++ 17 protože kompilátor vybere nový částečná specializace `A<void (*)() noexcept>`:

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

## <a name="see-also"></a>Viz také  
[Shoda jazyka Visual C++](visual-cpp-language-conformance.md)  