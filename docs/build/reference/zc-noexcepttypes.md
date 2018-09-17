---
title: '-Zc: noexceptTypes (pravidla C ++ 17 noexcept) | Dokumentace Microsoftu'
ms.date: 11/14/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc:noexceptTypes
dev_langs:
- C++
helpviewer_keywords:
- /Zc:noexceptTypes
- Zc:noexceptTypes
- -Zc:noexceptTypes
ms.assetid: 1cbf7e3c-0f82-4f91-84dd-612bcf26d2c6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 78657b293562e82e4691ae54f8ee60d490d78ba7
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716673"
---
# <a name="zcnoexcepttypes-c17-noexcept-rules"></a>/ Zc: noexcepttypes (pravidla c ++ 17 noexcept)

C ++ 17 standardního provede `throw()` jako alias pro `noexcept`, odebere `throw(<type list>)` a `throw(...)`a umožňuje určité typy zahrnout `noexcept`. To může způsobit řadu zdroj problémů s kompatibilitou v kódu, který odpovídá do C ++ 14 nebo dřívější. **/Zc: noexcepttypes** možnost můžete zadat shodu standardu C ++ 17, případně povolit C ++ 14 a dřívějších chování při kompilaci kódu v C ++ 17 režimu.

## <a name="syntax"></a>Syntaxe

> **/Zc:noexceptTypes**[-]

## <a name="remarks"></a>Poznámky

Když **/Zc: noexcepttypes** je zadána možnost, kompilátor odpovídá standardu C ++ 17 a zpracovává [throw()](../../cpp/exception-specifications-throw-cpp.md) jako alias pro [noexcept](../../cpp/noexcept-cpp.md), odebere `throw(<type list>)`a `throw(...)`a umožňuje určité typy zahrnout `noexcept`. **/Zc: noexcepttypes** možnost je dostupná jenom při [/std: c ++ 17](std-specify-language-standard-version.md) nebo [/std:latest](std-specify-language-standard-version.md) je povolená. **/ Zc: noexcepttypes** je ve výchozím nastavení povolené, tak, aby odpovídal ISO standardu C ++ 17. [/ Permissive-](permissive-standards-conformance.md) nemá vliv na možnost **/Zc: noexcepttypes**. Tuto možnost vypnout tak, že zadáte **/Zc:noexceptTypes-** se vrátit k C ++ 14 chování `noexcept` při **/std::C ++ 17** nebo **/std::latest** určena.

Od v sadě Visual Studio 2017 verze 15.5, kompilátor C++ diagnostikuje další specifikace neodpovídající výjimek v deklaracích v C ++ 17 režimu nebo když [/ permissive-](permissive-standards-conformance.md) je zadána možnost.

Tato ukázka předvádí, jak deklarace se specifikátorem k výjimce chovat, když **/Zc: noexcepttypes** možností je nastavit nebo zakázáno. Chcete-li zobrazit chování při nastavení, kompilovat s použitím `cl /EHsc /W4 noexceptTypes.cpp`. Chcete-li zobrazit chování, pokud je zakázán, kompilovat s použitím `cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp`.

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

Při kompilaci pomocí výchozí nastavení **/Zc: noexcepttypes**, ukázka generuje upozornění uvedené. Pokud chcete aktualizovat váš kód, použijte následující:

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

Další informace o problémech přizpůsobení v aplikaci Visual C++, naleznete v tématu [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Upravit **další možnosti** vlastnost, aby zahrnovala **/Zc: noexcepttypes** nebo **/Zc:noexceptTypes-** a klikněte na tlačítko **OK**.

## <a name="see-also"></a>Viz také:

[/Zc (shoda)](../../build/reference/zc-conformance.md)
[noexcept](../../cpp/noexcept-cpp.md)<br/>
[Specifikace výjimek (throw)](../../cpp/exception-specifications-throw-cpp.md)
