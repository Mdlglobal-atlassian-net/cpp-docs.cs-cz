---
title: "Visual C++ Co & č. 39; s novou 2003 až 2015 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: c4afde6f-3d75-40bf-986f-be57e3818e26
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e0e5090bc914648e527f335b261ad7838ad3d0bc
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="visual-c-what39s-new-2003-through-2015"></a>Visual C++ Co & č. 39; s novou 2003 až 2015

Tato stránka obsahuje všechny "Novinky" stránky pro všechny verze aplikace Visual C++ z Visual Studia 2015 zpět na 2003. Tyto informace mají sloužit jako v zájmu usnadnění práce v případě, že může být užitečné při upgradu z předchozích verzí aplikace Visual C++.

**Poznámka:** informace o Visual Studio 2017 najdete v tématu [co je nového pro Visual C++ v aplikaci Visual Studio 2017](../what-s-new-for-visual-cpp-in-visual-studio.md) a [shoda vylepšení v jazyce Visual C++ v aplikaci Visual Studio 2017](../cpp-conformance-improvements-2017.md).

## <a name="whats-new-for-c-in-visual-studio-2015"></a>Co je nového pro jazyk C++ v sadě Visual Studio 2015

V sadě Visual Studio 2015 a novější můžete probíhající vylepšení shoda s kompilátorem prostředí někdy změnit jak kompilátor rozumí existujícím zdrojovém kódu. Pokud k tomu dojde, můžete během sestavení nebo i chování rozdíly v kódu, který dříve vytvořené a došlo ke správnému setkat nové nebo jiné chyby.

 Naštěstí tyto rozdíly mít žádné nebo téměř žádné dopad na většinu vašeho zdrojového kódu a vyřešit tyto rozdíly jsou potřeba zdrojový kód nebo další změny, opravy jsou obvykle malé a jednoduché. Jsme zahrnuli mnoho příklady dříve přijatelné zdrojový kód, který může být nutné změnit *(před)* a opravy a opravte je *(po)*.

 I když tyto rozdíly mohou ovlivnit váš zdrojový kód nebo artefaktů sestavení, neovlivňují binární kompatibilitu mezi jednotlivými aktualizace Visual C++ verze. Další závažné druhu změny, *nejnovější změny* může mít vliv na binární kompatibilitu, ale tyto typy binární kompatibilitu zalomení dojít pouze mezi hlavní verzí aplikace Visual C++. Například mezi Visual C++ 2013 a Visual C++ 2015. Informace o nejnovějších změn, které došlo mezi Visual C++ 2013 a Visual C++ 2015, najdete v části [historie 2003 2015 změn Visual C++](../porting/visual-cpp-change-history-2003-2015.md).

- [Vylepšení shoda v sadě Visual Studio 2015](#VS_RTM)

- [Shoda vylepšení v nástroji Visual Studio 2015 Update 1](#VS_Update1)

- [Shoda vylepšení v nástroji Visual Studio 2015 Update 2](#VS_Update2)

- [Shoda vylepšení v nástroji Visual Studio 2015 Update 3](#VS_Update3)

### <a name="VS_RTM">Vylepšení shoda v sadě Visual Studio 2015</a>

- **Možnost /Zc:forScope-** možnost kompilátoru **/Zc:forScope-** je zastaralá a bude v budoucí verzi odebrána.

   ```output
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release
   ```

   Chcete-li povolit nestandardní kód, který používá cykly proměnné za bod, kde podle standard, že by se nachází mimo obor se obvykle použila možnost. Byla pouze nezbytné při jsou kompilaci s parametrem /Za od bez /Za, použití pro proměnnou smyčky po konci smyčky je vždycky povolená. Pokud vám nezáleží standardy shoda (například pokud není určena pro přenosný na jiné kompilátory kódu), můžete je možnost /Za (nebo nastavte vlastnost zakázat jazyková rozšíření na Ne). Pokud se zajímáte o psaní kódu přenosné, kompatibilní se standardy, by se tak, aby u standardního přesunutím deklaraci takovéto proměnné do bodu mimo smyčky přepište kód.

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

- **Zg – možnost kompilátoru.** Možnost kompilátoru /Zg (Generovat prototypy funkcí) již není k dispozici. Tato možnost kompilátoru byl dříve zastaralé.

- Už spuštěním testů jednotek s C + +/ CLI z příkazového řádku s mstest.exe. Místo toho použijte vstest.console.exe

- **Mutable – klíčové slovo.** `mutable` Specifikátor třídy úložiště je již povolen v místech, kde dříve ho kompilovat bez chyby. Nyní, kompilátor poskytuje chyba C2071 (třída neplatné úložiště). Proměnný specifikátor podle standard, lze použít pouze na názvy členů tříd dat a nelze použít pro názvy deklarovaný const nebo statické a nelze použít k odkazování členů.

   Zvažte například následující kód:

   ```cpp
    struct S {
        mutable int &r;
    };
   ```

   Předchozí verze Visual C++ compiler přijata to, ale teď kompilátor dává k následující chybě:

   ```Output
    error C2071: 'S::r': illegal storage class
   ```

   Chcete-li chybu opravit, odeberte jednoduše redundantní mutable – klíčové slovo.

- **char_16_t a char32_t** už můžete `char16_t` nebo `char32_t` jako aliasy v definici typu, protože tyto typy jsou nyní považovány za předdefinované. Bylo běžné pro uživatele a knihovna autorům zadat `char16_t` a `char32_t` jako aliasy `uint16_t` a `uint32_t`, v uvedeném pořadí.

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

   Aktualizace kódu, odeberte deklarace typedef a dalších identifikátorů, které je v konfliktu s těmito názvy přejmenovat.

- **Parametry šablon bez typu** určité kód, který zahrnuje parametry šablon bez typu je nyní správně kontrolována typ kompatibility při zadat explicitní šablony argumenty. Například následující kód kompilovat bez chyby v předchozích verzích Visual C++.

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

   Aktuální kompilátor správně vrátí chybu, protože se neshoduje typ parametru šablony argumentu šablony (parametr je ukazatel na člena const, ale bez const je funkce f):

   ```Output
    error C2893: Failed to specialize function template 'void S2::f(void)'note: With the following template arguments:note: 'C=S1'note: 'Function=S1::f'
   ```

   Chcete-li vyřešit tuto chybu v kódu, ujistěte se, že typ argumentu šablony používáte odpovídá deklarovaný typ parametr šablony.

- **__declspec(align)** kompilátor už přijímá `__declspec(align)` na funkce. To vždy ignorovat, ale nyní je dojde k chybě kompilátoru.

   ```cpp
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations
   ```

   Chcete-li tento problém vyřešit, odeberte `__declspec(align)` z deklarace funkce. Vzhledem k tomu, že ho měl žádný vliv, odebrat ho nezmění nic.

- **Zpracovávání výjimek v jazyce** existuje několik změn výjimek. Objekty výjimek nejprve musí být kopírovatelná nebo mobilní. Následující kód kompilovat v [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)], ale nejde kompilovat v [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)]:

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

   Problém je, že je konstruktor copy privátní, takže objekt nelze kopírovat, jak se stane při běžném průběhu zpracovávat výjimku. Totéž platí i když je deklarovaná konstruktor copy `explicit`.

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

   Aktualizace kódu, ověřte, že je konstruktor copy pro vaše objekt výjimky veřejné a není určena `explicit`.

   Zachytávání výjimku hodnotou taky vyžaduje výjimka objekt, který má být kopírovatelná. Následující kód kompilovat v [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)], ale nejde kompilovat v [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)]:

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

   Tento problém můžete vyřešit tak, že změníte typ parametru pro `catch` na odkaz.

   ```cpp
    catch(D& d)
    {
    }
   ```

- **Textové literály, za nímž následuje makra** kompilátor teď podporuje uživatelsky definované literály. Textové literály, za nímž následuje makra bez jakékoli použité prázdných znaků v důsledku toho jsou interpretovány jako uživateli definované literály, které může být chyby nebo neočekávané výsledky. Například v předchozí kompilátory následující kód zkompilovat úspěšně:

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

   Kompilátor interpretuje to jako řetězec literálu text "hello" následované makra, která je rozšířena "existuje", a pak se dva textové literály zřetězen do jednoho. V [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)], kompilátor interpretuje jako literál definovaný uživatelem, ale vzhledem k tomu, že neexistuje žádné odpovídající uživatelské literálu _x definované, nabízí k chybě.

   ```cpp
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found
    note: Did you forget a space between the string literal and the prefix of the following string literal?

   ```

   Chcete-li tento problém vyřešit, přidejte mezeru mezi řetězcový literál a makra.

- **Sousední textové literály** podobně jako na předchozí, z důvodu související změny při analýze řetězce, byly přiléhající textové literály (buď široké nebo úzké znak textové literály) bez jakékoli prázdný znak interpretovat jako jeden řetězec zřetězených v předchozí verze Visaul C++. V [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)], je nutné přidat nyní mezery mezi dva řetězce. Například je třeba změnit následující kód:

   ```cpp
    char * str = "abc""def";
   ```

   Stačí přidáte mezeru mezi dva řetězce.

   ```cpp
    char * str = "abc" "def";
   ```

- **Nové umístění a odstranění** změnu byl proveden operátor delete, aby byla v souladu s C ++ 14 standardní. Podrobnosti o změnu standardy najdete na [C++ velikost navrácení](http://isocpp.org/files/papers/n3778.html). Změny přidat formu globální odstranit operátor, který přebírá parametr velikosti. Narušující změně je, že pokud jste dříve používali delete – operátor se stejným podpisem (tak, aby odpovídaly s operátor new umístění), zobrazí se chyba kompilátoru (C2956, který probíhá v okamžiku, kdy nové umístění se používá, protože to je operátor delete pozici v kódu, kde se pokusí identifikovat odpovídající odpovídající kompilátor).

   Funkce `void operator delete(void *, size_t)` byl operátor delete umístění odpovídající nové funkce umístění "void \* new – operátor (size_t –, size_t –)" v C ++ 11. S C ++ 14 velikostí navrácení, tato funkce odstranění je teď *funkce obvykle navrácení* (globální delete – operátor). Standardní vyžaduje, aby pokud použití nové umístění vyhledá odpovídající funkce odstranit a vyhledá funkce obvykle navrácení, program nedůvěryhodný.

   Předpokládejme například, že váš kód definuje nové umístění a odstranění umístění:

   ```cpp
    void * operator new(std::size_t, std::size_t);
    void operator delete(void*, std::size_t) noexcept;

   ```

   K problému dochází kvůli shodu v signatury funkce mezi operátor delete umístění, kterou jste definovali a operátor new globální velikostí odstranit. Zvažte, jestli můžete použít jiného typu než size_t – pro všechny umístění nový a odstranit operátory.  Upozorňujeme, že je typ size_t – typedef kompilátoru závislé; je typedef pro nepodepsané int v jazyce Visual C++. Dobrým řešením je použití Výčtový typ jako je tato:

   ```cpp
    enum class my_type : size_t {};

   ```

   Pak změňte svou definici nové umístění a odstranit tento typ slouží jako druhý argument místo size_t –. Také budete muset aktualizovat volání do umístění nové předat nový typ (například pomocí `static_cast<my_type>` převést z celočíselnou hodnotu) definici nové aktualizace a odstranit zpět přetypovat na typ integer. Nemusíte používat výčet pro tento; Typ třídy s členem size_t – by taky měly fungovat.

   Alternativní řešení je, že může být schopni zcela eliminovat nové umístění. Pokud váš kód používá umístění nového k implementaci fondu paměti, kde argument umístění je velikost na objekt, který přidělené nebo odstraněna, pak velikostí navrácení funkce může být vhodný nahradit vlastní kód vlastní paměti fondu a můžete získat odstranit umístění funkce a právě použít vlastní dva argument delete – operátor místo funkce umístění.

   Pokud nechcete, aby váš kód okamžitou aktualizaci, můžete se vrátit k původní chování pomocí možnosti kompilátoru /Zc:sizedDealloc-. Pokud použijete tuto možnost, odstranění dva argument funkce neexistují a nebude způsobit konflikt s vaší umístění delete – operátor.

- **Union datové členy**

   Data členů sjednocení už můžete mít odkazové typy. Následující kód zkompilovat úspěšně v [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)], ale vytvoří chybu v [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)].

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

   Chcete-li tento problém vyřešit, změňte odkazové typy buď na ukazatel nebo na hodnotu. Změna typu na ukazatel vyžaduje změny v kódu, který používá pole union. Změna kódu na hodnotu změní data uložená v union, který ovlivňuje další pole, protože pole v union typy sdílejí stejnou paměť. V závislosti na velikosti hodnotu se může také změnit velikost sjednocení.

- **Anonymní sjednocení** jsou teď další vyhovující pro standardní. Předchozí verze kompilátoru generovány explicitní konstruktor a destruktor pro anonymní sjednocení. Ty se odstraní [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)].

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

   Předchozí kód generuje následující chybu v [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)]:

   ```cpp
    error C2280: '<unnamed-type-u>::<unnamed-type-u>(void)': attempting to reference a deleted function
    note: compiler has generated '<unnamed-type-u>::<unnamed-type-u>' here
   ```

   Chcete-li vyřešit tento problém, zadejte vlastní definice konstruktor a/nebo destruktor.

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

