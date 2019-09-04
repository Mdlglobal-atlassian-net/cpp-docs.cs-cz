---
title: '/Experimental: preprocesor (povolit režim shody preprocesoru)'
description: 'Použijte možnost kompilátoru/Experimental: preprocesor, chcete-li povolit experimentální podporu kompilátoru pro standardní vyhovující preprocesor.'
ms.date: 09/03/2019
f1_keywords:
- preprocessor
- /experimental:preprocessor
helpviewer_keywords:
- preprocessor conformance
- /experimental:preprocessor
- Enable preprocessor conformance mode
ms.openlocfilehash: 3055cfa2a32d1d668dbe0c51b5542415b5bb0af4
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70294421"
---
# <a name="experimentalpreprocessor-enable-preprocessor-conformance-mode"></a>/Experimental: preprocesor (povolit režim shody preprocesoru)

Tato možnost umožňuje experimentálního preprocesoru založeného na tokenech, který vyhovuje standardům C++ 11, včetně funkcí preprocesoru C99.

## <a name="syntax"></a>Syntaxe

> **/Experimental: preprocesor** [ **-** ]

## <a name="remarks"></a>Poznámky

Použijte možnost kompilátoru **/Experimental: preprocesor** pro povolení experimentálního vyhovujícího preprocesoru. Můžete použít **/Experimental: preprocesor –** možnost k explicitnímu určení tradičního preprocesoru.

Možnost **/Experimental: preprocesor** je k dispozici počínaje verzí Visual Studio 2017 verze 15,8.

Můžete zjistit, který preprocesor se používá v době kompilace. Ověřte hodnotu předdefinovaného makra [ \_MSVC\_tradiční](../../preprocessor/predefined-macros.md) a sdělte, zda se tradiční preprocesor používá. Toto makro je nastaveno na nepodmíněné verze kompilátoru, který ho podporuje, nezávisle na tom, který preprocesor je vyvolán. Jeho hodnota je 1 pro tradiční preprocesor. Je 0 pro vyhovující experimentální preprocesor:

```cpp
#if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
// Logic using the traditional preprocessor
#else
// Logic using cross-platform compatible preprocessor
#endif
```

### <a name="behavior-changes-in-the-experimental-preprocessor"></a>Změny chování v experimentálním preprocesoru

Zde jsou některé z nejběžnějších nedokončených změn, které byly zjištěny v případě, že je povolen režim shody preprocesoru:

#### <a name="macro-comments"></a>Komentáře makra

Tradiční preprocesor používá místo tokenů preprocesoru znaková vyrovnávací paměť. To umožňuje některé neobvyklé chování, jako je například tento štych preprocesoru komentáře, který nefunguje s vyhovujícím preprocesorem:

```cpp
#if DISAPPEAR
#define DISAPPEARING_TYPE /##/
#else
#define DISAPPEARING_TYPE int
#endif

// myVal disappears when DISAPPEARING_TYPE is turned into a comment
// To make standards compliant, wrap the following line with the appropriate #if/#endif
DISAPPEARING_TYPE myVal;
```

#### <a name="string-prefixes-lval"></a>Předpony řetězců (L # Val)

