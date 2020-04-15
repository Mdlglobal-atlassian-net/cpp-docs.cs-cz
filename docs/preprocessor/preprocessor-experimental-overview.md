---
title: Přehled experimentálního preprocesoru MSVC
description: Preprocesor MSVC je aktualizován pro shodu s c/c++ standardy.
ms.date: 02/09/2020
helpviewer_keywords:
- preprocessor, experimental
ms.openlocfilehash: 00c34ef75270e505d3781cf7eedf4d8aba95ee6e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337487"
---
# <a name="msvc-experimental-preprocessor-overview"></a>Přehled experimentálního preprocesoru MSVC

::: moniker range="vs-2015"

Visual Studio 2015 používá tradiční preprocesor, který neodpovídá standardnímu jazyce C++. Experimentální preprocesor je k dispozici v sadě Visual Studio 2017 a Visual Studio 2019 pomocí přepínače kompilátoru [/experimental:preprocessor.](../build/reference/experimental-preprocessor.md) Další informace o použití nového preprocesoru v sadě Visual Studio 2017 a Visual Studio 2019 jsou k dispozici. Chcete-li zobrazit dokumentaci k upřednostňované verzi sady Visual Studio, použijte ovládací prvek pro výběr **verze.** Nachází se v horní části obsahu na této stránce.

::: moniker-end

::: moniker range=">=vs-2017"

Aktualizujeme preprocesor Microsoft C++, abychom zlepšili shodu standardů, opravili dlouhodobé chyby a změnili některá chování, která jsou oficiálně nedefinovaná. Přidali jsme také novou diagnostiku, která varuje před chybami v definicích maker.

Tyto změny jsou k dispozici pomocí přepínače kompilátoru [/experimental:preprocessor](../build/reference/experimental-preprocessor.md) v sadě Visual Studio 2017 nebo Visual Studio 2019. Výchozí chování preprocesoru zůstává stejné jako v předchozích verzích.

Počínaje visual studio 2019 verze 16.5, experimentální preprocesor podpora pro standard C ++ 20 je funkce kompletní.

## <a name="new-predefined-macro"></a>Nové předdefinované makro

Můžete zjistit, který preprocesor se používá v době kompilace. Zkontrolujte hodnotu předdefinovaného makra [ \_MSVC\_TRADITIONAL](predefined-macros.md) a zjistěte, zda je používán tradiční preprocesor. Toto makro je nastaveno bezpodmínečně verzemi kompilátoru, které jej podporují, nezávisle na tom, který preprocesor je vyvolán. Jeho hodnota je 1 pro tradiční preprocesor. Je to 0 pro vyhovující preprocesor.

```cpp
#if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
// Logic using the traditional preprocessor
#else
// Logic using cross-platform compatible preprocessor
#endif
```

## <a name="behavior-changes-in-the-experimental-preprocessor"></a>Změny chování v experimentálním preprocesoru

Počáteční práce na experimentálním preprocesoru byla zaměřena na to, aby všechna rozšíření maker odpovídala standardu. Umožňuje používat kompilátor MSVC s knihovnami, které jsou aktuálně blokovány tradičním chováním. Otestovali jsme aktualizovaný preprocesor na projektech reálného světa. Zde jsou některé z nejčastějších změn, které jsme našli:

### <a name="macro-comments"></a>Komentáře k makru

Tradiční preprocesor je založen na znakových vyrovnávacích paměti, nikoli na tokenech preprocesoru. Umožňuje neobvyklé chování, jako je například následující preprocesor komentář trik, který nefunguje pod vyhovující preprocesor:

```cpp
#if DISAPPEAR
#define DISAPPEARING_TYPE /##/
#else
#define DISAPPEARING_TYPE int
#endif

// myVal disappears when DISAPPEARING_TYPE is turned into a comment
DISAPPEARING_TYPE myVal;
```

Oprava vyhovující normám je `int myVal` deklarovat uvnitř příslušných `#ifdef/#endif` směrnic:

```cpp
#define MYVAL 1

#ifdef MYVAL
int myVal;
#endif
```

### <a name="lval"></a>L#val

