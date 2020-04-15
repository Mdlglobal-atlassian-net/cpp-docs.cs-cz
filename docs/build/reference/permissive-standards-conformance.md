---
title: /permissive- (shoda se standardy)
description: Referenční příručka k možnosti kompilátoru Microsoft C++ /tolerantní- (Shody standardů).
ms.date: 04/14/2020
f1_keywords:
- /permissive
- VC.Project.VCCLCompilerTool.ConformanceMode
helpviewer_keywords:
- /permissive compiler options [C++]
- -permissive compiler options [C++]
- Standards conformance compiler options
- permissive compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 695f84e64f07128ac7744dc99e736f2a71ab3e79
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337406"
---
# <a name="permissive--standards-conformance"></a>/permissive- (shoda se standardy)

Zadejte režim shody standardů pro kompilátor. Pomocí této možnosti můžete identifikovat a opravit problémy s kondenzací v kódu, aby byl správnější a přenosnější.

## <a name="syntax"></a>Syntaxe

> **/tolerantní-**

## <a name="remarks"></a>Poznámky

Tato možnost je podporovaná v sadě Visual Studio 2017 a novější.

Můžete použít **/tolerantní-** kompilátor možnost určit standardy vyhovující chování kompilátoru. Tato možnost zakáže povolaní chování a nastaví možnosti kompilátoru [/Zc](zc-conformance.md) pro přísnou shodu. V ide, tato možnost také umožňuje intelliSense modul podtržení nevyhovující kód.

Ve výchozím nastavení **/tolerantní-** možnost je nastavena v nových projektech vytvořených Visual Studio 2017 verze 15.5 a novější verze. Ve výchozím nastavení není nastavena v dřívějších verzích. Pokud je tato možnost nastavena, kompilátor generuje diagnostické chyby nebo upozornění, když jsou v kódu zjištěny nestandardní jazykové konstrukce, včetně některých běžných chyb v kódu před C++11.

