---
title: Proměnné prostředí pro optimalizace na základě profilu | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- profile-guided optimizations, environment variables
ms.assetid: f95a6d1e-49a4-4802-a144-092026b600a3
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 701f0292d9960801139abc698946122718247645
ms.sourcegitcommit: ee7d74683af7631441c8c7f65ef5ceceaee4a5ee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="environment-variables-for-profile-guided-optimizations"></a>Proměnné prostředí pro optimalizace na základě profilu

Existují tři proměnné prostředí, které ovlivňují testovací scénáře na bitovou kopii vytvořené pomocí **/LTCG:PGI** pro optimalizace na základě profilu:

- **PogoSafeMode** Určuje, jestli se má použít rychlého režimu nebo v nouzovém režimu pro profilace aplikací.

- **Vcprofile_alloc_scale –** přidá další paměť pro použití profileru.

- **Vcprofile_path –** umožňuje určit složku pro soubory .pgc.

**Proměnné prostředí PogoSafeMode a vcprofile_alloc_scale – jsou zastaralé od verze sady Visual Studio 2015.** Možnosti linkeru [/GENPROFILE nebo /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) a [/USEPROFILE](useprofile.md) zadejte stejné chování linkeru jako těchto proměnných prostředí.

## <a name="pogosafemode"></a>PogoSafeMode

Tato proměnná prostředí je zastaralý. Použití **EXACT** nebo **NOEXACT** argumenty, které mají **/GENPROFILE** nebo **/FASTGENPROFILE** za účelem řízení.

Vymazat nebo nastavte **PogoSafeMode** proměnnou prostředí a určit, jestli se má použít pro profilace aplikací na x86 rychlého režimu nebo v nouzovém režimu systémy.

Optimalizace na základě profilu (PGO) má dva možné režimy profilování fázi: *rychlého režimu* a *nouzovém režimu*. Při vytváření profilu je v rychlého režimu, použije **INC** instrukce ke zvýšení dat čítače. **INC** instrukce je rychlejší, ale není bezpečné pro přístup z více vláken. Při vytváření profilu je v nouzovém režimu, použije **ZÁMKU INC** instrukce ke zvýšení dat čítače. **INC ZÁMKU** instrukce má stejné funkce jako **INC** instrukce a bezpečné pro přístup z více vláken, ale je nižší než **INC** instrukcí.

Ve výchozím nastavení vytváření profilů PGO funguje v rychlého režimu. **PogoSafeMode** je požadován, pouze pokud budete chtít použít nouzový režim.

Pokud chcete spustit PGO profilace v nouzovém režimu, je nutné použít proměnné prostředí **PogoSafeMode** nebo přepínač linkeru **/PogoSafeMode**, v závislosti na systému. Pokud provádíte profilace na x64 počítače, je potřeba použít přepínač linkeru. Pokud provádíte profilace na x86 počítače, můžete použít linkeru přepínač, nebo nastavte **PogoSafeMode** proměnnou prostředí na jakoukoli hodnotu před zahájením procesu optimalizace.

### <a name="pogosafemode-syntax"></a>Syntaxe PogoSafeMode

> **nastavit PogoSafeMode**[**=**_hodnotu_]

Nastavit **PogoSafeMode** na jakoukoli hodnotu Povolit nouzovém režimu. Nastavit bez hodnoty a vymazat předchozí hodnotu a znovu povolit rychlého režimu.

## <a name="vcprofileallocscale"></a>VCPROFILE_ALLOC_SCALE

Tato proměnná prostředí je zastaralý. Použití **MEMMIN** a **MEMMAX** argumenty, které mají **/GENPROFILE** nebo **/FASTGENPROFILE** za účelem řízení.

Změnit **vcprofile_alloc_scale –** proměnné prostředí, chcete-li změnit množství paměti přidělené pro všechna data profilu. Ve výjimečných případech, nebude dostatek paměti k dispozici pro podporu shromažďování dat profilu při spouštění testovací scénáře. V takových případech můžete zvýšit množství paměti nastavením **vcprofile_alloc_scale –**. Pokud se zobrazí chybová zpráva během spustit test, který označuje, zda máte dostatek paměti, přiřadit hodnotu větší na **vcprofile_alloc_scale –**, dokud se test spustí dokončeno bez chyb z důvodu nedostatku paměti.

### <a name="vcprofileallocscale-syntax"></a>Vcprofile_alloc_scale – syntaxe

> **set VCPROFILE_ALLOC_SCALE**[__=__*scale_value*]

*Scale_value* parametr je měřítko pro velikost paměti, které chcete použít pro spuštění scénáře testování.  Výchozí hodnota je 1. Například tento příkaz nastaví měřítko na 2:

`set VCPROFILE_ALLOC_SCALE=2`

## <a name="vcprofilepath"></a>VCPROFILE_PATH

Použití **vcprofile_path –** adresář, který chcete vytvořit soubory .pgc proměnné prostředí. Ve výchozím nastavení se ve stejném adresáři jako binární profilovaný vytváří soubory .pgc. Ale pokud absolutní cesta binárního souboru neexistuje, jako při spuštění profilu scénáře na jiný počítač, ze které byla vytvořena binárního souboru může být případ, můžete nastavit **vcprofile_path –** na cestu, která existuje v cílovém počítači.

### <a name="vcprofilepath-syntax"></a>Vcprofile_path – syntaxe

> **set VCPROFILE_PATH**[**=**_path_]

Nastavte *cesta* parametr cesta k adresáři, do kterého chcete přidat .pgc soubory. Například tento příkaz nastaví složku C:\profile:

`set VCPROFILE_PATH=c:\profile`

## <a name="see-also"></a>Viz také

[Optimalizace na základě profilu](../../build/reference/profile-guided-optimizations.md)<br/>
[/ GENPROFILE a /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/ USEPROFILE](useprofile.md)<br/>
