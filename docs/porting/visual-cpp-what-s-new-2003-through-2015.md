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
dev_langs: C++
ms.assetid: c4afde6f-3d75-40bf-986f-be57e3818e26
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 030a5e287d18884a2bbf49613a464c9d3c98f8d1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="visual-c-what39s-new-2003-through-2015"></a>Visual C++ Co & č. 39; s novou 2003 až 2015

**Poznámka:** informace o Visual Studio 2017 najdete v tématu [co je nového pro Visual C++ v aplikaci Visual Studio 2017](../what-s-new-for-visual-cpp-in-visual-studio.md) a [shoda vylepšení v jazyce Visual C++ v aplikaci Visual Studio 2017](../cpp-conformance-improvements-2017.md).

Ve Visual C++ 2015 a novější můžete probíhající vylepšení shoda s kompilátorem prostředí někdy změnit jak kompilátor rozumí existujícím zdrojovém kódu. Pokud k tomu dojde, můžete během sestavení nebo i chování rozdíly v kódu, který dříve vytvořené a došlo ke správnému setkat nové nebo jiné chyby.  
  
 Naštěstí tyto rozdíly mít žádné nebo téměř žádné dopad na většinu vašeho zdrojového kódu a vyřešit tyto rozdíly jsou potřeba zdrojový kód nebo další změny, opravy jsou obvykle malé a jednoduché. Jsme zahrnuli mnoho příklady dříve přijatelné zdrojový kód, který může být nutné změnit *(před)* a opravy a opravte je *(po)*.  
  
 I když tyto rozdíly mohou ovlivnit váš zdrojový kód nebo artefaktů sestavení, neovlivňují binární kompatibilitu mezi jednotlivými aktualizace Visual C++ verze. Další závažné druhu změny, *nejnovější změny* může mít vliv na binární kompatibilitu, ale tyto typy binární kompatibilitu zalomení dojít pouze mezi hlavní verzí aplikace Visual C++. Například mezi Visual C++ 2013 a Visual C++ 2015. Informace o nejnovějších změn, které došlo mezi Visual C++ 2013 a Visual C++ 2015, najdete v části [historie 2003 2015 změn Visual C++](../porting/visual-cpp-change-history-2003-2015.md).  
  
