---
title: /Qspectre-load
description: Popisuje možnost Microsoft C/C++ COMPILER (MSVC)/Qspectre-Load.
ms.date: 01/28/2020
helpviewer_keywords:
- /Qspectre-load
ms.openlocfilehash: a766cf9b7eef11b7c5819cbdaa7706ab5b80c608
ms.sourcegitcommit: 0f4ee9056d65043fa5a715f0ad1031c0ed30e2b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/05/2020
ms.locfileid: "77035527"
---
# <a name="qspectre-load"></a>/Qspectre-load

Určuje generování kompilátoru instrukcí serializace pro každou instrukci načtení. Tato možnost rozšiřuje příznak **/Qspectre** , což snižuje riziko při **útokech na straně stran při vykonávání kanálu** na základě zatížení.

## <a name="syntax"></a>Syntaxe

> **/Qspectre-load**

## <a name="remarks"></a>Poznámky

**/Qspectre-Load** způsobí, že kompilátor detekuje zátěže z paměti a za ně vloží pokyny pro serializaci. Instrukce toku řízení, které načítají paměť, včetně `RET` a `CALL`, jsou rozděleny do zátěže a přenosu toku řízení. Po zatížení následuje `LFENCE`, aby bylo zajištěno, že je zatížení chráněno. K dispozici jsou případy, kdy kompilátor nemůže rozdělit instrukce toku řízení, jako je například instrukce `jmp`, aby používala alternativní zmírňující technika. Kompilátor například snižuje `jmp [rax]` přidáním pokynů pro načtení cíle nedestruktivního před vložením prvku LFENCE, jak je znázorněno zde:

```asm
    xor rbx, [rax]
    xor rbx, [rax]  ; force a load of [rax]
    lfence          ; followed by an LFENCE
    jmp [rax]
```

Vzhledem k tomu, že **/Qspectre-Load** přestane spekulativní všechny zátěže, je dopad na výkon vysoký. Zmírňování není vhodné všude. Pokud jsou k dispozici kritické bloky kódu, které nevyžadují ochranu, můžete tato omezení zakázat pomocí `__declspec(spectre(nomitigation))`. Další informace najdete v tématu [__declspec Spectre](../../cpp/spectre.md).

Možnost **/Qspectre-Load** je ve výchozím nastavení vypnutá a podporuje všechny úrovně optimalizace.

Možnost **/Qspectre-Load** je k dispozici v aplikaci Visual Studio 2019 verze 16,5 a novější. Tato možnost je k dispozici pouze v kompilátorech cílících na procesory x86 a x64. Není k dispozici v kompilátorech, které cílí na procesory ARM.

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
