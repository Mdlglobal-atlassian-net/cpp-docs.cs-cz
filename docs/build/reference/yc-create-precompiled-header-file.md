---
title: /Yc (Vytvořit předkompilovaný hlavičkový soubor)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.UsePrecompiledHeader
- /yc
- VC.Project.VCCLWCECompilerTool.PrecompiledHeaderThrough
- VC.Project.VCCLWCECompilerTool.UsePrecompiledHeader
- VC.Project.VCCLCompilerTool.PrecompiledHeaderThrough
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- .pch files, creating
- -Yc compiler option [C++]
- /Yc compiler option [C++]
- Yc compiler option [C++]
ms.assetid: 47c2e555-b4f5-46e6-906e-ab5cf21f0678
ms.openlocfilehash: 71a05df3adc74edfd814bb6dc15121e4a343dc4d
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825753"
---
# <a name="yc-create-precompiled-header-file"></a>/Yc (Vytvořit předkompilovaný hlavičkový soubor)

Instruuje kompilátor, aby vytvořil soubor předkompilované hlavičky (. pch), který představuje stav kompilace v určitém bodě.

## <a name="syntax"></a>Syntaxe

> __/YC__\
> __/Yc__*Název souboru* /YC

## <a name="arguments"></a>Argumenty

*Bitmap*<br/>
Určuje soubor hlaviček (. h). Při použití tohoto argumentu zkompiluje kompilátor veškerý kód do souboru. h včetně.

## <a name="remarks"></a>Poznámky

Při zadání **/YC** bez argumentu zkompiluje kompilátor všechny kódy až do konce základního zdrojového souboru nebo do bodu v základní souboru, kde se nachází direktiva [hdrstop](../../preprocessor/hdrstop.md) . Výsledný soubor. pch má stejný základní název jako základní zdrojový soubor, pokud neurčíte jiný název souboru pomocí direktivy pragma **hdrstop** nebo možnosti **/FP** .

Předkompilovaný kód je uložen v souboru s názvem vytvořeným ze základního názvu souboru zadaného s možností **/YC** a příponou. pch. Můžete také použít [/FP (název. Soubor PCH)](fp-name-dot-pch-file.md) pro určení názvu předkompilované hlavičkového souboru.

Použijete-li*název souboru* __/YC__, kompilátor zkompiluje veškerý kód do a včetně zadaného souboru pro následné použití pomocí možnosti [/Yu (použít předkompilovaný hlavičkový soubor)](yu-use-precompiled-header-file.md) .

Pokud dojde k parametrům __/YC__*filename* a __/Yu__*filename* na stejném příkazovém řádku a na obou odkazech nebo implikuje stejný název souboru, __/Yc__*má přednost/YC název souboru* . Tato funkce zjednodušuje psaní souborů pravidel.

Další informace o předkompilovaných hlavičkách naleznete v tématu:

- [/Y (předkompilované hlavičky)](y-precompiled-headers.md)

- [Předkompilované hlavičkové soubory](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Vyberte soubor. cpp. Soubor. cpp musí #include soubor. h obsahující informace předkompilované hlavičky. Nastavení **/YC** projektu lze přepsat na úrovni souboru.

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení kompilátoru C++ a vlastností sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Otevřete stránku **Vlastnosti konfigurace**, **C/C++**, stránka vlastností **předkompilované hlavičky** .

1. Upravte vlastnost **předkompilované hlavičky** .

1. Chcete-li nastavit název souboru, upravte vlastnost **souboru předkompilované hlavičky** .

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A> a <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>.

## <a name="example"></a>Příklad

Uvažujte následující kód:

```cpp
// prog.cpp
// compile with: cl /c /Ycmyapp.h prog.cpp
#include <afxwin.h>   // Include header for class library
#include "resource.h" // Include resource definitions
#include "myapp.h"    // Include information specific to this app
// ...
```

Pokud je tento kód kompilován pomocí příkazu `CL /YcMYAPP.H PROG.CPP`, kompilátor uloží všechny předzpracování pro afxwin. h, Resource. h a MyApp. h v souboru předkompilované hlavičky s názvem MyApp. pch.

## <a name="see-also"></a>Viz také

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[Předkompilované hlavičkové soubory](../creating-precompiled-header-files.md)
