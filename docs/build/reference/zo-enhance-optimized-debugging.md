---
title: /Zo (rozšířené optimalizované ladění)
ms.date: 11/04/2016
f1_keywords:
- -Zo
- /Zo
helpviewer_keywords:
- Zo compiler option [C++]
- /Zo compiler option [C++]
- -Zo compiler option [C++]
ms.assetid: eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f
ms.openlocfilehash: 2fb64b0cc39d5b7ff0c96d3eae47197c455526f5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809935"
---
# <a name="zo-enhance-optimized-debugging"></a>/Zo (rozšířené optimalizované ladění)

Generovat rozšířené informace o ladění pro optimalizovaný kód v sestaveních bez ladění.

## <a name="syntax"></a>Syntaxe

```cpp
/Zo[-]
```

## <a name="remarks"></a>Poznámky

**/Zo** přepínač kompilátoru generuje rozšířené informace o ladění pro optimalizovaný kód. Optimalizace může použít registrů pro místní proměnné, změnit pořadí kódu, vektorizovaná smyčky a volání vložených funkcí. Tyto optimalizace může ztížit odhalení zjevného vztah mezi zdrojovým kódem a kompilovaný objektový kód. **/Zo** přepínač instruuje kompilátor, aby generování dalších informací o ladění pro místní proměnné a vložená funkce. Slouží k zobrazení proměnné v **automatické hodnoty**, **lokální**, a **Watch** windows při krokování přes optimalizovaného kódu v ladicím programu sady Visual Studio. Umožňuje také zobrazit vložené funkce v ladicím programu WinDBG trasování zásobníku. Laděná sestavení, které jste zakázali optimalizace ([/Od](od-disable-debug.md)) není nutné další ladicích informací generovaných při **/Zo** je zadán. Použití **/Zo** přepněte na konfiguraci vydání při ladění pomocí optimalizace zapnuté. Další informace o optimalizaci přepínače najdete v tématu [/O možnosti (Optimalizace kódu)](o-options-optimize-code.md). **/Zo** možnost je povolena ve výchozím nastavení v sadě Visual Studio, pokud zadáte ladicí informace s **/zi** nebo **/Z7**. Zadejte **/Zo-** explicitně zakázat tuto – možnost kompilátoru.

**/Zo** přepínač je k dispozici od verze Visual Studio 2013 Update 3 a nahrazuje dříve nedokumentované **/d2Zi+** přepnout.

### <a name="to-set-the-zo-compiler-option-in-visual-studio"></a>Nastavení parametru kompilátoru /Zo v sadě Visual Studio

1. Otevřít **stránky vlastností** dialogové okno pro projekt. Další informace najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace**, **C/C++** složky.

1. Vyberte **příkazového řádku** stránku vlastností.

1. Upravit **další možnosti** vlastnost, aby zahrnovala `/Zo` a klikněte na tlačítko **OK**.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[/O – možnosti (optimalizace kódu)](o-options-optimize-code.md)<br/>
[/Z7, /Zi, /ZI (formát informací o ladění)](z7-zi-zi-debug-information-format.md)<br/>
[Operace Upravit a pokračovat](/visualstudio/debugger/edit-and-continue)
