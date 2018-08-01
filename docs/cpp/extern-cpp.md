---
title: extern (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 04/12/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- extern
- extern_CPP
dev_langs:
- C++
helpviewer_keywords:
- extern keyword [C++], linkage to non-C++ functions
- declarations, external
- external linkage, extern modifier
ms.assetid: 1e2f0ae3-ae98-4410-85b5-222d6abc865a
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 133cbb01ba54ccc8bc0ce0c31b5d7b4436c2488d
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39403040"
---
# <a name="extern-c"></a>extern (C++)

**Extern** – klíčové slovo platí pro globální proměnné, funkce nebo šablona prohlášení k určení, zda má název celou věc nepropojili *vnější propojení*. Základní informace o propojení a proč se nedoporučuje použití globálních proměnných, naleznete v tématu [Program a propojení](program-and-linkage-cpp.md).

**Extern** – klíčové slovo má čtyři význam v závislosti na kontextu:

1. v nekonstantní globální deklaraci proměnné **extern** Určuje, že proměnná nebo funkce je definována v jiné jednotce překladu. **Extern** musí použít ve všech souborech s výjimkou toho, kde je proměnná definovaná.
1. v deklaraci proměnné const Určuje, že má proměnná vnější propojení. **Extern** musí vztahovat na všechny deklarace ve všech souborech. (Globální proměnné const mají ve výchozím nastavení vnitřní propojení.)
1. **extern "C"** Určuje, že funkce je definována jinde a používá konvence volání jazyka C. Modifikátor extern "C" mohou také použít pro více deklaracích funkcí v bloku.
1. v deklaraci šablony určuje, že šablona má už vytvářejí instance jinde. Toto je optimalizace, která sděluje kompilátoru, že může znovu použít jiné instanci spíše než vytvářet novou do aktuálního umístění. Další informace o tomto použití **extern**, naleznete v tématu [šablony](templates-cpp.md).

## <a name="extern-linkage-for-non-const-globals"></a>externí propojení pro nekonstantní globální prvky

Když linker uvidí **extern** před deklaraci globální proměnné, hledá definice v jiné jednotce překladu. Deklarace proměnných nekonstantní v globálním oboru jsou externí ve výchozím nastavení; platí jen **extern** do deklarací, které neposkytují definici.

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

## <a name="extern-linkage-for-const-globals"></a>externí propojení pro const globální prvky

A **const** globální proměnná má vnitřní propojení ve výchozím nastavení. Pokud chcete vnější propojení u proměnné, použijte **extern** – klíčové slovo do definice, jakož i všechny deklarace v jiných souborech:

```cpp
//fileA.cpp
extern const int i = 42; // extern const definition

//fileB.cpp
extern const int i;  // declaration only. same as i in FileA
```

## <a name="extern-constexpr-linkage"></a>Extern constexpr propojení

V sadě Visual Studio 2017 verze 15.3 nebo starší kompilátor vždy přiřadil constexpr vnitřní propojení proměnné i v případě, že proměnná byla označena jako extern. V sadě Visual Studio 2017 verze 15.5, nový přepínač kompilátoru ([/Zc: externconstexpr](../build/reference/zc-externconstexpr.md)) umožňuje správné chování vyhovující standardům. Nakonec to bude výchozí.

```cpp
extern constexpr int x = 10; //error LNK2005: "int const x" already defined
```

Pokud soubor hlavičky obsahuje proměnné deklarované extern constexpr, musí být označen **__declspec(selectany)** aby bylo možné správně mít jeho duplicitní deklarace kombinaci:

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

## <a name="extern-c-and-extern-c-function-declarations"></a>deklarace funkcí extern "C" a extern "C++"

 V jazyce C++ při použití s řetězcem **extern** Určuje, že propojovací konvence jiného jazyka se používají pro deklarátory. Funkce a data jazyka C mohou být zpřístupněny pouze v případě, že byly dříve deklarovány s propojením jazyka C. Musí však být definovány v odděleně kompilované jednotce překladu.

 Microsoft C++ podporuje řetězce **"C"** a **"C++"** v *řetězcový literál* pole. Všechny standardní vložené soubory používají **extern** syntaxe "C" Povolit funkce knihovny run-time, který se má použít v programech jazyka C++.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak deklarovat názvy, které mají propojení jazyka:

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
 [Klíčová slova](../cpp/keywords-cpp.md)  
 [Program a propojení](program-and-linkage-cpp.md)  
 [extern – specifikátor třídy úložiště v jazyce C](../c-language/extern-storage-class-specifier.md)  
 [Chování identifikátorů v jazyce C](../c-language/behavior-of-identifiers.md)  
 [Propojení v jazyce C](../c-language/linkage.md)