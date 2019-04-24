---
title: Možnosti EDITBIN
ms.date: 11/04/2016
f1_keywords:
- editbin
helpviewer_keywords:
- EDITBIN program, options
ms.assetid: 2da9f88e-cbab-4d64-bb66-ef700535230f
ms.openlocfilehash: e7338c6a45d74aa8efac1b72683cca7661c62e0a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271850"
---
# <a name="editbin-options"></a>Možnosti EDITBIN

Editbin – můžete použít k úpravě souborů objektů, spustitelných souborů a dynamické knihovny (DLL). Možnosti určují změny, které provádí EDITBIN.

Možnost sestává ze specifikátoru možnosti, který je buď pomlčka (-) nebo lomítkem (/), za nímž následuje název možnosti. Názvy možností nelze zkracovat. Některé možnosti přijímají argumenty zadané za dvojtečkou (:). Ve specifikaci možnosti nejsou povoleny mezery ani tabulátory. Jednotlivé specifikace možností lze na příkazovém řádku oddělit jednou nebo více mezerami či tabulátory. Názvy možností a jejich – klíčové slovo argumenty nebo argumenty názvů souborů nejsou malá a velká písmena. Například - bind a/BIND mají stejný význam.

Editbin – obsahuje následující možnosti:

|Možnost|Účel|
|------------|-------------|
|[/ALLOWBIND](allowbind.md)|Určuje, zda může být vázaný knihovny DLL.|
|[/ALLOWISOLATION](allowisolation.md)|Určuje knihovnu DLL nebo spustitelného souboru chování při vyhledávání manifestu.|
|[/APPCONTAINER](appcontainer.md)|Určuje, zda je třeba aplikaci spustit v rámci kontejneru AppContainer – například aplikace pro UPW.|
|[/BIND](bind.md)|Nastaví adresy pro vstupní body v zadané objekty, abyste urychlili čas zatížení.|
|[/DYNAMICBASE](dynamicbase.md)|Určuje, zda knihovna DLL nebo spustitelný obraz lze náhodně změnit základ v okamžiku načtení pomocí náhodného generování rozložení prostoru adres (ASLR).|
|[/ ERRORREPORT](errorreport-editbin-exe.md)|Společnosti Microsoft sestavy s interními chybami.|
|[/HEAP](heap.md)|Nastaví velikost haldy spustitelné bitové kopie v bajtech.|
|[/HIGHENTROPYVA](highentropyva.md)|Určuje, zda knihovna DLL nebo spustitelný obraz podporuje vysokou entropie (64-bit) Adresa náhodného generování rozložení prostoru (technologie ASLR).|
|[/INTEGRITYCHECK](integritycheck.md)|Určuje, jestli se má zkontrolovat digitální podpis v okamžiku načtení.|
|[/LARGEADDRESSAWARE](largeaddressaware.md)|Určuje, zda objekt podporuje adresy, které jsou větší než dva gigabajty.|
|[/NOLOGO](nologo-editbin.md)|Potlačí úvodní nápis EDITBIN.|
|[/NXCOMPAT](nxcompat.md)|Určuje, zda spustitelné bitové kopie je kompatibilní s předcházením spuštění dat Windows.|
|[/REBASE](rebase.md)|Nastaví bázové adresy pro zadané objekty.|
|[/RELEASE](release.md)|Nastaví kontrolní součet v hlavičce.|
|[/ SECTION](section-editbin.md)|Obejde atributy oddílu.|
|[/STACK](stack.md)|Nastaví velikost zásobníku spustitelné bitové kopie v bajtech.|
|[/SUBSYSTEM](subsystem.md)|Určuje prostředí spuštění.|
|[/SWAPRUN](swaprun.md)|Určuje, že spustitelné bitové kopie musí být zkopírován do odkládacího souboru a pak spusťte z něj.|
|[/TSAWARE](tsaware.md)|Určuje, že aplikace je navržen pro spouštění v prostředí s více uživateli.|
|[/VERSION](version.md)|Nastaví číslo verze v záhlaví.|

## <a name="see-also"></a>Viz také:

[Nástroje pro vytváření dalších MSVC](c-cpp-build-tools.md)<br/>
[EDITBIN – referenční dokumentace](editbin-reference.md)
