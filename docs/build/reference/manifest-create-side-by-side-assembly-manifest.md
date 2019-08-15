---
title: /MANIFEST (vytvoření manifestu souběžného sestavení)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.GenerateManifest
helpviewer_keywords:
- -MANIFEST linker option
- /MANIFEST linker option
- MANIFEST linker option
ms.assetid: 98c52e1e-712c-4f49-b149-4d0a3501b600
ms.openlocfilehash: ea58b43accdd854665fad3b70d7aecbc9eaa0f9e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492782"
---
# <a name="manifest-create-side-by-side-assembly-manifest"></a>/MANIFEST (vytvoření manifestu souběžného sestavení)

```
/MANIFEST[:{EMBED[,ID=#]|NO}]
```

## <a name="remarks"></a>Poznámky

Volba /MANIFEST určuje, že má linker vytvořit souběžný soubor manifestu. Další informace o souborech manifestu naleznete v tématu [Reference k souborům manifestu](/windows/win32/SbsCs/manifest-files-reference).

Výchozí hodnota je /MANIFEST.

Volba /MANIFEST:EMBED určuje, že má linker vložit soubor manifestu do bitové kopie jako prostředek typu RT_MANIFEST. Volitelný parametr `ID` je ID prostředku, které se použije pro manifest. Pro spustitelný soubor použijte hodnotu 1. Pro knihovnu DLL použijte hodnotu 2, aby bylo možné určit soukromé závislosti. Pokud parametr `ID` není zadán, výchozí hodnota je 2, pokud je nastavena volba /DLL. Jinak je výchozí hodnota 1.

Počínaje sadou Visual Studio 2008 soubory manifestu pro spustitelné soubory obsahují oddíl, který určuje informace o nástroji Řízení uživatelských účtů (UAC). Pokud zadáte/MANIFEST, ale nezadáte ani [/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md) ani [/DLL](dll-build-a-dll.md), do manifestu se vloží výchozí fragment nástroje řízení uživatelských účtů, který má na úrovni nástroje řízení uživatelských účtů nastavenou hodnotu *podle volajícího* . Další informace o úrovních nástroje řízení uživatelských účtů najdete [v tématu/MANIFESTUAC (vkládání informací o nástroji Řízení uživatelských účtů v manifestu)](manifestuac-embeds-uac-information-in-manifest.md).

Chcete-li změnit výchozí chování nástroje Řízení uživatelských účtů, proveďte jeden z následujících kroků:

- Určete volbu /MANIFESTUAC a nastavte úroveň nástroje Řízení uživatelských účtů na požadovanou hodnotu.

- Nebo určete možnost /MANIFESTUAC:NO, pokud nechcete v manifestu generovat fragment nástroje Řízení uživatelských účtů.

Pokud nezadáte/MANIFEST, ale zadáte komentáře [/MANIFESTDEPENDENCY](manifestdependency-specify-manifest-dependencies.md) , vytvoří se soubor manifestu. Soubor manifestu nebude vytvořen, pokud určíte volbu /MANIFEST:NO.

Pokud určíte volbu /MANIFEST, název souboru manifestu bude stejný jako název výstupního souboru, ale s příponou .manifest připojenou k názvu souboru. Například pokud bude název výstupního souboru MyFile.exe, název souboru manifestu bude MyFile.exe.manifest.  Pokud zadáte/MANIFESTFILE:*Name*, název manifestu je to, co zadáte v *názvu*.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Rozbalte uzel **Vlastnosti konfigurace** .

1. Rozbalte uzel **linker** .

1. Vyberte stránku vlastností **souboru manifestu** .

1. Upravte vlastnost **Generovat Manifest** .

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

1. Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateManifest%2A>.

## <a name="see-also"></a>Viz také:

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
