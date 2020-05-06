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
ms.openlocfilehash: 5c0ab3579fcb9633c435305a8b02b0c3f73d7a6f
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825701"
---
# <a name="opt-optimizations"></a>/OPT (optimalizace)

Řídí optimalizace, které program LINK provádí během sestavování.

## <a name="syntax"></a>Syntaxe

> **/OPT:**{**ref** | **NOREF**} \
> **/OPT:**{**ICF**[**=**_iterace_] | **NOICF**} \
> **/OPT:**{**LBR** | **NOLBR**}

## <a name="arguments"></a>Argumenty

**REF** &#124; **NOREF**

**/OPT: ref** eliminuje funkce a data, která nejsou nikdy odkazována; **/OPT: NOREF** uchovává funkce a data, která nejsou nikdy odkazována.

Když je povolená možnost/OPT: REF, odkaz odstraní neodkazované funkce a data, které se nazývají *sekvence COMDAT*. Tato optimalizace se označuje jako přechodné odstranění sekvence COMDAT. Možnost **/OPT: ref** také zakáže přírůstkové propojení.

Vložené funkce a členské funkce definované uvnitř deklarace třídy jsou vždy sekvence COMDAT. Všechny funkce v souboru objektu jsou vytvořeny do sekvence COMDAT, pokud je zkompilován pomocí možnosti [/Gy](gy-enable-function-level-linking.md) . Chcete-li umístit **const** data do sekvence COMDAT, je nutné ji `__declspec(selectany)`deklarovat pomocí. Informace o tom, jak zadat data pro odebrání nebo skládání, najdete v tématu [selectany](../../cpp/selectany.md).

Ve výchozím nastavení je **/OPT: ref** povolen linkerem, pokud není zadán parametr **/OPT: NOREF** nebo [/Debug](debug-generate-debug-info.md) . Pokud chcete přepsat toto výchozí nastavení a ponechat v programu neodkazované sekvence COMDAT, zadejte **/OPT: NOREF**. K přepsání odebrání konkrétního symbolu můžete použít možnost [/include](include-force-symbol-references.md) .

Je-li zadán parametr [/Debug](debug-generate-debug-info.md) , je výchozí hodnota pro **/opt** **NOREF**a všechny funkce jsou zachovány v imagi. Chcete-li přepsat toto výchozí nastavení a optimalizovat sestavení pro ladění, zadejte **/OPT: ref**. To může snížit velikost spustitelného souboru a může být užitečná optimalizace i v sestaveních ladění. Doporučujeme zadat také **/OPT: NOICF** , aby se zachovaly identické funkce v sestaveních ladění. Usnadníte tím čtení trasování zásobníku a nastavení zarážek ve funkcích, které by jinak byly složeny dohromady.

**ICF**\[**=**_Iterace_ICF] &#124; **NOICF**

Použijte **ICF**\[**=**_iterace_ICF] k provedení identického skládání COMDAT. Redundantní sekvence COMDAT lze odebrat z výstupu linkeru. Parametr volitelné *iterace* určuje počet pokusů, které se mají procházet symboly pro duplicity. Výchozí počet iterací je 1. Při dalších iteracích se mohou najít další duplicity, které se odhalí skládáním při předchozí iteraci.

Ve výchozím nastavení **/OPT: ICF** je povolena linkerem, pokud není zadán parametr **/OPT: NOICF** nebo [/Debug](debug-generate-debug-info.md) . Chcete-li přepsat toto výchozí nastavení a zabránit přeložení sekvence COMDAT do programu, zadejte **/OPT: NOICF**.

V sestavení pro ladění musíte explicitně zadat **/OPT: ICF** , aby se povolilo skládání COMDAT. Protože však **/OPT: ICF** může sloučit identická data nebo funkce, může změnit názvy funkcí, které se zobrazují v trasování zásobníku. Může také dojít k tomu, že není možné nastavovat zarážky v určitých funkcích nebo prozkoumávat některá data v ladicím programu a může přecházet k neočekávaným funkcím v případě, že jste provedli krokovat kód. Chování kódu je identické, ale prezentace ladicího programu může být velmi matoucí. Proto nedoporučujeme používat **/OPT: ICF** v sestavení ladění, pokud výhody menšího kódu převáží tyto nevýhody.

