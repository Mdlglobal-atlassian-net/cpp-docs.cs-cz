---
title: Vizuál C++ &#39;s novými 2003 až 2015
ms.date: 07/02/2019
ms.assetid: c4afde6f-3d75-40bf-986f-be57e3818e26
ms.openlocfilehash: 6a3db2c9af2bcd9201f696756053cedb0788571a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510310"
---
# <a name="visual-c-what39s-new-2003-through-2015"></a>Vizuál C++ &#39;s novými 2003 až 2015

Tato stránka shromáždí všechny stránky "Co je nového" pro všechny verze vizuálu C++ ze sady visual Studio 2015 zpět do 2003. Tyto informace se poskytují jako pohodlí pro případ, že může být užitečné při upgradu z dřívějších verzí sady Visual Studio.

> [!NOTE]
> Informace o aktuální verzi sady Visual Studio naleznete v tématu [co je nového pro vizuál C++ v aplikaci Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md) a [vylepšení shody v aplikaci C++ Visual Studio](../overview/cpp-conformance-improvements.md).

## <a name="whats-new-for-c-in-visual-studio-2015"></a>Co je nového C++ v aplikaci Visual Studio 2015

V aplikaci Visual Studio 2015 a novějších verzích může průběžná vylepšení shody kompilátoru někdy změnit způsob, jakým kompilátor rozumí vašemu existujícímu zdrojovému kódu. V takovém případě se můžete setkat s novými nebo různými chybami v průběhu sestavení, nebo dokonce i rozdíly v kódu, které dříve vytvořili a zdály se pracovat správně.

Naštěstí tyto rozdíly mají malý nebo žádný vliv na většinu vašeho zdrojového kódu a pokud je pro vyřešení těchto rozdílů nutný zdrojový kód nebo jiné změny, opravy jsou obvykle malé a rovné předem. Zahrnuli jsme spoustu příkladů dříve přijatelného zdrojového kódu, který může být potřeba změnit *(před)* , a opravy, které je třeba opravit *(po)* .

I když tyto rozdíly mohou ovlivnit váš zdrojový kód nebo jiné artefakty sestavení, nemají vliv na binární kompatibilitu mezi aktualizacemi C++ vizuálních verzí. U složitějších typů změn může zásadní *Změna* ovlivnit binární kompatibilitu, ale k těmto typům binárních rozbalení dochází pouze mezi hlavními verzemi vizuálu C++. Například mezi Visual C++ 2013 a Visual C++ 2015. Informace o nejnovějších změnách, ke kterým došlo mezi Visual C++ 2013 a Visual C++ 2015, najdete v tématu [vizuální C++ Změna historie 2003 – 2015](../porting/visual-cpp-change-history-2003-2015.md).

