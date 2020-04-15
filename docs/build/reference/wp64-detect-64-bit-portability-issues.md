---
title: /Wp64 (Zjištěny problémy s 64bitovou přenositelností)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.Detect64BitPortabilityProblems
- VC.Project.VCCLCompilerTool.Detect64BitPortabilityProblems
- /wp64
helpviewer_keywords:
- 64-bit compiler [C++], detecting portability problems
- /Wp64 compiler option [C++]
- -Wp64 compiler option [C++]
- Wp64 compiler option [C++]
ms.assetid: 331ae5aa-e627-4d03-8f63-dd2c2d76dadd
ms.openlocfilehash: e5c30ac9096094948a83195f5b3990794c421685
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335887"
---
# <a name="wp64-detect-64-bit-portability-issues"></a>/Wp64 (Zjištěny problémy s 64bitovou přenositelností)

Tato možnost kompilátoru je zastaralá. Ve verzích sady Visual Studio před Visual Studio 2013 to zjistí 64bitové problémy s přenositelností u typů, které jsou také označeny klíčovým slovem [__w64.](../../cpp/w64.md)

## <a name="syntax"></a>Syntaxe

```
/Wp64
```

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení je ve verzích sady Visual Studio před Visual Studio 2013 vypnutá možnost kompilátoru **/Wp64** v kompilátoru MSVC, který vytváří 32bitový kód x86, a v kompilátoru MSVC, který vytváří 64bitový kód x64.

> [!IMPORTANT]
> Možnost kompilátoru [/Wp64](wp64-detect-64-bit-portability-issues.md) a klíčové slovo [__w64](../../cpp/w64.md) jsou zastaralé v sadě Visual Studio 2010 a Visual Studio 2012 a není podporováno od spuštění v sadě Visual Studio 2013. Pokud převedete projekt, který používá tento přepínač, přepínač nebude během převodu migrován. Chcete-li tuto možnost použít v sadě Visual Studio 2010 nebo Visual Studio 2012, musíte zadat přepínač kompilátoru v části **Další možnosti** v části **Příkazový řádek** vlastností projektu. Pokud na příkazovém řádku použijete možnost kompilátoru **/Wp64,** kompilátor vydá upozornění příkazového řádku D9002. Namísto použití této možnosti a klíčového slova ke zjištění problémů s přenositelností 64 bitů použijte kompilátor MSVC, který cílí na 64bitovou platformu a zadejte možnost [/W4.](compiler-option-warning-level.md) Další informace naleznete v [tématu Konfigurace projektů jazyka C++ pro 64bitové cíle x64](../configuring-programs-for-64-bit-visual-cpp.md).

Proměnné následujících typů jsou testovány na 32bitovém operačním systému, jako by byly používány v 64bitovém operačním systému:

- int

- long

- ukazatel

Pokud pravidelně kompiluzujete aplikaci pomocí kompilátoru, který vytváří 64bitový kód x64, můžete jednoduše zakázat **/Wp64** v 32bitových kompilacích, protože 64bitový kompilátor zjistí všechny problémy. Další informace o cílení na 64bitový operační systém windows naleznete v [tématu Konfigurace projektů jazyka C++ pro 64bitové cíle x64](../configuring-programs-for-64-bit-visual-cpp.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **Stránky vlastností** projektu.

   Další informace naleznete [v tématu Nastavení kompilátoru c++ a vlastnosti sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na složku **C/C++.**

1. Klepněte na stránku vlastností **příkazového řádku.**

1. Upravte pole **Další možnosti** tak, aby **obsahovalo parametr /Wp64**.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Detect64BitPortabilityProblems%2A>.

## <a name="see-also"></a>Viz také

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[Konfigurace projektů Jazyka C++ pro 64bitové cíle x64](../configuring-programs-for-64-bit-visual-cpp.md)
