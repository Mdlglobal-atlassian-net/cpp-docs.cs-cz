---
title: extern (C++)
ms.date: 04/12/2018
f1_keywords:
- extern
- extern_CPP
helpviewer_keywords:
- extern keyword [C++], linkage to non-C++ functions
- declarations, external
- external linkage, extern modifier
ms.assetid: 1e2f0ae3-ae98-4410-85b5-222d6abc865a
ms.openlocfilehash: d42a32202f7fa67751ea36757c13b2c6af4953b2
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301532"
---
# <a name="extern-c"></a>extern (C++)

Klíčové slovo **extern** se používá pro deklaraci globální proměnné, funkce nebo šablony k určení toho, že název tohoto objektu má *vnější propojení*. Informace o propojení a o tom, proč použití globálních proměnných není doporučeno, naleznete v části [jednotky překladu a propojení](program-and-linkage-cpp.md).

Klíčové slovo **extern** má v závislosti na kontextu čtyři významy:

1. v deklaraci globální proměnné, která není const, **externí** určuje, že proměnná nebo funkce je definována v jiné jednotce překladu. **Extern** musí být použit ve všech souborech s výjimkou toho, kde je proměnná definována.
1. v deklaraci proměnné const určuje, že proměnná má vnější propojení. **Extern** musí být použit pro všechny deklarace ve všech souborech. (Globální proměnné const mají ve výchozím nastavení vnitřní propojení.)
1. **extern "C"** určuje, že funkce je definována jinde a používá konvenci volání jazyka C. Modifikátor extern "C" může být použit také pro více deklarací funkcí v bloku.
1. v deklaraci šablony určuje, že šablona již byla vytvořena jinde. Toto je optimalizace, která instruuje kompilátor, že může znovu použít jiné vytváření instancí místo vytvoření nové v aktuálním umístění. Další informace o tomto použití typu **extern**naleznete v tématu [Templates](templates-cpp.md).

## <a name="extern-linkage-for-non-const-globals"></a>externí propojení pro globální a nekonstantní

Když linker vidí **extern** před deklarací globální proměnné, vyhledá definici v jiné jednotce překladu. Deklarace nekonstantních proměnných v globálním oboru jsou ve výchozím nastavení externí; použijte pouze **extern** na deklarace, které neposkytují definici.

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

## <a name="extern-linkage-for-const-globals"></a>externí propojení pro konstantní Globals

**Konstantní** globální proměnná má ve výchozím nastavení vnitřní propojení. Pokud chcete, aby měla proměnná vnější propojení, použijte klíčové slovo **extern** na definici a také na všechny ostatní deklarace v jiných souborech:

```cpp
//fileA.cpp
extern const int i = 42; // extern const definition

//fileB.cpp
extern const int i;  // declaration only. same as i in FileA
```

## <a name="extern-constexpr-linkage"></a>externí propojení constexpr

V aplikaci Visual Studio 2017 verze 15,3 a dřívější kompilátor vždy přiřadil vnitřní propojení proměnné constexpr i v případě, že proměnná byla označena jako extern. V aplikaci Visual Studio 2017 verze 15,5 nový přepínač kompilátoru ([/Zc: externConstexpr](../build/reference/zc-externconstexpr.md)) umožňuje správné chování vyhovující standardům. Nakonec se stane výchozí. Možnost/Permissive-nepovoluje/Zc: externConstexpr.

```cpp
extern constexpr int x = 10; //error LNK2005: "int const x" already defined
```

Pokud hlavičkový soubor obsahuje proměnnou deklarovanou extern constexpr, musí být označena jako **__declspec (selectany)** , aby správně obsahovala své duplicitní deklarace:

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

## <a name="extern-c-and-extern-c-function-declarations"></a>extern "C" a extern "C++" deklarace funkcí

V C++, při použití s řetězcem **extern** určuje, že jsou použity konvence propojení jiného jazyka pro deklarátor. Funkce a data jazyka C mohou být zpřístupněny pouze v případě, že byly dříve deklarovány s propojením jazyka C. Musí však být definovány v odděleně kompilované jednotce překladu.

Microsoft C++ podporuje řetězce **"C"** a **C++""** v poli *řetězcové literály* . Všechny standardní zahrnuté soubory používají syntaxi **extern** "C", aby bylo možné používat funkce běhové knihovny v C++ programech.

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

Pokud funkce obsahuje více specifikací propojení, musejí tato propojení souhlasit. U deklarace funkcí, které mají propojení jazyka C i C++, se jedná o chybu. Pokud se navíc v jednom programu vyskytují dvě deklarace funkce – jedna se specifikací propojení a jedna bez ní – musí být deklarace se specifikací propojení jako první. Jakékoli nadbytečné deklarace funkcí, které již specifikaci propojení obsahují, obdrží propojení zadané v první deklaraci. Příklad:

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

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Jednotky překladu a propojení](program-and-linkage-cpp.md)<br/>
[extern – specifikátor třídy úložiště v jazyce C](../c-language/extern-storage-class-specifier.md)<br/>
[Chování identifikátorů v jazyce C](../c-language/behavior-of-identifiers.md)<br/>
[Propojení v jazyce C](../c-language/linkage.md)