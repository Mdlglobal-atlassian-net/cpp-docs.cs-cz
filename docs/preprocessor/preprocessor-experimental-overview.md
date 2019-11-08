---
title: MSVC experimentální preprocesor – přehled
description: MSVC preprocesor se aktualizuje pro dodržování předpisů pomocí jazyka C/C++ standardů.
ms.date: 11/06/2019
helpviewer_keywords:
- preprocessor, experimental
ms.openlocfilehash: 446603b34d9309c256afba9abd7234ae2ab16f5c
ms.sourcegitcommit: 2362d15b5eb18d27773c3f7522da3d0eed9e2571
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73797174"
---
# <a name="msvc-experimental-preprocessor-overview"></a>MSVC experimentální preprocesor – přehled

V současné C++ době probíhá aktualizace preprocesoru Microsoftu pro zlepšení dodržování standardů, opravy chyb dlouhodobě zavazuje chránit a změnu některých chování, která jsou oficiálně nedefinovaná. Kromě toho byly přidány nové diagnostiky, které upozorňují na chyby v definicích maker.

Tyto změny v jejich aktuálním stavu jsou k dispozici pomocí přepínače kompilátoru [/Experimental: preprocesor](../build/reference/experimental-preprocessor.md) v aplikaci visual Studio 2017 nebo visual Studio 2019. Výchozí chování preprocesoru zůstává stejné jako v předchozích verzích.

## <a name="new-predefined-macro"></a>Nové předdefinované makro

Můžete zjistit, který preprocesor se používá v době kompilace. Ověřte hodnotu předdefinovaného makra [\_MSVC\_tradiční](predefined-macros.md) a sdělte, zda se tradiční preprocesor používá. Toto makro je nastaveno na nepodmíněné verze kompilátoru, který ho podporuje, nezávisle na tom, který preprocesor je vyvolán. Jeho hodnota je 1 pro tradiční preprocesor. Je 0 pro vyhovující experimentální preprocesor:

```cpp
#if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
// Logic using the traditional preprocessor
#else
// Logic using cross-platform compatible preprocessor
#endif
```

```cpp
#if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
// Logic using the traditional preprocessor
#else
// Logic using cross-platform compatible preprocessor
#endif
```

## <a name="behavior-changes-in-the-experimental-preprocessor"></a>Změny chování v experimentálním preprocesoru

Počáteční práce na experimentálním preprocesoru se zaměřuje na zajištění shody všech rozšíření maker, aby bylo možné povolit použití kompilátoru MSVC s knihovnami, které jsou aktuálně blokované v důsledku tradičního chování. Níže je uveden seznam některých nejběžnějších nedokončených změn, které byly spuštěny při testování aktualizovaného preprocesoru s projekty reálného světa.

### <a name="macro-comments"></a>Komentáře makra

Tradiční preprocesor je založen na vyrovnávací paměti znaků spíše než tokeny preprocesoru. To umožňuje neobvyklým chováním, jako je například následující štych komentáře preprocesoru, který nebude fungovat s vyhovujícími preprocesory:

```cpp
#if DISAPPEAR
#define DISAPPEARING_TYPE /##/
#else
#define DISAPPEARING_TYPE int
#endif

// myVal disappears when DISAPPEARING_TYPE is turned into a comment
DISAPPEARING_TYPE myVal;
```

Vyhovující standardům je deklarovat `int myVal` v příslušných `#ifdef/#endif` direktivách:

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

V tomto případě je `L` prefix zbytečný, protože sousední řetězcové literály jsou kombinovány po rozšíření makra. Zpětně kompatibilní oprava je změna definice na následující:

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

- Použijte zřetězení řetězců `L""` a `#str` k přidání předpony. To funguje, protože sousední řetězcové literály jsou kombinovány po rozšíření makra:

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

