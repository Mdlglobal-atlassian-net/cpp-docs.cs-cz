---
title: -Zo (rozšířené optimalizované ladění) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- -Zo
- /Zo
dev_langs:
- C++
helpviewer_keywords:
- Zo compiler option [C++]
- /Zo compiler option [C++]
- -Zo compiler option [C++]
ms.assetid: eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8e93d8debbab26dc61b4c27de713b94d7bc6c417
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711942"
---
# <a name="zo-enhance-optimized-debugging"></a>/Zo (rozšířené optimalizované ladění)

Generovat rozšířené informace o ladění pro optimalizovaný kód v sestaveních bez ladění.

## <a name="syntax"></a>Syntaxe

```cpp
/Zo[-]
```

## <a name="remarks"></a>Poznámky

**/Zo** přepínač kompilátoru generuje rozšířené informace o ladění pro optimalizovaný kód. Optimalizace může použít registrů pro místní proměnné, změnit pořadí kódu, vektorizovaná smyčky a volání vložených funkcí. Tyto optimalizace může ztížit odhalení zjevného vztah mezi zdrojovým kódem a kompilovaný objektový kód. **/Zo** přepínač instruuje kompilátor, aby generování dalších informací o ladění pro místní proměnné a vložená funkce. Slouží k zobrazení proměnné v **automatické hodnoty**, **lokální**, a **Watch** windows při krokování přes optimalizovaného kódu v ladicím programu sady Visual Studio. Umožňuje také zobrazit vložené funkce v ladicím programu WinDBG trasování zásobníku. Laděná sestavení, které jste zakázali optimalizace ([/Od](../../build/reference/od-disable-debug.md)) není nutné další ladicích informací generovaných při **/Zo** je zadán. Použití **/Zo** přepněte na konfiguraci vydání při ladění pomocí optimalizace zapnuté. Další informace o optimalizaci přepínače najdete v tématu [/O možnosti (Optimalizace kódu)](../../build/reference/o-options-optimize-code.md). **/Zo** možnost je povolena ve výchozím nastavení v sadě Visual Studio, pokud zadáte ladicí informace s **/zi** nebo **/Z7**. Zadejte **/Zo-** explicitně zakázat tuto – možnost kompilátoru.

**/Zo** přepínač je k dispozici od verze Visual Studio 2013 Update 3 a nahrazuje dříve nedokumentované **/d2Zi+** přepnout.

### <a name="to-set-the-zo-compiler-option-in-visual-studio"></a>Nastavení parametru kompilátoru /Zo v sadě Visual Studio

1. Otevřít **stránky vlastností** dialogové okno pro projekt. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace**, **C/C++** složky.

1. Vyberte **příkazového řádku** stránku vlastností.

1. Upravit **další možnosti** vlastnost, aby zahrnovala `/Zo` a klikněte na tlačítko **OK**.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[/O možnosti (Optimalizace kódu)](../../build/reference/o-options-optimize-code.md)
[/Z7, / zi, /ZI (formát ladicích informací)](../../build/reference/z7-zi-zi-debug-information-format.md)
[upravit a pokračovat](/visualstudio/debugger/edit-and-continue)