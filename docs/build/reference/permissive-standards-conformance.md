---
title: / permissive-(shoda se standardy)
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
ms.openlocfilehash: 05089ef4f0a516f932d82f13be979da572701ae2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320042"
---
# <a name="permissive--standards-conformance"></a>/ permissive-(shoda se standardy)

Zadejte režim přizpůsobení standardy pro kompilátor. Pomocí této možnosti můžete zjistit a opravit problémech přizpůsobení v kódu, aby bylo více správné a větší přenositelnost.

## <a name="syntax"></a>Syntaxe

> **/permissive-**

## <a name="remarks"></a>Poznámky

Tato možnost je podporována v sadě Visual Studio 2017 nebo novější.

Můžete použít **/ permissive-** – možnost kompilátoru k určení chování kompilátoru vyhovující standardům. Tato možnost zakáže povolující chování a nastaví [/Zc](zc-conformance.md) – možnosti kompilátoru pro striktní shodu. V integrovaném vývojovém prostředí tato možnost také vytvoří podtržení nonkonformní kódu technologie IntelliSense modul.

Ve výchozím nastavení **/ permissive-** v nové projekty vytvořené pomocí sady Visual Studio 2017 verze 15.5 a novějších verzích je nastavená možnost. Ve výchozím nastavení v dřívějších verzích není nastavena. Když je tato možnost nastavená, kompilátor vygeneruje diagnostických chyby nebo upozornění při nestandardní jazykové konstrukce jsou zjištěny ve vašem kódu, včetně některých běžných chyb v pre-C ++ 11 kódu.

