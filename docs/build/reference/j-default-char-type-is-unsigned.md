---
title: -J (výchozí znakový typ není podepsán) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.DefaultCharIsUnsigned
- VC.Project.VCCLWCECompilerTool.DefaultCharIsUnsigned
- /j
dev_langs:
- C++
helpviewer_keywords:
- defaults, char type
- char data type
- -J compiler option [C++]
- /J compiler option [C++]
- J compiler option [C++]
- default char type is unsigned
ms.assetid: 50973667-6638-491e-9c41-bff73acae19f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 400985751d9ceebf7cc2c5f632cb33c5ba847bfe
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714282"
---
# <a name="j-default-char-type-is-unsigned"></a>/J (Výchozí znakový typ není podepsán)

Změní výchozí `char` typ z `signed char` k `unsigned char`a `char` typ je nulou při je rozšíření na `int` typu.

## <a name="syntax"></a>Syntaxe

```
/J
```

## <a name="remarks"></a>Poznámky

Pokud `char` hodnota je explicitně deklarována jako `signed`, **/J** možnost ji neovlivní a hodnota je rozšířena o znaménko při je rozšíření na `int` typu.

**/J** možnost definuje `_CHAR_UNSIGNED`, který se používá s `#ifndef` v LIMITS.h souboru pro účely definování rozsahu výchozí `char` typu.

ANSI C a C++ se nevyžaduje konkrétní implementaci `char` typu. Tato možnost je užitečná při práci s daty znak, který bude nakonec převedeny do jiného jazyka než angličtiny.

> [!NOTE]
>  Pokud použijete tuto možnost kompilátoru s knihovnou ATL/MFC, může být generována chyba. I když se tato chyba může zakázat tak, že definujete `_ATL_ALLOW_CHAR_UNSIGNED`, toto řešení se nepodporuje a vždy nemusí fungovat.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. V **Průzkumníka řešení**, otevřete místní nabídku pro projekt a klikněte na tlačítko **vlastnosti**.

1. V projektu **stránky vlastností** dialogové okno, v levém podokně v části **vlastnosti konfigurace**, rozbalte **C/C++** a pak vyberte **příkazovéhořádku**.

1. V **další možnosti** podokně, zadejte **/J** – možnost kompilátoru.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DefaultCharIsUnsigned%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)<br/>
[Práce s vlastnostmi projektu](../../ide/working-with-project-properties.md)