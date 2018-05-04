---
title: /Zc:forScope (vynutit dodržování pro obor cyklu for) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.ForceConformanceInForLoopScope
- VC.Project.VCCLWCECompilerTool.ForceConformanceInForLoopScope
- /zc:forScope
dev_langs:
- C++
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: 3031f02d-3b14-4ad0-869e-22b0110c3aed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b21c844cd29c7fb45e58f44fdf8eaae427b74235
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="zcforscope-force-conformance-in-for-loop-scope"></a>/Zc:forScope (Vynutit dodržování standardu pro obor cyklu for)

Použít k implementaci standardní C++ chování pro [pro](../../cpp/for-statement-cpp.md) smyčky s rozšíření Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)).

## <a name="syntax"></a>Syntaxe

> **/Zc:forScope**[**-**]

## <a name="remarks"></a>Poznámky

Standardní chování je umožnit **pro** smyčky na inicializátoru se dostala mimo rozsah po **pro** smyčky. V části **/Zc:forScope-** a [/Ze](../../build/reference/za-ze-disable-language-extensions.md), **pro** smyčky na inicializátoru zůstane v oboru, dokud nebude končí místní rozsah.

**/Zc:forScope** možnost ve výchozím nastavení zapnutý. **/Zc:forScope** při nemá vliv [/ projektovou-](permissive-standards-conformance.md) je zadána možnost.

**/Zc:forScope-** možnost je zastaralá a bude v budoucí verzi odebrána. Použití **/Zc:forScope-** generuje upozornění D9035 vyřazení.

Následující kód zkompiluje pod **/Ze** , ale není v **/Za**:

```cpp
// zc_forScope.cpp
// compile by using: cl /Zc:forScope- /Za zc_forScope.cpp
// C2065, D9035 expected  
int main() {
    // Compile by using cl /Zc:forScope- zc_forScope.cpp
    // to compile this non-standard code as-is.
    // Uncomment the following line to resolve C2065 for /Za.
    // int i;
    for (int i = 0; i < 1; i++)
        ;
    i = 20;   // i has already gone out of scope under /Za
}
```

Pokud používáte **/Zc:forScope-**, upozornění C4288 (ve výchozím nastavení vypnuté) se vygeneruje, pokud je proměnná v oboru z důvodu deklaraci, která byla vytvořená v předchozím oboru. Ukazuje to odebrat `//` znaky v kódu příklad deklarovat `int i`.

Můžete změnit chování běhové **/Zc:forScope** pomocí [odpovídat](../../preprocessor/conform.md) – Direktiva pragma.

Pokud používáte **/Zc:forScope-** v projektu, který má existující soubor .pch, se generuje upozornění, **/Zc:forScope-** je ignorován a pokračuje kompilace pomocí stávající soubory. Pokud chcete vygenerovat nový soubor .pch, použijte [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](../../build/reference/yc-create-precompiled-header-file.md).

Další informace o problémech shoda v jazyce Visual C++, najdete v části [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **jazyk** stránku vlastností.

1. Změnit **vynutit dodržování pro obor cyklu for** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForceConformanceInForLoopScope%2A>.

## <a name="see-also"></a>Viz také

[/Zc (shoda)](../../build/reference/zc-conformance.md)<br/>
[/Za, /Ze (zakázání jazykových rozšíření)](../../build/reference/za-ze-disable-language-extensions.md)<br/>
