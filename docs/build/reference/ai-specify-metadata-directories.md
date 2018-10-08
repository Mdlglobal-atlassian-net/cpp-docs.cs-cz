---
title: -AI (zadání adresáře metadat) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.AdditionalUsingDirectories
- VC.Project.VCNMakeTool.AssemblySearchPath
- /AI
- VC.Project.VCCLWCECompilerTool.AdditionalUsingDirectories
dev_langs:
- C++
helpviewer_keywords:
- /AI compiler option [C++]
- AI compiler option [C++]
- -AI compiler option [C++]
ms.assetid: fb9c1846-504c-4a3b-bb39-c8696de32f6f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ba4cb1411bca452de0f146626421315fa7dc177e
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2018
ms.locfileid: "48859858"
---
# <a name="ai-specify-metadata-directories"></a>/AI (Zadat adresáře metadat)

Určuje adresář, který kompilátor bude vyhledávání pro přeložení referencí souboru předaných `#using` směrnice.

## <a name="syntax"></a>Syntaxe

> **/AI**_adresáře_

## <a name="arguments"></a>Arguments

*Adresář*<br/>
Adresář nebo cesta, které má kompilátor prohledat.

## <a name="remarks"></a>Poznámky

Lze předat pouze jeden adresář **/AI** vyvolání. Zadejte jednu **/AI** možnost pro každou cestu, kterou má kompilátor prohledat. Například pro přidání do vyhledávací cesty kompilátoru C:\Project\Meta a C:\Common\Meta `#using` direktivy, přidejte `/AI"C:\Project\Meta" /AI"C:\Common\Meta"` do příkazového řádku kompilátoru nebo přidejte všechny adresáře do **další # adresáře using** Vlastnost v sadě Visual Studio.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **Obecné** stránku vlastností.

1. Upravit **další # adresáře using** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalUsingDirectories%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)<br/>
[#using – direktiva](../../preprocessor/hash-using-directive-cpp.md)
