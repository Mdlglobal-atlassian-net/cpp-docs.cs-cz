---
title: /WX (Zpracovávat upozornění linkeru jako chyby)
ms.date: 11/04/2016
f1_keywords:
- /WX
helpviewer_keywords:
- /WX linker option
- -WX linker option
- WX linker option
ms.assetid: e4ba97c7-93f7-43ae-a4bb-d866790926c9
ms.openlocfilehash: fa7b651d2a884e25a9b0e6f1ba824d082c3c01bc
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57412639"
---
# <a name="wx-treat-linker-warnings-as-errors"></a>/WX (Zpracovávat upozornění linkeru jako chyby)

```
/WX[:NO]
```

## <a name="remarks"></a>Poznámky

Parametr /WX způsobí, že žádný výstupní soubor, který chcete vygenerovat, pokud linker vydá upozornění.

To se podobá **/WX** kompilátor (naleznete v tématu [/w, /W0, /W1, /W2, w3, / W4, /w1, /w2, w3, / W4, / wall, WD, / jsme Wo, WV, /WX (úroveň upozornění)](../../build/reference/compiler-option-warning-level.md) Další informace). Ale zadání **/WX** pro kompilaci, která neznamená **/WX** také bude platit pro fáze propojení; je nutné explicitně zadat **/WX** pro jednotlivé nástroje.

Ve výchozím nastavení **/WX** není platná. Chcete-li zpracovávat upozornění linkeru jako chyby, zadejte **/WX**. **/WX:No** je stejné jako bez zadání **/WX**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **příkazového řádku** stránku vlastností.

1. Zadejte možnost do **další možnosti** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

1. Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)
