---
title: /errorReport (sestava s interními chybami kompilátoru)
description: Referenční informace pro možnost příkazovéhoC++ řádku Microsoft C/kompilátor/errorreport
ms.date: 02/09/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.ErrorReporting
helpviewer_keywords:
- /errorReport compiler option [C++]
- -errorReport compiler option [C++]
ms.assetid: 819828f8-b0a5-412c-9c57-bf822f17e667
ms.openlocfilehash: afc366728e62029ffbd3993e2fdd740e3aaf3369
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439895"
---
# <a name="errorreport-report-internal-compiler-errors"></a>/errorReport (sestava s interními chybami kompilátoru)

> [!NOTE]
> Možnost **/errorreport** je zastaralá. Od Windows Vista se hlášení chyb řídí nastavením [zasílání zpráv o chybách systému Windows (WER)](/windows/win32/wer/windows-error-reporting) .

## <a name="syntax"></a>Syntaxe

> **/errorreport:** \[**none** \| **prompt** \| **Queue** \| **Send** ]

## <a name="remarks"></a>Poznámky

Vnitřní chyba kompilátoru (ICE) má za následek, že kompilátor nemůže zpracovat soubor zdrojového kódu. Když dojde k ICE, kompilátor nevytvoří výstupní soubor nebo žádnou užitečnou diagnostiku, kterou můžete použít k opravě kódu.

Argumenty **/errorreport** jsou přepsané nastavením služby zasílání zpráv o chybách systému Windows. Kompilátor automaticky odesílá společnosti Microsoft zprávy o vnitřních chybách, pokud je generování sestav povoleno pomocí Zasílání zpráv o chybách systému Windows. Pokud je zakázána Zasílání zpráv o chybách systému Windows, není odeslána žádná sestava.


### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Další informace najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Otevřete stránku **Vlastnosti konfigurace** > stránce **Upřesnit** vlastnost **C++ C/**  > .

1. Upravte vlastnost **zasílání zpráv o chybách** .

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ErrorReporting%2A>.

## <a name="see-also"></a>Viz také

\ [možností kompilátoru MSVC](compiler-options.md)
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