- [Vylepšení shody v aplikaci Visual Studio 2015](#VS_RTM)

- [Vylepšení shody v aktualizaci Visual Studio 2015 Update 1](#VS_Update1)

- [Vylepšení shody v aktualizaci Visual Studio 2015 Update 2](#VS_Update2)

- [Vylepšení shody v aktualizaci Visual Studio 2015 Update 3](#VS_Update3)

### <a name="VS_RTM"></a>Vylepšení shody v aplikaci Visual Studio 2015

- **/Zc: forScope-Option**

   Možnost `/Zc:forScope-` kompilátoru je zastaralá a v budoucí verzi se odebere.

   ```output
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release
   ```

   Možnost byla obvykle použita, aby povolovala nestandardní kód, který používá proměnné smyčky za bodem, kde, podle standardu, by měl být mimo rozsah. Bylo nutné pouze v případě, že kompilujete s `/Za` možností, od bez `/Za`použití proměnné for Loop po konci smyčky, která je vždy povolena. Pokud si nejste jisti dodržováním standardů (například pokud váš kód není určen pro přenos do jiných kompilátorů), můžete `/Za` vypnout možnost (nebo nastavit vlastnost **Zakázat jazykové rozšíření** na hodnotu **ne**). Pokud se zajímáte o zápis přenosného kódu kompatibilního s normami, měli byste přepsat kód tak, aby odpovídal standardu přesunutím deklarace těchto proměnných do bodu mimo smyčku.

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

- **ZG – – možnost kompilátoru**

   Možnost `/Zg` kompilátoru (generovat prototypy funkce) už není dostupná. Tato možnost kompilátoru byla dřív zastaralá.

- Z příkazového řádku pomocí MSTest. exe C++už nemůžete spouštět testy jednotek pomocí/CLI. Místo toho použijte VSTest. Console. exe.

- **mutable – klíčové slovo**

   Specifikátor třídy měnitelného úložiště již není povolen v místech, kde byla dříve zkompilována bez chyby. Nyní kompilátor poskytuje chybu C2071 (neplatná třída úložiště). Podle standardu může být proměnlivý specifikátor použit pouze pro názvy datových členů třídy a nelze jej použít na názvy deklarované jako const nebo static a nelze jej použít pro členy odkazu.

   Zvažte například následující kód:

   ```cpp
    struct S {
        mutable int &r;
    };
   ```

   Předchozí verze kompilátoru Microsoft C++ to přijaly, ale teď kompilátor poskytuje tuto chybu:

   ```Output
    error C2071: 'S::r': illegal storage class
   ```

   Chybu opravíte tak, že jednoduše odeberete redundantní klíčové slovo **mutable** .

- **char_16_t a char32_t**

   V definici TypeDef už nemůžete používat `char16_t` nebo `char32_t` jako aliasy, protože tyto typy se teď považují za předdefinované. Bylo běžné, že uživatelé a autoři knihoven mají definovat `char16_t` a `char32_t` jako aliasy `uint16_t` a `uint32_t`v uvedeném pořadí.

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

   Chcete-li aktualizovat kód, odeberte deklarace **typedef** a přejmenujte všechny ostatní identifikátory, které s těmito názvy kolidují.

- **Parametry šablony bez typu**

   Určitý kód, který zahrnuje parametry šablony bez typu, je nyní správně zkontrolován na kompatibilitu typu při zadání explicitních argumentů šablony. Například následující kód byl zkompilován bez chyb v předchozích verzích vizuálu C++.

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

   Aktuální kompilátor správně poskytuje chybu, protože typ parametru šablony neodpovídá argumentu šablony (parametr je ukazatel na konstantní člen, ale funkce f není const):

   ```Output
    error C2893: Failed to specialize function template 'void S2::f(void)'note: With the following template arguments:note: 'C=S1'note: 'Function=S1::f'
   ```

   Chcete-li vyřešit tuto chybu ve vašem kódu, ujistěte se, že typ argumentu šablony, který použijete, odpovídá deklarovanému typu parametru šablony.

- **__declspec(align)**

   Kompilátor již nepřijímá `__declspec(align)` funkce. To se vždycky ignoruje, ale teď vytvoří chybu kompilátoru.

   ```cpp
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations
   ```

   Chcete-li tento problém vyřešit `__declspec(align)` , odeberte z deklarace funkce. Vzhledem k tomu, že nedošlo k žádnému vlivu, odebrání nemění nic.

- **Zpracování výjimek**

   Zpracovávání výjimek je několik změn. Nejprve objekty výjimky musí být buď kopírovací, nebo pohyblivý. Následující kód byl zkompilován v Visual Studio 2013, ale není zkompilován v aplikaci Visual Studio 2015:

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

   Problémem je, že kopírovací konstruktor je privátní, takže objekt nelze zkopírovat, protože se děje v normálním průběhu zpracování výjimky. Totéž platí, pokud je kopírovací konstruktor deklarovaný jako **explicitní**.

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

   Chcete-li aktualizovat kód, ujistěte se, že kopírovací konstruktor pro objekt výjimky je veřejný a není označen jako **explicitní**.

   Zachycení výjimky podle hodnoty také vyžaduje zkopírování objektu výjimky. Následující kód byl zkompilován v Visual Studio 2013, ale není zkompilován v aplikaci Visual Studio 2015:

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

   Tento problém můžete vyřešit tak, že změníte typ parametru pro **catch** na odkaz.

   ```cpp
    catch(D& d)
    {
    }
   ```

- **Řetězcové literály následované makry**

   Kompilátor teď podporuje uživatelsky definované literály. V důsledku toho jsou řetězcové literály následované makry bez použití mezer interpretovány jako uživatelsky definované literály, což může způsobit chyby nebo neočekávané výsledky. Například v předchozích kompilátorech byl následující kód úspěšně zkompilován:

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

   Kompilátor tuto hodnotu interpretoval jako řetězcový literál "Hello" následovaný makrem, které rozbalí "tam" a pak dva řetězcové literály byly zřetězeny do jednoho. V aplikaci Visual Studio 2015 Kompilátor interpretuje tuto hodnotu jako literál definovaný uživatelem, ale vzhledem k tomu, že není definována žádná vyhovující uživatelem definovaná Literálová _X, obsahuje chybu.

   ```cpp
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found
    note: Did you forget a space between the string literal and the prefix of the following string literal?

   ```

   Chcete-li tento problém vyřešit, přidejte mezeru mezi řetězcový literál a makro.

- **Sousedící řetězcové literály**

   Podobně jako v předchozím případě v důsledku souvisejících změn v analýze řetězců, sousedících řetězcových literálů (buď pro řetězce s velkým nebo úzkým znakem ") bez mezer byly interpretovány jako jeden zřetězený řetězec v C++předchozích verzích Visaul. V aplikaci Visual Studio 2015 je nyní nutné přidat prázdné znaky mezi dva řetězce. Například následující kód musí být změněn:

   ```cpp
    char * str = "abc""def";
   ```

   Jednoduše přidejte mezeru mezi dva řetězce.

   ```cpp
    char * str = "abc" "def";
   ```

- **Umístění – nové a odstranit**

   Byl proveden pokus o změnu operátoru **Delete** , aby byl do souladu s c++ 14 standardem. Podrobnosti o změně standardů najdete v [ C++ ](https://isocpp.org/files/papers/n3778.html)podrobnostech o navracení velikosti. Změny přidají formu globálního operátoru **Delete** , který přijímá parametr velikosti. Zásadní změna znamená, že pokud jste předtím používali operátor **Delete** se stejnou signaturou (aby odpovídala **umístění New** operator), obdržíte chybu kompilátoru (C2956, ke které dojde v místě, kde je **nová umístění.** se používá, protože je pozice v kódu, kde se kompilátor pokusí identifikovat příslušný odpovídající operátor **Delete** .

   Funkce `void operator delete(void *, size_t)` byla umístění operátoru **Delete** odpovídajícím funkci `void * operator new(size_t, size_t)` **umístění New** v c++ 11. Při dealokaci velikosti C++ 14 je tato funkce **odstranění** nyní *běžnou funkcí zrušení přidělení* (globální operátor **Delete** ). Standardně se vyžaduje, aby při použití **umístění nový** vyhledala odpovídající funkci **Delete** a vyhledala obvyklou funkci zrušení přidělení, program je nesprávně vytvořen.

   Předpokládejme například, že váš kód definuje **umístění nové** a **odstranění umístění**:

   ```cpp
    void * operator new(std::size_t, std::size_t);
    void operator delete(void*, std::size_t) noexcept;
   ```

   K tomuto problému dochází z důvodu shody v signaturách funkcí mezi uživatelem definovaným operátorem pro **odstranění umístění** a novým operátorem **odstranění** globální velikosti. Zvažte, zda můžete použít jiný typ než `size_t` pro jakékoli nové a **Odstranit** operátory pro **umístění** .  `size_t` Všimněte si, že typ **typedef** je závislý na kompilátoru; je **definice** typu **unsigned int** v vizuálu C++. Dobrým řešením je použít Výčtový typ, jako je například:

   ```cpp
    enum class my_type : size_t {};
   ```

   Pak změňte definici umístění **New** a **Delete** , abyste tento typ používali jako druhý `size_t`argument místo. Budete také muset aktualizovat volání do **umístění New** pro předání nového typu (například pomocí `static_cast<my_type>` funkce pro převod z celočíselné hodnoty) a aktualizace definice **New** a **Delete** pro přetypování zpět na celočíselný typ. Pro tuto chybu nemusíte používat **výčet** . může fungovat i typ třídy `size_t` se členem.

   Alternativním řešením je, že možná budete moct zcela úplně odstranit **nové umístění** . Pokud váš kód používá **nové umístění** k implementaci fondu paměti, kde argument umístění je velikost objektu, který je přidělen nebo smazán, může být funkce navracení velikosti velikosti vhodná k nahrazení vlastního kódu vlastní fond paměti a můžete se zbavit funkce umístění a stačí použít vlastní operátor **odstranění** dvou argumentů namísto funkcí umístění.

   Pokud nechcete kód hned aktualizovat, můžete se vrátit k původnímu chování pomocí možnosti `/Zc:sizedDealloc-`kompilátoru. Použijete-li tuto možnost, funkce **odstranění** dvou argumentů neexistují a nezpůsobí konflikt s operátorem **odstranění umístění** .

- **Sjednocení datových členů**

   Datové členy sjednocení již nemohou mít odkazové typy. Následující kód byl úspěšně zkompilován v Visual Studio 2013, ale vyvolá chybu v aplikaci Visual Studio 2015.

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

   Chcete-li tento problém vyřešit, změňte typ odkazu buď na ukazatel, nebo na hodnotu. Změna typu na ukazatel vyžaduje změny v kódu, který používá pole Union. Změna kódu na hodnotu by změnila data uložená ve sjednocení, která mají vliv na ostatní pole, protože pole v typech sjednocení sdílejí stejnou paměť. V závislosti na velikosti hodnoty může také dojít ke změně velikosti sjednocení.

- **Anonymní sjednocení**

   jsou nyní více vyhovující standardu. Předchozí verze kompilátoru vygenerovala explicitní konstruktor a destruktor pro anonymní sjednocení. Ty jsou odstraněny v aplikaci Visual Studio 2015.

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

   Předchozí kód generuje následující chybu v aplikaci Visual Studio 2015:

   ```cpp
    error C2280: '<unnamed-type-u>::<unnamed-type-u>(void)': attempting to reference a deleted function
    note: compiler has generated '<unnamed-type-u>::<unnamed-type-u>' here
   ```

   Chcete-li vyřešit tento problém, zadejte vlastní definice konstruktoru nebo destruktoru.

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

- **Sjednocení s anonymními strukturami**

   Aby bylo možné v souladu se standardem, bylo chování modulu runtime změněno pro členy anonymních struktur ve sjednoceních. Konstruktor pro členy anonymní struktury ve sjednocení již není implicitně volán při vytvoření takového sjednocení. Také destruktor pro členy anonymní struktury ve sjednocení již není implicitně volán, když se sjednocení dostanou mimo rozsah. Vezměte v úvahu následující kód, ve kterém sjednocení U obsahuje anonymní strukturu, která obsahuje člena, který je pojmenovaný strukturou S destruktorem.

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

   V Visual Studio 2013 konstruktor pro S je volán při vytvoření sjednocení a destruktor pro S je volán, když je vyčištěn zásobník funkce f. Ale v aplikaci Visual Studio 2015 nejsou volány konstruktor a destruktor. Kompilátor poskytuje upozornění na tuto změnu chování.

   ```Output
    warning C4587: 'U::s': behavior change: constructor is no longer implicitly calledwarning C4588: 'U::s': behavior change: destructor is no longer implicitly called
   ```

   Chcete-li obnovit původní chování, zadejte název anonymní struktury. Běhové chování neanonymních struktur je stejné, bez ohledu na verzi kompilátoru.

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

   Případně můžete zkusit přesunout konstruktor a kód destruktoru do nových funkcí a přidat volání těchto funkcí z konstruktoru a destruktoru pro sjednocení.

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

- **Řešení šablony**

   Byly provedeny změny překladu názvů pro šablony. V C++systému se při zvažování kandidátů na rozlišení názvu může jednat o případ, že jeden nebo více názvů, které se považují za potenciální shody, vytvoří neplatnou instanci šablony. Tyto neplatné instance běžně nezpůsobují chyby kompilátoru – princip, který se označuje jako SFINAE (Chyba při nahrazování není chyba).

   Pokud nyní SFINAE vyžaduje, aby kompilátor vytvořil instanci specializace šablony třídy, pak všechny chyby, ke kterým dojde během tohoto procesu, jsou chyby kompilátoru. V předchozích verzích kompilátor by tyto chyby ignoroval. Zvažte například následující kód:

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

   Pokud kompilujete s aktuálním kompilátorem, zobrazí se následující chyba:

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

   Důvodem je, že v bodě prvního vyvolání třídy is_base_of není ještě definován.

   V takovém případě oprava nepoužije tyto vlastnosti typu, dokud není definována třída. Pokud přesunete definice B a D na začátek souboru kódu, dojde k vyřešení chyby. Pokud jsou definice v hlavičkových souborech, zkontrolujte pořadí příkazů include pro hlavičkové soubory, abyste se ujistili, že všechny definice tříd jsou kompilovány před použitím problematických šablon.

- **Kopírovací konstruktory**

   V Visual Studio 2013 i Visual Studio 2015 kompilátor generuje kopírovací konstruktor pro třídu, pokud tato třída má uživatelsky definovaný konstruktor přesunu, ale neexistuje uživatelsky definovaný kopírovací konstruktor. V Dev14 je tento implicitně vygenerovaný kopírovací konstruktor označený také "= Delete".

### <a name="VS_Update1"></a>Vylepšení shody v aktualizaci Visual Studio 2015 Update 1

- **Soukromé virtuální základní třídy a nepřímá dědičnost**

   Předchozí verze kompilátoru povolily odvozenou třídu pro volání členských funkcí svých *nepřímo odvozených* `private virtual` základních tříd. Toto staré chování bylo nesprávné a nevyhovuje C++ standardu. Kompilátor již nepřijímá kód napsaný tímto způsobem a v důsledku toho vydává chybu kompilátoru C2280.

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

  \-ani

   ```cpp
    class base;  // as above

    class middle: private virtual base {};
    class top: public virtual middle, private virtual bottom {};

    void destroy(top *p)
    {
        delete p;
    }
   ```

- **Přetížený operátor New a operátor delete**

   Předchozí verze kompilátoru povolují nečlenský **operátor New** a nečlenský **operátor delete** , aby byly deklarované jako statické a deklarované v oborech názvů kromě globálního oboru názvů.  Toto staré chování vytvořilo riziko, že by program nevolal implementaci operátoru **New** nebo **Delete** , kterou programátor zamýšlel, a výsledkem je tiché chybné chování za běhu. Kompilátor již nepřijímá kód napsaný tímto způsobem a namísto toho vydá chybu kompilátoru C2323.

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

   Kromě toho, i když kompilátor neposkytuje konkrétní diagnostiku, je vložený operátor New považován za nesprávně vytvořený.

- **Volání operátoru ' *Type*() ' (uživatelem definovaný převod) pro typy bez třídy** , které jsou předchozími verzemi *typu*operátor () povoleno, aby byly volány na typy bez třídy, zatímco jsou tiše ignorovány. Toto staré chování vytvořilo riziko tichého chybného generování kódu, což vede k nepředvídatelnému chování za běhu. Kompilátor již nepřijímá kód napsaný tímto způsobem a namísto toho vydá chybu kompilátoru C2228.

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

- **Redundantní TypeName v propracované specifikátorech typu**  Předchozí verze kompilátoru povolily **TypeName** ve vypracovaném specifikátorech typu; kód psaný tímto způsobem je sémanticky nesprávným. Kompilátor již nepřijímá kód napsaný tímto způsobem a namísto toho vydá chybu kompilátoru C3406.

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

- **Typ srážek polí ze seznamu inicializátorů**  Předchozí verze kompilátoru nepodporovaly typ srážek polí ze seznamu inicializátorů. Kompilátor teď podporuje tento typ odvození typu, a proto volání šablon funkcí pomocí seznamů inicializátorů teď může být dvojznačné nebo jiné přetížení může být zvolené než v předchozích verzích kompilátoru. Aby bylo možné tyto problémy vyřešit, musí nyní program explicitně určit přetížení, které programátor zamýšlel.

   V případě, že toto nové chování způsobí, že řešení přetížení považuje další kandidáta, který je stejně vhodný jako historický kandidát, volání se nejednoznační a kompilátor vyvolá chybu kompilátoru C2668.

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

   Když toto nové chování způsobí, že řešení přetížení považuje další kandidáta, která je lepší, než historická kandidát, volání se jednoznačně vyřeší na novém kandidáta, což způsobí změnu v chování programu, která je pravděpodobně jiná než zamýšlený programátor.

   Příklad 2: Změna v řešení přetížení (před)

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

   Příklad 2: Změna v řešení přetížení (po)

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

   Předchozí verze kompilátoru odebrala dříve existující upozornění související s příkazy **Switch** ; Tato upozornění se teď obnovila. Kompilátor nyní vydá obnovená upozornění a upozornění související s konkrétními případy (včetně výchozího případu) jsou nyní vydány na řádku obsahujícím problematický případ, nikoli na posledním řádku příkazu switch. V důsledku toho, že teď tato upozornění vydávají na různých řádcích než v minulosti, už se upozornění, která `#pragma warning(disable:####)` jste předtím potlačili, už nebudou potlačit. Chcete-li potlačit tato upozornění jako zamýšlená, může být nutné `#pragma warning(disable:####)` přesunout direktivu na řádek nad první potenciálně problematický případ. V následujícím seznamu jsou obnovená upozornění.

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

   Příklad C4063 (za)

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

   Příklady dalších obnovených upozornění jsou uvedeny v dokumentaci.

- **#include: použití specifikátoru nadřazeného adresáře '.. ' v cestě** (týká `/Wall` `/WX`se jenom)

   Předchozí verze kompilátoru nerozpoznaly použití specifikátoru nadřazeného adresáře... v cestě `#include` k direktivám. Kód psaný tímto způsobem je obvykle určen pro zahrnutí hlaviček, které existují mimo projekt, pomocí nesprávného použití relativních cest projektu. Toto staré chování vytvořilo riziko, že program může být zkompilován zahrnutím jiného zdrojového souboru, než je programátor zamýšlen, nebo zda tyto relativní cesty nebudou přenosné do jiných prostředí pro sestavení. Kompilátor nyní detekuje a upozorňuje programátora kódu napsaného tímto způsobem a vydá volitelné C4464 upozornění kompilátoru, pokud je povoleno.

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

   I když kompilátor neposkytuje konkrétní diagnostiku, doporučujeme také, aby se pro určení adresáře include projektu použil specifikátor nadřazeného adresáře "..".

- **#pragma optimize () rozšiřuje poslední konec hlavičkového souboru** . (týká `/Wall` `/WX`se jenom)

   Předchozí verze kompilátoru nerozpoznaly změny nastavení příznaku optimalizace, které řídí hlavičkový soubor zahrnutý do jednotky překladu. Kompilátor nyní detekuje a upozorňuje programátora kódu napsaného tímto způsobem a vydá volitelné upozornění kompilátoru C4426 v umístění problematické `#include`, pokud je povoleno. Toto upozornění je vystaveno pouze v případě, že změny jsou v konfliktu s příznaky optimalizace nastavenými argumenty příkazového řádku pro kompilátor.

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

- **Neshoda #pragma upozornění (push)** a **upozornění #pragma (pop)** (týká `/Wall` `/WX`se jenom)

   Předchozí verze kompilátoru nerozpoznaly `#pragma warning(push)` změny stavu spárované se `#pragma warning(pop)` změnami stavu v jiném zdrojovém souboru, což je zřídka zamýšlené. Toto staré chování vytvořilo riziko, že program bude zkompilován s jinou sadou upozornění, než je zamýšlený programátor, což může vést k tichému chybnému chování za běhu. Kompilátor nyní detekuje a upozorňuje programátora kódu napsaného tímto způsobem a vydá volitelné upozornění kompilátoru C5031 v umístění odpovídajícího `#pragma warning(pop)`, pokud je povoleno. Toto upozornění obsahuje poznámku odkazující na umístění odpovídající `#pragma warning(push)`.

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

   I když je neobvyklá, kód napsaný tímto způsobem je někdy úmyslné. Kód psaný tímto způsobem je citlivý na změny v `#include` pořadí. Pokud je to možné, doporučujeme, aby soubory zdrojového kódu spravovaly stav upozornění v samostatném způsobu.

- **Upozornění na neshodné #pragma (push)** (týká `/Wall` `/WX`se jenom)

   Předchozí verze kompilátoru nezjistily neshodné `#pragma warning(push)` změny stavu na konci jednotky překladu. Kompilátor nyní detekuje a upozorňuje programátora kódu napsaného tímto způsobem a vydá volitelné upozornění kompilátoru C5032 v umístění nespárované `#pragma warning(push)`, pokud je povoleno. Toto upozornění je vystaveno pouze v případě, že v jednotce překladu nejsou žádné chyby kompilace.

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

- **Další upozornění můžou být vystavena v důsledku vylepšení sledování stavu upozornění #pragma**

   Předchozí verze sledovaných `#pragma warning` stavů kompilátoru nedostatečně dobře vydávaly všechna zamýšlená upozornění. Toto chování vytvořilo riziko, že určitá upozornění budou efektivně potlačena v jiných případech, než je programátor zamýšlen. Kompilátor teď sleduje `#pragma warning` stav robustnější – obzvláště v souvislosti se `#pragma warning` změnami stavu uvnitř šablon – a volitelně vydá nová upozornění C5031 a C5032, která mají pomáhat programátorovi najít nezamýšlené použití `#pragma warning(push)` a .`#pragma warning(pop)`

   V důsledku vylepšeného `#pragma warning` sledování změn stavu se teď můžou vydávat upozornění, která se dřív nesprávně potlačila, nebo upozornění související s dříve nezjištěnými problémy.

- **Vylepšená identifikace nedosažitelného kódu**

   C++Změny knihovny Standard a vylepšená možnost volání vložených funkcí v předchozích verzích kompilátoru může povolit, aby kompilátor prokázal, že určitý kód je nyní nedosažitelný. Toto nové chování může mít za následek nové a více často vydaných instancí upozornění C4720.

   ```Output
    warning C4720: unreachable code
   ```

   V mnoha případech může být toto upozornění vystaveno pouze při kompilaci s povolenými optimalizacemi, protože optimalizace mohou vložit více volání funkce, eliminovat redundantní kód nebo jinak určit, že určitý kód je nedosažitelný. Zjistili jsme, že v blocích **try/catch** se často objevily nové instance varovných C4720, zejména ve vztahu k použití [std:: Find](assetId:///std::find?qualifyHint=False&autoUpgrade=True).

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

### <a name="VS_Update2"></a>Vylepšení shody v aktualizaci Visual Studio 2015 Update 2

- **Další upozornění a chyby mohou být vydány v důsledku částečné podpory pro Expression SFINAE**

   Předchozí verze kompilátoru neanalyzovaly některé druhy výrazů uvnitř specifikátorů **decltype** z důvodu nedostatku podpory pro Expression SFINAE. Toto staré chování bylo nesprávné a nevyhovuje C++ standardu. Kompilátor nyní analyzuje tyto výrazy a má částečnou podporu pro Expression SFINAE z důvodu probíhajících vylepšení dodržování shody. V důsledku toho kompilátor nyní vydá upozornění a chyby nalezené ve výrazech, které předchozí verze kompilátoru neanalyzovaly.

   Když toto nové chování analyzuje výraz **decltype** , který obsahuje typ, který ještě není deklarovaný, kompilátor při výsledku vyvolá chybu kompilátoru C2039.

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

   Příklad 1 (za)

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

   Když toto nové chování analyzuje výraz **decltype** , který postrádá nezbytné použití klíčového slova **TypeName** k určení, že název závislého typu je typ, kompilátor vydává upozornění kompilátoru C4346 spolu s chybou kompilátoru C2923.

   ```Output
    warning C4346: 'S2<T>::Type': dependent name is not a type
   ```

   ```Output
    error C2923: 's1': 'S2<T>::Type' is not a valid template type argument for parameter 'T'
   ```

   Příklad 2: závislý název není typu (před).

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

- `volatile`**členské proměnné zabraňují implicitně definovaným konstruktorům a operátorům přiřazení** . Předchozí verze kompilátoru povolily třídu, která má nestálé členské proměnné, aby měly výchozí konstruktory Copy/Move a automaticky vygenerovaly výchozí operátory kopírování a přesunu. Toto staré chování bylo nesprávné a nevyhovuje C++ standardu. Kompilátor nyní považuje třídu, která má nestálé členské proměnné, aby měly operátory a přiřazení bez triviálního konstrukce, které brání automatickému generování výchozích implementací těchto operátorů. Když je taková třída členem sjednocení (nebo anonymního sjednocení uvnitř třídy), konstruktory Copy/Move a operátory přiřazení kopírování a přesunu (nebo třídy obsahující unonymous sjednocení) se implicitně definují jako odstraněné. Pokus o sestavení nebo zkopírování sjednocení (nebo třídy obsahující anonymní sjednocení) bez explicitního definování je chyba a kompilátor vyvolá chybu kompilátoru C2280, která je výsledkem.

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

   Předchozí verze Visual C++ 2015 povolily statickým členským funkcím kvalifikátory cv. K tomuto chování dochází z důvodu regrese v C++ jazyce Visual 2015 C++ a Visual 2015 Update 1; Visual C++ 2013 a předchozí verze kódu pro C++ vizuální odmítnutí zapsané tímto způsobem. Chování Visual C++ 2015 a Visual C++ 2015 Update 1 je nesprávné a nevyhovuje C++ standardu.  Visual Studio 2015 Update 2 odmítne kód napsaný tímto způsobem a místo toho vydá chybu kompilátoru C2511.

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

- **Dopředná deklarace výčtu není v kódu WinRT povolená** . (týká `/ZW` se jenom)

   Kód kompilovaný pro prostředí Windows Runtime (WinRT) neumožňuje dopředně deklarovat **výčtové** typy, podobně jako při kompilaci C++ spravovaného kódu pro rozhraní .NET `/clr` Framework pomocí přepínače kompilátoru. Díky tomuto chování je zajištěno, že velikost výčtu je vždy známá a lze jej správně promítnout do systému typů WinRT. Kompilátor odmítne kód napsaný tímto způsobem a vydá chybu kompilátoru C2599 spolu s chybou kompilátoru C3197.

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

- **Přetížený operátor New a operátor delete se nedá deklarovat jako inline** . (Úroveň 1 (`/W1`) při výchozím nastavení)

   Předchozí verze kompilátoru nevydá upozornění, když je nečlenský **operátor New** a funkce **Delete operátora** jsou deklarovány jako inline. Kód napsaný tímto způsobem je nesprávně vytvořen (bez diagnostiky není vyžadován) a může způsobit problémy s pamětí způsobenými neodpovídajícími operátory New a Delete (zejména při použití společně s velikostí dealokace), které mohou být obtížné diagnostikovat. Kompilátor nyní vydává upozornění kompilátoru C4595, aby mohl identifikovat kód napsaný tímto způsobem.

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

   Oprava kódu, který je napsán tímto způsobem, může vyžadovat, aby definice operátora byly přesunuty ze souboru hlaviček a do odpovídajícího zdrojového souboru.

### <a name="VS_Update3"></a>Vylepšení shody v aktualizaci Visual Studio 2015 Update 3

- **std:: is_convertable nyní detekuje samostatné přiřazení**  (standardní knihovna) Předchozí verze `std::is_convertable` typu vlastnost nerozpoznaly správně vlastní přiřazení typu třídy, pokud je jeho kopírovací konstruktor odstraněný nebo soukromý. Nyní je správně nastaven na **hodnotu false** při použití na typ třídy s odstraněným nebo soukromým kopírovacím konstruktorem. `std::is_convertable<>::value`

   K této změně není přidružená žádná Diagnostika kompilátoru.

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

   V předchozích verzích vizuálu C++jsou statické kontrolní výrazy ve spodní části tohoto příkladu Pass, protože `std::is_convertable<>::value` byla nesprávně nastavena na **hodnotu true**. Teď je správně nastavené na false, což způsobí selhání statických kontrolních výrazů. `std::is_convertable<>::value`

- **Přednastavené nebo odstraněné konstruktory triviálního kopírování a přesunu respektují specifikátory přístupu.**

   Předchozí verze kompilátoru nekontrolovaly specifikátor přístupu u výchozích nebo odstraněných konstruktorů triviální kopie a přemístění, než je povolí volání. Toto staré chování bylo nesprávné a nevyhovuje C++ standardu. V některých případech toto staré chování vytvořilo riziko tichého chybného generování kódu, což vede k nepředvídatelnému chování za běhu. Kompilátor nyní kontroluje specifikátor přístupu u výchozích nebo odstraněných konstruktorů triviální kopie a přesunutí, aby bylo možné určit, zda je lze volat, a pokud ne, vystaví se v důsledku upozornění kompilátoru C2248.

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

- Vyřazení **podpory kódu ATL s atributy** (Úroveň 1 (`/W1`) při výchozím nastavení)

   Předchozí verze kompilátoru podporovaly atribut ATL kódu. Jako další fáze odebrání podpory pro kód ATL s atributy, který [začal v jazyce Visual C++ 2008](#whats-new-for-c-in-visual-studio-2008), je kód ATL s atributy zastaralý. Kompilátor nyní vydává upozornění kompilátoru C4467, aby mohl identifikovat tento druh zastaralého kódu.

   ```Output
    warning C4467: Usage of ATL attributes is deprecated
   ```

   Pokud chcete pokračovat v používání kódu ATL s atributy, dokud není podpora odebrána od kompilátoru, můžete toto upozornění zakázat předáním `/Wv:18` argumentů nebo `/wd4467` příkazového řádku kompilátoru nebo přidáním `#pragma warning(disable:4467)` do zdrojového kódu.

   Příklad 1 (před)

   ```cpp
              [uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
    class A {};
   ```

   Příklad 1 (za)

   ```cpp
    __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) A {};
   ```

   Někdy možná budete potřebovat nebo chcete vytvořit soubor IDL, abyste se vyhnuli použití zastaralých atributů ATL, jako v následujícím příkladu kódu.

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

   Dále přidejte do sestavení krok MIDL, abyste se ujistili, že jsou C++ vygenerovány definice rozhraní.

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

   Pak použijte ATL přímo v implementačním souboru, jako v následujícím příkladu kódu.

   Příklad 2 implementace (za)

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

- **Soubory předkompilovaných hlaviček (PCH) a neodpovídající direktivy #include** (týká `/Wall` `/WX`se jenom)

   Předchozí verze kompilátoru přijaly neshodné `#include` direktivy ve zdrojových souborech mezi `-Yc` a `-Yu` kompilacemi při použití souborů předkompilované hlavičky (PCH). Kód napsaný tímto způsobem již není kompilátorem přijat. Kompilátor nyní vydává upozornění kompilátoru CC4598, aby při použití souborů PCH `#include` mohla identifikovat neshodné direktivy.

   ```Output
    warning C4598: 'b.h': included header file specified for Ycc.h at position 2 does not match Yuc.h at that position
   ```

   Příklad (před):

   X. cpp (-YCC. h)

   ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
   ```

   Z. cpp (-Yuc. h)

   ```cpp
    #include "b.h"
    #include "a.h"  // mismatched order relative to X.cpp
    #include "c.h"
   ```

   Příklad (po)

   X. cpp (-YCC. h)

   ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
   ```

   Z. cpp (-Yuc. h)

   ```cpp
    #include "a.h"
    #include "b.h" // matched order relative to X.cpp
    #include "c.h"
   ```

- **Soubory předkompilovaných hlaviček (PCH) a neodpovídající adresáře zahrnutí** (týká `/Wall` `/WX`se jenom)

   Předchozí verze kompilátoru přijaly při použití souborů předkompilované hlavičky (PCH`-I`) neodpovídající argumenty příkazového řádku include `-Yc` ( `-Yu` ) pro kompilátor mezi a kompilací. Kód napsaný tímto způsobem již není kompilátorem přijat.   Kompilátor nyní vydává upozornění kompilátoru CC4599, aby při použití souborů PCH mohla identifikovat neshodné argumenty příkazového řádku include (`-I`).

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

## <a name="whats-new-for-c-in-visual-studio-2013"></a>Co je nového C++ v nástroji v Visual Studio 2013

### <a name="improved-iso-cc-standards-support"></a>Vylepšená podpora ISOC++ C/standardů

#### <a name="compiler"></a>Přepínač

MSVC podporuje tyto funkce jazyka ISO C++ 11:

- Výchozí argumenty šablon pro šablony funkcí
- Delegování konstruktorů
- Explicitní operátory převodu
- Inicializační seznamy a jednotná inicializace.
- Nezpracované řetězcové literály.
- Variadické šablony.
- Šablony aliasů.
- Odstraněné funkce.
- Inicializátory nestatických datových členů (Nsdmi).
- Výchozí funkce. \*
- Podporuje tyto funkce jazyka ISO C99:
- _Bool
- Složené literály.
- Určené Inicializátory.
- Kombinování deklarací s kódem.
- Převod řetězcového literálu na upravitelné hodnoty může být zakázán pomocí nové možnosti `/Zc:strictStrings`kompilátoru. V jazyce c++ 98 je převod z řetězcových literálů na `char*` (a širší řetězcové literály na `wchar_t*`) zastaralý. V jazyce C++ 11 byl převod zcela odebrán. I když kompilátor může striktně splňovat standard, místo toho poskytuje `/Zc:strictStrings` možnost, abyste mohli řídit převod. Ve výchozím nastavení je tato možnost vypnuta. Všimněte si, že při použití této možnosti v režimu ladění nebude STL zkompilována.
- přetypování odkazů rvalue/lvalue. V případě odkazů rvalue může C++ 11 jasně rozlišovat mezi hodnoty lvalue a rvalue. Dříve kompilátor tuto situaci neposkytl ve zvláštních scénářích přetypování. Byla přidána nová možnost kompilátoru `/Zc:rvalueCast`, která má za to, že kompilátor vyhovuje pracovnímu dokumentu C++ jazyka (viz oddíl 5,4, [expr. cast]/1). Výchozí chování, pokud není tato možnost zadána, je stejné jako v aplikaci Visual Studio 2012.

> [!NOTE]
> U výchozích funkcí není podporováno použití = Default pro vyžádání kopírování členůch konstruktorů a operátorů přiřazení přesunutí.

### <a name="c99-libraries"></a>Knihovny C99

Deklarace a implementace jsou přidány pro chybějící funkce v těchto hlavičkách: Math. h, CType. h, wctype. h, stdio. h, Stdlib. h a WCHAR. h. Přidané jsou také nové hlavičky Complex. h, stdbool. h, fenv. h a inttypes. h a implementace pro všechny funkce deklarované v nich. K dispozici C++ jsou nové hlavičky obálky (ccomplex, cfenv, cinttypes, ctgmath) a několik dalších je aktualizováno (ccomplex, cctype, clocale, cmath, cstdint, cstdio, CString, cwchar a cwctype).

### <a name="standard-template-library"></a>Standardní šablona knihovny

Podpora pro explicitní operátory převodu C++ 11, seznamy inicializátorů, výčty v oboru a variadické šablony.
Všechny kontejnery teď podporují jemně odstupňované požadavky na prvky C++ 11.
Podpora pro tyto funkce C++ 14:

- "Transparentní operátor funktory" méně < >, větší < > a < >, vynásobí < > atd.
- make_unique<T>(args...) a make_unique < T [] > (n)
- cbegin ()/cend (), rbegin ()/rend () a crbegin – () nečlenské funkce/crend ().
- \<atomická > obdržela mnoho vylepšení výkonu.
- \<type_traits > obdržely zásadní stabilizaci a opravy kódu.

### <a name="breaking-changes"></a>Nejnovější změny

Tato vylepšená podpora ISO C/C++ standardů může vyžadovat změny stávajícího kódu tak, aby splňovaly c++ 11 a správně kompilovány v jazyce Visual C++ v Visual Studio 2013.

### <a name="visual-c-library-enhancements"></a>Vylepšení C++ vizuální knihovny

- C++Přidala se sada SDK REST. Má moderní C++ implementaci služeb REST.
- C++Podpora textury AMP je vylepšena. Nyní zahrnuje podporu pro mipmapy a nové režimy vzorkování.
- Úlohy PPL podporují více technologií plánování a asynchronní ladění. Nová rozhraní API umožňují vytvářet PPL úlohy pro normální výsledky a podmínky výjimky.

### <a name="c-application-performance"></a>C++Výkon aplikace

- Rutina auto-vektorizace nyní rozpoznává a C++ optimalizuje více vzorů, aby se váš kód spouštěl rychleji.
- Vylepšení kvality kódu pro platformu ARM a mikroarchitektury Atom.
- přidala se konvence volání __vectorcall. Předejte argumenty typu vektoru pomocí konvence volání __vectorcall pro použití vektorových registrů.
- Nové možnosti linkeru. Přepínače (Compiler) a `/Gy` (Assembler) umožňují optimalizace linkeru, aby se vytvořily binární soubory. `/Gw`
- C++Podpora sdílené paměti AMP umožňuje snížit nebo odstranit kopírování dat mezi CPU a GPU.

### <a name="profile-guided-optimization-pgo-enhancements"></a>Vylepšení optimalizace na základě profilu (PGO)

- Zvýšení výkonu při snížení pracovní sady aplikací, které jsou optimalizované pomocí PGO.
- Nový PGO pro vývoj aplikací prostředí Windows Runtime.

### <a name="windows-runtime-app-development-support"></a>Podpora vývoje prostředí Windows Runtime aplikací

- **Podpora zabaleného typu ve strukturách hodnot.**

   Nyní můžete definovat typy hodnot pomocí polí, která mohou mít hodnotu null – například `IBox<int>^` na rozdíl od **int**. To znamená, že pole mohou buď mít hodnotu, nebo být rovna **nullptr**.

- **Rozsáhlejší informace o výjimce.**

   C++/CX podporuje nový model chyb Windows, který umožňuje zachytit a rozmnožení informací s bohatou výjimkou napříč binárním rozhraním aplikace (ABI); To zahrnuje zásobníky volání a vlastní řetězce zpráv.

- **Objekt:: ToString () je teď virtuální.**

   Nyní můžete přepsat ToString v uživatelsky definovaných typech prostředí Windows Runtime odkazů.

- **Podpora pro zastaralá rozhraní API.**

   Veřejná prostředí Windows Runtime rozhraní API se teď dají označit jako zastaralá a přidaná vlastní zpráva, která se zobrazí jako upozornění sestavení, a může tak poskytnout pokyny k migraci.

- **Vylepšení ladicího programu.**

   Podpora ladění nativního/JavaScriptu pro interoperabilitu, prostředí Windows Runtime diagnózy výjimek a asynchronní ladění kódu (prostředí Windows Runtime i PPL).

> [!NOTE]
> Kromě C++specifických funkcí a vylepšení, která jsou popsána v této části, mohou další vylepšení v aplikaci Visual Studio také pomáhat při psaní lepších aplikací prostředí Windows Runtime.

### <a name="diagnostics-enhancements"></a>Vylepšení diagnostiky

- Vylepšení ladicího programu. Podpora pro asynchronní ladění a ladění Pouze můj kód.
- Kategorie analýzy kódu. Nyní můžete zobrazit výstup v kategoriích z analyzátoru kódu, který vám může pomoct najít a opravit vady kódu.
- Diagnostika XAML. Nyní můžete diagnostikovat reakce uživatelského rozhraní a problémy s využitím baterie v kódu XAML.
- Vylepšení grafiky a ladění GPU
- Vzdálené zachytávání a přehrávání na skutečných zařízeních.
- Souběžné C++ ladění v amp a CPU.
- Vylepšená C++ diagnostika modulu runtime amp.
- Ladění trasování HLSL výpočetního shaderu

### <a name="3-d-graphics-enhancements"></a>Vylepšení 3D grafiky

- Podpora kanálu obsahu obrázku pro předem vynásobený formát Alpha DDS.
- Editor obrázků používá interně předem vynásobený alfa pro vykreslování a brání tak vykreslování artefaktů, jako jsou tmavé olemování.
- Editory obrázků a modelů. Vytvoření uživatelem definovaného filtru je nyní podporováno v Návrháři shaderu v editoru obrázků a editoru modelů.

### <a name="ide-and-productivity"></a>Prostředí IDE a produktivita

**Vylepšené formátování kódu**. Můžete použít další nastavení formátování C++ kódu. Pomocí těchto nastavení můžete řídit nové umístění složených závorek a klíčových slov, odsazení, mezery a zalomení řádků. Kód je automaticky zformátován při dokončování příkazů a bloků a při vložení kódu do souboru.

**Dokončování složených závorek** C++Kód nyní automaticky dokončí uzavírací znaky, které odpovídají těmto úvodním znakům:

- {(složená závorka)
- [(hranatá závorka)
- ((závorky)
- ' (jednoduchá uvozovka)
- "(uvozovky)

**Další C++ funkce automatického dokončování.**

- Přidá středník pro typy tříd.
- Dokončí závorky pro literály nezpracovaných řetězců.
- Dokončí víceřádkové komentáře (/\* \*/).

**Najít všechny odkazy** teď automaticky vyřeší a filtruje odkazy na pozadí po zobrazení seznamu textových shod.

**Filtrování seznamu členů založeného na kontextu.** Nepřístupné členy jsou filtrovány ze seznamů členů technologie IntelliSense. Například soukromé členy nejsou zobrazeny v seznamu členů, pokud neupravujete kód, který implementuje daný typ. Když je seznam členů otevřený, můžete stisknutím **kombinace kláves CTRL +** +odebrat jednu úroveň filtrování (platí pouze pro aktuální okno seznamu členů). Stisknutím **kombinace kláves CTRL**+**J** můžete odebrat filtrování textu a zobrazit každého člena.

**Posouvání parametru help.** Podpis zobrazované funkce v popisku parametru nápovědy se teď změní na základě počtu parametrů, které jste skutečně napsali, a ne pouhým zobrazením libovolného podpisu a jeho aktualizace na základě aktuálního kontextu. Parametr help také správně funguje při zobrazení ve vnořených funkcích.

**Přepnout hlavičku/soubor kódu.** Nyní můžete přepínat mezi hlavičkou a odpovídajícím souborem kódu pomocí příkazu v místní nabídce nebo klávesové zkratky.

**Okno vlastností C++ projektu změny velikosti**

**Automatické generování kódu obslužné rutiny události v C++/CX a C++/CLI.**  Při psaní kódu pro přidání obslužné rutiny události do souboru kódu C++/CX nebo C++/CLI může editor automaticky generovat instanci delegáta a definici obslužné rutiny události. Okno popisu se zobrazí, když je možné automaticky generovat kód obslužné rutiny události.

**Vylepšení povědomí DPI.** Nastavení sledování DPI pro soubory manifestu aplikace teď podporuje nastavení "pro monitorování s vysokým rozlišením DPI".

**Rychlejší přepínání konfigurace.** U rozsáhlých aplikací se přepínáním konfigurací – zejména následných operací přepínání – provede mnohem víc rychleji.

**Efektivita při sestavování** Mnohé optimalizace a využití vícejádrových jader urychlují vytváření sestavení, zejména u velkých projektů. Přírůstková sestavení C++ pro aplikace, které mají C++ odkazy na WinMD, jsou také mnohem rychlejší.

## <a name="whats-new-for-c-in-visual-studio-2012"></a>Co je nového C++ v aplikaci Visual Studio 2012

### <a name="improved-c11-standards-support"></a>Vylepšená podpora standardů C++ 11

#### <a name="standard-template-library"></a>Standardní šablona knihovny

- Podpora pro nové hlavičky STL: \<atomické > \<, Chrono > \<, condition_variable > \<, > systému souborů \<, budoucí > \<, > pro \<zámek, poměr > \< a > vlákna.
- Pro optimalizaci využití prostředků paměti jsou kontejnery teď menší. Například v režimu vydání x86 s výchozími nastaveními `std::vector` se v aplikaci Visual Studio 2012 zmenšila ze 16 bajtů v aplikaci Visual Studio 2010 na 12 bajtů a `std::map` v aplikaci Visual Studio 2012 se zmenší z 16 bajtů 2010 na 8 bajtů.
- Jak je povoleno, ale není vyžadováno standardem C++ 11, byly implementovány iterátory SCARY.

#### <a name="other-c11-enhancements"></a>Další vylepšení pro C++ 11

- Smyčky for na základě rozsahu. Můžete napsat robustnější smyčky, které pracují s poli, kontejnery STL a kolekcemi prostředí Windows Runtime ve formě pro (for-range-declaration: Expression). Toto je součást základní jazykové podpory.
- Výrazy lambda bez stavů, které jsou bloky kódu, které začínají prázdným příznakem lambda [] a zachytit žádné místní proměnné, jsou nyní implicitně převoditelné na ukazatele funkcí, jak jsou vyžadovány standardem C++ 11.
- Podpora vymezených výčtů. Klíč C++ výčtu třídy výčtu je nyní podporován. Následující kód ukazuje, jak se tento výčet klíč liší od předchozího chování výčtu.

   ```cpp
  enum class Element { Hydrogen, Helium, Lithium, Beryllium };
  void func1(Element e);
  func1(Hydrogen); // error C2065: 'Hydrogen' : undeclared identifier
  func1(Element::Helium); // OK
   ```

### <a name="windows-runtime-app-development-support"></a>Podpora vývoje prostředí Windows Runtime aplikací

- **Nativní model uživatelského rozhraní založeného na jazyce XAML** Pro prostředí Windows Runtime aplikace můžete použít nový nativní model uživatelského rozhraní založeného na jazyce XAML.
- **Rozšíření C++ součástí Visual Component**. Tato rozšíření zjednodušují spotřebu prostředí Windows Runtime objektů, což je nezbytná součást prostředí Windows Runtimech aplikací. Další informace najdete v tématu [Průvodce pro prostředí Windows Runtime aplikace pomocí C++ ](../cppcx/universal-windows-apps-cpp.md) a [referenční C++ dokumentace jazyka VisualC++(/CX)](../cppcx/visual-c-language-reference-c-cx.md) .
- **Hry DirectX**. Můžete vyvíjet poutavé hry pomocí nové podpory rozhraní DirectX pro aplikace prostředí Windows Runtime.
- **Spolupráce XAML/DirectX**. Prostředí Windows Runtime aplikace, které používají XAML i DirectX, teď fungují efektivně.
- **Prostředí Windows Runtime vývoj knihoven DLL komponent**. Vývoj komponent knihovny DLL zpřístupňuje prostředí Windows Runtime prostředí.

### <a name="compiler-and-linker"></a>Kompilátor a linker

- **Auto-vektorizace**. Kompilátor analyzuje smyčky v kódu a tam, kde je to možné, vygeneruje pokyny, které používají vektorové registry a pokyny, které jsou přítomny ve všech moderních procesorech. Díky tomu se smyčky rychleji spouštějí. (Instrukce procesoru se označují jako SSE, pro Streaming SIMD Extensions). Tuto optimalizaci není nutné povolit ani vyžadovat, protože se používá automaticky.
- **Auto-paralelizace**. Kompilátor může analyzovat smyčky v kódu a generovat pokyny, které rozšíří výpočty napříč více jádry nebo procesory. Díky tomu můžou smyčky běžet rychleji. Tuto optimalizaci musíte požádat, protože není ve výchozím nastavení povolená. V mnoha případech pomáhá začlenit do kódu `#pragma loop(hint_parallel(N))` hned před smyčkami, které chcete paralelně použít.
- Automatické vektorizace a auto-paralelizace mohou fungovat společně, aby výpočty byly rozloženy mezi více jader a kód v každém jádru používá své vektorové Registry.

### <a name="new-in-visual-studio-2012-update-1"></a>Novinka v aplikaci Visual Studio 2012 Update 1

Při sestavování kódu cílit na C++ systém Windows XP.
K cílení na systémy C++ Windows XP a windows Server 2003 můžete použít kompilátor a knihovny společnosti Microsoft.

#### <a name="parallel-programming-support"></a>Podpora paralelního programování

##### <a name="c-accelerated-massive-parallelism-amp"></a>C++ Accelerated Massive Parallelism (AMP)

C++AMP zrychlí provádění C++ kódu využitím hardwaru, který je obvykle PŘÍTOMEN jako GPU na samostatné grafické kartě. Programovací C++ model amp zahrnuje multidimenzionální pole, indexování, přenos paměti, dělení a knihovnu matematických funkcí. Pomocí C++ rozšíření jazyka amp a omezení kompilátoru můžete řídit, jak se data přesunou z procesoru do GPU a zpátky.

**Tém.** Prostředí pro ladění aplikací, které používají C++ amp k cílení na GPU, je stejně jako ladění C++ pro jiné aplikace. To zahrnuje nové přidané paralelní ladění, které bylo zmíněno dříve.

**Profilace.** Nyní je k dispozici podpora profilace pro aktivitu GPU založenou C++ na amp a dalších programovacích modelech založených na rozhraní Direct3D.

#### <a name="general-parallel-programming-enhancements"></a>Vylepšení obecného paralelního programování

Díky přesunu hardwaru do architektur s více jádry a mnoha jádry už vývojáři nemůžou spoléhat na neustále rostoucí hodiny od jednoduchých jader. Podpora paralelního programování v Concurrency Runtime umožňuje vývojářům využít tyto nové architektury.
V aplikaci Visual Studio 2010 byly C++ představeny výkonné knihovny paralelního zpracování, jako je například knihovna paralelních vzorů, společně s funkcemi pro využití souběžnosti díky vyjádřením sofistikovaných kanálů toku dat. V aplikaci Visual Studio 2012 byly tyto knihovny rozšířeny tak, aby poskytovaly lepší výkon, větší kontrolu a bohatou podporu paralelních vzorů, které vývojáři potřebují nejvíc. Šířka nabídky teď zahrnuje:

- Bohatý programovací model založený na úlohách, který podporuje asynchronii a pokračování.
- Paralelní algoritmy, které podporují paralelismu rozvětvení (parallel_for, parallel_for s spřažením, parallel_for_each, parallel_sort, parallel_reduce, parallel_transform).
- Kontejnery bezpečné pro souběžnost, které poskytují verze STD datových struktur pro přístup z více vláken, jako jsou priority_queue, Queue, Vector a map.
- Knihovna asynchronních agentů, kterou můžou vývojáři použít k vyjádření kanálů toku dat, které se přirozeně rozloží na souběžné jednotky.
- Přizpůsobený Plánovač a správce prostředků, který usnadňuje hladké složení vzorů v tomto seznamu.

##### <a name="general-parallel-debugging-enhancements"></a>Obecná vylepšení paralelního ladění

Kromě okna **Paralelní úlohy** a **paralelní zásobníky** nabízí sada Visual Studio 2012 nové okno **paralelního sledování** , které umožňuje prozkoumávat hodnoty výrazu napříč všemi vlákny a procesy a provádět řazení a filtrování výsledku. Můžete také použít vlastní vizualizace k roztažení okna a můžete využít novou podporu více procesů napříč všemi okny nástrojů.

### <a name="ide"></a>IDE – integrované vývojové prostředí

**Šablony sady Visual Studio podporují.** Nyní můžete použít technologii šablon sady Visual Studio k vytváření C++ šablon projektů a položek.

**Asynchronní načtení řešení** Projekty jsou nyní načítány asynchronně – klíčové části řešení jako první, takže můžete začít pracovat rychleji.

**Automatizované nasazení pro vzdálené ladění.** Nasazení souborů pro vzdálené ladění v jazyce Visual C++ bylo zjednodušeno. Možnost **nasadit** v místní nabídce projektu automaticky kopíruje do vzdáleného počítače soubory, které jsou zadány ve vlastnostech konfigurace ladění. Ruční kopírování souborů do vzdáleného počítače již není vyžadováno.

**C++/CLI IntelliSense.** C++/CLI teď má plnou podporu technologie IntelliSense. Funkce IntelliSense, jako jsou rychlé informace, parametr help, členové seznamu a automatické dokončování, jsou C++teď pro/CLI. fungovat. Kromě toho další vylepšení technologie IntelliSense a IDE uvedená v tomto dokumentu fungují i pro C++/CLI.

**Bohatší popisy tlačítek technologie IntelliSense.** C++Přehledy rychlých informací technologie IntelliSense teď zobrazují rozšířené informace o stylu dokumentačních komentářů XML. Pokud používáte rozhraní API z knihovny, například C++ amp – obsahuje dokumentační komentáře XML, pak popisek technologie IntelliSense zobrazí více informací, než pouze deklarace. V případě, že váš kód obsahuje dokumentační komentáře XML, zobrazí popisky technologie IntelliSense bohatší informace.

**C++Konstrukce kódu.** Kostra kódu je k dispozici pro přepínač, if-else, for Loop a další základní konstrukce kódu, v rozevíracím seznamu Členové seznamu. Vyberte část kódu ze seznamu, kterou chcete vložit do kódu, a potom vyplňte požadovanou logiku. Můžete také vytvořit vlastní části kódu pro použití v editoru.

**Vypíše vylepšení členů.** Rozevírací seznam **Členové seznamu členů** se automaticky zobrazí při psaní kódu do editoru kódu. Výsledky se filtrují tak, aby se při psaní zobrazovaly jenom relevantní členy. Můžete řídit druh logiky filtrování používané seznamem členů – v dialogovém okně **Možnosti** v části **textový editor** >  > **C++C/** **Upřesnit**.

**Sémantická barva.** Typy, výčty, makra a další C++ tokeny teď mají ve výchozím nastavení barevné nabarvení.

**Zvýrazňování odkazů** Výběrem symbolu teď zvýrazníte všechny výskyty symbolu v aktuálním souboru. Stisknutím **kombinace kláves CTRL**+**SHIFT +** +**šipka nahoru** nebo **CTRL**+++**šipka dolů** se můžete pohybovat mezi zvýrazněnými odkazy. Tuto funkci můžete vypnout v dialogovém okně **Možnosti** v části **textový editor** > **C++C/**  > Upřesnit.

### <a name="application-lifecycle-management-tools"></a>Nástroje pro správu životního cyklu aplikací

#### <a name="static-code-analysis"></a>Analýza statického kódu

Statická analýza pro C++ byla aktualizována, aby poskytovala rozsáhlejší informace o kontextu chyby, více pravidel analýzy a lepší výsledky analýzy. V okně Nová analýza kódu můžete filtrovat zprávy podle klíčového slova, projektu a závažnosti. Když vyberete zprávu v okně, v editoru kódu se zvýrazní řádek v kódu, kde byla zpráva aktivována. V případě C++ některých upozornění zobrazuje zpráva obsahuje zdrojové řádky, které zobrazují cestu spuštění, která vede k upozornění. rozhodovací body a důvody pro provedení této konkrétní cesty jsou zvýrazněny.
Analýza kódu je obsažena ve většině edicí sady Visual Studio 2012. V edicích Professional, Premium a Ultimate jsou k dispozici všechna pravidla. V edicích Express pro Windows 8 a Windows Phone jsou k dispozici pouze nejzávažná upozornění. Analýza kódu není obsažena v edici Express pro web.
Tady je několik dalších vylepšení analýzy kódu:

- Nová upozornění souběžnosti vám pomohou vyhnout se chybám souběžnosti tím, že se ve vícevláknových C/C++ programech používají správné obory zámků. Analyzátor detekuje možné konflikty časování, jejich inverze, neshodující se kontrakty uzamčení volající/volaný, neodpovídající operace synchronizace a další chyby souběžnosti.
- Můžete zadat C++ pravidla, která chcete použít na analýzu kódu spouštěnou pomocí sad pravidel.
- V okně **Analýza kódu** můžete vložit do zdrojového kódu direktiva pragma, která potlačí vybrané upozornění.
- Můžete zvýšit přesnost a úplnost statické analýzy kódu pomocí nové verze jazyka Microsoft Source-Code Annotation (SAL) k popsání toho, jak funkce používá své parametry, předpoklady, které o nich jsou, a zaručuje, že provede dokončení.
- Podpora pro 64bitové C++ projekty.

#### <a name="updated-unit-test-framework"></a>Aktualizovaný systém testů jednotek

Použijte nové C++ rozhraní testování částí v aplikaci Visual Studio k zápisu C++ jednotkových testů. Do stávajícího C++ řešení přidejte nový projekt testování částí tak, že v kategorii C++ vizuálu C++ v dialogovém okně Nový projekt vyhledáte šablonu projektu testování částí. Začněte psát testy jednotek ve vygenerovaném zástupné složce TEST_METHOD kódu v souboru UnitTest1. cpp. Po zapsání testovacího kódu Sestavte řešení. Chcete-li spustit testy, otevřete okno **Průzkumníka testů jednotek** tak, že vyberete možnost **Zobrazit** > **ostatní okna** > **Průzkumníka testů**, a potom v místní nabídce požadovaného testovacího případu zvolte možnost **Spustit. vybraný test**. Po dokončení testovacího běhu můžete zobrazit výsledky testů a další informace o trasování zásobníku ve stejném okně.

#### <a name="architecture-dependency-graphs"></a>Grafy závislosti architektury

Pro lepší pochopení kódu můžete nyní generovat grafy závislostí pro binární, třídu, obor názvů a zahrnuté soubory v řešení. Na panelu nabídek zvolte **Architektura** > **Generovat graf závislosti**a potom **pro řešení** nebo **pro soubor include** pro vygenerování grafu závislostí. Po dokončení generování grafu ho můžete prozkoumat Rozbalením jednotlivých uzlů, získáním vztahů závislosti přesunutím mezi uzly a výběrem možnosti **Zobrazit obsah** v místní nabídce uzlu. Generovat graf závislostí pro zahrnuté soubory v místní nabídce pro zdrojový soubor \*.cpp nebo záhlaví \*.h souborů, zvolte **Generovat graf vložených souborů**.

#### <a name="architecture-explorer"></a>Průzkumník architektury

Pomocí **Průzkumníka architektury**můžete prozkoumat prostředky ve vašem C++ řešení, projektech nebo souborech. Na panelu nabídek vyberte **Architektura** > **Průzkumník architektury** **systému Windows** > . Můžete vybrat uzel, který vás zajímá, například **zobrazení tříd**. V tomto případě je pravá strana okna nástroje rozbalená se seznamem oborů názvů. Pokud vyberete obor názvů, nový sloupec zobrazí seznam tříd, struktur a výčtů v tomto oboru názvů. Můžete pokračovat v prozkoumání těchto prostředků nebo přejít zpět na sloupec v levém rohu a spustit další dotaz. Viz **Najít kód s Průzkumníkem architektury**.

#### <a name="code-coverage"></a>Pokrytí kódu

Pokrytí kódu bylo aktualizováno na dynamické instrumentace binárních souborů za běhu. Tím se sníží režie konfigurace a získáte lepší výkon. Můžete také shromažďovat data o pokrytí kódu z testů jednotek pro C++ aplikace. Když jste vytvořili C++ testy jednotek, můžete použít **Průzkumníka testů jednotek** ke zjišťování testů ve vašem řešení. Chcete-li spustit testy jednotek a shromažďovat data o pokrytí kódu pro ně, v **Průzkumníku testování částí**vyberte možnost **Analyzovat pokrytí kódu**. Výsledky pokrytí kódu můžete zkontrolovat v okně **výsledky pokrytí kódu** – na řádku nabídek vyberte **test** > **výsledků pokrytí kódu** **systému Windows** > .

## <a name="whats-new-for-c-in-visual-studio-2010"></a>Co je nového C++ v aplikaci Visual Studio 2010

### <a name="c-compiler-and-linker"></a>C++Kompilátor a linker

**auto – klíčové slovo** Klíčové slovo **auto** má nový účel. Použijte výchozí význam klíčového slova **auto** k deklaraci proměnné, jejíž typ je odvozen z inicializačního výrazu v deklaraci proměnné. Možnost kompilátoru vyvolá buď nový, nebo předchozí význam klíčového slova auto. `/Zc:auto`

**Specifikátor typu decltype.** Specifikátor typu **decltype** vrací typ zadaného výrazu. Použijte specifikátor typu **decltype** v kombinaci s klíčovým slovem **auto** k deklaraci typu, který je buď složitý, nebo známý pouze pro kompilátor. Například použijte kombinaci k deklarování šablony funkce, jejíž návratový typ závisí na typech svých argumentů šablony. Nebo Deklarujte funkci šablony, která volá jinou funkci, a potom vrátí návratový typ volané funkce.

**Výrazy lambda.** Funkce lambda mají tělo funkce, ale žádný název. Funkce lambda kombinují nejlepší vlastnosti ukazatelů na funkce a objekty funkce. Použijte funkci lambda samostatně, jako parametr funkce šablony namísto objektu Functions nebo spolu s klíčovým slovem **auto** k deklaraci proměnné, jejíž typ je lambda.

**Odkaz rvalue** Odkaz rvalue deklarátor (& &) deklaruje odkaz na rvalue. Odkaz rvalue umožňuje použít sémantiku přesunutí a dokonalé přesměrování k zápisu efektivnějších konstruktorů, funkcí a šablon.

**static_assert Declaration.** Deklarace **static_assert** testuje kontrolní výraz softwaru v době kompilace, na rozdíl od jiných mechanismů kontrolního výrazu, které jsou testovány v době běhu. Pokud se kontrolní výraz nezdařil, kompilace se nezdařila a je vydána zadaná chybová zpráva.

**Klíčová slova nullptr a __nullptr** MSVC umožňuje použití klíčového slova **nullptr** s nativním kódem nebo se spravovaným kódem. Klíčové slovo **nullptr** označuje, že popisovač objektu, vnitřní ukazatel nebo nativní typ ukazatele neodkazuje na objekt. Kompilátor interpretuje **nullptr** jako spravovaný kód při použití `/clr` možnosti kompilátoru a nativního kódu, pokud nepoužijete `/clr` možnost.
Klíčové slovo **__nullptr** specifické pro společnost Microsoft má stejný význam jako **nullptr**, ale vztahuje se pouze na nativní kód. Pokud kompilujete nativní kód CC++ /Code pomocí `/clr` možnosti kompilátoru, kompilátor nemůže určit, zda je klíčové slovo **nullptr** nativní nebo spravované období. Chcete-li záměr vyjasnit pro kompilátor, použijte klíčové slovo nullptr pro určení spravovaného termínu a **__nullptr** k určení nativního termínu.

**/Zc: trigraphs – možnost kompilátoru** Ve výchozím nastavení je podpora pro trigraphs zakázaná. Pro povolení podpory trigraphs použijte možnost kompilátoru.`/Zc:trigraphs`
Trigraph se skládá ze dvou po sobě jdoucích otazníků (??) následovaných jedinečným třetím znakem. Kompilátor nahradí trigraph odpovídajícím znakem interpunkce. Například kompilátor nahradí?? = trigraph se znakem # (čísla znaku). Použijte trigraphs ve zdrojových souborech jazyka C, které používají znakovou sadu, která neobsahuje určité znaky interpunkce.

**Nová možnost optimalizace na základě profilu.** PogoSafeMode je nová možnost optimalizace na základě profilu, která umožňuje určit, jestli se má při optimalizaci aplikace použít nouzový režim nebo rychlý režim. Bezpečný režim je bezpečný pro přístup z více vláken, ale je pomalejší než rychlý režim. Rychlý režim je výchozí chování.

**Nová možnost modulu CLR (Common Language Runtime)/CLR: nostdlib.** Je přidána nová možnost pro `/clr` (kompilace modulu Common Language Runtime). Pokud jsou zahrnuty různé verze stejných knihoven, je vydána Chyba kompilace. Nová možnost umožňuje vyloučit výchozí knihovny CLR, aby mohl program použít zadanou verzi.

**Nová direktiva pragma detect_mismatch.** Direktiva pragma detect_mismatch umožňuje do souborů vložit značku, která je porovnána s jinými značkami, které mají stejný název. Pokud je pro stejný název k dispozici více hodnot, linker vydá chybu.

**Vnitřní objekty XOP, vnitřní objekty FMA4 a vnitřní objekty LWP.** Přidaly se nové vnitřní funkce pro podporu vnitřních objektů XOP přidaných pro Visual Studio 2010 SP1, vnitřních objektů FMA4 přidaných pro Visual Studio 2010 SP1 a LWP Vnitřníchy přidaných pro technologie procesoru Visual Studio 2010 SP1. Pomocí __cpuid, __cpuidex určíte, které technologie procesoru jsou v konkrétním počítači podporovány.

### <a name="visual-studio-c-projects-and-the-build-system"></a>Projekty sady C++ Visual Studio a systém sestavení

**Nástroji.** Vizuální C++ řešení a projekty jsou nyní sestaveny pomocí nástroje MSBuild. exe, který nahrazuje soubor vcbuild. exe. MSBuild je stejný flexibilní a rozšiřitelný nástroj sestavení založený na jazyce XML, který používají jiné jazyky a typy projektů sady Visual Studio. Z důvodu této změny nyní soubory projektu C++ sady Visual Studio používají formát souboru XML a mají příponu. vcxproj. Soubory projektu C++ sady Visual Studio z dřívějších verzí sady Visual Studio se automaticky převedou do nového formátu souboru.

**Adresáře VC + +.** Nastavení adresáře VC + + se teď nachází na dvou místech. Pomocí stránky vlastností projektu můžete nastavit hodnoty pro jednotlivé projekty pro adresáře VC + +. Použijte **Správce vlastností** a seznam vlastností k nastavení globálních hodnot podle konfigurace pro adresáře VC + +.

**Závislosti mezi projekty.** V dřívějších verzích byly definované závislosti mezi projekty uloženy v souboru řešení. Při převodu těchto řešení do nového formátu souboru projektu jsou závislosti převedeny na odkazy z projektu na projekt. Tato změna může ovlivnit aplikace, protože se liší koncepty závislostí řešení a odkazů typu projekt-projekt.

**Makra a proměnné prostředí.** Nové makro _ITERATOR_DEBUG_LEVEL vyvolá podporu ladění pro iterátory. Použijte toto makro místo starších maker _SECURE_SCL a _HAS_ITERATOR_DEBUGGING.

### <a name="visual-c-libraries"></a>Knihovny jazyka Visual C++

**Knihovny Concurrency Runtime.** Rozhraní Concurrency Runtime Framework podporuje aplikace a komponenty, které běží souběžně, a je rozhraní pro programování souběžných aplikací C++v jazyce Visual. Aby bylo možné podporovat programování souběžných aplikací, knihovna paralelních vzorů (PPL) poskytuje obecné kontejnery a algoritmy pro provádění jemně odstupňovaného paralelismu. Knihovna asynchronních agentů poskytuje programovací model založený na objektech actor a rozhraní pro předávání zpráv pro hrubý úlohy toku dat a úloh.

**Standardní C++ knihovna:** Následující seznam popisuje mnoho změn, které byly provedeny ve standardní C++ knihovně.

- Nová funkce jazyka odkazu C++ rvalue byla použita k implementaci sémantiky přesunutí a dokonalého předávání mnoha funkcí v knihovně standardní šablony. Přesunutí sémantik a dokonalého předávání významně vylepšit výkon operací, které přidělují nebo přiřazují proměnné nebo parametry.
- Odkazy rvalue slouží také k implementaci nové `unique_ptr` třídy, což je bezpečnější typ inteligentního ukazatele `auto_ptr` než třída. `unique_ptr` Třída je přesunutá, ale nedá se kopírovat, implementuje striktní sémantiku vlastnictví bez ovlivnění bezpečnosti a funguje dobře s kontejnery, které jsou na odkazech rvalue vědět. `auto_ptr` Třída je zastaralá.
- `find_if_not`Patnáct nových funkcí, `copy_if`například,, a `is_sorted`, byly přidány do \<hlavičky > algoritmu.
- V hlavičce > paměti je nová funkce make_shared pohodlný, robustní a efektivní způsob, jak vytvořit sdílený ukazatel na objekt v okamžiku konstrukce objektu. \<
- Jednotlivě propojené seznamy jsou podporovány \<hlavičkou > forward_list.
- Nové `cbegin`členské funkce `cend`, `crbegin`, a `crend` poskytují objekt`const_iterator` , který se přesune dopředu nebo dozadu prostřednictvím kontejneru.
- \<System_error > záhlaví a související šablony podporují zpracování systémových chyb nízké úrovně. `exception_ptr` Členy třídy lze použít k přenosu výjimek mezi vlákny.
- Hlavička \<> codecvt podporuje převod různých kódování znaků Unicode na jiné kódování.
- Záhlaví \<> přidělování definuje několik šablon, které pomůžou přidělit a uvolnit bloky paměti pro kontejnery založené na uzlech.
- > Hlavičce \<náhodného existuje mnoho aktualizací.

### <a name="microsoft-foundation-class-mfc-library"></a>Knihovna Microsoft Foundation Class (MFC)

**Funkce systému Windows 7.** Knihovna MFC podporuje mnoho funkcí systému Windows 7, například uživatelské rozhraní (UI) pásu karet, hlavní panel, seznamy odkazů, miniatury s kartami, náhledy miniatur, indikátor průběhu, překryvná ikona a indexování vyhledávání. Vzhledem k tomu, že knihovna MFC automaticky podporuje mnoho funkcí Windows 7, možná nebudete muset upravovat existující aplikaci. Pro podporu dalších funkcí v nových aplikacích použijte Průvodce aplikací knihovny MFC k určení funkce, které chcete použít.

**Povědomí s více dotykovými.** MFC podporuje aplikace s uživatelským rozhraním s více dotykovými aplikacemi, například aplikace, které jsou napsané pro operační systém Microsoft Surface. Aplikace s více dotykovými aplikacemi může zpracovávat zprávy dotykového ovládání systému Windows a zprávy gesta, což jsou kombinace dotykové zprávy. Stačí zaregistrovat aplikaci pro události dotykové ovládání a gesta a operační systém bude směrovat události s více dotykovémi událostmi do obslužných rutin událostí.

**Povědomí o vysokém rozlišení DPI.** Ve výchozím nastavení jsou aplikace MFC nyní podporující vysoké rozlišení DPI. Pokud je aplikace s vysokým ROZLIŠENÍm (s vysokými body na palec), může operační systém škálovat Windows, text a jiné prvky uživatelského rozhraní na aktuální rozlišení obrazovky. To znamená, že obrázek s měřítkem je pravděpodobně správně rozložen a není oříznut nebo pixelated.

**Správce restartování.** Správce restartování automaticky uloží dokumenty a restartuje aplikaci, pokud se neočekávaně zavře nebo restartuje. Můžete například použít správce restartování k zahájení aplikace po jejím uzavření automatickou aktualizací. Další informace o tom, jak nakonfigurovat aplikaci tak, aby používala správce restartování, **najdete v tématu How to: Přidejte podporu**správce restartování.

**Objektu CTaskDialog.** Třídu lze použít místo standardního `AfxMessageBox` okna se zprávou. `CTaskDialog` `CTaskDialog` Třída zobrazuje a shromažďuje více informací, než je standardní okno se zprávou.

#### <a name="safeint-library"></a>SafeInt – knihovna

Nová knihovna SafeInt provádí bezpečné aritmetické operace, které vytváří účet pro přetečení celého čísla. Tato knihovna také porovnává různé druhy celých čísel.

#### <a name="new-active-template-library-atl-macros"></a>Nová makra knihovny ATL (Active Template Library)

Do knihovny ATL byla přidána nová makra pro rozšíření funkcí PROP_ENTRY_TYPE a PROP_ENTRY_TYPE_EX. PROP_ENTRY_INTERFACE a PROP_ENTRY_INTERFACE_EX umožňují přidat seznam platných identifikátorů CLSID. PROP_ENTRY_INTERFACE_CALLBACK a PROP_ENTRY_INTERFACE_CALLBACK_EX umožňují určit, zda je identifikátor CLSID platný, zadáním funkce zpětného volání.

#### <a name="analyze-warnings"></a>Upozornění/Analyze

Většina `/analyze` upozornění (Enterprise Code Analysis) byla z knihoven C run-time (CRT), MFC a ATL odebrána.

#### <a name="animation-and-d2d-support"></a>Animace a podpora D2D

MFC teď podporuje animace a Direct2D grafiky. Knihovna MFC má několik nových tříd knihovny MFC a funkcí, které podporují tuto funkci. Existují také dva nové návody k zobrazení, jak přidat objekt D2D a objekt animace do projektu. Tyto návody jsou **názorné: Přidání objektu D2D do projektu** knihovny MFC a **návodu: Přidání animace do projektu**MFC.

### <a name="ide"></a>IDE – integrované vývojové prostředí

**Vylepšená technologie IntelliSense.** IntelliSense pro vizuál C++ byl zcela přepracován, aby byl rychlejší a přesnější a byl schopný zvládnout větší projekty. Pro dosažení tohoto vylepšení rozhraní IDE rozlišuje mezi tím, jak vývojář zobrazuje a upravuje zdrojový kód, a jak rozhraní IDE používá zdrojový kód a nastavení projektu k sestavení řešení.
Vzhledem k tomu, že se jedná o oddělení funkcí, jsou funkce procházení, jako je například **zobrazení tříd** a nový dialog **Přejít na** , zpracovávány systémem, který je založen na novém souboru SQL Server desktopové databáze (. sdf), který nahrazuje starý soubor pro procházení sestavení (. NCB). Funkce IntelliSense, jako jsou rychlé informace, automatické dokončování a parametry, analyzují jednotky překladu pouze v případě potřeby. Hybridní funkce, jako je nové okno **hierarchie volání** , používají kombinaci funkcí Procházet a IntelliSense.
Vzhledem k tomu, že technologie IntelliSense zpracovává pouze informace, které požadujete v okamžiku, rozhraní IDE bude lépe reagovat. Vzhledem k tomu, že jsou informace v aktuálním stavu, zobrazení IDE a Windows jsou přesnější. Vzhledem k tomu, že je infrastruktura IDE lépe uspořádaná, podporuje větší škálovatelnost a je škálovatelná, může zpracovávat větší projekty.

**Vylepšené chyby technologie IntelliSense.** Rozhraní IDE lépe detekuje chyby, které by mohly způsobit ztrátu technologie IntelliSense, a v nich zobrazuje červené vlnovky. Kromě toho rozhraní IDE ohlásí chyby IntelliSense do **okna Seznam chyb**. Chcete-li zobrazit kód, který je příčinou problému, dvakrát klikněte na chybu v **okně Seznam chyb**.

**Funkce automatického dokončování #include.** IDE podporuje automatické dokončování pro `#include` klíčové slovo. Když zadáte `#include`, rozhraní IDE vytvoří rozevírací seznam platných hlavičkových souborů. Pokud budete pokračovat zadáním názvu souboru, rozhraní IDE vyfiltruje seznam na základě vaší položky. V libovolném okamžiku můžete vybrat ze seznamu soubor, který chcete zahrnout. To vám umožní rychle zahrnout soubory bez znalosti přesného názvu souboru.

**Přejděte na.** Dialogové okno **Přejít k** umožňuje vyhledat všechny symboly a soubory v projektu, které odpovídají zadanému řetězci. Výsledky hledání jsou okamžitě revidovány při psaní dalších znaků v hledaném řetězci. V poli zpětné vazby **výsledků** se dozvíte, kolik položek se našlo, a pomůže vám rozhodnout se, jestli se má vaše hledání omezit. Pole **druh/rozsah**, **umístění**a **Náhled** zpětné vazby vám pomůžou určit, které položky mají podobné názvy. Kromě toho můžete tuto funkci rozšířit tak, aby podporovala jiné programovací jazyky.

**Paralelní ladění a profilace.** Ladicí program sady Visual Studio je vědom Concurrency Runtime a pomáhá při odstraňování potíží s aplikacemi pro paralelní zpracování. K vizualizaci celkového chování aplikace můžete použít nový nástroj Concurrency Profiler. Můžete také použít nová okna nástrojů k vizualizaci stavu úloh a jejich zásobníků volání.

**Návrhář pásu karet** **Návrhář pásu karet** je grafický editor, který umožňuje vytvořit a upravit uživatelské rozhraní pásu karet MFC. Konečné uživatelské rozhraní pásu karet je reprezentované souborem prostředků založeným na jazyce XML (. mfcribbon-ms). U existujících aplikací můžete zachytit aktuální uživatelské rozhraní pásu karet dočasným přidáním několika řádků kódu a následným vyvoláním **Návrháře pásu karet**. Po vytvoření souboru prostředků pásu karet můžete ručně nahradit kód uživatelského rozhraní pásu karet několika příkazy, které načítají prostředek pásu karet.

**Hierarchii volání.** Okno **hierarchie volání** umožňuje přejít ke všem funkcím, které jsou volány určitou funkcí, nebo ke všem funkcím, které volají konkrétní funkci.

### <a name="tools"></a>Nástroje

**Průvodce třídou MFC** Visual C++ 2010 vrátí do nástroje Průvodce TŘÍDou MFC, který se dobře týká. Průvodce třídou MFC je pohodlný způsob, jak do projektu přidat třídy, zprávy a proměnné, aniž byste museli ručně upravovat sady zdrojových souborů.

**Průvodce ovládacím prvkem ATL.** Průvodce ovládacím prvkem ATL již `ProgID` pole automaticky neplní. Pokud ovládací prvek `ProgID`ATL nemá, jiné nástroje nemusí s ním fungovat. Jedním z příkladů nástroje, které vyžadují ovládací prvky `ProgID` , je dialogové okno **Vložit aktivní ovládací prvek** . Další informace o dialogovém okně najdete v tématu **Vložení ovládacího prvku ActiveX do dialogového pole**.

### <a name="microsoft-macro-assembler-reference"></a>Microsoft Macro Assembler – referenční dokumentace

Přidání datového typu YMMWORD podporuje ne256é multimediální operandy, které jsou zahrnuty v pokynech Intel Advanced Vector Extensions (AVX).

## <a name="whats-new-for-c-in-visual-studio-2008"></a>Co je nového C++ v aplikaci Visual Studio 2008

### <a name="visual-c-integrated-development-environment-ide"></a>Integrované C++ vývojové prostředí (IDE) Visual

- Dialogová okna, která jsou vytvořená v aplikacích ATL, MFC a Win32, teď vyhovují pravidlům stylu Windows Vista. Když vytváříte nový projekt pomocí sady Visual Studio 2008, všechna dialogová okna, která vložíte do vaší aplikace, budou vyhovovat zásadám stylu Windows Vista. Pokud znovu zkompilujete projekt, který jste vytvořili v dřívější verzi sady Visual Studio, všechna existující dialogová okna budou mít stejný vzhled jako dříve. Další informace o tom, jak vložit dialogová okna do aplikace, naleznete v tématu **Editor dialogových**oken.

- Průvodce **projektem ATL** teď má možnost Registrovat komponenty pro všechny uživatele. Počínaje sadou Visual Studio 2008 jsou komponenty modelu COM a knihovny typů, které jsou vytvořeny průvodcem **projektu knihovny ATL** , registrovány v uzlu HKEY_CURRENT_USER registru, pokud nevyberete možnost **Registrovat komponentu pro všechny uživatele**.
- Průvodce **projektem ATL** již neposkytuje možnost vytvářet projekty ATL s atributy. Počínaje sadou Visual Studio 2008 průvodce **projektem ATL** nemá možnost změnit stavový atribut nového projektu. Všechny nové projekty ATL, které průvodce vytvoří, nyní nemají atribut.
- Zápis do registru je možné přesměrovat. Při zavedení systému Windows Vista vyžaduje zápis do určitých oblastí registru program, který je spuštěn v režimu zvýšené úrovně. Není žádoucí vždy spouštět Visual Studio v režimu zvýšené úrovně. Přesměrování vázané na uživatele automaticky přesměruje zápisy registru z klíče HKEY_CLASSES_ROOT na HKEY_CURRENT_USER bez jakýchkoli jakýchkoli programovacích změn.
- **Návrhář tříd** nyní má omezené podpory pro nativní C++ kód. V dřívějších verzích sady Visual Studio **Návrhář tříd** pracovali pouze s Visual C# a Visual Basic. C++Uživatelé teď můžou použít **Návrhář tříd**, ale jenom v režimu jen pro čtení. Další informace o použití **Návrhář tříd** s C++najdete v tématu **práce s vizuálním C++ kódem v Návrhář tříd**.
- Průvodce projektem již nemá možnost vytvořit projekt C++ SQL Server. Počínaje sadou Visual Studio 2008, Průvodce vytvořením nového projektu nemá možnost vytvořit projekt C++ SQL Server. SQL Server projekty vytvořené pomocí starší verze sady Visual Studio budou i nadále kompilovány a fungovat správně.

### <a name="visual-c-libraries"></a>Knihovny jazyka Visual C++

#### <a name="general"></a>Obecné

- Aplikace mohou být vázány na konkrétní verze vizuálních C++ knihoven. Někdy aplikace závisí na aktualizacích, které byly provedeny v knihovně C++ vizuálů po vydání verze. V takovém případě může spuštění aplikace na počítači, který má starší verze knihoven, způsobit neočekávané chování. Nyní můžete vytvořit vazby aplikace na konkrétní verzi knihoven, aby se nespouštěla v počítači, který má starší verzi knihoven.

#### <a name="stlclr-library"></a>STL/CLR – knihovna

- Vizuál C++ teď obsahuje knihovnu STL/CLR. Knihovna STL/CLR je balíčkem knihovny Standard Template Library (STL), podmnožinou standardní C++ knihovny pro použití s C++ a .NET Framework Common Language Runtime (CLR). Pomocí STL/CLR teď můžete ve spravovaném prostředí použít všechny kontejnery, iterátory a algoritmy STL.

#### <a name="mfc-library"></a>Knihovna MFC

- Systém Windows Vista podporuje běžné ovládací prvky. K podpoře funkcí v systému Windows Vista bylo přidáno více než 150 metod v 18 nových nebo existujících třídách, nebo pro zlepšení funkčnosti v aktuálních třídách MFC.
- Nová `CNetAddressCtrl` třída umožňuje zadávání a ověřování adres IPv4 a IPv6 nebo názvů DNS.
- Nová `CPagerCtrl` třída zjednodušuje použití ovládacího prvku stránkování v systému Windows.
- Nová `CSplitButton` třída zjednodušuje použití ovládacího prvku Windows SplitButton k výběru výchozí nebo volitelné akce.

#### <a name="c-support-library"></a>Knihovna podpory C++

- C++zavádí zařazování knihovny. Zařazovací knihovna poskytuje snadný a optimalizovaný způsob, jak zařazovat data mezi nativními a spravovanými prostředími. Knihovna je alternativou k složitějším a méně efektivním přístupům, jako je například použití PInvoke. Další informace najdete **v C++ tématu Přehled zařazování** .

#### <a name="atl-server"></a>ATL Server

- ATL Server je vydán jako sdílený zdrojový projekt.
- Většina základu kódu serveru ATL byla vydána jako sdílený zdrojový projekt na webu CodePlex a není nainstalována jako součást sady Visual Studio 2008. Několik souborů přidružených k serveru ATL již nejsou součástí sady Visual Studio. Seznam odebraných souborů naleznete v tématu **odebrané soubory ATL serveru**.
- Třídy kódování a dekódování dat z atlenc. h a funkce nástrojů a třídy z atlutil. h a atlpath. h jsou nyní součástí knihovny ATL.
- Společnost Microsoft bude nadále podporovat verze serveru ATL, které jsou součástí dřívějších verzí sady Visual Studio, pokud jsou podporovány tyto verze sady Visual Studio. CodePlex bude pokračovat ve vývoji kódu ATL serveru jako projekt komunity. Společnost Microsoft nepodporuje verzi CodePlex serveru ATL.

### <a name="visual-c-compiler-and-linker"></a>Vizuální C++ kompilátor a linker

#### <a name="compiler-changes"></a>Změny kompilátoru

- Kompilátor podporuje spravovaná přírůstková sestavení. Když zadáte tuto možnost, kompilátor nebude po změně odkazovaného sestavení překompilovat kód. Místo toho provede přírůstkové sestavení. Soubory jsou znovu zkompilovány pouze v případě, že změny mají vliv na závislý kód.
- Atributy související se serverem ATL již nejsou podporovány. Kompilátor už nepodporuje několik atributů, které přímo souvisejí s ATL serverem. Úplný seznam odebraných atributů najdete v tématu průlomové změny.
- Kompilátor podporuje architekturu Intel Core. Kompilátor obsahuje ladění pro mikroarchitekturu Intel Core během generování kódu. Ve výchozím nastavení je toto ladění zapnuté a nedá se zakázat, protože taky pomáhá procesorům Pentium 4 a dalším procesorům.
- Vnitřní objekty podporují novější procesory AMD a Intel. Několik nových vnitřních instrukcí podporuje větší funkčnost v novějších procesorech AMD a Intel. Další informace o nových vnitřních objektech najdete v tématu **dodatečné streaming SIMD Extensions 3 pokyny**, **streaming SIMD Extensions 4 pokyny**, **SSE4A a pokročilá vnitřní manipulace**, vnitřní objekty **AES**,  **_mm_clmulepi64_si128**a **__rdtscp**.
- `__cpuid` Funkce je aktualizována. `__cpuid` Funkceteďpodporujeněkoliknovýchfunkcíznejnovějšíchrevizíprocesorů`__cpuidex` AMD a Intel. `__cpuidex` Vnitřní je nová a shromažďuje další informace z posledních procesorů.
- Možnost `/MP` kompilátoru zkracuje celkový čas sestavení. `/MP` Možnost může významně zkrátit celkovou dobu pro zkompilování několika zdrojových souborů vytvořením několika procesů, které soubory zkompiluje současně. Tato možnost je užitečná hlavně v počítačích, které podporují multithreading, více procesorů nebo více jader.
- Možnost kompilátoru a klíčové slovo __w64 jsou zastaralé. `/Wp64` Možnost kompilátoru a klíčové slovo __w64, které zjišťují problémy přenositelnosti 64, jsou zastaralé a v budoucí verzi kompilátoru budou odebrány. `/Wp64` Namísto této možnosti kompilátoru a klíčového slova použijte MSVC, která cílí na 64 platformu.
- `/Qfast_transcendentals`vygeneruje vložený kód pro transcendentní funkce.
- `/Qimprecise_fwaits`Odebere příkazy fwait interní pro try Blocks při použití `/fp:except` možnosti kompilátoru.

### <a name="linker-changes"></a>Linker – změny

- Informace o řízení uživatelských účtů jsou teď vložené do souborů manifestu pro spustitelné soubory pomocí vizuálního C++ linkeru (Link. exe). Tato funkce je ve výchozím nastavení povolená. Další informace o tom, jak tuto funkci zakázat, nebo jak změnit výchozí chování, najdete v tématu `/MANIFESTUAC` (vložení informací o nástroji Řízení uživatelských účtů v manifestu).
- Linker teď má `/DYNAMICBASE` možnost povolit funkci náhodnosti rozložení adresního prostoru v systému Windows Vista. Tato možnost upraví hlavičku spustitelného souboru, aby označovala, zda by měla být aplikace náhodně založena v době načítání.

## <a name="whats-new-for-c-in-visual-studio-2005"></a>Co je nového C++ v aplikaci Visual Studio 2005

V sadě Visual C++ 2005 Service Pack 1 byly novinkou následující funkce:

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

### <a name="intrinsics-for-x64-only"></a>Vnitřní objekty pouze pro platformu x64

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

Kompilátor v této verzi přerušuje změny.

- 64 bitové nativní a křížové kompilátory.
- `/analyze`(Analýza podnikových kódů) byla přidána možnost kompilátoru.
- `/bigobj`byla přidána možnost kompilátoru.
- `/clr:pure`byly `/clr:safe`přidány, `/clr:oldSyntax` a. (Později zastaralé v aplikaci Visual Studio 2015 a odebrané v aplikaci Visual Studio 2017.)
- Zastaralé možnosti kompilátoru: mnoho možností kompilátoru je v této verzi zastaralé; Další informace najdete v tématu **zastaralé možnosti kompilátoru** .
- Dvojitá dvojitý `/clr` v kódu je zmenšena. Další informace naleznete v tématu **Double dvojitý (C++)** .
- `/EH`(Model zpracování výjimek) nebo `/EHs` již nemůže být použit k zachycení výjimky, která je vyvolána s jinou výjimkou throw; use. `/EHa`
- `/errorReport`(Sestava vnitřních chyb kompilátoru) byla přidána možnost kompilátoru.
- `/favor`(Optimalizováno pro 64) byla přidána možnost kompilátoru.
- `/FA`, `/Fa` (Soubor výpisu) – byla přidána možnost kompilátoru.
- `/FC`(Úplná cesta k souboru zdrojového kódu v diagnostice) byla přidána možnost kompilátoru.
- `/fp`(Určení chování s plovoucí desetinnou čárkou) byla přidána možnost kompilátoru.
- `/G`(Optimalizovat pro procesor) Byla přidána možnost kompilátoru Options.
- `/G`(Optimalizovat pro procesor) Byla přidána možnost kompilátoru Options.
- `/G3`byly `/G4`odebrány `/G5`možnosti `/G6`kompilátoru `/G7`,, `/GB` ,, a. Kompilátor teď používá "smíšený model", který se pokouší vytvořit nejlepší výstupní soubor pro všechny architektury.
- `/Gf`bylo odebráno. Místo `/GF` toho použijte (Eliminujte duplicitní řetězce).
- `/GL`(Celková optimalizace programu) je teď kompatibilní s `/CLRHEADER`.
- `/GR`je teď ve výchozím nastavení zapnuté.
- `/GS`(Kontrolu zabezpečení vyrovnávací paměti) nyní poskytuje ochranu zabezpečení pro parametry ukazatele na hrozby. `/GS`je teď ve výchozím nastavení zapnuté. `/GS`nyní funguje také u funkcí kompilovaných do jazyka `/clr` MSIL pomocí (kompilace modulu Common Language Runtime).
- `/homeparams`(Kopírování parametrů registru do zásobníku) byla přidána možnost kompilátoru.
- `/hotpatch`(Vytvoření image opravitelnou za provozu) – byla přidána možnost kompilátoru.
- Byly aktualizovány heuristiky vložených funkcí. Dalšíinformace najdete v tématu inline, **__inline**, **__forceinline** a **inline_depth** .
- Přidali jsme mnoho nových vnitřních funkcí a teď jsme si popsali spoustu dříve nedokumentovaných vnitřních objektů.
- Ve výchozím nastavení jakékoli volání New, které selže, vyvolá výjimku.
- `/ML`a `/MLd` možnosti kompilátoru byly odebrány. Vizuál C++ už nepodporuje vícevláknovou a staticky propojenou knihovnu CRT.
- Kompilátor implementoval pojmenovanou optimalizaci pro návratovou hodnotu, která je povolena při kompilování `/O1`s `/O2` , (minimalizuje velikost, maximální rychlost `/Og` ), (globální optimalizace) a `/Ox` (úplná optimalizace).
- `/Oa`možnost kompilátoru byla odebrána, ale bude tiše ignorována; Použijte modifikátory `restrict__declspec`nebopro určení způsobu, jakým kompilátor dělá aliasing. `noalias`
- `/Op`možnost kompilátoru byla odebrána. Místo `/fp` toho použijte (určete chování s plovoucí desetinnou čárkou).
- Jazyk OpenMP teď podporuje Visual C++.
- `/openmp`(Povolení podpory OpenMP 2,0) byla přidána možnost kompilátoru.
- `/Ow`možnost kompilátoru se odebrala, ale bezobslužně se ignoruje. Použijte modifikátory `restrict__declspec`nebopro určení způsobu, jakým kompilátor dělá aliasing. `noalias`

### <a name="profile-guided-optimizations"></a>Optimalizace na základě profilu

- `/QI0f`bylo odebráno.
- `/QIfdiv`bylo odebráno.
- `/QIPF_B`(Seznam chyb for B CPU Stepping) byla přidána možnost kompilátoru.
- `/QIPF_C`(Seznam chyb for C CPU Stepping) byla přidána možnost kompilátoru.
- `/QIPF_fr32`(Nepoužívejte horní 96 Registry plovoucí desetinné čárky) byla přidána možnost kompilátoru.
- `/QIPF_noPIC`(Generování kódu závislého na pozici) byla přidána možnost kompilátoru.
- `/QIPF_restrict_plabels`(Za běhu nedošlo k vytvoření funkcí). byla přidána možnost kompilátoru.

### <a name="unicode-support-in-the-compiler-and-linker"></a>Podpora kódování Unicode v kompilátoru a linkeru

- `/vd`(Zakázat posunutí konstrukcí) teď umožňuje použít operátor dynamic_cast na vytvořeném objektu (/VD2).
- `/YX`možnost kompilátoru byla odebrána. Použijte `/Yc` (Vytvořit předkompilovaný hlavičkový soubor) `/Yu` nebo (použijte soubor předkompilované hlavičky) místo toho. Pokud odeberete `/YX` z konfigurací sestavení a nahradíte je bez Nothing, může to vést k rychlejším sestavením.
- `/Zc:forScope`je teď ve výchozím nastavení zapnuté.
- `/Zc:wchar_t`je teď ve výchozím nastavení zapnuté.
- `/Zd`možnost kompilátoru byla odebrána. Informace o ladění se už nepodporují jenom na číslo řádku. Místo `/Zi` toho použijte (viz **/Z7,/Zi,/Zi (formát ladicích informací)** , kde najdete další informace.
- `/Zg`je nyní platný pouze v souborech zdrojového kódu jazyka C a nikoli na C++ souborech zdrojového kódu.
- `/Zx`(Ladění optimalizovaného kódu Itanium) byla přidána možnost kompilátoru.

### <a name="new-language-features"></a>Nové funkce jazyka

- Attributeattribute je teď zastaralá.
- `appdomain__declspec`byl přidán modifikátor.
- `__clrcall`přidala se konvence volání.
- nepoužívané (C++) modifikátor **declspec** nyní umožňuje zadat řetězec, který bude zobrazen v době kompilace, když se uživatel pokusí získat přístup k zastaralým třídám nebo funkcím.
- **dynamic_cast** Operátor má zásadní změny.
- Nativní výčty teď umožňují zadat základní typ.
- `jitintrinsicdeclspec`byl přidán modifikátor.
- `noaliasdeclspec`byl přidán modifikátor.
- `process__declspec`byl přidán modifikátor.
- **abstraktní**, **přepsání**a **zapečetění** jsou platné pro nativní kompilace.
- bylo přidáno klíčové slovo **__restrict** .
- `restrictdeclspec`byl přidán modifikátor.
- **__thiscall** je nyní klíčové slovo.
- klíčové slovo **__unaligned** je nyní dokumentováno.
- **volatile** (C++) má aktualizované chování s ohledem na optimalizace.

### <a name="new-preprocessor-features"></a>Nové funkce preprocesoru

- Bylo přidáno předdefinované makro __CLR_VER.
- V komentáři (CC++/) pragma Now `/MANIFESTDEPENDENCY` se nyní přijímá jako komentář linkeru. Možnost exestr pro komentář je nyní zastaralá.
- `embedded_idl`atribut ( `#import` direktiva) nyní používá volitelný parametr.
- `fenv_access`pragma
- `float_control`pragma
- `fp_contract`pragma
- Globální proměnné nebudou inicializovány v pořadí, ve kterém jsou deklarovány, pokud máte globální proměnné v direktivách pragma managed, unmanaged a unmanaged. Jedná se o potenciální zásadní změnu, pokud je například inicializována nespravované globální proměnné se spravovanými globálními proměnnými a vyžaduje se plně vytvořený spravovaný objekt.
- Oddíly zadané pomocí init_seg jsou teď jen pro čtení, a ne pro čtení a zápis jako v předchozích verzích.
- Výchozí hodnota inline_depth je nyní 16. V jazyce Visual C++ .NET 2003 se projevily také výchozí hodnota 16.
- Předdefinované makro _INTEGRAL_MAX_BITS přidáno, viz Předdefinovaná makra.
- Přidaná Předdefinovaná makra _M_CEE, _M_CEE_PURE a _M_CEE_SAFE naleznete v tématu Předdefinovaná makra.
- Bylo přidáno předdefinované makro _M_IX86_FP.
- Bylo přidáno předdefinované makro _M_X64.
- `make_public`pragma
- `managed`, `unmanaged` syntaxe direktivy pragma se aktualizovala `pop`(teď má `push` a).
- knihovna mscorlib. dll je nyní implicitně odkazována `#using` direktivou ve `/clr` všech kompilacích.
- Bylo přidáno předdefinované makro _OPENMP.
- Direktiva pragma optimize se aktualizovala, a a w už neplatné parametry.
- byl přidán atribut no_registry # import.
- `region`, `endregion` přidány direktivy pragma
- Bylo přidáno předdefinované makro _VC_NODEFAULTLIB.
- Makra variadické jsou nyní implementována.
- `vtordisp`je zastaralá a v budoucí verzi vizuálu C++se odebere.
- `warning` Direktiva pragma nyní obsahuje specifikátor potlačení.

### <a name="new-linker-features"></a>Nové funkce linkeru

- Moduly (výstupní soubory MSIL bez sestavení) jsou teď povolené jako vstup linkeru.
- `/ALLOWISOLATION`(Vyhledávání v manifestu) byla přidána možnost linkeru.
- `/ASSEMBLYRESOURCE`(Vložení spravovaného prostředku) bylo aktualizováno na nyní, aby bylo možné zadat název prostředku v sestavení a určit, zda je prostředek v sestavení privátní.
- `/CLRIMAGETYPE`(Zadejte typ image CLR) možnost linkeru se přidala.
- `/CLRSUPPORTLASTERROR`(Zachovat kód poslední chyby pro volání PInvoke) možnost linkeru byla přidána.
- `/CLRTHREADATTRIBUTE`(Nastavení atributu vlákna modulu CLR) byla přidána možnost linkeru.
- `/CLRUNMANAGEDCODECHECK`(Přidání SuppressUnmanagedCodeSecurityAttribute) možnost linkeru se přidala.
- `/ERRORREPORT`(Nahlásit interní chyby linkeru) možnost linkeru se přidala.
- `/EXETYPE`možnost linkeru byla odebrána. Linker již nepodporuje vytváření ovladačů zařízení s Windows 95 a Windows 98. K vytvoření těchto ovladačů zařízení použijte odpovídající sadu DDK. Klíčové slovo EXETYPE již není platné pro soubory definice modulu.
- `/FUNCTIONPADMIN`(Vytvoření image opravitelnou za provozu) – přidala se možnost linkeru.
- `/LTCG`možnost linkeru je nyní podporována v modulech `/clr`kompilovaných pomocí. `/LTCG`aktualizovala se také podpora optimalizace na základě profilu.
- `/MANIFEST`(Vytvoření manifestu souběžného sestavení) byla přidána možnost linkeru.
- `/MANIFESTDEPENDENCY`(Určete závislosti manifestu) možnost linkeru byla přidána.
- `/MANIFESTFILE`(Název souboru manifestu) byla přidána možnost linkeru.
- `/MAPINFO:LINES`možnost linkeru byla odebrána.
- `/NXCOMPAT`(Kompatibilní s zabráněním spuštění dat) byla přidána možnost linkeru.
- `/PGD`(Zadejte databázi pro optimalizace na základě profilu). byla přidána možnost linkeru.
- `/PROFILE`(Profiler nástrojů pro sledování výkonu) – byla přidána možnost linkeru.
- `/SECTION`(Určete atributy oddílu) možnost linkeru teď podporuje negaci atributu a už nepodporuje atributy L a D (související s ovladačem VxD).
- Podpora kódování Unicode v kompilátoru a linkeru
- `/VERBOSE`(Tisk zpráv o průběhu): možnost linkeru teď taky přijímá bránu ICF a REF.
- `/VXD`možnost linkeru byla odebrána. Linker již nepodporuje vytváření ovladačů zařízení s Windows 95 a Windows 98. K vytvoření těchto ovladačů zařízení použijte odpovídající sadu DDK. Klíčové slovo VXD již není platné pro soubory definice modulu.
- `/WS`možnost linkeru byla odebrána. `/WS`byl použit pro úpravu imagí cílených pro systém Windows NT 4,0. IMAGECFG. exe-R filename lze použít místo `/WS`. IMAGECFG. exe najdete na disku CD-ROM Windows NT 4,0 v SUPPORT\DEBUG\I386\IMAGECFG. Programu.
- `/WX`(Zpracovávání upozornění linkeru jako chyb) je teď dokumentována možnost linkeru.

### <a name="new-linker-utility-features"></a>Nové funkce nástroje linker

- `/ALLOWISOLATION`byla přidána možnost nástroje Editbin.
- Je odebraný příkaz definičního souboru modulu popisu. Linker již nepodporuje vytváření ovladačů virtuálních zařízení.
- `/ERRORREPORT`byla přidána možnost BSCMAKE. exe, DUMPBIN. exe, nástroje Editbin. exe a lib. exe.
- `/LTCG`byla přidána možnost lib.
- `/NXCOMPAT`byla přidána možnost nástroje Editbin.
- `/RANGE`byla přidána možnost DUMPBIN.
- `/TLS`byla přidána možnost DUMPBIN.
- `/WS`možnost nástroje EDITBIN byla odebrána. `/WS`byl použit pro úpravu imagí cílených pro systém Windows NT 4,0. IMAGECFG. exe-R filename lze použít místo `/WS`. IMAGECFG. exe najdete na disku CD-ROM Windows NT 4,0 v SUPPORT\DEBUG\I386\IMAGECFG. Programu.
- Byla přidána možnost/WX [: NO] lib.

### <a name="new-nmake-features"></a>Nové funkce nástroje NMAKE

- `/ERRORREPORT`byl přidán.
- `/G`byl přidán.
- Předdefinovaná pravidla byla aktualizována.
- Makro $ (MAKE), které je dokumentováno v makrech rekurze, nyní poskytuje úplnou cestu k nástroji NMAKE. exe.

### <a name="new-masm-features"></a>Nové funkce MASM

- Výrazy MASM jsou teď 64 hodnoty bitů. V předchozích verzích MASM výrazy byly 32 hodnoty.
- Instrukce __asm int 3 nyní způsobí, že se funkce zkompiluje do nativního režimu.
- ALIAS (MASM) je nyní zdokumentován.
- `/ERRORREPORT`je přidána možnost ml. exe a ml64. exe.
- . ! Je nyní dokumentován.
- H2INC. exe nebude dodán v jazyce Visual C++ 2005. Pokud potřebujete i nadále používat H2INC, použijte H2INC. exe z předchozí verze vizuálu C++.
- byl přidán operátor IMAGEREL.
- byl přidán operátor HIGH32 –.
- byl přidán operátor LOW32 –.
- ml64. exe je verze MASM pro architekturu x64. Sestaví soubory x64. asm do souborů objektů x64. Jazyk vloženého sestavení není podporován v kompilátoru x64. Pro ml64. exe (x64) se přidaly tyto direktivy MASM:
- .ALLOCSTACK
- .ENDPROLOG
- .PUSHFRAME
- .PUSHREG
- .SAVEREG
- .SAVEXMM128
- . Direktiva PROC se navíc aktualizovala syntaxí jenom pro 64bitovou verzi (SETFRAME).
- Přidala se direktiva MMWORD.
- `/omf`(Možnost příkazového řádku ML. exe) teď `/c`implikuje. Soubor ML. exe nepodporuje propojování objektů formátu OMF.
- Direktiva SEGMENT teď podporuje další atributy.
- byl přidán operátor SECTIONREL –.
- Přidala se direktiva XMMWORD.

### <a name="new-crt-features"></a>Nové funkce CRT

- Byly přidány zabezpečené verze několika funkcí. Tyto funkce zpracovávají chyby lepším způsobem a vysazují přísnější ovládací prvky pro vyrovnávací paměti, aby se předešlo běžným chybám zabezpečení. Nové zabezpečené verze jsou identifikovány příponou **_s** .
- Existující méně zabezpečené verze mnoha funkcí jsou zastaralé. Pokud chcete zakázat upozornění na vyřazení, definujte _CRT_SECURE_NO_WARNINGS.
- Mnoho existujících funkcí nyní ověřuje jejich parametry a vyvolá obslužnou rutinu neplatného parametru, pokud je předán neplatný parametr.
- Mnoho existujících funkcí je nyní `errno` nastaveno na místo, kde předtím.
- Byl přidán `errno_t` typ typedef s typem Integer. `errno_t`se používá vždy, když se návratový typ funkce nebo parametr zabývá kódy chyb `errno`z. `errno_t`nahrazuje `errcode`.
- Funkce závislé na národním prostředí teď mají verze, které místo použití aktuálního národního prostředí přebírají národní prostředí jako parametr. Tyto nové funkce mají příponu **_l** . Bylo přidáno několik nových funkcí pro práci s objekty národního prostředí. Nové funkce zahrnují `_get_current_locale` `_create_locale` a .`_free_locale`
- Přidaly se nové funkce, které podporují uzamykání a odemykání popisovačů souborů.
- `_spawn` Rodina funkcí neresetuje errno na hodnotu nula, stejně jako v předchozích verzích.
- `printf` Verze rodiny funkcí, které umožňují určit pořadí, ve kterém jsou argumenty použity, jsou k dispozici.
- Unicode je teď podporovaný formát textu. Funkce `_open` podporuje atributy _O_TEXTW, _O_UTF8 a _O_UTF16. `fopen` Funkce podporuje metodu "CCS = Encoding", která určuje formát Unicode.
- K dispozici je nová verze knihoven CRT sestavených ve spravovaném kódu (MSIL), která se používá při kompilování `/clr` s možností (modul CLR (Common Language Runtime Compilation)).
- _fileinfo se odebral.
- Výchozí velikost pro `time_t` je nyní 64 bitů, čímž se rozšíří `time_t` rozsah a několik časových funkcí na rok 3000.
- CRT teď podporuje nastavení národního prostředí na základě jednotlivých vláken. Funkce `_configthreadlocale` byla přidána pro podporu této funkce.
- Byly přidány `__control87_2` funkce a,kteréumožňujípřístupkovládacímuslovusplovoucídesetinnoučárkouajejichřízenívprocesorusplovoucídesetinnoučárkoux87iSSE2.`_statusfp2`
- `_mkgmtime` Přidaly `_mkgmtime64` se funkce a, které poskytují podporu pro převod časů (struct tm) na Greenwichský střední čas (GMT).
- Byly provedeny `swprintf` změny v a `vswprintf` , aby lépe vyhovovaly standardu.
- Nový hlavičkový soubor INTRIN. H, poskytuje prototypy pro některé vnitřní funkce.
- `fopen` Funkce teď má atribut N.
- `_open` Funkce teď má atribut _O_NOINHERIT.
- Funkce nyní vrátí INT_MAX a nastaví `errno` ERANGE při přetečení. `atoi` V předchozích verzích bylo nedefinované chování přetečení.
- `printf` Rodina funkcí podporuje výstup v šestnáctkové soustavě s plovoucí desetinnou čárkou, který je implementován podle standardu ANSI C99 pomocí specifikátoru typu formátu% a a% a.
- `printf` Rodina teď podporuje předponu "LL" (dlouhý dlouhý) velikost.
- `_controlfp` Funkce byla optimalizována pro lepší výkon.
- Byly přidány ladicí verze některých funkcí.
- Přidány `_chgsignl` a`_cpysignl` (dlouhé dvojitých verzí).
- Do `_locale_t` tabulky typů byl přidán typ.
- Bylo přidáno `_countof` nové makro makra pro výpočet počtu prvků v poli.
- V každém tématu funkce byla přidána část .NET Framework ekvivalenty.
- Několik řetězcových funkcí nyní má možnost zkrátit řetězce, nikoli neúspěšné, pokud výstupní vyrovnávací paměť je příliš malá. viz **_TRUNCATE**.
- `_set_se_translator`nyní vyžaduje použití `/EHa` možnosti kompilátoru.
- `fpos_t`je nyní **__int64** pod `/Za` (pro kód C) a pokud je __STDC__ nastavena ručně (pro C++ kód). Slouží jako **Struktura**.
- _CRT_DISABLE_PERFCRIT_LOCKS může vylepšit výkon vstupně-výstupních programů v jednom vlákně.
- Názvy POSIX se už nepoužívají, protože mají vyhovující C++ názvy ISO (například `_getch` místo `getch`).
- Nové možnosti propojení soubory. obj jsou k dispozici pro režim Pure.
- `_recalloc`kombinuje funkce `realloc` a `calloc`.

## <a name="whats-new-for-c-in-visual-studio-2003"></a>Co je nového C++ v aplikaci Visual Studio 2003

### <a name="compiler"></a>Přepínač

- Informace o tom, jak spustit spravovaná rozšíření pro C++ aplikaci vytvořenou s kompilátorem aktuální verze v předchozí verzi modulu runtime.
- Spravovaná rozšíření pro C++ Nejčastější dotazy.
- Byl přidán návod, který ukazuje, jak portovat existující nativní aplikaci pro použití spravovaných rozšíření pro C++: Návod: Přenos existující nativní C++ aplikace pro spolupráci s komponentami .NET Framework.
- Nyní můžete vytvořit delegáta pro metodu typu hodnoty.
- Shoda kompilátoru s C++ normou byla výrazně vylepšena pro Visual C++ .NET 2003.
- `/arch`je přidána možnost kompilátoru.
- `/Gf`je zastaralá a bude odebrána v další verzi vizuálu C++.
- `/G7`je přidána možnost kompilátoru.
- Možnost `/GS` kompilátoru byla vylepšena, aby chránila místní proměnné z přímých přetečení vyrovnávací paměti.
- Možnost `/noBool` kompilátoru byla odebrána. Kompilátor nyní umožňuje zobrazení **bool** pouze jako klíčové slovo (a nikoli identifikátor) v souboru C++ zdrojového kódu.
- Typ **Long Long** je nyní k dispozici jako **definice** typu **__int64** . Všimněte si, že v CRT ještě není podporována **dlouhá** doba.
- Možnost `/Zm` kompilátoru teď Určuje limit přidělení paměti předkompilovaných hlaviček.
- _InterlockedCompareExchange vnitřní dokument.
- _InterlockedDecrement vnitřní dokument.
- _InterlockedExchange vnitřní dokument.
- _InterlockedExchangeAdd vnitřní dokument.
- _InterlockedIncrement vnitřní dokument.
- Přidaný vnitřní _ReadWriteBarrier

### <a name="attributes"></a>Atributy

- `implements`atribut je nyní zdokumentován.

### <a name="linker-features"></a>Funkce linkeru

Byly přidány následující přepínače linkeru:

- /ASSEMBLYDEBUG
- /ASSEMBLYLINKRESOURCE
- DELAYSIGN
- /KEYFILE
- /KEYCONTAINER
- /SAFESEH

### <a name="masm"></a>MASM

Okně. Přidala se `/safeseh` direktiva SAFESEH a možnost ml. exe.

## <a name="see-also"></a>Viz také:

[Průvodce přenosem a upgradem Visual C++](visual-cpp-porting-and-upgrading-guide.md)
