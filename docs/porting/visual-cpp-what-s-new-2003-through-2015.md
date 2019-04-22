---
title: Visual C++ co&#39;s novou 2003 – 2015
ms.date: 11/04/2016
ms.assetid: c4afde6f-3d75-40bf-986f-be57e3818e26
ms.openlocfilehash: ae21a81869bd68c5a2641dba47b89d7e10b67567
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58898853"
---
# <a name="visual-c-what39s-new-2003-through-2015"></a>Visual C++ co&#39;s novou 2003 – 2015

Tato stránka obsahuje všechny "Novinky" stránky pro všechny verze sady Visual C++ ze sady Visual Studio 2015 zpět do 2003. Tyto informace jsou poskytovány v zájmu usnadnění práce v případě, že může být užitečné při upgradu ze starší verze jazyka Visual C++.

> [!NOTE]
> Informace o aktuální verzi sady Visual Studio najdete v tématu [co je nového v aplikaci Visual C++ v sadě Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md) a [vylepšení v aplikaci Visual C++ v sadě Visual Studio](../overview/cpp-conformance-improvements.md).

## <a name="whats-new-for-c-in-visual-studio-2015"></a>Co je nového v C++ v sadě Visual Studio 2015

V sadě Visual Studio 2015 a novější probíhající vylepšení shoda s kompilátorem prostředí někdy změnit, jak kompilátor rozpozná existující zdrojový kód. Pokud k tomu dojde, mohou se vyskytnout nové nebo jiné chyby během sestavování nebo dokonce behaviorální rozdíly v kódu, který dříve vytvořené a vypadal jako správně spustit.

Naštěstí tyto rozdíly mít žádné nebo téměř žádné dopad na většinu zdrojový kód a vyřešit tyto rozdíly jsou potřeba zdrojový kód nebo jiné změny, opravy jsou obvykle malé a přímočaré. Přidali jsme mnoho příkladů dříve přijatelné zdrojový kód, který může být nutné změnit *(před)* a opravy je opravit *(po)*.

I když váš zdrojový kód nebo jiných artefaktů sestavení, můžete tyto rozdíly ovlivňují, neovlivňují binární kompatibilitu mezi aktualizace na verzi Visual C++. Více závažné druh změn, *narušující změna* může mít vliv na binární kompatibilitu, ale tyto druhy binární kompatibilitu konce vyskytovat jenom mezi hlavními verzemi Visual C++. Například mezi Visual C++ 2013 a Visual C++ 2015. Informace o nejnovější změny, ke kterým došlo mezi Visual C++ 2013 a Visual C++ 2015, najdete v části [změn Visual C++ 2003 – 2015 historie](../porting/visual-cpp-change-history-2003-2015.md).

