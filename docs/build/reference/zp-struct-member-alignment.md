---
title: -Zp (zarovnání členů struktury) | Microsoft Docs
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
ms.openlocfilehash: 1666da40f748d18c762eae19595692addcdbf78a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="zp-struct-member-alignment"></a>/Zp (zarovnání členů struktury)

Řídí, jak jsou členy struktury zabaleny do paměti a určuje stejné okolních pro všechny struktury v modulu.

## <a name="syntax"></a>Syntaxe

> **/Zp**[**1**|**2**|**4**|**8** | **16**]

## <a name="remarks"></a>Poznámky

Pokud zadáte **/Zp**_n_ možnost, každý člen struktura po uložení první velikost typ člena nebo *n*-hranice bajtů (kde *n* je 1, 2, 4, 8 nebo 16), než je menší.

K dispozici okolních hodnoty jsou popsány v následující tabulce:

|/Zp argument|Efekt|
|-|-|
|1|Balíčky struktury v rozsahu 1bajtů. Stejné jako **/Zp**.|
|2|Balíčky struktury na hranicích 2bajtová.|
|4|Balíčky struktury na hranicích 4bajtový.|
|8|Balíčky struktury na hranicích 8bajtový (výchozí).|
|16| Balíčky struktury na hranicích 16 bajtů.|

Tuto možnost byste neměli používat, pokud máte požadavky na konkrétní souvislost.

> [!WARNING]  
> Předpokládejme hlavičky C++ v sadě Windows SDK **/Zp8** balení. Pokud může dojít k poškození paměti **/Zp** nastavení se změní, když pomocí sady Windows SDK hlavičky.

Můžete také použít [pack](../../preprocessor/pack.md) k okolních struktura ovládacího prvku. Další informace o zarovnání naleznete v následujících tématech:

- [align](../../cpp/align-cpp.md)

- [__alignof – operátor](../../cpp/alignof-operator.md)

- [__unaligned](../../cpp/unaligned.md)

- [Příklady zarovnání struktur](../../build/examples-of-structure-alignment.md) (x64 konkrétní)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **C/C++** > **generování kódu** stránku vlastností.

1. Změnit **Strukturování členských přidružení** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StructMemberAlignment%2A>.

## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
- [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)
