---
title: 'Sestavení souborů informací o procházení: Přehled'
ms.date: 05/06/2019
helpviewer_keywords:
- .bsc files, about .bsc files
- bsc files, about bsc files
- browse information files (.bsc)
- browse information files (.bsc), creating
ms.assetid: b5c12832-51f6-4953-8044-4264dd0fb242
ms.openlocfilehash: ffacb7aaf9ac1f7ad6fc4cf12ab479099dc57725
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320672"
---
# <a name="building-browse-information-files-overview"></a>Sestavení souborů informací o procházení: Přehled

> [!WARNING]
> Přestože BSCMAKE je stále nainstalován s Visual Studio, je již používán ide. Od aplikace Visual Studio 2008 jsou informace o procházení a symbolech automaticky uloženy v souboru SQL Server .sdf ve složce řešení.

Chcete-li vytvořit informace o procházení pro procházení symbolů, kompilátor vytvoří soubor .sbr pro každý zdrojový soubor v projektu a poté BSCMAKE. EXE zřetězí soubory .sbr do jednoho souboru BSC.

Generování souborů .sbr a BSC nějakou dobu trvá, takže Visual Studio tyto funkce ve výchozím nastavení vypne. Chcete-li procházet aktuální informace, je nutné zapnout možnosti procházení a znovu sestavit projekt.

Pomocí [/FR](fr-fr-create-dot-sbr-file.md) nebo [/Fr](fr-fr-create-dot-sbr-file.md) sdělte kompilátoru, aby vytvořil soubory SBR. Chcete-li vytvořit soubory BSC, můžete volat [BSCMAKE](bscmake-command-line.md) z příkazového řádku. Použití BSCMAKE z příkazového řádku poskytuje přesnější kontrolu nad manipulací s informačními soubory procházení. Další informace naleznete v [tématu BSCMAKE Reference.](bscmake-reference.md)

> [!TIP]
> Generování souborů .sbr můžete zapnout, ale ponechat generování souborů BSC vypnuto. To poskytuje rychlé sestavení, ale také umožňuje rychle vytvořit nový soubor BSC zapnutím generování souboru BSC a sestavením projektu.

Zkrátíte čas, paměť a místo na disku potřebné k vytvoření souboru BSC zmenšením velikosti souboru BSC.

Informace o tom, jak vytvořit soubor prohlížeče ve vývojovém prostředí, najdete v tématu [Stránka obecných vlastností (Project).](general-property-page-project.md)

### <a name="to-create-a-smaller-bsc-file"></a>Vytvoření menšího souboru BSC

1. Pomocí [možností příkazového řádku BSCMAKE](bscmake-options.md) vylučte informace z informačního souboru procházení.

1. Při kompilaci nebo sestavování vyneche místní symboly v jednom nebo více souborech .sbr.

1. Pokud soubor objektu neobsahuje informace potřebné pro aktuální fázi ladění, vynechejte jeho soubor SBR z příkazu BSCMAKE při opětovném sestavení informačního souboru procházení.

### <a name="to-combine-the-browse-information-from-several-projects-into-one-browser-file-bsc"></a>Sloučení informací o procházení z několika projektů do jednoho souboru prohlížeče (.bsc)

1. Buď nevytvářejte soubor BSC na úrovni projektu, nebo použijte přepínač /n, abyste zabránili zkrácení souborů .sbr.

1. Po spuštění všech projektů spusťte BSCMAKE se všemi soubory .sbr jako vstup. Zástupné znaky jsou akceptovány. Pokud jste například měli v sobě adresáře projektu C:\X, C:\Y a C:\Z se soubory .sbr a chtěli jste je všechny zkombinovat\\\*do jednoho souboru\\\*BSC, použijte\\\*k vytvoření kombinovaného souboru Bsc soubor BSC:\X .sbr C:\Z .sbr /o c:\whatever_directory\combined.bsc.

## <a name="see-also"></a>Viz také

[Další nástroje pro sestavení msvc](c-cpp-build-tools.md)<br/>
[BSCMAKE – referenční dokumentace](bscmake-reference.md)