- **Sjednocení s anonymní struktury** Chcete-li v souladu se standardem, modul runtime chování pro členy anonymní struktury ve sjednoceních změnila. V konstruktoru pro anonymní struktury členy ve spojení se nazývá už implicitně při vytváření této unie.   Destruktor pro členy anonymní struktury sjednocení navíc je už implicitně volána, když sjednocení ocitne mimo rozsah. Vezměte v úvahu následující kód, ve kterém sjednocení U obsahuje strukturu anonymní, který obsahuje člena, který je s názvem struktura S, který má destruktor.

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

   V [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)], v konstruktoru pro S je volána, když se vytvoří sjednocení a destruktor pro S je volána, když je v zásobníku pro funkci f vyčištěna. Ale v [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)], nejsou volá konstruktor a destruktor. Kompilátor poskytuje upozornění o této změně chování.

   ```Output
    warning C4587: 'U::s': behavior change: constructor is no longer implicitly calledwarning C4588: 'U::s': behavior change: destructor is no longer implicitly called
   ```

   Pokud chcete obnovit původní chování, pojmenujte strukturu anonymní. Modul runtime chování anonymní struktury je stejný, bez ohledu na verzi kompilátoru.

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

   Případně zkuste přesun konstruktor a destruktor kód do nové funkce a přidejte volání na tyto funkce z konstruktoru a destruktoru pro sjednocení.

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

- **Šablona řešení** překlad názvů pro šablony byly provedeny změny. V jazyce C++ při zvažování kandidáty pro překlad názvu může být případ, že jeden nebo více názvů v úvahu jako potenciální odpovídá vytváří vytváření instancí šablon neplatný. Tyto neplatné konkretizací obvykle nezpůsobí chyby kompilátoru, zásadu, která se označuje jako sfinae u výrazů (nahrazení selhání je není chyba).

   Nyní pokud sfinae u výrazů vyžaduje kompilátor k vytváření instancí specializace šablony třídy, pak všechny chyby, ke kterým došlo během tohoto procesu jsou chyby kompilátoru. V předchozích verzích by kompilátor ignorovat takové chyby. Zvažte například následující kód:

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

   Pokud kompilujete s aktuální kompilátoru, zobrazí se následující chyba:

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

   Důvodem je, že v místě první volání is_base_of třídy by se ještě nebyl definován.

   V takovém případě je nechcete používat takové typové vlastnosti, dokud byla třída definována. Pokud přesunete definice B a D na začátek souboru kódu, se vyřeší chyby. Pokud definice v soubory hlaviček, zkontrolujte pořadí příkazy include pro soubory hlaviček a ujistěte se, že všechny definice tříd jsou kompilovat, než se používají problematické šablony.

- **Zkopírujte konstruktory** v obou [!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)] a Visual Studio 2015, kompilátor generuje kopírovacího konstruktoru třídy Pokud třídy má konstruktor move definovaný uživatelem, ale žádné uživatelem definované kopírovacího konstruktoru. Dev14 je tento konstruktor implicitně generovaného kopie také označený "= odstranění".

### <a name="VS_Update1">Shoda vylepšení v nástroji Visual Studio 2015 Update 1</a>

- **Privátní virtuální základní třídy a nepřímé dědění** předchozí verze kompilátoru povolené odvozené třídy za účelem zavolejte členské funkce jeho *nepřímo odvozené* `private virtual` základní třídy. Toto chování staré nebyla správná a neodpovídá C++ standard. Kompilátor už akceptuje kód napsaný v tímto způsobem a v důsledku vydá Chyba kompilátoru C2280.

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

  -nebo-

   ```cpp
    class base;  // as above

    class middle: private virtual base {};
    class top: public virtual middle, private virtual bottom {};

    void destroy(top *p)
    {
        delete p;
    }
   ```

- **Přetížený new – operátor a delete – operátor** předchozí verze kompilátoru povolené třetí `operator new` a třetí `operator delete` deklarovat statickou a deklarovat v oborech názvů než globální obor názvů.  Toto chování původního vytvoření riziko, že tento program nebude volání `new` nebo `delete` operátor implementace, která programátorů určený, což vede k bezobslužné chybný modul runtime chování. Kompilátor už akceptuje kód napsaný v tímto způsobem a vydá Chyba kompilátoru C2323 místo.

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

      Additionally, although the compiler doesn't give a specific diagnostic, inline operator new is considered ill-formed.

- **Volání ' operátor *typ*() ' (uživatelem definovaný převod) na typy jiné třídy** předchozí verze kompilátoru povolené ' operátor *typu*(), k volání na typy jiné třídy při tiché ignoruje se. Toto chování staré vytvořit riziko generování tichou chybného kódu, což vede k nepředvídatelným modul runtime chování. Kompilátor už akceptuje kód napsaný v tímto způsobem a vydá Chyba kompilátoru C2228 místo.

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

- **Redundantní typename použity ve specifikátorech typu propracována** předchozí verze kompilátoru povolené `typename` použity ve specifikátorech propracována typu; je sémanticky nesprávný kód napsaný v tímto způsobem. Kompilátor už akceptuje kód napsaný v tímto způsobem a vydá Chyba kompilátoru C3406 místo.

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

- **Zadejte odvození pole ze seznamu inicializátoru** předchozí verze kompilátoru nepodporuje odvození typu polí z inicializátoru seznamu. Kompilátor teď podporuje tato forma odvození typu a, v důsledku toho volání funkce šablon pomocí inicializační seznamy teď může být nejednoznačný nebo jiné přetížení může být zvolena než v předchozích verzích kompilátoru. Chcete-li tyto problémy vyřešit, program musí nyní explicitně zadáte přetížení, které programátorů určený.

   Když toto nové chování způsobí, že rozlišení přetížení vzít v úvahu další candidate, který je vhodný stejně jako na historické candidate, stane se nejednoznačné volání a kompilátor problémy v důsledku chyby kompilátoru C2668.

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

   Když toto nové chování způsobí rozlišení přetížení vzít v úvahu další candidate, který je lepší shodu než historické candidate volání jednoznačně přeloží na nové Candidate způsobí změnu v chování programu, který je pravděpodobně jiná než programátory určena.

   Příklad 2: změňte rozlišení přetížení (před)

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

   Příklad 2: změňte rozlišení přetížení (po)

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

- **Obnovení přepínač příkaz upozornění** A předchozí verze kompilátoru odebrána dříve existující upozornění související s `switch` příkazy; tato upozornění byly obnoveny. Kompilátor teď vystavuje obnovené upozornění a upozornění souvisejících s konkrétní případy (včetně výchozí případ) jsou nyní vystavené na řádek obsahující problematické případu, ne na poslední řádek příkaz switch. Výsledkem je nyní vydávajícího upozornění na různé řádky než v minulosti, upozornění dříve potlačit pomocí `#pragma warning(disable:####)` může potlačit už tak, jak má. K potlačení tato upozornění tak, jak má, může být potřeba přesunout `#pragma warning(disable:####)` direktivy na řádek nad prvním případě potenciálně poškozený. Níže jsou uvedeny obnovené upozornění.

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

   Příklady obnovené upozornění jsou uvedeny v jejich dokumentaci.

- **#include: použití nadřazený adresář specifikátor '..' v názvu cesty** (ovlivňuje pouze /Wall wdn)

     Předchozí verze kompilátoru se nepodařilo rozpoznat použití nadřazený adresář specifikátor '..' v názvu cesty z `#include` direktivy. Kód napsaný v tímto způsobem se má obvykle patří hlavičky, které existují mimo projekt nesprávně pomocí projektu relativní cesty. Toto chování staré vytvořit riziko, že program může být zkompilovány zahrnutím soubor jiný zdroj než programátorů určený nebo že tyto relativní cesty nebude přenosné do dalších prostředí sestavení. Kompilátor nyní zjistí a upozorní programátorů kód napsaný v tímto způsobem a problémy volitelné kompilátoru upozornění C4464, pokud je povoleno.

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

   Kromě toho, přestože kompilátor není poskytnuta konkrétní Diagnostika, také doporučujeme specifikátor nadřazený adresář "..." má poznámka použít k určení adresáře souborů k zahrnutí vašeho projektu.

- **#pragma optimize() přesahuje za konec souboru záhlaví** (ovlivňuje pouze /Wall wdn)

   Předchozí verze kompilátoru se nepodařilo rozpoznat změny nastavení příznaku optimalizace, které řídicí soubor hlaviček, který je zahrnutý v rámci překladu jednotky. Kompilátor nyní zjistí a upozorní programátorů kód napsaný v tímto způsobem a problémy volitelné kompilátoru upozornění C4426 v umístění je problematický `#include`, pokud je povoleno. Pokud změny konflikt s příznaky optimalizace nastavuje argumentů příkazového řádku pro kompilátor se pouze objeví toto upozornění.

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

- **Neshoda #pragma warning(push)** a **#pragma warning(pop)** (ovlivňuje pouze /Wall wdn)

   Předchozí verze kompilátoru se nepodařilo rozpoznat `#pragma warning(push)` stav se změní se spárovaný s `#pragma warning(pop)` stavu změny v souboru jiný zdroj, který je určený jen zřídka. Toto chování staré vytvoří riziko, který program by kompilovat s jinou sadu upozornění povoleno než programátorů určený, což může způsobit tichou chybný modul runtime chování. Kompilátor nyní zjistí a upozorní programátorů kód napsaný v tímto způsobem a problémy volitelné kompilátoru upozornění C5031 v umístění odpovídajících `#pragma warning(pop)`, pokud je povoleno. Toto upozornění zahrnuje Poznámka odkazující na umístění odpovídající warning(push) #pragma.

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

   Když neobvyklé, je někdy úmyslné kód napsaný v tímto způsobem. Kód napsaný v tímto způsobem je citlivé na změny v `#include` pořadí; Pokud je to možné, doporučujeme, že soubory zdrojového kódu spravovat stav varování nezávislý způsobem.

- **Neodpovídající #pragma warning(push)** (ovlivňuje pouze /Wall wdn) předchozí verze kompilátoru se nepodařilo rozpoznat neodpovídající `#pragma warning(push)` změny na konci jednotce překlad stavu. Kompilátor nyní zjistí a upozorní programátorů kód napsaný v tímto způsobem a problémy volitelné kompilátoru upozornění C5032 v umístění neodpovídající #pragma warning(push), pokud je povoleno. Pokud nejsou žádné chyby kompilace v jednotce překlad se pouze objeví toto upozornění.

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

- **Další upozornění může být vydaný v důsledku sledování stavu s varováním vylepšené #pragma** předchozí verze kompilátoru sledovat #pragma upozornění změny stavu nedostatečně i pro problém vše určená upozornění. Toto chování vytvořit riziko určitá upozornění by efektivně potlačit v situacích, které se liší od programátorů určena. Kompilátor nyní sleduje stav varování #pragma více robustní – zejména související s #pragma upozornění změny stavu v rámci šablony – a volitelně vydá nové upozornění C5031 a C5032, které pomohou najít nezamýšleným používá programátorů`#pragma warning(push)` a `#pragma warning(pop)`.

   V důsledku vylepšené #pragma může být nyní objeví upozornění sledování, upozornění dříve nesprávně Potlačené a upozornění souvisejících s problémy dříve misdiagnosed změny stavu.

