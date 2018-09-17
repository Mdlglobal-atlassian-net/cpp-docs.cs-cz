---
title: -DLL (sestavení knihovny DLL) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /dll
dev_langs:
- C++
helpviewer_keywords:
- -DLL linker option
- /DLL linker option [C++]
- exporting DLLs [C++], specifying exports
- DLLs [C++], building
- DLL linker option [C++]
ms.assetid: c7685aec-31d0-490f-9503-fb5171a23609
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ec5beed66de3834759f35a5021d0155eab0a066e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716823"
---
# <a name="dll-build-a-dll"></a>/DLL (Sestavit knihovnu DLL)

```
/DLL
```

## <a name="remarks"></a>Poznámky

Možnost/DLL sestavení a knihovny DLL jako hlavní výstupního souboru. Knihovny DLL obvykle obsahuje exporty se dají jiným programem. Existují tři metody pro určení exportů uvedené v doporučené pořadí podle používání:

1. [__declspec(dllexport)](../../cpp/dllexport-dllimport.md) ve zdrojovém kódu

1. [EXPORTY](../../build/reference/exports.md) – příkaz souboru .def

1. [/EXPORT](../../build/reference/export-exports-a-function.md) specifikace v příkazu LINK

Program můžete použít více než jednu metodu.

Dalším způsobem, jak sestavit knihovnu DLL se **KNIHOVNY** příkaz definice modulu. Možnosti propojovacího a/DLL společně odpovídají **KNIHOVNY** příkazu.

Tato možnost ve vývojovém prostředí; není zadáno Tato možnost je pro použití pouze v příkazovém řádku. Tato možnost je nastavena při vytváření projektu knihovny DLL pomocí Průvodce aplikací.

Všimněte si, že když vytvoříte knihovny importu v předběžný krok před vytvořením vaší knihovny DLL, je nutné předat stejnou sadu souborů objektů při sestavování knihovny DLL, jako úspěšný při sestavování knihovny importu.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **vlastnosti konfigurace** složky.

1. Klikněte na tlačítko **Obecné** stránku vlastností.

1. Upravit **typ konfigurace** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCPropertySheet.ConfigurationType%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)