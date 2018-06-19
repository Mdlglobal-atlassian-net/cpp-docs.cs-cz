---
title: -guard (povolení řízení toku ochrana) | Microsoft Docs
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
ms.openlocfilehash: b5c60ff444189e9e6b7919b43649b75722ee7249
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377401"
---
# <a name="guard-enable-control-flow-guard"></a>/guard (povolení ochrany toku řízení)
Povolte kompilátoru generování kontroly zabezpečení ochrany toku řízení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/guard:cf[-]  
```  
  
## <a name="remarks"></a>Poznámky  
 **/Guard:cf** způsobí, že kompilátor k analýze tok řízení pro cíle nepřímé volání při kompilaci a potom pro vložení kódu k ověření cílů v době běhu. Ve výchozím nastavení **/guard:cf** je vypnutý a musí být explicitně povolené. Chcete-li explicitně zakázat tuto možnost, použijte **/guard:cf-**.  
  
 Když **/guard:cf** je zadána možnost řízení toku Guard (CFG), kompilátoru a linkeru vložit kontrol zabezpečení navíc runtime zjišťování pokusů o ohrozit váš kód. Při kompilování a propojování, jsou všechny nepřímé volání v kódu analyzovány najít každé umístění, které kód dosáhnout při správném spuštění. Tyto informace jsou uloženy v navíc struktury v hlavičkách vaší binárních souborů. Kompilátor také vloží kontrolu před každou nepřímé volání ve vašem kódu, který zajistí, že cíl je jedním z ověřené umístění. Pokud kontrola selže za běhu na CFG používající operační systém, program ukončí operačního systému.  
  
 Běžné útok na softwaru využívá chyby při zpracování extrémně nebo neočekávané vstupy. Pečlivě vytvořené zadání aplikace může přepsat umístění, které obsahuje ukazatel na spustitelného kódu. To slouží k přesměrování tok řízení řízené útočník kódu. Kontroly runtime CFG nelze vyřešit chyby poškození dat ve vašem spustitelný soubor. Se místo toho je obtížné více pro útočníka je použít k vykonání libovolného kódu. CFG je nástroj zmírnění dopadů, která zabraňuje volání do umístění než funkce vstupních bodů ve vašem kódu. Je podobná jak Zabránění spuštění dat (DEP), [/GS](../../build/reference/gs-buffer-security-check.md) zásobníku kontroly, a [/DYNAMICBASE](../../build/reference/dynamicbase-use-address-space-layout-randomization.md) a [/highentropyva](../../build/reference/highentropyva-support-64-bit-aslr.md) adres místo rozložení náhodného přeskupování (technologie ASLR) nižší možnosti, která kódu stane je vektor zneužití.  
  
 **/Guard:cf** možnost musí být předán obou kompilátoru a linkeru vytvářet kód, který používá CFG zneužít zmírnění techniku. Pokud je vaše binární integrovaný pomocí jediné `cl` příkaz, kompilátor předá možnosti linkeru. Pokud kompilace a propojení samostatně, musí být nastavena možnost kompilátoru a linkeru příkazy. Také je vyžadována možnost /DYNAMICBASE linkeru. Pokud chcete ověřit, zda má vaše binární CFG data, použijte `dumpbin /headers /loadconfig` příkaz. Mít povoleno CFG binární soubory `Guard` v seznamu EXE nebo DLL vlastností a ochrana příznaky patří `CF Instrumented` a `FID table present`.  
  
 **/Guard:cf** možnost není kompatibilní s [/ZI](../../build/reference/z7-zi-zi-debug-information-format.md) (úpravy a pokračujete v ladění informace) nebo [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) (kompilace Common Language Runtime).  
  
 Kód zkompilovat pomocí **/guard:cf** objektu soubory, které nejsou kompilovány pomocí možnosti a může být propojený knihovny. Pouze tento kód, když také propojit pomocí **/guard:cf** možnost a spustit na deklaracemi CFG operačního systému, má CFG ochranu. Protože kód kompilovat bez možnosti neukončí útoku, doporučujeme použít možnost všechny, které zkompilujete kódu. Je malý modul runtime, náklady pro CFG kontroly, ale analysis kompilátoru pokusí optimalizovat rychle kontrolu na nepřímých přeskočí, které může být ověřené bezpečné.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **vlastnosti konfigurace**, **C/C++**, **generování kódu**.  
  
3.  Vyberte **řízení toku ochrana** vlastnost.  
  
4.  V ovládacím prvku rozevíracího seznamu vyberte **Ano** povolit ochranu toku řízení nebo **ne** ji zakázat.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)