Tradiční preprocesor nesprávně kombinuje předponu řetězce s výsledkem [operátoru převodu (#)](../../preprocessor/stringizing-operator-hash.md):

```cpp
#define DEBUG_INFO(val) L"debug prefix:" L#val
//                                       ^
//                                       this prefix

const wchar_t *info = DEBUG_INFO(hello world);
```

`L` Předpona je nepotřebná, protože sousední řetězcové literály jsou kombinovány po rozšíření makra. Zpětně kompatibilní oprava je změna definice na:

```cpp
#define DEBUG_INFO(val) L"debug prefix:" #val
//                                       ^
//                                       no prefix
```

Tento problém je také k dispozici v praktických makrech, která "převádějícím" je argumentem pro velký řetězcový literál:

```cpp
// The traditional preprocessor creates a single wide string literal token
#define STRING(str) L#str

// Potential fixes:
// Use string concatenation of L"" and #str to add prefix
// This works because adjacent string literals are combined after macro expansion
#define STRING1(str) L""#str

// Add the prefix after #str is stringized with additional macro expansion
#define WIDE(str) L##str
#define STRING2(str) WIDE(#str)

// Use concatenation operator ## to combine the tokens.
// The order of operations for ## and # is unspecified, although all compilers
// checked perform the # operator before ## in this case.
#define STRING3(str) L## #str
```

#### <a name="warning-on-invalid"></a>Upozornění na neplatné ##

Pokud [operátor vložení tokenu (# #)](../../preprocessor/token-pasting-operator-hash-hash.md) nevede k jednomu, platnému tokenu předzpracování, chování není definováno. Tradiční preprocesor bez upozornění nemůže kombinovat tokeny. Nový preprocesor se shoduje s chováním většiny ostatních kompilátorů a generuje diagnostiku.

```cpp
// The ## is unnecessary and doesn't result in a single preprocessing token.
#define ADD_STD(x) std::##x

// Declare a std::string
ADD_STD(string) s;
```

#### <a name="comma-elision-in-variadic-macros"></a>Čárka Elizi v makrech variadické

Vezměte v úvahu v následujícím příkladu:

```cpp
void func(int, int = 2, int = 3);
// This macro replacement list has a comma followed by __VA_ARGS__
#define FUNC(a, ...) func(a, __VA_ARGS__)
int main()
{
    // The following macro is replaced with:
    // func(10,20,30)
    FUNC(10, 20, 30);

    // A conforming preprocessor replaces the following macro with:
    // func(1, );
    // which results in a syntax error.
    FUNC(1, );
}
```

Všechny hlavní kompilátory mají rozšíření preprocesoru, které pomáhá vyřešit tento problém. Tradiční preprocesor MSVC vždy odebere čárky před prázdné `__VA_ARGS__` náhrady. Aktualizovaný preprocesor se podrobněji řídí chováním jiných oblíbených kompilátorů pro různé platformy. Aby byla čárka odebrána, argument variadické musí chybět, není pouze prázdný a musí být označen `##` operátorem:

```cpp
#define FUNC2(a, ...) func(a , ## __VA_ARGS__)
int main()
{
    // The variadic argument is missing in the macro being evoked
    // The comma is removed and replaced with:
    // func(1)
    FUNC2(1);

    // The variadic argument is empty, but not missing. (Notice the
    // comma in the argument list.) The comma isn't removed
    // when the macro is replaced:
    // func(1, )
    FUNC2(1, );
}
```

V nadcházejících standardech C + + 2a se tento problém vyřešil přidáním `__VA_OPT__`, který ještě není implementovaný.

#### <a name="macro-arguments-are-unpacked"></a>Argumenty makra jsou unpacked.

V tradičním preprocesoru, pokud makro předává některý z jeho argumentů jinému závislému makru, pak argument nezíská "unpacked", když je nahrazen. Obvykle se tato optimalizace neprojeví, ale může vést k neobvyklému chování:

```cpp
// Create a string out of the first argument, and the rest of the arguments.
#define TWO_STRINGS( first, ... ) #first, #__VA_ARGS__
#define A( ... ) TWO_STRINGS(__VA_ARGS__)

const char* c[2] = { A(1, 2) };
// Conformant preprocessor results:
// const char c[2] = { "1", "2" };
// Traditional preprocessor results, all arguments are in the first string:
// const char c[2] = { "1, 2", };
```

Při rozšiřování `A()`tradiční preprocesor přepošle všechny argumenty, které jsou `__VA_ARGS__` zabaleny do prvního argumentu `TWO_STRINGS`. Argument variadické argumentu `TWO_STRINGS` je prázdný, což způsobí, že `#first` výsledek bude `"1, 2"` spíše než pouze `"1"`. Možná vás zajímá, co se stalo s výsledkem `#__VA_ARGS__` v tradičním rozšíření preprocesoru. Pokud je parametr variadické prázdný, měla by být výsledkem prázdný řetězcový literál "". Z důvodu samostatného problému nebyl vygenerován prázdný token literálu řetězce.

#### <a name="rescanning-replacement-list-for-macros"></a>Znovu prohledat náhradní seznam pro makra

Po nahrazení makra se u výsledných tokenů znovu vyhledají další identifikátory maker, které se mají nahradit. Algoritmus opětovného prohledání používaný tradičním preprocesorem není vyhovující, jak je znázorněno v tomto příkladu na základě aktuálního kódu:

```cpp
#define CAT(a,b) a ## b
#define ECHO(...) __VA_ARGS__

// IMPL1 and IMPL2 are implementation details
#define IMPL1(prefix,value) do_thing_one( prefix, value)
#define IMPL2(prefix,value) do_thing_two( prefix, value)
// MACRO chooses the expansion behavior based on the value passed to macro_switch
#define DO_THING(macro_switch, b) CAT(IMPL, macro_switch) ECHO(( "Hello", b))

DO_THING(1, "World");
// Traditional preprocessor:
// do_thing_one( "Hello", "World");
// Conformant preprocessor:
// IMPL1 ( "Hello","World");
```

Chcete-li zjistit, co v tomto příkladu probíhá, rozdělíme rozšíření od `DO_THING`:

`DO_THING(1, "World")` ->
`CAT(IMPL, 1) ECHO(("Hello", "World"))`

Druhé, CAT je rozbalené:

`CAT(IMPL, 1)` -> `IMPL ## 1` -> `IMPL1`

Který do tohoto stavu vloží tokeny:

`IMPL1 ECHO(("Hello", "World"))`

Preprocesor vyhledá identifikátor `IMPL1`makra podobný funkci, ale není následován znakem "(", takže se nepovažuje za vyvolání makra jako funkce. Přesune se na následující tokeny a najde vyvolané makro `ECHO` podobné funkci:

`ECHO(("Hello", "World"))` -> `("Hello", "World")`

`IMPL1`se nikdy nepovažuje za rozšíření, takže úplný výsledek rozšíření je:

`IMPL1("Hello", "World");`

Makro lze upravit tak, aby se chovalo stejným způsobem v rámci experimentálního preprocesoru i tradičního preprocesoru. Řešením je přidat další vrstvu dereference:

```cpp
#define CAT(a,b) a##b
#define ECHO(...) __VA_ARGS__

// IMPL1 and IMPL2 are macros implementation details
#define IMPL1(prefix,value) do_thing_one( prefix, value)
#define IMPL2(prefix,value) do_thing_two( prefix, value)

#define CALL(macroName, args) macroName args
#define DO_THING_FIXED(a,b) CALL( CAT(IMPL, a), ECHO(( "Hello",b)))

DO_THING_FIXED(1, "World");
// macro expanded to:
// do_thing_one( "Hello", "World");
```

### <a name="conformance-mode-conformance"></a>Shoda režimu shody

Experimentální preprocesor ještě není dokončený a některé logiky direktiv preprocesoru se pořád vrátí k tradičnímu chování. Tady je částečný seznam neúplných funkcí:

- Podpora pro`_Pragma`
- Funkce c++ 20
- Další vylepšení diagnostiky
- Přepíná k řízení výstupu v části/E a/P.
- Chyba blokování zvýšení úrovně: Logické operátory v konstantních výrazech preprocesoru nejsou plně implementovány v novém preprocesoru. U některých `#if` direktiv se může nový preprocesor vrátit k tradičnímu preprocesoru. Tento efekt je patrné pouze v případě, že makra, která jsou nekompatibilní s tradičním preprocesorem, jsou rozbalena, což může nastat při sestavování zvýšení slotu preprocesoru.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte stránku vlastností **Konfigurace** > **C/C++**  > **příkazový řádek** .

1. Upravte vlastnost **Další možnosti** tak, aby zahrnovala **/Experimental: preprocesor** a pak zvolte **OK**.

## <a name="see-also"></a>Viz také:

[/Zc (shoda)](zc-conformance.md)
