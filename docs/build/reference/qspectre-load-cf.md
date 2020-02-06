---
title: /Qspectre-load-cf
description: Popisuje možnost Microsoft C/C++ COMPILER (MSVC)/Qspectre-load-cf.
ms.date: 01/28/2020
helpviewer_keywords:
- /Qspectre-load-cf
no-loc:
- Qspectre-load-cf
ms.openlocfilehash: c32b843df517cb6fbe662fba0b592cbf745f1764
ms.sourcegitcommit: 0f4ee9056d65043fa5a715f0ad1031c0ed30e2b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/05/2020
ms.locfileid: "77035520"
---
# /Qspectre-load-cf

Určuje generování kompilátoru pro účely serializace instrukcí pro každou instrukci toku ovládacích prvků, která obsahuje zatížení. Tato možnost provede podmnožinu rizik prováděných možností [/Qspectre-Load](qspectre-load.md) .

## <a name="syntax"></a>Syntaxe

> **/Qspectre-load-cf**

## <a name="remarks"></a>Poznámky

**/Qspectre-load-cf** způsobí, že kompilátor detekuje `JMP`, `RET`a `CALL` instrukcí pro řízení toku, které se načítají z paměti, a vkládání instrukcí k serializaci po načtení. Tam, kde je to možné, jsou tyto pokyny rozděleny do zátěže a přenosu toku řízení. Po zatížení následuje `LFENCE`, aby bylo zajištěno, že je zatížení chráněno. Existují případy, kdy kompilátor nemůže rozdělit instrukce, jako je `JMP` instrukci, aby používala alternativní zmírňující technika. Kompilátor například snižuje `jmp [rax]` přidáním pokynů pro načtení cíle nedestruktivního před vložením prvku LFENCE, jak je znázorněno zde:

```asm
    xor rbx, [rax]
    xor rbx, [rax]  ; force a load of [rax]
    lfence          ; followed by an LFENCE
    jmp [rax]
```

Vzhledem k tomu, že **/Qspectre-load-cf** zastaví spekulativní všechny zátěže v pokynech pro řízení toku, je dopad na výkon vysoký. Zmírňování není vhodné všude. Pokud jsou k dispozici kritické bloky kódu, které nevyžadují ochranu, můžete tato omezení zakázat pomocí `__declspec(spectre(nomitigation))`.

Možnost **Qspectre-load-cf/** je ve výchozím nastavení vypnutá a podporuje všechny úrovně optimalizace.

Možnost **Qspectre-load-cf/** je k dispozici v aplikaci Visual Studio 2019 verze 16,5 a novější. Tato možnost je k dispozici pouze v kompilátorech cílících na procesory x86 a x64. Není k dispozici v kompilátorech, které cílí na procesory ARM.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

2. Vyberte **Vlastnosti konfigurace** > stránka vlastností **generování kódu** **C++ jazyka C/**  > .

3. Vyberte novou hodnotu pro vlastnost **zmírnění rizika Spectre** . Kliknutím na **tlačítko OK** aplikujte změnu.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[/Q možnosti (operace nízké úrovně)](q-options-low-level-operations.md)\
\ [možností kompilátoru MSVC](compiler-options.md)
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
