---
title: 'Sestavení souborů informací o procházení: Přehled'
ms.date: 05/06/2019
helpviewer_keywords:
- .bsc files, about .bsc files
- bsc files, about bsc files
- browse information files (.bsc)
- browse information files (.bsc), creating
ms.assetid: b5c12832-51f6-4953-8044-4264dd0fb242
ms.openlocfilehash: 94cb5865e56e12f51ef4a8598a5df3fcbe69fa0f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078362"
---
# <a name="building-browse-information-files-overview"></a>Sestavení souborů informací o procházení: Přehled

> [!WARNING]
> I když je aplikace BSCMAKE stále nainstalována se sadou Visual Studio, již není používána rozhraním IDE. Vzhledem k tomu, že se Visual Studio 2008, informace o procházení a symbolech se ukládají automaticky do souboru SQL Server. SDF ve složce řešení.

Chcete-li vytvořit informace o procházení pro procházení symbolů, kompilátor vytvoří soubor. sbr pro každý zdrojový soubor v projektu a pak BSCMAKE. EXE zřetězí soubory. sbr do jednoho souboru. BSC.

Generování souborů. sbr a. BSC trvá čas, takže Visual Studio tyto funkce ve výchozím nastavení vypne. Chcete-li procházet aktuální informace, je nutné zapnout možnosti procházení a znovu sestavit projekt.

Pomocí [/fr](fr-fr-create-dot-sbr-file.md) nebo [/fr](fr-fr-create-dot-sbr-file.md) sdělte kompilátoru, aby vytvořil soubory. sbr. Chcete-li vytvořit soubory. BSC, můžete volat [BSCMAKE](bscmake-command-line.md) z příkazového řádku. Pomocí BSCMAKE z příkazového řádku získáte přesnější kontrolu nad manipulací se soubory s informacemi o procházení. Další informace najdete v [referenčních](bscmake-reference.md) informacích k BSCMAKE.

> [!TIP]
>  Můžete zapnout generování souborů. SBR, ale ponechat vypnuto generování souboru BSC. To poskytuje rychlé sestavení, ale také umožňuje rychle vytvořit nový soubor. BSC tím, že zapnete generování souborů. BSC a sestavíte projekt.

Omezením velikosti souboru. BSC můžete zkrátit čas, paměť a místo na disku potřebné k vytvoření souboru. BSC.

Informace o tom, jak vytvořit soubor prohlížeče ve vývojovém prostředí, najdete v části [Obecná stránka vlastností (projekt)](general-property-page-project.md) .

### <a name="to-create-a-smaller-bsc-file"></a>Vytvoření menšího souboru. BSC

1. K vyloučení informací ze souboru s informacemi o procházení použijte [Možnosti příkazového řádku BSCMAKE](bscmake-options.md) .

1. Vynechání místních symbolů v jednom nebo více souborech. sbr při kompilování nebo sestavování.

1. Pokud soubor objektu neobsahuje informace potřebné pro vaši aktuální fázi ladění, vynechejte jeho soubor. SBR z příkazu BSCMAKE při opětovném sestavování souboru s informacemi o procházení.

### <a name="to-combine-the-browse-information-from-several-projects-into-one-browser-file-bsc"></a>Kombinování informací o procházení z několika projektů do jednoho souboru prohlížeče (. BSC)

1. Buď nevytvářejte soubor. bsc na úrovni projektu, nebo použijte přepínač/n, abyste zabránili zkracování souborů. sbr.

1. Po sestavení všech projektů spusťte BSCMAKE se všemi soubory. sbr jako vstupem. Zástupné znaky jsou přijaty. Pokud byste například měli adresáře projektu C:\X, C:\Y a C:\Z se soubory. SBR v nich a chtěli jste je zkombinovat do jednoho souboru. BSC, použijte BSCMAKE C:\X\\\*. sbr C:\Y\\\*. sbr C:\Z\\\*. sbr/o c:\ whatever_directory \combined.BSC pro sestavení kombinovaného souboru BSC.

## <a name="see-also"></a>Viz také

[Další nástroje pro sestavení MSVC](c-cpp-build-tools.md)<br/>
[BSCMAKE – referenční dokumentace](bscmake-reference.md)
