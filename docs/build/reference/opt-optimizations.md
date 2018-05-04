---
title: -OPT (optimalizace) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: f8ac107f8a5654601f0c974f82fa83ae6aa83518
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="opt-optimizations"></a>/OPT (optimalizace)
Řídí optimalizace, které program LINK provádí během sestavování.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/OPT:{REF | NOREF}  
/OPT:{ICF[=iterations] | NOICF}  
/OPT:{LBR | NOLBR}  
```  
  
## <a name="arguments"></a>Arguments  
 **REF** &AMP;#124; **NOREF**  
 **/OPT:REF** eliminuje funkce a data, která se nikdy odkazuje; **/OPT:NOREF** zajišťuje funkce a data, která se nikdy odkazuje.  
  
 Pokud je povoleno /OPT:REF, odebere odkaz neregistrované zabalené funkce a data. Objekt obsahuje zabalené funkce a data (COMDATs), pokud byl kompilován s použitím [/Gy](../../build/reference/gy-enable-function-level-linking.md) možnost. Tato optimalizace se označuje jako přechodné odstranění sekvence COMDAT. Ve výchozím nastavení **/OPT:REF** je povolena v sestavení bez ladění. Chcete-li přepsat toto výchozí nastavení a zachovat neregistrované COMDATs v programu, zadejte **/OPT:NOREF**. Můžete použít [/INCLUDE](../../build/reference/include-force-symbol-references.md) možnost přepsání odebrání konkrétní symbolu.  
  
 Při **/OPT:REF** je povolené, explicitně nebo ve výchozím nastavení jsou omezené **/OPT:ICF** je povolen, pouze složení stejné funkce. Chcete-li **/OPT:REF** ale ne **/OPT:ICF**, je nutné zadat buď **/OPT:REF, NOICF** nebo **/OPT:NOICF**.  
  
 Pokud [/DEBUG](../../build/reference/debug-generate-debug-info.md) je zadána výchozí hodnota pro **/OPT** je **NOREF**, a všechny funkce, které budou zachovány v bitové kopii. Chcete-li přepsat toto výchozí nastavení a optimalizovat ladění sestavení, zadejte **/OPT:REF**. Protože **/OPT:REF** znamená **/OPT:ICF**, doporučujeme, aby také určit **/OPT:NOICF** se zachovat stejné funkce při ladění sestavení. Usnadníte tím čtení trasování zásobníku a nastavení zarážek ve funkcích, které by jinak byly složeny dohromady. **/OPT:REF** možnost zakáže přírůstkové propojování.  
  
 Je nutné explicitně označit `const` data jako sekvence COMDAT; použijte [__declspec(selectany)](../../cpp/selectany.md).  
  
 Určení **/OPT:ICF** není povolen **/OPT:REF** možnost.  
  
 **BRÁNOU FIREWALL [=** `iterations` **] &AMP;#124; NOICF**  
 Použití **/OPT:ICF [=**`iterations`**]** k provedení identické sekvence COMDAT skládání. Redundantní sekvence COMDAT lze odebrat z výstupu linkeru. Volitelné `iterations` parametr určuje počet pokusů procházení symboly pro duplicitní položky. Výchozí počet iterací jsou dvě. Při dalších iteracích se mohou najít další duplicity, které se odhalí skládáním při předchozí iteraci.  
  
 Linkeru chová odlišně při **/OPT:REF** je zadán – a **bránou Firewall** ve výchozím nastavení je v platnosti – než kdy **/OPT:REF, bránou Firewall** explicitně nastaven. Formu **bránou Firewall** , je povolená s **/OPT:REF** samostatně není fold jen pro čtení dat – to zahrnuje .rdata, .pdata a .xdata. Proto jsou méně funkcí přeloženy, když vytváří bitové kopie pro [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] protože funkcí v tyto moduly jsou více závislé na jen pro čtení dat – například .pdata a .xdata. Chcete-li získat úplné **bránou Firewall** skládání chování, explicitně zadáte **/OPT:ICF**.  
  
 Pokud chcete umístit funkce COMDATs, použijte **/Gy** – možnost kompilátoru; umístit `const` data, deklarovat `__declspec(selectany)`. Informace o tom, jak zadat data skládání najdete v tématu [selectany](../../cpp/selectany.md).  
  
 Ve výchozím nastavení **bránou Firewall** je-li **REF** zapnutý. Chcete-li přepsat toto výchozí nastavení, pokud **REF** je zadán, použijte **NOICF**. Když **/OPT:REF** není zadané v sestavení ladicí verze, je nutné explicitně zadat **/OPT:ICF** povolit sekvence COMDAT skládání. Ale protože **/OPT:ICF** můžete sloučit stejné údaje nebo funkce, ho můžete změnit názvy funkcí, které se zobrazují v trasování zásobníku. To také umožní nastavit zarážky v určitých funkcích nebo prozkoumat některá data v ladicím programu a při krokování kódu odhalit neočekávané funkce. Proto nedoporučujeme používat **/OPT:ICF** ladění sestavení Pokud výhody menší kódu převáží nad tyto nevýhody.  
  
> [!NOTE]
>  Protože **/OPT:ICF** může způsobit stejnou adresu pro přiřazení k různým funkcím nebo jen pro čtení datové členy (`const` proměnné zkompilovat pomocí **/Gy**), je možné přerušit programu, který závisí na jedinečné adresy pro funkce nebo jen pro čtení datových členů. Další informace najdete v tématu [/Gy (povolení propojení na úrovni funkcí)](../../build/reference/gy-enable-function-level-linking.md).  
  
 **LBR** &AMP;#124; **NOLBR**  
 **/OPT:LBR** a **/OPT:NOLBR** možnosti platí pouze pro binární soubory ARM. Protože některé větvicí instrukce procesoru ARM mají omezený rozsah, pokud linker zjistí skok na adresu mimo rozsah, nahradí cílovou adresu této větvicí instrukce adresou „ostrůvku“ kódu, jenž obsahuje větvicí instrukci, která míří na skutečné místo určení. Můžete použít **/OPT:LBR** k optimalizaci detekce dlouho větve pokyny a umístění zprostředkující kód ostrovy minimalizovat celkové velikosti kódu. **/OPT:NOLBR** dá pokyn linkeru ke generování kódu ostrovy dlouho větve pokyny, jak se vyskytují, bez optimalizace.  
  
 Ve výchozím nastavení **/OPT:LBR** je možnost nastavena, když přírůstkové propojování není povoleno. Pokud chcete nepřírůstkové odkaz, ale není optimalizace dlouho větve, zadejte **/OPT:NOLBR**. **/OPT:LBR** možnost zakáže přírůstkové propojování.  
  
## <a name="remarks"></a>Poznámky  
 Optimalizace obecně zmenšují velikost bitové kopie a zvyšují rychlost aplikace za cenu delšího propojování.  
  
 Můžete použít [/VERBOSE](../../build/reference/verbose-print-progress-messages.md) možnost zobrazit funkce, které jsou odebrány podle **/OPT:REF** a funkce, které jsou přeloženy podle **/OPT:ICF**.  
  
### <a name="to-set-the-opticf-or-optref-linker-option-in-the-visual-studio-development-environment"></a>Nastavení parametru linkeru OPT:ICF nebo OPT:REF ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  V levém podokně rozbalte **vlastnosti konfigurace**, **Linkeru**, **optimalizace**.  
  
3.  Změňte některou z těchto vlastností:  
  
    -   **Povolit sekvence COMDAT skládání**  
  
    -   **Odkazy**  
  
### <a name="to-set-the-optlbr-linker-option-in-the-visual-studio-development-environment"></a>Nastavení parametru linkeru OPT:LBR ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **Linkeru** složky.  
  
3.  Vyberte **příkazového řádku** stránku vlastností.  
  
4.  Zadejte možnost v **další možnosti**:  
  
     `/opt:lbr`  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
1.  V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableCOMDATFolding%2A> a <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OptimizeReferences%2A> vlastnosti.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)
