---
title: Proměnné prostředí pro optimalizace na základě profilu
ms.date: 03/14/2018
helpviewer_keywords:
- profile-guided optimizations, environment variables
ms.assetid: f95a6d1e-49a4-4802-a144-092026b600a3
ms.openlocfilehash: 2d69019f01a59f170aeeee22ef10b1af0de07a68
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595660"
---
# <a name="environment-variables-for-profile-guided-optimizations"></a>Proměnné prostředí pro optimalizace na základě profilu

Existují tři proměnné prostředí, které mají vliv na image vytvořené pomocí testovacích scénářů **/LTCG:PGI** pro optimalizace na základě profilu:

- **PogoSafeMode** Určuje, jestli se má použít pro vytvoření profilu aplikace rychlého režimu nebo nouzového režimu.

- **Vcprofile_alloc_scale –** přidává další paměť pro použití pomocí profileru.

- **Vcprofile_path –** vám umožní zadat složku pro soubory .pgc.

**Proměnné prostředí PogoSafeMode a vcprofile_alloc_scale – jsou zastaralé od verze Visual Studio 2015.** Možnosti linkeru [/genprofile nebo /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) a [/useprofile](useprofile.md) zadat stejné chování linkeru jako tyto proměnné prostředí.

## <a name="pogosafemode"></a>PogoSafeMode

Tato proměnná prostředí je zastaralá. Použití **EXACT** nebo **NOEXACT** argumenty **/genprofile** nebo **/FASTGENPROFILE** řízení tohoto chování.

Vymazat nebo nastavit **PogoSafeMode** proměnnou prostředí k určení, jestli se má použít pro vytvoření profilu aplikace na x86 rychlého režimu nebo nouzového režimu systémy.

Profilově řízené optimalizace (PGO) má během fáze vytváření profilů dva možné režimy: *rychlém režimu* a *Nouzový režim*. Když je profilování v rychlém režimu, používá **celkové** instrukce ke zvýšení počtu čítačů dat. **Celkové** instrukce je rychlejší, ale není bezpečná pro vlákno. Když je profilování v nouzovém režimu, používá **ZÁMEK celkové** instrukce ke zvýšení počtu čítačů dat. **ZÁMEK celkové** instrukce má stejné funkce jako **celkové** instrukce má a je bezpečná pro vlákno, ale je pomalejší, než **celkové** instrukce.

Ve výchozím nastavení PGO profilování pracuje v rychlém režimu. **PogoSafeMode** je vyžadováno pouze pokud budete chtít použít nouzový režim.

Pokud chcete spustit profilování PGO v nouzovém režimu, je nutné použít proměnnou prostředí **PogoSafeMode** nebo přepínač linker **/PogoSafeMode**, v závislosti na systému. Pokud provádíte profilaci na x x64 počítače, je potřeba použít přepínač linkeru. Pokud provádíte profilaci na x x86 počítače, můžete použít linkeru přepnout nebo nastavit **PogoSafeMode** proměnné prostředí na libovolnou hodnotu před zahájením procesu optimalizace.

### <a name="pogosafemode-syntax"></a>Syntaxe PogoSafeMode

> **Nastavte PogoSafeMode**[**=**_hodnotu_]

Nastavte **PogoSafeMode** na libovolnou hodnotu Povolit Nouzový režim. Nastavit bez hodnoty a smažte předchozí hodnotu a znovu povolit rychlém režimu.

## <a name="vcprofileallocscale"></a>VCPROFILE_ALLOC_SCALE

Tato proměnná prostředí je zastaralá. Použití **MEMMIN** a **MEMMAX** argumenty **/genprofile** nebo **/FASTGENPROFILE** řízení tohoto chování.

Upravit **vcprofile_alloc_scale –** proměnné prostředí, chcete-li změnit velikost paměti přidělené pro uchovávání dat profilu. Ve výjimečných případech nebude k dispozici pro podporu dostatek paměti při spuštění testu scénáře shromažďování dat profilu. V takových případech můžete zvýšit množství paměti tak, že nastavíte **vcprofile_alloc_scale –**. Pokud se zobrazí chybová zpráva během testovacího běhu, který označuje, že máte dostatek paměti, přiřadit větší hodnotu **vcprofile_alloc_scale –**, dokud se test nespustí dokončena bez chyb na více instancí z důvodu nedostatku paměti.

### <a name="vcprofileallocscale-syntax"></a>Vcprofile_alloc_scale – syntaxe

> **Nastavte vcprofile_alloc_scale –**[__=__*scale_value*]

*Scale_value* parametr je měřítko velikost paměti, které chcete použít pro spuštění testovacích scénářů.  Výchozí hodnota je 1. Třeba tento příkaz nastaví měřítko na 2:

`set VCPROFILE_ALLOC_SCALE=2`

## <a name="vcprofilepath"></a>VCPROFILE_PATH

Použití **vcprofile_path –** proměnnou prostředí k určení adresář, který chcete vytvořit soubory .pgc. Ve výchozím nastavení jsou soubory .pgc vytvoří ve stejném adresáři jako binární právě profilována. Nicméně, pokud se absolutní cesta binární soubor neexistuje, jak může být případ, kdy spustit scénáře profilu na jiném počítači než ve kterém byla vytvořena binární soubor, můžete nastavit **vcprofile_path –** na cestu, která existuje v cílovém počítači.

### <a name="vcprofilepath-syntax"></a>Vcprofile_path – syntaxe

> **Nastavte vcprofile_path –**[**=**_cesta_]

Nastavte *cesta* parametr cestu k adresáři, do kterého chcete přidat soubory .pgc. Třeba tento příkaz nastaví složku C:\profile:

`set VCPROFILE_PATH=c:\profile`

## <a name="see-also"></a>Viz také:

[Optimalizace na základě profilu](../../build/reference/profile-guided-optimizations.md)<br/>
[/ GENPROFILE a /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/USEPROFILE](useprofile.md)<br/>
