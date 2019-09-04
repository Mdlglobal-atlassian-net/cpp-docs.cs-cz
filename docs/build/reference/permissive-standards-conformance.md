---
title: /permissive- (shoda se standardy)
ms.date: 03/08/2019
f1_keywords:
- /permissive
- VC.Project.VCCLCompilerTool.ConformanceMode
helpviewer_keywords:
- /permissive compiler options [C++]
- -permissive compiler options [C++]
- Standards conformance compiler options
- permissive compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: aca0fbc6a2ca36ceae26ba060b5bf92fea79c32c
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273729"
---
# <a name="permissive--standards-conformance"></a>/permissive- (shoda se standardy)

Zadejte režim shody standardů pro kompilátor. Tuto možnost použijte, když chcete identifikovat a opravit problémy s kompatibilitou ve vašem kódu, aby byly lépe správné a lépe přenositelné.

## <a name="syntax"></a>Syntaxe

> **/Permissive-**

## <a name="remarks"></a>Poznámky

Tato možnost je podporována v aplikaci Visual Studio 2017 nebo novější.

Pomocí možnosti kompilátoru **/Permissive-** můžete zadat chování kompilátoru vyhovující standardům. Tato možnost zakáže opravňující chování a nastaví možnosti kompilátoru [/Zc](zc-conformance.md) pro striktní shodu. V integrovaném vývojovém prostředí (IDE) Tato možnost také umožňuje, aby modul IntelliSense podtrhnout nevyhovující kód.

Ve výchozím nastavení je možnost **/Permissive-** nastavena v nových projektech vytvořených sadou Visual Studio 2017 verze 15,5 a novějšími verzemi. Ve výchozím nastavení se v dřívějších verzích nenastavuje. Když je tato možnost nastavena, kompilátor generuje diagnostické chyby nebo upozornění, pokud jsou ve vašem kódu zjištěny nestandardní jazykové konstrukce, včetně některých běžných chyb v kódu před C + + 11.

