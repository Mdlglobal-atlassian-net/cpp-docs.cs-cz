---
title: 'Sestavení souborů informací o procházení: Přehled'
ms.date: 11/04/2016
helpviewer_keywords:
- .bsc files, about .bsc files
- bsc files, about bsc files
- browse information files (.bsc)
- browse information files (.bsc), creating
ms.assetid: b5c12832-51f6-4953-8044-4264dd0fb242
ms.openlocfilehash: 4f12bd25ca3ab718a845dbb04aba3169cc6d4b19
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820605"
---
# <a name="building-browse-information-files-overview"></a>Sestavení souborů informací o procházení: Přehled

K vytvoření informací o procházení pro procházení symbolů, kompilátor vytvoří soubor .sbr pro každý zdrojový soubor v projektu, pak BSCMAKE. Soubor EXE řetězí soubory .sbr do jednoho souboru .bsc.

Generují se soubory .sbr a .bsc zabere určitý čas, takže Visual C++ vypne tyto funkce ve výchozím nastavení. Pokud chcete aktuální informace o procházení, musíte zapnout možnosti procházení a sestavte projekt znovu.

Použití [/FR](fr-fr-create-dot-sbr-file.md) nebo [/Fr](fr-fr-create-dot-sbr-file.md) říct kompilátor vytvoří soubory .sbr. Pokud chcete vytvořit soubory .bsc, můžete volat [BSCMAKE](bscmake-command-line.md) z příkazového řádku. Pomocí nástroje BSCMAKE z příkazového řádku poskytuje přesnější kontrolu nad zpracování souborů informací o procházení. Zobrazit [BscMake – referenční dokumentace](bscmake-reference.md) Další informace.

> [!TIP]
>  Můžete zapnout generování souboru .sbr ale ponechte generování souboru .bsc vypnuté. Tento postup umožňuje rychlé sestavení, ale také umožňuje rychle vytvořit soubor .bsc čerstvé zapnutím generování souboru .bsc a sestavením projektu.

Můžete snížit čas, paměť a místo na disku potřebné k sestavení souboru .bsc snížením velikosti souboru .bsc.

Zobrazit [Obecná stránka vlastností (projekt)](general-property-page-project.md) informace o tom, jak vytvořit soubor prohlížeče ve vývojovém prostředí.

### <a name="to-create-a-smaller-bsc-file"></a>Chcete-li vytvořit menší soubor .bsc

1. Použití [bscmakee – možnosti příkazového řádku](bscmake-options.md) vyloučit informace z informačního souboru procházení.

1. Vynechte lokální symboly v jedné nebo více soubory .sbr při kompilaci nebo sestavení.

1. Pokud soubor objektu neobsahuje informace potřebné pro vaši aktuální fázi ladění, vynechte jeho soubor .sbr z příkazu BSCMAKE při opětovném sestavování informačního souboru procházení.

### <a name="to-combine-the-browse-information-from-several-projects-into-one-browser-file-bsc"></a>Ke sloučení informací procházení z několika projektů do souboru jeden prohlížeč (.bsc)

1. Buď není sestavení souboru .bsc na úrovni projektu nebo pomocí přepínače /n zabránit soubory .sbr vedlo ke zkrácení.

1. Po jsou všechny projekty sestaveny, spusťte nástroj BSCMAKE všechny soubory .sbr jako vstup. Zástupné znaky. Například pokud jste měli adresáře projektu C:\X C:\Y a C:\Z se soubory .sbr je, a chtěli je zkombinovat do jednoho souboru BSC programem, použijte nástroje BSCMAKE C:\X\\\*.sbr C:\Y\\\*.sbr C:\Z\\ \*.sbr /o c:\whatever_directory\combined.bsc pro sestavení souboru .bsc kombinované.

## <a name="see-also"></a>Viz také:

[Nástroje pro vytváření dalších MSVC](c-cpp-build-tools.md)<br/>
[BSCMAKE – referenční dokumentace](bscmake-reference.md)
