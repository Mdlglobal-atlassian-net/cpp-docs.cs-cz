---
title: /Qsafe_fp_loads
ms.date: 01/24/2018
ms.openlocfilehash: 57aece79dfab617121371e0489aa80f18e143372
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319327"
---
# <a name="qsafefploads"></a>/Qsafe_fp_loads

Vyžaduje instrukce přesunu celého čísla pro hodnoty s plovoucí desetinnou čárkou a zakáže některé optimalizace zátěže plovoucí desetinné čárky.

## <a name="syntax"></a>Syntaxe

> **/Qsafe_fp_loads**

## <a name="remarks"></a>Poznámky

**/ Qsafe_fp_loads** je dostupná pouze v kompilátorech, jejichž cílem x86; není k dispozici v kompilátorech, které se zaměřují x64 nebo ARM.

**/ Qsafe_fp_loads** vynutí kompilátoru nahrazujícím instrukce přesunu celého čísla s plovoucí desetinnou čárkou přesunout pokyny pro přesun dat mezi pamětí a MMX zaregistruje. Tato možnost také zakáže optimalizaci zatížení registru pro hodnoty s plovoucí desetinnou čárkou, které lze načíst více cest ovládacího prvku, když hodnota může způsobit výjimku při načtení – například hodnotu NaN.

Tato možnost je přepsán [/FP: except](fp-specify-floating-point-behavior.md). **/ Qsafe_fp_loads** určuje podmnožinu chování kompilátoru, která je zadána **/FP: except**.

**/ Qsafe_fp_loads** není kompatibilní s [/CLR](clr-common-language-runtime-compilation.md) a [Fast](fp-specify-floating-point-behavior.md). Další informace o možnostech kompilátoru plovoucího bodu najdete v tématu [/fp (určení chování plovoucí desetinné čárky)](fp-specify-floating-point-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Zadáním možnosti kompilátoru v **další možnosti** pole. Zvolte **OK** na použití změny.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[/Q – možnosti (operace nízké úrovně)](q-options-low-level-operations.md)<br/>
[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
