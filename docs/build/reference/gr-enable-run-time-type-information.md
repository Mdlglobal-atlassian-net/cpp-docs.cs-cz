---
title: /GR (Povolit informace běhového typu)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.RuntimeTypeInfo
- VC.Project.VCCLCompilerTool.RuntimeTypeInfo
helpviewer_keywords:
- -Gr compiler option [C++]
- Gr compiler option [C++]
- RTTI compiler option
- /Gr compiler option [C++]
- enable run-time type information compiler option [C++]
ms.assetid: d1f9f850-dcec-49fd-96ef-e72d01148906
ms.openlocfilehash: ee1398b2f9ee78c62fb84aa591e77708cd0d9d83
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439595"
---
# <a name="gr-enable-run-time-type-information"></a>/GR (Povolit informace běhového typu)

Přidá kód pro kontrolu typů objektů v době běhu.

## <a name="syntax"></a>Syntaxe

```
/GR[-]
```

## <a name="remarks"></a>Poznámky

Když je **/gr** , kompilátor definuje makro preprocesoru `_CPPRTTI`. Ve výchozím nastavení je **/gr** zapnutý. **/Gr-** zakazuje informace o běhovém typu.

Použijte **/gr** , pokud kompilátor nemůže statisticky přeložit typ objektu ve vašem kódu. Obvykle je potřeba možnost **/gr** , když kód používá [operátor dynamic_cast](../../cpp/dynamic-cast-operator.md) nebo [typeid](../../cpp/typeid-operator.md). **/Gr** ale zvětšuje velikost částí. rdata obrázku. Pokud váš kód nepoužívá **dynamic_cast** nebo **typeid**, může **/gr-** vytvořit menší obrázek.

Další informace o kontrole typu za běhu naleznete v tématu [informace o typu běhu](../../cpp/run-time-type-information.md) v  *C++ referenční příručce jazyka*.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na složku **CC++ /a** .

1. Klikněte na stránku vlastností **jazyka** .

1. Upravte vlastnost **Povolit informace o typu běhu** .

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeTypeInfo%2A>.

## <a name="see-also"></a>Viz také

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
