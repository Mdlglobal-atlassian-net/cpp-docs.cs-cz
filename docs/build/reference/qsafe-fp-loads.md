---
title: / Qsafe_fp_loads | Dokumentace Microsoftu
ms.custom: ''
ms.date: 01/24/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0af28b391390f28be4e111b55c909dcae66ca2f8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713658"
---
# <a name="qsafefploads"></a>/Qsafe_fp_loads

Vyžaduje instrukce přesunu celého čísla pro hodnoty s plovoucí desetinnou čárkou a zakáže některé optimalizace zátěže plovoucí desetinné čárky.

## <a name="syntax"></a>Syntaxe

> **/Qsafe_fp_loads**

## <a name="remarks"></a>Poznámky

**/ Qsafe_fp_loads** je dostupná pouze v kompilátorech, jejichž cílem x86; není k dispozici v kompilátorech, které se zaměřují x64 nebo ARM.

**/ Qsafe_fp_loads** vynutí kompilátoru nahrazujícím instrukce přesunu celého čísla s plovoucí desetinnou čárkou přesunout pokyny pro přesun dat mezi pamětí a MMX zaregistruje. Tato možnost také zakáže optimalizaci zatížení registru pro hodnoty s plovoucí desetinnou čárkou, které lze načíst více cest ovládacího prvku, když hodnota může způsobit výjimku při načtení – například hodnotu NaN.

Tato možnost je přepsán [/FP: except](../../build/reference/fp-specify-floating-point-behavior.md). **/ Qsafe_fp_loads** určuje podmnožinu chování kompilátoru, která je zadána **/FP: except**.

**/ Qsafe_fp_loads** není kompatibilní s [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) a [Fast](../../build/reference/fp-specify-floating-point-behavior.md). Další informace o možnostech kompilátoru plovoucího bodu najdete v tématu [/fp (určení chování plovoucí desetinné čárky)](../../build/reference/fp-specify-floating-point-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Zadáním možnosti kompilátoru v **další možnosti** pole. Zvolte **OK** na použití změny.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[/Q – možnosti (operace nízké úrovně)](../../build/reference/q-options-low-level-operations.md)
[– možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)
