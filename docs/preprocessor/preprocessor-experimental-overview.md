---
title: MSVC experimentální preprocesor – přehled
description: MSVC preprocesor se aktualizuje pro dodržování předpisů pomocí jazyka C/C++ standardů.
ms.date: 02/09/2020
helpviewer_keywords:
- preprocessor, experimental
ms.openlocfilehash: eb861b18a8d42c73429f6d00a3f47b35c9b198ca
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2020
ms.locfileid: "79090557"
---
# <a name="msvc-experimental-preprocessor-overview"></a>MSVC experimentální preprocesor – přehled

::: moniker range="vs-2015"

Visual Studio 2015 používá tradiční preprocesor, který není v souladu se standardem C++. Experimentální preprocesor je k dispozici v rámci sady Visual Studio 2017 a sady Visual Studio 2019 pomocí přepínače kompilátoru [/Experimental: preprocesor](../build/reference/experimental-preprocessor.md) . Další informace o použití nového preprocesoru v aplikaci Visual Studio 2017 a Visual Studio 2019 je k dispozici. Pokud ho chcete zobrazit, použijte selektor verzí dokumentace a vyberte jednu z těchto verzí.

::: moniker-end

::: moniker range=">=vs-2017"

Aktualizujeme preprocesor od Microsoftu C++ pro zlepšení dodržování standardů, opravu chyb dlouhodobě zavazuje chránit a změnu některých chování, která jsou oficiálně nedefinovaná. Přidali jsme také novou diagnostiku, která upozorňuje na chyby v definicích maker.

Tyto změny jsou k dispozici pomocí přepínače kompilátoru [/Experimental: preprocesor](../build/reference/experimental-preprocessor.md) v aplikaci visual Studio 2017 nebo visual Studio 2019. Výchozí chování preprocesoru zůstává stejné jako v předchozích verzích.

Počínaje verzí Visual Studio 2019 verze 16,5, experimentální podpora předběžného zpracování pro Standard C++ 20 je funkce dokončena.

## <a name="new-predefined-macro"></a>Nové předdefinované makro

Můžete zjistit, který preprocesor se používá v době kompilace. Ověřte hodnotu předdefinovaného makra [\_MSVC\_tradiční](predefined-macros.md) a sdělte, zda se tradiční preprocesor používá. Toto makro je nastaveno na nepodmíněné verze kompilátoru, který ho podporuje, nezávisle na tom, který preprocesor je vyvolán. Jeho hodnota je 1 pro tradiční preprocesor. Je 0 pro vyhovující preprocesor.

```cpp
#if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
// Logic using the traditional preprocessor
#else
// Logic using cross-platform compatible preprocessor
#endif
```

## <a name="behavior-changes-in-the-experimental-preprocessor"></a>Změny chování v experimentálním preprocesoru

Počáteční práce na experimentálním preprocesoru se zaměřuje na to, že všechna rozšíření makra jsou v souladu se standardem. Umožňuje použít kompilátor MSVC s knihovnami, které jsou aktuálně blokovány tradičním chováním. Otestovali jsme aktualizované preprocesory na projektech reálného světa. Tady jsou některé z nejběžnějších nejnovějších změn, které jsme našli:

### <a name="macro-comments"></a>Komentáře makra

Tradiční preprocesor je založen na vyrovnávací paměti znaků spíše než tokeny preprocesoru. Umožňuje neobvyklé chování, jako je například následující štych komentáře preprocesoru, který nefunguje s vyhovujícím preprocesorem:

```cpp
#if DISAPPEAR
#define DISAPPEARING_TYPE /##/
#else
#define DISAPPEARING_TYPE int
#endif

// myVal disappears when DISAPPEARING_TYPE is turned into a comment
DISAPPEARING_TYPE myVal;
```

Oprava vyhovující standardům je deklarována `int myVal` uvnitř příslušných `#ifdef/#endif`ch direktiv:

```cpp
#define MYVAL 1

#ifdef MYVAL
int myVal;
#endif
```

### <a name="lval"></a>L # Val

