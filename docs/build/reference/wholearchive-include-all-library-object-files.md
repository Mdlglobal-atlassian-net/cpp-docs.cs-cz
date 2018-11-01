---
title: / WHOLEARCHIVE (zahrnutí všech souborů objektů knihovny)
ms.date: 11/04/2016
ms.assetid: ee92d12f-18af-4602-9683-d6223be62ac9
ms.openlocfilehash: 26bd720a2ecd07bccb1317e1540cb071e7027078
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494221"
---
# <a name="wholearchive-include-all-library-object-files"></a>/ WHOLEARCHIVE (zahrnutí všech souborů objektů knihovny)

Platnost linkeru, aby zahrnutí všech souborů objektů ze statické knihovny v propojený spustitelný soubor.

## <a name="syntax"></a>Syntaxe

> / WHOLEARCHIVE [:*knihovny*]

## <a name="remarks"></a>Poznámky

Možnost /WHOLEARCHIVE vynutí linkeru pro zahrnutí každého objektu souboru buď z zadané statické knihovny, nebo pokud není zadána žádná knihovna, ze všech statických knihoven zadaný odkaz na příkaz. Zadejte možnost /WHOLEARCHIVE pro více knihoven, můžete více než jeden /WHOLEARCHIVE přepínat do příkazového řádku linkeru. Ve výchozím nastavení linker obsahuje soubory objektů v propojené výstup jenom v případě, že jsou symboly, které odkazují jiné objektové soubory ve spustitelném souboru exportu. Možnost /WHOLEARCHIVE díky linkeru považoval všechny soubory objekt archivovat ve statické knihovně, jako kdyby byly jednotlivě zadány do příkazového řádku linkeru.

Možnost /WHOLEARCHIVE je možné znovu exportovat všechny symboly ze statické knihovny. To umožňuje Ujistěte se, že všechny knihovny kódu, prostředky a metadata jsou zahrnuty při vytvoření komponenty z více než jednu statickou knihovnu. Pokud se zobrazí upozornění LNK4264 při vytváření statickou knihovnu, která obsahuje součásti prostředí Windows Runtime pro export, použijte možnost /WHOLEARCHIVE při propojování knihovny do jiné aplikace nebo komponenty.

Možnost /WHOLEARCHIVE byla zavedena v aplikaci Visual Studio 2015 Update 2.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Nastavení této možnosti linkeru v sadě Visual Studio

1. Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **příkazového řádku** stránka vlastností v rámci **vlastnosti konfigurace**, **Linkeru**.

1. Přidat možnost /WHOLEARCHIVE **další možnosti** textového pole.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)