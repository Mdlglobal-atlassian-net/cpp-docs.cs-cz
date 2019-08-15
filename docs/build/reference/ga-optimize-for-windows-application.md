---
title: /GA (optimalizace pro aplikaci systému Windows)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.OptimizeForWindowsApplication
- /ga
helpviewer_keywords:
- /GA compiler option [C++]
- GA compiler option [C++]
- -GA compiler option [C++]
- Optimize for Windows compiler options
ms.assetid: be97323e-15a0-4836-862c-95980b51926a
ms.openlocfilehash: 85efa03a3f3d267580cbb0442839afb18ac6c313
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492855"
---
# <a name="ga-optimize-for-windows-application"></a>/GA (optimalizace pro aplikaci systému Windows)

Výsledkem je efektivnější kód pro soubor. exe pro přístup k proměnným úložiště místních vláken (TLS).

## <a name="syntax"></a>Syntaxe

```
/GA
```

## <a name="remarks"></a>Poznámky

**/GA** zrychluje přístup k datům deklarovaným pomocí [__declspec (thread)](../../cpp/declspec.md) v programu určeném pro systém Windows. Pokud je tato možnost nastavena, předpokládá se, že je makro [__tls_index](/windows/win32/ProcThread/thread-local-storage) rovno 0.

Použití **/GA** pro knihovnu DLL může mít za následek špatné generování kódu.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na složku **CC++ /a** .

1. Klikněte na stránku vlastností **příkazový řádek** .

1. Zadejte možnost kompilátoru do pole **Další možnosti** .

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
