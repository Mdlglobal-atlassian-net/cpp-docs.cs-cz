---
title: extern (C++)
description: Průvodce C++ jazykovým externovým klíčovým slovem
ms.date: 01/28/2020
f1_keywords:
- extern
- extern_CPP
helpviewer_keywords:
- extern keyword [C++], linkage to non-C++ functions
- declarations, external
- external linkage, extern modifier
ms.assetid: 1e2f0ae3-ae98-4410-85b5-222d6abc865a
no-loc:
- extern
- const
- constexpr
- permissive
ms.openlocfilehash: 422b6960802c59f1c45e0c22a4a85988c808a5b3
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821763"
---
# <a name="opno-locextern-c"></a>extern (C++)

Klíčové slovo **extern** lze použít pro globální proměnnou, funkci nebo deklaraci šablony. Určuje, že má symbol *vnější propojení*. Informace o propojení a o tom, proč použití globálních proměnných není doporučeno, naleznete v části [jednotky překladu a propojení](program-and-linkage-cpp.md).

Klíčové slovo **extern** má v závislosti na kontextu čtyři významy:

- V deklaraci globální proměnné bez **const** **extern** určuje, že proměnná nebo funkce je definována v jiné jednotce překladu. **extern** musí být použito ve všech souborech s výjimkou toho, kde je proměnná definována.

- V deklaraci proměnné **const** určuje, zda má proměnná vnější propojení. **extern** musí být použita na všechny deklarace ve všech souborech. (Globální proměnné **const** mají ve výchozím nastavení interní propojení.)

- **extern "C"** určuje, že funkce je definována jinde a používá konvenci volání jazyka C. Modifikátor extern "C" může být použit také pro více deklarací funkcí v bloku.

- V deklaraci šablony **extern** určuje, že šablona již byla vytvořena jinde. **extern** instruuje kompilátor, může znovu použít jiné vytváření instancí namísto vytvoření nové v aktuálním umístění. Další informace o tomto použití **extern** naleznete v tématu [explicitní vytváření instancí](explicit-instantiation.md).

## <a name="opno-locextern-linkage-for-non-opno-locconst-globals"></a>extern propojení pro neconstou globální obsah

Když linker uvidí **extern** před deklarací globální proměnné, vyhledá definici v jiné jednotce překladu. Deklarace proměnných, které nejsou **const** v globálním oboru, jsou ve výchozím nastavení externí. U deklarací, které neposkytují definici, použijte pouze **extern** .

```cpp
//fileA.cpp
int i = 42; // declaration and definition

//fileB.cpp
extern int i;  // declaration only. same as i in FileA

//fileC.cpp
extern int i;  // declaration only. same as i in FileA

//fileD.cpp
int i = 43; // LNK2005! 'i' already has a definition.
extern int i = 43; // same error (extern is ignored on definitions)
```

## <a name="opno-locextern-linkage-for-opno-locconst-globals"></a>extern propojení pro const Globals

Globální proměnná **const** má ve výchozím nastavení vnitřní propojení. Chcete-li, aby měla proměnná vnější propojení, použijte klíčové slovo **extern** pro definici a pro všechny ostatní deklarace v jiných souborech:

```cpp
//fileA.cpp
extern const int i = 42; // extern const definition

//fileB.cpp
extern const int i;  // declaration only. same as i in FileA
```

## <a name="opno-locextern-opno-locconstexpr-linkage"></a>propojení extern constexpr

V aplikaci Visual Studio 2017 verze 15,3 a starší má kompilátor vždy **constexpr** interní propojení proměnné, a to i v případě, že proměnná byla označena **extern** . V aplikaci Visual Studio 2017 verze 15,5 a novější umožňuje přepínač [/Zc: externConstexpr](../build/reference/zc-externconstexpr.md) správné chování vyhovující standardům. Nakonec se stane výchozí možností. Možnost [/permissive-](../build/reference/permissive-standards-conformance.md) nepovoluje **/Zc: externConstexpr**.

```cpp
extern constexpr int x = 10; //error LNK2005: "int const x" already defined
```

Pokud hlavičkový soubor obsahuje proměnnou deklarovanou **extern** **constexpr** , musí být označena `__declspec(selectany)`, aby správně měla své duplicitní deklarace v kombinaci:

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

## <a name="opno-locextern-c-and-opno-locextern-c-function-declarations"></a>extern "C" a extern "C++" deklarace funkcí

V C++, pokud se používá s řetězcem, **extern** určuje, zda jsou používány konvence propojení jiného jazyka pro deklarátor (y). K funkcím a datům jazyka c lze přistupovat pouze v případě, že jsou již dříve deklarovány jako propojení jazyka C. Musí však být definovány v odděleně kompilované jednotce překladu.

Microsoft C++ podporuje řetězce **"C"** a **C++""** v poli *řetězcové literály* . Všechny standardní vložené soubory používají syntaxi **extern "C"** , aby bylo možné používat funkce knihovny run-time v C++ programech.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak deklarovat názvy, které mají propojení jazyka C:

```cpp
// Declare printf with C linkage.
extern "C" int printf(const char *fmt, ...);

//  Cause everything in the specified
//  header files to have C linkage.
extern "C" {
    // add your #include statements here
#include <stdio.h>
}

//  Declare the two functions ShowChar
//  and GetChar with C linkage.
extern "C" {
    char ShowChar(char ch);
    char GetChar(void);
}

//  Define the two functions
//  ShowChar and GetChar with C linkage.
extern "C" char ShowChar(char ch) {
    putchar(ch);
    return ch;
}

extern "C" char GetChar(void) {
    char ch;
    ch = getchar();
    return ch;
}

// Declare a global variable, errno, with C linkage.
extern "C" int errno;
```

Pokud má funkce více než jednu specifikaci propojení, musí souhlasit. Jedná se o chybu pro deklarování funkcí, které mají obojí C++ C i propojení. Pokud se navíc v jednom programu vyskytují dvě deklarace funkce – jedna se specifikací propojení a jedna bez ní – musí být deklarace se specifikací propojení jako první. Jakékoli nadbytečné deklarace funkcí, které již specifikaci propojení obsahují, obdrží propojení zadané v první deklaraci. Příklad:

```cpp
extern "C" int CFunc1();
...
int CFunc1();            // Redeclaration is benign; C linkage is
                         //  retained.

int CFunc2();
...
extern "C" int CFunc2(); // Error: not the first declaration of
                         //  CFunc2;  cannot contain linkage
                         //  specifier.
```

## <a name="see-also"></a>Viz také:

\ [klíčových slov](../cpp/keywords-cpp.md)
[Jednotky překladu a propojení](program-and-linkage-cpp.md)\
[extern specifikátoru třídy úložiště v jazyce C](../c-language/extern-storage-class-specifier.md)\
[Chování identifikátorů v jazyce C](../c-language/behavior-of-identifiers.md)\
[Propojení v jazyce C](../c-language/linkage.md)
