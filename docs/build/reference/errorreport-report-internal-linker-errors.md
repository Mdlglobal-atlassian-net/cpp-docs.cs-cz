---
title: /ERRORREPORT (sestava s interními chybami linkeru)
description: Referenční příručka k možnostem příkazového řádku Microsoft NMAKE
ms.date: 02/09/2020
f1_keywords:
- /ERRORREPORT
- VC.Project.VCLinkerTool.ErrorReporting
helpviewer_keywords:
- /ERRORREPORT linker option
- ERRORREPORT linker option
- -ERRORREPORT linker option
ms.assetid: f5fab595-a2f1-4eb0-ab5c-1c0fbd3d8c28
ms.openlocfilehash: 5e919d4f7eb59524b9145c8e3e59613e60aef1d2
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257686"
---
# <a name="errorreport-report-internal-linker-errors"></a>/ERRORREPORT (sestava s interními chybami linkeru)

Možnost **/errorreport** je zastaralá. Od Windows Vista se hlášení chyb řídí nastavením [zasílání zpráv o chybách systému Windows (WER)](/windows/win32/wer/windows-error-reporting) .

## <a name="syntax"></a>Syntaxe

> **/Errorreport:** \[ **none** \| **prompt** \| **Queue** \| **Send** ]

## <a name="remarks"></a>Poznámky

Argumenty **/errorreport** jsou přepsané nastavením služby zasílání zpráv o chybách systému Windows. Linker automaticky odesílá společnosti Microsoft zprávy o vnitřních chybách, pokud je generování sestav povoleno pomocí Zasílání zpráv o chybách systému Windows. Pokud je zakázána Zasílání zpráv o chybách systému Windows, není odeslána žádná sestava.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Další informace najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Otevřete **konfigurační vlastnosti** > **linker** > stránce **Upřesnit** vlastnost.

1. Upravte vlastnost **zasílání zpráv o chybách** .

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ErrorReporting%2A>.

## <a name="see-also"></a>Viz také

\ [Referenční příručka linkeru MSVC](linking.md)
[Možnosti linkeru MSVC](linker-options.md)
