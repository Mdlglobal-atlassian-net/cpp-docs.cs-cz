---
title: – Možnosti nástroje EDITBIN | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- editbin
dev_langs:
- C++
helpviewer_keywords:
- EDITBIN program, options
ms.assetid: 2da9f88e-cbab-4d64-bb66-ef700535230f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1922e410b0151337ce403e24d20ae90b7e964cd5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="editbin-options"></a>Možnosti EDITBIN
Editbin – slouží k úpravě objektu soubory, spustitelné soubory a dynamické knihovny (DLL). Zadejte možnosti změny, které provádí nástroje EDITBIN.  
  
 Možnost se skládá z specifikátor možnosti, která je pomlčkou (-) nebo lomítkem (/), za nímž následuje název možnosti. Názvy možností nelze zkracovat. Některé možnosti trvat argumenty, které jsou zadány po dvojtečkou (:). Ve specifikaci možnosti nejsou povoleny mezery ani tabulátory. Jednotlivé specifikace možností lze na příkazovém řádku oddělit jednou nebo více mezerami či tabulátory. Názvy možností a jejich argumentů – klíčové slovo nebo argumenty název souboru nejsou malá a velká písmena. Například - vazby a/BIND mají stejný význam.  
  
 Editbin – obsahuje následující možnosti:  
  
|Možnost|Účel|  
|------------|-------------|  
|[/ALLOWBIND](../../build/reference/allowbind.md)|Určuje, zda mohou být vázány knihovny DLL.|  
|[/ALLOWISOLATION](../../build/reference/allowisolation.md)|Určuje knihovny DLL nebo spustitelný soubor manifestu vyhledávání chování.|  
|[/APPCONTAINER](../../build/reference/appcontainer.md)|Určuje, zda aplikace musíte spustit v rámci AppContainer – například aplikace UPW.|  
|[/BIND](../../build/reference/bind.md)|Nastaví adresy pro vstupní body v zadané objekty, které se doba načítání rychlost.|  
|[/DYNAMICBASE](../../build/reference/dynamicbase.md)|Určuje, zda knihovnu DLL nebo spustitelné bitové kopie může být náhodně rebased během zatížení pomocí adres místo rozložení náhodné (technologie ASLR).|  
|[/ ERRORREPORT](../../build/reference/errorreport-editbin-exe.md)|Sestava s interními chybami společnosti Microsoft.|  
|[/HEAP](../../build/reference/heap.md)|Nastaví velikost haldy spustitelné bitové kopie v bajtech.|  
|[/HIGHENTROPYVA](../../build/reference/highentropyva.md)|Určuje, zda knihovnu DLL nebo spustitelné bitové kopie podporuje vysokou entropie (64 bitů) adresu místa rozložení náhodné (technologie ASLR).|  
|[/INTEGRITYCHECK](../../build/reference/integritycheck.md)|Určuje, jestli při načítání, zkontrolujte digitální podpis.|  
|[/LARGEADDRESSAWARE](../../build/reference/largeaddressaware.md)|Určuje, zda objekt podporuje adresy, které jsou větší než dva gigabajty.|  
|[/NOLOGO](../../build/reference/nologo-editbin.md)|Potlačí úvodní nápis nástroje EDITBIN.|  
|[/NXCOMPAT](../../build/reference/nxcompat.md)|Určuje, jestli je kompatibilní s Windows Zabránění spuštění dat spustitelné bitové kopie.|  
|[/REBASE](../../build/reference/rebase.md)|Nastaví základní adresy pro zadané objekty.|  
|[/RELEASE](../../build/reference/release.md)|Nastaví kontrolního součtu v hlavičce.|  
|[/ SECTION](../../build/reference/section-editbin.md)|Přepíše atributy oddílu.|  
|[/STACK](../../build/reference/stack.md)|Nastaví velikost zásobníku spustitelné bitové kopie v bajtech.|  
|[/SUBSYSTEM](../../build/reference/subsystem.md)|Určuje prostředí pro spuštění.|  
|[/SWAPRUN](../../build/reference/swaprun.md)|Určuje, že spustitelné bitové kopie musí být zkopírován do souboru odkládacího souboru a pak spusťte z.|  
|[/TSAWARE](../../build/reference/tsaware.md)|Určuje, že aplikace je určená ke spuštění v prostředí s více uživateli.|  
|[/VERSION](../../build/reference/version.md)|Nastaví číslo verze v hlavičce.|  
  
## <a name="see-also"></a>Viz také  
 [Nástroje sestavení C/C++](../../build/reference/c-cpp-build-tools.md)   
 [EDITBIN – referenční dokumentace](../../build/reference/editbin-reference.md)