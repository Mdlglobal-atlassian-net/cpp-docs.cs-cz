---
title: Proměnné prostředí pro optimalizace na základě profilu
ms.date: 03/14/2018
helpviewer_keywords:
- profile-guided optimizations, environment variables
ms.assetid: f95a6d1e-49a4-4802-a144-092026b600a3
ms.openlocfilehash: 099e57f1ac69223adafe7bec1af4cc3452915e86
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195263"
---
# <a name="environment-variables-for-profile-guided-optimizations"></a>Proměnné prostředí pro optimalizace na základě profilu

Existují tři proměnné prostředí, které mají vliv na testovací scénáře v imagi vytvořené pomocí **/LTCG: CHZO** pro optimalizace na základě profilu:

- **PogoSafeMode** určuje, zda má být pro profilaci aplikace použit rychlý režim nebo nouzový režim.

- **VCPROFILE_ALLOC_SCALE** přidá další paměť pro použití v profileru.

- **VCPROFILE_PATH** umožňuje zadat složku, která se používá pro soubory. pgc.

**Proměnné prostředí PogoSafeMode a VCPROFILE_ALLOC_SCALE jsou od začátku v aplikaci Visual Studio 2015 zastaralé.** Možnosti linkeru [/GENPROFILE nebo/FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md) a [/USEPROFILE](reference/useprofile.md) určují stejné chování linkeru jako tyto proměnné prostředí.

## <a name="pogosafemode"></a>PogoSafeMode

Tato proměnná prostředí je zastaralá. K řízení tohoto chování použijte **přesné** nebo **nepřesné** argumenty **/GENPROFILE** nebo **/FASTGENPROFILE** .

Zaškrtnutím nebo nastavením proměnné prostředí **PogoSafeMode** určete, jestli se má pro profilaci aplikace v systémech x86 použít rychlý režim nebo nouzový režim.

Optimalizace na základě profilu (PGO) má dva možné režimy během fáze profilace: *rychlý režim* a *bezpečný režim*. Když je profilace v rychlém režimu, používá ke zvýšení počtu čítačů dat instrukci **Inc** . Instrukce **Inc** je rychlejší, ale není bezpečná pro přístup z více vláken. Když je profilace v bezpečném režimu, nástroj použije instrukci **Lock Inc** ke zvýšení počtu čítačů dat. Instrukce **Lock Inc** má stejné funkce jako instrukce **Inc** a je bezpečná pro přístup z více vláken, ale je pomalejší než instrukce **Inc** .

Ve výchozím nastavení funguje profilace PGO v rychlém režimu. **PogoSafeMode** se vyžaduje jenom v případě, že chcete použít nouzový režim.

Chcete-li spustit profilování PGO v bezpečném režimu, je nutné buď použít proměnnou prostředí **PogoSafeMode** nebo přepínač linker **/PogoSafeMode**v závislosti na systému. Provádíte-li profilování v počítači x64, je nutné použít přepínač linkeru. Pokud provádíte profilaci v počítači x86, můžete použít přepínač linkeru nebo nastavit proměnnou prostředí **PogoSafeMode** na libovolnou hodnotu před zahájením procesu optimalizace.

### <a name="pogosafemode-syntax"></a>Syntaxe PogoSafeMode

> **Nastavení PogoSafeMode**[**=**_hodnota_]

Nastavte **PogoSafeMode** na libovolnou hodnotu pro povolení bezpečného režimu. Nastavte bez hodnoty, aby se vymazala předchozí hodnota, a znovu povolte rychlý režim.

## <a name="vcprofile_alloc_scale"></a>VCPROFILE_ALLOC_SCALE

Tato proměnná prostředí je zastaralá. Pro řízení tohoto chování použijte argumenty **MEMMIN** a **MEMMAX** k **/GENPROFILE** nebo **/FASTGENPROFILE** .

Upravte proměnnou prostředí **VCPROFILE_ALLOC_SCALE** pro změnu množství paměti přidělené pro uložení dat profilu. Ve výjimečných případech nebude k dispozici dostatek paměti pro podporu shromažďování dat profilu při spouštění testovacích scénářů. V těchto případech můžete zvýšit množství paměti nastavením **VCPROFILE_ALLOC_SCALE**. Pokud se během testovacího běhu zobrazí chybová zpráva s informacemi o tom, že máte nedostatek paměti, přiřaďte k **VCPROFILE_ALLOC_SCALE**větší hodnotu, dokud se test nedokončí bez chyb typu nedostatek paměti.

### <a name="vcprofile_alloc_scale-syntax"></a>VCPROFILE_ALLOC_SCALE syntaxe

> **Nastavení VCPROFILE_ALLOC_SCALE**[__=__*scale_value*]

Parametr *scale_value* je faktor škálování pro velikost paměti, kterou chcete používat při spouštění testovacích scénářů.  Výchozí hodnota je 1. Tento příkazový řádek například nastaví faktor škálování na 2:

`set VCPROFILE_ALLOC_SCALE=2`

## <a name="vcprofile_path"></a>VCPROFILE_PATH

K určení adresáře pro vytváření souborů. pgc použijte proměnnou prostředí **VCPROFILE_PATH** . Ve výchozím nastavení se soubory. pgc vytvoří ve stejném adresáři jako binární soubor. Pokud však absolutní cesta k binárnímu souboru neexistuje, protože se jedná o případ, kdy spouštíte scénáře profilu na jiném počítači, ze kterého byl vytvořen binární soubor, můžete nastavit **VCPROFILE_PATH** na cestu, která existuje v cílovém počítači.

### <a name="vcprofile_path-syntax"></a>VCPROFILE_PATH syntaxe

> **Nastavení VCPROFILE_PATH**[**=**_cesta_]

Nastavte parametr *path* na cestu k adresáři, do kterého chcete přidat soubory. pgc. Například Tento příkazový řádek nastaví složku na C:\profile:

`set VCPROFILE_PATH=c:\profile`

## <a name="see-also"></a>Viz také

[Optimalizace na základě profilu](profile-guided-optimizations.md)<br/>
[/GENPROFILE a/FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/USEPROFILE](reference/useprofile.md)<br/>
