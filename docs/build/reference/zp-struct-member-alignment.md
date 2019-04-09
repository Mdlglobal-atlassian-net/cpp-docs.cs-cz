---
title: /Zp (zarovnání členů struktury)
ms.date: 04/04/2019
f1_keywords:
- /zp
- VC.Project.VCCLCompilerTool.StructMemberAlignment
- VC.Project.VCCLWCECompilerTool.StructMemberAlignment
helpviewer_keywords:
- Struct Member Alignment compiler option
- Zp compiler option
- /Zp compiler option [C++]
- -Zp compiler option [C++]
ms.assetid: 5242f656-ed9b-48a3-bc73-cfcf3ed2520f
ms.openlocfilehash: d76cd93c7af4228bff8f73fa3bcbf40fa149b0be
ms.sourcegitcommit: 35c4b3478f8cc310ebbd932a18963ad8ab846ed9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59237161"
---
# <a name="zp-struct-member-alignment"></a>/Zp (zarovnání členů struktury)

Určuje, jak členy struktury jsou zkomprimována do paměti a určuje stejný komprimaci pro všechny struktury v modulu.

## <a name="syntax"></a>Syntaxe

> **/Zp**[**1**|**2**|**4**|**8**|**16**]

## <a name="remarks"></a>Poznámky

**/Zp**_n_ možnost instruuje kompilátor, kam se mají ukládat každý člen struktury. Kompilátor ukládá členy po první z nich na hranici, která je menší velikosti typ člena nebo *n*-bajtovou hranici.

K dispozici balení hodnoty jsou popsány v následující tabulce:

|Argument/zp|Efekt|
|-|-|
|1|Sbalí struktury na 1bajtových hranicích. Stejné jako **/zp**.|
|2|Sbalí struktury na 2bajtových hranicích.|
|4|Sbalí struktury na 4bajtových hranicích.|
|8|Sbalí struktury na 8bajtových hranicích (výchozí nastavení pro x86, ARM a ARM64).|
|16| Sbalí struktury na 16bajtových hranicích (výchozí nastavení pro x64).|

Nepoužívejte tuto možnost, pokud máte požadavky na konkrétní souvislost.

> [!WARNING]
> Nastavení hlaviček jazyka C++ v sadě Windows SDK a předpokládají **/zp8** balení interně. Pokud může dojít k poškození paměti **/zp** nastavení se změní v záhlaví Windows SDK. Záhlaví neovlivní žádné **/zp** možnost nastavíte na příkazovém řádku.

Můžete také použít [pack](../../preprocessor/pack.md) na balení struktury ovládacího prvku. Další informace o zarovnání naleznete v následujících tématech:

- [align](../../cpp/align-cpp.md)

- [__alignof – operátor](../../cpp/alignof-operator.md)

- [__unaligned](../../cpp/unaligned.md)

- [/ALIGN (zarovnání oddílů)](align-section-alignment.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **generování kódu** stránku vlastností.

1. Upravit **zarovnání členů struktury** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StructMemberAlignment%2A>.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru MSVC](compiler-options.md) \
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
