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
ms.openlocfilehash: b4b29ed364d39c5f105dded703b8530c08db35e6
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2019
ms.locfileid: "57822090"
---
# <a name="wx-treat-linker-warnings-as-errors"></a>/WX (Zpracovávat upozornění linkeru jako chyby)

```
/WX[:NO]
```

## <a name="remarks"></a>Poznámky

Parametr /WX způsobí, že žádný výstupní soubor, který chcete vygenerovat, pokud linker vydá upozornění.

To se podobá **/WX** kompilátor (naleznete v tématu [/w, /W0, /W1, /W2, w3, / W4, /w1, /w2, w3, / W4, / wall, WD, / jsme Wo, WV, /WX (úroveň upozornění)](compiler-option-warning-level.md) Další informace). Ale zadání **/WX** pro kompilaci, která neznamená **/WX** také bude platit pro fáze propojení; je nutné explicitně zadat **/WX** pro jednotlivé nástroje.

Ve výchozím nastavení **/WX** není platná. Chcete-li zpracovávat upozornění linkeru jako chyby, zadejte **/WX**. **/WX:No** je stejné jako bez zadání **/WX**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **příkazového řádku** stránku vlastností.

1. Zadejte možnost do **další možnosti** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

1. Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Odkaz na MSVC linkeru](linking.md)<br/>
[Možnosti Linkeru MSVC](linker-options.md)
