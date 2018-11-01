---
title: /Fm (název souboru mapování)
ms.date: 11/04/2016
f1_keywords:
- /fm
helpviewer_keywords:
- -Fm compiler option [C++]
- mapfiles [C++], creating linker
- files [C++], creating map
- Fm compiler option [C++]
- /Fm compiler option [C++]
ms.assetid: 8154448a-93a7-4546-8e4c-5c44d0aff45d
ms.openlocfilehash: 49a3d20aee54b06bae2670be139d748fd2aaca6d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50469849"
---
# <a name="fm-name-mapfile"></a>/Fm (název souboru mapování)

Přikáže linkeru, aby se vytvoří soubor mapfile obsahující seznam segmenty v pořadí, v jakém jsou uvedeny v odpovídající soubor .exe nebo knihovny DLL.

## <a name="syntax"></a>Syntaxe

```
/Fmpathname
```

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení, souboru mapování je uveden základní název odpovídajícího jazyka C nebo C++ zdrojového souboru s. MAPOVÁNÍ přípony.

Určení **/Fm** má stejný účinek, jako by se měl zadat [parametr/map (generování souboru mapování)](../../build/reference/map-generate-mapfile.md) – možnost linkeru.

Pokud zadáte [/c (Kompilovat bez propojení)](../../build/reference/c-compile-without-linking.md) propojování, potlačit **/Fm** nemá žádný vliv.

Globální symboly do souboru mapy obvykle mají jednu nebo více úvodní podtržítka, protože kompilátor přidá vedoucího podtržítka názvy proměnných. Mnoho globální symboly, které se zobrazují v souboru mapfile se používají interně tak, že kompilátor a standardní knihovny.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **příkazového řádku** stránku vlastností.

1. Zadejte možnost do kompilátoru **další možnosti** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Možnosti výstupního souboru (/F)](../../build/reference/output-file-f-options.md)<br/>
[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)<br/>
[Určení názvu cesty](../../build/reference/specifying-the-pathname.md)