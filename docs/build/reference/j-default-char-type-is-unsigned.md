---
title: /J (Výchozí znakový typ není podepsán)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.DefaultCharIsUnsigned
- VC.Project.VCCLWCECompilerTool.DefaultCharIsUnsigned
- /j
helpviewer_keywords:
- defaults, char type
- char data type
- -J compiler option [C++]
- /J compiler option [C++]
- J compiler option [C++]
- default char type is unsigned
ms.assetid: 50973667-6638-491e-9c41-bff73acae19f
ms.openlocfilehash: 7bcf0f2eb2bef08757250999d0a6696b256fb15c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322201"
---
# <a name="j-default-char-type-is-unsigned"></a>/J (Výchozí znakový typ není podepsán)

Změní výchozí `char` typ `signed char` `unsigned char`z na `char` , a typ je nula `int` rozšířené, pokud je rozšířen na typ.

## <a name="syntax"></a>Syntaxe

```
/J
```

## <a name="remarks"></a>Poznámky

Pokud `char` je hodnota explicitně deklarována jako `signed`, možnost **/J** nemá vliv na něj `int` a hodnota je znaménko rozšířené, pokud je rozšířena na typ.

Volba **/J** definuje `_CHAR_UNSIGNED`, který `#ifndef` se používá v souboru LIMITS.h `char` k definování rozsahu výchozího typu.

ANSI C a C++ nevyžadují konkrétní `char` implementaci typu. Tato možnost je užitečná, pokud pracujete s daty znaků, která budou nakonec přeložena do jiného jazyka než angličtiny.

> [!NOTE]
> Pokud použijete tuto možnost kompilátoru s KNIHOVNOu ATL/MFC, může být generována chyba. Přestože můžete zakázat tuto `_ATL_ALLOW_CHAR_UNSIGNED`chybu definováním , toto řešení není podporováno a nemusí vždy fungovat.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. V **Průzkumníku řešení**otevřete místní nabídku projektu a zvolte **Vlastnosti**.

1. V dialogovém okně **Stránky vlastností** projektu v levém podokně v části **Vlastnosti konfigurace**rozbalte **c/c++** a pak vyberte **Příkazový řádek**.

1. V podokně **Další možnosti** zadejte možnost kompilátoru **/J.**

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DefaultCharIsUnsigned%2A>.

## <a name="see-also"></a>Viz také

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[Nastavení vlastností kompilátoru a sestavení C++ v sadě Visual Studio](../working-with-project-properties.md)
