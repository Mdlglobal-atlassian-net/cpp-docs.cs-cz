---
title: Visual C++ Co&#39;s Novinka 2003 až 2015
ms.date: 07/02/2019
ms.assetid: c4afde6f-3d75-40bf-986f-be57e3818e26
ms.openlocfilehash: 48b812bf43918d7fbc37d20d0ef1b02348759544
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332088"
---
# <a name="visual-c-what39s-new-2003-through-2015"></a>Visual C++ Co&#39;s Novinka 2003 až 2015

Tato stránka shromažďuje všechny stránky "Co je nového" pro všechny verze visual c++ z Visual Studia 2015 zpět do roku 2003. Tyto informace jsou k dispozici pro případ, že by mohly být užitečné při upgradu z dřívějších verzí sady Visual Studio.

> [!NOTE]
> Informace o aktuální verzi sady Visual Studio najdete v tématu [Co je nového pro Visual C++ v sadě Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md) a vylepšení [shody v jazyce Visual C++ v sadě Visual Studio](../overview/cpp-conformance-improvements.md).

## <a name="whats-new-for-c-in-visual-studio-2015"></a>Co je nového pro C++ ve Visual Studiu 2015

V sadě Visual Studio 2015 a novější, probíhající vylepšení shody kompilátoru může někdy změnit způsob, jakým kompilátor chápe váš existující zdrojový kód. V takovém případě může dojít k nové nebo různé chyby během sestavení nebo dokonce behaviorální rozdíly v kódu, který dříve sestavené a zdálo se, že správně spustit.

Naštěstí tyto rozdíly mají malý nebo žádný vliv na většinu zdrojového kódu a když zdrojový kód nebo jiné změny jsou potřebné k řešení těchto rozdílů, opravy jsou obvykle malé a přímočaré. Zahrnuli jsme mnoho příkladů dříve přijatelného zdrojového kódu, který může být nutné změnit *(před)* a opravy, které je opravují *(po)*.

Přestože tyto rozdíly mohou ovlivnit zdrojový kód nebo jiné artefakty sestavení, nemají vliv na binární kompatibilitu mezi aktualizacemi verzí visual c++. Závažnější druh změny, *narušující změna* může ovlivnit binární kompatibilitu, ale tyto druhy binární kompatibility přestávky dojít pouze mezi hlavní verze Visual C ++. Například mezi Visual C++ 2013 a Visual C++ 2015. Informace o narušujících změnách, ke kterým došlo mezi Visual C++ 2013 a Visual C++ 2015, naleznete [v tématu Visual C++ change history 2003 - 2015](../porting/visual-cpp-change-history-2003-2015.md).

