---
title: -Gs (Kontrola volání ověření zásobníku ovládací prvek) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /GS
dev_langs:
- C++
helpviewer_keywords:
- disabling stack probes
- GS compiler option [C++]
- /GS compiler option [C++]
- stack, stack probes
- stack probes
- -GS compiler option [C++]
- stack checking calls
ms.assetid: 40daed7c-f942-4085-b872-01e12b37729e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c0c6a5af31eaba30af92201a2e2563b67aceed6e
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44104105"
---
# <a name="gs-control-stack-checking-calls"></a>/Gs (kontrola volání ověření zásobníku)
Řídí sondu zásobníku.

## <a name="syntax"></a>Syntaxe

```  
/Gs[size]
```  

## <a name="arguments"></a>Arguments
*Velikost*<br/>
(Volitelné) Počet bajtů, které může zabírat místní proměnné před sondu zásobníku je zahájeno. Pokud **/Gs** je zadána možnost bez `size` argument, je stejné jako zadání **/Gs0**,

## <a name="remarks"></a>Poznámky
Sondy zásobníku je posloupnost kód, který kompilátor vloží do každé volání funkce. Při spuštění, dosáhne sondu zásobníku benignly do paměti na množství místa, které je nutné pro ukládání místních proměnných funkce.

Pokud funkce vyžaduje více než `size` bajtů zásobníku místo pro místní proměnné, je zahájeno jeho sondy zásobníku. Ve výchozím nastavení kompilátor generuje kód, který iniciuje sondu zásobníku, pokud funkci vyžaduje více než jednu stránku místo v zásobníku. To je ekvivalentní možnosti kompilátoru **/Gs4096** x86, x64 a ARM platformy. Tato hodnota umožňuje aplikaci a Windows správce paměti pro zvýšení množství paměti potvrzené do zásobníku programu dynamicky za běhu.

> [!NOTE]
>  Výchozí hodnota **/Gs4096** umožňuje zásobníku aplikací pro Windows správně růst v době běhu programu. Doporučujeme vám, pokud si nejste jisti, že přesně Proč je třeba změnit ho nelze změnit výchozí hodnotu.

Některé programy – například ovladačů virtuálních zařízení – nevyžadují, aby tento mechanismus výchozí zásobníku růstu. V takovém případě nejsou nutné sondy zásobníku a zastavíte kompilátoru generování nastavením `size` na hodnotu, která je větší, než všechny funkce bude vyžadovat místní proměnné úložiště. Je povolena mezera mezi **/Gs** a `size`.

**/ Gs0** aktivuje sondy zásobníku pro každé volání funkce, která vyžaduje úložiště pro místní proměnné. To může mít negativní dopad na výkon.

Sondy zásobníku zapnutí nebo vypnutí můžete vypnout pomocí [check_stack –](../../preprocessor/check-stack.md). **/GS** a `check_stack` – Direktiva pragma nemají žádný vliv na standardní rutiny knihoven C; ovlivní pouze funkce, které při kompilaci.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1.  Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

2.  Vyberte **C/C++** složky.

3.  Vyberte **příkazového řádku** stránku vlastností.

4.  Zadejte možnost do kompilátoru **další možnosti** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

-   Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také
[Možnosti kompilátoru](../../build/reference/compiler-options.md)   
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)