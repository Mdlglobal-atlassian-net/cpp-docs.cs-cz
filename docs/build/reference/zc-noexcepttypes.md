---
title: '-Zc: noexceptTypes (C ++ 17 noexcept pravidla) | Microsoft Docs'
ms.date: 11/14/2017
ms.technology: cpp-tools
ms.topic: article
f1_keywords: /Zc:noexceptTypes
dev_langs: C++
helpviewer_keywords:
- /Zc:noexceptTypes
- Zc:noexceptTypes
- -Zc:noexceptTypes
ms.assetid: 1cbf7e3c-0f82-4f91-84dd-612bcf26d2c6
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: aa1cf155cd77c69decdff437d67d132a66819c72
ms.sourcegitcommit: 1b480aa74886930b3bd0435d71cfcc3ccda36424
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="zcnoexcepttypes-c17-noexcept-rules"></a>/Zc:noexceptTypes (c ++ 17 noexcept pravidla)

Díky C ++ 17 standardní `throw()` jako alias pro `noexcept`, odebere `throw(<type list>)` a `throw(...)`a umožňuje určité typy zahrnout `noexcept`. To může způsobit určité problémy s kompatibilitou zdroje v kódu, který vyhovuje C ++ 14 nebo dřívější. **/Zc:noexceptTypes** možnost můžete určit shoda pro C ++ 17 standardní nebo povolit C ++ 14 a starší chování, když kompilace kódu v C ++ 17 režimu.

## <a name="syntax"></a>Syntaxe

> **/Zc:noexceptTypes**[-]

## <a name="remarks"></a>Poznámky

Když **/Zc:noexceptTypes** je zadána možnost, kompilátor C ++ 17 standardní vyhovuje a považuje [throw()](../../cpp/exception-specifications-throw-cpp.md) jako alias pro [noexcept](../../cpp/noexcept-cpp.md), odebere `throw(<type list>)`a `throw(...)`a umožňuje určité typy zahrnout `noexcept`. **/Zc:noexceptTypes** možnost je dostupná jenom při [/std: c ++ 17](std-specify-language-standard-version.md) nebo [/std:latest](std-specify-language-standard-version.md) je povoleno. **/Zc:noexceptTypes** je ve výchozím nastavení povolené tak, aby odpovídala ISO standardu C ++ 17. Tuto možnost vypnout tak, že zadáte **/Zc:noexceptTypes-** se vrátit k C ++ 14 chování `noexcept` při **/std::C ++ 17** nebo **/std::latest** je zadán.

Od verze Visual Studio 2017 verze 15,5, C++ compiler diagnostikuje další specifikace neodpovídající výjimek v deklaracích v C ++ 17 režimu nebo když [/ projektovou-](permissive-standards-conformance.md) je zadána možnost.

Tento příklad ukazuje, jak deklarace s k výjimce specifikátor chovat, kdy **/Zc:noexceptTypes** je možnost nastavit nebo zakázána. Chcete-li zobrazit chování Pokud nastavíte, zkompilovat pomocí `cl /EHsc /W4 noexceptTypes.cpp`. Zobrazit chování, pokud je zakázán, zkompilovat pomocí `cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp`.

```cpp
// noexceptTypes.cpp
// Compile by using: cl /EHsc /W4 noexceptTypes.cpp
// Compile by using: cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp

void f() throw();    // equivalent to void f() noexcept;
void f() { }         // warning C5043
void g() throw(...); // warning C5040

struct A
{
    virtual void f() throw();
};

struct B : A
{
    virtual void f() { } // error C2694
};
```

Při kompilaci pomocí výchozí nastavení **/Zc:noexceptTypes**, ukázky generuje uvedené upozornění. Aktualizace kódu, použijte následující:

```cpp
void f() noexcept;
void f() noexcept { }
void g() noexcept(false);

struct A
{
    virtual void f() noexcept;
};

struct B : A
{
    virtual void f() noexcept { }
};
```

Další informace o problémech shoda v jazyce Visual C++, najdete v části [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **příkazového řádku** stránka vlastností v **C/C++** složky.

1. Změnit **další možnosti** vlastnost, aby zahrnovala **/Zc:noexceptTypes** nebo **/Zc:noexceptTypes-** a potom zvolte **OK**.

## <a name="see-also"></a>Viz také

[/Zc (shoda)](../../build/reference/zc-conformance.md)  
[noexcept](../../cpp/noexcept-cpp.md)  
[Specifikace výjimek (throw)](../../cpp/exception-specifications-throw-cpp.md)  
