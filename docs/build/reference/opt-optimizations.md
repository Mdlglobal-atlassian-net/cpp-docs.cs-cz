---
title: /OPT (optimalizace)
ms.date: 05/18/2018
f1_keywords:
- VC.Project.VCLinkerTool.OptimizeReferences
- /opt
- VC.Project.VCLinkerTool.OptimizeForWindows98
- VC.Project.VCLinkerTool.EnableCOMDATFolding
- VC.Project.VCLinkerTool.OptimizeFolding
- VC.Project.VCLinkerTool.FoldingIterations
- VC.Project.VCLinkerTool.OptimizeFoldingIterations
helpviewer_keywords:
- LINK tool [C++], controlling optimizations
- -OPT linker option
- linker [C++], optimizations
- OPT linker option
- optimization, linker
- /OPT linker option
ms.assetid: 8f229863-5f53-48a8-9478-243a647093ac
ms.openlocfilehash: fb59b861bc46c93a3f5fa1b6c6b8d1b73ddefc66
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818294"
---
# <a name="opt-optimizations"></a>/OPT (optimalizace)

Řídí optimalizace, které program LINK provádí během sestavování.

## <a name="syntax"></a>Syntaxe

> **/ OPT:**{**REF** | **NOREF**}<br/>
> **/OPT:**{**ICF**[**=**_iterations_] | **NOICF**}<br/>
> **/OPT:**{**LBR** | **NOLBR**}

## <a name="arguments"></a>Arguments

**REF** &AMP;#124; **NOREF**

**OPT** odstraní funkce a data, která nejsou nikdy odkazována; **Noref** zachová data, která nejsou nikdy odkazována.

Pokud je povoleno OPT, REF odebere program LINK neodkazované zabalené funkce a data, označované jako *sekvence Comdat*. Tato optimalizace se označuje jako přechodné odstranění sekvence COMDAT. **OPT** také zakáže přírůstkové propojení.

Vložené funkce a členské funkce definované uvnitř deklarace třídy jsou vždy sekvence Comdat. Všechny funkce v souboru objektu probíhají do sekvencí Comdat, pokud je zkompilován s použitím [/Gy](gy-enable-function-level-linking.md) možnost. Umístit **const** data do sekvencí Comdat, musíte ji deklarovat s použitím `__declspec(selectany)`. Informace o tom, jak zadat data pro odebrání nebo skládání naleznete v tématu [selectany](../../cpp/selectany.md).

Ve výchozím nastavení **OPT** je povoleno pomocí linkeru, není-li **noref** nebo [/DEBUG](debug-generate-debug-info.md) je zadán. Chcete-li přepsat toto výchozí nastavení a ponechat v programu neodkazované sekvence Comdat, zadejte **noref**. Můžete použít [/INCLUDE](include-force-symbol-references.md) lze přepsat odebrání určitého symbolu.

Pokud [/DEBUG](debug-generate-debug-info.md) není zadán, výchozí hodnota pro **/OPT** je **NOREF**, a všechny funkce jsou zachovány v obraze. Chcete-li přepsat toto výchozí nastavení a optimalizovat sestavení pro ladění, zadejte **OPT**. To může snížit velikost spustitelný soubor a může být užitečné optimalizace i v ladění sestavení. Doporučujeme vám, že zadáváte **noicf** pro zachování identických funkcí v ladění sestavení. Usnadníte tím čtení trasování zásobníku a nastavení zarážek ve funkcích, které by jinak byly složeny dohromady.

**Brána**\[**=**_iterací_] &#124; **NOICF**

Použití **ICF**\[**=**_iterací_] k provedení IDENTICKÉHO skládání comdat. Redundantní sekvence COMDAT lze odebrat z výstupu linkeru. Volitelný *iterací* parametr určuje počet, kolikrát procházet duplicity v symbolech. Výchozí počet iterací je 1. Při dalších iteracích se mohou najít další duplicity, které se odhalí skládáním při předchozí iteraci.

Ve výchozím nastavení **/OPT:ICF** je povoleno pomocí linkeru, není-li **noicf** nebo [/DEBUG](debug-generate-debug-info.md) je zadán. Chcete-li přepsat toto výchozí nastavení a zabránit sekvence Comdat se přeloží do programu, zadejte **noicf**.

