---
title: extern (C++) | Microsoft Docs
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
ms.openlocfilehash: 00b9f94d02443163f45b83d64702fe49622597cd
ms.sourcegitcommit: d06966efce25c0e66286c8047726ffe743ea6be0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238756"
---
# <a name="extern-c"></a>extern (C++)

**Extern** – klíčové slovo, které se použijí na globální proměnnou, funkce nebo šablony deklarace k určení, že má název této věc *externí propojení*. Základní informace o propojení a proč se nedoporučuje použití globální proměnné naleznete v tématu [Program a propojení](program-and-linkage-cpp.md).

**Extern** – klíčové slovo má čtyři významy v závislosti na kontextu:

1. v jiných const globální proměnné deklaraci **extern** Určuje, že se proměnné nebo funkce je definována v jiné jednotce překlad. **Extern** se musí použít v všechny soubory s výjimkou toho, kde je proměnná definovaná.
1. v deklaraci const proměnné určuje, že má proměnná externí propojení. **Extern** je nutné použít na všechny deklarace ve všech souborů. (Globální proměnné const mají vnitřní propojení ve výchozím nastavení.)
1. **extern "C"** Určuje, že funkce je definována jinde a používá konvence volání jazyka C. Extern – modifikátor "C" může použít také k více deklarací funkce v bloku.
1. v deklaraci šablony určuje, že šablona již instance jinde. Toto je optimalizace, která říká kompilátoru, ho můžete znovu použít jiné instance spíše než v aktuální umístění vytvořením nového. Další informace o použití této **extern**, najdete v části [šablony](templates-cpp.md).

## <a name="extern-linkage-for-non-const-globals"></a>externí propojení pro jiný const globální funkce

Když linkeru uvidí **extern** před globální deklarace proměnné, hledá definici v jiné jednotce překlad. Deklarace proměnných bez const v globálním oboru jsou externí ve výchozím nastavení; platí pouze **extern** deklaracích, které neposkytují definici.

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

## <a name="extern-linkage-for-const-globals"></a>externí propojení pro const globální funkce

A **const** globální proměnná vnitřní propojení nemá ve výchozím nastavení. Pokud chcete, aby proměnné tak, aby měl externí propojení, budou použity **extern** – klíčové slovo do definice také tak, aby všechny deklarace v jiné soubory:

```cpp
//fileA.cpp
extern const int i = 42; // extern const definition

//fileB.cpp
extern const int i;  // declaration only. same as i in FileA
```

## <a name="extern-constexpr-linkage"></a>Extern constexpr propojení

V aplikaci Visual Studio 2017 verze 15.3 a starší kompilátor vždy přiřadil constexpr proměnné vnitřní propojení i v případě, že proměnná byla označena jako externí. V aplikaci Visual Studio 2017 verze 15,5, nového přepínače kompilátoru ([/Zc:externConstexpr](../build/reference/zc-externconstexpr.md)) umožňuje správné chování podle standardů. Nakonec stane výchozí.

```cpp
extern constexpr int x = 10; //error LNK2005: "int const x" already defined
```

Pokud soubor hlaviček obsahuje proměnné deklarované extern constexpr, musí být označen **__declspec(selectany)** aby bylo možné správně používat jeho duplicitní deklarace kombinaci:

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

## <a name="extern-c-and-extern-c-function-declarations"></a>deklarace funkcí extern "C" a extern "C++"

 V jazyce C++ při použití s řetězcem **extern** Určuje propojení pravidla jiný jazyk, se používá pro declarator(s). Funkce a data jazyka C mohou být zpřístupněny pouze v případě, že byly dříve deklarovány s propojením jazyka C. Musí však být definovány v odděleně kompilované jednotce překladu.

 Microsoft C++ podporuje řetězce **"C"** a **"C++"** v *řetězcový literál* pole. Všechny standardní patří použití souborů **extern** syntaxe "C" Povolit funkce běhové knihovny pro použití v C++ – programy.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak deklarovat názvy, které mají propojení C:

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

## <a name="see-also"></a>Viz také

- [Klíčová slova](../cpp/keywords-cpp.md)
- [Program a propojení](program-and-linkage-cpp.md)
- [extern – specifikátor třídy úložiště v jazyce C](../c-language/extern-storage-class-specifier.md) 
- [Chování identifikátorů v jazyce C](../c-language/behavior-of-identifiers.md) 
- [Propojení v jazyce C](../c-language/linkage.md)