---
title: PgoAutoSweep
ms.date: 07/02/2019
f1_keywords:
- PgoAutoSweep
- PogoAutoSweepA
- PogoAutoSweepW
ms.openlocfilehash: 57bcd1b2e9f0a3312867c4373fd1e50bcf91576e
ms.sourcegitcommit: 9b904e490b1e262293a602bd1291a8f3045e755b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2019
ms.locfileid: "67552245"
---
# <a name="pgoautosweep"></a>PgoAutoSweep

`PgoAutoSweep`uloží informace o čítačích aktuálního profilu do souboru a pak obnoví čítače. Použijte funkci během školení na základě profilu na základě profilu k zápisu všech dat profilů z běžícího programu do `.pgc` souboru pro pozdější použití v sestavení optimalizace.

## <a name="syntax"></a>Syntaxe

```cpp
void PgoAutoSweep(const char* name);    // ANSI/MBCS
void PgoAutoSweep(const wchar_t* name); // UNICODE
```

### <a name="parameters"></a>Parametry

*Jméno*<br/>
Identifikační řetězec pro uložený `.pgc` soubor.

## <a name="remarks"></a>Poznámky

Můžete zavolat `PgoAutoSweep` z vaší aplikace pro uložení a resetování dat profilu v jakémkoli okamžiku při provádění aplikace. V instrumentované sestavení `PgoAutoSweep` zachycuje aktuální data profilace, uloží je do souboru a obnoví čítače profilů. Je ekvivalentem volání příkazu [pgosweep](pgosweep.md) v určitém místě ve spustitelném souboru. V optimalizovaném sestavení `PgoAutoSweep` je no-op.

Data čítače uložených profilů jsou umístěna v souboru s názvem *base_name*-*název*. *Value*. pgc, kde *base_name* je základní název spustitelného souboru, *název* je parametr předaný do `PgoAutoSweep`a *hodnota* je jedinečná hodnota, obvykle rovnoměrně zvětšující rostoucí číslo, aby se zabránilo kolizi názvů souborů.

`.pgc` Soubory vytvořené pomocí `PgoAutoSweep` musí být sloučeny do `.pgd` souboru, který se použije k vytvoření optimalizovaného spustitelného souboru. K provedení sloučení můžete použít příkaz [pgomgr](pgomgr.md) .

`.pgd` Název sloučeného souboru můžete předat linkeru během sestavení optimalizace pomocí argumentu **PGD =**_filename_ pro možnost linkeru [/USEPROFILE](reference/useprofile.md) nebo pomocí možnosti linkeru nepoužívaného **/PGD** . Pokud `.pgc` soubory sloučíte do souboru s názvem *base_name*. PGD, nemusíte zadávat název souboru do příkazového řádku, protože linker ve výchozím nastavení vybere tento název souboru.

`PgoAutoSweep` Funkce udržuje nastavení pro zabezpečení vlákna zadané při vytváření instrumentované sestavení. Pokud použijete výchozí nastavení nebo zadáte argument **NEpřesný** parametr linkeru [/GENPROFILE nebo/FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md) , volání `PgoAutoSweep` nejsou bezpečná pro přístup z více vláken. **Přesný** argument vytvoří bezpečný a přesnější přístup z více vláken, ale pomalejší, instrumentované spustitelné soubory.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`PgoAutoSweep`|\<pgobootrun. h>|

Spustitelný soubor musí obsahovat soubor pgobootrun. lib v propojených knihovnách. Tento soubor je součástí instalace sady Visual Studio, v adresáři knihoven VC pro každou podporovanou architekturu.

## <a name="example"></a>Příklad

Následující příklad používá `PgoAutoSweep` k vytvoření dvou `.pgc` souborů na různých místech během provádění. První obsahuje data, která popisují chování modulu runtime, `count` dokud se nerovná 3 a druhá obsahuje data shromážděná po tomto okamžiku, dokud neproběhne před ukončením aplikace.

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

Do příkazového řádku pro vývojáře zkompilujte kód do souboru objektu pomocí tohoto příkazu:

`cl /c /GL /W4 /EHsc /O2 pgoautosweep.cpp`

Pak vygenerujte instrumentované sestavení pro školení pomocí tohoto příkazu:

`link /LTCG /genprofile pgobootrun.lib pgoautosweep.obj`

Spusťte instrumentované spustitelné soubory, abyste mohli zachytit školicí data. Výstup dat voláním do `PgoAutoSweep` je uložen v souborech s názvem pgoautosweep-func1! 1. pgc a pgoautosweep-func2! 1. pgc. Výstup programu by měl vypadat jako při spuštění:

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

Uložte uložená data do databáze školení k profilům spuštěním příkazu **pgomgr** :

`pgoautosweep-func1!1.pgc pgoautosweep-func2!1.pgc`

Výstup tohoto příkazu vypadá nějak takto:

```Output
Microsoft (R) Profile Guided Optimization Manager 14.13.26128.0
Copyright (C) Microsoft Corporation. All rights reserved.

Merging pgoautosweep-func1!1.pgc
pgoautosweep-func1!1.pgc: Used  3.8% (22304 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
Merging pgoautosweep-func2!1.pgc
pgoautosweep-func2!1.pgc: Used  3.8% (22424 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
```

Nyní můžete pomocí těchto školicích dat vygenerovat optimalizované sestavení. Tento příkaz slouží k sestavení optimalizovaného spustitelného souboru:

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
