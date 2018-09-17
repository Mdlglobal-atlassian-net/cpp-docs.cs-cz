---
title: -GR (povolit informace běhového typu) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /gr
- VC.Project.VCCLWCECompilerTool.RuntimeTypeInfo
- VC.Project.VCCLCompilerTool.RuntimeTypeInfo
dev_langs:
- C++
helpviewer_keywords:
- -Gr compiler option [C++]
- Gr compiler option [C++]
- RTTI compiler option
- /Gr compiler option [C++]
- enable run-time type information compiler option [C++]
ms.assetid: d1f9f850-dcec-49fd-96ef-e72d01148906
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 24ef844c716d64e609440d41bf55db20308c02f1
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712241"
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

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **jazyk** stránku vlastností.

1. Upravit **povolit informace typu za běhu** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeTypeInfo%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)