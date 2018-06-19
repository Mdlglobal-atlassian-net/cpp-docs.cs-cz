---
title: -projektovou - (standardy shoda) | Microsoft Docs
ms.date: 11/11/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /permissive
- VC.Project.VCCLCompilerTool.ConformanceMode
dev_langs:
- C++
helpviewer_keywords:
- /permissive compiler options [C++]
- -permissive compiler options [C++]
- Standards conformance compiler options
- permissive compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 90cfdcf20cf74244afe026a392759ac59616bbdf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379312"
---
# <a name="permissive--standards-conformance"></a>/ projektovou-(standardy shoda)

Zadejte režim standardů shoda kompilátoru. Pomocí této možnosti vám pomohou identifikovat a opravit problémy, shoda v kódu, aby byl více správné a víc přenosného.

## <a name="syntax"></a>Syntaxe

> **/ projektovou-**

## <a name="remarks"></a>Poznámky

Můžete použít **/ projektovou-** – možnost kompilátoru k určení chování kompilátoru podle standardů. Tato možnost zakáže projektovou chování a nastaví [/Zc](../../build/reference/zc-conformance.md) pro striktní shoda – možnosti kompilátoru. V prostředí IDE tato možnost umožňuje také podtržení nonkonformní kódu technologie IntelliSense modul.

Ve výchozím nastavení **/ projektovou-** je možnost nastavena v nové projekty vytvořené verzi Visual Studio 2017 15,5 a novější verze. Ve výchozím nastavení v dřívějších verzích není nastavena. Když je nastaven možnost, kompilátor generuje diagnostiky chyby nebo upozornění, když vytvoří nestandardní jazyk zjištění v kódu, včetně některé běžné chyby v pre-C ++ 11 kódu.