-   [Vylepšení shoda v sadě Visual C++ 2015](#VS_RTM)  
  
-   [Shoda vylepšení v aktualizaci 1](#VS_Update1)  
  
-   [Shoda vylepšení v aktualizaci 2](#VS_Update2)  
  
-   [Shoda vylepšení v aktualizaci 3](#VS_Update3)  
  
##  <a name="VS_RTM"></a>Vylepšení shoda v sadě Visual C++ 2015  
  
-   Možnost /Zc:forScope-  
  
     Možnost kompilátoru **/Zc:forScope-** je zastaralá a bude v budoucí verzi odebrána.  
  
    ```  
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release  
    ```  
  
     Chcete-li povolit nestandardní kód, který používá cykly proměnné za bod, kde podle standard, že by se nachází mimo obor se obvykle použila možnost. Byla pouze nezbytné při jsou kompilaci s parametrem /Za od bez /Za, použití pro proměnnou smyčky po konci smyčky je vždycky povolená. Pokud vám nezáleží standardy shoda (například pokud není určena pro přenosný na jiné kompilátory kódu), můžete je možnost /Za (nebo nastavte vlastnost zakázat jazyková rozšíření na Ne). Pokud se zajímáte o psaní kódu přenosné, kompatibilní se standardy, by se tak, aby u standardního přesunutím deklaraci takovéto proměnné do bodu mimo smyčky přepište kód.  
  
    ```  
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
  
-   **/Zg – možnost kompilátoru**  
  
     Možnost kompilátoru /Zg (Generovat prototypy funkcí) již není k dispozici. Tato možnost kompilátoru byl dříve zastaralé.  
  
-   Už spuštěním testů jednotek s C + +/ CLI z příkazového řádku s mstest.exe. Místo toho použijte vstest.console.exe. V tématu [možnosti příkazového řádku VSTest.Console.exe](/devops-test-docs/test/vstest-console-exe-command-line-options).  
  
-   **Mutable – klíčové slovo**  
  
     `mutable` Specifikátor třídy úložiště je již povolen v místech, kde dříve ho kompilovat bez chyby. Nyní, kompilátor poskytuje chyba C2071 (třída neplatné úložiště). Proměnný specifikátor podle standard, lze použít pouze na názvy členů tříd dat a nelze použít pro názvy deklarovaný const nebo statické a nelze použít k odkazování členů.  
  
     Zvažte například následující kód:  
  
    ```  
    struct S {  
        mutable int &r;  
    };  
    ```  
  
     Předchozí verze Visual C++ compiler přijata to, ale teď kompilátor dává k následující chybě:  
  
    ```Output  
    error C2071: 'S::r': illegal storage class  
    ```  
  
     Chcete-li chybu opravit, odeberte jednoduše redundantní mutable – klíčové slovo.  
  
-   **char_16_t a char32_t**  
  
     Už můžete `char16_t` nebo `char32_t` jako aliasy v definici typu, protože tyto typy jsou nyní považovány za předdefinované. Bylo běžné pro uživatele a knihovna autorům zadat char16_t a char32_t jako aliasy uint16_t a uint32_t, v uvedeném pořadí.  
  
    ```  
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
  
-   **Parametry šablony non-type**  
  
     Některé kód, který zahrnuje parametry šablon bez typu je nyní správně kontrolována typ kompatibility při zadat explicitní šablony argumenty. Například následující kód kompilovat bez chyby v předchozích verzích Visual C++.  
  
    ```  
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
  
-   **__declspec(align)**  
  
     Kompilátor již přijímá `__declspec(align)` na funkce. To vždy ignorovat, ale nyní je dojde k chybě kompilátoru.  
  
    ```  
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations  
    ```  
  
     Chcete-li tento problém vyřešit, odeberte `__declspec(align)` z deklarace funkce. Vzhledem k tomu, že ho měl žádný vliv, odebrat ho nezmění nic.  
  
-   **Zpracování výjimek**  
  
     Existuje několik změn výjimek. Objekty výjimek nejprve musí být kopírovatelná nebo mobilní. Následující kód kompilovat v [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)], ale nejde kompilovat v [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)]:  
  
    ```  
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
  
    ```  
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
  
    ```  
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
  
    ```  
    catch(D& d)  
    {  
    }  
    ```  
  
-   **Textové literály, za nímž následuje makra**  
  
     Kompilátor teď podporuje uživatelsky definované literály. Textové literály, za nímž následuje makra bez jakékoli použité prázdných znaků v důsledku toho jsou interpretovány jako uživateli definované literály, které může být chyby nebo neočekávané výsledky. Například v předchozí kompilátory následující kód zkompilovat úspěšně:  
  
    ```  
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
  
    ```  
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found  
    note: Did you forget a space between the string literal and the prefix of the following string literal?  
  
    ```  
  
     Chcete-li tento problém vyřešit, přidejte mezeru mezi řetězcový literál a makra.  
  
-   **Sousední textové literály**  
  
     Podobně jako na předchozí, z důvodu související změny při analýze řetězce, byly přiléhající textové literály (buď široké nebo úzké znak textové literály) bez jakékoli prázdné interpretovat jako jeden řetězec zřetězených v předchozích verzích Visaul C++. V [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)], je nutné přidat nyní mezery mezi dva řetězce. Například je třeba změnit následující kód:  
  
    ```  
    char * str = "abc""def";  
    ```  
  
     Stačí přidáte mezeru mezi dva řetězce.  
  
    ```  
    char * str = "abc" "def";  
    ```  
  
-   **Nové umístění a odstranění**  
  
     Ke změně byl proveden operátor delete, aby byla v shoda s C ++ 14 standardní. Podrobnosti o změnu standardy najdete na [C++ velikost navrácení](http://isocpp.org/files/papers/n3778.html). Změny přidat formu globální odstranit operátor, který přebírá parametr velikosti. Narušující změně je, že pokud jste dříve používali delete – operátor se stejným podpisem (tak, aby odpovídaly s operátor new umístění), zobrazí se chyba kompilátoru (C2956, který probíhá v okamžiku, kdy nové umístění se používá, protože to je operátor delete pozici v kódu, kde se pokusí identifikovat odpovídající odpovídající kompilátor).  
  
     Funkce `void operator delete(void *, size_t)` byl operátor delete umístění odpovídající nové funkce umístění "void \* new – operátor (size_t –, size_t –)" v C ++ 11. S C ++ 14 velikostí navrácení, tato funkce odstranění je teď *funkce obvykle navrácení* (globální delete – operátor). Standardní vyžaduje, aby pokud použití nové umístění vyhledá odpovídající funkce odstranit a vyhledá funkce obvykle navrácení, program nedůvěryhodný.  
  
     Předpokládejme například, že váš kód definuje nové umístění a odstranění umístění:  
  
    ```  
    void * operator new(std::size_t, std::size_t);  
    void operator delete(void*, std::size_t) noexcept;  
  
    ```  
  
     K problému dochází kvůli shodu v signatury funkce mezi operátor delete umístění, kterou jste definovali a operátor new globální velikostí odstranit. Zvažte, jestli můžete použít jiného typu než size_t – pro všechny umístění nový a odstranit operátory.  Upozorňujeme, že je typ size_t – typedef kompilátoru závislé; je typedef pro nepodepsané int v jazyce Visual C++. Dobrým řešením je použití Výčtový typ jako je tato:  
  
    ```  
    enum class my_type : size_t {};  
  
    ```  
  
     Pak změňte svou definici nové umístění a odstranit tento typ slouží jako druhý argument místo size_t –. Také budete muset aktualizovat volání do umístění nové předat nový typ (například pomocí `static_cast<my_type>` převést z celočíselnou hodnotu) definici nové aktualizace a odstranit zpět přetypovat na typ integer. Nemusíte používat výčet pro tento; Typ třídy s členem size_t – by taky měly fungovat.  
  
     Alternativní řešení je, že může být schopni zcela eliminovat nové umístění. Pokud váš kód používá umístění nového k implementaci fondu paměti, kde argument umístění je velikost na objekt, který přidělené nebo odstraněna, pak velikostí navrácení funkce může být vhodný nahradit vlastní kód vlastní paměti fondu a můžete získat odstranit umístění funkce a právě použít vlastní dva argument delete – operátor místo funkce umístění.  
  
     Pokud nechcete, aby váš kód okamžitou aktualizaci, můžete se vrátit k původní chování pomocí možnosti kompilátoru /Zc:sizedDealloc-. Pokud použijete tuto možnost, odstranění dva argument funkce neexistují a nebude způsobit konflikt s vaší umístění delete – operátor.  
  
-   **Union datové členy**  
  
     Data členů sjednocení už můžete mít odkazové typy. Následující kód zkompilovat úspěšně v [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)], ale vytvoří chybu v [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)].  
  
    ```  
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
  
-   Anonymní sjednocení jsou teď další vyhovující pro standardní. Předchozí verze kompilátoru generovány explicitní konstruktor a destruktor pro anonymní sjednocení. Ty se odstraní [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)].  
  
    ```  
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
  
    ```  
    error C2280: '<unnamed-type-u>::<unnamed-type-u>(void)': attempting to reference a deleted function  
    note: compiler has generated '<unnamed-type-u>::<unnamed-type-u>' here  
    ```  
  
     Chcete-li vyřešit tento problém, zadejte vlastní definice konstruktor a/nebo destruktor.  
  
    ```  
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
  
-   **Sjednocení s anonymní struktury**  
  
     Chcete-li v souladu se standardem, došlo ke změně modulu runtime chování pro členy anonymní struktury ve sjednoceních. V konstruktoru pro anonymní struktury členy ve spojení se nazývá už implicitně při vytváření této unie. Destruktor pro členy anonymní struktury sjednocení navíc je už implicitně volána, když sjednocení ocitne mimo rozsah. Vezměte v úvahu následující kód, ve kterém sjednocení U obsahuje strukturu anonymní, který obsahuje člena, který je s názvem struktura S, který má destruktor.  
  
    ```  
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
  
    ```  
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
  
    ```  
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
  
-   **Šablona řešení**  
  
     Překlad názvů pro šablony byly provedeny změny. V jazyce C++ při zvažování kandidáty pro překlad názvu může být případ, že jeden nebo více názvů v úvahu jako potenciální odpovídá vytváří vytváření instancí šablon neplatný. Tyto neplatné konkretizací obvykle nezpůsobí chyby kompilátoru, zásadu, která se označuje jako sfinae u výrazů (nahrazení selhání je není chyba).  
  
     Nyní pokud sfinae u výrazů vyžaduje kompilátor k vytváření instancí specializace šablony třídy, pak všechny chyby, ke kterým došlo během tohoto procesu jsou chyby kompilátoru. V předchozích verzích by kompilátor ignorovat takové chyby. Zvažte například následující kód:  
  
    ```  
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
  
-   **Kopírovací konstruktory**  
  
     V obou [!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)] a Visual Studio 2015, kompilátor generuje kopírovacího konstruktoru třídy Pokud třídy má konstruktor move definovaný uživatelem, ale žádné uživatelem definované kopírovacího konstruktoru. Dev14 je tento konstruktor implicitně generovaného kopie také označený "= odstranění".  
  
##  <a name="VS_Update1"></a>Shoda vylepšení v aktualizaci 1  
  
-   **Privátní virtuální základní třídy a nepřímé dědění**  
  
     Předchozí verze kompilátoru povolené odvozené třídy za účelem zavolejte členské funkce jeho *nepřímo odvozené* `private virtual` základní třídy. Toto chování staré nebyla správná a neodpovídá C++ standard. Kompilátor už akceptuje kód napsaný v tímto způsobem a v důsledku vydá Chyba kompilátoru C2280.  
  
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
  
    ```  
    class base;  // as above  
  
    class middle: private virtual base {};  
    class top: public virtual middle, private virtual bottom {};  
  
    void destroy(top *p)  
    {  
        delete p;  
    }  
    ```  
  
-   **Přetížené new – operátor a delete – operátor**  
  
     Předchozí verze kompilátoru povolené třetí `operator new` a třetí `operator delete` deklarovat statickou a deklarovat v oborech názvů než globální obor názvů.  Toto chování původního vytvoření riziko, že tento program nebude volání `new` nebo `delete` operátor implementace, která programátorů určený, což vede k bezobslužné chybný modul runtime chování. Kompilátor už akceptuje kód napsaný v tímto způsobem a vydá Chyba kompilátoru C2323 místo.  
  
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
  
     Kromě toho i když kompilátor nedává konkrétní Diagnostika, vložené new – operátor považuje za nedůvěryhodný.  
  
-   **Volání metody ' operátor *typu*() ' (uživatelem definovaný převod) na typy jiné třídy**  
  
     Předchozí verze kompilátoru povolené ' operátor *typu*(), k volání na typy jiné třídy při tiché ignoruje se. Toto chování staré vytvořit riziko generování tichou chybného kódu, což vede k nepředvídatelným modul runtime chování. Kompilátor už akceptuje kód napsaný v tímto způsobem a vydá Chyba kompilátoru C2228 místo.  
  
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
  
-   **Redundantní typename použity ve specifikátorech typu propracována**  
  
     Předchozí verze kompilátoru povolené `typename` použity ve specifikátorech propracována typu; je sémanticky nesprávný kód napsaný v tímto způsobem. Kompilátor už akceptuje kód napsaný v tímto způsobem a vydá Chyba kompilátoru C3406 místo.  
  
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
  
-   **Odvození typu pole ze seznamu inicializátoru**  
  
     Předchozí verze kompilátoru nepodporuje odvození typu polí z inicializátoru seznamu. Kompilátor teď podporuje tato forma odvození typu a, v důsledku toho volání funkce šablon pomocí inicializační seznamy teď může být nejednoznačný nebo jiné přetížení může být zvolena než v předchozích verzích kompilátoru. Chcete-li tyto problémy vyřešit, program musí nyní explicitně zadáte přetížení, které programátorů určený.  
  
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
  
-   **Obnovení přepínač příkaz upozornění**  
  
     Předchozí verze kompilátoru odebrána dříve existující upozornění související s `switch` příkazy; tato upozornění byly obnoveny. Kompilátor teď vystavuje obnovené upozornění a upozornění souvisejících s konkrétní případy (včetně výchozí případ) jsou nyní vystavené na řádek obsahující problematické případu, ne na poslední řádek příkaz switch. Výsledkem je nyní vydávajícího upozornění na různé řádky než v minulosti, upozornění dříve potlačit pomocí `#pragma warning(disable:####)` může potlačit už tak, jak má. K potlačení tato upozornění tak, jak má, může být potřeba přesunout `#pragma warning(disable:####)` direktivy na řádek nad prvním případě potenciálně poškozený. Níže jsou uvedeny obnovené upozornění.  
  
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
  
-   **#include: použití nadřazený adresář specifikátor '..' v názvu cesty** (ovlivňuje pouze /Wall wdn)  
  
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
  
-   **#pragma optimize() přesahuje za konec souboru záhlaví** (ovlivňuje pouze /Wall wdn)  
  
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
  
-   **Neshoda #pragma warning(push)** a **#pragma warning(pop)** (ovlivňuje pouze /Wall wdn)  
  
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
  
-   **Neodpovídající #pragma warning(push)** (ovlivňuje pouze /Wall wdn)  
  
     Předchozí verze kompilátoru se nepodařilo rozpoznat neodpovídající `#pragma warning(push)` změny na konci jednotce překlad stavu. Kompilátor nyní zjistí a upozorní programátorů kód napsaný v tímto způsobem a problémy volitelné kompilátoru upozornění C5032 v umístění neodpovídající #pragma warning(push), pokud je povoleno. Pokud nejsou žádné chyby kompilace v jednotce překlad se pouze objeví toto upozornění.  
  
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
  
-   **Další upozornění může být vydaný v důsledku vylepšené #pragma upozornění stavu sledování**  
  
     Předchozí verze kompilátoru sledovat #pragma upozornění změny stavu nedostatečně i na problém, že vše určená upozornění. Toto chování vytvořit riziko určitá upozornění by efektivně potlačit v situacích, které se liší od programátorů určena. Kompilátor nyní sleduje stav varování #pragma více robustní – zejména související s #pragma upozornění změny stavu v rámci šablony – a volitelně vydá nové upozornění C5031 a C5032, které pomohou najít nezamýšleným používá programátorů`#pragma warning(push)` a `#pragma warning(pop)`.  
  
     V důsledku vylepšené #pragma může být nyní objeví upozornění sledování, upozornění dříve nesprávně Potlačené a upozornění souvisejících s problémy dříve misdiagnosed změny stavu.  
  
-   **Lepší identifikaci nedostupný kódu**  
  
     Standardní knihovna C++ změny a vylepšená možnost volání vnořené funkce porovnání s předchozími verzemi kompilátoru, mohou povolovat kompilátoru k prokázání, určitý kód je nyní nedostupný. Toto nové chování může mít za následek nové a další často vydané instancí upozornění C4720.  
  
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
  
##  <a name="VS_Update2"></a>Shoda vylepšení v aktualizaci 2  
  
-   **Další upozornění a chyby může být vydaný v důsledku částečné podporu pro výraz sfinae u výrazů**  
  
     Předchozí verze kompilátoru analyzovat určité druhy výrazů uvnitř `decltype` specifikátory z důvodu nedostatku podpory pro výraz sfinae u výrazů. Toto chování staré nebyla správná a neodpovídá C++ standard. Kompilátor teď analyzuje tyto výrazy a částečné podporu pro výraz sfinae u výrazů z důvodu vylepšení probíhající shoda. V důsledku toho nyní vydá upozornění a chyby nalezené ve výrazech, že předchozí verze kompilátoru není analyzovat.  
  
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
  
-   `volatile`**členské proměnné zabránit implicitně definované konstruktory a operátory přiřazení**  
  
     Předchozí verze kompilátoru povolené třídy, která má `volatile` členské proměnné tak, aby měl výchozí kopírování nebo přesunutí konstruktory a operátory přiřazení pro kopírování nebo přesunutí automaticky generovány výchozí. Toto chování staré nebyla správná a neodpovídá C++ standard. Kompilátor nyní brány v úvahu třídy, která má volatile členské proměnné tak, aby měl netriviální vytváření a operátory přiřazení, která brání automaticky generován výchozí implementace těchto operátorů.  Když tyto třídy je členem sjednocení (nebo anonymní sjednocení uvnitř třídu), zkopírovat nebo přesunout konstruktory a operátory přiřazení pro kopírování nebo přesunutí sjednocení (nebo třída obsahující sjednocení unonymous) budou implicitně definovány odstranit. Probíhá pokus o vytvoření nebo zkopírujte sjednocení (nebo třída obsahující anonymní sjednocení) bez nutnosti explicitně definovat je je chybu a Chyba kompilátoru problémy kompilátoru C2280 v důsledku.  
  
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
  
-   **Statické členské funkce nepodporují kvalifikátory odchylka nákladů.**  
  
     Předchozí verze Visual C++ 2015 povoleno statické členské funkce tak, aby měl kvalifikátory odchylka nákladů. Toto chování je z důvodu regrese v Visual C++ 2015 a Visual C++ 2015 Update 1; Visual C++ 2013 a předchozích verzích Visual C++ odmítnout kód napsaný v tímto způsobem. Chování Visual C++ 2015 a Visual C++ 2015 Update 1 není správná a neodpovídá standardní C++.  Visual Studio 2015 Update 2 odmítne kód napsaný v tímto způsobem a vydá Chyba kompilátoru C2511 místo.  
  
    ```Output  
    error C2511: 'void A::func(void) const': overloaded member function not found in 'A'  
    ```  
  
     Příklad (před)  
  
    ```  
    struct A  
    {  
      static void func();  
    };  
  
    void A::func() const {}  // C2511  
  
    ```  
  
     Příklad (po)  
  
    ```  
    struct A  
    {  
      static void func();  
    };  
  
    void A::func() {}  // removed const  
  
    ```  
  
-   **Předat dál deklarace výčtu není povolen v kódu WinRT** (/ZW ovlivňuje pouze)  
  
     Kód zkompilovat pro prostředí Windows Runtime (WinRT) neumožňuje `enum` typy dál deklarovat, podobně jako při kompilaci spravovaného kódu C++ pro rozhraní .net Framework pomocí kompilátoru/clr přepínače. Toto chování se zajistí, že velikost výčet je vždy známé a může být správně promítá do systému typu WinRT. Kompilátor odmítne kód napsaný v tímto způsobem a vydá Chyba kompilátoru C2599 společně s chyba kompilátoru C3197.  
  
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
  
-   **Přetížené třetí new – operátor a delete – operátor nemusí být deklarován vložené** (úroveň 1 (/ W1) na výchozím)  
  
     Předchozí verze kompilátoru není upozorní, když new – operátor třetí a operátor delete funkce jsou deklarovány vložené. Kód napsaný v tímto způsobem je nesprávně naformátován (nejsou potřeba žádné diagnostiky) a může způsobit paměti problémy vyplývající z nové Neshoda a odstranit operátory (zejména při použití společně s velikostí navrácení), které může být obtížné diagnostikovat.   Kompilátor nyní vydává kompilátoru upozornění C4595 k identifikaci kódu napsaného tímto způsobem.  
  
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
  
##  <a name="VS_Update3"></a>Shoda vylepšení v aktualizaci 3  
  
-   **std::is_convertable nyní rozpozná vlastní přiřazení** (standardní knihovna)  
  
     Předchozí verze `std::is_convertable` typ znak se nepodařilo rozpoznat správně vlastní přiřazení typu třídy, když se odstraní. jeho kopie konstruktoru nebo privátní. Nyní `std::is_convertable<>::value` je správně nastavena na `false` při použití typu třídy s odstraněný nebo soukromý kopírovacího konstruktoru.  
  
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
  
-   **Uvedena odstranění trivial kopírování nebo přesunutí specifikátory přístupu ohledem konstruktory**  
  
     Předchozí verze kompilátoru není zkontrolujte specifikátor přístupu uvedena nebo odstraněné trivial kopie a přesunout konstruktory před povolením, která se má volat. Toto chování staré nebyla správná a neodpovídá C++ standard. V některých případech toto chování staré vytvořit riziko generování tichou chybného kódu, což vede k nepředvídatelným modul runtime chování. Kompilátor nyní zkontroluje přístup specifikátor uvedena nebo odstraněné trivial kopie a přesunout konstruktory k určení, zda může být volána a pokud ne, kompilátoru problémy v důsledku upozornění C2248.  
  
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
  
-   **S atributy podpory kódu ATL** (úroveň 1 (/ W1) na výchozím)  
  
     Kódu ATL s atributy předchozích verzích kompilátoru podporována. Jako další fáze odebrání podporu pro knihovny ATL s atributy kód, který [začal ve Visual C++ 2008](https://msdn.microsoft.com/library/bb384632\(v=vs.90\).aspx), s atributy ATL kód je zastaralá. Kompilátor nyní vydává kompilátoru upozornění C4467 k identifikaci tento druh nepoužívané kódu.  
  
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
  
-   **Předkompilované soubory hlaviček (PCH) a neshoda # direktivy include** (ovlivňuje pouze /Wall wdn)  
  
     Neshoda akceptovat předchozí verze kompilátoru `#include` direktivy ve zdrojových souborech mezi `-Yc` a `-Yu` kompilace při použití předkompilovaných hlaviček (PCH) souborů. Kód napsaný v tímto způsobem je už přijat kompilátoru.   Kompilátor teď problémy kompilátoru upozornění CC4598 k identifikaci neshoda `#include` direktivy při použití souborů PCH.  
  
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
  
-   **Předkompilované soubory hlaviček (PCH) a neshoda adresáře souborů k zahrnutí** (ovlivňuje pouze /Wall wdn)  
  
     Předchozí verze kompilátoru přijata neshoda adresář include (`-I`) argumenty příkazového řádku pro kompilátor mezi `-Yc` a `-Yu` kompilace při použití předkompilovaných hlaviček (PCH) souborů. Kód napsaný v tímto způsobem je už přijat kompilátoru.   Kompilátor teď problémy kompilátoru upozornění CC4599 k identifikaci neshoda adresář include (`-I`) argumenty příkazového řádku při použití souborů PCH.  
  
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