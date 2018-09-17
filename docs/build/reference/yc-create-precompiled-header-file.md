---
title: -Yc (vytvoření předkompilovaného hlavičkového souboru) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- devlang-cpp
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.UsePrecompiledHeader
- /yc
- VC.Project.VCCLWCECompilerTool.PrecompiledHeaderThrough
- VC.Project.VCCLWCECompilerTool.UsePrecompiledHeader
- VC.Project.VCCLCompilerTool.PrecompiledHeaderThrough
dev_langs:
- C++
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- .pch files, creating
- -Yc compiler option [C++]
- /Yc compiler option [C++]
- Yc compiler option [C++]
ms.assetid: 47c2e555-b4f5-46e6-906e-ab5cf21f0678
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5288e748956a405073697ddd7331a73b95d8650
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714243"
---
# <a name="yc-create-precompiled-header-file"></a>/Yc (Vytvořit předkompilovaný hlavičkový soubor)

Dává pokyn kompilátoru k vytvoření souboru předkompilované hlavičky (pch), který představuje stav kompilace v určitém bodě.

## <a name="syntax"></a>Syntaxe

> __/Yc__
>  __/Yc__*název souboru*

## <a name="arguments"></a>Arguments

*Název souboru*<br/>
Určuje soubor hlaviček (.h). Pokud tento argument se používá, kompilátor zkompiluje veškerého kódu až po a .h souborů.

## <a name="remarks"></a>Poznámky

Při **/Yc** je zadán bez argumentu, kompilátor zkompiluje veškerého kódu až po end základní zdrojového souboru nebo do bodu v souboru základní kde [hdrstop](../../preprocessor/hdrstop.md) vyvolá směrnice. Výsledný soubor .pch má stejný základní název jako základní zdrojový soubor, pokud neurčíte název jiného souboru pomocí **hdrstop** – Direktiva pragma nebo **/FP** možnost.

Předkompilovaný kód je uloží do souboru s názvem vytvořené ze základní název souboru zadaný **/Yc** možnost a příponou .pch. Můžete také použít [/Fp (název. Soubor pch)](../../build/reference/fp-name-dot-pch-file.md) můžete zadat název předkompilovaného souboru hlaviček.

Pokud používáte __/Yc__*filename*, kompilátor zkompiluje veškerého kódu do a včetně zadaného souboru pro pozdější použití s [/Yu (Použít předkompilovaný hlavičkový soubor)](../../build/reference/yu-use-precompiled-header-file.md) možnost.

Pokud možnosti __/Yc__*filename* a __/Yu__*filename* vyskytovat na stejném příkazovém řádku a obě odkazovat, ani z nich nevyplývají stejný název souboru __/Yc__*filename* přednost. Tato funkce zjednodušuje psaní soubory pravidel.

Další informace o předkompilovaných hlaviček naleznete v tématu:

- [/Y (předkompilované hlavičky)](../../build/reference/y-precompiled-headers.md)

- [Vytváření předkompilovaných hlavičkových souborů](../../build/reference/creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Vyberte soubor .cpp. Soubor .cpp musí #include souboru .h, který obsahuje informace pro předkompilované hlavičky. V projektu **/Yc** nastavení můžete přepsat na úrovni souboru.

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Otevřít **vlastnosti konfigurace**, **C/C++**, **předkompilované hlavičky** stránku vlastností.

1. Upravit **předkompilovaných hlaviček** vlastnost.

1. Pokud chcete nastavit název souboru, upravte **předkompilovaný soubor hlaviček** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A> a <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>.

## <a name="example"></a>Příklad

Vezměte v úvahu následující kód:

```cpp
// prog.cpp
// compile with: cl /c /Ycmyapp.h prog.cpp
#include <afxwin.h>   // Include header for class library
#include "resource.h" // Include resource definitions
#include "myapp.h"    // Include information specific to this app
// ...
```

Když tento kód je zkompilován pomocí příkazu `CL /YcMYAPP.H PROG.CPP`, kompilátor uloží všechny předzpracování pro AFXWIN.h RESOURCE.h, a volá MYAPP.pch MYAPP.h v souboru předkompilované hlavičky.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)<br/>
[Vytváření předkompilovaných hlavičkových souborů](../../build/reference/creating-precompiled-header-files.md)