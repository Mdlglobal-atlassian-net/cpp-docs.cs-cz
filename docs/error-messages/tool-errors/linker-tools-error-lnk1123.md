---
title: Chyba linkerů LNK1123
ms.date: 12/29/2017
f1_keywords:
- LNK1123
helpviewer_keywords:
- LNK1123
ms.openlocfilehash: b67a2a4ddad13988967b7cc7d827862a2a6fe933
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62255226"
---
# <a name="linker-tools-error-lnk1123"></a>Chyba linkerů LNK1123

> Při převodu na COFF došlo k chybě: soubor je neplatný nebo poškozený

Vstupní soubory musí mít formát Common Object File Format (COFF). Pokud vstupní soubor není COFF, linker automaticky pokusí převést objekty omf – 32-bit na COFF nebo spouští CVTRES. Soubor EXE pro převod souborů prostředků. Tato zpráva znamená, že má linker nelze převést soubor. To může dojít také při použití nekompatibilní verze CVTRES. Soubor EXE z jiné instalace sady Visual Studio, sada Windows nebo .NET Framework.

> [!NOTE]
> Pokud používáte starší verzi sady Visual Studio, nemusí být podporované automatického převodu.

## <a name="to-fix-the-problem"></a>Chcete-li vyřešit tento problém

- Použijte všechny aktualizace service Pack a aktualizace pro vaši verzi sady Visual Studio. To je obzvláště důležité pro sadu Visual Studio 2010.

- Vyzkoušejte vytváření s přírůstkovým propojením zakázán. V panelu nabídky zvolte **projektu**, **vlastnosti**. V **stránky vlastností** dialogového okna rozbalte **vlastnosti konfigurace**, **Linkeru**. Změňte hodnotu vlastnosti **Povolit přírůstkové propojení** k **ne**.

- Ověřte, že verze CVTRES. Najít soubor EXE nejprve ve vaší proměnné prostředí PATH odpovídá verzi nástroje pro sestavení nebo verze sady nástrojů platformy použitou vaším projektem.

- Vypněte možnost Vložit Manifest. V panelu nabídky zvolte **projektu**, **vlastnosti**. V **stránky vlastností** dialogového okna rozbalte **vlastnosti konfigurace**, **Nástroj Manifest**, **vstupní a výstupní**. Změňte hodnotu vlastnosti **vložit Manifest** k **ne**.

- Ujistěte se, že je platný typ souboru. Například Ujistěte se, že objekt omf – je 32bitová verze a 16-bit. Další informace najdete v tématu [. Soubory obj jako vstup Linkeru](../../build/reference/dot-obj-files-as-linker-input.md) a [formátu PE](/windows/desktop/Debug/pe-format).

- Ujistěte se, že soubor není poškozen. Sestavení, v případě potřeby.

## <a name="see-also"></a>Viz také:

[Soubory .Obj jako vstup linkeru](../../build/reference/dot-obj-files-as-linker-input.md)<br/>
[EDITBIN – referenční dokumentace](../../build/reference/editbin-reference.md)<br/>
[DUMPBIN – odkaz](../../build/reference/dumpbin-reference.md)
