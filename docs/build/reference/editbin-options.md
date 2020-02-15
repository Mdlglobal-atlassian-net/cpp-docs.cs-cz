---
title: Možnosti EDITBIN
description: Referenční příručka k možnostem příkazového řádku nástroje Microsoft nástroje EDITBIN
ms.date: 02/09/2020
f1_keywords:
- editbin
helpviewer_keywords:
- EDITBIN program, options
ms.assetid: 2da9f88e-cbab-4d64-bb66-ef700535230f
ms.openlocfilehash: c27172522ceabeccd06d7b957aa791edc49beec8
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257699"
---
# <a name="editbin-options"></a>Možnosti EDITBIN

NÁSTROJE EDITBIN můžete použít k úpravě souborů objektů, spustitelných souborů a knihoven DLL (Dynamic-Link Library). Možnosti určují změny, které nástroje EDITBIN provede.

Možnost se skládá z specifikátoru možnosti, který je buď spojovník (`-`), nebo lomítko (`/`) následovaný názvem možnosti. Názvy možností nejde zkracovat. Některé možnosti přijímají argumenty, které jsou zadány po dvojtečkě (`:`). Ve specifikaci možnosti nejsou povoleny mezery ani tabulátory. Jednotlivé specifikace možností lze na příkazovém řádku oddělit jednou nebo více mezerami či tabulátory. Názvy možností a jejich argumenty klíčového slova nebo argumenty názvu souboru nerozlišují velká a malá písmena. Například `-bind` a `/BIND` znamenají stejnou věc.

NÁSTROJE EDITBIN má následující možnosti:

|Možnost|Účel|
|------------|-------------|
|[/ALLOWBIND](allowbind.md)|Určuje, zda může být vytvořena vazba knihovny DLL.|
|[/ALLOWISOLATION](allowisolation.md)|Určuje chování knihovny DLL nebo spustitelného souboru pro vyhledávání manifestu.|
|[/APPCONTAINER](appcontainer.md)|Určuje, jestli aplikace musí běžet v rámci kontejneru AppContainer, například v aplikaci pro UWP.|
|[/BIND](bind.md)|Nastaví adresy pro vstupní body v zadaných objektech, aby se urychlila doba načítání.|
|[/DYNAMICBASE](dynamicbase.md)|Určuje, jestli se knihovna DLL nebo spustitelná image dá náhodně využít při načtení, pomocí náhodnosti rozložení adresního prostoru (ASLR).|
|[/ERRORREPORT](errorreport-editbin-exe.md)| Zastaralé Zasílání zpráv o chybách se řídí nastavením [zasílání zpráv o chybách systému Windows (WER)](/windows/win32/wer/windows-error-reporting) . |
|[/HEAP](heap.md)|Nastaví velikost haldy spustitelných imagí v bajtech.|
|[/HIGHENTROPYVA](highentropyva.md)|Určuje, zda knihovna DLL nebo spustitelná bitová kopie podporuje náhodné vygenerování rozložení adresního prostoru (ASLR) s vysokou entropií (64 bitů).|
|[/INTEGRITYCHECK](integritycheck.md)|Určuje, zda se má v době načítání kontrolovat digitální podpis.|
|[/LARGEADDRESSAWARE](largeaddressaware.md)|Určuje, zda objekt podporuje adresy větší než 2 gigabajty.|
|[/NOLOGO](nologo-editbin.md)|Potlačí úvodní nápis nástroje Editbin.|
|[/NXCOMPAT](nxcompat.md)|Určuje, jestli je spustitelná image kompatibilní s zabráněním spuštění dat systému Windows.|
|[/REBASE](rebase.md)|Nastaví základní adresy pro zadané objekty.|
|[/RELEASE](release.md)|Nastaví kontrolní součet v hlavičce.|
|[/SECTION](section-editbin.md)|Přepisuje atributy oddílu.|
|[/STACK](stack.md)|Nastaví velikost zásobníku spustitelných imagí v bajtech.|
|[/SUBSYSTEM](subsystem.md)|Určuje spouštěcí prostředí.|
|[/SWAPRUN](swaprun.md)|Určuje, že se spustitelný obrázek zkopíruje do odkládacího souboru a pak se z něj spustí.|
|[/TSAWARE](tsaware.md)|Určuje, že aplikace je navržená tak, aby běžela v prostředí s více uživateli.|
|[/VERSION](version.md)|Nastaví číslo verze v záhlaví.|

## <a name="see-also"></a>Viz také

[Další nástroje pro sestavení MSVC](c-cpp-build-tools.md)\
[EDITBIN – referenční dokumentace](editbin-reference.md)
