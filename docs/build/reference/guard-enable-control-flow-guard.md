---
title: -guard (povolení ochrany toku řízení) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /guard
- VC.Project.VCCLCompilerTool.ControlFlowGuard
dev_langs:
- C++
ms.assetid: be495323-f59f-4cf3-a6b6-8ee69e6a19dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6c65bafc14f5ef29db89ddc0a4647193231f7e19
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2018
ms.locfileid: "43131667"
---
# <a name="guard-enable-control-flow-guard"></a>/guard (povolení ochrany toku řízení)
Povolení ochrany toku provádění kontroly zabezpečení kompilátoru generování.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/guard:cf[-]  
```  
  
## <a name="remarks"></a>Poznámky  
 **/Guard: CF** možnost způsobí, že kompilátor pro analýzu toku řízení pro cíle nepřímé volání v době kompilace a pak se vložit kód pro ověření cíle za běhu. Ve výchozím nastavení **/Guard: CF** je vypnuté a musí být explicitně povolené. Chcete-li explicitně zakázat tuto možnost, použijte **/guard:cf-**. 

**Visual Studio 2017 a novější**: Tato možnost přidá ochrany pro **přepnout** příkazy, které generují jump tabulky.
  
 Když **/Guard: CF** je zadána možnost řízení toku ochranu (CFG), kompilátoru a linkeru vložit kontrol zabezpečení navíc runtime odhalit pokusy o ohrozit váš kód. Při kompilování a propojování, jsou analyzovány všechna nepřímé volání v kódu najít každou oblast, které kód může dosáhnout při správném spuštění. Tyto informace jsou uloženy v dalších struktury v hlavičkách vaše binární soubory. Kompilátor vkládá také kontrolu před každou nepřímé volání v kódu, které zajistí, že cíl je jedním z ověřených umístění. Pokud kontrola selže v době běhu s ohledem na CFG operační systém, program ukončí operačního systému.  
  
 Běžných způsobů útoku na softwaru využívá chyby při zpracování extreme nebo neočekávané vstupy. Pečlivě vytvořený vstup do aplikace může přepsat umístění, které obsahuje ukazatel na spustitelného kódu. To je možné přesměrovat do kódu řídí útočník tok řízení. Kontroly za běhu CFG nelze vyřešit chyby poškození dat v spustitelný soubor. Se místo toho to ztížit útočník se dají použít k vykonání libovolného kódu. Parametr CFG je nástroj omezení rizik, které brání volání do umístění jiného než funkce vstupních bodů ve vašem kódu. Je podobný postupu Zabránění spuštění dat (DEP), [/GS](../../build/reference/gs-buffer-security-check.md) kontroly zásobníku a [možnost/DynamicBase](../../build/reference/dynamicbase-use-address-space-layout-randomization.md) a [/highentropyva](../../build/reference/highentropyva-support-64-bit-aslr.md) adres náhodného generování rozložení prostoru (technologie ASLR) nižší možnosti, že váš kód bude je vektor před zneužitím.  
  
 **/Guard: CF** možnost musí být předán do obou kompilátoru a linkeru sestavit kód, který se používá CFG zneužít techniku omezení rizik. Pokud je binární soubor sestavena pomocí jediné `cl` příkazu, kompilátor předá linkeru parametr. Pokud kompilujete a propojujete samostatně, musí být nastavena možnost v kompilátoru a linkeru příkazy. Možnosti linkeru možnost/DynamicBase je také nutný. Ověřte, že binární soubor má parametr CFG data, použijte `dumpbin /headers /loadconfig` příkazu. Povolené CFG binární soubory mají `Guard` v seznamu vlastností souboru EXE nebo DLL a příznaky Guard zahrnují `CF Instrumented` a `FID table present`.  
  
 **/Guard: CF** možnost není kompatibilní s [/zi](../../build/reference/z7-zi-zi-debug-information-format.md) (Upravit a pokračovat informace o ladění) nebo [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) (kompilace Common Language Runtime).  
  
 Kód zkompilovaný pomocí **/Guard: CF** lze propojit do knihovny a soubory, které nejsou zkompilovány pomocí možnosti objektu. Pouze tento kód, když také propojena s použitím **/Guard: CF** možnost a spouštět s ohledem na CFG operačního systému, ochranou CFG. Vzhledem k tomu, že kód zkompiloval bez možnosti nezpůsobí ukončení útoku, doporučujeme použít možnost kód, který kompilaci. Je malý modul runtime nákladů pro parametr CFG kontroly, ale analýza kompilátor se pokusí optimalizují kontrol nepřímé přeskočí, které mohou být prověřené jako bezpečné.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **vlastnosti konfigurace**, **C/C++**, **generování kódu**.  
  
3.  Vyberte **ochrany toku provádění** vlastnost.  
  
4.  V ovládacím prvku rozevíracího seznamu vyberte **Ano** k povolení ochrany toku provádění, nebo **ne** ho zakážete.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)