V sestavení pro ladění, je nutné explicitně zadat **/OPT:ICF** Povolit skládání sekvencí COMDAT. Ale protože **/OPT:ICF** může sloučit identická data nebo funkce, můžete změnit názvy funkcí, které se zobrazují v trasování zásobníku. Můžete také znemožnit nastavit zarážky v určitých funkcích nebo prozkoumat některá data v ladicím programu a může trvat neočekávané funkce po vás krokování kódu. Chování kódu jsou identické, ale prezentace ladicí program může být velmi matoucí. Proto nedoporučujeme používat **/OPT:ICF** v laděných sestaveních, pokud výhody menšího kódu nepřeváží tyto nevýhody.

> [!NOTE]
> Protože **/OPT:ICF** můžou způsobit stejné adresa přiřadí různým funkcím nebo jen pro čtení datové členy (to znamená **const** proměnné při kompilaci pomocí **/Gy**), může to přerušit program, který závisí na jedinečných adresách funkcí nebo členů dat jen pro čtení. Další informace najdete v tématu [/Gy (povolení funkce propojení na úrovni)](gy-enable-function-level-linking.md).

**LBR** &#124; **NOLBR**

**/OPT:LBR** a **/OPT:NOLBR** platí pouze pro binární soubory ARM. Protože některé větvicí instrukce procesoru ARM mají omezený rozsah, pokud linker zjistí skok na adresu mimo rozsah, nahradí cílovou adresu této větvicí instrukce adresou „ostrůvku“ kódu, jenž obsahuje větvicí instrukci, která míří na skutečné místo určení. Můžete použít **/OPT:LBR** optimalizovat detekci dlouhých větvicích instrukcí a umístění ostrůvků zprostředkujícího kódu k minimalizaci celkové velikosti kódu. **/OPT:NOLBR** přikáže linkeru generovat ostrůvky kódu pro rozvětvené pokyny v průběhu jejich výskytu, bez optimalizace.

Ve výchozím nastavení **/OPT:LBR** možnost je nastavena, když není zapnuto přírůstkové propojení. Pokud chcete nepřírůstkové propojení, ale ne dlouhé větve optimalizací, určete **/OPT:NOLBR**. **/OPT:LBR** zakáže přírůstkové propojení.

## <a name="remarks"></a>Poznámky

Při použití příkazového řádku linkeru výchozí **OPT: ICF, LBR**. Pokud **/DEBUG** není zadán, výchozí hodnota je **noref, NOICF, NOLBR**.

**/OPT** optimalizace obecně zmenšit velikost bitové kopie a zvyšují rychlost aplikace. Tato vylepšení může být významné v větších programů, což je důvod, proč je povoleno standardně pro prodejní buildy.

Optimalizace linkeru ještě před zahájením trvat delší dobu, ale optimalizovaný kód také šetří čas, kdy linkeru má méně přemístění se opravit a vytvoří menší finální image a uloží ještě víc času, kdy má méně ladících informací ke zpracování a zápis do PDB. Pokud je povolena optimalizace, může vést rychlejší propojování celkově jako malý poplatek analýzy může být více než v době, kdy úspory v linkeru přetahovaného menší binární soubory.

**/OPT** argumenty může zadat současně, oddělené čárkami. Například namísto z **OPT: noicf**, můžete zadat **OPT, NOICF**.

Můžete použít [/VERBOSE](verbose-print-progress-messages.md) – možnost linkeru můžete zobrazit funkce, které jsou odebrány parametrem **OPT** a funkce, které jsou složeny parametrem **/OPT:ICF**.

**/OPT** argumenty jsou často nastaveny pro projekty vytvořené pomocí **nový projekt** dialogového okna v sadě Visual Studio IDE, a obvykle mají různé hodnoty pro ladění a verze konfigurace. Pokud tyto možnosti linkeru v projektu pro není nastavena žádná hodnota, se může zobrazit výchozí vlastnosti projektu, které může lišit od výchozí hodnoty pro propojovací program na příkazovém řádku.

### <a name="to-set-the-opticf-or-optref-linker-option-in-the-visual-studio-development-environment"></a>Nastavení parametru linkeru OPT:ICF nebo OPT:REF ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **optimalizace** stránku vlastností.

1. Změňte některou z těchto vlastností:

   - **Povolit skládání sekvencí COMDAT**

   - **Odkazy**

### <a name="to-set-the-optlbr-linker-option-in-the-visual-studio-development-environment"></a>Nastavení parametru linkeru OPT:LBR ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **příkazového řádku** stránku vlastností.

1. Zadejte parametr do **další možnosti**:

   `/opt:lbr` Nebo `/opt:nolbr`

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableCOMDATFolding%2A> a <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OptimizeReferences%2A> vlastnosti.

## <a name="see-also"></a>Viz také:

- [Odkaz na MSVC linkeru](linking.md)
- [Možnosti Linkeru MSVC](linker-options.md)
