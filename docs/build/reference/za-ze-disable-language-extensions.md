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
ms.openlocfilehash: 1db1dbdba4829ccf939cdc4f07ccfefe2474a35d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812301"
---
# <a name="za-ze-disable-language-extensions"></a>/Za, /Ze (Zakázat jazyková rozšíření)

**/Za** – možnost kompilátoru zakáže a generuje chyby pro rozšíření Microsoft pro C, které nejsou kompatibilní s ANSI C90 C89/ISO. Zastaralá **/Ze** – možnost kompilátoru umožňuje rozšíření společnosti Microsoft. Ve výchozím nastavení jsou povolena rozšíření společnosti Microsoft.

## <a name="syntax"></a>Syntaxe

> **/Za**<br/>
> **/Ze**

## <a name="remarks"></a>Poznámky

> [!NOTE]
> Použití **/Za** Pokud kód je zkompilován jako C++ nedoporučuje. **/Ze** možnost je zastaralá, protože její chování je ve výchozím. Seznam zastaralých kompilátoru možnosti najdete v tématu [zastaralé funkce a možnosti kompilátoru odebrané](compiler-options-listed-by-category.md#deprecated-and-removed-compiler-options).

Kompilátor Microsoft C/C++ podporuje kompilaci kódu jazyka C dvěma způsoby:

- Kompilátor používá režim kompilace jazyka C ve výchozím nastavení, pokud má zdrojový soubor *.c* rozšíření, nebo když [/Tc](tc-tp-tc-tp-specify-source-file-type.md) nebo [/TC](tc-tp-tc-tp-specify-source-file-type.md) je zadána možnost. Kompilátor jazyka C je C89/C90 kompilátoru, která ve výchozím nastavení, povolí rozšíření jazyka C společnosti Microsoft. Další informace o konkrétní rozšíření najdete v tématu [Extensions Microsoft pro C a C++](microsoft-extensions-to-c-and-cpp.md). Pokud obě kompilace jazyka C a **/Za** jsou zadána možnost, kompilátor jazyka C odpovídá striktně C89/C90 standardu. Kompilátor zpracovává Rozšířená klíčová slova jako identifikátory jednoduché společnosti Microsoft, zakáže ostatní rozšíření společnosti Microsoft a automaticky definuje [ \_ \_STDC\_ \_ ](../../preprocessor/predefined-macros.md) předdefinované makra pro programy C.

- Kompilátor může kompilaci kódu jazyka C v režimu kompilace jazyka C++. Toto chování je výchozí nastavení pro zdrojové soubory, které nemají *.c* rozšíření a kdy [/Tp](tc-tp-tc-tp-specify-source-file-type.md) nebo [/TP](tc-tp-tc-tp-specify-source-file-type.md) je zadána možnost. V režimu kompilace jazyka C++ kompilátor podporuje tyto části ISO C99 a C11 standardy, které byly zahrnuty do C++ standard. Téměř všechny kódu jazyka C je také platný kód jazyka C++. Malý počet klíčová slova jazyka C a konstrukce kódu není platný kód jazyka C++, nebo se interpretují odlišně v jazyce C++. Kompilátor se chová podle standardu v těchto případech C++. V režimu kompilace jazyka C++ **/Za** možnost může způsobit neočekávané chování a nedoporučuje se používat.

Další možnosti kompilátoru může ovlivnit, jak kompilátor pak zajistí shoda se standardy. Způsoby, jak určit konkrétní standard jazyka C a C++ chování nastavení, najdete v článku [/Zc](zc-conformance.md) – možnost kompilátoru. Další nastavení shody standard C++, naleznete v tématu [/ permissive-](permissive-standards-conformance.md) a [/std](std-specify-language-standard-version.md) – možnosti kompilátoru.

Další informace o problémech přizpůsobení v aplikaci Visual C++, naleznete v tématu [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. V navigačním podokně zvolte **vlastnosti konfigurace** > **C/C++** > **jazyka**.

1. Upravit **zakázat jazyková rozšíření** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableLanguageExtensions%2A>.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru](compiler-options.md)<br/>
[/Zc (shoda)](zc-conformance.md)<br/>
[/permissive- (shoda se standardy)](permissive-standards-conformance.md)<br/>
[/std (určení standardní jazykové verze)](std-specify-language-standard-version.md)<br/>