**Možnost /tolerantní-** je kompatibilní s téměř všemi soubory hlaviček z nejnovějších sad Windows, jako je například Sada Pro vývoj softwaru (SDK) nebo Windows Driver Kit (WDK), počínaje sadou Windows Fall Creators SDK (10.0.16299.0). Starší verze sady SDK může selhat kompilovat pod **/tolerantní-** z různých důvodů shody zdrojového kódu. Kompilátor a sady SDK dodávají v různých časových osách vydání, proto existují některé zbývající problémy. Konkrétní problémy se soubory záhlaví najdete v [tématu Problémy s hlavičkou Windows](#windows-header-issues) níže.

**/permissive-** - Nastaví [/Zc:referenceBinding](zc-referencebinding-enforce-reference-binding-rules.md), [/Zc:strictStrings](zc-strictstrings-disable-string-literal-type-conversion.md)a [/Zc:rvalueCast](zc-rvaluecast-enforce-type-conversion-rules.md) možnosti přizpůsobení chování. Tyto možnosti výchozí neodpovídající chování. Můžete předat konkrétní **/Zc** možnosti po **/tolerantní-** na příkazovém řádku přepsat toto chování.

Ve verzích kompilátoru začínajícív sadě Visual Studio 2017 verze 15.3 možnost **/tolerantní-** nastaví možnost [/Zc:ternary.](zc-ternary.md) Kompilátor také implementuje další požadavky na dvoufázové vyhledávání názvů. Pokud je nastavena možnost **/tolerantní-** kompilátor analyzuje definice šablony funkcí a třídy a identifikuje závislé a nezávislé názvy použité v šablonách. V této verzi se provádí pouze analýza závislostí názvů.

Rozšíření specifická pro prostředí a jazykové oblasti, které norma ponechává na implementaci, nejsou ovlivněny **/tolerantní-**. Například microsoft specifické `__declspec`, konvence volání a strukturované výjimky zpracování klíčových slov a formulační pragma směrnic nebo atributy nejsou označeny kompilátorem v **/tolerantní-** režimu.

Možnost **/tolerantní-** používá podporu shody v aktuální verzi kompilátoru k určení, které jazykové konstrukce jsou nevyhovující. Tato možnost neurčuje, pokud váš kód odpovídá konkrétní verzi standardu C++. Chcete-li povolit veškerou implementovanou podporu kompilátoru pro nejnovější koncept standardu, použijte [možnost /std:latest.](std-specify-language-standard-version.md) Chcete-li omezit podporu kompilátoru na aktuálně implementovaný standard Jazyka C++17, použijte možnost [/std:c++17.](std-specify-language-standard-version.md) Chcete-li omezit podporu kompilátoru tak, aby lépe odpovídala standardu C++14, použijte možnost [/std:c++14,](std-specify-language-standard-version.md) která je výchozí.

Ne všechny C++ 11, C ++ 14 nebo C ++ 17 standardy vyhovující kód je podporován kompilátorem MSVC ve všech verzích Visual Studio 2017. V závislosti na verzi sady Visual Studio **/tolerantní-** možnost nemusí zjistit problémy týkající se některých aspektů dvoufázového vyhledávání názvů, vazby non-const odkaz na dočasné, považovat kopii init jako přímé init, povolení více uživatelem definované převody v inicializaci nebo alternativní tokeny pro logické operátory a další nepodporované oblasti shody. Další informace o problémech s kondenzací v jazyce Visual C++ naleznete [v tématu Nestandardní chování](../../cpp/nonstandard-behavior.md). Chcete-li získat co nejvíce z **/tolerantní-**, aktualizujte Visual Studio na nejnovější verzi.

### <a name="how-to-fix-your-code"></a>Jak opravit kód

Zde jsou některé příklady kódu, který je zjištěn jako nevyhovující při použití **/tolerantní-**, spolu s navrhovanými způsoby, jak problémy vyřešit.

#### <a name="use-default-as-an-identifier-in-native-code"></a>Použít výchozí jako identifikátor v nativním kódu

```cpp
void func(int default); // Error C2321: 'default' is a keyword, and
                        // cannot be used in this context
```

#### <a name="look-up-members-in-dependent-base"></a>Vyhledat členy v závislé základně

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

#### <a name="use-of-qualified-names-in-member-declarations"></a>Použití kvalifikovaných jmen v prohlášeních členů

```cpp
struct A {
    void A::f() { } // error C4596: illegal qualified name in member
                    // declaration.
                    // Remove redundant 'A::' to fix.
};
```

#### <a name="initialize-multiple-union-members-in-a-member-initializer"></a>Inicializovat více členů sjednocení v inicializátoru člena

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

#### <a name="hidden-friend-name-lookup-rules"></a>Pravidla vyhledávání skrytých jmen přátel

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
    f(p); // Hidden friend now found via argument-dependent lookup.
}
```

#### <a name="use-scoped-enums-in-array-bounds"></a>Použití výčtů s vymezením v mezích pole

```cpp
enum class Color {
    Red, Green, Blue
};

int data[Color::Blue]; // error C3411: 'Color' is not valid as the size
                       // of an array as it is not an integer type.
                       // Cast to type size_t or int to fix.
