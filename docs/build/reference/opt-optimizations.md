---
title: / OPT (optimalizace) | Microsoft Docs
ms.custom: ''
ms.date: 05/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.OptimizeReferences
- /opt
- VC.Project.VCLinkerTool.OptimizeForWindows98
- VC.Project.VCLinkerTool.EnableCOMDATFolding
- VC.Project.VCLinkerTool.OptimizeFolding
- VC.Project.VCLinkerTool.FoldingIterations
- VC.Project.VCLinkerTool.OptimizeFoldingIterations
dev_langs:
- C++
helpviewer_keywords:
- LINK tool [C++], controlling optimizations
- -OPT linker option
- linker [C++], optimizations
- OPT linker option
- optimization, linker
- /OPT linker option
ms.assetid: 8f229863-5f53-48a8-9478-243a647093ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc9f7f66b9bd0ee2c0da65d17eac33e1cbc8c316
ms.sourcegitcommit: da7b7533d1a4dc141cc0f09149e4e4196f2fe329
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2018
ms.locfileid: "34463102"
---
# <a name="opt-optimizations"></a>/OPT (optimalizace)

Řídí optimalizace, které program LINK provádí během sestavování.

## <a name="syntax"></a>Syntaxe

> **/ OPT:**{**REF** | **NOREF**}<br/>
> **/ OPT:**{**bránou Firewall**[**=**_iterací_] | **NOICF**}<br/>
> **/ OPT:**{**LBR** | **NOLBR**}

## <a name="arguments"></a>Arguments

**REF** &AMP;#124; **NOREF**

**/OPT:REF** eliminuje funkce a data, která se nikdy odkazuje; **/OPT:NOREF** zajišťuje funkce a data, která se nikdy odkazuje.

Pokud je povoleno /OPT:REF, odebere odkaz neregistrované zabalené funkce a data, označuje jako *COMDATs*. Tato optimalizace se označuje jako přechodné odstranění sekvence COMDAT. **/OPT:REF** možnost také zakáže přírůstkové propojování.

Vložená funkce a členské funkce definované uvnitř deklaraci třídy jsou vždy COMDATs. Všechny funkce v souboru objektu probíhají do COMDATs, pokud je kompilován s použitím [/Gy](../../build/reference/gy-enable-function-level-linking.md) možnost. Umístit **const** data v COMDATs, je potřeba deklarovat ho pomocí `__declspec(selectany)`. Informace o tom, jak zadejte data pro odebrání nebo skládání najdete v tématu [selectany](../../cpp/selectany.md).

Ve výchozím nastavení **/OPT:REF** ve linkeru je povolena, pokud **/OPT:NOREF** nebo [/DEBUG](../../build/reference/debug-generate-debug-info.md) je zadán. Chcete-li přepsat toto výchozí nastavení a zachovat neregistrované COMDATs v programu, zadejte **/OPT:NOREF**. Můžete použít [/INCLUDE](../../build/reference/include-force-symbol-references.md) možnost přepsání odebrání konkrétní symbolu.

Pokud [/DEBUG](../../build/reference/debug-generate-debug-info.md) je zadána výchozí hodnota pro **/OPT** je **NOREF**, a všechny funkce, které budou zachovány v bitové kopii. Chcete-li přepsat toto výchozí nastavení a optimalizace sestavení ladicí verze, zadejte **/OPT:REF**. To může snížit velikost vašeho spustitelný soubor a může být že užitečné optimalizace i v ladění sestavení. Doporučujeme, aby také určit **/OPT:NOICF** se zachovat stejné funkce ladění sestavení. Usnadníte tím čtení trasování zásobníku a nastavení zarážek ve funkcích, které by jinak byly složeny dohromady.

**Bránou Firewall**\[**=**_iterací_] &#124; **NOICF**

Použití **bránou Firewall**\[**=**_iterací_] k provedení identické sekvence COMDAT skládání. Redundantní sekvence COMDAT lze odebrat z výstupu linkeru. Volitelné *iterací* parametr určuje počet pokusů procházení symboly pro duplicitní položky. Výchozí počet opakování je 1. Při dalších iteracích se mohou najít další duplicity, které se odhalí skládáním při předchozí iteraci.

Ve výchozím nastavení **/OPT:ICF** ve linkeru je povolena, pokud **/OPT:NOICF** nebo [/DEBUG](../../build/reference/debug-generate-debug-info.md) je zadán. Chcete-li přepsat toto výchozí nastavení a zabránit COMDATs se přeloží do programu, zadejte **/OPT:NOICF**.

