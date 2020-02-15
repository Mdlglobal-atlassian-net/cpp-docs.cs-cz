---
title: /WHOLEARCHIVE (zahrnout všechny soubory objektů knihovny)
ms.date: 02/12/2020
ms.assetid: ee92d12f-18af-4602-9683-d6223be62ac9
ms.openlocfilehash: 95685c9c0dfde45c42449bbcad67228a0e21b36a
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257530"
---
# <a name="wholearchive-include-all-library-object-files"></a>/WHOLEARCHIVE (zahrnout všechny soubory objektů knihovny)

Vynutit, aby linker zahrnoval všechny soubory objektů ve statické knihovně v propojeném spustitelném souboru.

## <a name="syntax"></a>Syntaxe

> **/WHOLEARCHIVE**\
> **/WHOLEARCHIVE:** _Library_

### <a name="arguments"></a>Argumenty

\ *knihovny*
Volitelná cesta ke statické knihovně. Linker zahrnuje všechny soubory objektů z této knihovny.

## <a name="remarks"></a>Poznámky

Možnost/WHOLEARCHIVE vynutí linkeru zahrnout všechny soubory objektů ze zadané statické knihovny, nebo pokud není zadána žádná knihovna, ze všech statických knihoven zadaných do příkazu LINK. Chcete-li určit možnost/WHOLEARCHIVE pro více knihoven, můžete použít více než jeden/WHOLEARCHIVE přepínač na příkazovém řádku linkeru. Ve výchozím nastavení linker obsahuje soubory objektů v propojeném výstupu pouze v případě, že exportují symboly, na které odkazuje jiný objekt Files ve spustitelném souboru. Možnost/WHOLEARCHIVE zpřístupňuje linkeru všechny soubory objektů archivované ve statické knihovně, jako kdyby byly zadány jednotlivě na příkazovém řádku linkeru.

Možnost/WHOLEARCHIVE lze použít k opětovnému exportu všech symbolů ze statické knihovny. To vám umožní zajistit, aby veškerý kód knihovny, prostředky a metadata byly zahrnuty při vytváření komponenty z více než jedné statické knihovny. Pokud se zobrazí upozornění LNK4264 při vytváření statické knihovny, která obsahuje komponenty prostředí Windows Runtime pro export, použijte možnost/WHOLEARCHIVE při propojování této knihovny s jinou komponentou nebo aplikací.

Možnost/WHOLEARCHIVE byla představena v aktualizaci Visual Studio 2015 Update 2.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Nastavení této možnosti linkeru v sadě Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Další informace najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte stránku vlastností **příkazový řádek** v části **Vlastnosti konfigurace**, **linker**.

1. Do textového pole **Další možnosti** přidejte možnost/WHOLEARCHIVE.

## <a name="see-also"></a>Viz také

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