```

#### <a name="use-for-each-in-native-code"></a>Použít pro každou v nativním kódu

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

#### <a name="use-of-atl-attributes"></a>Použití atributů knihovny ATL

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

#### <a name="ambiguous-conditional-operator-arguments"></a>Nejednoznačné argumenty podmíněného operátoru

Ve verzích kompilátoru před Visual Studio 2017 verze 15.3 kompilátor přijal argumenty `?:` podmíněného operátoru (nebo ternárního operátoru), které standard považuje za nejednoznačné. V **/tolerantní-** režimkompilátor nyní vydává jednu nebo více diagnostiky v případech, které byly kompilovány bez diagnostiky v předchozích verzích.

Běžné chyby, které mohou být výsledkem této změny patří:

- chyba C2593: 'operátor?' je nejednoznačný

- error C2679: binary '?': nebyl nalezen žádný operátor, který by vzal pravostranný operand typu 'B' (nebo neexistuje žádný přijatelný převod)

- error C2678: binary '?': nebyl nalezen žádný operátor, který by vzal levostranný operand typu 'A' (nebo neexistuje žádný přijatelný převod)

- chyba C2446: ':': žádný převod z 'B' na 'A'

Typický vzor kódu, který může způsobit tento problém je, když některé třídy C poskytuje jak neexplicitní konstruktor z jiného typu T a neexplicitní operátor převodu na typ T. V tomto případě jsou platné převody jak převod druhého argumentu na typ třetího argumentu, tak převod třetího argumentu na typ druhého argumentu. Vzhledem k tomu, že oba jsou platné, je to nejednoznačné podle standardu.

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

Existuje důležitá výjimka z tohoto společného vzoru, když T představuje jeden z `const char *` `const char16_t *`typů řetězců ukončených null (například , , a tak dále) a skutečný argument `?:` je literál řetězce odpovídajícího typu. C++17 změnil sémantiku z C++14. V důsledku toho je kód v příkladu 2 přijat pod **/std:c++14** a odmítnut pod **/std:c++17** při použití **/Zc:ternary** nebo **/tolerantní-** .

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

Jiný případ, kdy se mohou zobrazit chyby `void`je v podmíněné operátory s jedním argumentem typu . Tento případ může být běžné v ASSERT-jako makra.

```cpp
// Example 3: void arguments
void myassert(const char* text, const char* file, int line);
// Accepted when /Zc:ternary or /permissive- is not used:
#define ASSERT_A(ex) (void)((ex) ? 1 : myassert(#ex, __FILE__, __LINE__))
// Accepted always:
#define ASSERT_B(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))
```

Můžete také vidět chyby v metaprogramování šablony, kde podmíněné typy výsledků operátoru se mohou měnit pod **/Zc:ternary** a **/tolerantní-**. Jedním ze způsobů, jak tento problém vyřešit, je použití [std::remove_reference](../../standard-library/remove-reference-class.md) na výsledný typ.

```cpp
// Example 4: different result types
extern bool cond;
extern int count;
char  a = 'A';
const char  b = 'B';
decltype(auto) x = cond ? a : b; // char without, const char& with /Zc:ternary
const char (&z)[2] = count > 3 ? "A" : "B"; // const char* without /Zc:ternary
```

#### <a name="two-phase-name-look-up"></a>Dvoufázové vyhledávání názvů

Když **/tolerantní-** možnost je nastavena, kompilátor analyzuje definice funkce a třídy šablony, identifikace závislé a nezávislé názvy používané v šablonách, jak je požadováno pro dvoufázové vyhledávání názvů. Ve Visual Studiu 2017 verze 15.3 se provádí analýza závislostí názvů. Zejména nezávislé názvy, které nejsou deklarovány v kontextu definice šablony způsobit diagnostickou zprávu, jak to vyžadují standardy ISO C++. V sadě Visual Studio 2017 verze 15.7, vazby nezávislých názvů, které vyžadují vyhledávání závislé na argumentech v kontextu definice se také provádí.

```cpp
// dependent base
struct B {
    void g() {}
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

Pokud chcete starší chování pro dvoufázové vyhledávání, ale jinak chcete **/tolerantní-** chování, přidejte **/Zc:twoPhase-** možnost.

### <a name="windows-header-issues"></a>Problémy se záhlavím systému Windows

**Možnost /tolerantní-** je příliš přísná pro verze sad Windows Kit před windows fall creators update sdk (10.0.16299.0) nebo Windows Driver Kit (WDK) verze 1709. Doporučujeme aktualizovat na nejnovější verze sad Windows Kitů, abyste mohli používat **/tolerantní-** v kódu ovladače systému Windows nebo zařízení.

Některé soubory hlaviček v sada Windows z dubna 2018 Update SDK (10.0.17134.0), Windows Fall Creators Update SDK (10.0.16299.0) nebo Windows Driver Kit (WDK) 1709, stále mají problémy, které je činí nekompatibilními s použitím **/permissive-**. Chcete-li tyto problémy vyřešit, doporučujeme omezit použití těchto záhlaví pouze na ty soubory zdrojového kódu, které je vyžadují, a odebrat **možnost /tolerantní-** při kompilaci těchto konkrétních souborů zdrojového kódu.

Tyto hlavičky WinRT WRL vydané v sada Windows z dubna 2018 update SDK (10.0.17134.0) nejsou čisté s **/tolerantní-**. Chcete-li tyto problémy vyřešit, nepoužívejte **/tolerantní-**, nebo použijte **/tolerantní-** s **/Zc:twoPhase-** při práci s těmito záhlavími:

- Problémy v winrt/wrl/async.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(483): error C3861: 'TraceDelegateAssigned': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(491): error C3861: 'CheckValidStateForDelegateCall': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(509): error C3861: 'TraceProgressNotificationStart': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(513): error C3861: 'TraceProgressNotificationComplete': identifier not found
   ```

- Vydání v winrt/wrl/implements.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\winrt\wrl\implements.h(2086): error C2039: 'SetStrongReference': is not a member of 'Microsoft::WRL::Details::WeakReferenceImpl'
   ```

Tyto hlavičky uživatelského režimu vydané v sada Windows z dubna 2018 update SDK (10.0.17134.0) nejsou čisté s **/tolerantní-**. Chcete-li tyto problémy vyřešit, nepoužívejte **/tolerantní-** při práci s těmito záhlavími:

- Problémy v um/Tune.h

