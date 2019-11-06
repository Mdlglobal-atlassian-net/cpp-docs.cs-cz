---
title: /Zc:noexceptTypes (pravidla C++17 noexcept)
ms.date: 11/14/2017
f1_keywords:
- /Zc:noexceptTypes
helpviewer_keywords:
- /Zc:noexceptTypes
- Zc:noexceptTypes
- -Zc:noexceptTypes
ms.assetid: 1cbf7e3c-0f82-4f91-84dd-612bcf26d2c6
ms.openlocfilehash: 35bea7c2c629c615c60a6136f289b6b11926c054
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624865"
---
# <a name="zcnoexcepttypes-c17-noexcept-rules"></a>/Zc:noexceptTypes (pravidla C++17 noexcept)

Standard C++ 17 vytvoří `throw()` alias pro `noexcept`, odebere `throw(<type list>)` a `throw(...)`a umožní určitým typům zahrnout `noexcept`. Tato změna může způsobit řadu potíží s kompatibilitou zdrojů v kódu, které odpovídají C++ 14 nebo starším. Možnost **/Zc: noexceptTypes** určuje shodu s normou c++ 17. **/Zc: noexceptTypes –** povolí chování c++ 14 a dřívější při kompilování kódu v režimu c++ 17.

## <a name="syntax"></a>Syntaxe

> **/Zc: noexceptTypes**[-]

## <a name="remarks"></a>Poznámky

Je-li zadána možnost **/Zc: noexceptTypes** , kompilátor odpovídá standardu c++ 17 a zpracovává [throw ()](../../cpp/exception-specifications-throw-cpp.md) jako alias pro, [s výjimkou](../../cpp/noexcept-cpp.md), odebrání `throw(<type list>)` a `throw(...)`a umožňuje určitým typům zahrnout `noexcept`. Možnost **/Zc: noexceptTypes** je k dispozici pouze v případě, že je povolená možnost [/std: c++ 17](std-specify-language-standard-version.md) nebo [/std: nejnovější](std-specify-language-standard-version.md) . Parametr **/Zc: noexceptTypes** je ve výchozím nastavení povolený tak, aby odpovídal standardu ISO c++ 17. Možnost [/Permissive-](permissive-standards-conformance.md) nemá vliv na **/Zc: noexceptTypes**. Vypněte tuto možnost zadáním parametru **/Zc: noexceptTypes-** pro návrat k chování c++ 14 `noexcept`, když je zadána možnost **/std: c++ 17** nebo **/std: nejnovější** .

Počínaje verzí Visual Studio 2017 verze 15,5 C++ kompilátor diagnostikuje více neodpovídající specifikace výjimek v deklaracích v režimu c++ 17 nebo když zadáte možnost [/Permissive-](permissive-standards-conformance.md) .

Tento příklad ukazuje, jak se deklarace se specifikátorem výjimky chová při nastavení nebo zakázání možnosti **/Zc: noexceptTypes** . Chcete-li zobrazit chování při nastavení, zkompilujte pomocí `cl /EHsc /W4 noexceptTypes.cpp`. Chcete-li zobrazit chování, je-li zakázáno, zkompilujte pomocí `cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp`.

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

Při kompilaci pomocí výchozího nastavení **/Zc: noexceptTypes**vygeneruje ukázka uvedená upozornění. Chcete-li aktualizovat kód, použijte místo toho následující:

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

Další informace o problémech s kompatibilitou ve vizuálu C++najdete v tématu [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **Vlastnosti konfigurace** > stránce vlastností **příkazového řádku** **jazyka C/C++**  > .

1. Upravte vlastnost **Další možnosti** tak, aby zahrnovala parametr **/Zc: noexceptTypes** nebo **/Zc: noexceptTypes-** a pak klikněte na **tlačítko OK**.

## <a name="see-also"></a>Viz také:

[/Zc (shoda)](zc-conformance.md)\
[s výjimkou](../../cpp/noexcept-cpp.md)\
[Specifikace výjimek (throw)](../../cpp/exception-specifications-throw-cpp.md)
