---
title: -Yu (Použít předkompilovaný hlavičkový soubor) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /yu
dev_langs:
- C++
helpviewer_keywords:
- Yu compiler option [C++]
- /Yu compiler option [C++]
- -Yu compiler option [C++]
- PCH files, use existing
- .pch files, use existing
- precompiled header files, use existing
ms.assetid: 24f1bd0e-b624-4296-a17e-d4b53e374e1f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d115017e843e7f03455e1eef2b384b3475a1b798
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378714"
---
# <a name="yu-use-precompiled-header-file"></a>/Yu (Použít předkompilovaný hlavičkový soubor)
Instruuje kompilátor, aby používal existující soubor předkompilovaných hlaviček (.pch) v aktuální kompilace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Yu[filename]  
```  
  
## <a name="arguments"></a>Arguments  
 *Název souboru*  
 Název záhlaví souboru, který je součástí zdrojový soubor pomocí **#include** direktivy preprocesoru.  
  
## <a name="remarks"></a>Poznámky  
 Název souboru začlenění musí být stejné pro **/Yc** možnost, která vytvoří předkompilovaných hlaviček a všechny následné **/Yu** možnost, která určuje použití předkompilovaných hlaviček.  
  
 Pro **/Yc**, `filename` Určuje bod, ve které předkompilaci zastaví; kompilátor překompiluje celý kód ale `filename` a názvy výsledné předkompilovaných hlaviček pomocí základní název souboru začlenění a rozšíření z .pch.  
  
 Souboru .pch musí být vytvořen pomocí **/Yc**.  
  
 Kompilátor považuje veškerý kód před souboru h jako předkompilovaných. Přeskočí na právě i mimo **#include** – direktiva spojených se souborem .h používá kód obsažené v souboru .pch a pak zkompiluje celý kód po `filename`.  
  
 Na příkazovém řádku, je povoleno bez mezery mezi **/Yu** a `filename`.  
  
 Pokud zadáte **/Yu** musí obsahovat možnost bez názvu souboru, zdrojový program [hdrstop – #pragma](../../preprocessor/hdrstop.md) – Direktiva pragma, který určuje název souboru předkompilované hlavičky souboru .pch. V takovém případě kompilátor použije předkompilovaných hlaviček (souboru .pch) s názvem podle [/Fp (název. Soubor pch)](../../build/reference/fp-name-dot-pch-file.md). Kompilátor přeskočí na umístění této – Direktiva pragma, obnoví zkompilovaný z předkompilovaný hlavičkový soubor určený touto – Direktiva pragma a pak zkompiluje pouze kód, který následuje – Direktiva pragma. Pokud **hdrstop – #pragma** neurčuje názvu souboru kompilátoru hledá soubor s názvem odvozené ze základní název zdrojového souboru s příponou .pch. Můžete také **/Fp** možnost zadat jiný .pch soubor.  
  
 Pokud zadáte **/Yu** možnost bez názvu souboru a zadejte v opačném případě **hdrstop –** – Direktiva pragma, se vygeneruje chybovou zprávu a kompilace neúspěšná.  
  
 Pokud **/Yc** `filename` a **/Yu** `filename` možnosti na stejném příkazovém řádku a obě odkazovat na stejný název, **/Yc** `filename` trvá Priorita, až předkompilace všechny kódu a včetně uvedeného souboru. Tato funkce zjednodušuje zápis soubory pravidel.  
  
 Soubory .pch obsahovat informace o prostředí počítače a paměti adresu informace o programu, byste měli používat jenom soubor pch na počítači, kde se vytvořila.  
  
 Další informace o předkompilovaných hlaviček najdete v tématu:  
  
-   [/Y (předkompilované hlavičky)](../../build/reference/y-precompiled-headers.md)  
  
-   [Vytváření předkompilovaných hlavičkových souborů](../../build/reference/creating-precompiled-header-files.md)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Zadejte [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](../../build/reference/yc-create-precompiled-header-file.md) na soubor sada ve vašem projektu.  
  
2.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
3.  Klikněte **C/C++** složky.  
  
4.  Klikněte **předkompilovaných hlaviček** stránku vlastností.  
  
5.  Změnit **vytvořit nebo použít PCH prostřednictvím soubor** vlastnost nebo **vytvoření nebo použití předkompilovaných hlaviček** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A> a <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>.  
  
## <a name="examples"></a>Příklady  
 Pokud následující kód:  
  
```  
#include <afxwin.h>   // Include header for class library  
#include "resource.h" // Include resource definitions  
#include "myapp.h"    // Include information specific to this app  
...  
```  
  
 Kompiluje s příkazovým řádkem `CL /YuMYAPP.H PROG.CPP`, kompilátor nezpracovává tří obsahují příkazy, ale používá předkompilovaných kód z MYAPP.pch, a tím ukládání čas zahrnutých v předběžném zpracování všechny tři soubory (a všech souborů se mohou zahrnovat).  
  
 Můžete použít [/Fp (název. Soubor pch)](../../build/reference/fp-name-dot-pch-file.md) možnost s **/Yu** možnost zadat název souboru .pch, pokud je název liší od buď argument názvu souboru do **/Yc** nebo základní název zdrojového souboru, jako v následující:  
  
```  
CL /YuMYAPP.H /FpMYPCH.pch PROG.CPP  
```  
  
 Tento příkaz určuje předkompilovaný hlavičkový soubor s názvem MYPCH.pch. Kompilátor používá k obnovení stavu předkompilovaných všechny hlavičky souborů až do a včetně MYAPP.h její obsah. Kompilátor pak zkompiluje kód, který nastane po MYAPP.h **zahrnují** příkaz.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)