   ```Output
   C:\ProgramFiles(x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(139): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(559): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): note: 'Release': function declaration must be available as none of the arguments depend on a template parameter
   ```

- Vydání v um/spddkhlp.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\spddkhlp.h(759): error C3861: 'pNode': identifier not found
   ```

- Problémy v um/refptrco.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(179): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(342): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(395): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   ```

Tyto problémy jsou specifické pro záhlaví uživatelského režimu v sada Windows Fall Creators Update SDK (10.0.16299.0):

- Problém v um/Query.h

   Při použití **přepínače kompilátoru /tolerantní,** `tagRESTRICTION` struktura není kompilovat z důvodu case(RTOr) člen 'nebo'.

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

   Chcete-li tento problém vyřešit, kompilujte soubory, které obsahují Query.h bez **možnosti /tolerantní-** .

- Vydání v um/cellularapi_oem.h

   Při použití **přepínače kompilátoru /tolerantní,** `enum UICCDATASTOREACCESSMODE` dopředné prohlášení způsobí upozornění:

   ```cpp
   typedef enum UICCDATASTOREACCESSMODE UICCDATASTOREACCESSMODE; // C4471
   ```

   Forward deklarace unscoped výčtu je rozšíření společnosti Microsoft. Chcete-li tento problém vyřešit, kompilujte soubory, které obsahují cellularapi_oem.h bez **možnosti /tolerantní-** nebo použijte možnost [/wd](compiler-option-warning-level.md) k umlčení upozornění C4471.

- Vydání v um/omscript.h

   V jazyce C++03 je převod z literálu řetězce na BSTR (což je typedef na 'wchar_t *') je zastaralé, ale povolené. V jazyce C++11 již není převod povolen.

   ```cpp
   virtual /* [id] */ HRESULT STDMETHODCALLTYPE setExpression(
       /* [in] */ __RPC__in BSTR propname,
       /* [in] */ __RPC__in BSTR expression,
       /* [in][defaultvalue] */ __RPC__in BSTR language = L"") = 0; // C2440
   ```

   Chcete-li tento problém vyřešit, kompilujte soubory, které obsahují omscript.h bez **/tolerantní-** možnost, nebo použijte **/Zc:strictStrings-** místo.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

V visual tase 2017 verze 15.5 a novější chod pomocí tohoto postupu:

1. Otevřete dialogové okno **Stránky vlastností** projektu.

1. Vyberte stránku **vlastností Vlastnosti** > **jazyka** **C/C++.** > 

1. Změňte hodnotu vlastnosti **režimu shody** na **Hodnotu Ano (/tolerantní-)**. Chcete-li změny uložit, zvolte **OK** nebo **Použít.**

Ve verzích před Visual Studio 2017 verze 15.5 použijte tento postup:

1. Otevřete dialogové okno **Stránky vlastností** projektu.

1. Vyberte stránku **vlastností Vlastnosti** > konfigurace**C/C++** > **.**

1. Do pole **Další možnosti** zadejte možnost **/permisivní** kompilátor. Chcete-li změny uložit, zvolte **OK** nebo **Použít.**

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru MSVC](compiler-options.md)\
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