Tradiční preprocesor nesprávně kombinuje předponu řetězce s výsledkem operátoru [operátoru převodu (#)](stringizing-operator-hash.md) :

```cpp
 #define DEBUG_INFO(val) L"debug prefix:" L#val
//                                       ^
//                                       this prefix

const wchar_t *info = DEBUG_INFO(hello world);
```

V tomto případě je `L` prefix zbytečný, protože sousední řetězcové literály jsou kombinovány po rozšíření makra. Zpětně kompatibilní oprava je změna definice:

```cpp
#define DEBUG_INFO(val) L"debug prefix:" #val
//                                       ^
//                                       no prefix
```

Stejný problém je také nalezen v praktických makrech, které "převádějícím" argumentem na řetězec literálu v šířce:

```cpp
 // The traditional preprocessor creates a single wide string literal token
#define STRING(str) L#str
```

Problém můžete vyřešit různými způsoby:

- Použijte zřetězení řetězců `L""` a `#str` k přidání předpony. Sousední řetězcové literály jsou kombinovány po rozšíření makra:

   ```cpp
   #define STRING1(str) L""#str
   ```

- Přidat předponu po `#str` se řetězit pomocí dalšího rozšíření makra

   ```cpp
   #define WIDE(str) L##str
   #define STRING2(str) WIDE(#str)
   ```

- K kombinování tokenů použijte operátor zřetězení `##`. Pořadí operací pro `##` a `#` není určeno, i když všechny kompilátory zdají vyhodnotit operátor `#` před `##` v tomto případě.

   ```cpp
   #define STRING3(str) L## #str
   ```

### <a name="warning-on-invalid-"></a>Upozornění na neplatné \#\#

Pokud [operátor vložení tokenu (# #)](token-pasting-operator-hash-hash.md) nevede k jednomu platnému tokenu předzpracování, chování není definováno. Tradiční preprocesor bez upozornění nemůže kombinovat tokeny. Nový preprocesor se shoduje s chováním většiny ostatních kompilátorů a generuje diagnostiku.

```cpp
// The ## is unnecessary and does not result in a single preprocessing token.
#define ADD_STD(x) std::##x
// Declare a std::string
ADD_STD(string) s;
```

### <a name="comma-elision-in-variadic-macros"></a>Čárka Elizi v makrech variadické

Tradiční preprocesor MSVC vždy odstraní čárky před prázdnými `__VA_ARGS__` nahrazení. Experimentální preprocesor se podrobněji řídí chováním ostatních oblíbených kompilátorů pro různé platformy. Aby byla čárka odebrána, argument variadické musí chybět (ne jen prázdné) a musí být označený operátorem `##`. Vezměte v úvahu v následujícím příkladu:

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

V následujícím příkladu ve volání metody `FUNC2(1)` argument variadické chybí ve vyvolání makra. V volání `FUNC2(1, )` argument variadické je prázdný, ale nebyl nalezen (Všimněte si čárky v seznamu argumentů).

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

V nadcházejícím standardu C++ 20 byl tento problém řešen přidáním `__VA_OPT__`. Experimentální podpora preprocesoru pro `__VA_OPT__` je k dispozici počínaje verzí Visual Studio 2019 verze 16,5.

### <a name="c20-variadic-macro-extension"></a>Rozšíření makra c++ 20 variadické

Experimentální preprocesor podporuje variadické Argument makra C++ 20 Elizi:

```cpp
#define FUNC(a, ...) __VA_ARGS__ + a
int main()
  {
  int ret = FUNC(0);
  return ret;
  }
```

Tento kód se neshoduje s standardem C++ 20. V MSVC experimentální preprocesor rozšiřuje toto chování jazyka C++ 20 na nižší standardní režimy ( **`/std:c++14`** , **`/std:c++17`** ). Toto rozšíření se shoduje s chováním dalších hlavních kompilátorů C++ pro různé platformy.

### <a name="macro-arguments-are-unpacked"></a>Argumenty makra jsou "unpacked".

V tradičním preprocesoru, pokud makro předává některý z jeho argumentů jinému závislému makru, pak argument nezíská "unpacked" při vložení. Obvykle se tato optimalizace neprojeví, ale může vést k neobvyklému chování:

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

Při rozbalování `A()`tradiční preprocesor přepošle všechny argumenty zabalené v `__VA_ARGS__` na první argument TWO_STRINGS, který ponechá argument variadické `TWO_STRINGS` prázdný. Výsledkem je, že výsledek `#first` být "1, 2" namísto pouze "1". Pokud máte pozor, můžete se setkat s tím, co se stalo s výsledkem `#__VA_ARGS__` v tradičním rozšíření preprocesoru: Pokud je parametr variadické prázdný, měla by být výsledkem `""`prázdného řetězcového literálu. Samostatný problém zachová prázdný řetězcový literálový token od vygenerování.

### <a name="rescanning-replacement-list-for-macros"></a>Znovu prohledat náhradní seznam pro makra

Po nahrazení makra se u výsledných tokenů znovu vyhledají další identifikátory maker, které se mají nahradit. Algoritmus používaný tradičním preprocesorem pro provedení opětovného prohledání není v souladu s tímto příkladem, jak je znázorněno v tomto příkladu na základě aktuálního kódu:

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

I když se tento příklad může zdát bit contrived, zobrazili jsme ho v reálném světě kódu. Pokud chcete zjistit, co se právě používá, můžeme rozšíření od `DO_THING`rozdělit:

1. `DO_THING(1, "World")` se rozšíří na `CAT(IMPL, 1) ECHO(("Hello", "World"))`
1. `CAT(IMPL, 1)` se rozšíří na `IMPL ## 1`, které se rozšíří na `IMPL1`
1. Nyní jsou tokeny v tomto stavu: `IMPL1 ECHO(("Hello", "World"))`
1. Preprocesor vyhledá identifikátor makra podobného funkci `IMPL1`. Vzhledem k tomu, že není následován `(`, není považován za vyvolání makra jako funkce.
1. Preprocesor se přesune na následující tokeny. Najde makro podobné funkci `ECHO` vyvolá vyvolání: `ECHO(("Hello", "World"))`, které se rozšíří na `("Hello", "World")`
1. `IMPL1` se pro rozšíření nikdy nepovažuje za znovu, takže úplný výsledek rozšíření je: `IMPL1("Hello", "World");`

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

Počínaje verzí Visual Studio 2019 verze 16,5 je experimentální preprocesor funkce dokončen pro C++ 20. V předchozích verzích sady Visual Studio je experimentální preprocesor většinou kompletní, i když se některá z nich logika direktiv preprocesoru stále nevrátí k tradičnímu chování. Zde je částečný seznam neúplných funkcí v verzích sady Visual Studio před 16,5:

- Podpora pro `_Pragma`
- Funkce c++ 20
- Zesílení blokující chybu: logické operátory v konstantních výrazech preprocesoru nejsou plně implementovány v novém preprocesoru před verzí 16,5. U některých direktiv `#if` se může nový preprocesor vrátit k tradičnímu preprocesoru. Tento efekt je patrné pouze v případě, že jsou makra nekompatibilní s tradičním preprocesorem rozbalena. K tomu může dojít při sestavování, když se budou zvyšovat sloty preprocesoru.

::: moniker-end