Pokud [operátor vložení tokenu (# #)](token-pasting-operator-hash-hash.md) nevede k jednomu platnému tokenu předzpracování, chování není definováno. Tradiční preprocesor by v tichém případě nemohlo kombinovat tokeny. Nový preprocesor bude odpovídat chování většiny ostatních kompilátorů a vygeneruje diagnostiku.

```cpp
// The ## is unnecessary and does not result in a single preprocessing token.
#define ADD_STD(x) std::##x
// Declare a std::string
ADD_STD(string) s;
```

### <a name="comma-elision-in-variadic-macros"></a>Čárka Elizi v makrech variadické

Tradiční preprocesor MSVC vždy odstraní čárky před prázdnými `__VA_ARGS__` nahrazení. Experimentální preprocesor se podrobněji řídí chováním ostatních oblíbených kompilátorů pro různé platformy. Aby byla čárka odebrána, argument variadické musí chybět (ne jen prázdné) a musí být označený operátorem `##`. Vezměte v úvahu následující příklad:

```cpp
void func(int, int = 2, int = 3);
// This macro replacement list has a comma followed by __VA_ARGS__
#define FUNC(a, ...) func(a, __VA_ARGS__)
int main()
{
    // In the traditional preprocessor, the following macro is replaced with:
    // func(10,20,30)
    FUNC(10, 20, 30);

    // A conforming preprocessor will replace the following macro with: func(1, ), which will result in a syntax error.
    FUNC(1, );
}
```

V následujícím příkladu ve volání metody `FUNC2(1)` argument variadické chybí v evoked makro. V volání `FUNC2(1, )` argument variadické je prázdný, ale nebyl nalezen (Všimněte si čárky v seznamu argumentů).

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

V nadcházejících standardech C + + 2a se tento problém vyřešil přidáním `__VA_OPT__`, která ještě není naimplementovaná.

### <a name="macro-arguments-are-unpacked"></a>Argumenty makra jsou "unpacked".

V tradičním preprocesoru, pokud makro přepošle jeden z argumentů na jiné závislé makro, pak argument nezíská "unpacked" při nahrazení. Obvykle se tato optimalizace neprojeví, ale může vést k neobvyklému chování:

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

Při rozbalování `A()`tradiční preprocesor přepošle všechny argumenty zabalené v `__VA_ARGS__` na první argument TWO_STRINGS, což ponechá argument variadické `TWO_STRINGS` prázdné. Výsledkem je, že výsledek `#first` být "1, 2" namísto pouze "1". Pokud máte pozor, můžete se setkat s tím, co se stalo s výsledkem `#__VA_ARGS__` v tradičním rozšíření preprocesoru: Pokud je parametr variadické prázdný, měla by být výsledkem `""`prázdného řetězcového literálu. Z důvodu samostatného problému nebyl vygenerován prázdný řetězcový literálový token.

### <a name="rescanning-replacement-list-for-macros"></a>Znovu prohledat náhradní seznam pro makra

Po nahrazení makra se u výsledných tokenů znovu prohledají další identifikátory maker, které je potřeba nahradit. Algoritmus používaný tradičním preprocesorem pro provedení opětovného prohledání není vyhovující, jak je znázorněno v tomto příkladu na základě aktuálního kódu:

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

I když se tento příklad jeví jako bitová contrived, bylo zjištěno, že došlo k reálnému světovému kódu. Pokud chcete zjistit, co se vám bude líbit, můžete rozšíření od `DO_THING`rozdělit:

1. `DO_THING(1, "World")` se rozšíří na `CAT(IMPL, 1) ECHO(("Hello", "World"))`
1. `CAT(IMPL, 1)` se rozšíří na `IMPL ## 1`, které se rozšíří na `IMPL1`
1. Nyní jsou tokeny v tomto stavu: `IMPL1 ECHO(("Hello", "World"))`
1. Preprocesor vyhledá identifikátor makra podobného funkci `IMPL1`, ale není následován `(`, takže není považován za vyvolání makra jako funkce. 
1. Přesune se na následující tokeny a najde makro podobné funkci `ECHO`: `ECHO(("Hello", "World"))`, které se rozšíří na `("Hello", "World")`
1. `IMPL1` se pro rozšíření nikdy nepovažuje za znovu, takže úplný výsledek rozšíření je: `IMPL1("Hello", "World");`

Makro lze upravit tak, aby se chovalo stejně jako experimentální preprocesor a tradiční preprocesor přidáním do jiné vrstvy dereference:

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

Experimentální preprocesor je většinou kompletní, i když se některé z logiky direktiv preprocesoru stále nevrátí k tradičnímu chování. Tady je částečný seznam neúplných funkcí:

- Podpora `_Pragma`
- Funkce c++ 20
- Zvýšení úrovně chyby při zablokování: logické operátory v konstantních výrazech preprocesoru nejsou plně implementované v novém preprocesoru. U některých direktiv `#if` se může nový preprocesor vrátit k tradičnímu preprocesoru. Tento efekt je patrné pouze v případě, že makra, která jsou nekompatibilní s tradičním preprocesorem, jsou rozbalena, což může nastat při sestavování zvýšení slotu preprocesoru.
