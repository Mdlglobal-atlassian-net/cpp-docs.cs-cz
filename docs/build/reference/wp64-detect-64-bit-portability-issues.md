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
ms.openlocfilehash: 5a3cdaf85fa4dc05ece54fc630cb69fc93650e6b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316545"
---
# <a name="wp64-detect-64-bit-portability-issues"></a>/Wp64 (Zjištěny problémy s 64bitovou přenositelností)

Tato možnost kompilátoru je zastaralý. Ve verzích sady Visual Studio před Visual Studio 2013, to zjistí problémy přenositelnosti na 64-bit na typy, které jsou také označené [__w64](../../cpp/w64.md) – klíčové slovo.

## <a name="syntax"></a>Syntaxe

```
/Wp64
```

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení ve verzích sady Visual Studio před Visual Studio 2013 **/Wp64** – možnost kompilátoru je vypnuté v, který vytváří x86 32-bit kompilátor MSVC kódu v kompilátoru MSVC, která sestavení a 64-bit, x64 kódu.

> [!IMPORTANT]
>  [/Wp64](wp64-detect-64-bit-portability-issues.md) – možnost kompilátoru a [__w64](../../cpp/w64.md) – klíčové slovo se považují za zastaralé v sadě Visual Studio 2010 a Visual Studio 2012 a nepodporuje se spouští v sadě Visual Studio 2013. Pokud převedete projekt, který používá tento přepínač, nebude se migrovat přepínač během převodu. Tato možnost dala použít v sadě Visual Studio 2010 nebo Visual Studio 2012, je nutné zadat přepínač kompilátoru pod **další možnosti** v **příkazového řádku** části Vlastnosti projektu. Pokud používáte **/Wp64** – možnost kompilátoru na příkazovém řádku, kompilátor vydá upozornění D9002 příkazového řádku. Namísto použití této možnosti a klíčového slova ke zjišťování problémů přenositelnosti na 64-bit, použijte kompilátor MSVC, který cílí na 64bitovou platformu a zadejte [/W4](compiler-option-warning-level.md) možnost. Další informace najdete v tématu [projekty konfigurace C++ pro 64bitové x64 cíle](../configuring-programs-for-64-bit-visual-cpp.md).

Proměnné z následujících typů jsou testovány v 32bitové verzi operačního systému, jako kdyby byly používány na 64bitový operační systém:

- int

- long

- ukazatel

Pokud kompilujete aplikace pravidelně pomocí kompilátoru, který vytváří 64-bit, x64 kódu, můžete jenom zakázat **/Wp64** do vaší 32bitové kompilace protože 64-bit kompilátor rozpozná všechny problémy. Další informace o tom, jak Windows 64-bit cílový operační systém najdete v tématu [projekty konfigurace C++ pro 64bitové x64 cíle](../configuring-programs-for-64-bit-visual-cpp.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete projekt **stránky vlastností** dialogové okno.

   Další informace najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **příkazového řádku** stránku vlastností.

1. Upravit **další možnosti** pole zahrnout **/Wp64**.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Detect64BitPortabilityProblems%2A>.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[Konfigurace projektů C++ pro 64bitové, x64 cíle](../configuring-programs-for-64-bit-visual-cpp.md)