- **Vylepšené identifikace nedostupný kódu** změny standardní knihovna C++ a vylepšená možnost volání vnořené funkce porovnání s předchozími verzemi kompilátoru může povolit kompilátoru k prokázání, určitý kód je nyní nedostupný. Toto nové chování může mít za následek nové a další často vydané instancí upozornění C4720.

   ```Output
    warning C4720: unreachable code
   ```

   V mnoha případech toto upozornění se objevit pouze při kompilaci s povolenými optimalizacemi, od optimalizace může vložené více volání funkce, odstranit redundantní kódu nebo v opačném případě zkontrolujte možné určit, že určité kód nedosažitelný. Jsme zaznamenali, že se nové instance třídy upozornění C4720 došlo často v try/catch – bloky, zejména ve vztahu k použití [std::find](assetId:///std::find?qualifyHint=False&autoUpgrade=True).

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

### <a name="VS_Update2">Shoda vylepšení v nástroji Visual Studio 2015 Update 2</a>

- **Další upozornění a chyby může být vydaný v důsledku částečné podporu pro výraz sfinae u výrazů** předchozí verze kompilátoru analyzovat určité druhy výrazů uvnitř `decltype` specifikátory z důvodu nedostatku podpory pro výraz. SFINAE U VÝRAZŮ. Toto chování staré nebyla správná a neodpovídá C++ standard. Kompilátor teď analyzuje tyto výrazy a částečné podporu pro výraz sfinae u výrazů z důvodu vylepšení probíhající shoda. V důsledku toho nyní vydá upozornění a chyby nalezené ve výrazech, že předchozí verze kompilátoru není analyzovat.

   Když toto nové chování analyzuje `decltype` výraz, který zahrnuje typ, který nebyl ještě deklarován, kompilátor problémy v důsledku chyby kompilátoru C2039.

   ```Output
    error C2039: 'type': is not a member of '`global namespace''
   ```

   Příklad 1: použití nedeklarované typu (před)

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

   Když toto nové chování analyzuje `decltype` výraz, který chybí nezbytné použití `typename` – klíčové slovo k určení, zda je závislé název typu, kompilátor vydá upozornění C4346 společně s chyba kompilátoru C2923 kompilátoru.

   ```Output
    warning C4346: 'S2<T>::Type': dependent name is not a type
   ```

   ```Output
    error C2923: 's1': 'S2<T>::Type' is not a valid template type argument for parameter 'T'
   ```

   Příklad 2: závislé název není typu (před)

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

- `volatile` **Členské proměnné zabránit implicitně definované konstruktory a operátory přiřazení** předchozí verze kompilátoru povolené třídy, která má `volatile` členské proměnné tak, aby měl výchozí konstruktory kopírování nebo přesunutí a výchozí kopírování či přesunutí operátory přiřazení automaticky generovány. Toto chování staré nebyla správná a neodpovídá C++ standard. Kompilátor nyní brány v úvahu třídy, která má volatile členské proměnné tak, aby měl netriviální vytváření a operátory přiřazení, která brání automaticky generován výchozí implementace těchto operátorů.  Když tyto třídy je členem sjednocení (nebo anonymní sjednocení uvnitř třídu), zkopírovat nebo přesunout konstruktory a operátory přiřazení pro kopírování nebo přesunutí sjednocení (nebo třída obsahující sjednocení unonymous) budou implicitně definovány odstranit. Probíhá pokus o vytvoření nebo zkopírujte sjednocení (nebo třída obsahující anonymní sjednocení) bez nutnosti explicitně definovat je je chybu a Chyba kompilátoru problémy kompilátoru C2280 v důsledku.

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

- **Statické členské funkce nepodporují kvalifikátory odchylka nákladů.** Předchozí verze Visual C++ 2015 povoleno statické členské funkce tak, aby měl kvalifikátory odchylka nákladů. Toto chování je z důvodu regrese v Visual C++ 2015 a Visual C++ 2015 Update 1; Visual C++ 2013 a předchozích verzích Visual C++ odmítnout kód napsaný v tímto způsobem. Chování Visual C++ 2015 a Visual C++ 2015 Update 1 není správná a neodpovídá standardní C++.  Visual Studio 2015 Update 2 odmítne kód napsaný v tímto způsobem a vydá Chyba kompilátoru C2511 místo.

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

- **Předat dál deklarace výčtu není povolen v kódu WinRT** (/ZW ovlivňuje pouze) kód zkompilovat pro prostředí Windows Runtime (WinRT) neumožňuje `enum` typy dál deklarovat, podobně jako při kompilaci spravovaného kódu C++ pro rozhraní .net Framework pomocí přepínače kompilátoru/CLR. Toto chování se zajistí, že velikost výčet je vždy známé a může být správně promítá do systému typu WinRT. Kompilátor odmítne kód napsaný v tímto způsobem a vydá Chyba kompilátoru C2599 společně s chyba kompilátoru C3197.

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

- **Přetížené třetí new – operátor a delete – operátor nemusí být deklarován vložené** (úroveň 1 (/ W1) na výchozím) předchozí verze kompilátoru nevydávají upozornění new – operátor třetí a operátor delete funkce jsou deklarovány vložené . Kód napsaný v tímto způsobem je nesprávně naformátován (nejsou potřeba žádné diagnostiky) a může způsobit paměti problémy vyplývající z nové Neshoda a odstranit operátory (zejména při použití společně s velikostí navrácení), které může být obtížné diagnostikovat.   Kompilátor nyní vydává kompilátoru upozornění C4595 k identifikaci kódu napsaného tímto způsobem.

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

   Opravě kód, který je zapsaný tímto způsobem může vyžadovat, aby definice operátor přesunout mimo soubor hlaviček a do odpovídající zdrojový soubor.

### <a name="VS_Update3">Shoda vylepšení v nástroji Visual Studio 2015 Update 3</a>

- **std::is_convertable nyní rozpozná vlastní přiřazení** (standardní knihovna) předchozí verze `std::is_convertable` typ znak se nepodařilo rozpoznat správně vlastní přiřazení typu třídy, když se odstraní. jeho kopie konstruktoru nebo privátní. Nyní `std::is_convertable<>::value` je správně nastavena na `false` při použití typu třídy s odstraněný nebo soukromý kopírovacího konstruktoru.

   Neexistuje žádné diagnostické kompilátoru přidružené k této změně.

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

   V předchozích verzích Visual C++, statické kontrolní výrazy v dolní části v tomto příkladu předat protože `std::is_convertable<>::value` nebyl správně nastaven `true`. Nyní `std::is_convertable<>::value` je správně nastavena na `false`, způsobuje statické kontrolní výrazy k selhání.

- **Uvedena odstranění trivial kopírování nebo přesunutí konstruktory respektují specifikátory přístupu** předchozí verze kompilátoru není zkontrolujte specifikátor přístupu uvedena nebo odstraněné trivial kopie a přesunout konstruktory před povolením, která se má volat. Toto chování staré nebyla správná a neodpovídá C++ standard. V některých případech toto chování staré vytvořit riziko generování tichou chybného kódu, což vede k nepředvídatelným modul runtime chování. Kompilátor nyní zkontroluje přístup specifikátor uvedena nebo odstraněné trivial kopie a přesunout konstruktory k určení, zda může být volána a pokud ne, kompilátoru problémy v důsledku upozornění C2248.

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

- **S atributy podpory kódu ATL** (úroveň 1 (/ W1) na výchozím) kódu ATL s atributy předchozí verze kompilátoru podporována. Jako další fáze odebrání podporu pro knihovny ATL s atributy kód, který [začal ve Visual C++ 2008](https://msdn.microsoft.com/library/bb384632\(v=vs.90\).aspx), s atributy ATL kód je zastaralá. Kompilátor nyní vydává kompilátoru upozornění C4467 k identifikaci tento druh nepoužívané kódu.

   ```Output
    warning C4467: Usage of ATL attributes is deprecated
   ```

   Pokud chcete pokračovat, dokud odebrala se podpora z kompilátoru použití kódu ATL s atributy, můžete toto upozornění zakázat předáním `/Wv:18` nebo `/wd4467` argumenty příkazového řádku pro kompilátor nebo přidáním `#pragma warning(disable:4467)` ve zdrojovém kódu.

   Příklad 1 (před)

   ```cpp
              [uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
    class A {};
   ```

   Příklad 1 (po)

   ```cpp
    __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) A {};

   ```

   Někdy může být nutné nebo chcete vytvořit IDL soubor nepoužívejte zastaralý ATL atributy, jako následující příklad kódu

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

   Nejprve vytvořte soubor *.idl; soubor vc140.idl generované slouží k získání \*.idl souboru, který obsahuje rozhraní a poznámky.

   Dále přidáte krok MIDL buildu a ujistěte se, že jsou generovány definice rozhraní C++.

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

   Potom pomocí knihovny ATL přímo v souboru implementace, jako v příkladu kódu níže.

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

- **Předkompilované soubory hlaviček (PCH) a neshoda # direktivy include** akceptovat (ovlivňuje pouze /Wall wdn) předchozí verze kompilátoru neshoda `#include` direktivy ve zdrojových souborech mezi `-Yc` a `-Yu` kompilace při použití souborů předkompilovaných hlaviček (PCH). Kód napsaný v tímto způsobem je už přijat kompilátoru.   Kompilátor teď problémy kompilátoru upozornění CC4598 k identifikaci neshoda `#include` direktivy při použití souborů PCH.

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

- **Předkompilované soubory hlaviček (PCH) a neshoda adresáře souborů k zahrnutí** adresář include (ovlivňuje pouze /Wall wdn) předchozí verze kompilátoru přijata neshoda (`-I`) argumenty příkazového řádku pro kompilátor mezi `-Yc`a `-Yu` kompilace při použití předkompilovaných hlaviček (PCH) souborů. Kód napsaný v tímto způsobem je už přijat kompilátoru.   Kompilátor teď problémy kompilátoru upozornění CC4599 k identifikaci neshoda adresář include (`-I`) argumenty příkazového řádku při použití souborů PCH.

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

## <a name="whats-new-for-c-in-visual-studio-2013"></a>Co je nového pro jazyk C++ v sadě Visual Studio 2013

### <a name="improved-iso-cc-standards-support"></a>Podpora standardy ISO vylepšené C/C++

#### <a name="compiler"></a>Kompilátoru

Microsoft Visual C++ compiler podporuje tyto ISO funkce C ++ 11 jazyka:

- Výchozí šablony argumenty pro šablony funkce.
- Delegování konstruktorů
- Operátory explicitního převodu.
- Inicializační seznamy a jednotná inicializace.
- Nezpracovaný řetězec literály.
- Variadické šablony.
- Alias šablony.
- Odstraněné funkce.
- Data nestatické členské inicializátory (NSDMIs).
- Uvedena funkce. *
- Podporuje tyto funkce jazyka ISO C99:
- _Bool
- Složené literály.
- Určené inicializátory.
- Kombinování deklarace s kódem.
- Řetězec literálu převod upravitelnými hodnoty můžete nepovolené pomocí nové možnosti kompilátoru **/Zc: strictstrings**. C ++ 98, převod textové literály typu char\* (a celý textové literály na wchar_t\*) se považovat za zastaralou. Převod C ++ 11, byla odebrána úplně. I když kompilátor může výhradně v souladu s standardní, místo toho poskytuje **/Zc: strictstrings** možnost, abyste mohli řídit převod. Ve výchozím nastavení je možnost je vypnuta. Všimněte si, že při použití této možnosti v režimu ladění, nebude kompilace STL.
- deklarátor/lvalue odkaz přetypování. S odkazy rvalue C ++ 11 můžete od sebe jasně odlišit hodnoty lvalue a rvalue. Dříve kompilátor neposkytnul to ve scénářích konkrétní přetypování. Nová možnost kompilátoru **/Zc: rvaluecast**, byl přidán do zkontrolujte kompilátoru shoduje s Paper(see section 5.4, [expr.cast]/1) práce jazyka C++. Výchozí chování, pokud není tato možnost zadána, je stejné jako v sadě Visual Studio 2012.
  - Poznámka: pro uvedena funkce, pomocí = výchozí žádosti o přesunutí memberwise konstruktory a přesuňte operátory přiřazení není podporován.

### <a name="c99-libraries"></a>C99 knihovny

Deklarace a implementace jsou přidány k chybějící funkcí v těchto hlavičky: math.h, ctype.h, wctype.h, stdio.h, stdlib.h a wchar.h. Přidáno také jsou nové hlavičky complex.h, stdbool.h fenv.h a inttypes.h implementace a pro všechny funkce, které jsou deklarované v nich. Neexistují nové hlavičky obálku C++ (ccomplex, cfenv, cinttypes, ctgmath) a počet jiné jsou aktualizovány (ccomplex, cctype –, clocale –, cmath –, cstdint, cstdio –, cstring, cwchar – a cwctype –).

### <a name="standard-template-library"></a>Standardní šablona knihovny

Podpora pro C ++ 11 operátory explicitního převodu, inicializační seznamy, vymezená výčty a variadické šablony.
Všechny kontejnery teď podporují C ++ 11 podrobných element požadavky.
Podpora pro tyto funkce C ++ 14:

- "Transparentní operátor functors" méně <>, větší <> a <>, vynásobí <> a tak dále.
- make_unique<T>(argumentů...) a make_unique < T [] > (ne)
- cbegin()/cend(), rbegin()/rend() a crbegin()/crend() třetí funkce.
- \<Atomic > přijata řada vylepšení výkonu.
- \<type_traits > přijatých hlavních ustálení a kód opravy.

### <a name="breaking-changes"></a>Nejnovější změny

Tato vylepšená podpora pro standardy ISO C/C++ může vyžadovat změny existujícího kódu tak, aby vyhovuje C ++ 11 a zkompiluje správně v jazyce Visual C++ v sadě Visual Studio 2013.

### <a name="visual-c-library-enhancements"></a>Vylepšení knihovna jazyka Visual C++

- C++ REST SDK je přidána. Má moderní implementace C++ služby REST.
- Podpora C++ AMP Texture je lepší. Teď zahrnuje podporu mipmaps a nové režimy vzorkování.
- Úlohy PPL podporovat více plánování technologie a asynchronní ladění. Nová rozhraní API umožňují vytvářet PPL úloh pro normální výsledky a podmínek výjimek.

### <a name="c-application-performance"></a>Výkon aplikace C++

- Automatickou vektorizací nyní rozpozná a optimalizuje další vzorů C++ pro rychlejší běh kódu.
- Platforma ARM a vylepšení kvality kódu micro architektura Atom.
- konvence volání __vectorcall je přidána. Předání argumentů typu vektoru pomocí konvence volání __vectorcall používat vektoru Registry.
- Nové možnosti Linkeru. /Gw (kompilátor) a přepínače /Gy (assembler) umožňují linkeru optimalizace k vytvoření zeštíhlen binární soubory.
- C++ AMP sdílené paměti podporu, aby omezit nebo odstranit data kopírování souborů mezi procesoru a GPU.

### <a name="profile-guided-optimization-pgo-enhancements"></a>Vylepšení profil na základě optimalizace (PGO)

- Vylepšení výkonu z snížení pracovní sadu aplikací, které jsou optimalizovány s použitím PGO.
- Vývoj aplikací pro nové PGO pro prostředí Windows Runtime

### <a name="windows-runtime-app-development-support"></a>Podpora prostředí Windows Runtime vývoj aplikací

- **Podpora pro do pole typů v hodnota struktury.** Nyní můžete určit typy hodnot s použitím pole, která může mít hodnotu null, například IBox\<int > ^ oproti int. To znamená, že pole můžete buď mít hodnotu, nebo být roven nullptr.
- **Širší informace o výjimce.** C + +/ CX podporuje nový model chyby systému Windows, který umožňuje zaznamenat a šíření bohaté výjimka informace napříč binární rozhraní aplikace (ABI); To zahrnuje zásobníky volání a vlastní zprávu řetězce.
- **Teď je virtuální objekt:: ToString().** Nyní můžete přepsat ToString v uživatelem definované typy ref prostředí Windows Runtime.
- **Podpora pro zastaralé rozhraní API.** Veřejné rozhraní API systému Windows Runtime můžete nyní označeny jako zastaralé a mají vlastní zprávu, která se zobrazí jako upozornění sestavení a může poskytnout pokyny pro migraci.
- Ladicí program vylepšení. Podpora pro nativní/JavaScript spolupráce ladění, prostředí Windows Runtime výjimka diagnostiky a kód asynchronní ladění (prostředí Windows Runtime a PPL).
  - Poznámka: Kromě C++ specifické funkce a vylepšení, které jsou popsané v této části, další vylepšení v sadě Visual Studio také můžete zapsat lepší aplikace Windows Runtime.

### <a name="diagnostics-enhancements"></a>Vylepšení diagnostiky

- Ladicí program vylepšení. Podpora pro asynchronní ladění, trasování a ladění pouze můj kód.
- Code Analysis kategorií. Teď si můžete zobrazit seřazený podle kategorií výstup z analyzátor kódu můžete najít a opravit závad v kódu.
- Diagnostika XAML. Nyní lze diagnostikovat odezvy uživatelského rozhraní a spotřeba energie problémy ve vašem XAML.
- Grafika a GPU ladění vylepšení.
- Vzdálené záznam a přehrávání na skutečné zařízení.
- Souběžné C++ AMP a ladění procesoru.
- Vylepšené diagnostiky C++ AMP modulu runtime.
- HLSL výpočetní shaderu trasování ladění.

### <a name="3-d-graphics-enhancements"></a>Vylepšení 3D grafiky

- Podpora obsahu kanálu Image pro platformu alpha předem vynásobená DDS formátu.
- Editor obrázků používá interně předem vynásobená alpha pro vykreslování a tím zabraňuje vykreslování artefaktů, jako jsou tmavý olemování.
- Bitové kopie a editory modelu. Vytvoření vlastní filtr se teď podporuje v Návrháři shaderu v editoru obrázků a Editor pro Model.

### <a name="ide-and-productivity"></a>IDE a produktivita

**Vylepšené formátování kódu**. Můžete provést další nastavení formátování kódu C++. Pomocí těchto nastavení můžete řídit umístění nového řádku složené závorky a klíčová slova, odsazení, mezery a zalomení řádku. Kód je naformátován automaticky po dokončení příkazů a blocích a vložte kód do souboru.

**Dokončení závorek.** C++ – kód nyní automaticky dokončuje koncových znaků, které odpovídají tyto otevírání znaky:

- {{(složené závorky)
- [(hranatá závorka)
- ((závorek).
- ' (jednoduchou uvozovku)
- "(uvozovky)

**Další automatické dokončování C++ funkce.**

- Přidá středník pro typy tříd.
- Dokončení závorkách pro literály Nezpracovaný řetězec.
- Dokončení Víceřádkový komentáře (/ * * /)

**Najít všechny odkazy** nyní automaticky vyřeší a filtry odkazy na pozadí, jakmile se zobrazí seznam textovou odpovídá.

**Na základě kontextu člen filtrování seznamu.** Nedostupné členové jsou filtrovány mimo seznamech členů IntelliSense. Například se nezobrazí soukromé členy v seznamu členů, pokud měníte kód, který implementuje typu. Seznam členů je otevřen, můžete stisknout Ctrl + J jednu úroveň filtrování (platí pouze pro aktuální okno Přehled člen). Stiskem kláves Ctrl + J znovu a odeberte textovou filtrování a zobrazení všech členů.

**Parametr Nápověda posouvání.** Podpis zobrazit funkce v popisu parametru help teď změny podle počtu parametry, které jste zadali ve skutečnosti, nikoli právě zobrazující libovolný podpisu a nebude se aktualizovat ji na základě aktuálního kontextu. Parametr nápovědy také funguje správně, který se zobrazí na vnořené funkce.

**Přepnutí soubor hlavičky nebo kódu.** Pomocí příkazu v místní nabídce nebo klávesové zkratky se může nyní přepínat mezi hlavičku a jeho odpovídající soubor kódu.

**S možností změny velikosti projektu C++ vlastnosti – okno**

**Automatické generování kód obslužné rutiny událostí v jazyce C + +/ CX a C + +/ CLI.**  Při psaní kódu pro přidání obslužné rutiny událostí v jazyce C + +/ CX nebo C + +/ CLI souboru kódu, editoru může automaticky generovat definici delegáta instance a obslužných rutin událostí. Popisek okno se zobrazí, když kód obslužné rutiny události může být automaticky generovaný.

**Vylepšení sledování DPI.** Nastavení DPI sledování pro soubory manifestu aplikace teď podporuje nastavení "Za monitorování vysokou DPI vědět".

**Rychlejší přepnutí konfigurace.** Pro velké aplikace přepínání konfigurace – zejména následné přepnutí operace – spuštění mnohem rychlejší.

**Sestavení čas efektivitu.** Řada optimalizace a využití vícejádrových rychleji sestavení, zejména u velkých projektů. Přírůstková sestavení C++ aplikací, které odkazují na C++ WinMD jsou také mnohem rychlejší.

## <a name="whats-new-for-c-in-visual-studio-2012"></a>Co je nového pro jazyk C++ v sadě Visual Studio 2012

### <a name="improved-c11-standards-support"></a>Vylepšené C ++ 11 standardy podporu

#### <a name="standard-template-library"></a>Standardní šablona knihovny

- Podpora pro záhlaví nového STL: \<atomic >, \<typu chrono >, \<condition_variable >, \<filesystem >, \<budoucí >, \<mutex >, \<poměr >, a \< vlákno >.
- Chcete-li optimalizovat využití prostředků paměti, jsou nyní kontejnery menší. Například v x86 vydání režimu s výchozím nastavením, std::vector má zmenšit z 16 bajtů v sadě Visual Studio 2010, 12 bajtů v sadě Visual Studio 2012 a std::map má zmenšit z 16 bajtů v sadě Visual Studio 2010 na 8 bajtů v sadě Visual Studio 2012.
- Jak je povoleno, ale není požadováno standardem C ++ 11 je implementovaná STRACH iterátory.

#### <a name="other-c11-enhancements"></a>Další C ++ 11 vylepšení

- Na základě rozsahu pro smyčky. Můžete napsat robustnější cykly, které pracují se pole, STL – kontejnery a prostředí Windows Runtime kolekce ve formuláři pro (deklarace pro rozsah: výraz). Toto je část základní jazyková podpora.
- Bezstavové lambdas, které jsou bloky kódu, které začínají [] prázdný lambda představení a zachycení žádné místní proměnné, jsou nyní implicitně převést na ukazatele na funkce potřeby C ++ 11 Standard.
- Vymezená výčty podporovat. Enum – klíč třídy výčtu C++ se teď podporuje. Následující kód ukazuje, jak se liší od předchozí chování výčtu tento klíč výčtu.

   ```cpp
enum class Element { Hydrogen, Helium, Lithium, Beryllium };
void func1(Element e);
func1(Hydrogen); // error C2065: 'Hydrogen' : undeclared identifier
func1(Element::Helium); // OK
   ```

### <a name="windows-runtime-app-development-support"></a>Podpora prostředí Windows Runtime vývoj aplikací

- **Nativní založených na XAML uživatelského rozhraní modelu**. Pro aplikace Windows Runtime můžete použít nový model nativní založených na XAML uživatelského rozhraní.
- **Visual C++ Component Extensions**. Tato rozšíření zjednodušit používání prostředí Windows Runtime objekty, které jsou nezbytné součástí aplikace Windows Runtime. Další informace najdete v tématu [plán pro prostředí Windows Runtime aplikací C++ pomocí](../windows/universal-windows-apps-cpp.md) a [referenční příručka jazyka Visual C++ (C + +/ CX)](../cppcx/visual-c-language-reference-c-cx.md)
- **Hry DirectX**. Nestačí, aby hry můžete vyvíjet pomocí nové rozhraní DirectX podporu pro aplikace Windows Runtime.
- **Zprostředkovatel komunikace s objekty jazyka XAML a rozhraní DirectX**. Prostředí Windows Runtime aplikace, které používají XAML a DirectX teď spolupracovat efektivně.
- **Vývoj pro Windows Runtime součást DLL**. Součást knihovny DLL vývoj díky prostředí Windows Runtime extensible.

### <a name="compiler-and-linker"></a>Kompilátoru a Linkeru

- **Automatickou vektorizací**. Kompilátor analyzuje smyčky v kódu a kde je to možné, vydá pokyny, které používají vektoru zaregistruje a pokyny, které jsou součástí všechny moderní procesory. Díky tomu smyčky pracovat rychleji. (Procesor pokyny jsou označovány jako SSE, pro Streaming SIMD Extensions). Není nutné k povolení nebo požadavek optimalizace, protože se automaticky použije.
- **Automatickou vektorizací**. Kompilátor analyzovat smyčky v kódu a emitování pokyny, které šíří výpočty mezi více jader nebo procesorů. To můžete provést smyčky pracovat rychleji. Tato optimalizace musí požadavek, protože není ve výchozím nastavení povolené. V mnoha případech je užitečné zahrnout #pragma loop(hint_parallel(N)) kód bezprostředně před cykly, které chcete parallelized.
- Automatickou vektorizací a automatickou vektorizací vzájemně spolupracují, aby výpočty se šíří mezi více jader a kód na každý základní používá jeho vektoru Registry.

### <a name="new-in-visual-studio-2012-update-1"></a>Ve Visual Studio 2012 Update 1

Cíle Windows XP se při sestavování kódu C++.
Můžete použít – kompilátor Visual C++ a knihovny do cílového systému Windows XP a Windows Server 2003.

#### <a name="parallel-programming-support"></a>Podpora paralelní programování

##### <a name="c-accelerated-massive-parallelism-amp"></a>C++ Accelerated Massive Parallelism (AMP)

C++ AMP zrychluje provádění kódu C++ a využívají data paralelní hardware, který je obvykle přítomen jako grafický procesor na diskrétní grafické karty. Programovací model C++ AMP zahrnuje vícerozměrná pole, indexování, přenos paměti, dlaždice a knihovnu matematické funkce. Pomocí rozšíření jazyka C++ AMP a omezení kompilátoru můžete řídit způsob přesunutí dat z procesoru na grafický procesor a zpět.

**Ladění.** Ladění prostředí pro aplikace, které používají C++ AMP cílit na grafický procesor je stejně jako ladění pro jiné aplikace C++. To zahrnuje novou paralelní ladění rozšíření, která měla již bylo zmíněno dříve.

**Profilace.** Nyní je profilace podpora aktivita GPU, který je založen na C++ AMP a ostatní programovací modely na základě Direct3D.

#### <a name="general-parallel-programming-enhancements"></a>Vylepšení obecné paralelní programování

S hardwarem přesunutím do více jader a mnoho základní architektury můžete vývojáři už spoléhají na stále rostoucí rychlosti hodiny z jednoho jádra. Paralelní programování podpory v Concurrency Runtime vývojářům umožňuje využít výhod těchto nových architektur.
V sadě Visual Studio 2010 výkonné paralelizace knihovny jazyka C++ například Parallel Library vzory byly přináší, společně s funkcí vyjadřující kanály toku dat sofistikované umožní plně využít souběžnosti. V sadě Visual Studio 2012 se rozšířily a poskytují lepší výkon, další ovládací prvek a bohatší podporu pro paralelní vzory, vývojáři nutné většinu tyto knihovny. Rozšiřuje nabídky nyní zahrnuje:

- Bohaté založený na úlohách programovací model, který podporuje asynchrony a pokračování.
- Paralelní algoritmy, které podporují připojení k rozvětvení paralelismus (parallel_for –, parallel_for – s spřažení, parallel_for_each –, parallel_sort –, parallel_reduce –, parallel_transform –).
- Bezpečné souběžnosti kontejnerů, které poskytují vláken verze – std datové struktury například priority_queue, fronty, vector a mapy.
- Asynchronní knihovny agentů, který mohou vývojáři express kanály toku dat, které přirozeně rozložit na souběžných jednotky.
- Přizpůsobitelné Plánovač a prostředků manažera usnadňuje smooth složení vzoru v tomto seznamu.

##### <a name="general-parallel-debugging-enhancements"></a>Vylepšení ladění paralelní obecné

Kromě okno paralelních úloh a okna paralelní zásobníky Visual Studio 2012 nabízí nového okna paralelního sledování, takže můžete zkoumat hodnoty výraz ve všech vláken a procesů a provádět, řazení a filtrování na výsledek. Můžete také použít vlastní vizualizérech rozšířit okno a napříč všechna okna nástrojů můžete využít nové podpoře více procesů.

### <a name="ide"></a>IDE – integrované vývojové prostředí

**Šablony sady Visual Studio podporují.** Teď můžete použít technologie šablony sady Visual Studio Autor C++ šablon projektů a položek.

**Asynchronní řešení zatížení.** Projekty jsou nyní načtena asynchronně – klíčovými částmi řešení první – tak, aby můžete začít pracovat rychleji.

**Automatické nasazení pro vzdálené ladění.** Nasazení souborů pro vzdálené ladění v jazyce Visual C++ je jednodušší. Ke vzdálenému počítači možnost nasazení na místní nabídky projektu automaticky zkopíruje soubory, které jsou určené v ladění vlastnosti konfigurace. Ruční kopírování souborů do vzdáleného počítače se už nevyžaduje.

**C++/CLI IntelliSense.** C + +/ CLI nyní má plnou podporu technologie IntelliSense. IntelliSense funkce, jako je rychlé informace, parametr nápovědy, vypsat členy a automatické doplňování teď pracovat pro C + +/ CLI. Kromě toho ostatní IntelliSense a IDE rozšířením uvedené v tomto dokumentu také funkční pro C + +/ CLI.

**Popisy tlačítek bohatší IntelliSense.** Širší dokumentační komentáře XML C++ IntelliSense rychlé informace nyní zobrazit informace o stylu. Pokud používáte rozhraní API z knihovny – například C++ AMP, který má dokumentační komentáře XML a potom popis tlačítka IntelliSense zobrazí další informace než jenom deklarace. Navíc má váš kód dokumentační komentáře XML, popisy tlačítek IntelliSense zobrazí rozsáhlejší informace.

**C++ – kód vytvoří.** Kostru kód je k dispozici pro přepínač if-else, smyčky a jiné základní kód konstrukce, v rozevíracím seznamu vypsat členy. Vyberte část kódu, ze seznamu a vložte ji do vašeho kódu a potom vyplňte požadovaná logiku. Můžete také vytvořit vlastní vlastní částí kódu pro použití v editoru.

**Vylepšení seznamu členů.** Vypsat členy rozevíracím seznamu se zobrazí automaticky při psaní kódu do editoru kódu. Výsledky se filtrují tak, že pouze relevantní členové jsou zobrazeny během psaní. Můžete řídit druh filtrování logiky, která je používána seznam členů – v dialogové okno Možnosti v části textový Editor, C/C++, Upřesnit.

**Sémantické zabarvení.** Typy, výčty, makra a dalších tokenů C++ teď mít zabarvení ve výchozím nastavení.

**Referenční dokumentace zvýraznění.** Výběr symbol nyní označuje všechny instance symbolu v aktuální soubor. Stisknutím kombinace kláves Ctrl + Shift + šipka nahoru nebo Ctrl + Shift + šipka dolů pro přesun mezi zvýrazněné odkazy. Můžete vypnout tato funkce v dialogovém okně Možnosti v části **textový Editor, C/C++, Upřesnit**.

### <a name="application-lifecycle-management-tools"></a>Nástroje pro správu životního cyklu aplikací

#### <a name="static-code-analysis"></a>Statická analýza kódu

Statické analýza pro C++ byl aktualizován zajistit bohatší kontextové informace o chybě, více pravidel analýzy a analýzy lepší výsledky. V novém okně Analýza kódu můžete filtrovat zprávy – klíčové slovo, projekt a závažnosti. Při výběru zprávy v okně zvýrazní se v editoru kódu na řádku kódu, kde byla spuštěna zprávy. Pro určité upozornění C++ zprávu seznam řádků zdroje, které se zobrazí cesta spuštění, který vede k upozornění; jsou vyznačené rozhodovací body a důvody přijetí dané cestě.
Analýza kódu je součástí většině edicí sady Visual Studio 2012. Professional, Premium a Ultimate Edition jsou zahrnuty všechna pravidla. V edicích Express pro Windows 8 a Windows Phone jsou zahrnuty pouze nejdůležitější upozornění. Analýza kódu není součástí edice Express pro Web.
Zde jsou některé další vylepšení pro analýzu kódu:

- Nové upozornění souběžnosti umožňuje vyhnout se chyby souběžnosti tím, že zajistí, že používáte správné uzamčení disciplíně v programy C/C++ s více vlákny. Nástroje analyzer zjišťuje potenciální konflikty časování, zámek pořadí jiného, volající/volaný uzamčení porušení smlouvy, operace neodpovídající synchronizace a jiné chyby souběžnosti.
- Můžete zadat, že že c++ pravidla, kterou chcete použít k code analysis spustí pomocí sady pravidel.
- V okně nástroje Analýza kódu vložíte do zdrojového kódu – Direktiva pragma, který potlačí vybrané upozornění.
- Pomocí nové verze Microsoft zdrojového kódu poznámky language (SAL) k popisu, jak funkce používá jeho parametry předpoklady, že umožňuje o a záruky, které můžete vylepšit přesnosti a úplnosti Statická analýza kódu Díky po jeho dokončení.
- Podpora pro 64bitové projekty C++.

#### <a name="updated-unit-test-framework"></a>Aktualizované Unit Test Framework

Zápis testů částí C++ pomocí nový systém testování částí C++ v sadě Visual Studio. Přidáte nové jednotkové testování projektu do stávajícího řešení pro C++ tím, že šablony projektu testování částí C++ v kategorii Visual C++ v dialogovém okně Nový projekt. Zahájit zápis testů jednotek v generovaného kódu TEST_METHOD kód v souboru Unittest1.cpp. Když dojde k zapsání testovacího kódu, sestavte řešení. Pokud chcete spustit testy, otevřete okno Průzkumníka testů jednotek výběrem zobrazení, ostatní okna Průzkumníka testů jednotek a potom v místní nabídce pro testovací případ chcete, vyberte možnost spustit vybrané test. Po dokončení spuštění testu můžete zobrazit výsledky testů a informace trasování zásobníku další v rámci stejného časového období.

#### <a name="architecture-dependency-graphs"></a>Architektura grafy závislostí

Pro lepší pochopení kódu, teď můžete vygenerovat grafy závislostí pro binární, třídu oboru názvů a zahrnout soubory do řešení. V řádku nabídek zvolte architekturu, Generovat graf závislostí a pak pro řešení nebo pro soubor začlenění ke generování graf závislostí. Po dokončení generování grafu vám umožní zkoumat rozbalením každého uzlu, další závislosti vztahy přesunutím mezi uzly a procházet zdrojový kód tak, že zvolíte Zobrazit obsah v místní nabídce pro uzel. Generovat graf závislostí pro zahrnout soubory v místní nabídce souboru se zdrojovým kódem *.cpp nebo *.h soubor hlaviček, zvolte Generovat grafu zahrnout soubory.

#### <a name="architecture-explorer"></a>Průzkumník architektury

Pomocí Průzkumníku architektura můžete prozkoumat prostředků v řešení C++, projektů nebo soubory. V řádku nabídek zvolte architekturu, Windows, architektura Explorer. Můžete vybrat uzel, který vás zajímá, například zobrazení tříd. V takovém případě se na pravé straně okno nástroje rozšířit seznam obory názvů. Pokud vyberete obor názvů, nový sloupec zobrazuje seznam tříd, struktur a výčty v tomto oboru názvů. Můžete dál prozkoumat tyto prostředky, nebo přejděte zpět na sloupci zcela vlevo spusťte další dotaz. Najdete v části kódu pomocí Průzkumníka architektura najít.

#### <a name="code-coverage"></a>Pokrytí kódu

Pokrytí kódu se aktualizovalo a dynamicky nástrojích binárních souborů za běhu. To snižuje nároky na konfigurace a poskytuje lepší výkon. Může taky shromažďovat data pro pokrytí kódu z testy jednotek pro aplikace C++. Pokud jste vytvořili testování částí C++, můžete zjistit testů ve vašem řešení Průzkumníka testů jednotek. Spouštění testů jednotek a shromažďovat kód vyberte data pro pokrytí jejich, v Průzkumníka testů jednotek, analýza pokrytí kódu. Můžete zkontrolovat výsledky pokrytí kódu v okně Výsledky pokrytí kódu – na řádku nabídek zvolte testovací, Windows, výsledky pokrytí kódu.

## <a name="whats-new-for-c-in-visual-studio-2010"></a>Co je nového pro jazyk C++ v sadě Visual Studio 2010

### <a name="c-compiler-and-linker"></a>Kompilátor C++ a Linkeru

**auto Keyword.** Auto – klíčové slovo má nový účel. Použijte výchozí význam auto – klíčové slovo deklarovat proměnnou, jejichž typ je odvozen z inicializace výrazu v deklaraci proměnné. Možnost/Zc: Auto kompilátoru vyvolá nový nebo předchozí význam auto – klíčové slovo.

**decltype – specifikátor typu.** Specifikátor typu decltype vrátí typ zadaného výrazu. Specifikátor typu decltype použijte v kombinaci s auto – klíčové slovo deklarovat typ, který je komplexní nebo známý pouze kompilátoru. Například pomocí kombinace deklarovat funkce šablony, jejichž návratový typ závisí na typech argumentů šablony. Nebo deklarovat funkci šablony, která volá jinou funkci a vrátí návratový typ volaná funkce.

**Lambda Expressions.** Lambda funkce mají tělo funkce, ale žádný název. Lambda funkce kombinují nejlepší vlastnosti ukazatelů na funkce a objekty funkcí.
Použijte funkci lambda samostatně, jako parametr funkce šablony místo objekt funkce nebo společně s auto – klíčové slovo deklarovat proměnnou jejichž typ je lambda.

**Deklarátor odkazu.** Rvalue – deklarátor odkazu (& &) deklaruje odkaz na rvalue. Umožňuje odkaz rvalue, které používáte, přesuňte sémantiku a ideální předávání zápis efektivnější konstruktory, funkce a šablony.

**static_assert Declaration.** Static_assert deklarace testuje assertion softwaru při kompilaci, na rozdíl od jiných kontrolní mechanismy, které testování v době běhu. Pokud kontrolní výraz selže, kompilace se nezdaří a vydání zadanou chybovou zprávu.

**nullptr a __nullptr klíčová slova.** Kompilátor Visual C++ vám umožní používat nullptr – klíčové slovo s nativním kódem nebo se spravovaným kódem. Nullptr – klíčové slovo označuje, že popisovač objektu, vnitřní ukazatel nebo nativní ukazatel typu neodkazuje na objekt. Kompilátor interpretuje nullptr jako spravovaného kódu, pokud použijete / CLR – možnost kompilátoru a nativní kód, pokud nepoužijete možnost/CLR.
__Nullptr – klíčové slovo specifické pro společnost Microsoft nemá stejný význam jako nullptr, ale se vztahuje pouze na nativní kód. Pokud při kompilaci nativního kódu C/C++ pomocí / CLR – možnost kompilátoru, kompilátor nemůže určit, zda nullptr – klíčové slovo je nativní nebo spravovaný termín. Pokud chcete mít vaším záměrem zrušte pro kompilátor, použijte k určení spravované termín a __nullptr k určení termínu nativním nullptr – klíčové slovo.

**/ Zc: trigraphs – možnost kompilátoru.** Ve výchozím nastavení podpora trigraphs je vypnuta. / Zc: trigraphs kompilátoru možnost použijte k povolení podpory trigraph.
Trigraph se skládá ze dvou po sobě jdoucích otazníky (?) následuje jedinečný třetí znak. Kompilátor nahradí trigraph odpovídající interpunkční znaménko. Například kompilátor nahradí?? = trigraph znakem # (symbol). Použití trigraphs ve zdrojových souborech C, které používají znaková sada, která neobsahuje některé znaky interpunkce.

**Nová možnost optimalizace na základě profilu.** PogoSafeMode je nová možnost optimalizace na základě profilu, který umožňuje určit, jestli se má používat nouzovém režimu nebo rychlého režimu při optimalizaci aplikace. Nouzový režim je bezpečné pro přístup z více vláken, ale je pomalejší než rychlého režimu. Rychlé režim je výchozí chování.

**Nové /clr:nostdlib možnost Common Language Runtime (CLR).** Přidá se nová možnost pro/CLR (kompilace Common Language Runtime). Pokud mají různé verze stejné knihovny, je vydána chyby kompilace. Nová možnost umožňuje vyloučit výchozí knihovny CLR tak, aby váš program můžete použít zadaná verze.

**Nová pragma směrnice detect_mistmatch.** Direktivy detect_mismatch – Direktiva pragma umožňuje umístit značku do vaše soubory, které se porovná na jiné značky, které mají stejný název. Pokud existuje více hodnot pro stejný název, propojovací k chybě.

**Vnitřní funkce XOP, Fma4 a vnitřní objekty LWP.** K podpoře XOP – vnitřní prvky přidány pro Visual Studio 2010 SP1, FMA4 – vnitřní prvky přidány pro Visual Studio 2010 SP1 a přidat LWP vnitřní funkce pro Visual Studio 2010 SP1 procesoru technologie byly přidány nové vnitřní funkce. Použijte __cpuid, __cpuidex k určení, které technologií procesoru jsou podporovány v určitém počítači.

### <a name="visual-c-projects-and-the-build-system"></a>Projekty Visual C++ a systém sestavení

**MSBuild.** Visual C++ řešení a projekty jsou teď integrované pomocí MSBuild.exe, který nahradí VCBuild.exe. MSBuild je stejný nástroj sestavení flexibilní, rozšiřitelný, formátu XML, který je používán jazycích Visual Studio a typy projektů. Z důvodu této změny souborů projektu Visual C++ teď použít formát souboru XML a mají příponu názvu souboru. Soubory projektu Visual C++ z dřívějších verzí sady Visual Studio jsou automaticky převedeny na nový formát souboru.

**Adresáře VC ++.** Nastavení adresáře VC ++ se nyní nachází na dvou místech. Stránky vlastností projektu slouží k nastavení hodnoty na projekt pro adresáře VC ++. Pomocí Správce vlastností a seznamu vlastností pro globální nastavení konfiguračních hodnot pro adresáře VC ++.

**Project-to-Project Dependencies.** V dřívějších verzích byly definované závislostí mezi projekty uložené v souboru řešení. Když tato řešení se převedou na nový formát souboru projektu, závislosti jsou převedeny na odkazy na projekt na projekt. Tato změna může ovlivnit aplikace, protože se koncepty závislostí řešení a odkazy na projekt na projekt se liší.

**Makra a proměnných prostředí.** Nové makro _ITERATOR_DEBUG_LEVEL vyvolá podpora ladění iterátorů. Použití tohoto makra místo starší _SECURE_SCL a _HAS_ITERATOR_DEBUGGING makra.

### <a name="visual-c-libraries"></a>Knihovny jazyka Visual C++

**Concurrency Runtime knihoven.** Rozhraní framework Concurrency Runtime podporuje aplikací a součástí, které běžet současně a je architektura pro programování souběžných aplikací v jazyce Visual C++. Pro podporu programování paralelních aplikací, paralelní vzory knihovny (PPL) poskytuje univerzální kontejnery a algoritmy pro provádění podrobného paralelismu. Knihovna asynchronních agentů poskytuje programovací model na základě objektu actor a zpráva předávání rozhraní pro hrubý toku dat a paralelní zpracování úlohy.

**Standardní knihovna C++.** Následující seznam popisuje mnoho změn, které byly provedeny na standardní knihovna C++.

- Nová funkce rvalue odkaz pro jazyk C++ jsou využívány k implementaci sémantiku přesunutí a ideální předávání pro mnoho funkcí v standardní knihovny šablon. Přesuňte sémantiku a ideální předávání výrazně zlepšit výkon operací, které přidělit nebo přiřadit proměnné nebo parametru.
- Odkazy rvalue se také používají k implementaci nové unique_ptr třídu, která je typu chytré ukazatele bezpečnější než auto_ptr – třída. Unique_ptr – třída je mobilní, ale není kopírovatelná implementuje sémantiku striktní vlastnictví bez ovlivnění zabezpečení a funguje dobře s kontejnery, které jsou odkazy rvalue. Auto_ptr – třída je zastaralá.
- Patnáct nových funkcí, například find_if_not –, copy_if a is_sorted, byly přidány do \<algoritmus > záhlaví.
- V \<paměti > záhlaví, nové funkce make_shared – je vhodné, robustní a efektivní způsob, jak vytvořit sdílený ukazatel na objekt ve stejnou dobu je objekt vytvořený.
- Jednotlivě propojený seznamy jsou podporovány \<forward_list – > záhlaví.
- Cbegin –, cend –, crbegin – a crend – nové funkce člena zadejte const_iterator –, který prochází kontejner nebo předchozí.
- \<System_error – > záhlaví a související šablony podpora zpracování chyby nízké úrovně systému. Členy třídy exception_ptr slouží k přenosu výjimek mezi vlákny.
- \<Codecvt – > záhlaví podporuje převod různých kódování znaků Unicode, jiné kódování.
- \<Alokátorů > záhlaví definuje několik šablon, které pomáhají přidělit a volné bloky paměti pro kontejnery založené na uzlu.
- Existuje řada aktualizací do \<náhodných > záhlaví.

### <a name="microsoft-foundation-class-mfc-library"></a>Knihovny Microsoft Foundation Class (MFC)

**Windows 7 Features.** MFC podporuje mnoho funkcí systému Windows 7, například uživatelské rozhraní (UI) pásu karet, hlavní panel, seznam odkazů, záložkách miniatur, miniaturami, indikátor průběhu, překryvnou ikonu a indexování pro hledání. Protože MFC automaticky podporuje mnoho funkcí systému Windows 7, nemusí mít k úpravě stávající aplikace. Pro podporu dalších funkcí v nové aplikace, použijte Průvodce aplikací MFC k zadání funkce, kterou chcete použít.

**Zvýšení povědomí více touch.** MFC podporuje aplikace, které mají více touch uživatelské rozhraní, například aplikace, které jsou určeny pro operační systém Microsoft Surface. Aplikace s více touch dokáže zpracovat touch zpráv systému Windows a gesto zprávy, které jsou kombinace touch zprávy. Právě registrace vaší aplikace pro dotykové ovládání a gesto události a operační systém bude směrovat více touch události vaší obslužné rutiny událostí.

**Sledování vysokou hodnotou DPI.** Ve výchozím nastavení jsou nyní aplikace MFC vysokým rozlišením DPI. Pokud aplikace je vysokou hodnotou DPI (vysoké bodů na palec) vědět, můžete škálovat operačního systému windows, text a další prvky uživatelského rozhraní pro aktuální rozlišení obrazovky. Tato znamená, že je pravděpodobnější správně rozložená, a není oříznut škálovat bitové kopie nebo pixelován.

**Restartujte správce.** Správce restartování automaticky uloží dokumenty a restartuje aplikace, pokud se neočekávaně ukončí nebo restartuje. Například můžete použít správce restartování spusťte aplikaci po zavření automatické aktualizace. Další informace o tom, jak nakonfigurovat aplikace pomocí Správce restartování najdete v tématu Postupy: Přidání podpory správce restartování.

**Objektu CTaskDialog.** Třídu objektu CTaskDialog lze použít místo okně AfxMessageBox – standardní. Třída objektu CTaskDialog zobrazuje a shromažďuje že informace než standardní zprávou nemá.

#### <a name="safeint-library"></a>SafeInt – knihovna

Nové knihovny SafeInt provádí bezpečné aritmetické operace tohoto účtu bez přetečení. Tato knihovna taky porovnává různé druhy celých čísel.

#### <a name="new-active-template-library-atl-macros"></a>Nová makra Active Template Library (ATL)

Nová makra byly přidány do knihovny ATL pro rozšíření funkcí PROP_ENTRY_TYPE a PROP_ENTRY_TYPE_EX. PROP_ENTRY_INTERFACE a PROP_ENTRY_INTERFACE_EX umožňuje přidat seznam platných CLSID. PROP_ENTRY_INTERFACE_CALLBACK a PROP_ENTRY_INTERFACE_CALLBACK_EX umožňují zadat funkce zpětného volání k určení, zda identifikátor CLSID je platný.

#### <a name="analyze-warnings"></a>/ analyze upozornění

Většina / analyze (Analýza kódu Enterprise) upozornění byla odebrána z knihoven C Run-Time (CRT), MFC a knihovna ATL.

#### <a name="animation-and-d2d-support"></a>Podpora animace a D2D

MFC nyní podporuje animace a grafiku Direct2D. Knihovny MFC má několik nových tříd MFC a funkce pro tuto funkci podporují. Existují také dva nové návody ukazují, jak přidání objektu D2D a objekt animace do projektu. Tyto kurzy jsou návod: přidání objektu D2D do projektu MFC a návod: Přidání animace do projektu MFC.

### <a name="ide"></a>IDE – integrované vývojové prostředí

**Vylepšené IntelliSense.** IntelliSense pro Visual C++ byla zcela přepracována být rychlejší, přesnější a schopná zpracovat větší projekty. Zajistit tomuto vylepšení prostředí IDE rozlišuje mezi jak vývojář zobrazení a upraví zdrojový kód a jak IDE používá nastavení zdrojového kódu a projekt k vytvoření řešení.
Kvůli tomuto oddělení povinností procházet procházení funkce, jako zobrazení tříd a nové dialogové okno Přejít na jsou zpracovány systémem, který je založen na nový soubor systému SQL Server desktop databáze (SDF), který nahrazuje starý žádné kompilaci souboru (.ncb). IntelliSense funkce jako je rychlé informace, automatické doplňování a parametr pomáhají analyzovat jednotky překladu pouze v případě potřeby. Funkcích pro hybridní nasazení například nové okno hierarchie volání použít kombinaci na Procházet a funkce IntelliSense.
Vzhledem k tomu, že IntelliSense zpracovává pouze informace, které budete potřebovat v okamžiku, je rychlejšího rozhraní IDE. Protože jsou informace aktuálnější, zobrazení IDE a windows jsou také přesnější. Nakonec protože infrastruktura IDE lépe uspořádány, více možností a větší škálovatelnost, může zpracovávat větší projekty.

**Chyb technologie IntelliSense.** Prostředí IDE lépe zjistí chyby, které by mohly způsobit ztrátu technologie IntelliSense a zobrazí červený podtržení vlnovkou pod nimi. Kromě toho rozhraní IDE zobrazuje chyby IntelliSense v okně Seznam chyb. Chcete-li zobrazit kód, který je příčinou problému, dvakrát klikněte na chybu v okně Seznam chyb.

**#include funkce automatického dokončování.** Rozhraní IDE podporuje automatické dokončování #include – klíčové slovo. Pokud zadáte #include, rozhraní IDE vytvoří rozevíracího seznamu pole platné hlavičkových souborů. Pokud budete pokračovat, zadejte název souboru, rozhraní IDE vyfiltruje seznam založený na zadání. V libovolném bodě můžete ze seznamu vyberte soubor, který chcete zahrnout. Díky tomu můžete rychle zahrnout soubory bez znalosti přesný název souboru.

**Přejděte do.** Dialogové okno Přejít na umožňuje vyhledat všechny soubory v projektu, které odpovídají zadaný řetězec a symboly. Výsledky hledání jsou okamžitě revize při psaní do vyhledávacího řetězce další znaky. Toto pole zpětné vazby výsledky zjistíte počet nalezených položek a vám pomůže zjistit, jestli se má omezit hledání. Pole zpětné vazby druh/obor, umístění a Preview můžete odstranit nejednoznačnost položky, které mají podobné názvy. Kromě toho můžete rozšířit tuto funkci pro podporu jinými programovací jazyky.

**Paralelní ladění a profilování.** Ladicí program Visual Studio si je vědoma Concurrency Runtime a vám pomůže vyřešit aplikací pro paralelní zpracování. Nový nástroj profileru souběžnost můžete použít k vizualizaci celkového chování vaší aplikace. Navíc můžete použít nové nástroje systému windows k vizualizaci stav úloh a jejich zásobníky volání.

**Návrhář pásu karet.** Návrhář pásu karet je grafický editor, který vám umožní vytvořit a upravit uživatelské rozhraní pásu karet MFC. Konečné uživatelské rozhraní pásu karet je reprezentována soubor prostředků na základě XML (.mfcribbon-ms). Pro existující aplikace můžete zaznamenat vaše aktuální uživatelské rozhraní pásu karet dočasně přidáním několika řádků kódu a pak vyvolání Návrháře pásu karet. Po vytvoření souboru prostředků pásu karet můžete nahradit kód uživatelského rozhraní pro psané pásu s několika příkazy, které načtení prostředku pásu karet.

**Hierarchie volání.** Okno hierarchie volání umožňuje přejděte na všechny funkce, které jsou volány určitou funkci, nebo všechny funkce, které vyžadují určitou funkci.

### <a name="tools"></a>Nástroje

**Průvodce třídou MFC.** Visual C++ 2010 zobrazí zpět dobře považovat za nástroj Průvodce třídou MFC. Průvodce třídou MFC je pohodlný způsob, jak přidat třídy, zpráv a proměnné na projekt bez nutnosti ručně změnit sady zdrojových souborů.

**Průvodce ovládacím prvkem ATL.** Průvodce ovládacím prvkem ATL již automaticky vyplní pole ProgID. Pokud ovládací prvek ATL nemá ProgID, nemusí fungovat jiné nástroje s ním. Příkladem nástroj, který vyžaduje ovládacích prvků tak, aby měl ProgID je dialogové okno Vložit aktivní ovládací prvek. Další informace o dialogovém okně najdete v části Insert Dialog Box ovládací prvek ActiveX.

### <a name="microsoft-macro-assembler-reference"></a>Microsoft Macro Assembler – referenční dokumentace

Přidání YMMWORD datového typu podporuje multimediální operandy 256 bitů, které jsou zahrnuty v pokynech Intel Advanced Vector Extensions (AVX).

## <a name="whats-new-for-c-in-visual-studio-2008"></a>Co je nového pro jazyk C++ v sadě Visual Studio 2008

### <a name="visual-c-integrated-development-environment-ide"></a>Integrované vývojové prostředí (IDE) Visual C++

- Dialogová okna, které jsou vytvořené v aplikace Win32, ATL a MFC nyní v souladu s pokyny styl Windows Vista. Když vytvoříte nový projekt pomocí sady Visual Studio 2008, budou všechny dialogových oken, které vložíte do své aplikace dodržovat platí styl Windows Vista. Pokud jste znovu zkompiluje projekt, který jste vytvořili pomocí starší verze sady Visual Studio, budou všechna existující dialogová okna udržovat stejné vzhledu, která dřív měla. Další informace o tom, jak vložit dialogová okna do vaší aplikace najdete v editoru dialogového okna.

- Průvodce projektem ATL má nyní možnost k registraci komponenty pro všechny uživatele. Počínaje verzí Visual Studio 2008, komponenty COM a knihovny typů, které jsou vytvořené pomocí Průvodce projektem ATL jsou zaregistrovány v registru HKEY_CURRENT_USER uzlu Pokud nevyberete možnost zaregistrovat součást pro všechny uživatele.
- Průvodce projektem ATL již poskytuje možnost pro vytvoření projekty knihovny ATL s atributy. Počínaje verzí Visual Studio 2008, Průvodce projektem ATL nemá možnost změnit s atributy stav nového projektu. Všechny nové projekty knihovny ATL, které průvodce vytvoří jsou nyní bez atributů.
- Zápis do registru můžete přesměrovat. Se zavedením systému Windows Vista zápis do určitých oblastí registru vyžaduje program spouštět v režimu zvýšených oprávnění. Není žádoucí, aby vždy Visual Studio spustit v režimu zvýšených oprávnění. Přesměrování na uživatele automaticky přesměruje registru zápisy z HKEY_CLASSES_ROOT HKEY_CURRENT_USER beze změn programování.
- Návrhář tříd teď má omezenou podporu pro nativní kód C++. V dřívějších verzích sady Visual Studio návrhář tříd fungovala jenom s Visual C# a Visual Basic. C++ uživatelé teď můžou používat návrhář tříd, ale jenom v režimu jen pro čtení. Další informace o tom, jak používat návrháře tříd s C++ naleznete v článku Working s kódem jazyka Visual C++ v Návrháři tříd.
- Průvodce projektem již nemá možnost pro vytvoření projektu C++ SQL Server. Počínaje verzí Visual Studio 2008, Průvodce vytvořením projektu nemá možnost pro vytvoření projektu C++ SQL Server. SQL Server projekty vytvořené pomocí starší verze sady Visual Studio bude stále zkompilování a správně fungovat.

### <a name="visual-c-libraries"></a>Knihovny jazyka Visual C++

#### <a name="general"></a>Obecné

- Aplikace mohou být vázány na konkrétní verze knihoven Visual C++. Aplikace se někdy závisí na aktualizace, které byly provedeny po vydání knihovny jazyka Visual C++. V takovém případě můžete spouštět aplikace na počítači, který má starší verze knihoven způsobit neočekávané chování. Nyní můžete aplikaci na konkrétní verzi knihovny svázat tak, aby se na počítač, který je starší verze knihoven nespustí.

#### <a name="stlclr-library"></a>STL/CLR – knihovna

- Visual C++ nyní zahrnuje knihovny STL/CLR. Knihovny STL/CLR je balení z standardní šablona knihovny (STL), podmnožinu standardní knihovna C++ pro použití s C++ a rozhraní .NET Framework common language runtime (CLR). S STL/CLR teď můžete použít všechny kontejnery, iterátory a algoritmy STL ve spravovaném prostředí.

#### <a name="mfc-library"></a>Knihovny MFC

- Windows Vista podporuje běžné ovládací prvky. Více než 150 metody v 18 nový nebo existující třídy byly přidány k podpoře funkce v systému Windows Vista nebo k dosažení funkce v aktuálním MFC – třídy.
- Nová třída CNetAddressCtrl umožňuje vstup a ověření IPv4 a IPv6 adresy nebo názvy DNS.
- Nová třída CPagerCtrl zjednodušuje použití ovládacího prvku Windows pager.
- Nová třída CSplitButton zjednodušuje použití ovládacího prvku splitbutton Windows a vyberte výchozí nebo volitelná akce.

#### <a name="c-support-library"></a>Knihovna podpory C++

- C++ zavádí knihovny zařazování. Knihovny zařazování poskytuje snadný a optimalizované způsob zařazování dat mezi nativní a spravovaná prostředí. Knihovna je alternativa k přístupy složitější a méně efektivní, například pomocí služby PInvoke. Další informace naleznete v tématu Přehled zařazování v jazyku C++.

#### <a name="atl-server"></a>ATL Server

- Jako zdroj sdílené projekt vydání ATL Server.
- Většinu kódu ATL Server základní byla vydána jako sdílený zdroj projekt na webu CodePlex a není nainstalován jako součást sady Visual Studio 2008. Několik souborů, které jsou přidružené k serveru ATL již nejsou součástí sady Visual Studio. Seznam odebrané soubory naleznete v části odebrat soubory serveru ATL.
- Data kódování a dekódování třídy z funkce atlenc.h a nástroj a třídy z atlutil.h a atlpath.h jsou teď součástí knihovny serveru ATL.
- Microsoft bude podporovat verzích ATL Server, které jsou zahrnuty v dřívějších verzích sady Visual Studio, dokud jsou podporovány tyto verze sady Visual Studio. Vývoj kódu ATL Server jako komunity projekt bude pokračovat webu CodePlex. Společnost Microsoft na webu CodePlex verzi ATL Server nepodporuje.

### <a name="visual-c-compiler-and-linker"></a>Visual C++ kompilátoru a Linkeru

#### <a name="compiler-changes"></a>Změny v kompilátoru

- Kompilátor podporuje spravované přírůstkové sestavení. Pokud určíte tuto možnost, nebudou kompilátor znovu zkompiluje kód, když se změní odkazované sestavení. Místo toho bude provedeno přírůstkové sestavení. Soubory jsou překompilovat pouze v případě, že vliv budou změny mít kód závislé.
- Atributy týkající se serveru ATL již nejsou podporovány. Kompilátor již nepodporuje několik atributů, které byly přímo souvisí s ATL Server. Úplný seznam atributů odebrána najdete v části nejnovější změny.
- Kompilátor podporuje mikroarchitektury Intel Core. Kompilátor obsahuje ladění pro mikroarchitektury Intel Core během generování kódu. Ve výchozím nastavení je na toto ladění a nelze zakázáno, protože pomáhá také Pentium 4 a dalších procesorů.
- Vnitřní funkce podporují novější AMD a Intel procesory. Několik nový vnitřní pokyny podporují funkci větší v novější AMD a Intel procesory. Další informace o nové vnitřní funkce najdete v dodatečné Streaming SIMD Extensions 3 pokyny, Streaming SIMD Extensions 4 pokyny, SSE4A a Advanced vnitřní Bit manipulaci s objekty, vnitřní funkce AES, _mm_clmulepi64_si128 a __rdtscp.
- Funkce __cpuid se aktualizuje. __Cpuid, __cpuidex funkce teď podporuje několik nových funkcí z nejnovější revize AMD a Intel procesorů. Vnitřní __cpuidex je nový a shromáždí informace z poslední procesory.
- Možnost kompilátoru /MP snižuje dobu celkový sestavení. Možnost/MP může výrazně snížit celkový čas zkompilovat několik zdrojových souborů tak, že vytvoříte několik procesů, které zkompilovat soubory současně. Tato možnost je obzvláště užitečná v počítačích, které podporují Hyper-threadingem, více procesorů nebo víc jader.
- /Wp64 – možnost kompilátoru a __w64 – klíčové slovo jsou zastaralé. /Wp64 – možnost kompilátoru a __w64 – klíčové slovo, které rozpoznat problémy s 64bitovou přenositelností, jsou zastaralé a bude v budoucí verzi systému kompilátoru odebrána. Místo tento – možnost kompilátoru a – klíčové slovo použijte – kompilátor Visual C++ této cíle 64bitové platformě.
- / Qfast_transcendentals generuje vloženého kódu pro přechodový funkce.
- / Qimprecise_fwaits odebere fwait příkazy, interní try – bloky při použití /fp: kromě – možnost kompilátoru.

### <a name="linker-changes"></a>Změny linkeru

- Informace o řízení účet uživatele je nyní vložený do manifestu souborů spustitelných souborů linkeru Visual C++ (link.exe). Tato funkce je ve výchozím nastavení povolená.   Další informace o tom, jak tuto funkci zakázat nebo tom, jak změnit výchozí chování najdete v tématu /MANIFESTUAC (vložené informace UAC v manifestu).
- Linkeru má teď možnost /DYNAMICBASE povolit funkci náhodného přeskupování rozložení adresu místa systému Windows Vista. Tato možnost upravuje záhlaví spustitelný soubor indikující, zda má aplikace při načítání, náhodně rebased.

## <a name="whats-new-for-c-in-visual-studio-2005"></a>Co je nového pro jazyk C++ v sadě Visual Studio 2005

Následující funkce byly nového ve Visual C++ 2005 Service Pack 1:

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

### <a name="new-language-keywords"></a>Nové klíčová slova jazyka

__sptr, __uptr

### <a name="new-compiler-features"></a>Nové funkce kompilátoru

Kompilátor má nejnovější změny v této verzi.

- nativní ' 64bitová verze a mezi kompilátory.
- / analyze (Analýza kódu Enterprise) – možnost kompilátoru byla přidána.
- / bigobj – možnost kompilátoru byla přidána.
- / CLR: pure, / CLR: safe a /clr:oldSyntax byly přidány. (Později nepoužívané ve Visual Studiu 2015.)
- Možnosti kompilátoru zastaralé: v této verzi; jsou zastaralé mnoho – možnosti kompilátoru Další informace najdete v části – možnosti kompilátoru zastaralé.
- Dvojitý převod adres v/CLR kódu se snižuje; Další informace najdete v části dvojitý převod adres (C++).
- /EH (Model zpracování výjimek) nebo /EHs už umožňuje zachytit výjimku, která se vyvolá s něco jiného než throw; Použijte/EHa.
- / errorreport (sestava interními chybami kompilátoru) – možnost kompilátoru byla přidána.
- / favor (optimalizace pro 64) – možnost kompilátoru byla přidána.
- / FA, /Fa (soubor výpis) – možnost kompilátoru byla přidána.
- /FC (úplná cesta z souboru zdrojového kódu v diagnostice) – možnost kompilátoru byla přidána.
- /fp (zadejte Floating-Point chování) – možnost kompilátoru byla přidána.
- Byla přidána možnost kompilátoru možnosti /G (optimalizace pro procesoru).
- Byla přidána možnost kompilátoru možnosti /G (optimalizace pro procesoru).
- / Možnosti kompilátoru G3, /G4, /G5, /G6, /G7 a /GB byly odebrány. Kompilátor teď používá "kombinaci model", pokusí se vytvořit nejlepší výstupního souboru pro všechny architektury.
- /GF byla odebrána. Místo toho použijte /GF (odstranění duplicitních řetězců).
- /GL (optimalizace celého programu) je teď kompatibilní s /CLRHEADER.
- GR nyní ve výchozím nastavení zapnutý.
- /GS (Kontrola zabezpečení vyrovnávací paměti) teď poskytuje ochranu zabezpečení pro citlivé ukazatel parametry. /GS nyní ve výchozím nastavení zapnutý. /GS teď funguje taky na funkce, zkompilované k MSIL s volbou/CLR (kompilace Common Language Runtime).
- / homeparams (Kopírovat parametry registru do zásobníku) – možnost kompilátoru byla přidána.
- / hotpatch (vytvořit kopii opravitelnou za provozu) – možnost kompilátoru byla přidána.
- Vložené funkce heuristiky byly aktualizovány; Zobrazit vložené, __inline, __forceinline a inline_depth – Další informace
- Byly přidány mnoho nové vnitřní funkce a mnoho dříve nedokumentovanými vnitřní objekty jsou nyní zdokumentované.
- Ve výchozím nastavení volání do nové, který selže vyvolá výjimku.
- Byly odebrány /ml a /MLd – možnosti kompilátoru. Visual C++ nepodporuje podpora knihovny CRT jednovláknové, staticky propojený.
- Kompilátor implementováno s názvem vrátit hodnotu optimalizace, které je povoleno, když kompilujete s /O1, / O2 (velikost minimalizovat, maximalizovat rychlost), /Og (globální optimalizace) a /Ox (úplná optimalizace).
- /Oa – možnost kompilátoru byla odebrána, ale bude bezobslužně ignorován; Modifikátory noalias nebo restrict__declspec slouží k určení, jak funguje kompilátor aliasy.
- – Možnost kompilátoru /OP byly zrušeny. Místo toho použijte /fp (zadejte Floating-Point chování).
- OpenMP se teď podporuje ve Visual C++.
- byla přidána možnost kompilátoru/OpenMP (povolit podporu OpenMP 2.0).
- /Ow – možnost kompilátoru byla odebrána, ale budou bez upozornění ignorovat. Modifikátory noalias nebo restrict__declspec slouží k určení, jak funguje kompilátor aliasy.

### <a name="profile-guided-optimizations"></a>Optimalizace na základě profilu

- / QI0f byla odebrána.
- / QIfdiv byla odebrána.
- / Byla přidána možnost kompilátoru QIPF_B (chybující pro taktování procesoru B).
- / Byla přidána možnost kompilátoru QIPF_C (chybující pro C taktování procesoru).
- / Byla přidána možnost kompilátoru QIPF_fr32 (provést není použití horní 96 plovoucí bodu zaregistruje).
- / Byla přidána možnost kompilátoru QIPF_noPIC (Generovat pozice závislé kód).
- / Byla přidána možnost kompilátoru QIPF_restrict_plabels (předpokládá ne funkce vytvořit za běhu).

### <a name="unicode-support-in-the-compiler-and-linker"></a>Podpora kódování Unicode v kompilátoru a linkeru

- /VD (zakázat posunutí konstrukcí) teď umožňuje použít na objekt vytvářen dynamic_cast – operátor (nebo vd2)
- Odebrali jsme /YX – možnost kompilátoru. Místo toho použijte /Yc (Vytvořit předkompilovaný hlavičkový soubor) nebo /Yu (Použít předkompilovaný hlavičkový soubor). Pokud odeberete /YX z konfigurace sestavení a nahraďte ji metodou nic, může být v sestaveních rychlejší.
- /Zc:forScope nyní ve výchozím nastavení zapnutý.
- / Zc: nyní ve výchozím nastavení zapnutý.
- /Zd – možnost kompilátoru byla odebrána. Číslo řádku pouze ladicí informace již není podporována. Místo toho použijte /Zi (/Z7, / zi, /ZI (formát ladění informací) Další informace najdete v části).
- /Zg je nyní platná pouze na soubory zdrojového kódu C a ne na soubory zdrojového kódu C++.
- Byla přidána možnost kompilátoru /ZX (ladění optimalizované Itanium kód).

### <a name="new-language-features"></a>Nové jazykové funkce

- AtributAtribut je nyní zastaralý.
- Modifikátor appdomain__declspec byla přidána.
- konvence volání __clrcall byla přidána.
- nepoužívané – modifikátor (C++) declspec teď umožňuje zadejte řetězec, který se zobrazí při kompilaci, když se uživatel pokusí o přístup k nepoužívané třídy nebo funkce.
- dynamic_cast – operátor má nejnovější změny.
- Nativní výčty teď umožňují určit základní typ.
- Modifikátor jitintrinsicdeclspec byla přidána.
- Modifikátor noaliasdeclspec byla přidána.
- Modifikátor process__declspec byla přidána.
- abstraktní, přepsání a zapečetěná jsou platné pro nativní kompilaci.
- __restrict – klíčové slovo byla přidána.
- Modifikátor restrictdeclspec byla přidána.
- __thiscall je nyní klíčové slovo.
- __unaligned – klíčové slovo je nyní zdokumentované.
- volatile (C++) byl aktualizován chování s ohledem na optimalizace.

### <a name="new-preprocessor-features"></a>Nové funkce preprocesoru

- __Clr_ver – předdefinované makro přidat.
- Direktiva pragma komentáře (C/C++) teď přijme /MANIFESTDEPENDENCY jako komentář linkeru. Možnost exestr komentovat je nyní zastaralý.
- embedded_idl – atribut (#import – direktiva) teď přebírá volitelný parametr.
- fenv_access – direktiva pragma
- float_control – direktiva pragma
- fp_contract – direktiva pragma
- Globální proměnné nebudou inicializována v pořadí, ve kterém jsou deklarovány Pokud máte ve – Direktiva pragma spravované, nespravované a nespravované globální proměnné. Pokud je potenciální narušující změně, například nespravované globální proměnná je inicializován s spravované globální proměnné a úplně konstruovaný spravovaného objektu je požadovaná.
- Části zadaným init_seg – jsou nyní jen pro čtení a není pro čtení a zápis jako předchozí verze.
- inline_depth – výchozí hodnota je nyní 16. Výchozí hodnota je 16 se také v platnosti ve Visual C++ .NET 2003.
- _Integral_max_bits – makro předdefinované přidali, najdete v části předdefinovaná makra.
- _M_CEE – _m_cee_pure – a _m_cee_safe – předdefinovaná makra přidali, najdete v části předdefinovaná makra.
- _M_ix86_fp – předdefinované makro přidat.
- _M_x64 – předdefinované makro přidat.
- make_public – direktiva pragma
- spravované, nespravované – Direktiva pragma syntaxe byla aktualizována (má nyní nabízení a pop)
- mscorlib.dll teď implicitně odkazuje #using – direktiva v všechny kompilace/CLR.
- _Openmp – předdefinované makro přidat.
- optimize – Direktiva pragma je aktualizovaná a w již nejsou platné parametry.
- no_registry – #import atribut byla přidána.
- oblast, endregion – direktivy přidán
- _Vc_nodefaultlib – předdefinované makro přidat.
- Nyní jsou implementovány Variadická makra.
- vtordisp – je zastaralá a bude v budoucí verzi Visual C++ odebrána.
- Direktiva pragma upozornění má nyní specifikátor potlačit.

### <a name="new-linker-features"></a>Nové funkce Linkeru

- Moduly (bez sestavení MSIL výstupní soubory) jsou nyní povoleny jako vstup linkeru.
- / ALLOWISOLATION (vyhledání manifestu) – možnost linkeru byla přidána.
- / ASSEMBLYRESOURCE (vložení spravované prostředků) je aktualizovaná tak, aby teď můžete zadat název prostředku v sestavení a k určení, zda je prostředek privátní v sestavení povolit.
- / CLRIMAGETYPE (zadat typ z obrázku CLR) – možnost linkeru byla přidána.
- / CLRSUPPORTLASTERROR (zachovat poslední kód chyby pro volání PInvoke) – možnost linkeru byla přidána.
- / CLRTHREADATTRIBUTE (nastavit CLR vláken atribut) – možnost linkeru byla přidána.
- / CLRUNMANAGEDCODECHECK (přidat atribut SupressUnmanagedCodeSecurityAttribute) – možnost linkeru byla přidána.
- / ERRORREPORT (sestava interními chybami Linkeru) – možnost linkeru byla přidána.
- / Odebrali jsme EXETYPE – možnost linkeru. Linkeru nepodporuje vytváření ovladače zařízení systému Windows 95 a Windows 98. Pomocí příslušné DDK můžete vytvořit tyto ovladače zařízení. Klíčové slovo EXETYPE již není platný pro soubory definice modulu.
- / FUNCTIONPADMIN (vytvořit kopii opravitelnou za provozu) – možnost linkeru byla přidána.
- / LTCG – možnost linkeru se teď podporuje na moduly kompilovat s volbou/CLR. / LTCG také aktualizoval na podporu optimalizace na základě profilu.
- / MANIFEST (vytvoření souběžně sdílená sestavení manifestu) – možnost linkeru byla přidána.
- / MANIFESTDEPENDENCY (určit závislosti manifestu) – možnost linkeru byla přidána.
- / MANIFESTFILE (název souboru manifestu) – možnost linkeru byla přidána.
- Odebrali jsme /MAPINFO:lines – možnost linkeru.
- / NXCOMPAT (kompatibilní s předcházením spuštění dat) – možnost linkeru byla přidána.
- / PGD (určit databázi pro optimalizace Profile-Guided) – možnost linkeru byla přidána.
- / PROFILE (Profiler nástrojů výkonu) – možnost linkeru byla přidána.
- / SECTION (určit atributy oddílu) – možnost linkeru nyní podporuje atribut negace a již nepodporuje L nebo D atributy (VxD souvisejících).
- Podpora kódování Unicode v kompilátoru a linkeru
- / VERBOSE (Tisk zpráv průběhu) – možnost linkeru teď také přijme bránou Firewall a REF.
- / Odebrali jsme VXD – možnost linkeru. Linkeru nepodporuje vytváření ovladače zařízení systému Windows 95 a Windows 98. Pomocí příslušné DDK můžete vytvořit tyto ovladače zařízení. VXD – klíčové slovo již není platný pro soubory definice modulu.
- Odebrali jsme /ws – možnost linkeru. /WS se používají k úpravě bitové kopie určený pro systém Windows NT 4.0. Název souboru -R IMAGECFG.exe lze namísto /WS. IMAGECFG.exe naleznete na disku CD-ROM systému Windows NT 4.0 v SUPPORT\DEBUG\I386\IMAGECFG. SOUBOR EXE.
- /WX (považovat upozornění Linkeru jako chyby) – možnost linkeru je nyní zdokumentované.

### <a name="new-linker-utility-features"></a>Nové funkce nástroje Linkeru

- / Byla přidána ALLOWISOLATION – možnost nástroje editbin
- Popis příkazů soubor definice modulu se odebere. Linkeru již nepodporuje vytváření virtuální ovladače zařízení.
- / ERRORREPORT – možnost přidala bscmake.exe, dumpbin.exe, editbin.exe a lib.exe.
- / LTCG – možnost lib byla přidána.
- / NXCOMPAT – možnost nástroje editbin byla přidána.
- / RANGE – možnost nástroje dumpbin byla přidána.
- / TLS – možnost nástroje dumpbin byla přidána.
- – Možnost nástroje editbin /ws byla odebrána. /WS se používají k úpravě bitové kopie určený pro systém Windows NT 4.0. Název souboru -R IMAGECFG.exe lze namísto /WS. IMAGECFG.exe naleznete na disku CD-ROM systému Windows NT 4.0 v SUPPORT\DEBUG\I386\IMAGECFG. SOUBOR EXE.
- /WX [: Ne] byla přidána možnost lib.

### <a name="new-nmake-features"></a>Nové funkce NMAKE

- / ERRORREPORT byla přidána.
- /G byla přidána.
- Předdefinovaná pravidla bylo aktualizováno.
- Makro $(MAKE), která je popsána v rekurzivní makra, teď poskytuje úplnou cestu k nmake.exe.

### <a name="new-masm-features"></a>Nové funkce MASM

- Výrazy MASM jsou nyní 64-bit hodnoty. V předchozích verzích MASM byly výrazy 32bitové hodnoty.
- Int __asm instrukce 3 nyní způsobí, že funkce sestavují na nativní.
- ALIAS (MASM) je nyní zdokumentované.
- / ERRORREPORT – možnost ml.exe a ml64.exe je přidána.
- . FPO je nyní zdokumentované.
- H2INC.exe nebude dodat ve Visual C++ 2005. Pokud potřebujete dál používat H2INC, použijte H2INC.exe z předchozí verze aplikace Visual C++.
- operátor IMAGEREL byla přidána.
- high32 – operátor byla přidána.
- low32 – operátor byla přidána.
- ml64.exe je verze MASM pro x64 architektura. Ji sestaví x64 .asm soubory do x64 objektu soubory. Vložené sestavení jazyk není podporován v x64 kompilátoru. Byly přidány následující direktivy MASM pro ml64.exe (x64):
- .ALLOCSTACK
- .ENDPROLOG
- .PUSHFRAME
- .PUSHREG
- .SAVEREG
- .SAVEXMM128
- . SETFRAME v navíc PROC – direktiva byl aktualizován s jen x64 syntaxe.
- Byla přidána mmword – direktiva
- / omf (ML.exe možnost příkazového řádku) teď znamená /c. ML.exe nepodporuje propojení objektů OMF formátu.
- SEGMENT – direktiva teď podporuje další atributy.
- sectionrel – operátor byla přidána.
- Byla přidána xmmword – direktiva

### <a name="new-crt-features"></a>Nové funkce CRT

- Bylo přidáno bezpečné verze několik funkcí. Tyto funkce v lepší způsob zpracování chyb a vynucovat přísnější ovládacích prvků ve vyrovnávací paměti, abyste se vyhnuli běžné chyby zabezpečení. Nové verze zabezpečení jsou identifikovány příponou _M.
- Existující méně bezpečná verze mnoha funkcí jsou zastaralé. Chcete-li zakázat odstranění upozornění, definujte _CRT_SECURE_NO_WARNINGS.
- Mnoho funkcí existující nyní ověřit jejich parametrů a vyvolat obslužnou rutinu neplatný parametr, pokud je předán neplatný parametr.
- Mnoho funkcí existující teď nastavit kód chyby, které se předtím není.
- Byla přidána errno_t typedef s celočíselného typu. errno_t se používá při každém funkci návratový typ nebo parametr zabývá kódy chyb z kód chyby. errno_t nahradí errcode.
- Funkce závislých na národním prostředí, mají nyní verze, které trvat národní prostředí jako parametr, nikoli pomocí aktuální národní prostředí. Tyto nové funkce mít příponu _l. Několik nových funkcí byly přidány do práce s objekty národního prostředí. Nové funkce zahrnují _get_current_locale –, _create_locale – a _free_locale –.
- Pro podporu zamykání a odemykání obslužných rutin souborů byly přidány nové funkce.
- _Spawn řadu funkcí neprovádí vynulování errno nule v případě úspěchu, stejně jako v předchozích verzích.
- Verze printf řadu funkcí, které vám umožní určit pořadí, ve kterém se používají argumenty, které jsou k dispozici.
- Unicode je nyní podporované textovém formátu. Funkce _Otevřít podporuje _O_TEXTW, _O_UTF8 a _O_UTF16 atributy. Podporuje funkci fopen – "ccs = kódování" metoda sloužící k určení formátu Unicode.
- Nová verze knihovny CRT vytvořené ve spravovaném kódu (MSIL) je nyní k dispozici a je použitý ke zkompilování s parametrem/CLR (kompilace Common Language Runtime).
- Odebrali jsme _fileinfo.
- Výchozí velikost pro time_t – je nyní 64 bitů, které rozšíří rozsah time_t – a řadu časové funkce out roku 3000.
- CRT teď podporuje nastavení národního prostředí na základě za přístup z více vláken. _Configthreadlocale – funkce byla přidána do tuto funkci podporovat.
- _Statusfp2 – a __control87_2 – funkce byly přidány do povolit přístup k a kontrolu nad plovoucí bod řídicího slova na obou x87 a SSE2 plovoucí bod procesoru.
- Funkce The_mkgmtime a _mkgmtime64 – byly přidány do poskytují podporu pro převod dobu (struktura tm) greenwichský střední čas (GMT).
- Swprintf – a vswprintf – aby lépe odpovídaly se standardem byly provedeny změny.
- Nový soubor záhlaví, INTRIN. H, poskytuje prototypy pro některé vnitřní funkce.
- Fopen – funkce má nyní atribut N.
- Funkce _Otevřít má nyní atribut _O_NOINHERIT.
- Atoi – funkce teď vrátí INT_MAX a nastaví errno erange – na přetečení. V předchozích verzích nebyla definována chování přetečení.
- Printf řadu funkcí podporuje hexadecimální plovoucí desetinnou čárkou výstup implementována podle standardu ANSI C99 použití specifikátorů formátu typ %a a %A.
- Rodina printf teď podporuje velikost předponu "vše" (long long).
- _Controlfp – funkce optimalizovaná pro dosažení vyššího výkonu.
- Ladicí verze některé funkce nebyly přidány.
- Přidání _chgsignl – a _cpysignl (long double verze).
- Přidání _locale_t – typ pro typ tabulky.
- Nové _countof – makro makro přidat pro výpočetní počet prvků v poli.
- V každém tématu funkce přidaná oddíl v rozhraní .NET Framework – ekvivalenty.
- Několik řetězcové funkce mají nyní možnost zkracování řetězců, nikoli selhání při výstupní vyrovnávací paměti je příliš malý. v tématu _truncate –.
- _set_se_translator – nyní vyžaduje použití možnosti/EHa kompilátoru.
- fpos_t – je nyní __int64 pod /Za (pro kód C) a kdy __STDC__ je nastavit ručně (pro C++ – kód). Struktury dříve.
- _Crt_disable_perfcrit_locks – může zvýšit výkon vstupně-výstupních operací jednovláknové programů.
- POSIX názvy jsou zastaralé považuje ISO C++ vyhovující názvy (například _getch – použijte namísto getch –).
- Nové soubory .obj odkaz Možnosti jsou k dispozici pro čistá režimu
- _recalloc – kombinuje funkce realloc – a calloc –.

## <a name="whats-new-for-c-in-visual-studio-2003"></a>Co je nového pro jazyk C++ v aplikaci Visual Studio 2003

### <a name="compiler"></a>Kompilátoru

- Informace o tom, jak spustit spravovaných rozšíření pro C++ aplikace vytvořené s aktuální verzí kompilátoru na předchozí verzi modulu runtime.
- Spravovaná rozšíření pro C++ nejčastější dotazy.
- Byla přidána návod znázorňující portu existující, nativní aplikace pro použití spravovaných rozšíření pro C++: Návod: portování stávající nativní aplikace C++ do Interoperate s součásti rozhraní .NET Framework.
- Nyní můžete vytvořit delegáta pro metodu typ hodnoty.
- Kompilátoru shody se standardem C++ je výrazně Vylepšená Visual C++ .NET 2003.
- / – možnost kompilátoru architektury je přidána.
- /GF je zastaralá a bude v budoucí verzi systému Visual C++ odebrána.
- / G7 – možnost kompilátoru je přidána.
- /GS kompilátoru možnosti je vylepšená k ochraně místní proměnné z přímé přetečení zásobníku.
- Možnost kompilátoru /noBool byla odebrána. Kompilátor teď umožňuje bool objevit pouze jako klíčové slovo (a ne identifikátorem) v souboru zdrojového kódu C++.
- Je k dispozici jako definici typu __int64 Všimněte si, že je ještě podpora dlouho dlouho v CRT typu long long.
- /Zm – možnost kompilátoru teď určuje omezení přidělení paměti pro předkompilované hlavičky.
- _InterlockedCompareExchange vnitřní nyní zdokumentované.
- _InterlockedDecrement vnitřní nyní zdokumentované.
- _InterlockedExchange vnitřní nyní zdokumentované.
- Vnitřní _InterlockedExchangeAdd nyní zdokumentované.
- _InterlockedIncrement vnitřní nyní zdokumentované.
- _Readwritebarrier – vnitřní funkce přidán.

### <a name="attributes"></a>Atributy

- `implements` atribut je nyní zdokumentované.

### <a name="linker-features"></a>Funkce linkeru

Byly přidány následující linkerů přepínače:

- / ASSEMBLYDEBUG
- / ASSEMBLYLINKRESOURCE
- DELAYSIGN
- /KEYFILE
- / KEYCONTAINER
- / SAFESEH

### <a name="masm"></a>MASM

Na. Možnost SAFESEH – direktiva a/SAFESEH ml.exe byly přidány.

## <a name="see-also"></a>Viz také

[Průvodce přenosem a upgradem Visual C++](visual-cpp-porting-and-upgrading-guide.md)
