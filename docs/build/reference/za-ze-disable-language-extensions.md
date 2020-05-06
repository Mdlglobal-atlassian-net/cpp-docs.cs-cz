---
title: /Za, /Ze (Zakázat jazyková rozšíření)
ms.date: 02/19/2019
f1_keywords:
- VC.Project.VCCLWCECompilerTool.DisableLanguageExtensions
- /za
- /ze
- VC.Project.VCCLCompilerTool.DisableLanguageExtensions
helpviewer_keywords:
- -Za compiler option [C++]
- Za compiler option [C++]
- language extensions, disabling in compiler
- -Ze compiler option [C++]
- language extensions
- enable language extensions
- /Za compiler option [C++]
- /Ze compiler option [C++]
- Disable Language Extensions compiler option
- Ze compiler option [C++]
ms.assetid: 65e49258-7161-4289-a176-7c5c0656b1a2
ms.openlocfilehash: 9a2584591f6ca22d6767a5c447ffb72bea0a78ea
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825872"
---
# <a name="za-ze-disable-language-extensions"></a>/Za, /Ze (Zakázat jazyková rozšíření)

Možnost kompilátoru **/za** zakáže a vygeneruje chyby pro rozšíření Microsoftu v jazyce C, které nejsou kompatibilní se standardem ANSI c89/ISO C90. Nepoužívané možnost kompilátoru **/ze** povoluje rozšíření společnosti Microsoft. Ve výchozím nastavení jsou rozšíření společnosti Microsoft povolena.

## <a name="syntax"></a>Syntaxe

> **/Za**\
> **/Ze**

## <a name="remarks"></a>Poznámky

> [!NOTE]
> Použití **/za** při kompilování kódu jako C++ se nedoporučuje. Možnost **/ze** je zastaralá, protože její chování je ve výchozím nastavení zapnuté. Seznam zastaralých možností kompilátoru naleznete v tématu [zastaralé a odebrané možnosti kompilátoru](compiler-options-listed-by-category.md#deprecated-and-removed-compiler-options).

Kompilátor jazyka C/C++ společnosti Microsoft podporuje kompilaci kódu jazyka C dvěma způsoby:

- Kompilátor ve výchozím nastavení používá režim kompilace jazyka C, pokud má zdrojový soubor příponu *C* nebo pokud je zadána možnost [/TC](tc-tp-tc-tp-specify-source-file-type.md) nebo [/TC](tc-tp-tc-tp-specify-source-file-type.md) . Kompilátor jazyka C je kompilátorem c89/C90, který ve výchozím nastavení umožňuje rozšíření společnosti Microsoft pro jazyk C. Další informace o konkrétních rozšířeních najdete v tématu [rozšíření Microsoft pro C a C++](microsoft-extensions-to-c-and-cpp.md). Pokud jsou zadány obě kompilace jazyka C i možnost **/za** , bude kompilátor jazyka c striktně striktně na standard c89/C90. Kompilátor považuje rozšířená klíčová slova společnosti Microsoft jako jednoduché identifikátory, zakáže další rozšíření společnosti Microsoft a automaticky definuje [ \_ \_předdefinované\_ makro STDC](../../preprocessor/predefined-macros.md) pro programy C.

- Kompilátor může kompilovat kód jazyka C v režimu kompilace jazyka C++. Toto chování je výchozí pro zdrojové soubory, které nemají příponu *. c* a při určení možnosti [/TP](tc-tp-tc-tp-specify-source-file-type.md) nebo [/TP](tc-tp-tc-tp-specify-source-file-type.md) . V režimu kompilace C++ kompilátor podporuje tyto části standardů ISO C99 a C11, které byly začleněny do standardu C++. Skoro všechny kódy jazyka C jsou také platný kód C++. Malý počet klíčových slov a konstrukcí kódu jazyka C není platný kód C++, nebo jsou v jazyce C++ interpretovány jinak. Kompilátor se chová v závislosti na standardu C++ v těchto případech. V režimu kompilace jazyka C++ může možnost **/za** způsobit neočekávané chování a nedoporučuje se.

Další možnosti kompilátoru mohou ovlivnit způsob, jakým kompilátor zajišťuje soulad standardů. Způsoby, jak zadat konkrétní standardní nastavení chování jazyka C a C++, naleznete v možnosti kompilátoru [/Zc](zc-conformance.md) . Další standardní nastavení pro normu C++ naleznete v tématu Možnosti kompilátoru [/Permissive-](permissive-standards-conformance.md) a [/STD](std-specify-language-standard-version.md) .

Další informace o problémech shody s Visual C++ naleznete v tématu [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení kompilátoru C++ a vlastností sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. V navigačním podokně vyberte možnost **vlastnosti** > konfigurace**jazyk****C/C++** > .

1. Upravte vlastnost **Zakázat jazykové rozšíření** .

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableLanguageExtensions%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](compiler-options.md)<br/>
[/Zc (shoda)](zc-conformance.md)<br/>
[/permissive- (shoda se standardy)](permissive-standards-conformance.md)<br/>
[/std (určení standardní jazykové verze)](std-specify-language-standard-version.md)<br/>
