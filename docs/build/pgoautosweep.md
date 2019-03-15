---
title: PgoAutoSweep
ms.date: 03/14/2018
f1_keywords:
- PgoAutoSweep
- PogoAutoSweepA
- PogoAutoSweepW
ms.openlocfilehash: 2d9804e5ce90663d44ac389ab4f71d10290e6470
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823175"
---
# <a name="pgoautosweep"></a>PgoAutoSweep

`PgoAutoSweep` Uloží aktuální informace z čítače profilu do souboru a potom obnoví čítače. Použijte funkci během optimalizace na základě profilu školení k zápisu do souboru .pgc pro pozdější použití v sestavení optimalizace na všechna data profilu ze spuštěného programu.

## <a name="syntax"></a>Syntaxe

```cpp
void PgoAutoSweep(const char* name);    // ANSI/MBCS
void PgoAutoSweep(const wchar_t* name); // UNICODE
```

### <a name="parameters"></a>Parametry

*Jméno*<br/>
Identifikační řetězec pro soubor .pgc uložené.

## <a name="remarks"></a>Poznámky

Můžete volat `PgoAutoSweep` z vaší aplikace na Uložit a obnovit data profilu kdykoli během spuštění aplikace. V instrumentovaném buildu `PgoAutoSweep` zaznamená aktuální data o profilování, uloží ho do souboru a obnoví čítače profilu. Jedná se o ekvivalent volání [pgosweep](pgosweep.md) příkaz v konkrétním bodě v spustitelný soubor. V optimalizovaného sestavení `PgoAutoSweep` je no-op.

Data čítače uloženého profilu je umístěn v souboru s názvem *base_name*-*název*! *Hodnota*.pgc, kde *base_name* je základní název spustitelného souboru, *název* je parametr předána `PgoAutoSweep`, a *hodnotu* je jedinečná hodnota, obvykle monotónně se zvyšující číslo, aby se zabránilo kolize názvů souborů.

Soubory .pgc vytvořené `PgoAutoSweep` je potřeba sloučit do souboru .pgd se použije k vytvoření optimalizované spustitelný soubor. Můžete použít [pgomgr](pgomgr.md) příkaz k provedení sloučení.

Můžete předat název souboru sloučeného .pgd linkeru během sestavování optimalizace s použitím **PGD =**_filename_ argument [/useprofile](reference/useprofile.md) – možnost linkeru, nebo pomocí zastaralá **/PGD** – možnost linkeru. Pokud jste soubory .pgc sloučit do souboru s názvem *base_name*.pgd, není potřeba zadat název souboru v příkazovém řádku vzhledem k tomu, že má linker převezme název souboru ve výchozím nastavení.

`PgoAutoSweep` Funkce spravuje nastavení zabezpečení vlákna zadané, když se vytvoří instrumentované sestavení. Pokud používáte výchozí nastavení nebo zadejte **NOEXACT** argument [/genprofile nebo /FASTGENPROFILE]() – možnost linkeru, zavolá do `PgoAutoSweep` nejsou bezpečné pro vlákna. **EXACT** argument vytvoří bezpečné pro vlákna a přesnější, ale pomalejší, instrumentovaný spustitelný soubor.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`PgoAutoSweep`|\<pgobootrun.h>|

Spustitelný soubor musí obsahovat soubor pgobootrun.lib v propojených knihoven. Tento soubor je součástí instalace sady Visual Studio, v adresáři VC knihovny pro každou podporovanou architekturu.

## <a name="example"></a>Příklad

V příkladu níže použití `PgoAutoSweep` vytvořte dvě. PGC soubory v různých fázích během provádění. Obsahuje data, která popisuje chování za běhu až do první `count` rovná 3, a druhá obsahuje data shromážděná za touto pozicí dokud těsně před ukončení aplikace.

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

V příkazovém řádku pro vývojáře zkompiluje kód, který objektový soubor pomocí tohoto příkazu:

`cl /c /GL /W4 /EHsc /O2 pgoautosweep.cpp`

Potom generování instrumentované sestavení pro trénování pomocí tohoto příkazu:

`link /LTCG /genprofile pgobootrun.lib pgoautosweep.obj`

Spustíte instrumentovaný spustitelný soubor k zachycení trénovací data. Výstup dat voláním `PgoAutoSweep` se uloží do souborů s názvem pgoautosweep func1! 1.pgc a pgoautosweep func2! 1.pgc. Výstup programu by měl vypadat takto při jejím spuštění:

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

Sloučit s uloženými daty profilové databáze školení spuštěním **pgomgr** příkaz:

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

Teď můžete použít tento trénovací data pro generování optimalizovaného sestavení. K vytvoření optimalizované spustitelný soubor, použijte tento příkaz:

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

## <a name="see-also"></a>Viz také:

[Optimalizace na základě profilu](profile-guided-optimizations.md)<br/>
[pgosweep](pgosweep.md)<br/>