- [Vylepšení shody v sadě Visual Studio 2015](#VS_RTM)

- [Vylepšení shody v aktualizaci Visual Studio 2015 Update 1](#VS_Update1)

- [Vylepšení shody v aktualizaci Visual Studio 2015 Update 2](#VS_Update2)

- [Vylepšení shody v aktualizaci Visual Studio 2015 Update 3](#VS_Update3)

### <a name="conformance-improvements-in-visual-studio-2015"></a><a name="VS_RTM"></a>Vylepšení shody v sadě Visual Studio 2015

- **/Zc:forScope- volba**

   Možnost `/Zc:forScope-` kompilátoru je zastaralé a budou odebrány v budoucí verzi.

   ```output
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release
   ```

   Tato možnost byla obvykle použita, aby bylo možné nestandardní kód, který používá proměnné smyčky po bodu, kde podle standardu měly být mimo rozsah. Bylo to nutné pouze při kompilaci `/Za` s možností, protože bez `/Za`, použití proměnné smyčky for po skončení smyčky je vždy povoleno. Pokud se nestaráte o shodu standardů (například pokud váš kód není určen k `/Za` přenositelnosti na jiné kompilátory), můžete tuto možnost vypnout (nebo nastavit vlastnost **Zakázat rozšíření jazyka** na **ne).** Pokud vám záleží na psaní přenosný, standardy kompatibilní kód, měli byste přepsat kód tak, aby odpovídalstandard přesunutím deklarace těchto proměnných do bodu mimo smyčky.

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

- **Možnost kompilátoru Zg.**

   Možnost `/Zg` kompilátoru (Generovat prototypy funkcí) již není k dispozici. Tato možnost kompilátoru byla dříve zastaralá.

- Již nelze spustit testy částí s C++/CLI z příkazového řádku s mstest.exe. Místo toho použijte vstest.console.exe

- **proměnlivé klíčové slovo.**

   Specifikátor třídy **proměnlivé** úložiště již není povolen v místech, kde dříve zkompiloval bez chyby. Nyní kompilátor poskytuje chybu C2071 (třída neplatné úložiště). Podle standardu lze proměnlivý specifikátor použít pouze na názvy datových členů třídy a nelze jej použít na názvy deklarované jako const nebo statické a nelze jej použít na referenční členy.

   Zvažte například následující kód:

   ```cpp
    struct S {
        mutable int &r;
    };
   ```

   Předchozí verze kompilátoru Microsoft C++ to přijaly, ale nyní kompilátor udává následující chybu:

   ```Output
    error C2071: 'S::r': illegal storage class
   ```

   Chcete-li chybu opravit, jednoduše odeberte redundantní **proměnlivé** klíčové slovo.

- **char_16_t a char32_t**

   Již nelze použít `char16_t` `char32_t` nebo jako aliasy v typedef, protože tyto typy jsou nyní považovány za předdefinované. Bylo běžné, že uživatelé `char16_t` a `char32_t` autoři knihovny definovali a jako aliasy `uint16_t` a `uint32_t`, resp.

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

   Chcete-li aktualizovat kód, odeberte deklarace **typedef** a přejmenujte všechny ostatní identifikátory, které se srazí s těmito názvy.

- **Parametry šablony bez typu**

   Určitý kód, který zahrnuje parametry šablony bez typu, je nyní správně zkontrolován na kompatibilitu typů, když zadáte explicitní argumenty šablony. Například následující kód zkompilován bez chyby v předchozích verzích visual c++.

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

   Aktuální kompilátor správně poskytuje chybu, protože typ parametru šablony neodpovídá argumentu šablony (parametr je ukazatel na člen const, ale funkce f není const):

   ```Output
    error C2893: Failed to specialize function template 'void S2::f(void)'note: With the following template arguments:note: 'C=S1'note: 'Function=S1::f'
   ```

   Chcete-li tuto chybu vyřešit v kódu, ujistěte se, že typ argumentu šablony, který používáte, odpovídá deklarovanému typu parametru šablony.

- **__declspec(zarovnat)**

   Kompilátor již přijímá `__declspec(align)` funkce. To bylo vždy ignorováno, ale nyní vytváří chybu kompilátoru.

   ```cpp
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations
   ```

   Chcete-li tento `__declspec(align)` problém vyřešit, odeberte z deklarace funkce. Vzhledem k tomu, že neměl žádný účinek, jeho odstranění nic nemění.

- **Zpracování výjimek**

   Existuje několik změn zpracování výjimek. Za prvé, objekty výjimky musí být kopírovatelné nebo pohyblivé. Následující kód zkompilován ve Visual Studiu 2013, ale nekompiluje v sadě Visual Studio 2015:

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

   Problém je, že konstruktor kopie je soukromý, takže objekt nelze zkopírovat, jak se děje v normálním průběhu zpracování výjimky. Totéž platí, když je konstruktor kopie **deklarován explicitní**.

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

   Chcete-li aktualizovat kód, ujistěte se, že konstruktor kopie pro objekt výjimky je veřejný a není označen **explicitní**.

   Zachycení výjimky podle hodnoty také vyžaduje, aby objekt výjimky byl kopírovatelný. Následující kód zkompilován ve Visual Studiu 2013, ale nekompiluje v sadě Visual Studio 2015:

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

   Tento problém můžete vyřešit změnou typu parametru pro **catch** na odkaz.

   ```cpp
    catch(D& d)
    {
    }
   ```

- **Řetězcové literály následované makry**

   Kompilátor nyní podporuje uživatelem definované literály. V důsledku toho řetězcové literály následované makry bez jakýchkoli zasahujících mezer jsou interpretovány jako literály definované uživatelem, které mohou způsobit chyby nebo neočekávané výsledky. Například v předchozích kompilátorech byl úspěšně zkompilován následující kód:

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

   Kompilátor interpretoval to jako literál řetězce "hello" následovaný makro, které je rozbaleno "tam", a pak dva řetězcové literály byly zřetězeny do jednoho. V sadě Visual Studio 2015 kompilátor interpretuje jako uživatelem definovaný literál, ale protože neexistuje žádný odpovídající uživatelem definovaný literál _x definován, poskytuje chybu.

   ```cpp
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found
    note: Did you forget a space between the string literal and the prefix of the following string literal?

   ```

   Chcete-li tento problém vyřešit, přidejte mezeru mezi literál řetězce a makro.

- **Sousední řetězcové literály**

   Podobně jako předchozí, z důvodu souvisejících změn v analýzě řetězců, sousední řetězcové literály (literály řetězce široký nebo úzký znak) bez jakýchkoli mezer byly interpretovány jako jeden zřetězený řetězec v předchozích verzích Visaul C++. V sadě Visual Studio 2015 je nyní nutné přidat mezery mezi dva řetězce. Například následující kód musí být změněn:

   ```cpp
    char * str = "abc""def";
   ```

   Jednoduše přidejte mezeru mezi dva řetězce.

   ```cpp
    char * str = "abc" "def";
   ```

- **Umístění nové a odstranit**

   Byla provedena změna operátoru **delete,** aby byl shodou se standardem C++ 14. Podrobnosti o změně standardů lze nalézt na [C ++ velikosti Deallocation](https://isocpp.org/files/papers/n3778.html). Změny přidat formu globální **delete** operátor, který má parametr velikosti. Narušující změna je, že pokud jste dříve používali operátor **odstranit** se stejným podpisem (aby **odpovídaly umístění nového** operátoru), obdržíte chybu kompilátoru (C2956, ke kterému dochází v místě, kde se používá **umístění nové,** protože to je pozice v kódu, kde kompilátor se pokusí identifikovat odpovídající **operátor delete).**

   Funkce `void operator delete(void *, size_t)` byla operátor **odstranění umístění** odpovídající umístění **nové** funkce `void * operator new(size_t, size_t)` v C ++ 11. S C ++ 14 velikosti deallocation, tato funkce **odstranění** je nyní *obvyklé funkce mezera umístění* (globální operátor **odstranění).** Standard vyžaduje, aby v případě, že použití **umístění nové** vyhledá odpovídající **odstranit** funkci a najde obvyklou funkci deallocation, program je špatně-tvořil.

   Předpokládejme například, že váš kód definuje **nové umístění** a **odstranění umístění**:

   ```cpp
    void * operator new(std::size_t, std::size_t);
    void operator delete(void*, std::size_t) noexcept;
   ```

   K problému dochází z důvodu shody v podpisech funkce mezi operátorem **odstranění umístění,** který jste definovali, a novým operátorem **odstranění** globální velikosti. Zvažte, zda můžete použít `size_t` jiný typ než pro **jakékoli umístění nové** a **odstranit** operátory.  Všimněte si, `size_t` že typ **typedef** je závislý na kompilátoru; je **typedef** pro **nepodepsané int v** visual c++. Dobrým řešením je použít výčtový typ, jako je tento:

   ```cpp
    enum class my_type : size_t {};
   ```

   Potom změňte definici umístění **nové** a **odstranit** použít tento `size_t`typ jako druhý argument namísto . Budete také muset aktualizovat volání **umístění nové** předat nový typ (například `static_cast<my_type>` pomocí převést z celé číslo hodnoty) a aktualizovat definici **nové** a **odstranit** přetypování zpět na typ celé ho. Není nutné použít **výčtu** pro toto; typ třídy `size_t` s členem bude také fungovat.

   Alternativním řešením je, že byste mohli být schopni odstranit **umístění nové** úplně. Pokud váš kód používá **nové umístění** k implementaci fondu paměti, kde argument umístění je velikost objektu, který je přidělen nebo odstraněn, pak velikost imlokační funkce může být vhodné nahradit vlastní kód fondu paměti a můžete se zbavit umístění funkce a stačí použít vlastní dva **argumenty odstranit** operátor místo umístění funkce.

   Pokud nechcete aktualizovat kód okamžitě, můžete se vrátit ke starému chování pomocí `/Zc:sizedDealloc-`možnosti kompilátoru . Pokud použijete tuto možnost, funkce **odstranění** dvěma argumenty neexistují a nezpůsobí konflikt s operátorem **odstranění umístění.**

- **Členové dat Unie**

   Datové členy sjednocení již nemohou mít typy odkazů. Následující kód byl úspěšně zkompilován v sadě Visual Studio 2013, ale v sadě Visual Studio 2015 vytvoří chybu.

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

   Předchozí kód vytváří následující chyby:

   ```Output
    test.cpp(67): error C2625: 'U2::i': illegal union member; type 'int &' is reference type
    test.cpp(70): error C2625: 'U3::i': illegal union member; type 'int &' is reference type
   ```

   Chcete-li tento problém vyřešit, změňte typy odkazů na ukazatel nebo hodnotu. Změna typu na ukazatel vyžaduje změny v kódu, který používá pole sjednocení. Změna kódu na hodnotu by změnila data uložená v unii, což má vliv na jiná pole, protože pole v typech sjednocení sdílejí stejnou paměť. V závislosti na velikosti hodnoty může také změnit velikost unie.

- **Anonymní odbory**

   jsou nyní více v souladu se standardem. Předchozí verze kompilátoru vygenerovaly explicitní konstruktor a destruktor pro anonymní sjednocení. Ty se odstraní v sadě Visual Studio 2015.

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

   Chcete-li tento problém vyřešit, zadejte vlastní definice konstruktoru nebo destruktoru.

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

- **Odbory s anonymními strukturami**

   Aby bylo možné v souladu se standardem, chování za běhu se změnilo pro členy anonymnístruktury v sjednocení. Konstruktor pro členy anonymní struktury v unii již není implicitně volána při vytvoření takového sjednocení. Destruktor pro členy anonymní struktury v unii již není implicitně volána, když unie přejde mimo rozsah. Zvažte následující kód, ve kterém unie U obsahuje anonymní strukturu, která obsahuje člen, který je pojmenovaná struktura S, která má destruktor.

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

   V sadě Visual Studio 2013 je při vytvoření sjednocení volán konstruktor pro S a destruktor pro S je volán při vyčištění zásobníku pro funkci f. Ale v sadě Visual Studio 2015 konstruktor a destruktor nejsou volány. Kompilátor poskytuje upozornění o této změně chování.

   ```Output
    warning C4587: 'U::s': behavior change: constructor is no longer implicitly calledwarning C4588: 'U::s': behavior change: destructor is no longer implicitly called
   ```

   Chcete-li obnovit původní chování, pojmenujte anonymní strukturu. Chování runtime neanonymních struktur je stejné, bez ohledu na verzi kompilátoru.

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

   Případně zkuste přesunout kód konstruktoru a destruktoru do nových funkcí a přidat volání těchto funkcí z konstruktoru a destruktoru pro sjednocení.

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

- **Rozlišení šablony**

   Byly provedeny změny překladu názvů šablon. V jazyce C++ při zvažování kandidátů pro rozlišení názvu může být případ, že jeden nebo více názvů v úvahu jako potenciální shody vytvoří neplatný vytvoření instance šablony. Tyto neplatné instance obvykle nezpůsobují chyby kompilátoru, což je princip, který je znám jako SFINAE (Selhání nahrazení není chyba).

   Nyní pokud SFINAE vyžaduje kompilátor k vytvoření instance specializace šablony třídy, pak všechny chyby, ke kterým dojde během tohoto procesu jsou chyby kompilátoru. V předchozích verzích by kompilátor tyto chyby ignoroval. Zvažte například následující kód:

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

   Pokud kompilujete s aktuálníkompilátor, zobrazí se následující chyba:

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

   Je tomu tak proto, že v okamžiku prvního vyvolání is_base_of třída "D" ještě nebyla definována.

   V tomto případě oprava není používat tyto vlastnosti typu, dokud třída byla definována. Pokud přesunete definice B a D na začátek souboru kódu, chyba je vyřešena. Pokud jsou definice v souborech hlaviček, zkontrolujte pořadí příkazů include pro soubory hlaviček a ujistěte se, že všechny definice tříd jsou zkompilovány před použitím problematických šablon.

- **Kopírovat konstruktory**

   V obou Visual Studio 2013 a Visual Studio 2015 kompilátor generuje konstruktor kopie pro třídu, pokud tato třída má uživatelem definovaný konstruktor přesunutí, ale žádný uživatelem definovaný konstruktor kopírování. V Dev14 je tento implicitně generovaný konstruktor kopie také označen "= delete".

### <a name="conformance-improvements-in-visual-studio-2015-update-1"></a><a name="VS_Update1"></a>Vylepšení shody v aktualizaci Visual Studio 2015 Update 1

- **Soukromé virtuální základní třídy a nepřímá dědičnost**

   Předchozí verze kompilátoru povoleno odvozené třídy volat členské funkce jeho *nepřímo odvozené* `private virtual` základní třídy. Toto staré chování bylo nesprávné a neodpovídá standardu C++. Kompilátor již přijímá kód napsaný tímto způsobem a v důsledku toho vydává chybu kompilátoru C2280.

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

  \-nebo-

   ```cpp
    class base;  // as above

    class middle: private virtual base {};
    class top: public virtual middle, private virtual bottom {};

    void destroy(top *p)
    {
        delete p;
    }
   ```

- **Přetížený operátor nový a odstranit operátor**

   Předchozí verze kompilátoru povoleno nečlen **operátor nový** a nečlen operátor **odstranit deklarovat** statické a deklarovat v oborech názvů než globální obor názvů.  Toto staré chování vytvořilo riziko, že program nebude volat **novou** nebo **odstranit** implementaci operátoru, kterou programátor zamýšlel, což vedlo k tichému chybnému chování za běhu. Kompilátor již přijímá kód napsaný tímto způsobem a místo toho vydává chybu kompilátoru C2323.

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

   Navíc i když kompilátor neposkytuje konkrétní diagnostiku, inline operátor new je považován za neutvářený.

- **Volání *'typ operátoru*()' (uživatelem definovaný převod) u typů mimo třídu** Předchozí verze kompilátoru povolily volání typu *operátoru*()" u typů mimo třídu, zatímco je tiše ignorovaly. Toto staré chování vytvořilo riziko tichého generování chybného kódu, což vedlo k nepředvídatelnému chování za běhu. Kompilátor již přijímá kód napsaný tímto způsobem a místo toho vydává chybu kompilátoru C2228.

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

- **Redundantní název typu v propracovaných specifikátorech typu**  Předchozí verze kompilátoru povolené **typename** v propracované specifikátory typu; kód napsaný tímto způsobem je sémanticky nesprávný. Kompilátor již přijímá kód napsaný tímto způsobem a místo toho vydává chybu kompilátoru C3406.

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

- **Zadejte odpočet polí ze seznamu inicializačních zařízení**  Předchozí verze kompilátoru nepodporovaly typ odpočtu polí ze seznamu inicializátoru. Kompilátor nyní podporuje tento formulář odpočtu typu a v důsledku toho volání šablon funkcí pomocí seznamů inicializátoru může být nyní nejednoznačné nebo může být vybráno jiné přetížení než v předchozích verzích kompilátoru. Chcete-li tyto problémy vyřešit, program musí nyní explicitně určit přetížení, které programátor zamýšlel.

   Když toto nové chování způsobí, že řešení přetížení zvážit další kandidát, který je stejně dobrý jako historický kandidát, volání se stane nejednoznačný a kompilátor problémy chyba kompilátoru C2668 jako výsledek.

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

   Pokud toto nové chování způsobí přetížení řešení zvážit další kandidát, který je lepší shoda než historický kandidát, volání jednoznačně řeší nového kandidáta, což způsobuje změnu chování programu, která je pravděpodobně odlišná od programátora zamýšlel.

   Příklad 2: změna rozlišení přetížení (před)

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

   Příklad 2: změna rozlišení přetížení (po)

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

- **Obnovení upozornění příkazu switch**

   Předchozí verze kompilátoru odebrala dříve existující upozornění týkající se **příkazů switch;** tato varování byla nyní obnovena. Kompilátor nyní vydává obnovená upozornění a upozornění týkající se konkrétních případů (včetně výchozího případu) jsou nyní vydávána na řádku obsahujícím problematický případ, nikoli na posledním řádku příkazu switch. V důsledku nyní vydávání těchto varování na různých řádcích než v `#pragma warning(disable:####)` minulosti, varování dříve potlačena pomocí již nemusí být potlačeny tak, jak bylo zamýšleno. Chcete-li potlačit tato upozornění, jak bylo `#pragma warning(disable:####)` zamýšleno, může být nutné přesunout směrnice na řádek nad první potenciálně problematický případ. Následují obnovená upozornění.

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

   Příklady dalších obnovených upozornění jsou uvedeny v jejich dokumentaci.

- **#include: použití specifikátoru nadřazeného adresáře '..' v cestě (ovlivňuje** pouze `/Wall` `/WX`)

   Předchozí verze kompilátoru nezjistily použití nadřazeného specifikátoru adresáře ... v názvu směrnic. `#include` Kód napsaný tímto způsobem je obvykle určen k zahrnutí záhlaví, které existují mimo projekt nesprávně pomocí cest relativní chod projektu. Toto staré chování vytvořilo riziko, že by program mohl být zkompilován zahrnutím jiného zdrojového souboru, než programátor zamýšlel, nebo že tyto relativní cesty nebudou přenosné do jiných prostředí sestavení. Kompilátor nyní detekuje a upozorní programátora napsaný takto a vydá volitelné upozornění kompilátoru C4464, pokud je povoleno.

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

   Navíc i když kompilátor neposkytuje konkrétní diagnostiku, doporučujeme také, aby nadřazený adresář specifikátor ".." by měl být použit k určení adresáře zahrnutí projektu.

- **#pragma optimize() rozšiřuje za konec souboru záhlaví** (týká se `/Wall` `/WX`pouze)

   Předchozí verze kompilátoru nezjistily změny nastavení příznaku optimalizace, které unikly souboru záhlaví obsaženému v jednotce překladu. Kompilátor nyní detekuje a upozorní programátora na kód napsaný tímto způsobem a vydá volitelné upozornění kompilátoru C4426 v umístění problematicky `#include`, pokud je povoleno. Toto upozornění je vydáno pouze v případě, že změny v konfliktu s příznaky optimalizace nastavit argumenty příkazového řádku kompilátoru.

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

- **Neshoda #pragma varování (push)** a **#pragma warning(pop)** (týká se `/Wall` `/WX`pouze)

   Předchozí verze kompilátoru nezjistily `#pragma warning(push)` změny `#pragma warning(pop)` stavu spárované se změnami stavu v jiném zdrojovém souboru, který je zřídka určen. Toto staré chování vytvořilo riziko, že program bude kompilován s jinou sadou upozornění povolenou, než programátor zamýšlel, což by mohlo vést k tichému špatnému chování za běhu. Kompilátor nyní detekuje a upozorní programátora napsaný takto a vydá volitelné upozornění kompilátoru C5031 v umístění odpovídající `#pragma warning(pop)`, pokud je povoleno. Toto upozornění zahrnuje poznámku odkazující `#pragma warning(push)`na umístění odpovídající .

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

   Ačkoli neobvyklé, kód napsaný tímto způsobem je někdy úmyslné. Takto napsaný kód je `#include` citlivý na změny v pořadí; pokud je to možné, doporučujeme, aby soubory zdrojového kódu spravovaly stav upozornění samostatným způsobem.

- **Bezkonkurenční #pragma varování (push)** (týká se `/Wall` `/WX`pouze )

   Předchozí verze kompilátoru nezjistily `#pragma warning(push)` neodpovídající změny stavu na konci jednotky překladu. Kompilátor nyní detekuje a upozorní programátora kódu napsaného tímto způsobem a vydá volitelné upozornění kompilátoru `#pragma warning(push)`C5032 v umístění neodpovídající , pokud je povoleno. Toto upozornění je vydáno pouze v případě, že v jednotce překladu nejsou žádné chyby kompilace.

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

- **Další upozornění mohou být vydána v důsledku vylepšeného sledování stavu #pragma varování**

   Předchozí verze kompilátoru `#pragma warning` sledované změny stavu nedostatečně dobře vydat všechna zamýšlená upozornění. Toto chování vytvořilo riziko, že některá upozornění budou účinně potlačena za jiných okolností, než programátor zamýšlel. Kompilátor nyní `#pragma warning` sleduje stav robustněji `#pragma warning` – zejména v souvislosti se změnami stavu uvnitř šablon – a volitelně vydává nová upozornění C5031 a C5032, která mají programátorovi pomoci najít nezamýšlené použití `#pragma warning(push)` a `#pragma warning(pop)`.

   V důsledku vylepšeného `#pragma warning` sledování změn stavu mohou být nyní vydána upozornění dříve nesprávně potlačená nebo upozornění týkající se problémů, které byly dříve chybně diagnostikovány.

- **Vylepšená identifikace nedostupného kódu**

   Změny standardní knihovny jazyka C++ a vylepšená možnost vsazených volání funkcí přes předchozí verze kompilátoru mohou kompilátoru umožnit, aby dokázal, že určitý kód je nyní nedostupný. Toto nové chování může mít za následek nové a častěji vydané instance upozornění C4720.

   ```Output
    warning C4720: unreachable code
   ```

   V mnoha případech toto upozornění může být vydáno pouze při kompilaci s povolené optimalizace, protože optimalizace může vložit více volání funkce, eliminovat redundantní kód nebo jinak umožnit určit, že určitý kód je nedostupný. Zjistili jsme, že nové instance varování C4720 se často vyskytují v **try/catch** bloky, zejména ve vztahu k použití [std::find](../standard-library/algorithm-functions.md#find).

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

### <a name="conformance-improvements-in-visual-studio-2015-update-2"></a><a name="VS_Update2"></a>Vylepšení shody v aktualizaci Visual Studio 2015 Update 2

- **Další varování a chyby mohou být vydány v důsledku částečné podpory výrazu SFINAE**

   Předchozí verze kompilátoru neanalyzují určité druhy výrazů uvnitř specifikátorů **decltype** z důvodu nedostatečné podpory výrazu SFINAE. Toto staré chování bylo nesprávné a neodpovídá standardu C++. Kompilátor nyní analyzuje tyto výrazy a má částečnou podporu výrazu SFINAE z důvodu průběžné zlepšení shody. V důsledku toho kompilátor nyní vydává upozornění a chyby nalezené ve výrazech, které předchozí verze kompilátoru nebyly analyzovat.

   Když toto nové chování analyzuje **decltype** výraz, který obsahuje typ, který ještě nebyl deklarován, kompilátor problémy chyba kompilátoru C2039 jako výsledek.

   ```Output
    error C2039: 'type': is not a member of '`global namespace''
   ```

   Příklad 1: použití nedeklarovaného typu (před)

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

   Když toto nové chování analyzuje **decltype** výraz, který chybí nezbytné použití klíčového slova **typename** k určení, že závislý název je typ, kompilátor vydá upozornění kompilátoru C4346 spolu s chybou kompilátoru C2923.

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

- `volatile`**členské proměnné brání implicitně definovaným konstruktorům a operátorům přiřazení** Předchozí verze kompilátoru umožnily třídě, která má **nestálé** členské proměnné, aby byly automaticky generovány výchozí konstruktory kopírování/přesunutí a výchozí operátory přiřazení kopírování/přesunutí. Toto staré chování bylo nesprávné a neodpovídá standardu C++. Kompilátor nyní považuje třídu, která má nestálé členské proměnné, za netriviální operátory konstrukce a přiřazení, které brání automatickému generování výchozích implementací těchto operátorů. Pokud je taková třída členem unie (nebo anonymní unie uvnitř třídy), konstruktory copy/move a operátory přiřazení copy/move unie (nebo třídy obsahující unonymní sjednocení) budou implicitně definovány jako odstraněné. Pokus o vytvoření nebo zkopírování sjednocení (nebo třídy obsahující anonymní sjednocení) bez jejich explicitního definování je chyba a kompilátor vystaví chybu kompilátoru C2280 jako výsledek.

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

- **Statické členské funkce nepodporují cv-qualifiers.**

   Předchozí verze Visual C++ 2015 povoleno statické členské funkce mít cv-kvalifikátory. Toto chování je způsobeno regrese ve Visual C++ 2015 a Visual C++ 2015 Update 1; Visual C++ 2013 a předchozí verze Visual C++ odmítnout kód napsaný tímto způsobem. Chování Visual C++ 2015 a Visual C++ 2015 Update 1 je nesprávná a neodpovídá standardu C++.  Visual Studio 2015 Update 2 odmítne kód napsaný tímto způsobem a problémy chyba kompilátoru C2511 místo.

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

- **Dopředné prohlášení výčtu není v kódu WinRT povoleno** (týká se `/ZW` pouze)

   Kód zkompilovaný pro prostředí Windows Runtime (WinRT) neumožňuje **předsunout typy výčtu** deklarované, podobně jako `/clr` při kompilaci spravovaného kódu Jazyka C++ pro rozhraní .Net Framework pomocí přepínače kompilátoru. Toto chování je zajišťuje, že velikost výčtu je vždy známa a může být správně promítána do systému typu WinRT. Kompilátor odmítne kód napsaný tímto způsobem a vydá chybu kompilátoru C2599 spolu s chybou kompilátoru C3197.

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

- **Přetížený operátor bez členů new a delete operátoru nemusí být deklarovány jako inline** (Úroveň 1 (`/W1`) ve výchozím nastavení)

   Předchozí verze kompilátoru nevydávají upozornění, když jsou funkce **odstranění** operátoru, které nejsou **členy,** deklarovány jako vepříné. Kód napsaný tímto způsobem je špatně tvarované (není vyžadována žádná diagnostika) a může způsobit problémy s pamětí vyplývající z neshody nové a odstranit operátory (zejména při použití společně s velikosti deallocation), které může být obtížné diagnostikovat. Kompilátor nyní vydává upozornění kompilátoru C4595, který pomáhá identifikovat kód napsaný tímto způsobem.

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

   Oprava kódu, který je napsán tímto způsobem může vyžadovat, aby definice operátoru byly přesunuty ze souboru záhlaví do odpovídajícího zdrojového souboru.

### <a name="conformance-improvements-in-visual-studio-2015-update-3"></a><a name="VS_Update3"></a>Vylepšení shody v aktualizaci Visual Studio 2015 Update 3

- **std::is_convertable nyní detekuje vlastní přiřazení** (standardní knihovna) `std::is_convertable` Předchozí verze vlastnosti typu nezjistily správně vlastní přiřazení typu třídy při odstranění jeho konstruktoru kopie nebo soukromé. Nyní `std::is_convertable<>::value` je správně nastavena na **false** při použití na typ třídy s odstraněné nebo soukromé kopie konstruktoru.

   K této změně není přidružena žádná diagnostika kompilátoru.

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

   V předchozích verzích visual c++ statické kontrolní výrazy v `std::is_convertable<>::value` dolní části tohoto příkladu předat, protože byla nesprávně nastavena na **hodnotu true**. Nyní `std::is_convertable<>::value` je správně nastavena na **false**, což způsobuje statické kontrolní výrazy nezdaří.

- **Výchozí nebo odstraněné triviální kopírování a přesouvání konstruktorů respektuje specifikátory přístupu**

   Předchozí verze kompilátoru nezkontrolovaly specifikátor přístupu výchozí nebo odstraněné triviální kopie a přesunout konstruktory před jejich voláním. Toto staré chování bylo nesprávné a neodpovídá standardu C++. V některých případech toto staré chování vytvořilo riziko tichého generování chybného kódu, což vedlo k nepředvídatelnému chování za běhu. Kompilátor nyní zkontroluje specifikátor přístupu výchozí nebo odstraněné triviální kopie a přesunout konstruktory k určení, zda může být volána, a pokud ne, vydá upozornění kompilátoru C2248 jako výsledek.

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

- **Vyřazení podpory přiřazeného kódu KNIHOVNY ATL** (úroveň 1 (`/W1`) ve výchozím nastavení)

   Předchozí verze kompilátoru podporované přiřazený kód KNIHOVNY ATL. Jako další fáze odebrání podpory pro přiřazený kód KNIHOVNY ATL, který [začal v jazyce Visual C++ 2008](#whats-new-for-c-in-visual-studio-2008), byl přiřazen kód KNIHOVNY ATL zastaral. Kompilátor nyní vydává upozornění kompilátoru C4467, který pomáhá identifikovat tento druh zastaralého kódu.

   ```Output
    warning C4467: Usage of ATL attributes is deprecated
   ```

   Pokud chcete pokračovat v používání přiřazený kód KNIHOVNY ATL, dokud nebude podpora `/Wv:18` odebrána z kompilátoru, můžete toto upozornění zakázat předáním argumentů nebo `/wd4467` příkazového řádku kompilátoru nebo přidáním `#pragma warning(disable:4467)` zdrojového kódu.

   Příklad 1 (před)

   ```cpp
              [uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
    class A {};
   ```

   Příklad 1 (po)

   ```cpp
    __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) A {};
   ```

   Někdy můžete potřebovat nebo chcete vytvořit soubor IDL, abyste se vyhnuli použití zastaralých atributů KNIHOVNY ATL, jako v příkladu níže

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

   Nejprve vytvořte soubor *.idl; generovaný soubor vc140.idl lze použít \*k získání souboru .idl obsahujícího rozhraní a poznámky.

   Dále přidejte krok MIDL do sestavení a ujistěte se, že jsou generovány definice rozhraní Jazyka C++.

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

   Potom použijte ATL přímo v souboru implementace, jako v příkladu kódu níže.

   Příklad implementace 2 (po)

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

- **Předkompilované soubory záhlaví (PCH) a neodpovídající #include direktivy** (týká se `/Wall` `/WX`pouze)

   Předchozí verze kompilátoru přijaly `#include` neodpovídající direktivy ve zdrojových souborech mezi `-Yc` a `-Yu` kompilacemi při použití předkompilovaných souborů záhlaví (PCH). Kód napsaný tímto způsobem již není kompilátorem akceptován. Kompilátor nyní vydává upozornění kompilátoru CC4598, aby pomohl identifikovat neodpovídající `#include` direktivy při použití souborů PCH.

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

- **Předkompilované soubory záhlaví (PCH) a neodpovídající zahrnují adresáře** (týká se `/Wall` `/WX`pouze)

   Předchozí verze přijatého kompilátoru neodpovídající`-I`zahrnují argumenty příkazového řádku `-Yc` adresáře ( ) do kompilátoru mezi a `-Yu` kompilace při použití předkompilovaných souborů záhlaví (PCH). Kód napsaný tímto způsobem již není kompilátorem akceptován.   Kompilátor nyní vydává upozornění kompilátoru CC4599, aby`-I`pomohl identifikovat neodpovídající argumenty příkazového řádku zahrnutí adresáře ( ) při použití souborů PCH.

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

## <a name="whats-new-for-c-in-visual-studio-2013"></a>Co je nového pro C++ ve Visual Studiu 2013

### <a name="improved-iso-cc-standards-support"></a>Vylepšená podpora standardů ISO C/C++

#### <a name="compiler"></a>Kompilátoru

MSVC podporuje tyto funkce jazyka ISO C ++ 11:

- Výchozí argumenty šablony pro šablony funkcí.
- Delegování konstruktorů
- Explicitní operátory převodu.
- Inicializační seznamy a jednotná inicializace.
- Nezpracovaná řetězcová literála.
- Variadické šablony.
- Alias šablony.
- Odstraněné funkce.
- Nestatické inicializátory datových členů (NSDMI).
- Výchozí funkce. \*
- Podporuje tyto funkce jazyka ISO C99:
- _Bool
- Složené literály.
- Určené inicializátory.
- Míchání deklarací s kódem.
- Převod literálu řetězce na upravitelné hodnoty lze povolit pomocí `/Zc:strictStrings`nové možnosti kompilátoru . V jazyce C++98 byl zastaralá konverze z řetězcových literál na `char*` (a široké řetězcové literály na). `wchar_t*` V jazyce C++11 byl převod zcela odebrán. Přestože kompilátor může striktně odpovídat standardu, místo toho poskytuje `/Zc:strictStrings` možnost, takže můžete řídit převod. Ve výchozím nastavení je tato možnost vypnuta. Všimněte si, že pokud používáte tuto možnost v režimu ladění, STL nebude kompilovat.
- rvalue/lvalue Referenční přetypování. S rvalue odkazy C++ 11 lze jasně rozlišovat mezi lvalues a rvalues. Dříve kompilátor neposkytl tuto možnost v konkrétních scénářích přetypování. Byla přidána nová `/Zc:rvalueCast`možnost kompilátoru , která kompilátoru odpovídá pracovnímu dokumentu jazyka C++(viz bod 5.4, [expr.cast]/1). Výchozí chování, pokud tato možnost není zadána, je stejné jako v sadě Visual Studio 2012.

> [!NOTE]
> Pro výchozí funkce není podporováno použití =default k vyžádání konstruktorů přesunutí v memberwise a operátorů přesunutí přiřazení.

### <a name="c99-libraries"></a>C99 Knihovny

Deklarace a implementace jsou přidány pro chybějící funkce v těchto záhlavích: math.h, ctype.h, wctype.h, stdio.h, stdlib.h a wchar.h. Také jsou přidány nové hlavičky complex.h, stdbool.h, fenv.h a inttypes.h a implementace pro všechny funkce deklarované v nich. Existují nové hlavičky obálky Jazyka C++ (ccomplex, cfenv, cinttypes, ctgmath) a řada dalších jsou aktualizovány (ccomplex, cctype, clocale, cmath, cstdint, cstdio, cstring, cwchar a cwctype).

### <a name="standard-template-library"></a>Standardní šablona knihovny

Podpora explicitních operátorů převodu jazyka C++11, seznamů inicializátorů, výčtů s vymezeným oborem a variadických šablon.
Všechny kontejnery nyní podporují požadavky na jemně odstupňovaný prvek jazyka C++11.
Podpora těchto funkcí jazyka C++14:

- "Transparentní operátor functors" méně<>, větší<>, plus<>, násobí<>, a tak dále.
- make_unique\<T> (args...) a make_unique<T[]>(n)
- cbegin()/cend(), rbegin()/rend(), a crbegin()/crend() nečlenné funkce.
- \<atomic> obdrželi řadu vylepšení výkonu.
- \<type_traits> obdržela hlavní stabilizaci a opravy kódu.

### <a name="breaking-changes"></a>Zásadní změny

Tato vylepšená podpora standardů ISO C/C++ může vyžadovat změny existujícího kódu tak, aby odpovídal ac++ 11 a správně zkompiluje v jazyce Visual C++ ve Visual Studiu 2013.

### <a name="visual-c-library-enhancements"></a>Vylepšení knihovny Visual C++

- Je přidána sada C++ REST SDK. Má moderní c++ implementaci rest služeb.
- C++ AMP Textura podpora je vylepšena. Nyní obsahuje podporu pro mipmaps a nové režimy vzorkování.
- Úlohy PPL podporují více plánovacích technologií a asynchronní ladění. Nová api umožňují vytváření úloh PPL pro normální výsledky i podmínky výjimky.

### <a name="c-application-performance"></a>Výkon aplikace c++

- Auto-Vectorizer nyní rozpozná a optimalizuje více vzorů Jazyka C++, aby váš kód běžel rychleji.
- Arm platforma a Atom mikro-architektura zlepšení kvality kódu.
- __vectorcall je přidána konvence volání. Předat argumenty typu vektoru pomocí __vectorcall konvence volání k použití vektorových registrů.
- Nové možnosti propojovacího zařízení. Přepínače `/Gw` (kompilátor) a `/Gy` (assembler) umožňují optimalizace linkeru k vytvoření štíhlejších binárních souborů.
- Podpora sdílené paměti C++ AMP pro snížení nebo vyloučení kopírování dat mezi procesorem a grafickým procesorem.

### <a name="profile-guided-optimization-pgo-enhancements"></a>Vylepšení optimalizace s asistencí profilu (PGO)

- Vylepšení výkonu díky snížení pracovní sady aplikací, které jsou optimalizovány pomocí PGO.
- Vývoj nových aplikací PGO pro Prostředí Windows Runtime.

### <a name="windows-runtime-app-development-support"></a>Podpora vývoje aplikací prostředí Windows Runtime

- **Podpora pro krabicové typy v hodnotě struktury.**

   Nyní můžete definovat typy hodnot pomocí polí, která `IBox<int>^` mohou být null – například na rozdíl od **int**. To znamená, že pole mohou mít hodnotu nebo se mohou rovnat **hodnotě nullptr**.

- **Bohatší informace o výjimce.**

   C++/CX podporuje nový model chyb systému Windows, který umožňuje sběr a šíření bohatých informací o výjimce v binárním rozhraní aplikace (ABI); to zahrnuje zásobníky volání a vlastní řetězce zpráv.

- **Objekt::ToString() je nyní virtuální.**

   Nyní můžete přepsat ToString v uživatelem definovaných typech refů prostředí Windows Runtime.

- **Podpora pro zastaralá api.**

   Veřejná prostředí WINDOWS Runtime API lze nyní označit jako zastaralé a vzhledem k vlastní zprávu, která se zobrazí jako upozornění sestavení a může poskytnout pokyny pro migraci.

- **Vylepšení ladicího programu.**

   Podpora pro nativní/JavaScript interop ladění, Windows Runtime diagnostiku výjimek a asynchronní ladění kódu (Windows Runtime a PPL).

> [!NOTE]
> Kromě funkcí a vylepšení specifických pro C++, které jsou popsány v této části, vám mohou další vylepšení v sadě Visual Studio také pomoci psát lepší aplikace prostředí Windows Runtime.

### <a name="diagnostics-enhancements"></a>Vylepšení diagnostiky

- Vylepšení ladicího programu. Podpora pro asynchronní ladění a pouze ladění kódu.
- Kategorie analýzy kódu. Nyní můžete zobrazit kategorizovaný výstup z Analyzátoru kódu, který vám pomůže najít a opravit vady kódu.
- Diagnostika XAML. Nyní můžete diagnostikovat odezvu uživatelského rozhraní a problémy s používáním baterie v xaml.
- Vylepšení ladění grafického procesoru a GPU.
- Vzdálené zachycení a přehrávání na skutečných zařízeních.
- Simultánní ladění C++ AMP a CPU.
- Vylepšená diagnostika běhu C++ AMP.
- Ladění trasování shaderu výpočetního shaderu HLSL.

### <a name="3-d-graphics-enhancements"></a>3D grafická vylepšení

- Podpora kanálu obsahu obrázků pro předem vynásobený formát alfa DDS.
- Editor obrázků používá interně předem vynásobenou alfa pro vykreslování, a tím zabraňuje vykreslování artefaktů, jako jsou tmavé aureoly.
- Editory obrázků a modelů. Vytvoření uživatelem definovaného filtru je nyní podporováno v návrháři shaderu v editoru obrázků a editoru modelů.

### <a name="ide-and-productivity"></a>IDE a produktivita

**Vylepšené formátování kódu**. Na kód c++ můžete použít další nastavení formátování. Pomocí těchto nastavení můžete řídit umístění závorek a klíčových slov na nový řádek, odsazení, mezery a obtékání řádků. Kód je automaticky formátován při dokončení příkazů a bloků a při vkládání kódu do souboru.

**Dokončení ortézy.** Kód Jazyka C++ nyní automaticky doplní uzavírací znaky, které odpovídají těmto počátečním znakům:

- { (složená závorka)
- [ (hranatá závorka)
- ( (závorky)
- ' (jedna citace)
- "(uvozovky)

**Další funkce automatického dokončování c++.**

- Přidá středník pro typy tříd.
- Dokončí závorky pro nezpracované řetězcové literály.
- Dokončuje víceřádkové komentáře\* \*(/ /)

**Najít všechny odkazy** nyní automaticky vyřeší a filtruje odkazy na pozadí poté, co zobrazí seznam textových shod.

**Filtrování seznamu členů na základě kontextu.** Nepřístupné členy jsou odfiltrovány ze seznamů členů technologie IntelliSense. Například soukromé členy nejsou zobrazeny v seznamu členů, pokud upravujete kód, který implementuje typ. Pokud je seznam členů otevřený, můžete stisknutím **klávesctrlj**+**J** odebrat jednu úroveň filtrování (platí pouze pro aktuální okno seznamu členů). Stisknutím **klávesy Ctrl**+**J** můžete textové filtrování odebrat a zobrazit všechny členy.

**Posouvání nápovědy k parametru.** Zobrazený podpis funkce v popisku nápovědy k parametrům se nyní mění na základě počtu parametrů, které jste skutečně zadali, a nikoli pouze zobrazení libovolného podpisu a jeho neaktualizace na základě aktuálního kontextu. Funkce parametru také funguje správně, když je zobrazena na vnořených funkcích.

**Přepnout soubor záhlaví/kódu.** Nyní můžete přepínat mezi záhlavím a odpovídajícím souborem kódu pomocí příkazu v místní nabídce nebo klávesové zkratky.

**Okno Vlastnosti projektu csizable c++**

**Automatické generování kódu obslužné rutiny události v jazyce C++/CX a C++/CLI.**  Při zadávání kódu pro přidání obslužné rutiny události do souboru kódu C++/CX nebo C++/CLI může editor automaticky generovat instanci delegáta a definici obslužné rutiny události. Okno s popisem se zobrazí, když lze kód obslužné rutiny události automaticky generovat.

**Zvýšení povědomí o DPI.** Nastavení povědomí o dpi pro soubory manifestu aplikace nyní podporuje nastavení "Per Monitor High DPI Aware".

**Rychlejší přepínání konfigurace.** U velkých aplikací se přepínání konfigurací – zejména následných přepínacích operací – provádí mnohem rychleji.

**Budovat čas účinnost.** Četné optimalizace a vícejádrové využití zrychlují sestavení, zejména pro velké projekty. Přírůstková sestavení pro aplikace jazyka C++, které mají odkazy na C++ WinMD jsou také mnohem rychlejší.

## <a name="whats-new-for-c-in-visual-studio-2012"></a>Co je nového pro C++ ve Visual Studiu 2012

### <a name="improved-c11-standards-support"></a>Vylepšená podpora standardů c++11

#### <a name="standard-template-library"></a>Standardní šablona knihovny

- Podpora nových hlavičky \<STL: \<atomic>, chrono>, \<condition_variable>, \<> souborového systému, \<budoucí>, \<> mutex, \<poměr> a \<> vláken.
- Chcete-li optimalizovat využití prostředků paměti, kontejnery jsou nyní menší. Například v režimu vydání x86 `std::vector` s výchozím nastavením se zmenšil z 16 bajtů v sadě Visual Studio 2010 na 12 bajtů v sadě Visual Studio 2012 a `std::map` zmenšil se z 16 bajtů v sadě Visual Studio 2010 na 8 bajtů v sadě Visual Studio 2012.
- Jak je povoleno, ale není vyžadováno standardem C ++ 11, byly implementovány iterátory SCARY.

#### <a name="other-c11-enhancements"></a>Další vylepšení jazyka C++11

- Na základě rozsahu pro smyčky. Můžete psát robustnější smyčky, které pracují s maticemi, kontejnery STL a kolekcemi prostředí Windows Runtime ve formuláři pro ( for-range-declaration : expression ). Toto je součástí základní jazykové podpory.
- Lambdy bez státní příslušnosti, což jsou bloky kódu, které začínají prázdným zaváděčem lambda [] a zachycují žádné místní proměnné, jsou nyní implicitně konvertibilní, aby fungovaly ukazatele podle požadavků standardu C ++ 11.
- Podpora výčtů s rozsahem. Kód výčtu třídy C++ je nyní podporován. Následující kód ukazuje, jak se tento výčet liší od předchozího chování výčtu.

   ```cpp
  enum class Element { Hydrogen, Helium, Lithium, Beryllium };
  void func1(Element e);
  func1(Hydrogen); // error C2065: 'Hydrogen' : undeclared identifier
  func1(Element::Helium); // OK
   ```

### <a name="windows-runtime-app-development-support"></a>Podpora vývoje aplikací prostředí Windows Runtime

- **Nativní model uživatelského uživatelského systému založený na XAML**. Pro aplikace prostředí Windows Runtime můžete použít nový nativní model uživatelského prostředí založený na XAML.
- **Rozšíření komponent Visual C++**. Tato rozšíření zjednodušují spotřebu objektů prostředí Windows Runtime, které jsou nezbytnou součástí aplikací prostředí Windows Runtime. Další informace najdete v tématu Plán pro aplikace prostředí Windows Runtime pomocí odkazů na [jazyky C++](../cppcx/universal-windows-apps-cpp.md) a [Visual C++ (C++/CX).](../cppcx/visual-c-language-reference-c-cx.md)
- **DirectX hry**. Poutavé hry můžete vyvíjet pomocí nové podpory DirectX pro aplikace prostředí Windows Runtime.
- **XAML/DirectX interop**. Aplikace prostředí Windows Runtime, které používají xaml i directx, nyní efektivně spolupracují.
- **Vývoj dll součásti prostředí Windows Runtime**. Vývoj dll součásti umožňuje rozšiřitelné prostředí prostředí prostředí Prostředí Prostředí Windows Runtime.

### <a name="compiler-and-linker"></a>Kompilátor a propojovací linka

- **Auto-vectorizer**. Kompilátor analyzuje smyčky ve vašem kódu a pokud je to možné, vydává pokyny, které používají vektorové registry a pokyny, které jsou k dispozici ve všech moderních procesorů. Díky tomu smyčky běží rychleji. (Pokyny procesoru jsou známé jako SSE, pro streamování rozšíření SIMD). Není nutné povolit nebo požádat o tuto optimalizaci, protože je použita automaticky.
- **Autoparalelizátor**. Kompilátor může analyzovat smyčky ve vašem kódu a vyzařovat pokyny, které rozšiřují výpočty mezi více jader nebo procesorů. To může způsobit, že smyčky běží rychleji. Tuto optimalizaci je nutné požádat, protože není ve výchozím nastavení povolena. V mnoha případech pomáhá zahrnout `#pragma loop(hint_parallel(N))` do kódu bezprostředně před smyčky, které chcete paralelizovat.
- Auto-vectorizer a auto-parallelizer může spolupracovat tak, aby výpočty jsou rozloženy do více jader a kód na každé jádro používá jeho vektorové registry.

### <a name="new-in-visual-studio-2012-update-1"></a>Novinka v aktualizaci Visual Studia 2012 1

Cílte na systém Windows XP při vytváření kódu jazyka C++.
Kompilátor a knihovny jazyka Microsoft C++ můžete použít k cílení na systémy Windows XP a Windows Server 2003.

#### <a name="parallel-programming-support"></a>Podpora paralelního programování

##### <a name="c-accelerated-massive-parallelism-amp"></a>C++ Accelerated Massive Parallelism (AMP)

C++ AMP urychluje provádění kódu Jazyka C++ využitím paralelního datového hardwaru, který je obvykle přítomen jako GPU na samostatné grafické kartě. Programovací model C++ AMP zahrnuje vícerozměrná pole, indexování, přenos paměti, dlaždicové obklady a knihovnu matematických funkcí. Pomocí rozšíření jazyka C++ AMP a omezení kompilátoru můžete řídit, jak se data přesouvají z procesoru na GPU a zpět.

**Ladění.** Ladění prostředí pro aplikace, které používají C++ AMP k cílení GPU je stejně jako ladění pro jiné aplikace C++. To zahrnuje nové paralelní ladění dodatky, které byly zmíněny dříve.

**Profilování.** Nyní existuje podpora profilování pro aktivitu GPU, která je založena na C++ AMP a dalších programovacích modelech založených na Direct3D.

#### <a name="general-parallel-programming-enhancements"></a>Obecná vylepšení paralelního programování

Vzhledem k tomu, že hardware přechází na vícejádrové a mnohojádrové architektury, vývojáři se již nemohou spoléhat na stále rostoucí rychlost hodin z jednojádrových. Podpora paralelního programování v runtime souběžnosti umožňuje vývojářům využívat výhod těchto nových architektur.
V sadě Visual Studio 2010 byly zavedeny výkonné knihovny paralelizace jazyka C++, jako je například knihovna paralelních vzorů, spolu s funkcemi, které využívají souběžnosti vyjádřením sofistikovaných kanálů toku dat. V sadě Visual Studio 2012 byly tyto knihovny rozšířeny tak, aby poskytovaly lepší výkon, větší kontrolu a bohatší podporu paralelních vzorů, které vývojáři potřebují nejvíce. Šíře nabídky nyní zahrnuje:

- Bohatý programovací model založený na úlohách, který podporuje asynchronii a pokračování.
- Paralelní algoritmy, které podporují paralelismus spojení vleků (parallel_for, parallel_for se spřažením, parallel_for_each, parallel_sort, parallel_reduce, parallel_transform).
- Kontejnery bezpečné pro souběžnosti, které poskytují verze datových struktur STD, jako jsou priority_queue, fronty, vektoru a mapy, které jsou bezpečné pro přístup z více vláken.
- Knihovna asynchronních agentů, kterou mohou vývojáři použít k vyjádření kanálů toku dat, které se přirozeně rozkládají na souběžné jednotky.
- Přizpůsobitelný plánovač a správce prostředků pro usnadnění hladkého složení vzorků v tomto seznamu.

##### <a name="general-parallel-debugging-enhancements"></a>Obecná vylepšení paralelního ladění

Kromě okna **Paralelní úkoly** a **Paralelní zásobníky,** Visual Studio 2012 nabízí nové paralelní **sledování** okna, takže můžete prozkoumat hodnoty výrazu ve všech vláknech a procesech a provádět řazení a filtrování na výsledek. Můžete také použít vlastní vizualizéry k rozšíření okna a můžete využít nové podpory více procesů ve všech oknech nástrojů.

### <a name="ide"></a>IDE – integrované vývojové prostředí

**Podpora šablon sady Visual Studio.** Nyní můžete použít technologii Visual Studio Templates k vytváření šablon projektu a položek jazyka C++.

**Asynchronní zatížení řešení.** Projekty jsou nyní načteny asynchronně – nejprve klíčové části řešení – takže můžete začít pracovat rychleji.

**Automatizované nasazení pro vzdálené ladění.** Nasazení souborů pro vzdálené ladění v jazyce Visual C++ bylo zjednodušeno. Možnost **Nasadit** v kontextové nabídce projektu automaticky zkopíruje do vzdáleného počítače soubory, které jsou určeny ve vlastnostech konfigurace ladění. Ruční kopírování souborů do vzdáleného počítače již není nutné.

**C++/CLI IntelliSense.** C++/CLI má nyní plnou podporu Technologie IntelliSense. Funkce technologie IntelliSense, jako jsou rychlé informace, nápověda k parametrům, seznam členů a automatické dokončování, nyní fungují pro c++/CLI. Kromě toho ostatní vylepšení Technologie IntelliSense a IDE uvedená v tomto dokumentu fungují také pro c++/CLI.

**Bohatší popisky Technologie IntelliSense.** Popisky rychlých informací aplikace C++ IntelliSense nyní zobrazují bohatší informace o stylu komentářů dokumentace XML. Pokud používáte rozhraní API z knihovny – například C++ AMP – která má komentáře k dokumentaci XML, pak popisek Technologie IntelliSense zobrazuje více informací než pouze deklarace. Pokud má váš kód komentáře k dokumentaci XML, zobrazí se popisky Technologie IntelliSense bohatší informace.

**Konstrukce kódu jazyka C++.** Kostrový kód je k dispozici pro přepínač, if-else, pro smyčku a další základní konstrukce kódu v rozevíracím seznamu Členové seznamu. Vyberte část kódu ze seznamu, chcete-li jej vložit do kódu a potom vyplňte požadovanou logiku. Můžete také vytvořit vlastní kousky kódu pro použití v editoru.

**Seznam členů Vylepšení.** Rozevírací seznam **Členové seznamu** se zobrazí automaticky při psaní kódu do editoru kódu. Výsledky jsou filtrovány tak, aby při psaní byly zobrazeny pouze příslušné členy. Můžete řídit druh logiky filtrování, který používá seznam členů – v dialogovém okně **Možnosti** v části **Textový editor** > **C/C++** > **Upřesnit**.

**Sémantické zbarvení.** Typy, výčty, makra a další tokeny jazyka C++ mají nyní ve výchozím nastavení vybarvení.

**Zvýraznění odkazů.** Výběr symbolu nyní zvýrazní všechny výskyty symbolu v aktuálním souboru. Stisknutím **kláves Ctrl**+**Shift**+**Arrow** nebo **Ctrl**+**Shift**+Shift**Arrow** se přesuňte mezi zvýrazněné odkazy. Tuto funkci můžete vypnout v dialogovém okně **Možnosti** v části **Textový editor** > **C/C++** > **Upřesnit**.

### <a name="application-lifecycle-management-tools"></a>Nástroje pro správu životního cyklu aplikací

#### <a name="static-code-analysis"></a>Analýza statického kódu

Statická analýza pro c++ byla aktualizována, aby poskytovala bohatší informace o kontextu chyb, další pravidla analýzy a lepší výsledky analýzy. V novém okně Analýza kódu můžete filtrovat zprávy podle klíčového slova, projektu a závažnosti. Když vyberete zprávu v okně, řádek v kódu, kde byla zpráva spuštěna, je zvýrazněn v editoru kódu. Pro některá upozornění jazyka C++ zpráva uvádí zdrojové řádky, které zobrazují cestu spuštění, která vede k upozornění; rozhodnutí a důvody pro přijetí této konkrétní cesty.
Analýza kódu je součástí většiny edicí sady Visual Studio 2012. V edicích Professional, Premium a Ultimate jsou zahrnuta všechna pravidla. V edicích Express pro Windows 8 a Windows Phone jsou zahrnuta pouze nejkritičtější upozornění. Analýza kódu není zahrnuta v edici Express pro web.
Zde jsou některé další vylepšení analýzy kódu:

- Nová upozornění souběžnosti vám pomohou vyhnout se chybám souběžnosti tím, že se ujistíte, že používáte správné uzamykací disciplíny v programech c/c++s více vlákny. Analyzátor detekuje potenciální časovací podmínky, inverze pořadí uzamčení, porušení smlouvy uzamčení volajícího a volavky, neodpovídající synchronizační operace a další chyby souběžnosti.
- Můžete zadat pravidla jazyka C++, která chcete použít pro spuštění analýzy kódu pomocí sad pravidel.
- V okně **Analýza kódu** můžete vložit do zdrojového kódu pragma, který potlačí vybrané upozornění.
- Můžete zvýšit přesnost a úplnost analýzy statického kódu pomocí nové verze jazyka poznámky zdrojového kódu společnosti Microsoft (SAL) k popisu, jak funkce používá své parametry, předpoklady, které o nich provede, a záruky, které provede po dokončení.
- Podpora 64bitc++ projektů.

#### <a name="updated-unit-test-framework"></a>Aktualizovaný rámec testování částí

Pomocí nového rozhraní testování částí C++ v sadě Visual Studio zapište testy částí jazyka C++. Přidejte nový projekt testování částí do stávajícího řešení jazyka C++ vyhledáním šablony projektu testování částí c++ v kategorii Visual C++ v dialogovém okně Nový projekt. Začněte psát testy částí v generované TEST_METHOD kód se zakázaným inzerováním v souboru Unittest1.cpp. Při zápisu testovacího kódu vytvořte řešení. Chcete-li spustit testy, otevřete okno **Průzkumník a test jednotky** výběrem **možnosti Zobrazit** > další**Průzkumník testování částí systému****Windows** > a v místní nabídce požadovaného testovacího případu zvolte **Spustit vybraný test**. Po dokončení testu můžete zobrazit výsledky testů a další informace o trasování zásobníku ve stejném okně.

#### <a name="architecture-dependency-graphs"></a>Grafy závislostí architektury

Chcete-li lépe porozumět kódu, můžete nyní generovat grafy závislostí pro binární, třídu, obor názvů a zahrnout soubory do řešení. Na řádku nabídek zvolte **Architektura** > **generovat graf závislostí**a potom pro **řešení** nebo pro **zahrnout soubor** generovat graf závislostí. Po dokončení generování grafu můžete prozkoumat rozšířením každého uzlu, naučit vztahy závislostí přesunutím mezi uzly a procházet zdrojový kód výběrem **zobrazit obsah** v místní nabídce pro uzel. Chcete-li generovat graf závislostí pro soubory zahrnutí, zvolte v místní nabídce souboru zdrojového kódu \*CPP nebo \*soubor hlavičky .h možnost Generovat graf **zahrnutých souborů**.

#### <a name="architecture-explorer"></a>Průzkumník architektury

Pomocí **Průzkumníka architektury**můžete prozkoumat datové zdroje v řešení jazyka C++, projektech nebo souborech. Na řádku nabídek zvolte **Architektura** > **Průzkumníka architektury****windows** > . Můžete vybrat uzel, který vás zajímá, například **Zobrazení třídy**. V tomto případě je pravá strana okna nástroje rozbalena o seznam oborů názvů. Pokud vyberete obor názvů, nový sloupec zobrazí seznam tříd, struktur a výčtů v tomto oboru názvů. Můžete pokračovat v prozkoumání těchto datových zdrojů nebo se vrátit ke sloupci zcela vlevo a spustit další dotaz. Viz **Hledání kódu pomocí Průzkumníka architektury**.

#### <a name="code-coverage"></a>Pokrytí kódu

Pokrytí kódu bylo aktualizováno na dynamicky instrumentální binární soubory za běhu. To snižuje režii konfigurace a poskytuje lepší výkon. Můžete také shromažďovat data pokrytí kódu z testů částí pro aplikace C++. Když jste vytvořili testy jednotek C++, můžete použít **Průzkumník testování částí** ke zjištění testů ve vašem řešení. Chcete-li spustit testy částí a shromažďovat data pokrytí kódu pro ně, v **Průzkumníku testování částí**zvolte **Analyzovat pokrytí kódu**. Výsledky pokrytí kódu můžete zkontrolovat v okně **Výsledky pokrytí kódu** – na řádku nabídek zvolte **Testovat** > **výsledky pokrytí kódu systému****Windows** > .

## <a name="whats-new-for-c-in-visual-studio-2010"></a>Co je nového pro C++ ve Visual Studiu 2010

### <a name="c-compiler-and-linker"></a>Kompilátor a propojovací program jazyka C++

**automatické klíčové slovo.** Klíčové slovo **auto** má nový účel. Výchozí význam **klíčového** slova auto použijte k deklarování proměnné, jejíž typ je odvozen z inicializačního výrazu v deklaraci proměnné. Možnost `/Zc:auto` kompilátoru vyvolá buď nový nebo předchozí význam klíčového slova **auto.**

**Dekletype Typ Specifikátor.** Specifikátor typu **decltype** vrátí typ zadaného výrazu. Pomocí specifikátoru typu **decltype** v kombinaci s klíčovým slovem **auto** deklarujte typ, který je buď složitý, nebo je znám pouze kompilátoru. Pomocí kombinace můžete například deklarovat funkci šablony, jejíž návratový typ závisí na typech argumentů šablony. Nebo deklarujte funkci šablony, která volá jinou funkci, a pak vrátí návratový typ volané funkce.

**Lambda výrazy.** Lambda funkce mají tělo funkce, ale žádný název. Funkce Lambda kombinují nejlepší vlastnosti ukazatelů funkce a objektů funkce. Funkci lambda použijte samostatně jako parametr funkce šablony namísto objektu funkce nebo společně s klíčovým slovem **auto** deklarujte proměnnou, jejíž typ je lambda.

**Rvalue Reference.** Deklarátor odkazu na rvalue (&&) deklaruje odkaz na rvalue. Odkaz na rvalue umožňuje použít sémantiku přesunutí a dokonalé předávání k zápisu efektivnějších konstruktorů, funkcí a šablon.

**prohlášení static_assert.** Deklarace **static_assert** testuje kontrolní výraz softwaru v době kompilace, na rozdíl od jiných kontrolních mechanismů, které testují za běhu. Pokud se kontrolní výraz nezdaří, kompilace se nezdaří a je vydána zadaná chybová zpráva.

**nullptr a __nullptr klíčová slova.** MSVC umožňuje používat klíčové slovo **nullptr** s nativním kódem nebo se spravovaným kódem. Klíčové slovo **nullptr** označuje, že popisovač objektu, vnitřní ukazatel nebo nativní typ ukazatele neodkazuje na objekt. Kompilátor interpretuje **nullptr,** který má `/clr` být spravován při použití možnosti kompilátoru, a nativní kód, pokud tuto `/clr` možnost nepoužíváte.
Klíčové slovo **__nullptr** specifické pro společnost Microsoft má stejný význam jako **nullptr**, ale vztahuje se pouze na nativní kód. Pokud kompilujete nativní kód `/clr` C/C++ pomocí možnosti kompilátoru, kompilátor nemůže určit, zda je klíčové slovo **nullptr** nativní nebo spravované termín. Chcete-li, aby byl váš záměr kompilátoru jasný, použijte klíčové slovo nullptr k určení spravovaného termínu a **__nullptr** k určení nativního termínu.

**/Zc:možnost kompilátoru trigrafů.** Ve výchozím nastavení je zakázána podpora trigrafů. Pomocí `/Zc:trigraphs` možnosti kompilátoru povolte podporu trigrafů.
Trigraph se skládá ze dvou po sobě jdoucích otazníků (??) následovaných jedinečným třetím znakem. Kompilátor nahradí trigraph odpovídajícím interpunkčním znakem. Například kompilátor nahradí ?? = trigraph se znakem #(znak čísla). Použijte trigrafy ve zdrojových souborech Jazyka C, které používají znakovou sadu, která neobsahuje určité interpunkční znaky.

**Nová možnost optimalizace s asistencí profilu.** PogoSafeMode je nová možnost optimalizace s asistencí profilu, která vám umožní určit, zda chcete použít nouzový režim nebo rychlý režim při optimalizaci aplikace. Nouzový režim je bezpečný pro přístup z více vláken, ale je pomalejší než rychlý režim. Rychlý režim je výchozí chování.

**Nový společný jazyk Runtime (CLR) Option /clr:nostdlib.** Je přidána nová `/clr` možnost (Kompilace common language runtime). Pokud jsou zahrnuty různé verze stejných knihoven, je vydána chyba kompilace. Nová možnost umožňuje vyloučit výchozí knihovny CLR, aby váš program mohl používat zadanou verzi.

**Nová směrnice pragma detect_mismatch.** Směrnice pragma detect_mismatch umožňuje umístit značku do souborů, která je porovnána s jinými značkami, které mají stejný název. Pokud existuje více hodnot pro stejný název, propojovací aplikace vydá chybu.

**Vnitřní síta XOP, vnitřní objekty FMA4 a vnitřní objekty LWP.** Byly přidány nové vnitřní funkce pro podporu vnitřních prostředí XOP přidané pro visual studio 2010 SP1, FMA4 Intrinsics přidané pro visual studio 2010 SP1 a vnitřní zařízení LWP přidané pro technologie procesorů Visual Studio 2010 SP1. Pomocí __cpuid __cpuidex určete, které technologie procesoru jsou v konkrétním počítači podporovány.

### <a name="visual-studio-c-projects-and-the-build-system"></a>Projekty Visual Studio C++ a systém sestavení

**Msbuild.** Řešení a projekty visual c++ jsou nyní vytvářeny pomocí programu MSBuild.exe, který nahrazuje program VCBuild.exe. MSBuild je stejný flexibilní, rozšiřitelný nástroj sestavení založený na XML, který používá ostatní jazyky sady Visual Studio a typy projektů. Z důvodu této změny nyní soubory projektu sady Visual Studio C++ používají formát souboru XML a mají příponu .vcxproj. Soubory projektu Visual Studio C++ z dřívějších verzí sady Visual Studio se automaticky převedou do nového formátu souboru.

**Adresáře VC++.** Nastavení adresářů VC++ je nyní umístěno na dvou místech. Pomocí stránek vlastností projektu můžete nastavit hodnoty pro projekt pro adresáře VC++. Pomocí **Správce vlastností** a seznamu vlastností nastavte globální hodnoty pro konfiguraci adresářů VC++.

**Závislosti mezi projekty.** V dřívějších verzích byly definované závislosti mezi projekty uloženy v souboru řešení. Při převodu těchto řešení do nového formátu souboru projektu jsou závislosti převedeny na odkazy projekt na projekt. Tato změna může ovlivnit aplikace, protože koncepty závislostí řešení a odkazů mezi projekty se liší.

**Makra a proměnné prostředí.** Nové makro _ITERATOR_DEBUG_LEVEL vyvolá podporu ladění pro iterátory. Toto makro použijte místo starších _SECURE_SCL a _HAS_ITERATOR_DEBUGGING makra.

### <a name="visual-c-libraries"></a>Knihovny jazyka Visual C++

**Souběžné knihovny runtime.** Souběžné runtime framework podporuje aplikace a součásti, které běží současně a je rámec pro programování souběžných aplikací v jazyce Visual C++. Pro podporu souběžného programování aplikací poskytuje knihovna paralelních vzorů (PPL) univerzální kontejnery a algoritmy pro provádění jemně odstupňovaného paralelismu. Knihovna asynchronních agentů poskytuje programovací model založený na actoru a rozhraní pro předávání zpráv pro hrubozrnné tok dat a úlohy pipeliningu.

**Standardní knihovna C++.** Následující seznam popisuje mnoho změn, které byly provedeny v knihovně Standard C++.

- Nová funkce jazyka rvalue reference C++ byla použita k implementaci sémantiky přesunutí a dokonalého předávání pro mnoho funkcí v knihovně standardních šablon. Přesuňte sémantiku a dokonalé předávání výrazně zlepšit výkon operací, které přidělují nebo přiřazují proměnné nebo parametry.
- Rvalue odkazy se také používají `unique_ptr` k implementaci nové třídy, což `auto_ptr` je bezpečnější inteligentní ukazatel typu než třídy. Třída `unique_ptr` je movitá, ale není kopírovatelná, implementuje sémantiku přísného vlastnictví bez ovlivnění bezpečnosti a dobře funguje s kontejnery, které jsou si vědomy rvalue odkazy. Třída `auto_ptr` je zastaralá.
- Do `find_if_not` \<hlavičky algoritmu> `copy_if`bylo `is_sorted`přidáno patnáct nových funkcí, například , , a .
- V \<záhlaví paměti> je funkce nové make_shared pohodlným, robustním a efektivním způsobem, jak vytvořit sdílený ukazatel na objekt současně s vytvořením objektu.
- Singly propojené seznamy \<jsou podporovány hlavičkou forward_list>.
- Nové `cbegin`, `cend` `crbegin`, `crend` a členské `const_iterator` funkce poskytují, který se pohybuje vpřed nebo vzad přes kontejner.
- Záhlaví \<system_error> a související šablony podporují zpracování systémových chyb nižší úrovně. Členy třídy `exception_ptr` lze použít k přenosu výjimek mezi vlákny.
- Hlavička \<codecvt> podporuje převod různých kódování znaků Unicode na jiná kódování.
- Alokátory \<> záhlaví definuje několik šablon, které pomáhají přidělit a uvolnit bloky paměti pro kontejnery založené na uzlu.
- Existuje mnoho aktualizací \<náhodného> záhlaví.

### <a name="microsoft-foundation-class-mfc-library"></a>Knihovna třídy Microsoft Foundation (MFC)

**Funkce systému Windows 7.** Knihovna MFC podporuje mnoho funkcí systému Windows 7, například uživatelské rozhraní pásu karet, hlavní panel, seznamy odkazů, miniatury s kartami, náhledy miniatur, indikátor průběhu, překrytí ikon a indexování vyhledávání. Vzhledem k tomu, že knihovna MFC automaticky podporuje mnoho funkcí systému Windows 7, nemusí být nutné upravit stávající aplikaci. Chcete-li podporovat další funkce v nových aplikacích, použijte Průvodce aplikací knihovny MFC k určení funkcí, které chcete použít.

**Multi-touch povědomí.** Knihovna MFC podporuje aplikace, které mají vícedotykové uživatelské rozhraní, například aplikace, které jsou napsány pro operační systém Microsoft Surface. Vícedotyková aplikace dokáže zpracovat dotykové zprávy a zprávy gesty systému Windows, což jsou kombinace dotykových zpráv. Stačí zaregistrovat aplikaci pro události dotykového ovládání a gest a operační systém bude směrovat události s více dotykovými událostmi do obslužných rutin událostí.

**Povědomí o vysokém dpi.** Ve výchozím nastavení aplikace knihovny MFC jsou nyní high-DPI vědomi. Pokud aplikace je High-DPI (vysoké tečky na palec) vědomi, operační systém můžete škálovat okna, text a další prvky uživatelského rozhraní na aktuální rozlišení obrazovky. To znamená, že obraz s měřítkem je pravděpodobnější, že bude správně rozložen a není oříznut nebo pixelován.

**Správce restartování.** Správce restartování automaticky uloží dokumenty a restartuje aplikaci, pokud se neočekávaně zavře nebo restartuje. Můžete například použít správce restartování ke spuštění aplikace po zavření automatickou aktualizací. Další informace o konfiguraci aplikace tak, aby používala správce restartování, naleznete v **tématu How to: Add Restart Manager Support**.

**CTaskDialog.** Třídu `CTaskDialog` lze použít namísto `AfxMessageBox` standardního okna se zprávou. Třída `CTaskDialog` zobrazuje a shromažďuje více informací než standardní okno se zprávou.

#### <a name="safeint-library"></a>SafeInt – knihovna

Nová knihovna SafeInt provádí bezpečné aritmetické operace, které představují přetečení celého čísla. Tato knihovna také porovnává různé druhy celých čísel.

#### <a name="new-active-template-library-atl-macros"></a>Makra nové knihovny aktivních šablon (ATL)

Do souboru ATL byla přidána nová makra, která rozšiřují funkce PROP_ENTRY_TYPE a PROP_ENTRY_TYPE_EX. PROP_ENTRY_INTERFACE a PROP_ENTRY_INTERFACE_EX vám umožní přidat seznam platných CLSID. PROP_ENTRY_INTERFACE_CALLBACK a PROP_ENTRY_INTERFACE_CALLBACK_EX umožňují určit funkci zpětného volání k určení, zda je clsid platný.

#### <a name="analyze-warnings"></a>/analyzovat varování

Většina `/analyze` (Enterprise Code Analysis) upozornění byly odebrány z C Run-Time (CRT), MFC a KNIHOVNY ATL.

#### <a name="animation-and-d2d-support"></a>Podpora pro animaci a D2D

Knihovna MFC nyní podporuje animaci a grafiku Direct2D. Knihovna knihovny MFC má několik nových tříd knihovny MFC a funkce pro podporu této funkce. K dispozici jsou také dva nové návody, které ukazují, jak přidat objekt D2D a objekt animace do projektu. Tyto návody jsou **návod: Přidání objektu D2D do projektu knihovny MFC** a **návod: Přidání animace do projektu knihovny MFC**.

### <a name="ide"></a>IDE – integrované vývojové prostředí

**Vylepšená technologie IntelliSense.** Technologie IntelliSense for Visual C++ byla kompletně přepracována tak, aby byla rychlejší, přesnější a schopná zvládat větší projekty. K dosažení tohoto zlepšení ide dělá rozdíl mezi jak vývojář zobrazení a upravuje zdrojový kód a jak ide používá zdrojový kód a nastavení projektu k vytvoření řešení.
Z důvodu tohoto oddělení povinností jsou funkce procházení, jako je **zobrazení třídy** a nové dialogové okno **Přejít na,** zpracovány systémem, který je založen na novém souboru databáze SQL Server pro stolní počítače (.sdf), který nahrazuje starý soubor no compile browse (.ncb). Funkce technologie IntelliSense, jako jsou rychlé informace, automatické dokončování a pomoc s parametry, analyzují jednotky překladu pouze v případě potřeby. Hybridní funkce, jako je například nové okno **Hierarchie volání,** používají kombinaci funkcí procházení a technologie IntelliSense.
Vzhledem k tomu, že technologie IntelliSense zpracovává pouze informace, které v současné době požadujete, rozhraní IDE je citlivější. Protože jsou informace aktuálnější, jsou zobrazení i deinebo okna přesnější. A konečně, protože infrastruktura IDE je lépe organizovaná, schopnější a škálovatelnější, může zpracovávat větší projekty.

**Vylepšené chyby technologie IntelliSense.** IDE lépe detekuje chyby, které by mohly způsobit ztrátu Technologie IntelliSense, a zobrazí pod nimi červené podtržení vlnovkou. Rozhraní IDE navíc hlásí chyby technologie IntelliSense do **okna seznamu chyb**. Chcete-li zobrazit kód, který je příčinou problému, poklepejte na chybu v **okně seznamu chyb**.

**#include funkce automatického dokončování.** IDE podporuje automatické dokončování pro `#include` klíčové slovo. Při psaní `#include`vytvoří ide rozevírací seznam platných souborů hlaviček. Pokud budete pokračovat zadáním názvu souboru, ide filtruje seznam na základě vaší položky. Kdykoli můžete vybrat ze seznamu soubor, který chcete zahrnout. To vám umožní rychle zahrnout soubory bez znalosti přesného názvu souboru.

**Přejít na.** Dialogové okno **Přejít na** umožňuje vyhledat všechny symboly a soubory v projektu, které odpovídají zadanému řetězci. Výsledky hledání jsou okamžitě revidovány při psaní dalších znaků do vyhledávacího řetězce. Pole **Zpětná vazba výsledků** udává počet nalezených položek a pomáhá vám rozhodnout se, zda hledání omezíte. Pole **Druh/Obor**, **Umístění**a **Náhled** zpětné vazby vám pomohou rozptýlit položky, které mají podobné názvy. Kromě toho můžete tuto funkci rozšířit tak, aby podporovala další programovací jazyky.

**Paralelní ladění a profilování.** Ladicí program sady Visual Studio si je vědom aconcurrency Runtime a pomáhá řešit potíže s paralelními zpracováním aplikací. Můžete použít nový nástroj profiler souběžnosti k vizualizaci celkové chování aplikace. Pomocí nových oken nástrojů můžete také vizualizovat stav úkolů a jejich zásobníky volání.

**Návrhář pásu karet.** **Návrhář pásu karet** je grafický editor, který umožňuje vytvářet a upravovat uživatelské rozhraní pásu karet knihovny MFC. Konečné uzp., které je reprezentováno souborem prostředků založeným na xml (.mfcribbon-ms). U existujících aplikací můžete zachytit aktuální unové nastavení pásu karet dočasným přidáním několika řádků kódu a následným vyvoláním **Návrháře pásu karet**. Po vytvoření souboru prostředků pásu karet můžete ručně psaný kód ui pásu karet nahradit několika příkazy, které načítají prostředek pásu karet.

**Hierarchii volání.** Okno **Hierarchie volání** umožňuje přejít na všechny funkce, které jsou volány určitou funkcí, nebo na všechny funkce, které volají určitou funkci.

### <a name="tools"></a>nástroje

**Průvodce třídou knihovny MFC.** Visual C++ 2010 přináší zpět uznávaný nástroj Průvodce třídami knihovny MFC. Průvodce třídou knihovny MFC představuje pohodlný způsob přidání tříd, zpráv a proměnných do projektu bez nutnosti ruční úpravy sad zdrojových souborů.

**Průvodce řízením atl.** Průvodce řízením seznamu atl již `ProgID` pole automaticky nevyplňuje. Pokud ovládací prvek ATL `ProgID`nemá , jiné nástroje nemusí pracovat s ním. Jedním z příkladů nástroje, který `ProgID` vyžaduje, aby ovládací prvky měly, je dialogové okno **Vložit aktivní řízení.** Další informace o dialogovém okně naleznete v **tématu Vložení ovládacího dialogového okna ActiveX**.

### <a name="microsoft-macro-assembler-reference"></a>Microsoft Macro Assembler – referenční dokumentace

Přidání datového typu YMMWORD podporuje 256bitové multimediální operandy, které jsou součástí pokynů Intel Advanced Vector Extensions (AVX).

## <a name="whats-new-for-c-in-visual-studio-2008"></a>Co je nového pro C++ v sadě Visual Studio 2008

### <a name="visual-c-integrated-development-environment-ide"></a>Integrované vývojové prostředí Visual C++ (IDE)

- Dialogová okna vytvořená v aplikacích KNIHOVNY ATL, MFC a Win32 nyní splňují pokyny pro styl systému Windows Vista. Při vytváření nového projektu pomocí sady Visual Studio 2008 budou všechna dialogová okna, která vložíte do aplikace, splňovat pokyny pro styl systému Windows Vista. Pokud překompilujete projekt, který jste vytvořili se starší verzí sady Visual Studio, všechna existující dialogová okna zachová stejný vzhled, který dříve měla. Další informace o vkládání dialogových oken do aplikace naleznete v **tématu Dialog Editor**.

- Průvodce **projektem ATL** má nyní možnost zaregistrovat součásti pro všechny uživatele. Počínaje visual studio 2008 jsou komponenty modelu COM a knihovny typů vytvořené průvodcem **projektu knihovny ATL** registrovány v uzlu HKEY_CURRENT_USER registru, pokud nevyberete **možnost Registrovat komponentu pro všechny uživatele**.
- Průvodce **projektem knihovny ATL** již neposkytuje možnost vytvořit projekty atl přiřazené knihovny ATL. Počínaje Visual Studio 2008 průvodce **projektem knihovny ATL** nemá možnost změnit přiřazený stav nového projektu. Všechny nové projekty knihovny ATL, které průvodce vytvoří, jsou nyní nepřiřazené.
- Zápis do registru lze přesměrovat. Se zavedením systému Windows Vista, zápis do určitých oblastí registru vyžaduje program spustit ve zvýšeném režimu. Není žádoucí vždy spustit visual studio ve zvýšeném režimu. Přesměrování na uživatele automaticky přesměruje zápisy registru z HKEY_CLASSES_ROOT do HKEY_CURRENT_USER bez jakýchkoli změn programování.
- **Návrhář tříd** má nyní omezenou podporu pro nativní kód Jazyka C++. V dřívějších verzích sady Visual Studio pracoval **Návrhář tříd** pouze s visual c# a visual basic. Uživatelé jazyka C++ teď můžou používat **Návrhář e-také v šaku**) třídách , ale pouze v režimu jen pro čtení. Další informace o použití **Návrháře tříd** s C++naleznete v **tématu Práce s visual c++ kód em v Návrháři tříd**.
- Průvodce projektem již nemá možnost vytvořit projekt serveru SQL Server jazyka C++. Počínaje Visual Studio 2008, nový průvodce projektu nemá možnost vytvořit projekt C++ SQL Server. Sql Server projekty vytvořené pomocí starší verze sady Visual Studio bude stále kompilovat a pracovat správně.

### <a name="visual-c-libraries"></a>Knihovny jazyka Visual C++

#### <a name="general"></a>Obecné

- Aplikace mohou být vázány na konkrétní verze knihoven Visual C++. Někdy aplikace závisí na aktualizacích, které byly provedeny v knihovnách Visual C++ po vydání. V tomto případě spuštění aplikace v počítači, který má starší verze knihoven může způsobit neočekávané chování. Nyní můžete svázat aplikaci s určitou verzí knihoven tak, aby nebyla spuštěna v počítači, který má starší verzi knihoven.

#### <a name="stlclr-library"></a>STL/CLR – knihovna

- Visual C++ nyní obsahuje knihovnu STL/CLR. Knihovna STL/CLR je obal knihovny standardníšablony (STL), podmnožiny standardní knihovny C++pro použití s c++ a clr rozhraní .NET Framework. S STL/CLR, nyní můžete použít všechny kontejnery, iterátory a algoritmy STL ve spravovaném prostředí.

#### <a name="mfc-library"></a>Knihovna knihovny MFC

- Systém Windows Vista podporuje běžné ovládací prvky. Více než 150 metody v 18 nové nebo existující třídy byly přidány do podpory funkcí v systému Windows Vista nebo ke zlepšení funkčnosti v aktuálních tříd knihovny MFC.
- Nová `CNetAddressCtrl` třída umožňuje zadávání a ověřování adres IPv4 a IPv6 nebo názvů DNS.
- Nová `CPagerCtrl` třída zjednodušuje použití ovládacího prvku stránkovače systému Windows.
- Nová `CSplitButton` třída zjednodušuje použití ovládacího prvku Windows splitbutton pro výběr výchozí nebo volitelné akce.

#### <a name="c-support-library"></a>Knihovna podpory C++

- C++ zavádí zařazovací knihovny. Zařazovací knihovna poskytuje snadný a optimalizovaný způsob zařazování dat mezi nativní a spravovaná prostředí. Knihovna je alternativou k složitější a méně efektivní přístupy, jako je například použití PInvoke. Další informace najdete **v tématu Přehled zařazování v jazyce C++.**

#### <a name="atl-server"></a>ATL Server

- Atl Server je vydán jako projekt sdíleného zdroje.
- Většina základního kódu serveru ATL byla vydána jako projekt sdíleného zdroje v codeplexu a není nainstalována jako součást sady Visual Studio 2008. Několik souborů přidružených ke serveru ATL již není součástí sady Visual Studio. Seznam odebraných souborů naleznete v tématu **Removed ATL Server Files**.
- Třídy kódování a dekódování dat z atlenc.h a utility funkce a třídy z atlutil.h a atlpath.h jsou nyní součástí knihovny ATL.
- Společnost Microsoft bude nadále podporovat verze serveru ATL, které jsou součástí dřívějších verzí sady Visual Studio, pokud jsou podporovány tyto verze sady Visual Studio. CodePlex bude pokračovat ve vývoji kódu ATL Serveru jako komunitní projekt. Společnost Microsoft nepodporuje verzi codeplexu serveru ATL.

### <a name="visual-c-compiler-and-linker"></a>Kompilátor a propojovací program Visual C++

#### <a name="compiler-changes"></a>Změny kompilátoru

- Kompilátor podporuje spravovaná přírůstková sestavení. Když zadáte tuto možnost, kompilátor nebude znovu zkompilovat kód při změně odkazované sestavení. Místo toho bude provádět přírůstkové sestavení. Soubory jsou znovu kompilovány pouze v případě, že změny ovlivní závislý kód.
- Atributy související se serverem ATL již nejsou podporovány. Kompilátor již nepodporuje několik atributů, které přímo souvisely se serverem ATL. Úplný seznam odebraných atributů naleznete v tématu Breaking Changes.
- Kompilátor podporuje mikroarchitekturu Intel Core. Kompilátor obsahuje ladění pro mikroarchitekturu Intel Core během generování kódu. Ve výchozím nastavení je toto ladění zapnuté a nelze jej zakázat, protože také pomáhá Pentium 4 a dalším procesorům.
- Vnitřní objekty podporují novější procesory AMD a Intel. Několik nových vnitřních pokynů podporuje větší funkčnost v novějších procesorech AMD a Intel. Další informace o nových vnitřních objektech naleznete v **tématu Doplňkové rozšíření SIMD pro streamování 3 Pokyny**, Rozšíření **služby SIMD pro streamování 4 – pokyny**, **SSE4A a Pokročilé vnitřní jednotky bitů**, **Vnitřní objekty AES**, **_mm_clmulepi64_si128**a **__rdtscp**.
- Funkce `__cpuid` je aktualizována. Funkce `__cpuid` `__cpuidex` nyní podporují několik nových funkcí z nejnovějších revizí procesorů AMD a Intel. `__cpuidex` Vnitřní je nový a shromažďuje další informace z posledních procesorů.
- Možnost `/MP` kompilátoru snižuje celkovou dobu sestavení. Tato `/MP` možnost může výrazně snížit celkový čas kompilace několika zdrojových souborů vytvořením několika procesů, které kompilují soubory současně. Tato možnost je užitečná zejména v počítačích, které podporují hyperthreading, více procesorů nebo více jader.
- Možnost `/Wp64` kompilátoru a klíčové slovo **__w64** jsou zastaralé. Možnost `/Wp64` kompilátoru a **__w64** klíčové slovo, které detekují problémy s přenositelností 64 bitů, jsou zastaralé a budou odebrány v budoucí verzi kompilátoru. Namísto této možnosti kompilátoru a klíčové slovo, použijte MSVC, který se zaměřuje na 64bitovou platformu.
- `/Qfast_transcendentals`generuje vtípkový kód pro transcendentální funkce.
- `/Qimprecise_fwaits`odebere příkazy fwait vnitřní vyzkoušet bloky `/fp:except` při použití možnosti kompilátoru.

### <a name="linker-changes"></a>Změny propojovacího propojení

- Informace o řízení uživatelských účtů jsou nyní vloženy do souborů manifestu pro spustitelné soubory pomocí propojovacího programu Visual C++ (link.exe). Tato funkce je ve výchozím nastavení povolena. Další informace o tom, jak zakázat tuto funkci nebo `/MANIFESTUAC` jak změnit výchozí chování, naleznete v tématu (Vložení informací nástroje Řízení dat do manifestu).
- Propojovací program `/DYNAMICBASE` má nyní možnost povolit funkci randomizace rozložení adresního prostoru systému Windows Vista. Tato možnost upravuje záhlaví spustitelného souboru označující, zda aplikace by měla být náhodně rebased v době načítání.

## <a name="whats-new-for-c-in-visual-studio-2005"></a>Co je nového pro C++ v sadě Visual Studio 2005

V aktualizaci Visual C++ 2005 Service Pack 1 byly nové následující funkce:

### <a name="intrinsics-for-x86-and-x64"></a>Vnitřní objekty pro x86 a x64

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

### <a name="intrinsics-for-x64-only"></a>Vnitřní objekty pouze pro x64

- __vmx_on
- __vmx_vmclear
- __vmx_vmlaunch
- __vmx_vmptrld
- __vmx_vmread
- __vmx_vmresume
- __vmx_vmwrite

### <a name="new-language-keywords"></a>Klíčová slova nového jazyka

__sptr, __uptr

### <a name="new-compiler-features"></a>Nové funkce kompilátoru

Kompilátor má nejnovější změny v této verzi.

- 64bitové nativní a křížové kompilátory.
- `/analyze`(Enterprise Code Analysis) byla přidána možnost kompilátoru.
- `/bigobj`byla přidána možnost kompilátoru.
- `/clr:pure`, `/clr:safe`a `/clr:oldSyntax` byly přidány. (Později se v sadě Visual Studio 2015 zastarala a v sadě Visual Studio 2017 se odebere.)
- Zastaralé možnosti kompilátoru: mnoho možností kompilátoru bylo v této verzi zastaralé; další informace naleznete **v tématu Možnosti zastaralého kompilátoru.**
- Dvojité thunking `/clr` v kódu je snížena; další informace naleznete **v tématu Double Thunking (C++).**
- `/EH`(Model zpracování výjimek) nebo `/EHs` již nelze použít k zachycení výjimky, která je vyvolána s něčím jiným než throw; použití `/EHa`.
- `/errorReport`(Zpráva vnitřní chyby kompilátoru) kompilátor možnost byla přidána.
- `/favor`(Optimalizovat pro 64) byla přidána možnost kompilátoru.
- `/FA`, `/Fa` byla přidána možnost kompilátoru (Listing File).
- `/FC`(Úplná cesta souboru zdrojového kódu v diagnostice) byla přidána možnost kompilátoru.
- `/fp`(Zadejte chování s plovoucí desetinnou desetinnou tázkem) byla přidána možnost kompilátoru.
- `/G`(Optimalizovat pro procesor) Byla přidána možnost kompilátoru možností.
- `/G`(Optimalizovat pro procesor) Byla přidána možnost kompilátoru možností.
- `/G3`, `/G4` `/G5`, `/G6` `/G7`, `/GB` , a možnosti kompilátoru byly odebrány. Kompilátor nyní používá "blended model", který se pokouší vytvořit nejlepší výstupní soubor pro všechny architektury.
- `/Gf`byla odebrána. Místo `/GF` toho použijte (Odstranění duplicitních řetězců).
- `/GL`(Optimalizace celého programu) `/CLRHEADER`je nyní kompatibilní s .
- `/GR`je nyní ve výchozím nastavení zapnuta.
- `/GS`(Kontrola zabezpečení vyrovnávací paměti) nyní poskytuje ochranu zabezpečení pro ohrožené parametry ukazatele. `/GS`je nyní ve výchozím nastavení zapnuta. `/GS`nyní také pracuje na funkce zkompilované do MSIL s `/clr` (Common Language Runtime Compilation).
- `/homeparams`(Kopírovat parametry registru do zásobníku) byla přidána možnost kompilátoru.
- `/hotpatch`(Vytvořit hotpatchable image) kompilátor možnost byla přidána.
- Heuristiky vřádících funkcí byly aktualizovány; další informace naleznete **v inline**, **__inline**, **__forceinline** a **inline_depth**
- Bylo přidáno mnoho nových vnitřních funkcí a mnoho dříve nedokumentovaných vnitřních funkcí je nyní dokumentováno.
- Ve výchozím nastavení jakékoli volání na nové, které se nezdaří vyvolá výjimku.
- `/ML`a `/MLd` možnosti kompilátoru byly odebrány. Visual C++ již nepodporuje podporu knihovny CRT s jedním podprocesem a staticky propojeným.
- Kompilátor implementoval optimalizaci pojmenované návratové hodnoty, `/O1` `/O2` která je povolena `/Og` při kompilaci s `/Ox` , (Minimalizovat velikost, Maximalizovat rychlost), (globální optimalizace) a (Úplná optimalizace).
- `/Oa`možnost kompilátoru byla odebrána, ale bude tiše ignorována; pomocí `noalias` modifikátorů nebo `restrict__declspec` určete, jak kompilátor provádí aliasing.
- `/Op`kompilátoru byla odebrána. Místo `/fp` toho použijte (Zadejte chování s plovoucí desetinnou táhou).
- OpenMP je nyní podporován visual c++.
- `/openmp`(Povolit podporu OpenMP 2.0) byla přidána možnost kompilátoru.
- `/Ow`možnost kompilátoru byla odebrána, ale bude tiše ignorována. Pomocí `noalias` modifikátorů nebo `restrict__declspec` určete, jak kompilátor provádí aliasování.

### <a name="profile-guided-optimizations"></a>Optimalizace na základě profilu

- `/QI0f`byla odebrána.
- `/QIfdiv`byla odebrána.
- `/QIPF_B`(Errata pro B CPU Stepping) byla přidána možnost kompilátoru.
- `/QIPF_C`(Errata pro C cpu stepping) byla přidána možnost kompilátoru.
- `/QIPF_fr32`(Nepoužívejte horní 96 plovoucí desetinná žlábka možnost překladač byla přidána.
- `/QIPF_noPIC`(Generovat kód závislý na pozici) byla přidána možnost kompilátoru.
- `/QIPF_restrict_plabels`(Předpokládejme, že žádná funkce vytvořena za běhu) kompilátor možnost byla přidána.

### <a name="unicode-support-in-the-compiler-and-linker"></a>Podpora kódování Unicode v kompilátoru a linkeru

- `/vd`(Zakázat konstrukční posunutí) nyní umožňuje použít dynamic_cast Operátor na objekt, který je konstruován (/vd2)
- `/YX`kompilátor ubyl. Použijte `/Yc` (Vytvořit předkompilovaný `/Yu` soubor hlaviček) nebo (Použít předkompilovaný soubor záhlaví). Pokud odeberete `/YX` z konfigurace sestavení a nahradit je s ničím, může mít za následek rychlejší sestavení.
- `/Zc:forScope`je nyní ve výchozím nastavení zapnuta.
- `/Zc:wchar_t`je nyní ve výchozím nastavení zapnuta.
- `/Zd`kompilátor ubyl. Informace o ladění číslo řádku již nejsou podporovány. Použijte `/Zi` místo toho (viz **/Z7, /Zi, /ZI (Debug Information Format)** pro další informace).
- `/Zg`nyní platí pouze pro soubory zdrojového kódu Jazyka C a nikoli v souborech zdrojového kódu jazyka C++.
- `/Zx`(Ladění optimalizovaného kódu Itanium) byla přidána možnost kompilátoru.

### <a name="new-language-features"></a>Nové jazykové funkce

- Atribut je nyní zastaralé.
- `appdomain__declspec`modifikátor byl přidán.
- `__clrcall`byla přidána konvence volání.
- zastaralé (C++) **declspec** modifikátor nyní umožňuje zadat řetězec, který se zobrazí v době kompilace, kdy se uživatel pokusí o přístup k zastaralé třídy nebo funkce.
- **dynamic_cast** Operátor má změny.
- Nativní výčty nyní umožňují zadat základní typ.
- `jitintrinsicdeclspec`modifikátor byl přidán.
- `noaliasdeclspec`modifikátor byl přidán.
- `process__declspec`modifikátor byl přidán.
- **abstraktní**, **přepsat**a **zapečetěné** jsou platné pro nativní kompilace.
- **__restrict** klíčové slovo bylo přidáno.
- `restrictdeclspec`modifikátor byl přidán.
- **__thiscall** je nyní klíčové slovo.
- **klíčové** slovo __unaligned je nyní zdokumentováno.
- **volatile** (C++) aktualizoval chování s ohledem na optimalizace.

### <a name="new-preprocessor-features"></a>Nové funkce preprocesoru

- __CLR_VER přidáno předdefinované makro.
- Komentář (C/C++) pragma nyní `/MANIFESTDEPENDENCY` přijímá jako komentář propojovacího programu. Možnost exestr komentář je nyní zastaralé.
- `embedded_idl`(Směrnice) `#import` má nyní volitelný parametr.
- `fenv_access`Pragma
- `float_control`Pragma
- `fp_contract`Pragma
- Globální proměnné nebudou inicializovány v pořadí, ve které jsou deklarovány, pokud máte globální proměnné v oddílech pragma spravované, nespravované a nespravované. Toto je potenciální narušující změna, pokud je například inicializována nespravovanou globální proměnnou pomocí spravovaných globálních proměnných a je vyžadován plně vytvořený spravovaný objekt.
- Oddíly zadané s init_seg jsou nyní jen pro čtení a nejsou pro čtení a zápis jako v předchozích verzích.
- inline_depth výchozí hodnota je nyní 16. Výchozí hodnota 16 byla také v platnosti v jazyce Visual C++ .NET 2003.
- _INTEGRAL_MAX_BITS přidáno předdefinované makro, viz Předdefinovaná makra.
- _M_CEE, _M_CEE_PURE a _M_CEE_SAFE předdefinovaná makra, viz Předdefinovaná makra.
- _M_IX86_FP přidáno předdefinované makro.
- _M_X64 přidáno předdefinované makro.
- `make_public`Pragma
- `managed`, `unmanaged` pragma syntaxe `push` aktualizována (nyní má a `pop`)
- mscorlib.dll je nyní implicitně `#using` odkazováno `/clr` směrnicí ve všech kompilacích.
- _OPENMP přidáno předdefinované makro.
- optimalizace pragma byla aktualizována, a a w již nejsou platné parametry.
- no_registry byl přidán atribut importu.no_registry#import attribute has been added.
- `region`, `endregion` pragmas přidáno
- _VC_NODEFAULTLIB přidáno předdefinované makro.
- Variadická makra jsou nyní implementována.
- `vtordisp`je zastaralé a budou odebrány v budoucí verzi Visual C++.
- `warning` Pragma má nyní specifikátor potlačení.

### <a name="new-linker-features"></a>Nové funkce linkeru

- Moduly (výstupní soubory MSIL bez sestavení) jsou nyní povoleny jako vstup do propojovacího zařízení.
- `/ALLOWISOLATION`(Manifest Lookup) propojovací nástroj možnost byla přidána.
- `/ASSEMBLYRESOURCE`(Vložit spravovaný prostředek) byla aktualizována, aby nyní umožnila zadat název prostředku v sestavení a určit, že prostředek je soukromý v sestavení.
- `/CLRIMAGETYPE`(Zadejte typ obrázku CLR) propojovací ho diář.
- `/CLRSUPPORTLASTERROR`(Zachovat poslední kód chyby pro volání PInvoke) byla přidána možnost propojovacího programu.
- `/CLRTHREADATTRIBUTE`(Nastavit atribut clr podprocesu) propojovací ho disponitel.
- `/CLRUNMANAGEDCODECHECK`(Přidat možnost propojovacího programu "Přidat suppressUnmanagedCodeAttribute) byla přidána.
- `/ERRORREPORT`(Zpráva vnitřní propojovací ho protokolu) propojovací systém možnost byla přidána.
- `/EXETYPE`propojovací ho dispozičního nebo propojovacího. Propojovací program již nepodporuje vytváření ovladačů zařízení systému Windows 95 a Windows 98. K vytvoření těchto ovladačů zařízení použijte příslušnou ddk. Klíčové slovo EXETYPE již není platné pro definiční soubory modulu.
- `/FUNCTIONPADMIN`(Vytvořit hotpatchable image) propojovací zařízení možnost byla přidána.
- `/LTCG`Možnost linkeru je nyní podporována `/clr`u modulů kompilovaných pomocí aplikace . `/LTCG`byl také aktualizován, aby podporoval optimalizace s asistencí profilu.
- `/MANIFEST`(Vytvořit manifest sestavení vedle sebe) byla přidána možnost propojovacího zařízení.
- `/MANIFESTDEPENDENCY`(Zadat závislost ní manifest) byla přidána možnost propojovacího zařízení.
- `/MANIFESTFILE`(Name Manifest File) propojovací nástroj možnost byla přidána.
- `/MAPINFO:LINES`propojovací ho dispozičního nebo propojovacího.
- `/NXCOMPAT`(Kompatibilní s funkcemi zabránění spuštění dat) byla přidána možnost propojovacího zařízení.
- `/PGD`(Zadejte databázi pro optimalizace s asistencí profilu) propojovací ho disponitova možnost byla přidána.
- `/PROFILE`(Performance Tools Profiler) propojovací nástroj možnost byla přidána.
- `/SECTION`Možnost propojovacího zařízení (Zadat atributy oddílu) nyní podporuje negaci atributů a již nepodporuje atributy L nebo D (související s VxD).
- Podpora kódování Unicode v kompilátoru a linkeru
- `/VERBOSE`Možnost propojovacího programu (Zprávy průběhu tisku) nyní také přijímá i vi.
- `/VXD`propojovací ho dispozičního nebo propojovacího. Propojovací program již nepodporuje vytváření ovladačů zařízení systému Windows 95 a Windows 98. K vytvoření těchto ovladačů zařízení použijte příslušnou ddk. Klíčové slovo VXD již není platné pro definiční soubory modulu.
- `/WS`propojovací ho dispozičního nebo propojovacího. `/WS`Byl použit k úpravě obrázků určených pro systém Windows NT 4.0. IMAGECFG.exe -R název souboru `/WS`lze použít místo . Soubor IMAGECFG.exe naleznete na disku CD-ROM systému Windows NT 4.0 v části SUPPORT\DEBUG\I386\IMAGECFG. Exe.
- `/WX`(Považovat upozornění linkeru jako chyby) propojovacího programu možnost je nyní zdokumentována.

### <a name="new-linker-utility-features"></a>Nové funkce nástroje Linker

- `/ALLOWISOLATION`byla přidána možnost editbin
- Příkaz definition souboru modulu DESCRIPTION je odebrán. Propojovací nástroj již nepodporuje vytváření ovladačů virtuálních zařízení.
- `/ERRORREPORT`byla přidána možnost bscmake.exe, dumpbin.exe, editbin.exe a lib.exe.
- `/LTCG`lib možnost byla přidána.
- `/NXCOMPAT`byla přidána možnost editbin.
- `/RANGE`byla přidána možnost dumpbin.
- `/TLS`byla přidána možnost dumpbin.
- `/WS`editbin byla odebrána. `/WS`Byl použit k úpravě obrázků určených pro systém Windows NT 4.0. IMAGECFG.exe -R název souboru `/WS`lze použít místo . Soubor IMAGECFG.exe naleznete na disku CD-ROM systému Windows NT 4.0 v části SUPPORT\DEBUG\I386\IMAGECFG. Exe.
- /WX[:NO] lib možnost byla přidána.

### <a name="new-nmake-features"></a>Nové funkce NMAKE

- `/ERRORREPORT`byla přidána.
- `/G`byla přidána.
- Předdefinovaná pravidla byla aktualizována.
- Makro $(MAKE), které je dokumentováno v rekurzním makru, nyní poskytuje úplnou cestu k souboru nmake.exe.

### <a name="new-masm-features"></a>Nové funkce MASM

- MASM výrazy jsou nyní 64bitové hodnoty. V předchozích verzích byly výrazy MASM 32bitové hodnoty.
- Instrukce __asm int 3 nyní způsobí, že funkce, které mají být kompilovány nativní.
- ALIAS (MASM) je nyní zdokumentován.
- `/ERRORREPORT`ml.exe a ml64.exe možnost.
- . FPO je nyní zdokumentován.
- H2INC.exe nebude dodáván v jazyce Visual C++ 2005. Pokud potřebujete pokračovat v používání h2inc, použijte H2INC.exe z předchozí verze visual c++.
- byl přidán operátor IMAGEREL.
- operátor HIGH32.
- operátor LOW32.
- ml64.exe je verze MASM pro architekturu x64. To sestavuje x64 .asm soubory do x64 objektových souborů. Jazyk vřádíku není v kompilátoru x64 podporován. Pro funkci ml64.exe (x64) byly přidány následující direktivy MASM:
- .ALLOCSTACK
- .ENDPROLOG
- .PUSHFRAME
- .PUSHREG
- .SAVEREG
- .SAVEXMM128
- . SETFRAME Kromě toho byla směrnice PROC aktualizována syntaxí pouze x64.
- Byla přidána směrnice MMWORD.
- `/omf`(Ml.exe příkazový řádek `/c`možnost) nyní znamená . Ml.exe nepodporuje propojení objektů formátu OMF.
- Direktiva SEGMENT nyní podporuje další atributy.
- byl přidán operátor SECTIONREL.
- Byla přidána směrnice XMMWORD

### <a name="new-crt-features"></a>Nové funkce CRT

- Byly přidány zabezpečené verze několika funkcí. Tyto funkce zpracovávají chyby lepším způsobem a vynucují přísnější ovládací prvky vyrovnávacích pamětí, aby se zabránilo běžným chybám zabezpečení. Nové zabezpečené verze jsou označeny **příponou _s.**
- Stávající méně zabezpečené verze mnoha funkcí byly zastaralé. Chcete-li zakázat upozornění na vyřazení, definujte _CRT_SECURE_NO_WARNINGS.
- Mnoho existujících funkcí nyní ověřuje jejich parametry a vyvolá neplatný obslužnou rutinu parametru při předání neplatného parametru.
- Mnoho existujících `errno` funkcí nyní nastavit, kde tomu nebylo dříve.
- Typedef `errno_t` s type množeným číselným číselným číselným písmem byl přidán. `errno_t`se používá vždy, když se návratový `errno`typ nebo parametr funkce zabývá kódy chyb od aplikace . `errno_t`nahrazuje `errcode`.
- Funkce závislé na národním prostředí mají nyní verze, které berou národní prostředí jako parametr, nikoli jako aktuální národní prostředí. Tyto nové funkce mají **_l** příponu. Pro práci s objekty národního prostředí bylo přidáno několik nových funkcí. Mezi nové `_get_current_locale` `_create_locale` funkce `_free_locale`patří a .
- Byly přidány nové funkce pro podporu zamykání a odemykání popisovačů souborů.
- Rodina `_spawn` funkcí neobnoví errno na nulu na úspěch, jako tomu bylo v předchozích verzích.
- Verze `printf` rodiny funkcí, které umožňují určit pořadí, ve kterém jsou použity argumenty jsou k dispozici.
- Unicode je nyní podporovaný textový formát. Funkce `_open` podporuje atributy _O_TEXTW, _O_UTF8 a _O_UTF16. Funkce `fopen` podporuje metodu "ccs=ENCODING" pro určení formátu Unicode.
- Nová verze knihoven CRT integrovaných ve spravovaném kódu (MSIL) je nyní `/clr` k dispozici a používá se při kompilaci s možností (Common Language Runtime Compilation).
- _fileinfo byl odstraněn.
- Výchozí velikost `time_t` pro je nyní 64 bitů, `time_t` což rozšiřuje rozsah a několik časových funkcí na rok 3000.
- CRT nyní podporuje nastavení národního prostředí na základě vlákna. Funkce `_configthreadlocale` byla přidána pro podporu této funkce.
- Funkce `_statusfp2` `__control87_2` a byly přidány, aby umožnily přístup a řízení řídicího slova s plovoucí desetinnou tázkem na procesoru s plovoucí desetinnou tázkem x87 a SSE2.
- Funkce `_mkgmtime` `_mkgmtime64` a byly přidány k poskytování podpory pro převod časů (struct tm) na greenwichský střední čas (GMT).
- Byly provedeny `swprintf` změny `vswprintf` a lépe odpovídaly normě.
- Nový soubor záhlaví INTRIN. H, poskytuje prototypy pro některé vnitřní funkce.
- Funkce `fopen` má nyní atribut N.
- Funkce `_open` má nyní atribut _O_NOINHERIT.
- Funkce `atoi` nyní vrátí INT_MAX `errno` a nastaví eRANGE při přetečení. V předchozích verzích bylo chování přetečení nedefinováno.
- Řada `printf` funkcí podporuje šestnáctkový výstup s plovoucí desetinnou čárkou implementovaný podle standardu ANSI C99 pomocí specifikátorů typu formátu %a a %A.
- Rodina `printf` nyní podporuje předponu velikosti "ll".
- Funkce `_controlfp` byla optimalizována pro lepší výkon.
- Byly přidány ladicí verze některých funkcí.
- `_chgsignl` Přidáno `_cpysignl` a (dlouhé dvojité verze).
- Do `_locale_t` tabulky typu byl přidán typ.
- Přidáno `_countof` nové makro makro pro výpočet počtu prvků v poli.
- V každém tématu funkce byla přidána část o ekvivalentech rozhraní .NET Framework.
- Několik funkcí řetězce nyní mají možnost zkrácení řetězce spíše než selhání, pokud výstupní vyrovnávací paměti jsou příliš malé; viz **_TRUNCATE**.
- `_set_se_translator`Nyní vyžaduje použití `/EHa` možnosti kompilátoru.
- `fpos_t`je **__int64** nyní `/Za` __int64 pod (pro kód C) a při __STDC__ je nastavena ručně (pro kód C++). Bývala to **struktura.**
- _CRT_DISABLE_PERFCRIT_LOCKS může zlepšit výkon vstupně-va( vně jednovláknové programy.
- NÁZVY POSIX byly zastaralé ve prospěch konformních názvů ISO C++ (například použití `_getch` spíše než `getch`).
- Nové možnosti propojení .obj soubory jsou k dispozici pro čistý režim
- `_recalloc`kombinuje vlastnosti `realloc` `calloc`a .

## <a name="whats-new-for-c-in-visual-studio-2003"></a>Co je nového pro C++ v sadě Visual Studio 2003

### <a name="compiler"></a>Kompilátoru

- Informace o tom, jak spustit spravované rozšíření pro aplikaci C++ sestavené s kompilátorem aktuální verze na předchozí verzi runtime.
- Spravovaná rozšíření pro často kladené otázky jazyka C++.
- Byl přidán návod, který ukazuje, jak přenést existující nativní aplikaci pro použití spravovaných rozšíření pro C++: Návod: Porting existující nativní aplikace jazyka C++ pro vzájemné provozování komponent rozhraní .NET Framework Components.
- Nyní můžete vytvořit delegáta na metodu typu hodnoty.
- Shoda kompilátoru se standardem C++ byla výrazně vylepšena pro visual c++ .NET 2003.
- `/arch`je přidána možnost kompilátoru.
- `/Gf`je zastaralé a budou odebrány v další verzi visual c++.
- `/G7`je přidána možnost kompilátoru.
- Možnost `/GS` kompilátoru byla vylepšena tak, aby pomohla chránit místní proměnné před přímým přetečením vyrovnávací paměti.
- Možnost `/noBool` kompilátoru byla odebrána. Kompilátor nyní umožňuje **bool** se zobrazí pouze jako klíčové slovo (a ne identifikátor) v souboru zdrojového kódu Jazyka C++.
- Dlouhý **dlouhý** typ je nyní k dispozici jako **typedef** **__int64** Všimněte si, že ještě není podpora pro **dlouhou dobu** v CRT.
- Možnost `/Zm` kompilátoru nyní určuje limit přidělení paměti předkompilované hlavičky.
- _InterlockedCompareExchange vnitřní nyní zdokumentovány.
- _InterlockedDecrement vnitřní nyní zdokumentovány.
- _InterlockedExchange vnitřní nyní zdokumentovány.
- _InterlockedExchangeAdd vnitřní nyní zdokumentovány.
- _InterlockedIncrement vnitřní nyní zdokumentovány.
- _ReadWriteBarrier přidáno do vnitřního.

### <a name="attributes"></a>Atributy

- `implements`atribut je nyní zdokumentován.

### <a name="linker-features"></a>Funkce linkeru

Byly přidány následující přepínače linkerů:

- /CHYBA SESTAVENÍ
- /ASSEMBLYLINKRESOURCE
- Delaysign
- /SOUBOR KLÁVES
- /KEYCONTAINER
- /SAFESEH

### <a name="masm"></a>MASM

Tá. byla přidána `/safeseh` směrnice SAFESEH a možnost ml.exe.

## <a name="see-also"></a>Viz také

[Průvodce přenosem a upgradem Visual C++](visual-cpp-porting-and-upgrading-guide.md)
