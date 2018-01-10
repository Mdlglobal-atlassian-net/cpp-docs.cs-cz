---
title: "-Gs (Kontrola volání ověření zásobníku ovládací prvek) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /GS
dev_langs: C++
helpviewer_keywords:
- disabling stack probes
- GS compiler option [C++]
- /GS compiler option [C++]
- stack, stack probes
- stack probes
- -GS compiler option [C++]
- stack checking calls
ms.assetid: 40daed7c-f942-4085-b872-01e12b37729e
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ff02465b4e1b1a727a2367c8d5e038f30854ecc6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="gs-control-stack-checking-calls"></a>/Gs (kontrola volání ověření zásobníku)
Sondy zásobníku ovládací prvky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Gs[size]  
```  
  
## <a name="arguments"></a>Arguments  
 `size`  
 (Volitelné) Počet bajtů, které můžete před sondy zásobníku zabírají lokální proměnné je zahájena. Pokud **/Gs** je zadána možnost bez `size` argument, je stejné jako zadání **/Gs0**,  
  
## <a name="remarks"></a>Poznámky  
 Sondy zásobníku je posloupnost kód, který kompilátor vloží do každé volání funkce. Při spuštění, dosáhne sondy zásobníku benignly do paměti podle množství místa, které je potřeba k uložení místní proměnné funkce.  
  
 Pokud funkce vyžaduje více než `size` bajtů zásobníku místo pro místní proměnné, je zahájeno jeho sondy zásobníku. Ve výchozím nastavení kompilátor generuje kód, který iniciuje sondy zásobníku, pokud funkci vyžaduje více než jednu stránku místa v zásobníku. Jde o ekvivalent kompilátoru možnost **/Gs4096** pro x86, [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]a platformy ARM. Tato hodnota aplikace a systému Windows umožňuje správci paměti zvýšit množství paměti, které jsou potvrzené do zásobníku program dynamicky za běhu.  
  
> [!NOTE]
>  Výchozí hodnota **/Gs4096** umožňuje programu zásobník aplikací systému Windows správně růst v době běhu. Doporučujeme, pokud si nejste jisti, přesně proč máte ho můžete změnit není změňte výchozí hodnotu.  
  
 Některé programy – například virtuální ovladače zařízení – nevyžadují, aby tento mechanismus výchozí zásobník růstu. V takových případech nejsou nutné sondy zásobníku a můžete zastavit kompilátoru z jejich generování nastavením `size` na hodnotu, která je větší, než bude vyžadovat žádné funkce pro místní proměnné úložiště. Žádné místo je povoleno mezi **/Gs** a `size`.  
  
 **/ Gs0** aktivuje sondy zásobníku pro každé volání funkce, která vyžaduje úložiště pro místní proměnné. To může mít negativní dopad na výkon.  
  
 Chcete-li sondy zásobníku zapnout nebo vypnout pomocí [check_stack –](../../preprocessor/check-stack.md). **/GS** a `check_stack` – Direktiva pragma mít žádný vliv na standardní rutiny knihovny C; ovlivní pouze tyto funkce, které zkompilujete.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **C/C++** složky.  
  
3.  Vyberte **příkazového řádku** stránku vlastností.  
  
4.  Možnosti kompilátoru v typu **další možnosti** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)