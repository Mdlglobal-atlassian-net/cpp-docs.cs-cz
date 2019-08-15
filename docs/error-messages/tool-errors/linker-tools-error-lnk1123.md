---
title: Chyba linkerů LNK1123
ms.date: 12/29/2017
f1_keywords:
- LNK1123
helpviewer_keywords:
- LNK1123
ms.openlocfilehash: 31fd634291bfb0af17348197ae8a6225ac490c89
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509910"
---
# <a name="linker-tools-error-lnk1123"></a>Chyba linkerů LNK1123

> Při převodu na COFF došlo k chybě: soubor je neplatný nebo poškozený.

Vstupní soubory musí mít formát formátu COFF (Common Object File Format). Pokud vstupní soubor není COFF, linker se automaticky pokusí převést 32 objektů OMF na COFF nebo spustí CVTRES. EXE pro převod souborů prostředků. Tato zpráva znamená, že linker nemohl převést soubor. K tomu může dojít také při použití nekompatibilní verze CVTRES. EXE z jiné instalace sady Visual Studio, sady Windows Development Kit nebo .NET Framework.

> [!NOTE]
> Pokud používáte starší verzi sady Visual Studio, automatický převod nemusí být podporován.

## <a name="to-fix-the-problem"></a>Řešení problému

- Použijte všechny aktualizace Service Pack a aktualizace pro vaši verzi sady Visual Studio. To je zvláště důležité pro Visual Studio 2010.

- Zkuste sestavit s neaktivovaným přírůstkovým propojením. V panelu nabídek vyberte položku **projekt**, **vlastnosti**. V dialogovém okně **stránky vlastností** rozbalte položku **Vlastnosti konfigurace**, **linker**. Změňte hodnotu **Povolit přírůstkové propojení** na **ne**.

- Ověřte, že verze nástroje CVTRES. Soubor EXE, který se v proměnné prostředí PATH nastavil jako první, odpovídá verzi nástrojů sestavení nebo verzi sady nástrojů platformy, kterou používá váš projekt.

- Zkuste vypnout možnost manifestu pro vložení. V panelu nabídek vyberte položku **projekt**, **vlastnosti**. V dialogovém okně **stránky vlastností** rozbalte položku **Vlastnosti konfigurace**, **Nástroj manifest**, **vstup a výstup**. Změňte hodnotu **manifestu vložení** na **ne**.

- Ujistěte se, že je typ souboru platný. Ujistěte se například, že objekt OMF je 32-bit a není 16bitová. Další informace najdete v tématu [. Soubory obj jako vstup linkeru](../../build/reference/dot-obj-files-as-linker-input.md) a [Formát PE](/windows/win32/Debug/pe-format).

- Ujistěte se, že soubor není poškozený. V případě potřeby ho znovu sestavte.

## <a name="see-also"></a>Viz také:

[Soubory .Obj jako vstup linkeru](../../build/reference/dot-obj-files-as-linker-input.md)<br/>
[EDITBIN – referenční dokumentace](../../build/reference/editbin-reference.md)<br/>
[DUMPBIN – odkaz](../../build/reference/dumpbin-reference.md)