> [!NOTE]
> Vzhledem k tomu, že **/OPT: ICF** může způsobit přiřazení stejné adresy různým funkcím nebo datovým členům jen pro čtení (tj. **konstantní** proměnné při kompilaci pomocí **/Gy**), může přerušit program, který závisí na jedinečných adresách pro funkce nebo datové členy jen pro čtení. Další informace najdete v tématu [/Gy (povolení propojení na úrovni funkcí)](gy-enable-function-level-linking.md).

**LBR** &#124; **NOLBR**

**/OPT: LBR** a **/OPT: možnosti NOLBR** platí pouze pro binární soubory ARM. Vzhledem k tomu, že některé instrukce větví procesoru ARM mají omezený rozsah, pokud linker zjistí skok na adresu mimo rozsah, nahradí cílovou adresu instrukce větve adresou kódu "ostrov", který obsahuje instrukci větve, která cílí na skutečný cíl. **/OPT: LBR** můžete použít k optimalizaci detekce dlouhých instrukcí větví a umístění ostrovů zprostředkujícího kódu pro minimalizaci celkové velikosti kódu. **/OPT: NOLBR** dá linkeru pokyn, aby vygeneroval znakové ostrovy pro instrukce dlouhé větve, když jsou zjištěny, bez optimalizace.

Ve výchozím nastavení je možnost **/OPT: LBR** nastavena, když není povoleno přírůstkové propojení. Pokud chcete nepřírůstkové propojení, ale ne dlouhé větve, zadejte **/OPT: NOLBR**. Možnost **/OPT: LBR** zakáže přírůstkové propojení.

## <a name="remarks"></a>Poznámky

Při použití v příkazovém řádku je linker standardně **/OPT: REF, ICF, LBR**. Je-li zadán parametr **/Debug** , výchozí hodnota je **/OPT: NOREF, NOICF, NOLBR**.

Optimalizace **/opt** obecně zmenšují velikost obrázku a zvyšují rychlost programu. Tato vylepšení můžou být značná ve větších programech, což je důvod, proč jsou ve výchozím nastavení povolené pro maloobchodní buildy.

Optimalizace linkeru převezme předem čas dopředu, ale optimalizovaný kód také šetří čas, pokud má linker méně přemístění, aby opravil a vytvořil menší finální obrázek, a šetří ještě více času, pokud má méně ladicí informace ke zpracování a zápisu do souboru PDB. Když je optimalizace povolená, může to mít za následek rychlejší čas propojení, protože drobné další náklady na analýzu můžou být vyšší než posun, protože úspory času v linkeru přecházejí přes menší binární soubory.

Argumenty **/opt** lze zadat společně, oddělené čárkami. Například namísto **/OPT: ref/OPT: NOICF**můžete zadat **/OPT: REF, NOICF**.

Můžete použít možnost [/verbose](verbose-print-progress-messages.md) linker k zobrazení funkcí, které jsou odstraněny pomocí **/OPT: ref** a funkcí, které jsou složeny pomocí **/OPT: ICF**.

Argumenty **/opt** jsou často nastaveny pro projekty vytvořené pomocí dialogového okna **Nový projekt** v integrovaném vývojovém prostředí (IDE) sady Visual Studio a obvykle mají jiné hodnoty pro konfigurace ladění a vydání. Pokud není nastavena žádná hodnota pro tyto možnosti linkeru v projektu, můžete získat výchozí hodnoty projektu, které se mohou lišit od výchozích hodnot používaných linkerem na příkazovém řádku.

### <a name="to-set-the-opticf-or-optref-linker-option-in-the-visual-studio-development-environment"></a>Nastavení parametru linkeru OPT:ICF nebo OPT:REF ve vývojovém prostředí sady Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení kompilátoru C++ a vlastností sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte stránku vlastností**optimalizace**  > **linkeru** >  **Vlastnosti konfigurace**.

1. Změňte některou z těchto vlastností:

   - **Povolit skládání sekvencí COMDAT**

   - **Odkazy**

### <a name="to-set-the-optlbr-linker-option-in-the-visual-studio-development-environment"></a>Nastavení parametru linkeru OPT:LBR ve vývojovém prostředí sady Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení kompilátoru C++ a vlastností sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte stránku vlastností**příkazový řádek**  > **linkeru** >  **vlastností konfigurace**.

1. Zadejte možnost v části **Další možnosti**:

   `/opt:lbr` nebo `/opt:nolbr`

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableCOMDATFolding%2A> a <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OptimizeReferences%2A> vlastnosti.

## <a name="see-also"></a>Viz také

- [Referenční zdroje k linkeru MSVC](linking.md)
- [Možnosti linkeru MSVC](linker-options.md)
