---
title: Chyba sestavení projektu PRJ0003
ms.date: 11/04/2016
f1_keywords:
- PRJ0003
helpviewer_keywords:
- PRJ0003
ms.assetid: fc5a84bb-c6d3-41d6-8dd6-475455820778
ms.openlocfilehash: 00d101e62d49078ebfcfff9455497f30224b84fe
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039503"
---
# <a name="project-build-error-prj0003"></a>Chyba sestavení projektu PRJ0003

> Chyba vytváření podřízeného procesu "*příkazového řádku*".

*Příkazového řádku* příkaz vytvořený ze vstupu v **stránky vlastností** dialogové okno vrátil kód chyby, ale v neobjevují žádné informace **výstup** okna.

Mezi možné důvody této chyby patří:

- Váš projekt závisí na ATL Server. Od v sadě Visual Studio 2008, ATL Server již není součástí sady Visual Studio, ale byl vydán jako projekt sdílený zdroj na webu CodePlex. Chcete-li stáhnout zdrojový kód ATL Server a nástroje, přejděte na [ATL Server knihovny a nástroje](http://go.microsoft.com/fwlink/p/?linkid=81979).

- Nedostatek systémových prostředků. Ukončete některé aplikace chcete tento problém vyřešit.

- Nedostatečná oprávnění. Ověřte, že máte dostatečná oprávnění.

- Spustitelný soubor cesty zadané v **adresáře VC ++** neobsahují cestu pro nástroj, který se pokoušíte spustit. Informace najdete v tématu [nastavení kompilátoru a vlastnosti sestavení](../../build/working-with-project-properties.md)

- Pro projekty souborů pravidel, jsou chybějící příkaz pro spuštění buď **sestavení příkazového řádku** nebo **opětovné sestavení příkazového řádku**.

## <a name="see-also"></a>Viz také:

[Chyby a upozornění sestavení projektu (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)