---
title: /WINMD (Generování metadat Windows)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadata
ms.assetid: bcfb4901-411e-4c9e-9f78-23028b6e5fcc
ms.openlocfilehash: 93db20d14d3477734e35d33111246f9459310b90
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810364"
---
# <a name="winmd-generate-windows-metadata"></a>/WINMD (Generování metadat Windows)

Povolí generování souboru Windows Runtime Metadata (.winmd).

> **/ WINMD**\[**:**{**NE**\|**POUZE**}]

## <a name="arguments"></a>Arguments

**/ WINMD**<br/>
Výchozí nastavení pro aplikace univerzální platformy Windows. Propojovací program vytvoří binární spustitelný soubor a soubor metadat .winmd.

**/WINMD:NO**<br/>
Linker generuje pouze binární spustitelný soubor, ale nejedná se o soubor winmd.

**/ WINMD: POUZE**<br/>
Linker generuje pouze soubor winmd, ale nikoli binární spustitelný soubor.

## <a name="remarks"></a>Poznámky

**Winmd** – možnost linkeru se používá pro aplikace UWP a součástí prostředí Windows runtime k řízení vytvoření souboru Windows Runtime metadata (.winmd). Soubor winmd je druh knihovny DLL, která obsahuje metadata pro typy Windows runtime a v případě součásti modulu runtime, implementace těchto typů. Řídí metadata [ECMA-335](http://www.ecma-international.org/publications/standards/Ecma-335.htm) standard.

Ve výchozím nastavení, název výstupního souboru má tvar *binaryname*.winmd. Chcete-li zadat jiný název souboru, použijte [/WINMDFILE](winmdfile-specify-winmd-file.md) možnost.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **metadat Windows** stránku vlastností.

1. V **generování metadat Windows** rozevíracího seznamu vyberte požadovanou možnost.

## <a name="see-also"></a>Viz také:

[Návod: Vytvoření součásti jednoduché prostředí Windows Runtime a volání komponenty z jazyka JavaScript](/windows/uwp/winrt-components/walkthrough-creating-a-simple-windows-runtime-component-and-calling-it-from-javascript)<br/>
[Úvod do Microsoft Interface Definition Language 3.0](/uwp/midl-3/intro)<br/>
[/WINMDFILE (určení souboru winmd)](winmdfile-specify-winmd-file.md)<br/>
[/WINMDKEYFILE (určení souboru klíče winmd)](winmdkeyfile-specify-winmd-key-file.md)<br/>
[/WINMDKEYCONTAINER (určení kontejneru klíče)](winmdkeycontainer-specify-key-container.md)<br/>
[/WINMDDELAYSIGN (částečné podepsání souboru winmd)](winmddelaysign-partially-sign-a-winmd.md)<br/>
[Odkaz na MSVC linkeru](linking.md)<br/>
[Možnosti Linkeru MSVC](linker-options.md)
