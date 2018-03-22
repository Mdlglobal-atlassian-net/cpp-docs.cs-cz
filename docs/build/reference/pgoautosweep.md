---
title: PgoAutoSweep | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
f1_keywords:
- PgoAutoSweep
- PogoAutoSweepA
- PogoAutoSweepW
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6b26eb95552594733fa0849c0df114676dc7a222
ms.sourcegitcommit: ee7d74683af7631441c8c7f65ef5ceceaee4a5ee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="pgoautosweep"></a>PgoAutoSweep

`PgoAutoSweep` Uloží aktuální informace z čítače profilu do souboru a poté obnoví počítadla. Pomocí funkce během optimalizace na základě profilu školení k zápisu všechna data profilu z spuštěným programem do souboru .pgc pro pozdější použití v optimalizace sestavení.

## <a name="syntax"></a>Syntaxe

```cpp
void PgoAutoSweep(const char* name);    // ANSI/MBCS
void PgoAutoSweep(const wchar_t* name); // UNICODE
```

### <a name="parameters"></a>Parametry

*name*<br/>
Identifikační řetězec uložený .pgc souboru.

## <a name="remarks"></a>Poznámky

Můžete volat `PgoAutoSweep` z vaší aplikace pro uložení a obnovit data profilu kdykoli během provádění aplikací. Instrumentované sestavení `PgoAutoSweep` zaznamená aktuální data profilování, uloží ho do souboru a obnoví čítače profilu. Jedná se o ekvivalent volání [pgosweep –](pgosweep.md) příkazu v určitém ve vašem spustitelný soubor. V optimalizovaného sestavení `PgoAutoSweep` je žádná operace.

Data čítače uloženého profilu je umístěn v souboru s názvem *base_name*-*název*! *Hodnota*.pgc, kde *base_name* je základní název spustitelného souboru, *název* parametr předaný `PgoAutoSweep`, a *hodnotu* je jedinečná hodnota, obvykle monotónně se zvyšující číslo, aby se zabránilo kolize názvů souborů.

Vytvořené soubory .pgc `PgoAutoSweep` je potřeba sloučit do .pgd soubor, který chcete použít k vytvoření optimalizované spustitelný soubor. Můžete použít [pgomgr –](pgomgr.md) příkaz k provedení sloučení.

Můžete předat název souboru sloučené .pgd do linkeru během optimalizace sestavení pomocí **PGD =**_filename_ argument [/USEPROFILE](useprofile.md) – možnost linkeru, nebo pomocí nepoužívané **/PGD** – možnost linkeru. Pokud slučte .pgc soubory do souboru s názvem *base_name*.pgd, není nutné zadat název souboru na příkazovém řádku, protože linkeru převezme tento název souboru ve výchozím nastavení.

`PgoAutoSweep` Funkce uchovává nastavení zabezpečení vlákna zadat, když je vytvořena instrumentovaného sestavení. Pokud používáte výchozí nastavení nebo zadejte **NOEXACT** argument [/GENPROFILE nebo /FASTGENPROFILE]() – možnost linkeru, volání `PgoAutoSweep` nejsou bezpečné pro přístup z více vláken. **EXACT** argument vytvoří vláken a přesnější, ale pomalejší, instrumentovaného spustitelný soubor.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`PgoAutoSweep`|\<pgobootrun.h>|

Spustitelný soubor musí obsahovat soubor pgobootrun.lib v propojených knihoven. Tento soubor je součástí instalace Visual Studia, v adresáři VC knihovny pro každou podporovanou architekturu.

## <a name="example"></a>Příklad

V příkladu níže používá `PgoAutoSweep` vytvořte dvě. PGC soubory v různých okamžicích během provádění. První obsahuje data, která popisuje modul runtime chování až `count` rovná 3, a druhá obsahuje data shromážděná od tohoto okamžiku dokud těsně před ukončení aplikace.

```cpp
// pgoautosweep.cpp
// Compile by using: cl /c /GL /W4 /EHsc /O2 pgoautosweep.cpp
// Link to instrument: link /LTCG /genprofile pgobootrun.lib pgoautosweep.obj
// Run to generate data: pgoautosweep
// Merge data by using command line pgomgr tool:
// pgomgr /merge pgoautosweep-func1!1.pgc pgoautosweep-func2!1.pgc pgoautosweep.pgd
// Link to optimize: link /LTCG /useprofile pgobootrun.lib pgoautosweep.obj

#include <iostream>
#include <windows.h>
#include <pgobootrun.h>

void func2(int count)
{
    std::cout << "hello from func2 " << count << std::endl;
    Sleep(2000);
}

void func1(int count)
{
    std::cout << "hello from func1 " << count << std::endl;
    Sleep(2000);
}

int main()
{
    int count = 10;
    while (count--)
    {
        if (count < 3)
            func2(count);
        else
        {
            func1(count);
            if (count == 3)
            {
                PgoAutoSweep("func1");
            }
        }
    }
    PgoAutoSweep("func2");
}
```

V příkazovém řádku vývojáře zkompilujte kód do souboru objektu pomocí tohoto příkazu:

`cl /c /GL /W4 /EHsc /O2 pgoautosweep.cpp`

Potom generujte instrumentovaného sestavení pro školení pomocí tohoto příkazu:

`link /LTCG /genprofile pgobootrun.lib pgoautosweep.obj`

Spuštění instrumentovaného spustitelného souboru k zaznamenání dat školení. Výstupní data ve volání `PgoAutoSweep` je uložené v souborech s názvem pgoautosweep func1! 1.pgc a pgoautosweep func2! 1.pgc. Výstup programu by měl vypadat přibližně takto při jeho spuštění:

```Output
hello from func1 9
hello from func1 8
hello from func1 7
hello from func1 6
hello from func1 5
hello from func1 4
hello from func1 3
hello from func2 2
hello from func2 1
hello from func2 0
```

Sloučení uložená data do databáze školení profil spuštěním **pgomgr –** příkaz:

`pgoautosweep-func1!1.pgc pgoautosweep-func2!1.pgc`

Výstup tohoto příkazu vypadá přibližně takto:

```Output
Microsoft (R) Profile Guided Optimization Manager 14.13.26128.0
Copyright (C) Microsoft Corporation. All rights reserved.

Merging pgoautosweep-func1!1.pgc
pgoautosweep-func1!1.pgc: Used  3.8% (22304 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
Merging pgoautosweep-func2!1.pgc
pgoautosweep-func2!1.pgc: Used  3.8% (22424 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
```

Nyní můžete toto Cvičná data pro generování optimalizovaného sestavení. K vytvoření optimalizované spustitelný soubor, použijte tento příkaz:

`link /LTCG /useprofile pgobootrun.lib pgoautosweep.obj`

```Output
Microsoft (R) Incremental Linker Version 14.13.26128.0
Copyright (C) Microsoft Corporation.  All rights reserved.

Merging pgoautosweep!1.pgc
pgoautosweep!1.pgc: Used  3.9% (22904 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
  Reading PGD file 1: pgoautosweep.pgd
Generating code

0 of 0 ( 0.0%) original invalid call sites were matched.
0 new call sites were added.
294 of 294 (100.00%) profiled functions will be compiled for speed
348 of 1239 inline instances were from dead/cold paths
294 of 294 functions (100.0%) were optimized using profile data
16870 of 16870 instructions (100.0%) were optimized using profile data
Finished generating code
```

## <a name="see-also"></a>Viz také

[Optimalizace na základě profilu](profile-guided-optimizations.md)<br/>
[pgosweep](pgosweep.md)<br/>