- [Vylepšení v sadě Visual Studio 2015](#VS_RTM)

- [Vylepšení Visual Studio 2015 Update 1](#VS_Update1)

- [Vylepšení Visual Studio 2015 Update 2](#VS_Update2)

- [Vylepšení Visual Studio 2015 Update 3](#VS_Update3)

### <a name="VS_RTM"></a> Vylepšení v sadě Visual Studio 2015

- **Možnost /Zc:forScope-**

   Možnost kompilátoru `/Zc:forScope-` je zastaralá a bude v budoucí verzi odebrána.

   ```output
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release
   ```

   Možnost se obvykle používají aby nestandardní kód, který používá smyčku proměnné od chvíle, kdy podle standardu, že by měl nepřejdou mimo rozsah. Byla pouze nezbytné při kompilaci s `/Za` možnost, neboť bez `/Za`, použije pro proměnnou smyčky po konci smyčky je vždycky povolená. Pokud vám nezáleží shoda se standardy (například, pokud není určena pro přenositelnost na jiné kompilátory kódu), může vypnout `/Za` možnost (nebo nastavit **zakázat jazyková rozšíření** vlastnost **ne** ). Pokud vás zajímají psaní kódu, přenosná, který vyhovuje standardům, byste měli přepsat váš kód, který vyhovuje standardu přesunutím deklaraci těchto proměnných do bodu mimo smyčku.

   ```cpp
    // zc_forScope.cpp
    // compile with: /Zc:forScope- /Za
    // C2065 expected
    int main() {
       // Uncomment the following line to resolve.
       // int i;
       for (int i =0; i < 1; i++)
          ;
       i = 20;   // i has already gone out of scope under /Za
    }
   ```

- **Zg – možnost kompilátoru.**

   `/Zg` – Možnost kompilátoru (Generovat prototypy funkcí) už nejsou k dispozici. Tato možnost kompilátoru dříve byla zrušena.

- Už můžete spustit testy jednotek s C++vyhodnocovací z příkazového řádku pomocí mstest.exe. Místo toho používá příkaz vstest.console.exe

- **Mutable – klíčové slovo.**

   **Proměnlivé** specifikátor třídy úložiště již není povolena na místech, kde dříve ho zkompilovány bez chyb. Nyní, kompilátor dochází k chybě C2071 (neplatná třída úložiště). Proměnný specifikátor podle standardu, lze použít pouze u názvů datové členy třídy a nejde použít u názvů deklarovaný jako const nebo statické a nejde použít u odkazovat na členy.

   Zvažte například následující kód:

   ```cpp
    struct S {
        mutable int &r;
    };
   ```

   Toto přijetí předchozí verze kompilátoru jazyka Visual C++, ale teď kompilátor poskytuje následující chybu:

   ```Output
    error C2071: 'S::r': illegal storage class
   ```

   Chcete-li vyřešit chybu, jednoduše odebrat redundantní **proměnlivé** – klíčové slovo.

- **char_16_t a char32_t**

   Již slouží `char16_t` nebo `char32_t` jako aliasy v definici typu, protože tyto typy jsou nyní považovány za předdefinované. Je běžné, že uživatelé a autoři knihovny k definování `char16_t` a `char32_t` jako aliasy `uint16_t` a `uint32_t`v uvedeném pořadí.

   ```cpp
    #include <cstdint>

    typedef uint16_t char16_t; //C2628
    typedef uint32_t char32_t; //C2628

    int main(int argc, char* argv[])
    {
    uint16_t x = 1; uint32_t y = 2;
    char16_t a = x;
    char32_t b = y;
    return 0;
    }
   ```

   Chcete-li aktualizovat váš kód, odeberte **– typedef** deklarace a přejmenujte další identifikátory, které kolidují s těmito názvy.

- **Parametry šablony bez typu**

   Určitý kód, který zahrnuje parametry šablony bez typu je nyní správně kontroluje kompatibilita typů při poskytování explicitní argumenty šablony. Například následující kód zkompilován bez chyby v předchozích verzích Visual C++.

   ```cpp
    struct S1
    {
        void f(int);
        void f(int, int);
    };

    struct S2
    {
        template <class C, void (C::*Function)(int) const> void f() {}
    };

    void f()
    {
        S2 s2;
        s2.f<S1, &S1::f>();
    }
   ```

   Aktuální kompilátor správně vrátí chybu, protože typ parametru šablony neodpovídá argument šablony (parametru je ukazatel na člena const, ale funkce f je nekonstantní):

   ```Output
    error C2893: Failed to specialize function template 'void S2::f(void)'note: With the following template arguments:note: 'C=S1'note: 'Function=S1::f'
   ```

   Chcete-li vyřešit tuto chybu v kódu, ujistěte se, že typ argumentu šablony používáte odpovídá deklarovaného typu parametru šablony.

- **__declspec(align)**

   Kompilátor už přijímá `__declspec(align)` na funkce. To vždy ignorovány, ale nyní způsobí chybu kompilátoru.

   ```cpp
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations
   ```

   Chcete-li tento problém vyřešit, odeberte `__declspec(align)` z deklarace funkce. Protože to nemělo žádný vliv, jeho odebrání není něco změnit.

- **Zpracování výjimek**

   Existuje několik změn pro zpracování výjimek. Nejprve objekty výjimky musí být kopírovatelné nebo přesouvatelný. Následující kód zkompilován v sadě Visual Studio 2013, ale nebude zkompilován v sadě Visual Studio 2015:

   ```cpp
    struct S {
    public:
        S();
    private:
        S(const S &);
    };

    int main()
    {
        throw S(); // error
    }
   ```

   Problém je, že je kopírovací konstuktor je soukromé, tak, aby objekt nelze zkopírovat, protože dochází v běžném zpracování výjimky. To samé platí při deklaraci konstruktoru kopie **explicitní**.

   ```cpp
    struct S {
        S();
        explicit S(const S &);
    };

    int main()
    {
        throw S(); // error
    }
   ```

   A aktualizujte svůj kód, zajistěte, aby kopírovací konstruktor pro svůj objekt výjimky veřejné a není určena **explicitní**.

   Zachycování výjimky podle hodnoty vyžaduje také kopírovatelné objekt výjimky. Následující kód zkompilován v sadě Visual Studio 2013, ale nebude zkompilován v sadě Visual Studio 2015:

   ```cpp
    struct B {
    public:
        B();
    private:
        B(const B &);
    };

    struct D : public B {
    };

    int main()
    {
        try
        {
        }
        catch (D d) // error
        {
        }
    }
   ```

   Tento problém můžete opravit tak, že změníte typ parametru pro položku **catch** na odkaz.

   ```cpp
    catch(D& d)
    {
    }
   ```

- **Řetězcové literály, za nímž následuje makra**

   Kompilátor nyní podporuje uživatelsky definované literály. Řetězcové literály, za nímž následuje makra bez žádné prázdné znaky použité v důsledku toho jsou interpretovány jako uživateli definované literály, které by mohla vést k chybám nebo neočekávané výsledky. Například v předchozím kompilátory následující kód zkompilován úspěšně:

   ```cpp
    #define _x "there"
    char* func() {
        return "hello"_x;
    }
    int main()
    {
        char * p = func();
        return 0;
    }
   ```

   Kompilátor interpretuje to jako řetězec literálu "hello" následované makro, které je rozbalený "obsahuje", a potom byly spojeny dva řetězcové literály do jedné. V sadě Visual Studio 2015 Kompilátor interpretuje jako uživatelem definovaného literálu, ale protože neexistuje žádné odpovídající uživatelské literálu _x definovaný, vrátí chybu.

   ```cpp
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found
    note: Did you forget a space between the string literal and the prefix of the following string literal?

   ```

   Chcete-li tento problém vyřešit, přidejte mezeru mezi řetězcový literal a makro.

- **Sousední řetězcové literály**

   Podobně jako na předchozí, z důvodu související změny v analýze řetězce byly sousedních textových literálů (buď široký nebo úzký znak řetězcových literálů) bez žádné prázdné znaky interpretován jako jeden řetězec zřetězených v předchozích verzích Visaul C++. V sadě Visual Studio 2015 teď musíte přidat prázdné znaky mezi dva řetězce. Například musíte změnit následující kód:

   ```cpp
    char * str = "abc""def";
   ```

   Jednoduše přidejte mezeru mezi dva řetězce.

   ```cpp
    char * str = "abc" "def";
   ```

- **Nové umístění a delete**

   Byla provedena změna **odstranit** operátor pamětí souladu s C ++ 14, standardní. Podrobnosti o změně standardy najdete v [C++ velikostí Dealokace](http://isocpp.org/files/papers/n3778.html). Změny přidejte formulář globálního **odstranit** operátor, který přijímá parametr velikosti. Rozbíjející změnu je, že pokud jste dříve používali operátor **odstranit** se stejným podpisem (tak, aby odpovídaly s **nové umístění** operátor), obdržíte chybu kompilátoru (C2956, to se stává v místě, kde **nové umístění** se používá, protože to je pozice v kódu, kde kompilátor se pokusí identifikovat příslušné odpovídající **odstranit** operátor).

   Funkce `void operator delete(void *, size_t)` byla **umístění operátoru delete** odpovídající operátor **umístění nového** funkce `void * operator new(size_t, size_t)` v C ++ 11. Pomocí C ++ 14 velikostí dealokace, to **odstranit** funkce je teď *funkce zrušení přidělení obvykle* (globální **odstranit** operátor). Standardní vyžaduje, že pokud použití **umístění nového** vyhledá odpovídající **odstranit** funkce a najde funkce obvykle zrušení přidělení, program je chybně vytvořený.

   Předpokládejme například, že váš kód definuje, jak **umístění nového** a **umístění operátoru delete**:

   ```cpp
    void * operator new(std::size_t, std::size_t);
    void operator delete(void*, std::size_t) noexcept;
   ```

   K problému dochází kvůli shodu v podpisech funkcí mezi **umístění operátoru delete** operátoru, které jste definovali a nové globální velikosti **odstranit** operátor. Zvažte, jestli můžete použít jiný typ než `size_t` libovolné **umístění nového** a **odstranit** operátory.  Všimněte si, že typ `size_t` **– typedef** závisí na kompilátoru; je **– typedef** pro **unsigned int** v jazyce Visual C++. Dobrým řešením je použití Výčtový typ takovou situaci:

   ```cpp
    enum class my_type : size_t {};
   ```

   Změňte vaší definice umístění **nové** a **odstranit** použít tento typ, jako druhý argument místo `size_t`. Také budete muset aktualizovat volání **umístění nového** nový typ (například pomocí `static_cast<my_type>` pro převod z celočíselnou hodnotu) a aktualizace definice **nové** a  **Odstranit** přetypovat zpět na typ celé číslo. Není nutné používat **výčtu** pro tento účel; typ třídy s `size_t` člen by také fungovat.

   Alternativním řešením je, že je možné odstranit **umístění nového** úplně se vynechá. Pokud váš kód používá **umístění nového** implementace fondu paměti, kde argument umístění je velikost objektu se přidělené nebo odstraněna, pak velikostí dealokace funkce může být vhodné nahradit vlastním kódem fondu vlastní paměti a můžete vyřadit umístění funkce a stačí použít vlastní dvěma argumenty **odstranit** operátor namísto funkce umístění.

   Pokud nechcete aktualizovat váš kód okamžitě, můžete se vrátit k staré chování pomocí možnosti kompilátoru `/Zc:sizedDealloc-`. Pokud použijete tuto možnost, dvěma argumenty **odstranit** neexistují funkce a nebude způsobovat konflikt s vaší **umístění operátoru delete** operátor.

- **Sjednocení datových členů**

   Data členů sjednocení může mít už typy odkazů. Následující kód zkompilován úspěšně v sadě Visual Studio 2013, ale dojde k chybě v sadě Visual Studio 2015.

   ```cpp
    union U1 {
        const int i;
    };
    union U2 {
       int &i;
    };
    union U3 {
        struct {int &i;};
    };
   ```

   Předchozí kód vytvoří následující chyby:

   ```Output
    test.cpp(67): error C2625: 'U2::i': illegal union member; type 'int &' is reference type
    test.cpp(70): error C2625: 'U3::i': illegal union member; type 'int &' is reference type
   ```

   Chcete-li tento problém vyřešit, změňte typy odkazů na ukazatel nebo hodnotu. Změna typu ukazatele vyžaduje změny v kódu, který používá pole typu union. Kód na hodnotu by změna dat uložených ve sjednocení, které ovlivňují ostatní pole, protože pole ve sjednocení typů sdílejí stejnou paměť. V závislosti na velikosti hodnotu se může také změnit velikost sjednocení.

- **Anonymní sjednocení**

   jsou teď další splňující podmínky standardu. Předchozí verze kompilátoru generované představují explicitní konstruktor a destruktor pro anonymní sjednocení. Odstraní se v sadě Visual Studio 2015.

   ```cpp
   struct S {
      S();
   };

   union {
      struct {
         S s;
      };
   } u; // C2280
   ```

   Předchozí kód generuje následující chybu v sadě Visual Studio 2015:

   ```cpp
    error C2280: '<unnamed-type-u>::<unnamed-type-u>(void)': attempting to reference a deleted function
    note: compiler has generated '<unnamed-type-u>::<unnamed-type-u>' here
   ```

   Chcete-li vyřešit tento problém, poskytnout vlastní definice konstruktor nebo destruktor.

   ```cpp
    struct S {
       // Provide a default constructor by adding an empty function body.
       S() {}
    };

    union {
       struct {
          S s;
       };
    } u;
   ```

- **Sjednocení s anonymní struktury**

   Aby bylo možné v souladu se standardem, chování za běhu změnil členům anonymní struktury ve sjednoceních. Konstruktor pro anonymní struktury členům ve sjednocení je už nebude implicitně volána při vytvoření těchto sjednocení. Destruktor pro anonymní struktury členům ve sjednocení také, je už nebude implicitně volána, když sjednocení dostane mimo rozsah. Uvažujme následující kód, ve kterém sjednocení U obsahuje anonymní struktury, který obsahuje člena, který je pojmenované struktury S, který má destruktor.

   ```cpp
    #include <stdio.h>
    struct S {
        S() { printf("Creating S\n"); }
        ~S(){ printf("Destroying S\n"); }
    };
    union U {
        struct {
        S s;
    };
        U() {}
        ~U(){}
    };

    void f()
    {
        U u;
        // Destructor implicitly called here.
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
   ```

   V sadě Visual Studio 2013 je konstruktor S volá, když se vytvoří sjednocení a destruktor S se volá, když je pro funkci f zásobník vyčištěn. Ale v sadě Visual Studio 2015, se nazývá konstruktor a destruktor. Kompilátor obsahuje upozornění týkající se této změny chování.

   ```Output
    warning C4587: 'U::s': behavior change: constructor is no longer implicitly calledwarning C4588: 'U::s': behavior change: destructor is no longer implicitly called
   ```

   Chcete-li obnovit původní chování, pojmenujte anonymní struktury. Modul runtime chování – a anonymní struktury je stejný, bez ohledu na verze kompilátoru.

   ```cpp
    #include <stdio.h>

    struct S {
        S() { printf("Creating S.\n"); }
        ~S() { printf("Destroying S\n"); }
    };
    union U {
        struct {
            S s;
        } namedStruct;
        U() {}
        ~U() {}
    };

    void f()
    {
        U u;
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
   ```

   Případně zkuste přesunout konstruktor a destruktor kód do nové funkce a přidejte volání těchto funkcí z konstruktor a destruktor pro sjednocení.

   ```cpp
    #include <stdio.h>

    struct S {
        void Create() { printf("Creating S.\n"); }
        void Destroy() { printf("Destroying S\n"); }
    };
    union U {
        struct {
            S s;
        };
        U() { s.Create();  }
        ~U() { s.Destroy(); }
    };

    void f()
    {
        U u;
    }

    int main()
    {
        f();

    char s[1024];
    printf("Press any key.\n");
    gets_s(s);
    return 0;
    }
   ```

- **Šablony řešení**

   Překlad názvů pro šablony byly provedeny změny. V jazyce C++ při zvažování kandidáty pro rozlišení názvu může být případ, že jeden nebo více názvů uvažovanou jako potenciální shody vytváří instance neplatná šablona. Tyto neplatné instancí obvykle nezpůsobí chyby kompilátoru principem, který je označován jako SFINAE (nahrazení selhání je není chybovou).

   Nyní pokud SFINAE vyžaduje, aby kompilátor pro vytvoření instance specializace šablony třídy, pak všechny chyby, ke kterým dochází během tohoto procesu jsou chyby kompilátoru. V předchozích verzích by kompilátor ignorovat tyto chyby. Zvažte například následující kód:

   ```cpp
    #include <type_traits>

    template<typename T>
    struct S
    {
    S() = default;
    S(const S&);
    S(S&&);

    template<typename U, typename = typename std::enable_if<std::is_base_of<T, U>::value>::type>
    S(S<U>&&);
    };

    struct D;

    void f1()
    {
    S<D> s1;
        S<D> s2(s1);
    }

    struct B
    {
    };

    struct D : public B
    {
    };

    void f2()
    {
    S<D> s1;
        S<D> s2(s1);
    }
   ```

   Pokud kompilujete s aktuální kompilátorem, zobrazí se následující chyba:

   ```Output
    type_traits(1110): error C2139: 'D': an undefined class is not allowed as an argument to compiler intrinsic type trait '__is_base_of'
    ..\t331.cpp(14): note: see declaration of 'D'
    ..\t331.cpp(10): note: see reference to class template instantiation 'std::is_base_of<T,U>' being compiled
            with
            [
                T=D,
                U=D
            ]
   ```

   Důvodem je, že při prvním vyvolání is_base_of – třída by "ještě nebyl definován.

   V tomto případě opravy je nepoužívat těchto vlastností s typem, dokud je definována třída. Pokud je definice B a D přesunout na začátek souboru kódu, se problém nevyřeší. Pokud jsou definice v souborech hlaviček, zkontrolujte pořadí příkazů zahrnout soubory hlaviček, abyste měli jistotu, že žádné definice tříd jsou zkompilovány před problematický šablony používá.

- **Kopírovací konstruktory**

   V sadě Visual Studio 2013 a Visual Studio 2015 kompilátor generuje kopírovací konstruktor pro třídu, pokud tato třída má konstruktor přesunutí definovaný uživatelem, ale žádná uživatelem definovaného kopírovacího konstruktoru. V Dev14 tento implicitně generovaný kopírovací konstuktor je také označena, "= delete".

### <a name="VS_Update1"></a> Vylepšení Visual Studio 2015 Update 1

- **Privátní virtuální základní třídy a nepřímé dědění**

   Předchozí verze kompilátoru povolené odvozené třídy za účelem volat členské funkce z jeho *nepřímo odvozeny* `private virtual` základních tříd. Toto chování staré bylo nesprávné a není v souladu s standardu jazyka C++. Kompilátor už přijímá kódu napsaného v tímto způsobem a vydá Chyba kompilátoru C2280 ve výsledku.

   ```Output
    error C2280: 'void *S3::__delDtor(unsigned int)': attempting to reference a deleted function
   ```

   Příklad (před)

   ```cpp
    class base
    {
    protected:
        base();
        ~base();
    };

    class middle: private virtual base {};class top: public virtual middle {};

    void destroy(top *p)
    {
        delete p;  //
    }
   ```

   Příklad (po)

   ```cpp
    class base;  // as above

    class middle: protected virtual base {};
    class top: public virtual middle {};

    void destroy(top *p)
    {
        delete p;
    }
   ```

  \-or-

   ```cpp
    class base;  // as above

    class middle: private virtual base {};
    class top: public virtual middle, private virtual bottom {};

    void destroy(top *p)
    {
        delete p;
    }
   ```

- **Přetížený operátor new a delete – operátor**

   Předchozí verze kompilátoru povoleno bez členů **operátor new** a třetí **operátor delete** být deklarované jako statické a být deklarovány v oborech názvů, než je globální obor názvů.  Toto chování staré vytvořili riziko, že program by volat **nové** nebo **odstranit** operátor implementace, která má programátora, výsledný tiché chybný modul runtime chování. Kompilátor už přijímá kódu napsaného v tímto způsobem a místo toho vystavuje Chyba kompilátoru C2323.

   ```Output
    error C2323: 'operator new': non-member operator new or delete functions may not be declared static or in a namespace other than the global namespace.
   ```

   Příklad (před)

   ```cpp
    static inline void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // error C2323
   ```

   Příklad (po)

   ```cpp
    void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // removed 'static inline'
   ```

   Kromě toho Ačkoli kompilátor nedává zvláštní diagnostiky, vložené operátor new se považuje za chybně vytvořený.

- **Volání ' – operátor *typ*() "(uživatelem definovaný převod) na typech bez třídy** předchozí verze kompilátoru povolené" – operátor *typ*() "k volání na typech bez třídy při bezobslužném režimu ignoruje se. Toto chování staré vytvořili riziko generování tiché chybného kódu, což vede k modulu runtime nepředvídatelné chování. Kompilátor už přijímá kódu napsaného v tímto způsobem a místo toho vystavuje Chyba kompilátoru C2228.

   ```Output
    error C2228: left of '.operator type' must have class/struct/union
   ```

   Příklad (před)

   ```cpp
    typedef int index_t;

    void bounds_check(index_t index);

    void login(int column)
    {
        bounds_check(column.operator index_t());  // error C2228
    }
   ```

   Příklad (po)

   ```cpp
    typedef int index_t;

    void bounds_check(index_t index);

    void login(int column)
    {
         bounds_check(column);  // removed cast to 'index_t', 'index_t' is an alias of 'int'
    }
   ```

- **Redundantní typename v elaborované specifikátory typu** předchozí verze kompilátoru povolené **typename** v elaborované specifikátory typu; je sémanticky nesprávný kód napsaný v tímto způsobem. Kompilátor už přijímá kódu napsaného v tímto způsobem a místo toho vystavuje Chyba kompilátoru C3406.

   ```Output
    error C3406: 'typename' cannot be used in an elaborated type specifier
   ```

   Příklad (před)

   ```cpp
    template <typename class T>
    class container;
   ```

   Příklad (po)

   ```cpp
    template <class T>  // alternatively, could be 'template <typename T>'; 'typename' is not elaborating a type specifier in this case
    class container;
   ```

- **Odvození pole ze seznamu inicializátorů typu** předchozí verze kompilátoru nepodporuje odvození typu polí ze seznamu inicializátorů. Kompilátor nyní podporuje tento formulář odvození typu a v důsledku toho volání šablony funkce pomocí seznamy inicializátorů teď může být nejednoznačná nebo jiné přetížení může zvolit než v předchozích verzích kompilátoru. Jak tyto problémy vyřešit, program musí nyní explicitně určit přetížení, které určené programátorovi.

   Když toto nové chování způsobí, že řešení přetížení, které byste měli zvážit další Release candidate, který je stejně tak dobré jako historické Release candidate, stane se nejednoznačné volání a kompilátor vyvolá chybu kompilátoru C2668 ve výsledku.

   ```Output
    error C2668: 'function' : ambiguous call to overloaded function.
   ```

   Příklad 1: Nejednoznačné volání přetížené funkce (před)

   ```cpp
    // In previous versions of the compiler, code written in this way would unambiguously call f(int, Args...)
    template <typename... Args>
    void f(int, Args...);  //

    template <int N, typename... Args>
    void f(const int (&)[N], Args...);

    int main()
    {
        // The compiler now considers this call ambiguous, and issues a compiler error
        f({3});  error C2668: 'f' ambiguous call to overloaded function
    }
   ```

   Příklad 1: nejednoznačné volání přetížené funkce (po)

   ```cpp
    template <typename... Args>
    void f(int, Args...);  //

    template <int N, typename... Args>
    void f(const int (&)[N], Args...);

    int main()
    {
        // To call f(int, Args...) when there is just one expression in the initializer list, remove the braces from it.
        f(3);
    }
   ```

   Když toto nové chování způsobí řešení přetížení, které byste měli zvážit další Release candidate, který je lepší shody než historické Release candidate, volání řeší jednoznačně na novou verzi Release candidate, způsobí změnu v chování programu, který je pravděpodobně odlišná od programátor určené.

   Příklad 2: změny v řešení přetížení (před)

   ```cpp
    // In previous versions of the compiler, code written in this way would unambiguously call f(S, Args...)
    struct S
    {
        int i;
        int j;
    };

    template <typename... Args>
    void f(S, Args...);

    template <int N, typename... Args>
    void f(const int *&)[N], Args...);

    int main()
    {
        // The compiler now resolves this call to f(const int (&)[N], Args...) instead
        f({1, 2});
    }
   ```

   Příklad 2: změny v řešení přetížení (po)

   ```cpp
    struct S;  // as before

    template <typename... Args>
    void f(S, Args...);

    template <int N, typename... Args>
    void f(const int *&)[N], Args...);

    int main()
    {
        // To call f(S, Args...), perform an explicit cast to S on the initializer list.
        f(S{1, 2});
    }
   ```

- **Obnovení upozornění switch – příkaz**

   Předchozí verzi kompilátoru odstraněny dříve existující upozornění související s **přepnout** příkazů; toto upozornění ACLs byly obnoveny. Kompilátor vyvolá nyní obnovené upozornění a upozornění souvisejících s konkrétní případy (včetně výchozí případ) jsou teď vydaný na řádek obsahující problematický případu, nikoli na posledním řádku příkazu switch. Díky tomu teď vystavujících upozornění na samostatné řádky než v minulosti, upozornění dříve potlačit pomocí `#pragma warning(disable:####)` už dá potlačit očekávaným způsobem. Chcete-li tato upozornění potlačit očekávaným způsobem, může být potřeba přesunout `#pragma warning(disable:####)` direktivy řádku nad prvním případě potenciálně poškozený. Následují obnovené upozornění.

   ```Output
    warning C4060: switch statement contains no 'case' or 'default' labels
   ```

   ```Output
    warning C4061: enumerator 'bit1' in switch of enum 'flags' is not explicitly handled by a case label
   ```

   ```Output
    warning C4062: enumerator 'bit1' in switch of enum 'flags' is not handled
   ```

   ```Output
    warning C4063: case 'bit32' is not a valid value for switch of enum 'flags'
   ```

   ```Output
    warning C4064: switch of incomplete enum 'flags'
   ```

   ```Output
    warning C4065: switch statement contains 'default' but no 'case' labels
   ```

   ```Output
    warning C4808: case 'value' is not a valid value for switch condition of type 'bool'
   ```

   ```Output
    Warning C4809: switch statement has redundant 'default' label; all possible 'case' labels are given
   ```

   Příklad C4063 (před)

   ```cpp
    class settings
    {
    public:
        enum flags
        {
            bit0 = 0x1,
            bit1 = 0x2,
            ...
        };
        ...
    };

    int main()
    {
        auto val = settings::bit1;

        switch (val)
        {
        case settings::bit0:
            break;

        case settings::bit1:
            break;

        case settings::bit0 | settings::bit1:  // warning C4063
            break;
        }
    };
   ```

   Příklad C4063 (po)

   ```cpp
    class settings {...};  // as above

    int main()
    {
        // since C++11, use std::underlying_type to determine the underlying type of an enum
        typedef std::underlying_type<settings::flags>::type flags_t;

        auto val = settings::bit1;

        switch (static_cast<flags_t>(val))
        {
        case settings::bit0:
            break;

        case settings::bit1:
            break;

        case settings::bit0 | settings::bit1:  // ok
            break;
        }
    };
   ```

   Příklady dalších obnovené upozornění jsou k dispozici v jejich dokumentaci.

- **#include: použití specifikátoru nadřazený adresář '..' v názvu cesty** (má vliv pouze `/Wall` `/WX`)

   Předchozí verze kompilátoru nezjistili použití specifikátoru nadřazený adresář '..' v cestě `#include` direktivy. Kód napsaný v tímto způsobem obvykle má zahrnout záhlaví, které existují mimo projekt nesprávně pomocí projektu relativní cesty. Toto chování staré vytvořili riziko, že program může zkompilovat zahrnutím souboru jiného zdroje než programátor určené nebo že tyto relativní cesty by být nepřenositelné na jiné prostředí sestavení. Kompilátor nyní zjistí a upozorní programátor kódu napsaného v tímto způsobem a problémy volitelné kompilátor varování C4464, pokud je povoleno.

   ```Output
    warning C4464: relative include path contains '..'
   ```

   Příklad (před)

   ```cpp
    #include "..\headers\C4426.h"  // emits warning C4464
   ```

   Příklad (po)

   ```cpp
    #include "C4426.h"  // add absolute path to 'headers\' to your project's include directories
   ```

   Kromě toho, přestože kompilátor neposkytuje konkrétní diagnostiky, také doporučujeme, aby specifikátor nadřazený adresář ".." Poznámka slouží k určení adresáře souborů k zahrnutí vašeho projektu.

- **#pragma optimize() přesahuje za konec souboru záhlaví** (má vliv pouze `/Wall` `/WX`)

   Předchozí verze kompilátoru se nepodařilo rozpoznat změny nastavení příznaku optimalizace, které řídicí hlavičkovém souboru zahrnutém v jednotce překladu. Kompilátor nyní zjistí a upozorní programátor kódu napsaného v tímto způsobem a problémy volitelné kompilátor varování C4426 na umístění je problematický `#include`, pokud je povoleno. Pokud argumenty příkazového řádku pro kompilátor nastaven změny jsou v konfliktu s příznaky optimalizace se pouze objeví toto upozornění.

   ```Output
    warning C4426: optimization flags changed after including header, may be due to #pragma optimize()
   ```

   Příklad (před)

   ```cpp
    // C4426.h
    #pragma optimize("g", off)
    ...
    // C4426.h ends

    // C4426.cpp
    #include "C4426.h"  // warning C4426
   ```

   Příklad (po)

   ```cpp
    // C4426.h
    #pragma optimize("g", off)
    ...
    #pragma optimize("", on)  // restores optimization flags set via command-line arguments
    // C4426.h ends

    // C4426.cpp
    #include "C4426.h"
   ```

- **Neshoda #pragma warning(push)** a **#pragma warning(pop)** (má vliv pouze `/Wall` `/WX`)

   Předchozí verze kompilátoru nezjistili `#pragma warning(push)` změny stavu je spárovaná s `#pragma warning(pop)` stavu změny v odlišném zdrojovém souboru, která je určena jen zřídka. Toto chování staré vytvořil riziko, který program by být kompilována s jinou sadu upozornění povolená než programátor určena, může být výsledkem chování za běhu tiché chybná. Kompilátor nyní zjistí a upozorní programátor kódu napsaného v tímto způsobem a problémy volitelné kompilátor varování C5031 na odpovídající pozici `#pragma warning(pop)`, pokud je povoleno. Toto upozornění zahrnuje poznámku odkazující na umístění odpovídající `#pragma warning(push)`.

   ```Output
    warning C5031: #pragma warning(pop): likely mismatch, popping warning state pushed in different file
   ```

   Příklad (před)

   ```cpp
    // C5031_part1.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    // C5031_part1.h ends without #pragma warning(pop)

    // C5031_part2.h
    ...
    #pragma warning(pop)  // pops a warning state not pushed in this source file
    ...
    // C5031_part1.h ends

    // C5031.cpp
    #include "C5031_part1.h" // leaves #pragma warning(push) 'dangling'
    ...
    #include "C5031_part2.h" // matches 'dangling' #pragma warning(push), resulting in warning C5031
    ...
   ```

   Příklad (po)

   ```cpp
    // C5031_part1.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    #pragma warning(pop)  // pops the warning state pushed in this source file
    // C5031_part1.h ends without #pragma warning(pop)

    // C5031_part2.h
    #pragma warning(push)  // pushes the warning state pushed in this source file
    #pragma warning(disable:####)
    ...
    #pragma warning(pop)
    // C5031_part1.h ends

    // C5031.cpp
    #include "C5031_part1.h" // #pragma warning state changes are self-contained and independent of other source files or their #include order.
    ...
    #include "C5031_part2.h"
    ...
   ```

   I když je běžné, kód napsaný v tímto způsobem je někdy úmyslné. Je citlivá na změny v kódu napsaného v tímto způsobem `#include` pořadí; Pokud je to možné, doporučujeme vám, že soubory se zdrojovým kódem spravovat stav s varováním samostatná způsobem.

- **Bezkonkurenční #pragma warning(push)** (má vliv pouze `/Wall` `/WX`)

   Předchozí verze kompilátoru nezjistili bezkonkurenční `#pragma warning(push)` stavu změny na konci jednotky překladu. Kompilátor nyní zjistí a upozorní programátor kódu napsaného v tímto způsobem a problémy volitelné kompilátor varování C5032 v umístění souboru neporovnané `#pragma warning(push)`, pokud je povoleno. Pokud nejsou žádné chyby během kompilace v jednotce překladu se pouze objeví toto upozornění.

   ```Output
    warning C5032: detected #pragma warning(push) with no corresponding #pragma warning(pop)
   ```

   Příklad (před)

   ```cpp
    // C5032.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    // C5032.h ends without #pragma warning(pop)

    // C5032.cpp
    #include "C5032.h"
    ...
    // C5032.cpp ends -- the translation unit is completed without #pragma warning(pop), resulting in warning C5032 on line 1 of C5032.h
   ```

   Příklad (po)

   ```cpp
    // C5032.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    #pragma warning(pop) // matches #pragma warning (push) on line 1
    // C5032.h ends

    // C5032.cpp
    #include "C5032.h"
    ...
    // C5032.cpp ends -- the translation unit is completed without unmatched #pragma warning(push)
   ```

- **Může se objevit další upozornění v důsledku stav varování #pragma vylepšené sledování**

   Předchozí verze kompilátoru sledovat `#pragma warning` změně stavu dostatečně vydat všechny určené upozornění. Toto chování vytvoření rizika určitá upozornění by efektivně potlačit v případech liší od programátor určené. Kompilátor nyní sleduje `#pragma warning` stav více robustní – zejména související s `#pragma warning` stav se změní v rámci šablony – a volitelně vydá nová upozornění C5031 a C5032, které umožní programátora, vyhledejte neúmyslnému použití `#pragma warning(push)` a `#pragma warning(pop)`.

   Kvůli vylepšení `#pragma warning` stav řešení change tracking, dříve nesprávně potlačit upozornění a upozornění související s problémy dříve misdiagnosed mohou nyní být vydány.

- **Vylepšila se identifikace nedosažitelný kód**

   Změny standardní knihovny C++ a vylepšená možnost volání vložených funkcí porovnání s předchozími verzemi kompilátoru může umožnit kompilátoru prokázat, že určitý kód je nyní nedostupná. Toto nové chování může způsobit nové a dalších často vydané instancí upozornění C4720.

   ```Output
    warning C4720: unreachable code
   ```

   V mnoha případech se toto upozornění může se objevit jenom při kompilaci s povolenou optimalizací, od optimalizace může vložené více volání funkcí, vyloučit redundantní kód nebo jinak ji možné určit, že některé kód nedosažitelný. Zjistili jsme, že nové instance upozornění C4720 často došlo v **bloku try/catch** blokuje, zejména ve vztahu k užívání [std::find](assetId:///std::find?qualifyHint=False&autoUpgrade=True).

   Příklad (před)

   ```cpp
    try
    {
        auto iter = std::find(v.begin(), v.end(), 5);
    }
    catch(...)
    {
        do_something();  // ok
    }
   ```

   Příklad (po)

   ```cpp
    try
    {
        auto iter = std::find(v.begin(), v.end(), 5);
    }
    catch(...)
    {
        do_something();  // warning C4702: unreachable code
    }
   ```

### <a name="VS_Update2"></a> Vylepšení Visual Studio 2015 Update 2

- **Další upozornění a chyby mohou být vydány v důsledku částečná podpora sfinae u výrazů**

   Předchozí verze kompilátoru analyzovat určité druhy výrazy uvnitř **decltype** specifikátory vzhledem k absenci podpora sfinae u výrazů. Toto chování staré bylo nesprávné a není v souladu s standardu jazyka C++. Kompilátor nyní analyzuje tyto výrazy a má částečná podpora sfinae u výrazů z důvodu probíhající vylepšení. V důsledku toho kompilátor nyní vyvolá upozornění a chyby nalezené ve výrazech, že analyzovat předchozí verze kompilátoru.

   Když toto nové chování analyzuje **decltype** výraz, který obsahuje typ, který nebyl dosud deklarován, kompilátor vydává chybu kompilátoru C2039 ve výsledku.

   ```Output
    error C2039: 'type': is not a member of '`global namespace''
   ```

   Příklad 1: použití neurčený typ (před)

   ```cpp
    struct s1
    {
      template <typename T>
      auto f() -> decltype(s2<T>::type::f());  // error C2039

      template<typename>
      struct s2 {};
    }
   ```

   Příklad 1 (po)

   ```cpp
    struct s1
    {
      template <typename>  // forward declare s2struct s2;

      template <typename T>
      auto f() -> decltype(s2<T>::type::f());

      template<typename>
      struct s2 {};
    }
   ```

   Když toto nové chování analyzuje **decltype** výraz, který chybí nezbytné používání **typename** – klíčové slovo k určení, že je název závislý typ, kompilátor vydává kompilátor varování C4346 spolu s chyba kompilátoru C2923.

   ```Output
    warning C4346: 'S2<T>::Type': dependent name is not a type
   ```

   ```Output
    error C2923: 's1': 'S2<T>::Type' is not a valid template type argument for parameter 'T'
   ```

   Příklad 2: závislý název není typ (před)

   ```cpp
    template <typename T>
    struct s1
    {
      typedef T type;
    };

    template <typename T>
    struct s2
    {
      typedef T type;
    };

    template <typename T>
    T declval();

    struct s
    {
      template <typename T>
      auto f(T t) -> decltype(t(declval<S1<S2<T>::type>::type>()));  // warning C4346, error C2923
    };
   ```

   Příklad 2 (po)

   ```cpp
    template <typename T> struct s1 {...};  // as above
    template <typename T> struct s2 {...};  // as above

    template <typename T>
    T declval();

    struct s
    {
      template <typename T>
      auto f(T t) -> decltype(t(declval<S1<typename S2<T>::type>::type>()));
    };
   ```

- `volatile` **Členské proměnné zabránit implicitně definované konstruktory a operátory přiřazení** třídu, která má povolené předchozí verze kompilátoru **volatile** kopírovat nebo přesunout členské proměnné mají výchozí konstruktory a Výchozí kopírování/operátory přiřazení pro přesunutí automaticky generovány. Toto chování staré bylo nesprávné a není v souladu s standardu jazyka C++. Kompilátor nyní brány v úvahu třídu, která má volatile členské proměnné nejsou v netriviálních konstrukce a operátory přiřazení, který brání automatickému generování výchozí implementace těchto operátorů. Pokud takové třídy je člen sjednocení (nebo anonymní sjednocení uvnitř třídy), zkopírovat nebo přesunout konstruktory a operátory přiřazení kopie nebo přesunout sjednocení (nebo třídy obsahující unonymous sjednocení) bude možné implicitně definovaný jako odstraněný. Pokus o vytvoření nebo zkopírujte sjednocení (nebo třídu obsahující anonymní sjednocení) bez nutnosti explicitně definovat jejich je chyba a Chyba kompilátoru problémy kompilátoru C2280 ve výsledku.

   ```Output
    error C2280: 'B::B(const B &)': attempting to reference a deleted function
   ```

   Příklad (před)

   ```cpp
    struct A
    {
      volatile int i;
      volatile int j;
    };

    extern A* pa;

    struct B
    {
      union
      {
        A a;
        int i;
      };
    };

    B b1 {*pa};
    B b2 (b1);  // error C2280
   ```

   Příklad (po)

   ```cpp
    struct A
    {
      int i;int j;
    };

    extern volatile A* pa;

    A getA()  // returns an A instance copied from contents of pa
    {
      A a;
      a.i = pa->i;
      a.j = pa->j;
      return a;
    }

    struct B;  // as above

    B b1 {GetA()};
    B b2 (b1);  // error C2280
   ```

- **Statické členské funkce nepodporují kvalifikátory cv.**

   Předchozích verzích Visual C++ 2015 povoleny kvalifikátory cv mít statické členské funkce. Toto chování je z důvodu regrese v Visual C++ 2015 a Visual C++ 2015 Update 1; Visual C++ 2013 a předchozích verzích Visual C++ odmítnout kódu napsaného v tímto způsobem. Chování Visual C++ 2015 a Visual C++ 2015 Update 1 je nesprávný a není v souladu s C++ standard.  Visual Studio 2015 Update 2 odmítne kódu napsaného v tímto způsobem a místo toho vystavuje Chyba kompilátoru C2511.

   ```Output
    error C2511: 'void A::func(void) const': overloaded member function not found in 'A'
   ```

   Příklad (před)

   ```cpp
    struct A
    {
      static void func();
    };

    void A::func() const {}  // C2511
   ```

   Příklad (po)

   ```cpp
    struct A
    {
      static void func();
    };

    void A::func() {}  // removed const
   ```

- **Dopředná deklarace výčtu není povolený v kódu WinRT** (ovlivňuje `/ZW` jenom)

   Kód zkompilován pro prostředí Windows Runtime (WinRT) neumožňuje **výčtu** typy vpřed deklarovat, podobně jako při kompilaci spravovaného kódu C++ pro rozhraní .net Framework pomocí `/clr` přepínač kompilátoru. Toto chování je zajišťuje, že velikost výčet je vždy známé a je možné správně promítnout do systému typů WinRT. Kompilátor odmítne kódu napsaného v tímto způsobem a vyvolá chybu kompilátoru C2599 spolu s chyba kompilátoru C3197.

   ```Output
    error C2599: 'CustomEnum': the forward declaration of a WinRT enum is not allowed
   ```

   ```Output
    error C3197: 'public': can only be used in definitions
   ```

   Příklad (před)

   ```cpp
    namespace A {
      public enum class CustomEnum: int32;  // forward declaration; error C2599, error C3197
    }

    namespace A {
      public enum class CustomEnum: int32
      {
        Value1
      };
    }

    public ref class Component sealed
    {
    public:
      CustomEnum f()
      {
        return CustomEnum::Value1;
      }
    };
   ```

   Příklad (po)

   ```cpp
              // forward declaration of CustomEnum removed
    namespace A {
      public enum class CustomEnum: int32
      {
        Value1
      };
    }

    public ref class Component sealed
    {
    public:
      CustomEnum f()
      {
        return CustomEnum::Value1;
      }
    };
   ```

- **Přetížení bez členů operátor new a operátor delete se nedá deklarovat vložené** (úroveň 1 (`/W1`) na výchozím nastavení)

   Předchozí verze kompilátoru bez vyvolání upozornění, pokud nejsou členy **operátor new** a **operátor delete** funkce je deklarovaná jako inline. Kód napsaný v tímto způsobem je chybně vytvořený (vyžadováno žádné diagnostické) a může způsobit paměti problémy způsobené nový Neshoda a operátory (zejména při použití společně s velikostí dealokace), které může být obtížné diagnostikovat, odstranit. Kompilátor nyní vyvolá kompilátor varování C4595 vám pomůže identifikovat kód napsaný v tímto způsobem.

   ```Output
    warning C4595: 'operator new': non-member operator new or delete functions may not be declared inline
   ```

   Příklad (před)

   ```cpp
    inline void* operator new(size_t sz)  // warning C4595
    {
      ...
    }
   ```

   Příklad (po)

   ```cpp
    void* operator new(size_t sz)  // removed inline
    {
      ...
    }
   ```

   Oprava kódu, která je napsána tímto způsobem může vyžadovat, že definice operátorů přesunout mimo soubor hlaviček a do odpovídající zdrojový soubor.

### <a name="VS_Update3"></a> Vylepšení Visual Studio 2015 Update 3

- **std::is_convertable nyní rozpozná vlastní přiřazení** (standardní knihovna) předchozí verze `std::is_convertable` vlastnost typu nezjistili správně vlastní přiřazení typu třídy při jeho konstruktor kopie je odstraněna nebo soukromé. Nyní `std::is_convertable<>::value` správně nastavená na **false** při použití na typ třídy s odstraněný nebo soukromý kopírovací konstruktor.

   Neexistuje žádné diagnostiky kompilátoru přidružené k této změně.

   Příklad

   ```cpp
    #include <type_traits>

    class X1
    {
    public:
        X1(const X1&) = delete;
    };

    class X2
    {
    private:
        X2(const X2&);
    };

    static_assert(std::is_convertible<X1&, X1>::value, "BOOM");static_assert(std::is_convertible<X2&, X2>::value, "BOOM");
   ```

   V předchozích verzích aplikace Visual C++, předat statický kontrolní výrazy v dolní části v tomto příkladu, protože `std::is_convertable<>::value` bylo nesprávně nastaveno jejich **true**. Nyní `std::is_convertable<>::value` správně nastavená na **false**, způsobuje selhání statický kontrolní výrazy.

- **Nastavit na výchozí hodnotu nebo odstranit triviální kopírování a přesun konstruktorů specifikátory přístupu dodržování**

   Předchozí verze kompilátoru není zkontrolujte specifikátor přístupu nastavených výchozích nebo odstraněných triviální kopírování a přesun konstruktorů před povolením, která se má volat. Toto chování staré bylo nesprávné a není v souladu s standardu jazyka C++. V některých případech se vytvoří toto staré chování riziko generování tiché chybného kódu, což vede k modulu runtime nepředvídatelné chování. Kompilátor nyní zkontroluje specifikátor přístupu nastavených výchozích nebo odstraněných triviální kopírování a přesun konstruktorů k určení, zda může být volána a pokud ne, problémy kompilátoru C2248 upozornění ve výsledku.

   ```Output
    error C2248: 'S::S' cannot access private member declared in class 'S'
   ```

   Příklad (před)

   ```cpp
    class S {
    public:
       S() = default;
    private:
        S(const S&) = default;
    };

    void f(S);  // pass S by value

    int main()
    {
        S s;
        f(s);  // error C2248, can't invoke private copy constructor
    }
   ```

   Příklad (po)

   ```cpp
    class S {
    public:
       S() = default;
    private:
        S(const S&) = default;
    };

    void f(const S&);  // pass S by reference

    int main()
    {
        S s;
        f(s);
    }
   ```

- **Vyřazení podpory kódu ATL s atributy** (úroveň 1 (`/W1`) na výchozím nastavení)

   Předchozí verze kompilátoru nepodporuje kódu ATL s přidělenými atributy. Jako další fází odebrání podpory knihovny ATL s atributy kódu, který [začal v aplikaci Visual C++ 2008](https://msdn.microsoft.com/library/bb384632), s atributy kódu ATL je zastaralá. Kompilátor nyní vyvolá kompilátor varování C4467 pomáhá rozpoznat tento druh zastaralý kód.

   ```Output
    warning C4467: Usage of ATL attributes is deprecated
   ```

   Pokud chcete pokračovat, dokud se odebrala se podpora z kompilátoru použití kódu ATL s atributy, které toto upozornění vypněte předáním `/Wv:18` nebo `/wd4467` argumenty příkazového řádku pro kompilátor nebo přidáním `#pragma warning(disable:4467)` ve zdrojovém kódu.

   Příklad 1 (před)

   ```cpp
              [uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
    class A {};
   ```

   Příklad 1 (po)

   ```cpp
    __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) A {};
   ```

   Někdy potřebujete nebo chcete vytvořit souboru IDL souboru se vyhněte použití zastaralé atributů ATL, stejně jako v níže uvedeného ukázkového kódu

   Příklad 2 (před)

   ```cpp
    [emitidl];
    [module(name="Foo")];

    [object, local, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb")]
    __interface ICustom {
        HRESULT Custom([in] long l, [out, retval] long *pLong);
        [local] HRESULT CustomLocal([in] long l, [out, retval] long *pLong);
    };

    [coclass, appobject, uuid("9e66a294-4365-11d2-a997-00c04fa37ddb")]
    class CFoo : public ICustom
    {
        // ...
    };
   ```

   Nejprve vytvořte soubor \*.idl; vc140\*.idl vygeneruje soubor lze použít k získání obsahující rozhraní a poznámky souboru IDL.

   V dalším kroku přidejte krok MIDL vašeho sestavení, abyste měli jistotu, že jsou generovány definice rozhraní C++.

   Příklad 2 IDL (po)

   ```cpp
    import "docobj.idl";

    [
        object,local,uuid(9e66a290-4365-11d2-a997-00c04fa37ddb)
    ]

    interface ICustom : IUnknown {
        HRESULT  Custom([in] long l, [out,retval] long *pLong);
        [local] HRESULT  CustomLocal([in] long l, [out,retval] long *pLong);
    };

    [ version(1.0), uuid(29079a2c-5f3f-3325-99a1-3ec9c40988bb) ]
    library Foo
    {
        importlib("stdole2.tlb");
        importlib("olepro32.dll");
            [
                version(1.0),
                appobject,uuid(9e66a294-4365-11d2-a997-00c04fa37ddb)
            ]

        coclass CFoo {
            interface ICustom;
        };
    }
   ```

   Potom použijte ATL přímo v souboru implementace, stejně jako v následujícím příkladu kódu.

   Příklad 2 implementace (po)

   ```cpp
    #include <idl.header.h>
    #include <atlbase.h>

    class ATL_NO_VTABLE CFooImpl :
        public ICustom,
        public ATL::CComObjectRootEx<CComMultiThreadModel>
    {
    public:
        BEGIN_COM_MAP(CFooImpl)
        COM_INTERFACE_ENTRY(ICustom)
        END_COM_MAP()
    };
   ```

- **Předkompilované hlavičky (PCH) soubory a neshoda #include** (má vliv pouze `/Wall` `/WX`)

   Předchozí verze kompilátoru přijato neshoda `#include` direktivy ve zdrojových souborech mezi `-Yc` a `-Yu` kompilace při použití předkompilované hlavičky (PCH) soubory. Kód napsaný v tímto způsobem je už akceptuje kompilátor. Kompilátor nyní problémy kompilátor varování CC4598 vám pomůže identifikovat neshoda `#include` direktivy při použití souborů PCH.

   ```Output
    warning C4598: 'b.h': included header file specified for Ycc.h at position 2 does not match Yuc.h at that position
   ```

   Příklad (před):

   X.cpp (-Ycc.h)

   ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
   ```

   Z.cpp (-Yuc.h)

   ```cpp
    #include "b.h"
    #include "a.h"  // mismatched order relative to X.cpp
    #include "c.h"
   ```

   Příklad (po)

   X.cpp (-Ycc.h)

   ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
   ```

   Z.cpp (-Yuc.h)

   ```cpp
    #include "a.h"
    #include "b.h" // matched order relative to X.cpp
    #include "c.h"
   ```

- **Předkompilované hlavičky (PCH) soubory a neshoda adresáře souborů k zahrnutí** (má vliv pouze `/Wall` `/WX`)

   Předchozí verze kompilátoru přijato neshoda zahrnout adresáře (`-I`) argumenty příkazového řádku pro kompilátor mezi `-Yc` a `-Yu` kompilace při použití předkompilované hlavičky (PCH) soubory. Kód napsaný v tímto způsobem je už akceptuje kompilátor.   Kompilátor nyní problémy kompilátor varování CC4599 vám pomůže identifikovat neshoda zahrnout adresáře (`-I`) argumenty příkazového řádku při použití souborů PCH.

   ```Output
    warning C4599: '-I..' : specified for Ycc.h at position 1 does not match Yuc.h at that position
   ```

   Příklad (před)

   ```ms-dos
    cl /c /Wall /Ycc.h -I.. X.cpp
    cl /c /Wall /Yuc.h Z.cpp
   ```

   Příklad (po)

   ```ms-dos
    cl /c /Wall /Ycc.h -I.. X.cpp
    cl /c /Wall /Yuc.h -I.. Z.cpp
   ```

## <a name="whats-new-for-c-in-visual-studio-2013"></a>Co je nového v C++ v sadě Visual Studio 2013

### <a name="improved-iso-cc-standards-support"></a>Podpora standardů ISO vylepšené C/C++

#### <a name="compiler"></a>Kompilátor

Kompilátor jazyka Microsoft Visual C++ podporuje tyto funkce ISO C ++ 11 jazyka:

- Výchozí argumenty šablon pro šablony funkcí.
- Delegování konstruktorů
- Explicitní operátory převodu.
- Jednotná inicializace a seznamy inicializátorů.
- Nezpracované řetězcové literály.
- Variadické šablony.
- Šablony aliasů.
- Odstraněné funkce.
- Inicializátory členů nestatických dat (Nsdmi).
- Výchozí funkce. \*
- Podporuje tyto funkce jazyka ISO C99:
- _Bool
- Složené literály.
- Určené inicializátory.
- Míchání deklarací s kódem.
- Řetězec převod literálu na upravitelné hodnoty můžou být zakázáno pomocí nové možnosti kompilátoru `/Zc:strictStrings`. V C ++ 98 převod z řetězcových literálů na `char*` (a široký řetězec literálů na `wchar_t*`) byla zrušena. V C ++ 11 byl převod úplně odebrán. Ačkoli kompilátor může důsledně splňovat normy, místo toho poskytuje `/Zc:strictStrings` možnost tak, aby mohli převod řídit. Ve výchozím nastavení je možnost je vypnuta. Všimněte si, že při použití této možnosti v režimu ladění, STL nebude kompilovat.
- Přetypování rvalue/lvalue. S odkazy rvalue může C ++ 11 jasně rozlišovat mezi lvalues a rvalues. Dříve kompilátor toto neposkytl v konkrétních scénářích obsazení. Nová možnost kompilátoru `/Zc:rvalueCast`, byla přidána, aby splňovaly kompilátoru C++ Paper(see section 5.4, [expr.cast]/1) práce jazyka. Výchozí chování, pokud není tato možnost zadána, je stejné jako v sadě Visual Studio 2012.

> [!NOTE]
> Pro výchozí funkce pomocí = default k vyžádání konstruktorů s přesouváním a operátory přiřazení nepodporuje přesun.

### <a name="c99-libraries"></a>Knihovny systému C99

Deklarace a implementaci jsou přidány pro chybějící funkce v těchto záhlavích: math.h ctype.h, wctype.h, stdio.h, stdlib.h a wchar.h. Přidána jsou také nová záhlaví complex.h, stdbool.h fenv.h a inttypes.h implementace a pro všechny funkce v nich deklarované. Existují nové hlavičky obálky C++ (ccomplex cfenv, cinttypes, ctgmath) a spousta dalších je aktualizována (ccomplex cctype –, clocale –, cmath, cstdint, cstdio –, cstring, cwchar – a cwctype –).

### <a name="standard-template-library"></a>Standardní šablona knihovny

Podporu pro C ++ 11 explicitní operátory převodu, inicializační seznamy, oboru výčtů a variadické šablony.
Všechny kontejnery nyní podporují C ++ 11 detailní požadavky prvků.
Podpora pro tyto funkce C ++ 14:

- "Transparentní funktory operátorů" méně <>, větší <> navíc <>, se vynásobí <> a tak dále.
- make_unique<T>(args...) a make_unique < T [] > (n)
- cbegin()/cend() rbegin()/rend() a crbegin()/crend() nečlenské funkce.
- \<Atomic > obdržel četná vylepšení výkonu.
- \<type_traits > přijatých hlavní opravy stabilizace a kódu.

### <a name="breaking-changes"></a>Nejnovější změny

Tato vylepšená podpora standardů ISO C/C++ mohou vyžadovat změny existujícího kódu tak, aby odpovídá C ++ 11 a správně zkompiluje v jazyce Visual C++ v sadě Visual Studio 2013.

### <a name="visual-c-library-enhancements"></a>Vylepšení knihovny jazyka Visual C++

- C++ REST SDK je přidána. Má moderní implementaci C++ služeb REST.
- Je vylepšená podpora textur C++ AMP. Teď zahrnuje podporu pro mipmapy a nové způsoby vzorkování.
- Úkoly PPL podporují více technologií plánování a asynchronní ladění. Nová rozhraní API umožňují vytvářet úlohy PPL s normálními výsledky i podmínkami výjimky.

### <a name="c-application-performance"></a>Výkon aplikace v jazyce C++

- Automatický Vektorizér nyní rozpoznává a optimalizuje další vzory jazyka C++, aby váš kód běžel rychleji.
- Zvýšení kvality kódu platformy ARM a mikroarchitekturu Atom.
- konvence volání __vectorcall je přidána. Předejte argumenty typu vektoru pomocí konvence volání __vectorcall a použít vektorové Registry.
- Nové možnosti Linkeru. `/Gw` (Kompilátor) a `/Gy` přepínače (assembler) umožňují optimalizaci propojovacího programu a štíhlejší binární soubory.
- C++ AMP podpora sdílené paměti ke snížení nebo eliminaci kopírování dat mezi CPU a GPU.

### <a name="profile-guided-optimization-pgo-enhancements"></a>Vylepšení profil na základě optimalizace (PGO)

- Zlepšení výkonu snížením pracovní sady aplikací optimalizovaných pomocí PGO.
- Vývoj aplikací pro nové PGO pro prostředí Windows Runtime

### <a name="windows-runtime-app-development-support"></a>Podpora pro vývoj aplikací pro modul Runtime Windows

- **Podpora pro Boxed typy ve struktuře hodnot.**

   Nyní můžete určit typy hodnot s použitím pole, která může mít hodnotu null, například `IBox<int>^` nikoli **int**. To znamená, že pole mohou buď mít hodnotu nebo být roven **nullptr**.

- **Podrobnější informace o výjimce.**

   C++/CX podporuje nový model chyb Windows, který umožňuje zachycení a propagaci bohatých informací o výjimkách napříč binárním rozhraním aplikace (ABI); To zahrnuje volání zásobníku a o vlastní řetězce zpráv.

- **Object:: ToString() je nyní virtuální.**

   Nyní můžete přepsat ToString v uživatelem definované typy Windows Runtime ref.

- **Podpora pro zastaralé rozhraní API.**

   Veřejné rozhraní API Windows Runtime lze nyní označit jako zastaralé a doplnit vlastní zprávu, která se zobrazí jako varování při sestavení a může poskytnout pokyny k migraci.

- **Vylepšení ladicího programu.**

   Podpora pro definiční ladění nativního prostředí/JavaScript, diagnostiky výjimky Windows Runtime a asynchronní ladění (Windows Runtime a PPL) kódu.

> [!NOTE]
> Kromě funkcí specifických pro C++ a vylepšení, které jsou popsány v této části Další vylepšení v sadě Visual Studio vám mohou také pomoci psát lepší aplikace pro Windows Runtime.

### <a name="diagnostics-enhancements"></a>Zdokonalení diagnostiky

- Vylepšení ladicího programu. Podpora asynchronního ladění a ladění pouze můj kód.
- Kategorie analýzy kódu. Teď si můžete zobrazit kategorizovaný výstup z nástroje Code Analyzer můžete najít a opravit závadný kód.
- Diagnostika XAML. Nyní lze diagnostikovat odezvu uživatelského rozhraní a problémy spotřeba energie baterie ve vaší XAML.
- Grafika a vylepšení ladění GPU.
- Vzdálený záznam a přehrávání na skutečných zařízeních.
- Současně C++ AMP a procesoru ladění.
- Zlepšení diagnostiky C++ AMP runtime.
- Hlsl – ladění trasování výpočetního shaderu.

### <a name="3-d-graphics-enhancements"></a>Vylepšení 3D grafiky

- Obrázek podpory kanál pro obsahové materiály pro formát přednásobené alfa DDS.
- Editor obrázků pro vykreslování používá interně přednásobené alfa a tím se vyhnete vykreslování artefaktů, jako je tmavé olemování.
- Editory modelu a obrazu. Vytvoření uživatelem definovaných filtrů je nyní podporována v Návrháři shaderu v Editoru obrázku a editoru modelů.

### <a name="ide-and-productivity"></a>IDE a produktivita

**Vylepšili jsme formátování kódu**. Můžete provést další nastavení formátování kódu jazyka C++. Pomocí těchto nastavení můžete řídit nový řádek umístění složené závorky a klíčová slova, odsazení, řádkování a zalomení řádku. Po dokončení příkazů a bloků a po vložení kódu do souboru je kód automaticky formátován.

**Uzavírání hranatých závorek.** Kód jazyka C++ nyní automaticky dokončuje koncové znaky, které odpovídají těmto počátečním znakům:

- {(složená závorka)
- [(hranatá závorka)
- ((závorek).
- ' (jednoduchá uvozovka)
- "(uvozovky)

**Funkce další automatického dokončování jazyka C++.**

- Přidá středník pro typy tříd.
- Dokončí závorky u nezpracovaných řetězcových literálů.
- Dokončuje Víceřádkové komentáře (/\* \*/)

**Najít všechny odkazy** nyní automaticky vyhodnocuje a filtruje odkazy na pozadí poté, co zobrazí seznam odpovídajících textových položek.

**Členů založení na kontextu filtrování seznamu.** Nepřístupní členové jsou filtrovány ze seznamů členů IntelliSense. Například soukromé členy nejsou zobrazeny v seznamu členů, pokud neupravujete kód, který typ implementuje. Při otevření seznamu členů můžete stisknout **Ctrl**+**J** odebrat jednu úroveň filtrování (platí pouze pro aktuální okno seznam členů). Stisknutím klávesy **Ctrl**+**J** znovu a odstranit textové filtrování a zobrazit každého člena.

**Procházení parametru nápovědy.** Podpis zobrazené funkce v popisku parametru nápovědy nyní změny podle počtu parametrů, které jste zadali ve skutečnosti, namísto pouhého zobrazení libovolného podpisu a bez aktualizace podle aktuálního kontextu. Parametr nápovědy také funguje správně, který se zobrazí ve vnořených funkcích.

**Přepínač záhlaví/kódový soubor.** Teď můžete přepínat mezi záhlavím a odpovídajícím kódovým souborem pomocí příkazu na nabídce zkratek nebo klávesové zkratky.

**V okně vlastností umožňující změnu velikosti projektu C++**

**Automatické generování kódu obslužné rutiny události v C++/CX a C++vyhodnocovací.**  Když píšete kód k přidání obslužné rutiny události v C++/CX nebo C++vyhodnocovací soubor kódu, editor může automaticky generovat definice delegáta instance a obslužnou rutinu události. Okno popisku se zobrazí, pokud automaticky generovaný kód obslužné rutiny události.

**Zvýšení povědomí o dpi.** Nastavení sledování DPI v souborech manifestu aplikace nyní podporuje nastavení "Za sledování vysoké rozlišení DPI".

**Rychlejší přepínání konfigurace.** Pro velké aplikace lze přepínání konfigurace – zejména následné operace přepínání – provést mnohem rychleji.

**Časové efektivita sestavení.** Četné optimalizace a využití více jader umožňují urychlit sestavení, zejména u velkých projektů. Přírůstková sestavení pro aplikace C++ odkazující na C++ WinMD jsou také mnohem rychlejší.

## <a name="whats-new-for-c-in-visual-studio-2012"></a>Co je nového v C++ v sadě Visual Studio 2012

### <a name="improved-c11-standards-support"></a>Podpora vylepšené standardů C ++ 11.

#### <a name="standard-template-library"></a>Standardní šablona knihovny

- Podporu pro nové hlavičky STL: \<atomické >, \<chrono >, \<condition_variable >, \<filesystem >, \<budoucí >, \<vzájemně vyloučený přístup >, \<poměr >, a \< vlákno >.
- Pokud chcete optimalizovat využití prostředků paměti, jsou kontejnery nyní menší. Například v x86 ve verzi s výchozím nastavením `std::vector` má zmenšit z 16 bajtů v sadě Visual Studio 2010, 12 bajtů v sadě Visual Studio 2012 a `std::map` má zmenšit z 16 bajtů v sadě Visual Studio 2010 na 8 bajtů v sadě Visual Studio 2012.
- Jako povolené, ale nevyžadováno standardem C ++ 11 byly implementovány iterátory SCARY.

#### <a name="other-c11-enhancements"></a>Další C ++ 11 vylepšení

- Na základě rozsahu smyček for. Můžete napsat robustnějších smyček, které využívají službu kolekcí ve formuláři pro pole, kontejnerů STL a prostředí Windows Runtime (deklarace pro rozsah: výraz). To je součástí základní jazykové podpory.
- Jsou výrazy lambda, které jsou bloky kódu, které začínají [] představení prázdné lambda a zaznamenají žádné místní proměnné, se teď implicitně převést na ukazatele funkcí, podle potřeby standardem C ++ 11.
- S vymezeným oborem výčty podporují. Enum – klíč třídy výčtu C++ se teď podporuje. Následující kód ukazuje, jak tento klíč výčtu se liší od předchozí chování výčtu.

   ```cpp
  enum class Element { Hydrogen, Helium, Lithium, Beryllium };
  void func1(Element e);
  func1(Hydrogen); // error C2065: 'Hydrogen' : undeclared identifier
  func1(Element::Helium); // OK
   ```

### <a name="windows-runtime-app-development-support"></a>Podpora pro vývoj aplikací pro modul Runtime Windows

- **Nativní uživatelské rozhraní založené na XAML model**. Pro aplikace Windows Runtime můžete použít nový model nativního uživatelského rozhraní založeného na XAML.
- **Rozšíření Visual C++ komponent**. Tato rozšíření zjednodušit využití objektů prostředí Windows Runtime, které jsou nezbytnou součástí aplikace Windows Runtime. Další informace najdete v tématu [plán pro prostředí Windows Runtime aplikace s využitím C++ ](../windows/universal-windows-apps-cpp.md) a [Visual C++ referenční informace k jazyku (C++/CX)](../cppcx/visual-c-language-reference-c-cx.md)
- **Hry rozhraní DirectX**. Zajímavé hry můžete vyvíjet s využitím nových rozhraní DirectX podpory pro aplikace Windows Runtime.
- **Zprostředkovatele komunikace XAML nebo DirectX**. Aplikace Windows Runtime, používající XAML a rozhraní DirectX nyní efektivně spolupracovat.
- **Vývoj DLL komponenty Windows Runtime**. Součást knihovny DLL vývoj díky rozšiřitelné prostředí Windows Runtime.

### <a name="compiler-and-linker"></a>Kompilátoru a Linkeru

- **Automatický vektorizér**. Kompilátor analyzuje smyčky ve vašem kódu a kde je možné, vydá pokyny, které používají vektoru zaregistruje a pokyny, které jsou k dispozici ve všech moderní procesorů. Díky tomu smyčky běžel rychleji. (Instrukce procesoru jsou označovány jako SSE, Streaming SIMD Extensions). Není nutné k povolení nebo požádat o tyto optimalizace, protože se automaticky použije.
- **Automatický paralelizér**. Kompilátor může analyzovat smyčky ve vašem kódu a generování pokynů, které šíří výpočty napříč více jader nebo procesorů. Díky tomu smyčky běžel rychleji. Tato optimalizace musí žádosti, protože není povolená ve výchozím nastavení. V mnoha případech umožňuje zahrnout `#pragma loop(hint_parallel(N))` ve vašem kódu těsně před smyček, které mají paralelizované.
- Automatický paralelizér a automatický vektorizér vzájemně spolupracují, aby výpočty jsou rozděleny mezi více jádry a kód na každé jádro používá jeho vektorové Registry.

### <a name="new-in-visual-studio-2012-update-1"></a>Novinka ve Visual Studio 2012 Update 1

Při sestavování kódu C++ jako cíl Windows XP.
Můžete použít kompilátor jazyka Visual C++ a knihoven a cíl Windows XP a Windows Server 2003.

#### <a name="parallel-programming-support"></a>Paralelní programování podpory

##### <a name="c-accelerated-massive-parallelism-amp"></a>C++ Accelerated Massive Parallelism (AMP)

C++ AMP zrychlí provádění kódu jazyka C++ využitím hardwaru paralelizovaného pro data, která je běžně přítomen jako GPU na samostatné grafické kartě. Model programování C++ AMP zahrnuje vícerozměrná pole, indexování, přenos paměti, rozložení a knihovnu matematických funkcí. Pomocí omezení kompilátoru a rozšíření jazyka C++ AMP, můžete řídit, jak jsou data přenášena z procesoru do GPU a zpět.

**Ladění.** Možnosti ladění pro aplikace, které používají C++ AMP cílit na GPU je stejné jako ladění pro jiné aplikace C++. To zahrnuje novou paralelní ladění doplňky, které byly zmíněny dříve.

**Profilace.** Nyní je profilování podpora GPU aktivitu, která je založena na C++ AMP a ostatní programovací modely založené na rozhraní Direct3D.

#### <a name="general-parallel-programming-enhancements"></a>Vylepšení obecné paralelní programování

S hardwarem Přesun na vícejádrových a mnohojádrová architektury můžou vývojáři už nespoléhají na stále se zvětšujícím rychlosti hodin od jednoho jádra. Paralelní programování v modulu Runtime souběžnosti podpory umožňuje vývojářům využívat tyto nové architektury.
V sadě Visual Studio 2010 byly výkonné paralelizace knihovny C++, jako jsou knihovny Ppl zavedení, společně s funkcí, které využít souběžnosti vyjádření kanály toku dat sofistikované. V sadě Visual Studio 2012 se rozšířily a poskytovat lepší výkon, další ovládací prvek a bohatší podporu pro ppl, že vývojáři nepotřebuje většinu těchto knihoven. Široké nabídky teď zahrnuje:

- Bohaté možnosti založené na úlohách programovací model, který podporuje asynchronii a pokračování.
- Paralelní algoritmy, které podporují paralelismu forku spojení (parallel_for, parallel_for spřažení, parallel_for_each, parallel_sort –, parallel_reduce, parallel_transform).
- Bezpečná pro souběžnost kontejnery, které poskytují bezpečné pro vlákna verzích std datové struktury, například priority_queue –, fronty, vektoru a mapy.
- Asynchronní knihovnou agentů, které mohou vývojáři express kanály toku dat, které přirozeně rozložit na souběžné jednotky.
- Přizpůsobitelné Plánovač a prostředků manažera pro usnadnění smooth složení tyto vzory se dají v tomto seznamu.

##### <a name="general-parallel-debugging-enhancements"></a>Vylepšení ladění paralelní obecné

Kromě **paralelní úlohy** okno a **paralelní zásobníky** okně Visual Studio 2012 nabízí novou **paralelního sledování** okna tak, aby můžete zkoumat hodnoty výraz napříč všemi vlákna a procesy a provést řazení a filtrování na výsledek. Můžete také použít vlastní vizualizéry rozšířit okno a napříč všechna okna nástrojů můžete využít novou podporu více procesů.

### <a name="ide"></a>IDE – integrované vývojové prostředí

**Šablony sady Visual Studio podporují.** Teď můžete použít technologii šablony sady Visual Studio do šablon projektů a položek Autor C++.

**Načtení asynchronní řešení.** Projekty jsou nyní úlohy načítány asynchronně – klíčových částí tohoto řešení první, takže můžete začít pracovat rychleji.

**Automatické nasazení pro vzdálené ladění.** Zjednodušili jsme nasazení soubory pro vzdálené ladění v jazyce Visual C++. **Nasadit** možnost v místní nabídce projektu automaticky zkopíruje do vzdáleného počítače soubory, které jsou určené ve vlastnostech ladění konfigurace. Ruční kopírování souborů do vzdáleného počítače se už nevyžaduje.

**C++/ Rozhraní příkazového řádku IntelliSense.** C++/ CLI nyní obsahuje plnou podporu technologie IntelliSense. Funkce technologie IntelliSense, jako je rychlé informace, parametr nápovědy, seznam členů a automatické dokončování prováděna pro C++vyhodnocovací. Kromě toho další technologie IntelliSense a prostředí IDE vylepšení uvedených v tomto dokumentu fungovat i pro C++vyhodnocovací.

**Richer IntelliSense Tooltips.** Popisky rychlé informace technologie IntelliSense jazyka C++ nyní zobrazit informace o stylu bohatší dokumentační komentáře XML. Pokud používáte rozhraní API z knihovny – například C++ AMP –, který se dokumentační komentáře XML a popisu tlačítka technologie IntelliSense zobrazí další informace než jenom deklarace. Také pokud váš kód obsahuje komentáře dokumentace XML, popisy technologie IntelliSense se zobrazí podrobnější informace.

**Konstrukce kódu jazyka C++.** Kostru kód je k dispozici pro přepínač, if-else, smyčky a další základní konstrukcí, v rozevíracím seznamu pro seznam členů. Vyberte část kódu, ze seznamu a vložit ho do svého kódu a potom vyplňte požadované logiku. Můžete také vytvořit vlastní vlastní části kódu pro použití v editoru.

**Seznam členů rozšíření.** **Seznam členů** rozevíracího seznamu se zobrazí automaticky při psaní kódu v editoru kódu. Výsledky se filtrují tak, aby pouze důležité členy se zobrazí při psaní. Můžete řídit druh filtrování logiku, která používá seznam členů – v **možnosti** dialogové okno pod **textový Editor** > **C/C++**  >  **Advanced**.

**Sémantického barevného zvýraznění.** Typy, výčty, makra a další tokeny jazyka C++ nyní mají zabarvení ve výchozím nastavení.

**Zvýraznění odkazů.** Výběrem symbolu teď zvýrazní všechny výskyty symbolu v aktuálním souboru. Stisknutím klávesy **Ctrl**+**Shift**+**šipka nahoru** nebo **Ctrl**+**Shift**  + **Šipka dolů** k procházení zvýrazněných odkazů. Můžete vypnout tato funkce **možnosti** dialogovém okně **textový Editor** > **C/C++** > **Upřesnit**.

### <a name="application-lifecycle-management-tools"></a>Nástroje pro správu životního cyklu aplikací

#### <a name="static-code-analysis"></a>Analýza statického kódu

Aktualizovali jsme statické analýzy pro jazyk C++ poskytnout bohatší kontextové informace o chybě, více pravidel analýzy a lepší analýzu výsledků. V novém okně analýzy kódu můžete filtrovat zprávy podle klíčového slova, projektu a závažnosti. Při výběru zprávy v okně řádku v kódu, kde byla aktivována. zpráva je zvýrazněn v editoru kódu. U určitých upozornění C++ zpráva uvádí zdrojové řádky, které ukazují provádění cestu, která vede k upozornění; rozhodovací body a důvody přijetí této konkrétní cesty jsou zvýrazněné.
Analýza kódu je součástí většině edicí sady Visual Studio 2012. V Professional, Premium a Ultimate Edition jsou zahrnuté všechna pravidla. Ve verzích Express pro Windows 8 a Windows Phone jsou zahrnuty pouze těch nejdůležitějších upozornění. Analýza kódu není zahrnut v edici Express for Web.
Tady jsou některé další vylepšení analýzy kódu:

- Nová upozornění souběžnosti umožňuje vyhnout se souběžnosti chyby pomocí a ujistěte se, že používáte správný zámku oborů ve vícevláknových programů jazyka C/C++. Analyzátor zjistí potenciální konflikty časování, jiného pořadí uzamčení, volající/volaný zamykání porušení smlouvy, neodpovídající synchronizační operace a jiné chyby souběžnosti.
- Můžete určit, že pravidla jazyka C++, že chcete použít pro spuštění analýzy kódu pomocí sad pravidel.
- V **analýzy kódu** okně můžete vložit do zdrojového kódu – Direktiva pragma, které potlačí vybrané upozornění.
- Pomocí nové verze poznámky jazyk zdrojového kódu Microsoft (SAL) pro popis, jak funkce používá parametry předpoklady, že ji provádí a záruky, že můžete zvýšit přesnosti a úplnosti statické analýzy kódu Díky po dokončení.
- Podpora pro 64bitové projekty C++.

#### <a name="updated-unit-test-framework"></a>Aktualizované testování částí

Zápis testů jednotek C++ pomocí novém rozhraní testování částí C++ v sadě Visual Studio. Přidejte nová jednotka zkušebního projektu do existujícího řešení C++ vyhledáním projekt testu jednotek C++ šablony v kategorii Visual C++ v dialogovém okně Nový projekt. Zahájit zápis testování částí v generované provizorního kódu TEST_METHOD Unittest1.cpp souboru. Při zápisu testovacího kódu sestavte řešení. Pokud chcete spustit testy, otevřete **Průzkumník testu jednotek** okno výběrem **zobrazení** > **ostatní Windows** > **testu jednotek Průzkumník**a potom v místní nabídce pro testovací případ má, zvolte **spustit vybraný test**. Po dokončení spuštění testu můžete zobrazit výsledky testů a informace o trasování zásobníku další ve stejném okně.

#### <a name="architecture-dependency-graphs"></a>Grafy závislosti architektury

Pro lepší pochopení kódu teď můžete generovat grafy závislosti pro binární, třídy a oboru názvů a zahrnout soubory v řešení. V panelu nabídky zvolte **architektura** > **Generovat graf závislosti**a potom **pro řešení** nebo **pro soubor zahrnutí**vygenerujte graf závislosti. Po dokončení generování grafu můžete prozkoumat rozbalením každého uzlu, další vztahů závislosti díky přesunu mezi uzly a procházení zdrojového kódu výběrem **zobrazit obsah** na místní nabídku pro uzel. Generovat graf závislostí pro zahrnuté soubory v místní nabídce pro zdrojový soubor \*.cpp nebo záhlaví \*.h souborů, zvolte **Generovat graf vložených souborů**.

#### <a name="architecture-explorer"></a>Průzkumník architektury

S použitím **Průzkumník architektury**, můžete prozkoumat prostředky v C++ řešení, projektů nebo soubory. V panelu nabídky zvolte **architektura** > **Windows** > **Průzkumník architektury**. Můžete vybrat uzel, který vás zajímá, například **zobrazení tříd**. V tomto případě pravé straně okna nástroje je rozbalený seznam oborů názvů. Pokud zvolíte možnost oboru názvů, nový sloupec zobrazuje seznam tříd, struktur a výčty v tomto oboru názvů. Můžete dál prozkoumat tyto prostředky, nebo se vrátit zpět na sloupec úplně vlevo spusťte další dotaz. Zobrazit **vyhledávání kódu pomocí Průzkumníka architektury**.

#### <a name="code-coverage"></a>Pokrytí kódu

Pokrytí kódu je aktualizovaná na dynamicky instrumentace binárních souborů v době běhu. To snižuje nároky na konfigurace a poskytuje lepší výkon. Může také shromažďovat data pokrytí kódu z testů jednotek pro aplikace v C++. Při testování jednotek C++, kterou jste vytvořili, můžete použít **Průzkumník testu jednotek** ke zjišťování testů v rámci vašeho řešení. Chcete-li spustit testy jednotek a shromažďování dat o pokrytí kódu, v **Průzkumník testu jednotek**, zvolte **analyzovat pokrytí kódu**. Můžete zkontrolovat výsledky pokrytí kódu v **výsledky pokrytí kódu** okno – v panelu nabídky zvolte **testovací** > **Windows**  >   **Výsledky pokrytí kódu**.

## <a name="whats-new-for-c-in-visual-studio-2010"></a>Co je nového v C++ v sadě Visual Studio 2010

### <a name="c-compiler-and-linker"></a>Kompilátor jazyka C++ a propojovací program

**Auto – klíčové slovo.** **Automaticky** – klíčové slovo má nový účel. Použít výchozí význam **automaticky** klíčového slova pro deklarování proměnné, jejíž typ je odvozen z výrazu inicializace při deklaraci proměnné. `/Zc:auto` – Možnost kompilátoru vyvolá nový nebo předchozí význam **automaticky** – klíčové slovo.

**decltype – specifikátor typu.** **Decltype** specifikátor typu vrací typ zadaného výrazu. Použití **decltype** specifikátor typu v kombinaci s **automaticky** – klíčové slovo Chcete-li deklarovat typ, který je komplexní nebo známé pouze pro kompilátor. Například pomocí kombinace k deklarování šablony funkce, jejíž návratový typ závisí na typech šablony argumentů. Nebo deklarování šablony funkce, která volá jinou funkci a potom vrátí návratový typ volané funkce.

**Výrazy lambda.** Funkce lambda mají tělo funkce, ale žádný název. Lambda funkce se kombinují nejlepší vlastnosti ukazatele na funkce a objekty funkce. Použijte funkci lambda samostatně, jako parametr funkce šablon místo objekt funkce, nebo společně s **automaticky** klíčového slova pro deklarování proměnné, jejíž typ je výraz lambda.

**Odkazy rvalue.** Deklarátor odkazu r-hodnoty (& &) deklaruje odkaz na r-hodnoty. Rvalue reference vám umožňuje používat přesunutí sémantiky a dokonalé předávání k tvorbě efektivnější konstruktory, funkcí a šablony.

**static_assert Declaration.** A **static_assert** deklarace testuje výraz softwaru v době kompilace, na rozdíl od jiných kontrolní výraz mechanismů, které testují v době běhu. Pokud výraz se nezdaří, kompilace se nezdaří a vydává zadanou chybovou zprávou.

**klíčová slova nullptr a __nullptr.** Kompilátor Visual C++ vám umožní používat **nullptr** – klíčové slovo nativního kódu nebo spravovaného kódu. **Nullptr** – klíčové slovo určuje, že popisovač objektu, vnitřní ukazatel nebo typ nativní ukazatel neukazuje na objekt. Kompilátor interpretuje **nullptr** být při použití spravovaného kódu `/clr` – možnost kompilátoru a nativní kód, když použijete `/clr` možnost.
Specifické pro Microsoft **__nullptr** – klíčové slovo má stejný význam jako **nullptr**, ale se vztahuje pouze na nativní kód. Pokud kompilujete pomocí nativního kódu C/C++ `/clr` – možnost kompilátoru, kompilátor nemůže určit, jestli **nullptr** – klíčové slovo je nativní nebo spravovaný termín. Aby váš záměr vymazat pro kompilátor pomocí klíčového slova nullptr můžete zadat jako spravované a **__nullptr** k určení nativní termínu.

**/ Zc: trigraphs – možnost kompilátoru.** Ve výchozím nastavení podpora trigraphs je vypnutá. Použití `/Zc:trigraphs` povolení podpory trigraphs – možnost kompilátoru.
Trigraf se skládá ze dvou po sobě jdoucími otazníky (?) následovaný znakem třetí jedinečný. Kompilátor nahradí trigraph na odpovídající znak interpunkce. Například, kompilátor nahradí?? = trigraph znakem # (znak čísla). Použití trigraphs ve zdrojových souborech jazyka C, které používají znakovou sadu, která obsahuje některá interpunkční znaménka.

**Nová možnost optimalizace na základě profilu.** PogoSafeMode je nová možnost optimalizace na základě profilu, který umožňuje určit, jestli se má použít nouzový režim nebo rychlém režimu při optimalizaci aplikace. Nouzový režim je bezpečná pro vlákno, ale je pomalejší než rychlém režimu. Rychlý režim je výchozí chování.

**Nové nostdlib – možnost Common Language Runtime (CLR).** Přidána nová možnost pro `/clr` (kompilace Common Language Runtime). Pokud různé verze stejné knihovny jsou zahrnuty, objeví se chyba při kompilaci. Nová možnost umožňuje vyloučit výchozí knihovny CLR tak, aby váš program můžete použít zadanou verzi.

**Nové direktivy detect_mismatch – Direktiva pragma.** Detect_mismatch direktiv pragma umožňuje umístit klíčové slovo ve vašich souborech, které je ve srovnání další značky, které mají stejný název. Pokud existuje více hodnot stejného názvu, vyvolá linker chybu.

**Vnitřní funkce XOP, Fma4 a LWP vnitřních objektů.** Nový vnitřní funkce byly přidány pro podporu XOP vnitřní objekty přidány pro Visual Studio 2010 SP1, přidá FMA4 vnitřních objektů pro Visual Studio 2010 SP1 a přidali LWP vnitřních objektů pro Visual Studio 2010 SP1 procesoru technologie. Použijte __cpuid __cpuidex k určení, které procesor technologie jsou podporovány v určitém počítači.

### <a name="visual-c-projects-and-the-build-system"></a>Projekty Visual C++ a systému sestavení

**MSBuild.** Visual C++ řešení a projekty jsou nyní integrovány pomocí MSBuild.exe, která nahrazuje VCBuild.exe. Nástroj MSBuild je stejný nástroj pro sestavení flexibilní, rozšiřitelné a založený na formátu XML, který se používá v jiných jazycích sady Visual Studio a typy projektů. Z důvodu této změny soubory projektu Visual C++ teď použít formát souboru XML a mají příponu názvu souboru .vcxproj. Soubory projektu Visual C++ z předchozích verzí sady Visual Studio se automaticky převedou na nový formát souboru.

**Adresáře VC ++.** Nastavení adresáře VC ++ se nyní nachází na dvou místech. Pomocí stránky vlastností projektu můžete nastavit hodnoty jednotlivých projektů pro adresáře VC ++. Použití **Správce vlastností** a seznam vlastností pro globální nastavení podle konfigurace hodnoty adresáře VC ++.

**Závislosti projektu k projektu.** V dřívějších verzích definované závislostí mezi projekty byly uloženy v souboru řešení. Když tato řešení se převedou na nový formát souboru projektu, závislosti jsou převedeny na odkazy typu projekt projekt. Tato změna může ovlivnit aplikace, protože koncepty závislostí řešení a odkazy typu projekt projekt jsou různé.

**Makra a proměnných prostředí.** Nové makru _ITERATOR_DEBUG_LEVEL vyvolá podpora ladění iterátorů. Použijte toto makro místo starší _SECURE_SCL a _HAS_ITERATOR_DEBUGGING makra.

### <a name="visual-c-libraries"></a>Knihovny jazyka Visual C++

**Knihovny Runtime souběžnosti.** Rozhraní Concurrency Runtime podporuje aplikace a součásti, které běží současně a je rozhraní pro programování souběžných aplikací v jazyce Visual C++. Pro podporu programování souběžných aplikací, poskytuje knihovna paralelních vzorů (PPL) pro obecné účely kontejnery a algoritmy pro provádění dosáhnout jemně odstupňovaného paralelismu. Asynchronní knihovnou agentů poskytuje programovací model založený na objektu actor a message passing rozhraní pro hrubých toku dat a paralelní zpracování úloh.

**Standardní knihovna C++.** Následující seznam popisuje mnoho změn, které byly provedeny standardní knihovny C++.

- Nové funkce jazyka r-hodnoty odkaz C++ se použil k implementaci sémantiky přesunutí a dokonalé předávání pro mnoho funkcí v knihovně Standard Template Library. Sémantiky přesunutí a dokonalé předávání výrazně zlepšit výkon operace, které přidělit nebo přiřazení proměnných nebo parametrech.
- Odkazy rvalue slouží také k implementaci nového `unique_ptr` třídy, což je bezpečnější typ inteligentního ukazatele než `auto_ptr` třídy. `unique_ptr` Třídy je striktní sémantiku vlastnictví aniž by to ovlivnilo bezpečný přístup z více pohyblivých, ale ne kopírovatelné implementuje a dobře funguje s kontejnery, které jsou odkazy rvalue. `auto_ptr` Třída je zastaralá.
- Patnáct nové funkce, například `find_if_not`, `copy_if`, a `is_sorted`, byly přidány do \<algoritmus > záhlaví.
- V \<paměti > hlavičky, nová funkce make_shared je pohodlné, robustní a efektivní způsob, jak vytvořit sdílený ukazatel na objekt ve stejnou dobu vytvoření objektu.
- Jsou podporovány jednotlivě propojený seznam \<forward_list – > záhlaví.
- Nové `cbegin`, `cend`, `crbegin`, a `crend` poskytují členské funkce `const_iterator` , který prochází vpřed nebo vzad přes kontejneru.
- \<System_error > Podpora zpracování chyb nízké úrovně systému záhlaví a související šablony. Členové `exception_ptr` třída umožňuje přenášet výjimky mezi vlákny.
- \<Codecvt – > záhlaví podporuje převod různých kódování znaků Unicode, jiné kódování.
- \<Alokátorů > záhlaví definuje několik šablon, které pomáhají přidělit a uvolnit bloky paměti pro kontejnery založené na uzlu.
- Existují celou řadu aktualizací \<náhodné > záhlaví.

### <a name="microsoft-foundation-class-mfc-library"></a>Knihovny Microsoft Foundation Class (MFC)

**Funkce Windows 7.** MFC podporuje mnoho funkcí Windows 7, například pás karet uživatelské rozhraní (UI), na hlavním panelu, seznamy odkazů, s kartami miniatury, náhledy, indikátor průběhu, překrytí ikony a indexování. Protože MFC automaticky podporuje mnoho funkcí Windows 7, pravděpodobně nemáte k úpravě stávající aplikace. Pro podporu dalších funkcí v nové aplikace, použijte k určení funkce, které chcete použít Průvodce aplikací knihovny MFC.

**Sledování více dotyků.** MFC podporuje aplikace, které mají více dotyků uživatelského rozhraní, například aplikace, které jsou vytvořené pro operační systém Microsoft Surface. Více dotyků aplikace dokáže zpracovat zprávy Windows dotykového ovládání a gesta zpráv, které jsou kombinací touch zprávy. Pouze registrace vaší aplikace pro dotykové ovládání a gesta události a operačního systému bude směrovat více dotyků do obslužné rutiny události.

**Sledování vysokých hodnot DPI.** Ve výchozím nastavení nyní jsou vysoce rozlišením DPI aplikace MFC Pokud je stav aplikace vysokých hodnot DPI (vysoká bodů na palec) vědět, můžete škálovat operačního systému windows, text a další prvky uživatelského rozhraní pro aktuální rozlišení obrazovky. Tento znamená, že škálován image je pravděpodobně být správně rozloží a není oříznut nebo pixelován.

**Restartujte správce.** Správce restartování automaticky ukládá dokumenty a restartování aplikace, pokud se neočekávaně zavře nebo restartuje. Například můžete použít správce restartování spusťte aplikaci po zavření automatických aktualizací. Další informace o tom, jak nakonfigurovat svoji aplikaci pomocí Správce restartování najdete v tématu **jak: Přidání podpory správce restartování**.

**CTaskDialog.** `CTaskDialog` Třídy je možné použít místo standardní `AfxMessageBox` okno se zprávou. `CTaskDialog` Třída zobrazuje a shromažďuje informace než standardní zprávou.

#### <a name="safeint-library"></a>SafeInt – knihovna

Nové SafeInt – knihovna provádí aritmetické operace bezpečné tento účet pro přetečení celého čísla. Tato knihovna také porovnává různé typy celých čísel.

#### <a name="new-active-template-library-atl-macros"></a>Nová makra aktivní šablony knihovny (ATL)

ATL a rozbalte funkce PROP_ENTRY_TYPE a PROP_ENTRY_TYPE_EX Přibyla nová makra. PROP_ENTRY_INTERFACE a PROP_ENTRY_INTERFACE_EX umožňují přidat seznam CLSID platný. PROP_ENTRY_INTERFACE_CALLBACK a PROP_ENTRY_INTERFACE_CALLBACK_EX umožňují určit funkce zpětného volání k určení, zda je identifikátor CLSID platný.

#### <a name="analyze-warnings"></a>/ analyze upozornění

Většina `/analyze` upozornění (analýzy kódu Enterprise) byly odebrány z knihovny Run-Time C (CRT), knihovna MFC a ATL.

#### <a name="animation-and-d2d-support"></a>Animace a D2D podpory

MFC teď podporuje animace a grafické rozhraní Direct2D. Knihovna MFC má několik nových tříd knihovny MFC a funkcí pro podporu této funkce. Existují také dva nové návody, které ukazují, jak přidat objekt D2D a objekt animace do projektu. Tyto kurzy jsou **názorný postup: Přidání objektu D2D do projektu MFC** a **názorný postup: Přidání animace do projektu MFC**.

### <a name="ide"></a>IDE – integrované vývojové prostředí

**Vylepšená technologie IntelliSense.** Rychlejší, přesnější a schopna zpracovávat větší projektů byl zcela přepracován technologie IntelliSense jazyka Visual C++. K dosažení toto vylepšení integrovaného vývojového prostředí rozlišuje mezi jak vývojář, zobrazení a upraví zdrojový kód a použití zdrojový kód a projekt nastavení rozhraní IDE k vytvoření řešení.
Z důvodu tohoto oddělení povinností, procházení funkce **zobrazení tříd** a nové **přejít na** dialogové okno jsou zpracovány systémem, který je založen na nový Server SQL database klasické pracovní plochy (SDF) souboru, který nahradí původní soubor Procházet (.ncb) bez kompilace. Funkce technologie IntelliSense, jako je rychlé informace, automatické dokončování a parametr pomůžou analyzovat jednotky překladu pouze v případě potřeby. Funkcích pro hybridní nasazení jako je například nový **hierarchie volání** okno použijte kombinaci funkcí IntelliSense a procházení.
Vzhledem k tomu, že IntelliSense zpracovává pouze informace, které budete potřebovat v okamžiku, rozhraní IDE je rychlejší reakce. Protože jsou více aktuální informace, integrované vývojové prostředí zobrazení a windows jsou také přesnější. Protože integrovaného vývojového prostředí infrastruktury je lépe uspořádat, více možností a větší škálovatelnost, je zpracovat větší projekty.

**Vylepšená technologie IntelliSense chyby.** Rozhraní IDE lépe zjistí chyby, které mohou způsobit ztrátu technologie IntelliSense a zobrazí se červené podtržení vlnovkou pod nimi. Kromě toho rozhraní IDE hlásit chyby IntelliSense **okno Seznam chyb**. Chcete-li zobrazit kód, který je příčinou problému, klikněte dvakrát na chybu v **okno Seznam chyb**.

**#include funkce automatického dokončování.** Integrované vývojové prostředí podporuje automatické dokončování pro `#include` – klíčové slovo. Po zadání `#include`, rozhraní IDE vytvoří pole rozevíracího seznamu platnou hlavičku souborů. Pokud budete pokračovat zadáním názvu souboru, rozhraní IDE filtruje seznam podle vaší položce. V kterékoli fázi můžete ze seznamu vyberte soubor, který chcete zahrnout. To vám umožňuje rychle zahrnout soubory bez znalosti názvu souborů.

**Přejděte do.** **Přejít na** dialogové okno umožňuje pole můžete vyhledat všechny symboly a soubory v projektu, které odpovídají zadaného řetězce. Výsledky hledání jsou revize hned při psaní do vyhledávacího řetězce další znaky. **Výsledky** pole zpětné vazby sděluje, počet nalezených položek a vám pomůže rozhodnout, jestli se má omezte vaše hledání. **Typ/obor**, **umístění**, a **ve verzi Preview** pole zpětné vazby umožňují rozlišení položek, které mají podobné názvy. Kromě toho můžete rozšířit tuto funkci pro podporu jiných programovacích jazycích.

**Paralelní ladění a profilování.** Ladicí program sady Visual Studio si je vědoma souběžnosti modulu runtime a pomáhá odstraňovat potíže s aplikací pro paralelní zpracování. Nový nástroj profiler souběžnosti můžete vizualizovat celkové chování vaší aplikace. Navíc můžete použít nové nástroje windows vizualizovat stav úloh a jejich zásobníky volání.

**Návrhář pásu karet.** **Návrháře pásu karet** je grafický editor, který vám umožní vytvořit a upravit MFC pásu karet uživatelského rozhraní. Konečné uživatelské rozhraní pásu karet je reprezentován soubor prostředků založený na formátu XML (.mfcribbon-ms). Pro existující aplikace, můžete zaznamenat vaše aktuální uživatelské rozhraní pásu karet dočasně přidáním několika řádků kódu a pak volání **Návrháře pásu karet**. Po vytvoření souboru prostředků pásu karet můžete nahradit kód uživatelského rozhraní pro rukou psaný pásu s několika příkazy, které načtení prostředku pásu karet.

**Hierarchie volání.** **Hierarchie volání** okno vám umožní přejít ke všem funkcím, které jsou volány konkrétní funkce nebo všem funkcím, které volají určité funkce.

### <a name="tools"></a>Nástroje

**Průvodce třídou MFC.** Visual C++ 2010 vrací oceňovanému nástroj Průvodce třídami MFC. Průvodce třídou MFC je pohodlný způsob, jak přidat třídy, zprávy a proměnné do projektu bez nutnosti ručně upravit sady zdrojových souborů.

**Průvodce ovládacími prvky ATL.** Průvodce ovládacími prvky ATL už nebude automaticky naplní `ProgID` pole. Pokud nemá žádné ovládacího prvku ATL `ProgID`, dalších nástrojů, nemusí fungovat s ním. Příkladem nástroj, který vyžaduje ovládacích prvků `ProgID` je **vložit aktivní ovládací prvek** dialogové okno. Další informace o dialogovém okně najdete v tématu **Insert Dialog Box ovládacího prvku ActiveX**.

### <a name="microsoft-macro-assembler-reference"></a>Microsoft Macro Assembler – referenční dokumentace

Přidání datového typu YMMWORD podporuje oborového 256bitového multimediální operandy, které jsou zahrnuty v pokynech pro Intel Advanced Vector Extensions (AVX).

## <a name="whats-new-for-c-in-visual-studio-2008"></a>Co je nového v C++ v sadě Visual Studio 2008

### <a name="visual-c-integrated-development-environment-ide"></a>Visual C++ integrované vývojové prostředí (IDE)

- Dialogová okna vytvořené v ATL, MFC a Win32 aplikace nyní nutné dodržovat pravidla stylu Windows Vista. Když vytvoříte nový projekt pomocí sady Visual Studio 2008, všechna dialogová okna, které vkládají do své aplikace dodržovat prokázat stylu Windows Vista. Pokud je provedena rekompilace projekt, který jste vytvořili pomocí starší verze sady Visual Studio, zachová všechna existující dialogová okna, které dříve měly stejnou vzhledu. Další informace o tom, jak do aplikace vložit dialogových oknech, naleznete v tématu **editoru dialogového okna**.

- **Projekt knihovny ATL** Průvodce má teď možnost k registraci komponenty pro všechny uživatele. Od verze Visual Studio 2008, komponenty modelu COM a knihovny typů, které jsou vytvořené **projekt knihovny ATL** průvodce jsou registrovány v uzlu registru HKEY_CURRENT_USER nevyberte **zaregistrovat součásti pro všechny uživatele**.
- **Projekt knihovny ATL** průvodce již poskytuje možnost vytvořit projekty knihovny ATL s přidělenými atributy. Od verze Visual Studio 2008, **projekt knihovny ATL** Průvodce nemá možnost změnit stav nového projektu s atributy. Všechny nové projekty knihovny ATL, které průvodce vytvoří jsou nyní zjednodušeně.
- Zápis do registru je možné přesměrovat. Zavedení projektového systému Windows Vista zápis na určité oblasti registru vyžaduje program ke spuštění v režimu se zvýšenými oprávněními. Není žádoucí, aby vždy spustit sadu Visual Studio v režimu se zvýšenými oprávněními. Přesměrování dle uživatele automaticky přesměruje zápisy v registru z HKEY_CLASSES_ROOT na HKEY_CURRENT_USER bez nutnosti jakkoli měnit programování.
- **Návrhář tříd** teď má omezenou podporu pro nativní kód C++. V dřívějších verzích sady Visual Studio **návrhář tříd** pouze s Visual C# a Visual Basic. C++ uživatelé teď můžou používat **návrhář tříd**, ale pouze v režimu jen pro čtení. Další informace o tom, jak používat **návrhář tříd** v jazyce C++ naleznete v tématu **práce s kódem jazyka Visual C++ v Návrháři tříd**.
- Průvodce projektu není k dispozici možnost pro vytvoření projektu C++ SQL Server. Od verze Visual Studio 2008, Průvodce vytvořením projektu nemá možnost pro vytvoření projektu C++ SQL Server. Projekty systému SQL Server vytvořili pomocí starší verze sady Visual Studio bude stále zkompilujte a správně fungovat.

### <a name="visual-c-libraries"></a>Knihovny jazyka Visual C++

#### <a name="general"></a>Obecné

- Aplikace mohou být vázány na konkrétní verze knihoven Visual C++. Někdy aplikace závisí na aktualizace, které byly provedeny s knihovnami Visual C++ po vydání verze. Spuštění aplikace na počítači, který má starší verze knihoven v takovém případě může způsobit neočekávané chování. Nyní lze svázat aplikaci ke konkrétní verzi knihoven tak, aby se nespustí na počítači, který používá starší verzi knihoven.

#### <a name="stlclr-library"></a>STL/CLR – knihovna

- Visual C++ teď obsahuje knihovnu STL/CLR. Knihovny STL/CLR je obal z do knihovny STL (Standard Template), podmnožina standardní knihovny C++ pro použití s C++ a .NET Framework common language runtime (CLR). STL/CLR můžete nyní pomocí kontejnerů, iterátorů a algoritmů STL ve spravovaném prostředí.

#### <a name="mfc-library"></a>Knihovna MFC

- Windows Vista podporuje běžné ovládací prvky. Víc než 150 metody v 18 nové nebo existující třídy byly přidány pro podporu funkcí ve Windows Vista nebo ke zlepšení funkce v aktuální třídy knihovny MFC.
- Nové `CNetAddressCtrl` třída umožňuje zadání a ověření IPv4 a IPv6 adresy nebo názvy DNS.
- Nové `CPagerCtrl` třída zjednodušuje použití ovládacího prvku stránkování Windows.
- Nové `CSplitButton` třída zjednodušuje použití ovládacího prvku splitbutton Windows a vyberte výchozí a volitelné akce.

#### <a name="c-support-library"></a>Knihovna podpory C++

- C++ zavádí zařazovací knihovna. Zařazovací knihovna poskytuje snadný a optimalizované způsob zařazování dat mezi nativními a spravovanými prostředími. Knihovna je alternativou k složitější a míň efektivní přístupy, například pomocí služby PInvoke. Zobrazit **Overview of Marshaling in C++** Další informace.

#### <a name="atl-server"></a>ATL Server

- Jako sdílený zdrojový projekt se uvolní ATL Server.
- Většina základu kódu serveru ATL byla uvedena jako sdílený zdrojový projekt na webu CodePlex a není nainstalován jako součást sady Visual Studio 2008. Několik souborů, které jsou přidružené k serveru knihovny ATL už nejsou součástí sady Visual Studio. Seznam odebraných souborech najdete v tématu **odebrat soubory serveru ATL**.
- Kódování a dekódování z funkce atlenc.h a nástroje a třídy z atlutil.h a atlpath.h dat jsou teď součástí knihovny ATL.
- Microsoft bude nadále podporovat verze serveru ATL, které jsou zahrnuty v dřívějších verzích sady Visual Studio, tak dlouho, dokud se podporují tyto verze sady Visual Studio. CodePlex bude pokračovat ve vývoji kódu ATL Server jako to komunitní projekt. Microsoft nepodporuje CodePlex verze serveru ATL Server.

### <a name="visual-c-compiler-and-linker"></a>Kompilátor Visual C++ a propojovací program

#### <a name="compiler-changes"></a>Změny kompilátoru

- Kompilátor podporuje spravované přírůstkové sestavení. Když nastavíte tuto možnost, kompilátor nebude znovu zkompilovat kód, když se změní odkazované sestavení. Místo toho bude provedeno přírůstkové sestavení. Soubory jsou překompilovány pouze v případě, že změny ovlivní závislé kódu.
- Atributy související s ATL Server již nejsou podporovány. Kompilátor už podporuje několik atributů, které byly přímo souvisí s ATL Server. Úplný seznam odebrané atributy naleznete v tématu Rozbíjející změny.
- Kompilátor podporuje mikroarchitekturu Intel Core. Kompilátor obsahuje ladění pro mikroarchitekturu Intel Core při generování kódu. Ve výchozím nastavení tato optimalizace je zapnuté a nejde zakázat, protože pomáhá také procesor Pentium 4 a dalších procesorů.
- Vnitřní funkce podporují novější procesorů AMD a Intel. Několik nových vnitřní pokynů podporovat více funkcí v novější procesorů AMD a Intel. Další informace o nové vnitřních objektů najdete v tématu **doplňkové Streaming SIMD Extensions 3 pokyny**, **Streaming SIMD Extensions 4 pokyny**, **SSE4A a rozšířená verze Manipulace s vnitřní objekty**, **vnitřní objekty AES**, **_mm_clmulepi64_si128**, a **__rdtscp**.
- `__cpuid` Funkce se aktualizuje. `__cpuid`, `__cpuidex` Funkce teď podporují několik nových funkcí z nejnovější revize procesory AMD a Intel. `__cpuidex` Vnitřní novinky a shromažďuje informace z poslední procesory.
- `/MP` – Možnost kompilátoru snižuje čas celkové sestavení. `/MP` Možnost může výrazně snížit celkový čas kompilace několik zdrojových souborů tak, že vytvoříte několik procesů, které se kompilují soubory současně. Tato možnost je užitečná v počítačích, které podporují hyperthreadingem, více procesorů nebo více jader.
- `/Wp64` – Možnost kompilátoru a **__w64** – klíčové slovo se považují za zastaralé. `/Wp64` – Možnost kompilátoru a **__w64** – klíčové slovo, které zjišťovat problémy přenositelnosti na 64-bit, se považují za zastaralé a bude v budoucí verzi kompilátoru odebrána. Namísto tohoto – možnost kompilátoru a – klíčové slovo využijte kompilátor Visual C++ této platformy cíle 64-bit.
- `/Qfast_transcendentals` generuje kód vloženého Transcendentní funkce.
- `/Qimprecise_fwaits` Odstraní příkazy fwait interní na bloky try při použití `/fp:except` – možnost kompilátoru.

### <a name="linker-changes"></a>Změny linkeru

- Informace o řízení účet uživatele je teď vložená do manifestu souborů pro spustitelné soubory Visual C++ Linker (link.exe). Tato funkce je ve výchozím nastavení povolena. Další informace o tom, jak tuto funkci zakázat a jak změnit výchozí chování najdete v tématu `/MANIFESTUAC` (vložené informace UAC v manifestu).
- Propojovací program má teď `/DYNAMICBASE` možnost povolit funkci náhodného generování rozložení prostoru adres systému Windows Vista. Tato možnost změní záhlaví spustitelného souboru k označení, zda aplikace by měla být náhodně změnit základ v okamžiku načtení.

## <a name="whats-new-for-c-in-visual-studio-2005"></a>Co je nového v jazyce C++ v sadě Visual Studio 2005

Visual C++ 2005 Service Pack 1 přibyly následující funkce:

### <a name="intrinsics-for-x86-and-x64"></a>Vnitřní funkce pro x86 a x64

- __halt
- __lidt
- __nop
- __readcr8
- __sidt
- __svm_clgi
- __svm_invlpga
- __svm_skinit
- __svm_stgi
- __svm_vmload
- __svm_vmrun
- __svm_vmsave
- __ud2
- __vmx_off
- __vmx_vmptrst
- __writecr8

### <a name="intrinsics-for-x64-only"></a>Vnitřní funkce pro x64 pouze

- __vmx_on
- __vmx_vmclear
- __vmx_vmlaunch
- __vmx_vmptrld
- __vmx_vmread
- __vmx_vmresume
- __vmx_vmwrite

### <a name="new-language-keywords"></a>Nová klíčová slova jazyka

__sptr, __uptr

### <a name="new-compiler-features"></a>Nové funkce kompilátoru

Rozbíjející změny v této verzi má kompilátor.

- "64-bitové nativní a křížové kompilátory.
- `/analyze` Byla přidána možnost kompilátoru (Analýza kódu Enterprise).
- `/bigobj` byla přidána možnost kompilátoru.
- `/clr:pure`, `/clr:safe`, a `/clr:oldSyntax` byly přidány. (Později zastaralé v sadě Visual Studio 2015 a odebrané v sadě Visual Studio 2017.)
- Zastaralé parametry kompilátoru: v této verzi; se již nepoužívají mnoho možností kompilátoru Zobrazit **zastaralé parametry kompilátoru** Další informace.
- Dvojitému v `/clr` kódu je omezeno na něm zobrazí **dvojitý převod adres (C++)** Další informace.
- `/EH` (Model zpracování výjimek) nebo `/EHs` je už nebude možné zachytit výjimku, která je vyvolána něčím jiným než vyvolání; použijte `/EHa`.
- `/errorReport` Byla přidána možnost kompilátoru (sestava interními chybami kompilátoru).
- `/favor` (Optimalizace pro 64) – možnost kompilátoru se přidala.
- `/FA`, `/Fa` – Možnost kompilátoru (soubor výpisu) se přidal.
- `/FC` Byla přidána možnost kompilátoru (úplná cesta ze souboru zdrojového kódu v diagnostice).
- `/fp` (Zadání chování plovoucí desetinné čárky) – možnost kompilátoru se přidala.
- `/G` (Optimalizace pro procesor) Byla přidána možnost možnosti kompilátoru.
- `/G` (Optimalizace pro procesor) Byla přidána možnost možnosti kompilátoru.
- `/G3`, `/G4`, `/G5`, `/G6`, `/G7`, a `/GB` – možnosti kompilátoru se odebraly. Kompilátor nyní používá "kombinaci model", která se pokusí vytvořit nejlepší výstupní soubor pro všechny architektury.
- `/Gf` byl odebrán. Použití `/GF` (odstranit duplicitní řetězce) místo toho.
- `/GL` (Optimalizace celého programu) je teď kompatibilní se `/CLRHEADER`.
- `/GR` Teď je ve výchozím.
- `/GS` (Vyrovnávací paměti, kontrola zabezpečení) nyní poskytuje ochranu zabezpečení pro ukazatel ohrožené parametry. `/GS` Teď je ve výchozím. `/GS` Teď také funguje pro funkce zkompilované do jazyka MSIL s `/clr` (kompilace Common Language Runtime).
- `/homeparams` Byla přidána možnost kompilátoru (Kopírovat parametry registru do zásobníku).
- `/hotpatch` (Vytvoření Image vyměnitelné za provozu) se přidal – možnost kompilátoru.
- Vložené funkce heuristiky se aktualizovaly; Zobrazit **vložené**, **__inline**, **__forceinline** a **inline_depth** Další informace
- Mnoho nových vnitřní funkce byly přidány, a mnoho dříve nedokumentované vnitřní objekty jsou nyní zdokumentované.
- Ve výchozím nastavení volání na nový, kterému se nedaří vyvolá výjimku.
- `/ML` a `/MLd` – možnosti kompilátoru se odebraly. Jazyk Visual C++ podporuje už s jedním vláknem, staticky propojených podpora knihovny CRT.
- Kompilátor implementovat vrácení pojmenované optimalizace hodnot, které je povolená, když kompilujete s `/O1`, `/O2` (minimalizovat velikost, maximální rychlost), `/Og` (globální optimalizace), a `/Ox` (úplná optimalizace).
- `/Oa` – možnost kompilátoru, byla odebrána, ale bude tiše ignorovat; použít `noalias` nebo `restrict__declspec` modifikátory k určení, jak kompilátor provádí aliasing.
- `/Op` – možnost kompilátoru byl odstraněn. Použití `/fp` (zadání chování plovoucí desetinné čárky) místo toho.
- Visual C++ teď podporuje OpenMP.
- `/openmp` Byla přidána možnost kompilátoru (povolení podpory OpenMP 2.0).
- `/Ow` – možnost kompilátoru, byla odebrána, ale bude tiše ignorovat. Použití `noalias` nebo `restrict__declspec` modifikátory k určení, jak kompilátor provádí aliasing.

### <a name="profile-guided-optimizations"></a>Optimalizace na základě profilu

- `/QI0f` byl odebrán.
- `/QIfdiv` byl odebrán.
- `/QIPF_B` Byla přidána možnost kompilátoru (seznam chyb pro revizi krokování procesoru B).
- `/QIPF_C` Byla přidána možnost kompilátoru (seznam chyb pro revizi krokování procesoru C).
- `/QIPF_fr32` (Provádět, není použití horní 96 s plovoucí desetinnou čárkou bodu zaregistruje) byla přidána možnost kompilátoru.
- `/QIPF_noPIC` (Generovat kód umístění) se přidal – možnost kompilátoru.
- `/QIPF_restrict_plabels` (Předpokládejme žádné funkce vytvořené za běhu) byla přidána možnost kompilátoru.

### <a name="unicode-support-in-the-compiler-and-linker"></a>Podpora kódování Unicode v kompilátoru a linkeru

- `/vd` (Zakázat posunutí konstrukcí) teď umožňuje použít na objekt při konstrukci dynamic_cast – operátor (/ vd2)
- `/YX` Odebrali jsme – možnost kompilátoru. Použití `/Yc` (Vytvořit předkompilovaný hlavičkový soubor) nebo `/Yu` (Použít předkompilovaný soubor hlaviček) místo toho. Pokud odeberete `/YX` z konfigurace sestavení a nahraďte ji není nic, může vést rychlejšími sestaveními.
- `/Zc:forScope` Teď je ve výchozím.
- `/Zc:wchar_t` Teď je ve výchozím.
- `/Zd` Odebrali jsme – možnost kompilátoru. Číslo řádku pouze informace o ladění se už nepodporuje. Použití `/Zi` místo toho (viz **/Z7, / zi, /ZI (formát informací o ladění)** Další informace).
- `/Zg` je nyní platná pouze na soubory zdrojového kódu jazyka C a ne na soubory zdrojového kódu C++.
- `/Zx` Byla přidána možnost kompilátoru (ladění optimalizovaného kódu Itanium).

### <a name="new-language-features"></a>Nové funkce jazyků

- AtributAtribut je nyní zastaralá.
- `appdomain__declspec` Modifikátor se přidala.
- `__clrcall` konvence volání se přidala.
- Zastaralé (C++) **declspec** modifikátor můžete nyní zadat řetězec, který se zobrazí v době kompilace, když se uživatel pokusí o přístup k zastaralé třídy nebo funkce.
- **přetypování dynamic_cast** operátor má rozbíjející změny.
- Nativních výčtech nyní umožňují určit základní typ.
- `jitintrinsicdeclspec` Modifikátor se přidala.
- `noaliasdeclspec` Modifikátor se přidala.
- `process__declspec` Modifikátor se přidala.
- **abstraktní**, **přepsat**, a **zapečetěné** jsou platné pro nativní kompilace.
- **Kvalifikátor __restrict** – klíčové slovo se přidala.
- `restrictdeclspec` Modifikátor se přidala.
- **klíčové slovo __thiscall** je nyní klíčové slovo.
- **__unaligned** – klíčové slovo je nyní zdokumentované.
- **volatile** (C++) byl aktualizován chování s ohledem na optimalizaci.

### <a name="new-preprocessor-features"></a>Nové funkce preprocesoru

- __CLR_VER přidat předdefinované makro.
- Pragmatu komentáře (C/C++) nyní přijímá `/MANIFESTDEPENDENCY` jako komentář linkeru. Možnost exestr komentář je nyní zastaralá.
- `embedded_idl` atribut ( `#import` – direktiva) nyní přijímá volitelný parametr.
- `fenv_access` Direktiva pragma
- `float_control` Direktiva pragma
- `fp_contract` Direktiva pragma
- Globální proměnné nelze inicializovat v pořadí, ve kterém jsou deklarovány, pokud máte v direktivy pragma managed, spravované a nespravované části globální proměnné. To je potenciální rozbíjející změny, pokud například nespravované globální proměnná je inicializována s spravované globální proměnné a na úplně konstruovaný objekt spravovaný je povinný.
- Zadaný init_seg – oddíly jsou nyní jen pro čtení a není pro čtení a zápis stejně jako v předchozích verzích.
- inline_depth výchozí hodnota je nyní 16. Výchozí hodnota je 16 byl také v platnosti v jazyce Visual C++ .NET 2003.
- _INTEGRAL_MAX_BITS předdefinované makro přidali, najdete v článku předdefinovaná makra.
- _M_CEE _M_CEE_PURE a _M_CEE_SAFE předdefinovaná makra přidali, najdete v článku předdefinovaná makra.
- _M_IX86_FP přidat předdefinované makro.
- _M_X64 přidat předdefinované makro.
- `make_public` Direktiva pragma
- `managed`, `unmanaged` aktualizovat syntaxe direktivy pragma (má teď `push` a `pop`)
- soubor mscorlib.dll je nyní implicitně odkazováno `#using` direktiv ve všech `/clr` kompilace.
- _OPENMP přidat předdefinované makro.
- optimize – Direktiva pragma se aktualizovala, a w už nejsou platné parametry.
- byla přidána #import no_registry – atribut.
- `region`, `endregion` Přidání direktivy pragma
- _VC_NODEFAULTLIB přidat předdefinované makro.
- Variadická makra je nyní implementována.
- `vtordisp` je zastaralá a v příští verzi Visual C++ se odebere.
- `warning` – Direktiva pragma má teď specifikátor potlačit.

### <a name="new-linker-features"></a>Nové funkce Linkeru

- Moduly (bez sestavení jazyka MSIL výstupní soubory) jsou teď povolené jako vstup do linkeru.
- `/ALLOWISOLATION` Byla přidána možnost linkeru (vyhledání manifestu).
- `/ASSEMBLYRESOURCE` (Vložení spravovaného prostředku) byla aktualizována na teď můžete zadat název prostředku v sestavení nebo k určení, že prostředek je privátní v sestavení.
- `/CLRIMAGETYPE` (Zadání typu Image modulu CLR) – možnost linkeru se přidala.
- `/CLRSUPPORTLASTERROR` Byla přidána možnost linkeru (zachování kódu poslední chyby pro volání PInvoke).
- `/CLRTHREADATTRIBUTE` Byla přidána možnost linkeru (nastavení atributu modulu CLR vlákno).
- `/CLRUNMANAGEDCODECHECK` (Přidat atribut SuppressUnmanagedCodeSecurityAttribute) – možnost linkeru se přidala.
- `/ERRORREPORT` Byla přidána možnost linkeru (sestava interními chybami Linkeru).
- `/EXETYPE` Odebrali jsme – možnost linkeru. Propojovací program již podporuje vytváření Windows 95 a Windows 98 ovladače zařízení. Pomocí příslušné DDK můžete vytvořit tyto ovladače zařízení. Klíčové slovo EXETYPE už není platný pro soubory definice modulu.
- `/FUNCTIONPADMIN` (Vytvoření Image vyměnitelné za provozu) se přidal – možnost linkeru.
- `/LTCG` – možnost linkeru je nyní podporována v modulech zkompilovaných pomocí `/clr`. `/LTCG` aktualizovali jsme také pro podporu optimalizace na základě profilu.
- `/MANIFEST` (Vytvoření manifestu sestavení vedle sebe) se přidal – možnost linkeru.
- `/MANIFESTDEPENDENCY` (Určení závislostí manifestu) – možnost linkeru se přidala.
- `/MANIFESTFILE` Byla přidána možnost linkeru (pojmenování souboru manifestu).
- `/MAPINFO:LINES` Odebrali jsme – možnost linkeru.
- `/NXCOMPAT` (Kompatibilní s předcházením spuštění dat) se přidal – možnost linkeru.
- `/PGD` (Určení databáze pro optimalizace Profile-Guided) – možnost linkeru se přidala.
- `/PROFILE` Byla přidána možnost linkeru (Profiler nástrojů výkonu).
- `/SECTION` – Možnost linkeru (určení atributů oddílu) teď podporuje atribut negace a už nepodporuje L nebo D (VxD související s) atributy.
- Podpora kódování Unicode v kompilátoru a linkeru
- `/VERBOSE` (Zprávy o průběhu tisknout) – možnost linkeru nyní přijímá také ICF a REF.
- `/VXD` Odebrali jsme – možnost linkeru. Propojovací program již podporuje vytváření Windows 95 a Windows 98 ovladače zařízení. Pomocí příslušné DDK můžete vytvořit tyto ovladače zařízení. VXD – klíčové slovo už není platný pro soubory definice modulu.
- `/WS` Odebrali jsme – možnost linkeru. `/WS` byl použit vám umožní upravit obrázky určené pro Windows NT 4.0. Název souboru IMAGECFG.exe -R je možné místo `/WS`. IMAGECFG.exe můžete najít na disku CD-ROM systému Windows NT 4.0 SUPPORT\DEBUG\I386\IMAGECFG. SOUBOR EXE.
- `/WX` Nyní je popsána – možnost linkeru (zpracovávat upozornění Linkeru jako chyb).

### <a name="new-linker-utility-features"></a>Nové funkce nástrojů Linkeru

- `/ALLOWISOLATION` byla přidána – možnost nástroje Editbin
- Popis – příkaz souboru definice modulu se odebere. Propojovací program již podporuje vytváření virtuální ovladače zařízení.
- `/ERRORREPORT` byla přidána možnost bscmake.exe, dumpbin.exe, editbin.exe a lib.exe.
- `/LTCG` byla přidána možnost lib.
- `/NXCOMPAT` – možnost nástroje Editbin se přidala.
- `/RANGE` byla přidána možnost nástroje DUMPBIN.
- `/TLS` byla přidána možnost nástroje DUMPBIN.
- `/WS` – možnost nástroje Editbin se odebrala. `/WS` byl použit vám umožní upravit obrázky určené pro Windows NT 4.0. Název souboru IMAGECFG.exe -R je možné místo `/WS`. IMAGECFG.exe můžete najít na disku CD-ROM systému Windows NT 4.0 SUPPORT\DEBUG\I386\IMAGECFG. SOUBOR EXE.
- /WX [: NO] byla přidána možnost lib.

### <a name="new-nmake-features"></a>Nové funkce NMAKE

- `/ERRORREPORT` byla přidána.
- `/G` byla přidána.
- Předdefinovaná pravidla se aktualizovaly.
- $(MAKE) makro, které jsou uvedené v rekurzivní makra, nyní poskytuje úplnou cestu k nmake.exe.

### <a name="new-masm-features"></a>Nové funkce MASM

- Výrazy MASM jsou teď hodnoty 64-bit. V předchozích verzích MASM výrazy byly 32bitové hodnoty.
- __Asm int instrukce 3 nyní způsobí, že funkce se zkompiluje do native.
- Nyní je popsána ALIAS (MASM).
- `/ERRORREPORT` je přidána možnost ml.exe a ml64.exe.
- . FPO je nyní zdokumentované.
- H2INC.exe nebude součástí Visual C++ 2005. Pokud je potřeba pokračovat v používání H2INC, použijte H2INC.exe z předchozí verze aplikace Visual C++.
- operátor IMAGEREL se přidala.
- high32 – operátor se přidala.
- low32 – operátor se přidala.
- ml64.exe je verze MASM pro x64 architektury. Sestaví x64 .asm soubory do x64 objektu soubory. Vložené sestavení jazyk není podporován v x64 kompilátoru. Byly přidány následující direktivy MASM pro ml64.exe (x64):
- .ALLOCSTACK
- .ENDPROLOG
- .PUSHFRAME
- .PUSHREG
- .SAVEREG
- .SAVEXMM128
- . SETFRAME. kromě, PROC – direktiva byla aktualizována jen x64 syntaxe.
- Byla přidána MMWORD – direktiva
- `/omf` (Možnost příkazového řádku ML.exe) nyní zahrnuje `/c`. ML.exe nepodporuje propojení omf – formát objektů.
- SEGMENT – direktiva teď podporuje další atributy.
- sectionrel – operátor se přidala.
- Byla přidána XMMWORD – direktiva

### <a name="new-crt-features"></a>Nové funkce CRT

- Přidali jsme bezpečné verze několik funkcí. Tyto funkce v ještě lepší způsob zpracování chyb a vynucovat přísnější ovládacích prvků u vyrovnávacích pamětí, která pomáhá zabránit běžné nedostatky v zabezpečení. Nové bezpečné verze jsou určeny **_Malá** příponu.
- Méně bezpečné verze mnoha existující funkce se již nepoužívají. Chcete-li zakázat upozornění na zastaralost, definujte _CRT_SECURE_NO_WARNINGS.
- Mnoho existujících funkcí se teď ověřují své parametry a vyvolat obslužnou rutinu neplatného parametru, pokud je předán neplatný parametr.
- Nyní nastavte mnoho existujících funkcí `errno` kde udělal ne dřív.
- Typedef `errno_t` s typem byl přidán celé číslo. `errno_t` se používá pokaždé, když se funkce, návratový typ nebo parametr se zabývá kódy chyb z `errno`. `errno_t` nahradí `errcode`.
- Funkce závislé na národním prostředí teď mají verze, které berou národní prostředí jako parametr namísto použití aktuálního národního prostředí. Tyto nové funkce mají **_l** příponu. Několik nových funkcí byly přidány pro práci s objekty národní prostředí. Nové funkce patří `_get_current_locale`, `_create_locale` a `_free_locale`.
- Nové funkce byly přidány pro podporu zamykání a odemykání popisovače souborů.
- `_spawn` Rodinu funkcí neprovádí vynulování errno na hodnotu nula v případě úspěchu, stejně jako v předchozích verzích.
- Verze `printf` řady funkcí, které vám umožňují určit pořadí, ve kterém jsou argumenty použity jsou k dispozici.
- Kódování Unicode je nyní podporovaný textovém formátu. Funkce `_open` podporuje _O_TEXTW, _O_UTF8 a _O_UTF16 atributy. `fopen` Funkce podporuje "ccs = ENCODING" metodu pro určení formátu kódování Unicode.
- Novou verzi knihovny CRT vytvořené ve spravovaném kódu (MSIL) je teď k dispozici a používá se při kompilaci s `/clr` možnost (kompilace Common Language Runtime).
- _fileinfo – byla odebrána.
- Výchozí velikost pro `time_t` je nyní 64 bitů, které rozšíří rozsah `time_t` a některé časové funkce navýšení kapacity na rok 3000.
- CRT nyní podporuje nastavení národního prostředí na základě na vlákno. Funkce `_configthreadlocale` byla přidaná kvůli podpoře tuto funkci.
- `_statusfp2` a `__control87_2` funkce byly přidány do povolit přístup k a ovládacího prvku s plovoucí desetinnou čárkou bod řídicího slova na obou x87 a s plovoucí desetinnou čárkou SSE2 bod procesoru.
- `_mkgmtime` a `_mkgmtime64` funkce byly přidány k poskytování podpory pro převod časy (struktura tm) greenwichský střední čas (GMT).
- Provedly se změny `swprintf` a `vswprintf` tak, aby lépe vyhovovala standard.
- Nový soubor hlaviček, INTRIN. H, poskytuje prototypy pro některé vnitřní funkce.
- `fopen` Funkce má nyní atribut N.
- `_open` Funkce má nyní atribut _O_NOINHERIT.
- `atoi` Nyní vrací INT_MAX a nastaví funkce `errno` k ERANGE při přetečení. V předchozích verzích nedefinované chování přetečení.
- `printf` Řadu funkcí podporuje šestnáctkové číslo s plovoucí desetinnou čárkou výstup implementovány podle standardu ANSI C99 pomocí specifikátorů formátu typ %a a %A.
- `printf` Řady teď podporuje Předpona velikosti "l" (long long).
- `_controlfp` Funkce optimalizovaná pro zajištění lepšího výkonu.
- Ladicí verze některé funkce byly přidány.
- Přidání `_chgsignl` a `_cpysignl` (long dvakrát verze).
- Přidání `_locale_t` typ na typ tabulka.
- Nové – makro `_countof` – makro přidány pro výpočty počet prvků v poli.
- V každé téma funkce byla přidána část věnovanou ekvivalentech rozhraní .NET Framework.
- Několik funkcí řetězce mají nyní možnost zkracování řetězců a ne selhání při výstupní vyrovnávací paměti je příliš malý. Zobrazit **_TRUNCATE**.
- `_set_se_translator` nyní vyžaduje použití `/EHa` – možnost kompilátoru.
- `fpos_t` Nyní je **__int64** pod `/Za` (pro kód jazyka C) a kdy __STDC__ je nastavit ručně (pro C++ kód). Používá se **struktura**.
- _CRT_DISABLE_PERFCRIT_LOCKS může zlepšit výkon vstupně-výstupních operací s jedním vláknem programů.
- POSIX – názvy jsou zastaralé a místo toho použití názvů splňující podmínky ISO C++ (například použít `_getch` spíše než `getch`).
- Nové soubory .obj odkaz Možnosti jsou k dispozici pro režim čisté
- `_recalloc` kombinuje funkce `realloc` a `calloc`.

## <a name="whats-new-for-c-in-visual-studio-2003"></a>Co je nového v C++ v aplikaci Visual Studio 2003

### <a name="compiler"></a>Kompilátor

- Informace o tom, jak spustit spravovaného rozšíření jazyka C++ aplikaci vytvořenou v aktuální verzi kompilátoru v předchozí verzi modulu runtime.
- Spravovaná rozšíření pro C++ – nejčastější dotazy.
- Byla přidána názorný postup ukazuje, jak přenést existující, nativní aplikace pro použití spravovaného rozšíření jazyka C++: Návod: Portování stávající nativní kód C++ aplikace pro spolupráci s součásti rozhraní .NET Framework.
- Nyní můžete vytvořit delegáta pro metodu hodnotového typu.
- Kompilátoru soulad se standardem jazyka C++ je výrazně Vylepšená Visual C++ .NET 2003.
- `/arch` – možnost kompilátoru je přidána.
- `/Gf` je zastaralá a v příští verzi Visual C++ se odebere.
- `/G7` – možnost kompilátoru je přidána.
- `/GS` Bylo vylepšeno – možnost kompilátoru pomoc při ochraně místních proměnných z přetečení vyrovnávací paměti s přímým přístupem.
- `/noBool` – Možnost kompilátoru se odebrala. Kompilátor nyní umožňuje **bool** se zobrazí pouze v případě, že klíčové slovo (a nikoli identifikátor) C++ zdrojového souboru kódu.
- **Long long** je teď dostupná jako typ **– typedef** z **__int64** Všimněte si, že je ještě není podpora **long long** v CRT.
- `/Zm` Nyní – možnost kompilátoru určuje omezení přidělení paměti pro předkompilované hlavičky.
- _InterlockedCompareExchange vnitřní nyní zdokumentované.
- _InterlockedDecrement vnitřní nyní zdokumentované.
- _InterlockedExchange vnitřní nyní zdokumentované.
- Vnitřní _InterlockedExchangeAdd nyní zdokumentované.
- _InterlockedIncrement vnitřní nyní zdokumentované.
- _Readwritebarrier – vnitřní funkce přidána.

### <a name="attributes"></a>Atributy

- `implements` atribut je nyní zdokumentované.

### <a name="linker-features"></a>Funkce linkeru

Byly přidány následující přepínače linkeru:

- / ASSEMBLYDEBUG
- / ASSEMBLYLINKRESOURCE
- DELAYSIGN
- / KEYFILE
- / KEYCONTAINER
- / SAFESEH

### <a name="masm"></a>MASM

Na. SAFESEH – direktiva a `/safeseh` ml.exe možnost byly přidány.

## <a name="see-also"></a>Viz také:

[Průvodce přenosem a upgradem Visual C++](visual-cpp-porting-and-upgrading-guide.md)