V sestavení ladicí verze, je nutné explicitně zadat **/OPT:ICF** povolit sekvence COMDAT skládání. Ale protože **/OPT:ICF** můžete sloučit stejné údaje nebo funkce, ho můžete změnit názvy funkcí, které se zobrazují v trasování zásobníku. Můžete také znemožňují nastavte zarážky v určité funkce a zkontrolujte některá data v ladicím programu a může trvat do neočekávané funkce když jste krokování prostřednictvím kódu. Chování kód je stejné, ale prezentace ladicí program může být velmi matoucí. Proto nedoporučujeme používat **/OPT:ICF** ladění sestavení Pokud výhody menší kódu převáží nad tyto nevýhody.

> [!NOTE]
> Protože **/OPT:ICF** může způsobit stejnou adresu pro přiřazení k různým funkcím nebo jen pro čtení datové členy (tedy **const** proměnné při kompilaci pomocí **/Gy**), je možné přerušit programu, který závisí na jedinečných adres pro funkce nebo jen pro čtení datové členy. Další informace najdete v tématu [/Gy (povolení propojení na úrovni funkcí)](../../build/reference/gy-enable-function-level-linking.md).

**LBR** &AMP;#124; **NOLBR**

**/OPT:LBR** a **/OPT:NOLBR** možnosti platí pouze pro binární soubory ARM. Protože některé větvicí instrukce procesoru ARM mají omezený rozsah, pokud linker zjistí skok na adresu mimo rozsah, nahradí cílovou adresu této větvicí instrukce adresou „ostrůvku“ kódu, jenž obsahuje větvicí instrukci, která míří na skutečné místo určení. Můžete použít **/OPT:LBR** k optimalizaci detekce dlouho větve pokyny a umístění zprostředkující kód ostrovy minimalizovat celkové velikosti kódu. **/OPT:NOLBR** dá pokyn linkeru ke generování kódu ostrovy dlouho větve pokyny, jak se vyskytují, bez optimalizace.

Ve výchozím nastavení **/OPT:LBR** je možnost nastavena, když přírůstkové propojování není povoleno. Pokud chcete nepřírůstkové odkaz, ale není optimalizace dlouho větve, zadejte **/OPT:NOLBR**. **/OPT:LBR** možnost zakáže přírůstkové propojování.

## <a name="remarks"></a>Poznámky

Pokud se používá v příkazovém řádku, linkeru výchozí **/OPT:REF, bránou Firewall, LBR**. Pokud **/DEBUG** je zadána výchozí hodnota je **/OPT:NOREF, NOICR, NOLBR**.

**/OPT** optimalizace obecně zmenšit velikost bitové kopie a zvýšit rychlost programu. Tato vylepšení může být výrazně větší aplikace, proto jsou povolené ve výchozím nastavení pro prodejní sestavení.

Optimalizace linkeru předem trvat delší dobu, ale optimalizovaný kód také šetří čas, kdy linkeru má méně relocations opravit a vytvoří menší finální image a ukládá i delší dobu, kdy má méně ladicí informace o zpracování a zápis do PDB. Pokud je povolená optimalizace, může být rychlejší odkaz celkově platí, protože malé náklady analýzou může být více než posunut době úspory v linkeru předá přes menší binární soubory.

**/OPT** argumenty může být určen společně, oddělených čárkami. Například místo z **/OPT:REF /OPT:NOICF**, můžete zadat **/OPT:REF, NOICF**.

Můžete použít [/VERBOSE](../../build/reference/verbose-print-progress-messages.md) – možnost linkeru zobrazit funkce, které jsou odebrány podle **/OPT:REF** a funkce, které jsou přeloženy podle **/OPT:ICF**.

**/OPT** jsou často nastaveny argumenty pro projekty vytvořené pomocí **nový projekt** dialogové okno v prostředí Visual Studio IDE, a obvykle mají různé hodnoty pro ladění a konfigurace verze. Pokud není nastavena žádná hodnota pro tyto možnosti linkeru ve vašem projektu, může získat projektu výchozí hodnoty, které může být jiný než výchozí hodnoty používané linkeru na příkazovém řádku.

### <a name="to-set-the-opticf-or-optref-linker-option-in-the-visual-studio-development-environment"></a>Nastavení parametru linkeru OPT:ICF nebo OPT:REF ve vývojovém prostředí sady Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **optimalizace** stránku vlastností.

1. Změňte některou z těchto vlastností:

   - **Povolit sekvence COMDAT skládání**

   - **Odkazy**

### <a name="to-set-the-optlbr-linker-option-in-the-visual-studio-development-environment"></a>Nastavení parametru linkeru OPT:LBR ve vývojovém prostředí sady Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **příkazového řádku** stránku vlastností.

1. Zadejte možnost v **další možnosti**:

   `/opt:lbr` Nebo `/opt:nolbr`

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableCOMDATFolding%2A> a <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OptimizeReferences%2A> vlastnosti.

## <a name="see-also"></a>Viz také

- [Nastavení možností linkeru](../../build/reference/setting-linker-options.md)
- [Možnosti linkeru](../../build/reference/linker-options.md)