Možnost **/Permissive-** je kompatibilní s téměř všemi soubory hlaviček z nejnovějších sad Windows, jako je sada SDK (Software Development Kit) nebo sada Windows Driver Kit (WDK), počínaje verzí Windows v sadě Creators SDK (10.0.16299.0). Starší verze sady SDK se nemusí podařit zkompilovat do **/Permissive-** pro různé důvody shody zdrojového kódu. Kompilátor a sady SDK dodávají na různých časových osách vydaných verzí, proto existují některé zbývající problémy. Konkrétní problémy se soubory hlaviček najdete v [záhlaví Windows](#windows-header-issues) níže.

Možnost **/Permissive-** nastaví možnosti [/Zc: referenceBinding](zc-referencebinding-enforce-reference-binding-rules.md), [/Zc: strictStrings](zc-strictstrings-disable-string-literal-type-conversion.md)a [/Zc: rvalueCast](zc-rvaluecast-enforce-type-conversion-rules.md) pro vyhovující chování. Tyto možnosti jsou standardně nevyhovující chování. Můžete předat konkrétní možnosti **/Zc** po **/Permissive-** na příkazovém řádku, aby se toto chování potlačilo.

Ve verzích kompilátoru počínaje verzí Visual Studio 2017 verze 15,3 možnost **/Permissive-** nastaví možnost [/Zc: Ternární](zc-ternary.md) . Kompilátor také implementuje více požadavků pro vyhledávání názvů se dvěma fázemi. Pokud je nastavena možnost **/Permissive-** , kompilátor analyzuje funkce a definice šablon tříd a identifikuje závislé a nezávislé názvy používané v šablonách. V této verzi se provádí jenom analýza závislých názvů.

Rozšíření specifická pro prostředí a jazykové oblasti, které standardní verze ponechává až do implementace, nejsou ovlivněny **/Permissive-** . Například konvence volání specifická `__declspec`pro společnost Microsoft a strukturovaná klíčová slova strukturovaného zpracování výjimek a direktivy pragma specifické pro kompilátor nejsou příznakem kompilátoru v režimu **/Permissive-** .

Možnost **/Permissive-** používá podporu shody v aktuální verzi kompilátoru k určení, které jazykové konstrukce nejsou vyhovující. Možnost neurčuje, zda kód odpovídá určité verzi C++ Standard. Pokud chcete povolit veškerou implementovanou podporu kompilátoru pro nejnovější koncept standardu, použijte možnost [/std: nejnovější](std-specify-language-standard-version.md) . Chcete-li omezit podporu kompilátoru na aktuálně implementovaný Standard C++ 17, použijte možnost [/std: c++ 17](std-specify-language-standard-version.md) . Chcete-li omezit podporu kompilátoru na přesněji odpovídat standardu C++ 14, použijte možnost [/std: c++ 14](std-specify-language-standard-version.md) , což je výchozí hodnota.

Ne všechny standardy kódu C++ 11, C++ 14 nebo C++ 17 jsou podporovány kompilátorem MSVC ve všech verzích sady Visual Studio 2017. V závislosti na verzi sady Visual Studio nemusí možnost **/Permissive-** detekovat problémy týkající se některých aspektů dvou fází vyhledávání názvů, vázání nekonstantních odkazů na dočasné a zpracování příkazu copy init jako přímého příkazu init, který umožňuje více uživatelsky definovaných. převody v inicializačním nebo alternativním tokenech pro logické operátory a jiné nepodporované oblasti shody. Další informace o problémech s kompatibilitou ve vizuálu C++najdete v tématu [nestandardní chování](../../cpp/nonstandard-behavior.md). Pokud chcete získat maximum z **/Permissive-** , aktualizujte sadu Visual Studio na nejnovější verzi.

### <a name="how-to-fix-your-code"></a>Jak opravit kód

Tady je několik příkladů kódu, který se detekuje jako nevyhovující při použití **/Permissive-** , spolu s navrhovanými způsoby, jak tyto problémy vyřešit.

#### <a name="use-default-as-an-identifier-in-native-code"></a>Použít jako identifikátor v nativním kódu výchozí hodnotu

```cpp
void func(int default); // Error C2321: 'default' is a keyword, and
                        // cannot be used in this context
```

#### <a name="look-up-members-in-dependent-base"></a>Vyhledat členy v závislém základu

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

#### <a name="use-of-qualified-names-in-member-declarations"></a>Použití kvalifikovaných názvů v deklaracích členů

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

#### <a name="hidden-friend-name-lookup-rules"></a>Skrytá pravidla vyhledávání názvů přátel

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

#### <a name="use-scoped-enums-in-array-bounds"></a>Použít vymezené výčty v hranicích pole

```cpp
enum class Color {
    Red, Green, Blue
};

int data[Color::Blue]; // error C3411: 'Color' is not valid as the size
                       // of an array as it is not an integer type.
                       // Cast to type size_t or int to fix.
```

#### <a name="use-for-each-in-native-code"></a>Použít pro každý z nativního kódu

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

#### <a name="ambiguous-conditional-operator-arguments"></a>Dvojznačné argumenty podmíněného operátoru

Ve verzích kompilátoru před Visual Studio 2017 verze 15,3 kompilátor přijal argumenty pro podmíněný operátor (nebo Ternární operátor) `?:` , které jsou považovány za dvojznačné standardem. V režimu **/Permissive-** nyní kompilátor vydává jednu nebo více diagnostických nástrojů v případech, které byly zkompilovány bez diagnostiky v dřívějších verzích.

Mezi běžné chyby, které mohou nastat při této změně, patří:

- Chyba C2593: operátor? je dvojznačný

- Chyba C2679: binární '? ': nebyl nalezen žádný operátor, který by zpracovával pravý operand typu ' B ' (nebo neexistuje žádný přijatelný převod)

- Chyba C2678: binární '? ': nebyl nalezen žádný operátor, který by zpracovával levý operand typu ' A ' (nebo neexistuje žádný přijatelný převod).

- Chyba C2446: ': ': žádný převod z ' B ' na ' A '

Typický vzor kódu, který může být příčinou tohoto problému, je, že některé třídy C poskytují neexplicitní konstruktor z jiného typu T a neexplicitní operátor převodu na typ T. V tomto případě jsou platnými převody jak převod druhého argumentu na typ třetího argumentu, tak i převod třetího argumentu na typ druhého argumentu. Vzhledem k tomu, že obě jsou platné, je nejednoznačné podle standardu.

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

K tomuto běžnému vzoru má zásadní výjimku, pokud T představuje jeden z typů řetězců zakončených hodnotou null (například `const char *` `const char16_t *`,, a tak dále) a skutečný argument pro `?:` je řetězcový literál odpovídajícího typu. C++ 17 změnil sémantiku z C++ 14. V důsledku toho je kód v příkladu 2 přijatý v **/std: c++ 14** a zamítnutý v **/std: c++ 17** při použití **/Zc: Ternární** nebo **/Permissive-** .

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

Další případ, kde se mohou zobrazit chyby, je v podmíněných operátorech `void`s jedním argumentem typu. Tento případ může být běžný v makrech, jako je například vyhodnocení.

```cpp
// Example 3: void arguments
void myassert(const char* text, const char* file, int line);
// Accepted when /Zc:ternary or /permissive- is not used:
#define ASSERT_A(ex) (void)((ex) ? 1 : myassert(#ex, __FILE__, __LINE__))
// Accepted always:
#define ASSERT_B(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))
```

V šabloně metaprogramování šablonou mohou být zobrazeny také chyby, kde se typy výsledků podmíněného operátoru mohou změnit v části **/Zc: Ternární** a **/Permissive-** . Jedním ze způsobů, jak tento problém vyřešit, je použít pro výsledný typ [std:: remove_reference](../../standard-library/remove-reference-class.md) .

```cpp
// Example 4: different result types
extern bool cond;
extern int count;
char  a = 'A';
const char  b = 'B';
decltype(auto) x = cond ? a : b; // char without, const char& with /Zc:ternary
const char (&z)[2] = count > 3 ? "A" : "B"; // const char* without /Zc:ternary
```

#### <a name="two-phase-name-look-up"></a>Vyhledávací název se dvěma fázemi

Je-li nastavena možnost **/Permissive-** , kompilátor analyzuje funkce a definice šablon třídy, identifikuje závislé a nezávislé názvy používané v šablonách, jak je požadováno pro vyhledávání názvů se dvěma fázemi. V aplikaci Visual Studio 2017 verze 15,3 je provedena analýza závislosti názvů. Konkrétně nezávislé názvy, které nejsou deklarovány v kontextu definice šablony, způsobují diagnostické zprávy podle požadavků standardu ISO C++ . V aplikaci Visual Studio 2017 verze 15,7 jsou také provedeny vazby nezávislých názvů, které vyžadují vyhledávání závislé na argumentech v kontextu definice.

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

Pokud chcete starší chování při dvoufázovém vyhledávání, ale jinak chcete chování **/Permissive-** , přidejte parametr **/Zc: twoPhase-** Option.

### <a name="windows-header-issues"></a>Problémy s hlavičkou Windows

Možnost **/Permissive-** je pro verze sad Windows moc striktní, než Windows patří Creators Update SDK (10.0.16299.0) nebo Windows Driver Kit (WDK) verze 1709. Doporučujeme, abyste provedli aktualizaci na nejnovější verze sad Windows, aby bylo možné používat **/Permissive-** v kódu ovladače pro Windows nebo zařízení.

Některé hlavičkové soubory v sadě Windows duben 2018 Update SDK (10.0.17134.0), Windows patří Creators Update SDK (10.0.16299.0) nebo sada Windows Driver Kit (WDK) 1709, stále mají problémy, které je nekompatibilní s používáním **/Permissive-** . Chcete-li tyto problémy obejít, doporučujeme omezit použití těchto hlaviček pouze na ty soubory zdrojového kódu, které je vyžadují, a odebrat možnost **/Permissive-** při kompilaci těchto souborů se specifickým zdrojovým kódem.

Tato Hlavičková WRL WinRT vydaná v sadě Windows duben 2018 Update SDK (10.0.17134.0) se nečistí pomocí **/Permissive-** . Pokud chcete tyto problémy obejít, buď Nepoužívejte **/Permissive-** , nebo použijte **/Permissive-** s parametrem **/Zc: twoPhase –** při práci s těmito záhlavími:

- Problémy v WinRT/WRL/Async. h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(483): error C3861: 'TraceDelegateAssigned': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(491): error C3861: 'CheckValidStateForDelegateCall': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(509): error C3861: 'TraceProgressNotificationStart': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(513): error C3861: 'TraceProgressNotificationComplete': identifier not found
   ```

- Problém v WinRT/WRL/Implements. h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\winrt\wrl\implements.h(2086): error C2039: 'SetStrongReference': is not a member of 'Microsoft::WRL::Details::WeakReferenceImpl'
   ```

Tyto hlavičky uživatelských režimů vydané v sadě Windows duben 2018 Update SDK (10.0.17134.0) se nečistí pomocí **/Permissive-** . Pokud chcete tyto problémy obejít, nepoužívejte **/Permissive-** při práci s těmito hlavičkami:

- Problémy v um a ladit. h

   ```Output
   C:\ProgramFiles(x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(139): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(559): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): note: 'Release': function declaration must be available as none of the arguments depend on a template parameter
   ```

- Problém v um/spddkhlp. h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\spddkhlp.h(759): error C3861: 'pNode': identifier not found
   ```

- Problémy v um/refptrco. h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(179): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(342): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(395): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   ```

Tyto problémy se týkají hlaviček uživatelských režimů v sadě Windows Update Creators SDK (10.0.16299.0):

- Problém v um/dotaz. h

   Při použití přepínače `tagRESTRICTION` kompilátoru/Permissive-není struktura zkompilována v důsledku člena Case (RTOr) nebo.

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

   Chcete-li tento problém vyřešit, zkompilujte soubory, které zahrnují Query. h bez možnosti **/Permissive-** .

- Problém v um/cellularapi_oem. h

   Při použití přepínače kompilátoru **/Permissive-** se Dopředná deklarace `enum UICCDATASTOREACCESSMODE` vyvolá upozornění:

   ```cpp
   typedef enum UICCDATASTOREACCESSMODE UICCDATASTOREACCESSMODE; // C4471
   ```

   Dopředná deklarace výčtu bez oboru je rozšířením společnosti Microsoft. Chcete-li tento problém vyřešit, zkompilujte soubory, které zahrnují cellularapi_oem. h bez možnosti **/Permissive-** , nebo použijte možnost [/WD](compiler-option-warning-level.md) pro netiché upozornění C4471.

- Problém v um/omscript. h

   V jazyce C++ 03 je převod z řetězcového literálu na typ BSTR (který je typu typedef na wchar_t *) zastaralý, ale povolený. V jazyce C++ 11 již převod není povolen.

   ```cpp
   virtual /* [id] */ HRESULT STDMETHODCALLTYPE setExpression(
       /* [in] */ __RPC__in BSTR propname,
       /* [in] */ __RPC__in BSTR expression,
       /* [in][defaultvalue] */ __RPC__in BSTR language = L"") = 0; // C2440
   ```

   Chcete-li tento problém vyřešit, zkompilujte soubory, které zahrnují omscript. h bez možnosti **/Permissive-** , nebo použijte parametr **/Zc: strictStrings-** namísto.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

V aplikaci Visual Studio 2017 verze 15,5 a novější použijte tento postup:

1. Otevřete dialogové okno **stránky vlastností** projektu.

1. Vyberte stránku vlastností **Konfigurace** > **C/C++**  > **jazyk** .

1. Změňte hodnotu vlastnosti **Režim odpovídání** na **Ano (/Permissive-)** . Změny uložte kliknutím na **OK** nebo **použít** .

V části verze před Visual Studio 2017 verze 15,5 použijte tento postup:

1. Otevřete dialogové okno **stránky vlastností** projektu.

1. Vyberte stránku vlastností **Konfigurace** > **C/C++**  > **příkazový řádek** .

1. Do pole **Další možnosti** zadejte možnost kompilátoru **/Permissive-** . Změny uložte kliknutím na **OK** nebo **použít** .

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru MSVC](compiler-options.md)\
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
