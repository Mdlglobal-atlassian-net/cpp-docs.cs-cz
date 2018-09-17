---
title: -diagnostics (Možnosti diagnostiky kompilátoru) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/11/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /diagnostics
- VC.Project.VCCLCompilerTool.DiagnosticsFormat
dev_langs:
- C++
helpviewer_keywords:
- /diagnostics compiler diagnostic options [C++]
- -diagnostics compiler diagnostic options [C++]
- diagnostics compiler diagnostic options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 97b5e3ef2e5c14ae93d4fcc3b016f4dbc955edbd
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709160"
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

2. V části **vlastnosti konfigurace**, rozbalte **C/C++** složky a vyberte **Obecné** stránku vlastností.

3. Použijte rozevírací seznam ovládacího prvku **formát diagnostiky** možnost zobrazení pole k výběru Diagnostika. Zvolte **OK** nebo **použít** uložte provedené změny.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)