**/ Permissive-** možnost je kompatibilní s téměř všechny soubory hlavičky z nejnovější sady Windows, jako je například Software Development Kit (SDK) nebo Windows Driver Kit (WDK), od Windows Fall Creators SDK (10.0.16299.0). Starší verze sady SDK se pravděpodobně nezdaří zkompilovat v rámci **/ permissive-** různé zdroje důvodů shodu kódu. Kompilátor a sady SDK příjemce na časové ose jinou verzi, proto nejsou některé zbývající problémy. Problémy s konkrétní záhlaví souboru, naleznete v tématu [problémy záhlaví Windows](#windows-header-issues) níže.

**/ Permissive-** sady možností [/Zc: referencebinding](zc-referencebinding-enforce-reference-binding-rules.md), [/Zc: strictstrings](zc-strictstrings-disable-string-literal-type-conversion.md), a [/Zc: rvaluecast](zc-rvaluecast-enforce-type-conversion-rules.md) možnosti vyhovující chování. Výchozí chování nonkonformní tyto možnosti. Můžete předat konkrétní **/Zc** možnosti po **/ permissive-** na příkazový řádek pro toto chování přepsat.

Ve verzích od kompilátoru v sadě Visual Studio 2017 verze 15.3 **/ permissive-** sady možností [/Zc: ternary](zc-ternary.md) možnost. Kompilátor také implementuje další požadavky na název pro dvoufázové vyhledávání. Když **/ permissive-** nastavena možnost, kompilátor analyzuje definice šablony funkce a třídy a identifikuje nezávislé a závislé názvů používaných v šablonách. V této verzi se provádí pouze název analýzu závislostí.

Rozšíření specifické pro prostředí a jazyk oblastí, které standardní opustí až po provedení nejsou ovlivněny **/ permissive-**. Například specifické pro společnost Microsoft `__declspec`, konvence volání a klíčová slova a direktivy pragma specifických pro kompilátor nebo atributy zpracování strukturovaných výjimek nejsou označeny příznakem kompilátorem v **/ permissive-** režimu.

**/ Permissive-** možnost využívá podporu shoda v aktuální verzi kompilátoru k určení, které jazykové konstrukce jsou nevyhovující. Možnost určí, jestli váš kód odpovídá na konkrétní verzi jazyka C++ standard. Chcete-li povolit všechny implementované kompilátoru podporu pro nejnovější koncept standardu, použijte [/std:latest](std-specify-language-standard-version.md) možnost. Chcete-li omezit podporu kompilátoru aktuální implementace standardu C ++ 17, použijte [/std: c ++ 17](std-specify-language-standard-version.md) možnost. Chcete-li omezit podporu kompilátoru tak, aby lépe odpovídaly standard C ++ 14, použijte [/std: c ++ 14](std-specify-language-standard-version.md) možnost, která je výchozí nastavení.

Ne všechny C ++ 11, C ++ 14 nebo C ++ 17 vyhovující standardům kódu je podporována kompilátorem MSVC se všemi verzemi sady Visual Studio 2017. V závislosti na verzi sady Visual Studio **/ permissive-** možnost nemusí rozpoznat problémy týkající se některé aspekty dvoufázové vyhledávání názvů vazby nekonstantní odkaz na dočasný, zpracuje kopírování inicializace jako přímé init, povolení více uživatelem definovaných převodů inicializace nebo alternativní tokeny pro logické operátory a dalších oblastí shoda není podporováno. Další informace o problémech přizpůsobení v aplikaci Visual C++, naleznete v tématu [nestandardní chování](../../cpp/nonstandard-behavior.md). Chcete-li získat maximum z **/ permissive-**, aktualizujte na nejnovější verzi sady Visual Studio.

### <a name="how-to-fix-your-code"></a>Postup opravy kódu

Tady je několik příkladů kódu, který je rozpoznán jako nevyhovující při použití **/ permissive-**, spolu s doporučené způsoby, jak vyřešit problémy.

#### <a name="use-default-as-an-identifier-in-native-code"></a>Použít výchozí jako identifikátor v nativním kódu

```cpp
void func(int default); // Error C2321: 'default' is a keyword, and
                        // cannot be used in this context
```

#### <a name="look-up-members-in-dependent-base"></a>Vyhledání členy v závislé base

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

#### <a name="use-of-qualified-names-in-member-declarations"></a>Použijte kvalifikované názvy v deklaracích členů

```cpp
struct A {
    void A::f() { } // error C4596: illegal qualified name in member
                    // declaration.
                    // Remove redundant 'A::' to fix.
};
```

#### <a name="initialize-multiple-union-members-in-a-member-initializer"></a>Inicializovat více členy, které jsou v inicializátoru člena sjednocení.

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

#### <a name="hidden-friend-name-lookup-rules"></a>Pravidla vyhledávání název skrytou přítele

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

#### <a name="use-scoped-enums-in-array-bounds"></a>Použití oboru výčtů v hranice pole

```cpp
enum class Color {
    Red, Green, Blue
};

int data[Color::Blue]; // error C3411: 'Color' is not valid as the size
                       // of an array as it is not an integer type.
                       // Cast to type size_t or int to fix.
```

#### <a name="use-for-each-in-native-code"></a>Použijte pro každý v nativním kódu

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

#### <a name="use-of-atl-attributes"></a>Používání atributů ATL

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

#### <a name="ambiguous-conditional-operator-arguments"></a>Argumenty nejednoznačný podmíněný operátor

Ve verzích kompilátoru před Visual Studio 2017 verze 15.3, kompilátor přijmout argumenty pro podmíněný operátor (nebo tříhodnotový operátor) `?:` , které jsou považovány za nejednoznačné Standard. V **/ permissive-** režimu, kompilátor nyní vyvolá jednu nebo více diagnostiky v případech, kdy se zkompiloval bez diagnostiky v dřívějších verzích.

Běžné chyby, které mohou být důsledkem této změny patří:

- Chyba C2593: 'operator'? je nejednoznačný

- Chyba C2679: binární '?': nenašel se žádný operátor, který by zpracovával pravý operand typu "B" (nebo neexistuje žádný přijatelný převod)

- Chyba C2678: binární '?': nenašel se žádný operátor, který by zpracovával levý operand typu "A" (nebo neexistuje žádný přijatelný převod)

- Chyba C2446: ":": žádný převod z "B" na "A"

Vzor typické kód, který může způsobit potíže při některých tříd jazyka C poskytuje z jiného typu T neexplicitní konstruktor a operátor bez explicitního převodu typu T. Platné převody jsou v tomto případě převodu druhý argument typu třetí argument a třetí argument převodu na typ druhého argumentu. Protože obě jsou platné, je nejednoznačný podle standardu.

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

Je důležité výjimky tohoto společného modelu při T představuje jeden z typů řetězec zakončený hodnotou null (například `const char *`, `const char16_t *`, a tak dále) a skutečný argument `?:` není řetězcový literál odpovídající typu. C ++ 17 se změnila sémantiku z C ++ 14. V důsledku toho je v části přijato kódem v příkladu 2 **/std: c ++ 14** a zamítnutých podle **/std: c ++ 17** při **/Zc: ternary** nebo **/permissive-** se používá.

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

Dalším užitečným, kde se zobrazí chyby je v podmíněných operátorů s jedním argumentem typu `void`. Tento případ může běžně docházet ve vyhodnocení jako makra.

```cpp
// Example 3: void arguments
void myassert(const char* text, const char* file, int line);
// Accepted when /Zc:ternary or /permissive- is not used:
#define ASSERT_A(ex) (void)((ex) ? 1 : myassert(#ex, __FILE__, __LINE__))
// Accepted always:
#define ASSERT_B(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))
```

Může se také zobrazí chyby v metaprogramování, kde typy výsledků podmiňovací operátor může změnit v části **/Zc: ternary** a **/ permissive-**. Jeden ze způsobů, jak vyřešit tento problém je použití [std::remove_reference](../../standard-library/remove-reference-class.md) na výsledný typ.

```cpp
// Example 4: different result types
extern bool cond;
extern int count;
char  a = 'A';
const char  b = 'B';
decltype(auto) x = cond ? a : b; // char without, const char& with /Zc:ternary
const char (&z)[2] = count > 3 ? "A" : "B"; // const char* without /Zc:ternary
```

#### <a name="two-phase-name-look-up"></a>Název pro dvoufázové vyhledávání

Když **/ permissive-** nastavena možnost, kompilátor analyzuje funkce a třídy definice šablon identifikace nezávislé a závislé názvů používaných v šablonách podle potřeby pro název pro dvoufázové vyhledávání. V sadě Visual Studio 2017 verze 15.3 se provádí analýzu závislostí název. Nezávislé názvy, které nejsou deklarovány v rámci definice šablony zejména způsobit diagnostickou zprávu znamének podle normy ISO C++. V sadě Visual Studio 2017 verze 15.7 se taky dělá vazby závislé na jiné názvy, které vyžadují vyhledávání závislého na argumentu v rámci definice.

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

Pokud chcete použít starší verzi chování pro dvoufázové vyhledávání, ale jinak mají **/ permissive-** chování, přidejte **/Zc:twoPhase-** možnost.

### <a name="windows-header-issues"></a>Problémy záhlaví Windows

**/ Permissive-** možnost je příliš přísné pro verze sady Windows než Windows Fall Creators Update SDK (10.0.16299.0) nebo Windows Driver Kit (WDK) verze 1709. Doporučujeme aktualizovat na nejnovější verze sady Windows Chcete-li použít **/ permissive-** ve vašem kódu ovladače Windows nebo zařízení.

Některé hlavičkových souborů ve Windows dubna 2018 Update SDK (10.0.17134.0), Windows Fall Creators Update SDK (10.0.16299.0) nebo Windows Driver Kit (WDK) 1709, ještě další problémy, které je znekompatibilnit použití **/permissive-**. Chcete-li tyto problémy obejít, doporučujeme omezit použití těchto hlaviček pouze těchto souborů se zdrojovým kódem, které požadují a odeberte **/ permissive-** možnost při kompilaci kódu konkrétní zdrojové soubory.

Tyto hlavičky knihovny WRL WinRT vydané v Windows. dubna 2018 Update SDK (10.0.17134.0) nejsou s čistou **/ permissive-**. Chcete-li tyto problémy vyřešit, buď nepoužívejte **/ permissive-**, nebo použijte **/ permissive-** s **/Zc:twoPhase-** při práci s těmito záhlavími:

- Problémy v winrt/wrl/async.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(483): error C3861: 'TraceDelegateAssigned': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(491): error C3861: 'CheckValidStateForDelegateCall': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(509): error C3861: 'TraceProgressNotificationStart': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(513): error C3861: 'TraceProgressNotificationComplete': identifier not found
   ```

- Problém při winrt/wrl/implements.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\winrt\wrl\implements.h(2086): error C2039: 'SetStrongReference': is not a member of 'Microsoft::WRL::Details::WeakReferenceImpl'
   ```

Tyto hlavičky uživatelského režimu vydání v Windows. dubna 2018 Update SDK (10.0.17134.0) nejsou s čistou **/ permissive-**. Chcete-li vyřešit tyto problémy, nepoužívejte **/ permissive-** při práci s těmito záhlavími:

- Problémy v um/Tune.h

   ```Output
   C:\ProgramFiles(x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(139): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(559): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): note: 'Release': function declaration must be available as none of the arguments depend on a template parameter
   ```

- Problém při um/spddkhlp.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\spddkhlp.h(759): error C3861: 'pNode': identifier not found
   ```

- Problémy v um/refptrco.h

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(179): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(342): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(395): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   ```

Tyto problémy jsou specifické pro záhlaví uživatelského režimu ve Windows Fall Creators Update SDK (10.0.16299.0):

- Problém při um/Query.h

   Při použití **/ permissive-** přepínač kompilátoru `tagRESTRICTION` struktura nezkompiluje kvůli case(RTOr) člena 'nebo'.

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

   Chcete-li tento problém vyřešit, kompilovat soubory, které zahrnují Query.h bez **/ permissive-** možnost.

- Problém při um/cellularapi_oem.h

   Při použití **/ permissive-** přepínače kompilátoru, Dopředná deklarace `enum UICCDATASTOREACCESSMODE` způsobí, že upozornění:

   ```cpp
   typedef enum UICCDATASTOREACCESSMODE UICCDATASTOREACCESSMODE; // C4471
   ```

   Dopředná deklarace výčtu mimo obor je rozšířením společnosti Microsoft. Chcete-li tento problém vyřešit, kompilovat soubory, které zahrnují cellularapi_oem.h bez **/ permissive-** , nebo použitím [/wd](compiler-option-warning-level.md) možnost nečinnosti upozornění C4471.

- Problém při um/omscript.h

   V C ++ 03, převod z řetězcového literálu na BSTR (což je typedef pro "wchar_t *") je zastaralý, ale povoleno. V C ++ 11 převod již není povolena.

   ```cpp
   virtual /* [id] */ HRESULT STDMETHODCALLTYPE setExpression(
       /* [in] */ __RPC__in BSTR propname,
       /* [in] */ __RPC__in BSTR expression,
       /* [in][defaultvalue] */ __RPC__in BSTR language = L"") = 0; // C2440
   ```

   Chcete-li tento problém vyřešit, kompilovat soubory, které zahrnují omscript.h bez **/ permissive-** , nebo použitím **/Zc:strictStrings-** místo.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

V sadě Visual Studio 2017 verze 15.5 a novějších verzích použijte tento postup:

1. Otevřete svůj projekt **stránky vlastností** dialogové okno.

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **jazyk** stránku vlastností.

1. Změnit **režim přizpůsobení** hodnoty vlastnosti **Ano (/ permissive-)**. Zvolte **OK** nebo **použít** uložte provedené změny.

Ve verzích před Visual Studio 2017 verze 15.5 použijte tento postup:

1. Otevřete svůj projekt **stránky vlastností** dialogové okno.

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Zadejte **/ permissive-** – možnost kompilátoru v **další možnosti** pole. Zvolte **OK** nebo **použít** uložte provedené změny.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

- [Parametry kompilátoru MSVC](compiler-options.md)
- [Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
