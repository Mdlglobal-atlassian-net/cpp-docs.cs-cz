---
title: / Diagnostics (Možnosti diagnostiky kompilátoru)
ms.date: 11/11/2016
f1_keywords:
- /diagnostics
- VC.Project.VCCLCompilerTool.DiagnosticsFormat
helpviewer_keywords:
- /diagnostics compiler diagnostic options [C++]
- -diagnostics compiler diagnostic options [C++]
- diagnostics compiler diagnostic options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 6b7d043e00204fa191530f03bbed069d71a25fc5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293820"
---
# <a name="diagnostics-compiler-diagnostic-options"></a>/ Diagnostics (Možnosti diagnostiky kompilátoru)

Použití **/Diagnostics** – možnost kompilátoru k určení zobrazovat informace o umístění chyby a upozornění.

## <a name="syntax"></a>Syntaxe

```
/diagnostics:{caret|classic|column}
```

## <a name="remarks"></a>Poznámky

Tato možnost je podporována v sadě Visual Studio 2017 nebo novější.

**/Diagnostics** – možnost kompilátoru ovládací prvky zobrazení chyby a upozornění.

**/Diagnostics:classic** je výchozí nastavení, která hlásí pouze číslo řádku ve kterém byl nalezen problém.

**/Diagnostics:column** možnost také obsahuje sloupec, ve kterém byl nalezen problém. To může pomoct identifikovat konkrétní jazykové konstrukce nebo znak, který je příčinou problému.

**/Diagnostics:caret** možnost obsahuje sloupce, kde byl nalezen problém a umístí stříšky (^) v části umístění v řádku kódu, kde byl zjištěn problém.

Všimněte si, že v některých případech, kompilátor nezjistí kde došlo k problému. Chybí středník například nemusí zjistit, dokud byly zjištěny symboly, které neočekávané. Sloupec se použije v hlášení a blikající kurzor je umístěn, kde kompilátor zjistil, že něco pokazilo, což není vždy potřebujete-li provést opravu.

**/Diagnostics** možnost je k dispozici od verze Visual Studio 2017.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete svůj projekt **stránky vlastností** dialogové okno.

1. V části **vlastnosti konfigurace**, rozbalte **C/C++** složky a vyberte **Obecné** stránku vlastností.

1. Použijte rozevírací seznam ovládacího prvku **formát diagnostiky** možnost zobrazení pole k výběru Diagnostika. Zvolte **OK** nebo **použít** uložte provedené změny.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
