---
title: /Zc:forScope (Vynutit dodržování standardu pro obor cyklu for)
ms.date: 03/06/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.ForceConformanceInForLoopScope
- VC.Project.VCCLWCECompilerTool.ForceConformanceInForLoopScope
- /zc:forScope
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: 3031f02d-3b14-4ad0-869e-22b0110c3aed
ms.openlocfilehash: 7f98667d3a771994d1b4e54b429f42cb566c102c
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810248"
---
# <a name="zcforscope-force-conformance-in-for-loop-scope"></a>/Zc:forScope (Vynutit dodržování standardu pro obor cyklu for)

Používaný k implementaci standardního chování jazyka C++ pro [pro](../../cpp/for-statement-cpp.md) cykly s rozšířeními společnosti Microsoft ([/Ze](za-ze-disable-language-extensions.md)).

## <a name="syntax"></a>Syntaxe

> **/Zc:forScope**[**-**]

## <a name="remarks"></a>Poznámky

Standardní chování je umožnit **pro** smyčky inicializátor dostanou mimo rozsah po **pro** smyčky. V části **/Zc:forScope-** a [/Ze](za-ze-disable-language-extensions.md), **pro** smyčky inicializátor zůstává v oboru až do ukončení místní rozsah.

**/Zc: forscope** možnost zapnutá ve výchozím nastavení. **/ Zc: forscope** při nemá vliv [/ permissive-](permissive-standards-conformance.md) je zadána možnost.

**/Zc:forScope-** možnost je zastaralá a bude v budoucí verzi odebrána. Použití **/Zc:forScope-** vygeneruje upozornění D9035 vyřazení.

Následující kód se zkompiluje podle **/Ze** ale nenachází v **/Za**:

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

Pokud používáte **/Zc:forScope-**, upozornění C4288 (ve výchozím nastavení vypnuté) je generována, pokud je proměnná v oboru z důvodu deklarace, která byla vytvořená v předchozím oboru. Chcete-li to ukazuje, odeberte `//` znaků v příkladu kódu pro deklaraci `int i`.

Můžete změnit chování za běhu **/Zc: forscope** pomocí [odpovídat](../../preprocessor/conform.md) direktivy pragma.

Pokud používáte **/Zc:forScope-** v projektu, který má existující soubor .pch, vygeneruje se upozornění, **/Zc:forScope-** se ignoruje, a pokračuje v kompilaci pomocí existující soubory .pch. Pokud chcete vygenerovat nový soubor .pch, použijte [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](yc-create-precompiled-header-file.md).

Další informace o problémech přizpůsobení v aplikaci Visual C++, naleznete v tématu [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **jazyk** stránku vlastností.

1. Upravit **vynutit dodržování standardu pro obor cyklu for** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForceConformanceInForLoopScope%2A>.

## <a name="see-also"></a>Viz také:

[/Zc (shoda)](zc-conformance.md)<br/>
[/Za, /Ze (zakázání jazykových rozšíření)](za-ze-disable-language-extensions.md)<br/>
