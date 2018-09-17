---
title: -Zp (zarovnání členů struktury) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 04/30/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /zp
- VC.Project.VCCLCompilerTool.StructMemberAlignment
- VC.Project.VCCLWCECompilerTool.StructMemberAlignment
dev_langs:
- C++
helpviewer_keywords:
- Struct Member Alignment compiler option
- Zp compiler option
- /Zp compiler option [C++]
- -Zp compiler option [C++]
ms.assetid: 5242f656-ed9b-48a3-bc73-cfcf3ed2520f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0268f5c5d5d34d8fa244dc6260889bea6b1e837a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715907"
---
# <a name="zp-struct-member-alignment"></a>/Zp (zarovnání členů struktury)

Určuje, jak členy struktury jsou zkomprimována do paměti a určuje stejný komprimaci pro všechny struktury v modulu.

## <a name="syntax"></a>Syntaxe

> **/ Zp**[**1**|**2**|**4**|**8** | **16**]

## <a name="remarks"></a>Poznámky

Pokud zadáte **/zp**_n_ možnost, každý člen struktury po prvním uložen velikosti typ člena nebo *n*-hranice (kde *n* je 1, 2, 4, 8 nebo 16), podle toho, co je menší.

K dispozici balení hodnoty jsou popsány v následující tabulce:

|Argument/zp|Efekt|
|-|-|
|1|Sbalí struktury na 1bajtových hranicích. Stejné jako **/zp**.|
|2|Sbalí struktury na 2bajtových hranicích.|
|4|Sbalí struktury na 4bajtových hranicích.|
|8|Sbalí struktury na 8bajtových hranicích (výchozí).|
|16| Sbalí struktury na 16bajtových hranicích.|

Tuto možnost nepoužívejte, pokud nemáte konkrétní souvislost požadavky.

> [!WARNING]
> Předpokládejme hlaviček jazyka C++ v sadě Windows SDK **/zp8** balení. Pokud může dojít k poškození paměti **/zp** nastavení se změní při použití sady Windows SDK záhlaví.

Můžete také použít [pack](../../preprocessor/pack.md) na balení struktury ovládacího prvku. Další informace o zarovnání naleznete v následujících tématech:

- [align](../../cpp/align-cpp.md)

- [__alignof – operátor](../../cpp/alignof-operator.md)

- [__unaligned](../../cpp/unaligned.md)

- [Příklady zarovnání struktur](../../build/examples-of-structure-alignment.md) (x64 konkrétní)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **C/C++** > **generování kódu** stránku vlastností.

1. Upravit **zarovnání členů struktury** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StructMemberAlignment%2A>.

## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru](../../build/reference/compiler-options.md)
- [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)
