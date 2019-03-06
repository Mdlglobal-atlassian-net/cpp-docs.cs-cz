---
title: Možnosti EDITBIN
ms.date: 11/04/2016
f1_keywords:
- editbin
helpviewer_keywords:
- EDITBIN program, options
ms.assetid: 2da9f88e-cbab-4d64-bb66-ef700535230f
ms.openlocfilehash: 409c40986068475299c95f1be0dff5f15d022520
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424324"
---
# <a name="editbin-options"></a>Možnosti EDITBIN

Editbin – můžete použít k úpravě souborů objektů, spustitelných souborů a dynamické knihovny (DLL). Možnosti určují změny, které provádí EDITBIN.

Možnost sestává ze specifikátoru možnosti, který je buď pomlčka (-) nebo lomítkem (/), za nímž následuje název možnosti. Názvy možností nelze zkracovat. Některé možnosti přijímají argumenty zadané za dvojtečkou (:). Ve specifikaci možnosti nejsou povoleny mezery ani tabulátory. Jednotlivé specifikace možností lze na příkazovém řádku oddělit jednou nebo více mezerami či tabulátory. Názvy možností a jejich – klíčové slovo argumenty nebo argumenty názvů souborů nejsou malá a velká písmena. Například - bind a/BIND mají stejný význam.

Editbin – obsahuje následující možnosti:

|Možnost|Účel|
|------------|-------------|
|[/ALLOWBIND](../../build/reference/allowbind.md)|Určuje, zda může být vázaný knihovny DLL.|
|[/ALLOWISOLATION](../../build/reference/allowisolation.md)|Určuje knihovnu DLL nebo spustitelného souboru chování při vyhledávání manifestu.|
|[/APPCONTAINER](../../build/reference/appcontainer.md)|Určuje, zda je třeba aplikaci spustit v rámci kontejneru AppContainer – například aplikace pro UPW.|
|[/BIND](../../build/reference/bind.md)|Nastaví adresy pro vstupní body v zadané objekty, abyste urychlili čas zatížení.|
|[/DYNAMICBASE](../../build/reference/dynamicbase.md)|Určuje, zda knihovna DLL nebo spustitelný obraz lze náhodně změnit základ v okamžiku načtení pomocí náhodného generování rozložení prostoru adres (ASLR).|
|[/ ERRORREPORT](../../build/reference/errorreport-editbin-exe.md)|Společnosti Microsoft sestavy s interními chybami.|
|[/HEAP](../../build/reference/heap.md)|Nastaví velikost haldy spustitelné bitové kopie v bajtech.|
|[/HIGHENTROPYVA](../../build/reference/highentropyva.md)|Určuje, zda knihovna DLL nebo spustitelný obraz podporuje vysokou entropie (64-bit) Adresa náhodného generování rozložení prostoru (technologie ASLR).|
|[/INTEGRITYCHECK](../../build/reference/integritycheck.md)|Určuje, jestli se má zkontrolovat digitální podpis v okamžiku načtení.|
|[/LARGEADDRESSAWARE](../../build/reference/largeaddressaware.md)|Určuje, zda objekt podporuje adresy, které jsou větší než dva gigabajty.|
|[/NOLOGO](../../build/reference/nologo-editbin.md)|Potlačí úvodní nápis EDITBIN.|
|[/NXCOMPAT](../../build/reference/nxcompat.md)|Určuje, zda spustitelné bitové kopie je kompatibilní s předcházením spuštění dat Windows.|
|[/REBASE](../../build/reference/rebase.md)|Nastaví bázové adresy pro zadané objekty.|
|[/RELEASE](../../build/reference/release.md)|Nastaví kontrolní součet v hlavičce.|
|[/ SECTION](../../build/reference/section-editbin.md)|Obejde atributy oddílu.|
|[/STACK](../../build/reference/stack.md)|Nastaví velikost zásobníku spustitelné bitové kopie v bajtech.|
|[/SUBSYSTEM](../../build/reference/subsystem.md)|Určuje prostředí spuštění.|
|[/SWAPRUN](../../build/reference/swaprun.md)|Určuje, že spustitelné bitové kopie musí být zkopírován do odkládacího souboru a pak spusťte z něj.|
|[/TSAWARE](../../build/reference/tsaware.md)|Určuje, že aplikace je navržen pro spouštění v prostředí s více uživateli.|
|[/VERSION](../../build/reference/version.md)|Nastaví číslo verze v záhlaví.|

## <a name="see-also"></a>Viz také:

[Nástroje sestavení C/C++](../../build/reference/c-cpp-build-tools.md)<br/>
[EDITBIN – referenční dokumentace](../../build/reference/editbin-reference.md)
