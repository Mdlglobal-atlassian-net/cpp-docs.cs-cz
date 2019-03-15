---
title: /GR (Povolit informace běhového typu)
ms.date: 11/04/2016
f1_keywords:
- /gr
- VC.Project.VCCLWCECompilerTool.RuntimeTypeInfo
- VC.Project.VCCLCompilerTool.RuntimeTypeInfo
helpviewer_keywords:
- -Gr compiler option [C++]
- Gr compiler option [C++]
- RTTI compiler option
- /Gr compiler option [C++]
- enable run-time type information compiler option [C++]
ms.assetid: d1f9f850-dcec-49fd-96ef-e72d01148906
ms.openlocfilehash: 15ad453b10fd31de97bbc25f8062e628129076f5
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2019
ms.locfileid: "57820604"
---
# <a name="gr-enable-run-time-type-information"></a>/GR (Povolit informace běhového typu)

Přidává kód pro kontrolu typů objektů v době běhu.

## <a name="syntax"></a>Syntaxe

```
/GR[-]
```

## <a name="remarks"></a>Poznámky

Když **GR** zapnutý, kompilátor definuje `_CPPRTTI` makro preprocesoru. Ve výchozím nastavení **GR** zapnutý. **/GR-** zakáže informace typu za běhu.

Použití **GR** Pokud kompilátor nemůže vyřešit staticky typ objektu, který ve svém kódu. Obvykle potřebujete **GR** při váš kód používá možnost [dynamic_cast – operátor](../../cpp/dynamic-cast-operator.md) nebo [typeid](../../cpp/typeid-operator.md). Ale **GR** zvyšuje velikost souboru .rdata část obrázku. Pokud váš kód nepoužívá **dynamic_cast** nebo **typeid**, **/GR-** může způsobit menší obrázek.

Další informace o kontrole run-time typu, najdete v části [informace o typu za běhu](../../cpp/run-time-type-information.md) v *referenční dokumentace jazyka C++*.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **jazyk** stránku vlastností.

1. Upravit **povolit informace typu za běhu** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeTypeInfo%2A>.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
