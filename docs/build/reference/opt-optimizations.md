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
ms.openlocfilehash: b25db4d6c260c3c6751de293aa2a82df8aa05e7e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336225"
---
# <a name="opt-optimizations"></a>/OPT (optimalizace)

Řídí optimalizace, které program LINK provádí během sestavování.

## <a name="syntax"></a>Syntaxe

> **/OPT:**{**REF** | **NOREF**}<br/>
> **/OPT:**{**ICF**[**=**_iterací_] | **NOICF**}<br/>
> **/OPT:**{**LBR** | **NOLBR**}

## <a name="arguments"></a>Argumenty

**REF** &#124; **NOREF**

**/OPT:REF** eliminuje funkce a data, na které se nikdy neodkazuje; **/OPT:NOREF** uchovává funkce a data, na které se nikdy neodkazuje.

Pokud je povolen parametr /OPT:REF, link odebere neodkazované sbalené funkce a data, známé jako *COMDATs*. Tato optimalizace se označuje jako přechodné odstranění sekvence COMDAT. Možnost **/OPT:REF** také zakáže přírůstkové propojení.

Vložené funkce a členské funkce definované uvnitř deklarace třídy jsou vždy COMDATs. Všechny funkce v souboru objektu jsou provedeny do COMDATs, pokud je kompilován pomocí [/Gy](gy-enable-function-level-linking.md) možnost. Chcete-li umístit data **const** do comdats, `__declspec(selectany)`musíte deklarovat pomocí . Informace o určení dat pro odebrání nebo skládání naleznete v [tématu selectany](../../cpp/selectany.md).

Ve výchozím nastavení **/OPT:REF** je povoleno propojovacím sítí, pokud **/OPT:NOREF** nebo [/DEBUG](debug-generate-debug-info.md) je zadán. Chcete-li přepsat toto výchozí nastavení a zachovat v programu neodkazované hodnoty COMDAT, zadejte **parametr /OPT:NOREF**. Možnost [/INCLUDE](include-force-symbol-references.md) můžete použít k přepsání odebrání určitého symbolu.

Pokud je zadán [/DEBUG,](debug-generate-debug-info.md) výchozí pro **/OPT** je **NOREF**a všechny funkce jsou zachovány v obraze. Chcete-li přepsat toto výchozí nastavení a optimalizovat sestavení ladění, zadejte **/OPT:REF**. To může zmenšit velikost spustitelného souboru a může být užitečná optimalizace i v sestavení ladění. Doporučujeme také zadat **/OPT:NOICF** zachovat identické funkce v sestavení ladění. Usnadníte tím čtení trasování zásobníku a nastavení zarážek ve funkcích, které by jinak byly složeny dohromady.

**ICF**\[**=**_Iterace_iCF ] &#124; **NOICF**

Pomocí_iterací_ **icf**\[**=**] proveďte identické skládání comdat. Redundantní sekvence COMDAT lze odebrat z výstupu linkeru. Parametr volitelné *iterace* určuje počet procházení symbolů pro duplikáty. Výchozí počet iterací je 1. Při dalších iteracích se mohou najít další duplicity, které se odhalí skládáním při předchozí iteraci.

Ve výchozím nastavení **/OPT:ICF** je povoleno propojovacím programů, pokud **/OPT:NOICF** nebo [/DEBUG](debug-generate-debug-info.md) je zadán. Chcete-li přepsat toto výchozí nastavení a zabránit skládání comdat v programu, zadejte **/OPT:NOICF**.

V sestavení ladění je nutné explicitně zadat **/OPT:ICF,** abyste povolili skládání comdat. Protože však **/OPT:ICF** může sloučit identická data nebo funkce, může změnit názvy funkcí, které se zobrazují v trasování zásobníku. Může také znemožnit nastavení zarážek v určitých funkcích nebo prozkoumat některá data v ladicím programu a může vás převést do neočekávaných funkcí při vytvoření kódu jedním krokem. Chování kódu je identické, ale ladicí program prezentace může být velmi matoucí. Proto nedoporučujeme používat **/OPT:ICF** v sestavení ladění, pokud výhody menší kód převažují nad těmito nevýhodami.

> [!NOTE]
> Protože **/OPT:ICF** může způsobit, že stejnou adresu přiřadit k různým funkcím nebo jen pro čtení datových členů (to znamená **const** proměnné při kompilaci pomocí **/Gy**), může přerušit program, který závisí na jedinečné adresy pro funkce nebo jen pro čtení datových členů. Další informace naleznete v tématu [/Gy (Enable Function-Level Linking)](gy-enable-function-level-linking.md).

**LBR** &#124; **NOLBR**

