---
title: /Ob (rozbalení vložené funkce)
ms.date: 08/08/2019
f1_keywords:
- VC.Project.VCCLWCECompilerTool.InlineFunctionExpansion
- VC.Project.VCCLCompilerTool.InlineFunctionExpansion
- /ob
helpviewer_keywords:
- inline functions, function expansion compiler option [C++]
- -Ob1 compiler option [C++]
- -Ob0 compiler option [C++]
- /Ob0 compiler option [C++]
- /Ob1 compiler option [C++]
- any suitable compiler option [C++]
- Ob2 compiler option [C++]
- Ob1 compiler option [C++]
- /Ob2 compiler option [C++]
- Ob compiler option [C++]
- -Ob2 compiler option [C++]
- disable compiler option [C++]
- -Ob compiler option [C++]
- /Ob compiler option [C++]
- only __inline compiler option [C++]
- Ob0 compiler option [C++]
- inline expansion, compiler option
ms.assetid: f134e6df-e939-4980-a01d-47425dbc562a
ms.openlocfilehash: 7eb3db1e359349eaf5125a6c8a46a3ac7d847f2f
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915486"
---
# <a name="ob-inline-function-expansion"></a>/Ob (rozbalení vložené funkce)

Ovládá vložené rozšíření funkcí. Ve výchozím nastavení, když se optimalizuje, rozšíření proběhne na uvážení kompilátoru u všech funkcí, které se často označují jako *Automatické vkládání*.

## <a name="syntax"></a>Syntaxe

::: moniker range=">=vs-2019"

> **/Ob** {**0**|12|**3**}|

::: moniker-end

::: moniker range="<=vs-2017"

> **/Ob** {**0**|12|}

::: moniker-end

## <a name="arguments"></a>Arguments

**0,8**\
Výchozí hodnota v rámci [/od](od-disable-debug.md). Zakáže vložená rozšíření.

**1**\
Povoluje rozšíření pouze funkcí označených [](../../cpp/inline-functions-cpp.md)jako inline, [__inline](../../cpp/inline-functions-cpp.md)nebo [__forceinline](../../cpp/inline-functions-cpp.md), nebo v C++ členské funkci definované v deklaraci třídy.

**odst**\
Výchozí hodnota pod [/O1](o1-o2-minimize-size-maximize-speed.md) a [/O2](o1-o2-minimize-size-maximize-speed.md). Umožňuje kompilátoru rozšířit všechny funkce, které nejsou explicitně označené pro žádné vkládání.

::: moniker range=">=vs-2019"

**1**\
Tato možnost určuje více agresivní vkládání než **/Ob2**, ale má stejná omezení. Možnost **/Ob3** je k dispozici od začátku v aplikaci Visual Studio 2019.

::: moniker-end

## <a name="remarks"></a>Poznámky

Kompilátor zpracovává možnosti vloženého rozšíření a klíčová slova jako návrhy. Není nijak zaručeno, že všechny funkce budou rozbaleny na vložené. Můžete zakázat vložená rozšíření, ale nemůžete vynutit, aby kompilátor mohl vložit konkrétní funkci, a to ani `__forceinline` při použití klíčového slova.

Chcete-li vyloučit funkce ze zvážení jako kandidáty na vložené rozšíření, můžete použít [__declspec (vloženou)](../../cpp/noinline.md)nebo oblast označenou [#pragma auto_inline (off)](../../preprocessor/auto-inline.md) a [#pragma auto_inline (on)](../../preprocessor/auto-inline.md) direktivy. Další informace o tom, jak poskytnout pokyny pro vložení do kompilátoru, naleznete v [#pragma vnitřní](../../preprocessor/intrinsic.md) direktiva.

> [!NOTE]
> Informace, které se shromažďují z testovacích běhů, potlačí optimalizace, které by jinak mohly platit, protože jste zadali **/ob**, **/OS**nebo **/ot**. Další informace najdete v tématu [optimalizace na základě profilu](../profile-guided-optimizations.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte stránku vlastností **Konfigurace** > pro**CC++/**  > **optimalizaci** .

1. Upravte vlastnost **rozšíření vložené funkce** .

::: moniker range=">=vs-2019"

Možnost **/Ob3** není k dispozici ve vlastnosti **rozšíření vložené funkce** . Nastavení **/Ob3**:

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte stránku vlastností **Konfigurace** > **C/C++**  > **příkazový řádek** .

1. Do **dalších možností**zadejte **/Ob3** .

::: moniker-end

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.InlineFunctionExpansion%2A>.

## <a name="see-also"></a>Viz také:

[/O – možnosti (optimalizace kódu)](o-options-optimize-code.md)\
[Možnosti kompilátoru MSVC](compiler-options.md)\
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