**/ Projektovou-** možnost je kompatibilní s téměř všechny hlavičky souborů z nejnovější sady Windows, jako je například Software Development Kit (SDK) nebo ovladač Kit WDK (Windows), od verze Windows patří Creators SDK (10.0.16299.0). Starší verze sady SDK se nemusí podařit kompilovat v části **/ projektovou-** pro různé zdroje kódu shoda důvodů. Kompilátor a sady SDK lodě na jinou verzi časových os, proto nejsou některé zbývající problémy. Konkrétní hlavičky souboru problémy najdete v tématu [problémy hlavičky Windows](#windows-header-issues) níže.

**/ Projektovou-** možnost nastaví [/Zc: strictstrings](../../build/reference/zc-conformance.md) a [/Zc: rvaluecast](../../build/reference/zc-conformance.md) možnosti vyhovující chování. Jejich výchozí nonkonformní chování. Můžete předat konkrétní **/Zc** možnosti po **/ projektovou-** na příkazovém řádku toto chování potlačit.

Ve verzích počínaje kompilátoru Visual Studio 2017 verze 15.3 **/ projektovou-** možnost nastaví [/Zc:ternary](../../build/reference/zc-ternary.md) možnost. Kompilátor také implementuje více požadavků pro hledání dvoufázového název. Když **/ projektovou-** je možnost nastavena, kompilátor analyzuje funkce a – třída definice šablony identifikace závislé a nezávislých názvů používaných v šablonách. V této verzi se provádí pouze název detekci závislosti.

Rozšíření pro konkrétní prostředí a jazyk oblastí, které standardní opustí až implementace nemá vliv **/ projektovou-**. Například konkrétní Microsoft `__declspec`, konvence volání a strukturovaného zpracování klíčová slova a direktivy pragma kompilátoru konkrétní nebo atributy výjimek nejsou příznakem kompilátorem v **/ projektovou-** režimu.

**/ Projektovou-** možnost používá podporu shoda v aktuální verzi kompilátoru k určení, které jazykové konstrukty jsou nonkonformní. Možnost nezjišťuje, pokud kód vyhovuje na konkrétní verzi standardní C++. Pokud chcete povolit všechny implementovaná kompilátoru podporu pro nejnovější koncept standard, použijte [/std:latest](../../build/reference/std-specify-language-standard-version.md) možnost. Chcete-li omezit podpora kompilátoru současné době implementovanou standardu C ++ 17, použijte [/std: c ++ 17](../../build/reference/std-specify-language-standard-version.md) možnost. Chcete-li omezit podpora kompilátoru tak, aby lépe odpovídaly C ++ 14 standard, použijte [/std: c ++ 14](../../build/reference/std-specify-language-standard-version.md) možnost, která je výchozí.

Ne všechny C ++ 11, C ++ 14 nebo C ++ 17 standardy odpovídající kód podporuje – kompilátor Visual C++ v aplikaci Visual Studio 2017. **/ Projektovou-** možnost nemusí rozpoznat problémy s ohledně některých aspektů vyhledávání dvoufázového názvu, vazby bez const odkaz na dočasný, považuje kopie init jako přímý init, která umožňují více uživatelem definované převody v Inicializace nebo alternativní tokeny pro logické operátory a další oblasti nepodporované shoda. Další informace o problémech shoda v jazyce Visual C++, najdete v části [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="how-to-fix-your-code"></a>Jak opravit kódu

Zde jsou některé příklady kódu, který je zjišťován jako nonkonformní při použití **/ projektovou-**, společně s návrhy způsoby, jak opravit problémy.

#### <a name="use-default-as-an-identifier-in-native-code"></a>Použít výchozí jako identifikátor v nativním kódu

```cpp
void func(int default); // Error C2321: 'default' is a keyword, and
                        // cannot be used in this context
```

#### <a name="lookup-members-in-dependent-base"></a>Členy vyhledávání ve znalostní bázi závislé base

```cpp
template <typename T>
struct B {
    void f();
};

template <typename T>
struct D : public B<T> // B is a dependent base because its type
                       // depends on the type of T.
{
    // One possible fix is to uncomment the following line.
    // If this is a type, don't forget the 'typename' keyword.
    // using B<T>::f;

    void g() {
        f(); // error C3861: 'f': identifier not found
             // Another fix is to change it to 'this->f();'
    }
};

void h() {
    D<int> d;
    d.g();
}
```

#### <a name="use-of-qualified-names-in-member-declarations"></a>Použití kvalifikované názvy v deklarace členů

```cpp
struct A {
    void A::f() { } // error C4596: illegal qualified name in member
                    // declaration.
                    // Remove redundant 'A::' to fix.
};
```

#### <a name="initialize-multiple-union-members-in-a-member-initializer"></a>Inicializace více union členů v inicializátoru člena

```cpp
union U
{
    U()
        : i(1), j(1) // error C3442: Initializing multiple members of
                     // union: 'U::i' and 'U::j'.
                     // Remove all but one of the initializations to fix.
    {}
    int i;
    int j;
};
```

#### <a name="hidden-friend-name-lookup-rules"></a>Pravidla vyhledávání název skrytá friend

```cpp
// Example 1
struct S {
    friend void f(S *);
};
// Uncomment this declaration to make the hidden friend visible:
// void f(S *); // This declaration makes the hidden friend visible

using type = void (*)(S *);
type p = &f; // error C2065: 'f': undeclared identifier.
```

```cpp
// Example 2
struct S {
    friend void f(S *);
};
void g() {
    // Using nullptr instead of S prevents argument dependent lookup in S
    f(nullptr); // error C3861: 'f': identifier not found

    S *p = nullptr;
    f(S); // Hidden friend now found via argument-dependent lookup.
}
```

#### <a name="use-scoped-enums-in-array-bounds"></a>Použít vymezenou výčty v meze pole

```cpp
enum class Color {
    Red, Green, Blue
};

int data[Color::Blue]; // error C3411: 'Color' is not valid as the size
                       // of an array as it is not an integer type.
                       // Cast to type size_t or int to fix.
```

#### <a name="use-for-each-in-native-code"></a>Použijte pro každou v nativním kódu

```cpp
void func() {
    int array[] = {1, 2, 30, 40};
    for each (int i in array) // error C4496: nonstandard extension
                              // 'for each' used: replace with
                              // ranged-for statement:
                              // for (int i: array)
    {
        // ...
    }
}
```

#### <a name="use-of-atl-attributes"></a>Použití atributů ATL

```cpp
// Example 1
[uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
class A {};
```

```cpp
// Fix for example 1
class __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) B {};
```

```cpp
// Example 2
[emitidl];
[module(name="Foo")];

[object, local, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb")]
__interface ICustom {
    HRESULT Custom([in] longl, [out, retval] long*pLong);
    [local] HRESULT CustomLocal([in] longl, [out, retval] long*pLong);
};

[coclass, appobject, uuid("9e66a294-4365-11d2-a997-00c04fa37ddb")]
class CFoo : public ICustom
{};
```

```cpp
// Fix for example 2
// First, create the *.idl file. The vc140.idl generated file can be 
// used to automatically obtain a *.idl file for the interfaces with 
// annotation. Second, add a midl step to your build system to make 
// sure that the C++ interface definitions are outputted. 
// Last, adjust your existing code to use ATL directly as shown in 
// the atl implementation section.

-- IDL  FILE--
import "docobj.idl";

[object, local, uuid(9e66a290-4365-11d2-a997-00c04fa37ddb)]
interface ICustom : IUnknown {
    HRESULT Custom([in] longl, [out,retval] long*pLong);
    [local] HRESULT CustomLocal([in] longl, [out,retval] long*pLong);
};

[ version(1.0), uuid(29079a2c-5f3f-3325-99a1-3ec9c40988bb) ]
library Foo {
    importlib("stdole2.tlb");
    importlib("olepro32.dll");

    [version(1.0), appobject, uuid(9e66a294-4365-11d2-a997-00c04fa37ddb)]
    coclass CFoo { interface ICustom; };
}

-- ATL IMPLEMENTATION--
#include <idl.header.h>
#include <atlbase.h>

class ATL_NO_VTABLE CFooImpl : public ICustom,
    public ATL::CComObjectRootEx<CComMultiThreadModel>
{
    public:BEGIN_COM_MAP(CFooImpl)
    COM_INTERFACE_ENTRY(ICustom)
    END_COM_MAP()
};
```

#### <a name="ambiguous-conditional-operator-arguments"></a>Nejednoznačný podmíněný operátor argumenty

Ve verzích kompilátoru před Visual Studio 2017 verze 15.3, kompilátor přijata argumenty podmíněný operátor (nebo Ternární operátor) `?:` , jsou považovány za nejednoznačný standardem. V **/ projektovou-** režimu, kompilátor teď vystavuje jeden nebo více diagnostiky v případech, kdy kompilovat bez diagnostiky v dřívějších verzích.

Obecných chyb, které může být důsledkem této změny patří:

- Chyba C2593: operátor? je nejednoznačný

- Chyba C2679: binární '?': žádná operátorem najít, což trvá pravém operand typu "B" (nebo není žádný převod přijatelné)

- Chyba C2678: binární '?': žádná operátorem najít, což trvá levé operand typu "A" (nebo není žádný převod přijatelné)

- Chyba C2446: ':': žádný převod z "B" na "A"

Vzor typické kód, který může způsobit, že tento problém je, když některé třída C poskytuje-explicitní konstruktor z jiného typu T a operátor-explicitní převod typu T. V takovém případě převod argumentu 2. typ 3. i převod argumentem 3. na typ 2. jsou platné převody, které je nejednoznačné podle standardní.

```cpp
// Example 1: class that provides conversion to and initialization from some type T
struct A
{
    A(int);
    operator int() const;
};

extern bool cond;

A a(42);
// Accepted when /Zc:ternary or /permissive- is not used:
auto x = cond ? 7 : a; // A: permissive behavior prefers A(7) over (int)a
// Accepted always:
auto y = cond ? 7 : int(a);
auto z = cond ? A(7) : a;
```

Je důležité výjimkou z tohoto vzoru běžné při T představuje jeden z typů řetězce ukončené hodnotou null (například `const char *`, `const char16_t *`a tak dále) a argument skutečné `?:` je řetězec odpovídající typu literálu. C ++ 17 změnil sémantiku z C ++ 14. V důsledku toho je kód v příkladu 2 přijímán pod **/std: c ++ 14** a odmítnuté pod **/std: c ++ 17** při **/Zc:ternary** nebo **/permissive-** se používá.

```cpp
// Example 2: exception from the above
struct MyString
{
    MyString(const char* s = "") noexcept;  // from char*
    operator const char* () const noexcept; //   to char*
};

extern bool cond;

MyString s; 
// Using /std:c++14, /permissive- or /Zc:ternary behavior
// is to prefer MyString("A") over (const char*)s
// but under /std:c++17 this line causes error C2445:
auto x = cond ? "A" : s;
// You can use a static_cast to resolve the ambiguity:
auto y = cond ? "A" : static_cast<const char*>(s);
```

Kde můžou zobrazit chyby jiném případě je v podmíněné operátory s jedním argumentem typu `void`. Tento případ, může být v makra ASSERT jako běžné.

```cpp
// Example 3: void arguments
void myassert(const char* text, const char* file, int line);
// Accepted when /Zc:ternary or /permissive- is not used:
#define ASSERT_A(ex) (void)((ex) ? 1 : myassert(#ex, __FILE__, __LINE__))
// Accepted always:
#define ASSERT_B(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))
```

Může se také zobrazit chyby v šabloně metaprogramování, kde typy výsledků podmíněný operátor může změnit v části **/Zc:ternary** a **/ projektovou-**. Jedním ze způsobů, chcete-li vyřešit tento problém je použití [std::remove_reference](../../standard-library/remove-reference-class.md) na výsledný typ.

```cpp
// Example 4: different result types 
extern bool cond;
extern int count;
char  a = 'A'; 
const char  b = 'B'; 
decltype(auto) x = cond ? a : b; // char without, const char& with /Zc:ternary 
const char (&z)[2] = count > 3 ? "A" : "B"; // const char* without /Zc:ternary 
```

#### <a name="two-phase-name-look-up-partial"></a>Dvoufázové název vyhledávání (částečné)

Když **/ projektovou-** je možnost nastavena v Visual Studio 2017 verze 15.3, kompilátor analyzuje funkce a – třída definice šablony identifikace závislé a nezávislých názvů používaných v šablonách podle potřeby pro dvoufázového název hledání. V této verzi se provádí pouze název detekci závislosti. Konkrétně nezávislých názvy, které nejsou deklarované v rámci definice šablony způsobit diagnostické zprávy podle potřeby standardy ISO C++. Ale vazby nezávislých názvů, které vyžadují, že argument závislé vyhledávání v kontextu definice není nastavená.

```cpp
// dependent base
struct B {
    void g();
};

template<typename T>
struct D : T {
    void f() {
        // The call to g was incorrectly allowed in VS2017:
        g();  // Now under /permissive-: C3861
        // Possible fixes:
        // this->g();
        // T::g();
    }
};

int main()
{
    D<B> d;
    d.f();
}
```

### <a name="windows-header-issues"></a>Problémy hlavičky Windows

**/ Projektovou-** možnost je příliš přísné pro verze sady Windows než Windows patří Creators aktualizace SDK (10.0.16299.0) nebo verze ovladače Kit WDK (Windows). 1709. Doporučujeme, abyste je aktualizovat na nejnovější verze sady Windows, aby bylo možné používat **/ projektovou-** ve vašem kódu ovladačů systému Windows nebo zařízení.

Některé soubory hlaviček v systému Windows patří Creators aktualizace SDK (10.0.16299.0) nebo ovladač Kit WDK (Windows). 1709, stále mít problémy, které je kompatibilní s použitím **/ projektovou-**. Chcete-li tyto problémy vyřešit, doporučujeme, můžete omezit použití těchto hlaviček pouze tyto soubory zdrojového kódu, které je vyžadují a odeberte **/ projektovou-** možnost při kompilaci tyto soubory konkrétní zdrojového kódu. Následující problémy jsou specifické pro Windows patří Creators aktualizace SDK (10.0.16299.0):

#### <a name="issue-in-umqueryh"></a>Problém um\Query.h

Při použití **/ projektovou-** přepínače kompilátoru `tagRESTRICTION` struktura nekompiluje z důvodu case(RTOr) člen 'nebo'.

```cpp
struct tagRESTRICTION
    {
    ULONG rt;
    ULONG weight;
    /* [switch_is][switch_type] */ union _URes
        {
        /* [case()] */ NODERESTRICTION ar;
        /* [case()] */ NODERESTRICTION or;  // error C2059: syntax error: '||'
        /* [case()] */ NODERESTRICTION pxr;
        /* [case()] */ VECTORRESTRICTION vr;
        /* [case()] */ NOTRESTRICTION nr;
        /* [case()] */ CONTENTRESTRICTION cr;
        /* [case()] */ NATLANGUAGERESTRICTION nlr;
        /* [case()] */ PROPERTYRESTRICTION pr;
        /* [default] */  /* Empty union arm */
        } res;
    };
```

Chcete-li vyřešit tento problém, zkompilovat soubory, které zahrnují Query.h bez **/ projektovou-** možnost.

#### <a name="issue-in-umcellularapioemh"></a>Problém um\cellularapi_oem.h

Při použití **/ projektovou-** přepínače kompilátoru, předat dál deklaraci `enum UICCDATASTOREACCESSMODE` způsobí, že upozornění:

```cpp
typedef enum UICCDATASTOREACCESSMODE UICCDATASTOREACCESSMODE; // C4471
```

Předat dál deklaraci bez ohledu na obor výčtu je rozšíření Microsoft. Chcete-li vyřešit tento problém, zkompilovat soubory, které zahrnují cellularapi_oem.h bez **/ projektovou-** možnost, nebo použijte [/wd](../../build/reference/compiler-option-warning-level.md) možnost ticho upozornění C4471.

#### <a name="issue-in-umomscripth"></a>Problém um\omscript.h

V C ++ 03, převod z řetězcového literálu na BSTR (což je typedef k ' wchar_t *') je zastaralý, ale povoleny. V C ++ 11 převod již není povoleno.

```cpp
virtual /* [id] */ HRESULT STDMETHODCALLTYPE setExpression(
    /* [in] */ __RPC__in BSTR propname,
    /* [in] */ __RPC__in BSTR expression,
    /* [in][defaultvalue] */ __RPC__in BSTR language = L"") = 0; // C2440
```

Chcete-li vyřešit tento problém, zkompilovat soubory, které zahrnují omscript.h bez **/ projektovou-** možnost, nebo použijte **/Zc:strictStrings-** místo.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

Ve verzi Visual Studio 2017 15,5 a novější verze použijte tento postup:

1. Otevřete váš projekt **stránky vlastností** dialogové okno.

1. V části **vlastnosti konfigurace**, rozbalte **C/C++** složky a vyberte **jazyk** stránku vlastností.

1. Změna **shoda režimu** hodnotu vlastnosti na **Ano (/ projektovou-)**. Zvolte **OK** nebo **použít** uložte provedené změny.

Ve verzi před Visual Studio 2017 verze 15,5 použijte tento postup:

1. Otevřete váš projekt **stránky vlastností** dialogové okno.

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Zadejte **/ projektovou-** – možnost kompilátoru v **další možnosti** pole. Zvolte **OK** nebo **použít** uložte provedené změny.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)   
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)