Tradiční preprocesor nesprávně kombinuje předponu řetězce s výsledkem [operátoru stringizing (#):](stringizing-operator-hash.md)

```cpp
 #define DEBUG_INFO(val) L"debug prefix:" L#val
//                                       ^
//                                       this prefix

const wchar_t *info = DEBUG_INFO(hello world);
```

V tomto případě `L` je předpona zbytečná, protože sousední literály řetězce jsou po rozšíření makra stejně kombinovány. Zpětně kompatibilní oprava je změnit definici:

```cpp
#define DEBUG_INFO(val) L"debug prefix:" #val
//                                       ^
//                                       no prefix
```

Stejný problém se také nachází v pohodlí makra, které "stringize" argument na široký řetězec literál:

```cpp
 // The traditional preprocessor creates a single wide string literal token
#define STRING(str) L#str
```

Problém můžete vyřešit různými způsoby:

- Použijte zřetězení `L""` `#str` řetězce a přidejte předponu. Sousední řetězcové literály jsou kombinovány po rozšíření makra:

   ```cpp
   #define STRING1(str) L""#str
   ```

- Přidat předponu `#str` poté, co je stringized s další rozšíření makra

   ```cpp
   #define WIDE(str) L##str
   #define STRING2(str) WIDE(#str)
   ```

- Pomocí operátoru `##` zřetězení zkombinujte tokeny. Pořadí operací pro `##` `#` a je nespecifikovaný, i když `#` všechny `##` kompilátory Zdá se, že vyhodnotit operátor dříve v tomto případě.

   ```cpp
   #define STRING3(str) L## #str
   ```

### <a name="warning-on-invalid-"></a>Upozornění na neplatné\#\#

Pokud [operátor vkládání tokenu (##)](token-pasting-operator-hash-hash.md) nevede k jedinému platnému tokenu předběžného zpracování, chování není definováno. Tradiční preprocesor tiše nedokáže kombinovat tokeny. Nový preprocesor odpovídá chování většiny ostatních kompilátorů a vydává diagnostiku.

```cpp
// The ## is unnecessary and does not result in a single preprocessing token.
#define ADD_STD(x) std::##x
// Declare a std::string
ADD_STD(string) s;
```

### <a name="comma-elision-in-variadic-macros"></a>Čárka elize v variadických makru

Tradiční preprocesor MSVC vždy odstraní čárky `__VA_ARGS__` před prázdnými náhradami. Experimentální preprocesor více sleduje chování jiných populárních kompilátorů napříč platformami. Aby čárka byla odebrána, musí variadický argument chybět (nejen prázdný) `##` a musí být označen operátorem. Uvažujte následující příklad:

```cpp
void func(int, int = 2, int = 3);
// This macro replacement list has a comma followed by __VA_ARGS__
#define FUNC(a, ...) func(a, __VA_ARGS__)
int main()
{
    // In the traditional preprocessor, the
    // following macro is replaced with:
    // func(10,20,30)
    FUNC(10, 20, 30);

    // A conforming preprocessor replaces the
    // following macro with: func(1, ), which
    // results in a syntax error.
    FUNC(1, );
}
```

V následujícím příkladu ve `FUNC2(1)` volání variadického argumentu chybí ve vzpoňovaném makru. Ve volání `FUNC2(1, )` variadic argument je prázdný, ale nechybí (všimněte si čárky v seznamu argumentů).

```cpp
#define FUNC2(a, ...) func(a , ## __VA_ARGS__)
int main()
{
   // Expands to func(1)
   FUNC2(1);

   // Expands to func(1, )
   FUNC2(1, );
}
```

V nadcházejícím standardu C++ 20 byl tento `__VA_OPT__`problém vyřešen přidáním . Experimentální podpora preprocesoru `__VA_OPT__` je k dispozici od visual studia 2019 verze 16.5.

### <a name="c20-variadic-macro-extension"></a>Rozšíření variadického makra c++20

Experimentální preprocesor podporuje c++ 20 variadic makro argument elision:

```cpp
#define FUNC(a, ...) __VA_ARGS__ + a
int main()
  {
  int ret = FUNC(0);
  return ret;
  }
```

Tento kód není v souladu před standardem C++ 20. V MSVC experimentální preprocesor rozšiřuje toto chování C++ 20**`/std:c++14`** **`/std:c++17`** na nižší jazyk standardní režimy ( , ). Toto rozšíření odpovídá chování jiných velkých kompilátorů jazyka C++ pro různé platformy.

### <a name="macro-arguments-are-unpacked"></a>Argumenty maker jsou "rozbaleny"

V tradičním preprocesoru, pokud makro předá jeden ze svých argumentů do jiného závislého makra, pak argument nezíská "rozbalen" při vložení. Obvykle tato optimalizace zůstává bez povšimnutí, ale může vést k neobvyklému chování:

```cpp
// Create a string out of the first argument, and the rest of the arguments.
#define TWO_STRINGS( first, ... ) #first, #__VA_ARGS__
#define A( ... ) TWO_STRINGS(__VA_ARGS__)
const char* c[2] = { A(1, 2) };

// Conforming preprocessor results:
// const char c[2] = { "1", "2" };

// Traditional preprocessor results, all arguments are in the first string:
// const char c[2] = { "1, 2", };
```

Při `A()`rozbalení předává tradiční preprocesor všechny argumenty `__VA_ARGS__` zabalené do prvního argumentu TWO_STRINGS, což `TWO_STRINGS` ponechává variadický argument prázdné. To způsobí, `#first` že výsledek je "1, 2" spíše než jen "1". Pokud jste po spolu pozorně, pak se můžete divit, co se stalo s výsledkem `#__VA_ARGS__` v tradiční rozšíření preprocesoru: `""`pokud variadic parametr je prázdný by měl mít za následek prázdný řetězec literál . Samostatný problém stále prázdný řetězec literál token z generování.

### <a name="rescanning-replacement-list-for-macros"></a>Opětovné prohledávání náhradního seznamu maker

Po nahrazení makra jsou výsledné tokeny znovu prohledány, aby byly nahrazeny další identifikátory maker. Algoritmus používaný tradiční preprocesor pro provádění prohledávání není v souladu, jak je znázorněno v tomto příkladu na základě skutečného kódu:

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
// Conforming preprocessor:
// IMPL1 ( "Hello","World");
```

I když se tento příklad může zdát trochu vykonstruovaný, viděli jsme ho v kódu reálného světa. Chcete-li zjistit, co se děje, můžeme `DO_THING`rozebrat rozšíření počínaje:

1. `DO_THING(1, "World")`rozšiřuje na`CAT(IMPL, 1) ECHO(("Hello", "World"))`
1. `CAT(IMPL, 1)`rozšiřuje na `IMPL ## 1`, který se rozšiřuje na`IMPL1`
1. Nyní tokeny jsou v tomto stavu:`IMPL1 ECHO(("Hello", "World"))`
1. Preprocesor vyhledá identifikátor `IMPL1`makra podobný funkci . Vzhledem k tomu, `(`že není následovaný , není považován za vyvolání makra podobné funkci.
1. Preprocesor přejde na následující tokeny. Zjistí, že makro `ECHO` podobné funkci `ECHO(("Hello", "World"))`se vyvolá: , které se rozbalí na`("Hello", "World")`
1. `IMPL1`je nikdy považován za znovu pro expanzi, takže plný výsledek expanze je:`IMPL1("Hello", "World");`

Chcete-li upravit makro tak, aby se chovalo stejným způsobem v rámci experimentálního preprocesoru i tradičního preprocesoru, přidejte další vrstvu dereference:

```cpp
#define CAT(a,b) a##b
#define ECHO(...) __VA_ARGS__
// IMPL1 and IMPL2 are macros implementation details
#define IMPL1(prefix,value) do_thing_one( prefix, value)
#define IMPL2(prefix,value) do_thing_two( prefix, value)
#define CALL(macroName, args) macroName args
#define DO_THING_FIXED(a,b) CALL( CAT(IMPL, a), ECHO(( "Hello",b)))
DO_THING_FIXED(1, "World");

// macro expands to:
// do_thing_one( "Hello", "World");
```

## <a name="incomplete-features"></a>Neúplné funkce

Počínaje Visual Studio 2019 verze 16.5, experimentální preprocesor je funkce kompletní pro C ++ 20. V předchozích verzích sady Visual Studio je experimentální preprocesor většinou dokončen, i když některé logiky direktivy preprocesoru stále přecvádí zpět na tradiční chování. Tady je částečný seznam neúplných funkcí ve verzích sady Visual Studio před verzí 16.5:

- Podpora pro`_Pragma`
- Funkce jazyka C++20
- Chyba blokování podpory: Logické operátory v konstantních výrazech preprocesoru nejsou plně implementovány v novém preprocesoru před verzí 16.5. U `#if` některých směrnic může nový preprocesor spadat zpět k tradičnímu preprocesoru. Efekt je patrný pouze v případě, že se makra nekompatibilní s tradičním preprocesorem rozbalí. To se může stát při vytváření slotů pro preprocesor Boost.

::: moniker-end