Možnosti **/OPT:LBR** a **/OPT:NOLBR** platí pouze pro binární soubory ARM. Vzhledem k tomu, že některé pokyny větve procesoru ARM mají omezený rozsah, pokud propojovací program zjistí skok na adresu mimo rozsah, nahradí cílovou adresu instrukce větve adresou adresou kódu "ostrov", který obsahuje instrukce větve, která se zaměřuje na skutečný cíl. Můžete použít **/OPT:LBR** optimalizovat detekci dlouhé větve pokyny a umístění zprostředkující kód ostrovů minimalizovat celkovou velikost kódu. **/OPT:NOLBR** instruuje propojovací program ke generování kódových ostrovů pro dlouhé instrukce větve, jakmile se vyskytnou, bez optimalizace.

Ve výchozím nastavení je možnost **/OPT:LBR** nastavena, pokud není povoleno přírůstkové propojení. Pokud chcete nepřírůstkové propojení, ale ne dlouhé optimalizace větví, zadejte **/OPT:NOLBR**. Možnost **/OPT:LBR** zakáže přírůstkové propojení.

## <a name="remarks"></a>Poznámky

Při použití na příkazovém řádku je propojovací systém výchozí parametr **/OPT:REF,ICF,LBR**. Pokud je zadán **parametr /DEBUG,** je výchozí hodnota **/OPT:NOREF,NOICF,NOLBR**.

Optimalizace **/OPT** obecně zmenšují velikost obrázku a zvyšují rychlost programu. Tato vylepšení mohou být podstatná ve větších programech, což je důvod, proč jsou ve výchozím nastavení povolena pro maloobchodní sestavení.

Optimalizace linkeru trvá více času dopředu, ale optimalizovaný kód také šetří čas, když propojovací program má méně přemisťování opravit a vytvoří menší konečný obraz a šetří ještě více času, když má méně ladicí informace pro zpracování a zápis do PDB. Pokud je optimalizace povolena, může celkově vést k rychlejšímu prodloužení doby propojení, protože malé dodatečné náklady na analýzu mohou být více než kompenzovány časovými úsporami v propojovacím programu přes menší binární soubory.

**/OPT** argumenty mohou být určeny společně, oddělené čárkami. Například místo **/OPT:REF /OPT:NOICF**můžete zadat **/OPT:REF,NOICF**.

Pomocí možnosti propojovacího systému [/VERBOSE](verbose-print-progress-messages.md) můžete zobrazit funkce, které jsou odebrány **parametrem /OPT:REF,** a funkce, které jsou přeloženy **parametrem /OPT:ICF**.

**/OPT** argumenty jsou často nastaveny pro projekty vytvořené pomocí **dialogového** okna Nový projekt v IDE sady Visual Studio a obvykle mají různé hodnoty pro ladění a uvolnění konfigurace. Pokud žádná hodnota je nastavena pro tyto možnosti propojovacího systému v projektu, pak může získat výchozí hodnoty projektu, které se mohou lišit od výchozí hodnoty používané propojovacího systému na příkazovém řádku.

### <a name="to-set-the-opticf-or-optref-linker-option-in-the-visual-studio-development-environment"></a>Nastavení parametru linkeru OPT:ICF nebo OPT:REF ve vývojovém prostředí sady Visual Studio

1. Otevřete dialogové okno **Stránky vlastností** projektu. Podrobnosti naleznete v [tématu Nastavení kompilátoru jazyka C++ a vlastnosti sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte stránku**vlastností Optimalizace**  > **linkeru** >  **vlastností vlastností vlastností vlastností vlastností vlastností vlastností konfigurace.**

1. Změňte některou z těchto vlastností:

   - **Povolit skládání sekvencí COMDAT**

   - **Odkazy**

### <a name="to-set-the-optlbr-linker-option-in-the-visual-studio-development-environment"></a>Nastavení parametru linkeru OPT:LBR ve vývojovém prostředí sady Visual Studio

1. Otevřete dialogové okno **Stránky vlastností** projektu. Podrobnosti naleznete v [tématu Nastavení kompilátoru jazyka C++ a vlastnosti sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte stránku vlastností**příkazového řádku** **propojovacího** > programu **Vlastnosti** > konfigurace.

1. Zadejte možnost v **dalších možnostech**:

   `/opt:lbr` nebo `/opt:nolbr`

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableCOMDATFolding%2A> <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OptimizeReferences%2A> a vlastnosti.

## <a name="see-also"></a>Viz také

- [Referenční zdroje k linkeru MSVC](linking.md)
- [Možnosti propojovacího zařízení MSVC](linker-options.md)
