---
title: /Qfast_transcendentals (Vynutit rychlé transcendentní objekty)
ms.date: 11/04/2016
f1_keywords:
- /Qfast_transcendentals
helpviewer_keywords:
- /Qfast_transcendentals
- Force Fast Transcendentals
ms.assetid: 4de24bd1-38e6-49d4-9a05-04c9937d24ac
ms.openlocfilehash: 383a915721d627367ca2ca035957df947996bbe2
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818346"
---
# <a name="qfasttranscendentals-force-fast-transcendentals"></a>/Qfast_transcendentals (Vynutit rychlé transcendentní objekty)

generuje kód vloženého Transcendentní funkce.

## <a name="syntax"></a>Syntaxe

```
/Qfast_transcendentals
```

## <a name="remarks"></a>Poznámky

Tato možnost kompilátoru vynutí Transcendentní funkce pro převod na vložený kód, aby se zvýšila rychlost provádění. Tuto možnost má vliv pouze v případě, že je spárovaná s **/FP: except** nebo **/FP: precise**. Generování vloženého kódu pro Transcendentní funkce už je výchozí chování v rámci **Fast**.

Tato možnost není kompatibilní s **/FP: strict**. Zobrazit [/fp (určení chování plovoucí desetinné čárky)](fp-specify-floating-point-behavior.md) Další informace o – možnosti kompilátoru bod s plovoucí desetinnou čárkou.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **příkazového řádku** stránku vlastností.

1. Zadejte možnost do kompilátoru **další možnosti** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[/Q – možnosti (operace nízké úrovně)](q-options-low-level-operations.md)<br/>
[Možnosti kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
