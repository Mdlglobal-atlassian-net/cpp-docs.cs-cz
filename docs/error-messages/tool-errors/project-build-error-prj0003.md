---
title: Chyba sestavení projektu PRJ0003 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0003
dev_langs:
- C++
helpviewer_keywords:
- PRJ0003
ms.assetid: fc5a84bb-c6d3-41d6-8dd6-475455820778
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3d1a23b8171c916b05df1d715f803893ab0720e6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053814"
---
# <a name="project-build-error-prj0003"></a>Chyba sestavení projektu PRJ0003

> Chyba vytváření podřízeného procesu "*příkazového řádku*".

*Příkazového řádku* příkaz vytvořený ze vstupu v **stránky vlastností** dialogové okno vrátil kód chyby, ale v neobjevují žádné informace **výstup** okna.

Mezi možné důvody této chyby patří:

- Váš projekt závisí na ATL Server. Od v sadě Visual Studio 2008, ATL Server již není součástí sady Visual Studio, ale byl vydán jako projekt sdílený zdroj na webu CodePlex. Chcete-li stáhnout zdrojový kód ATL Server a nástroje, přejděte na [ATL Server knihovny a nástroje](http://go.microsoft.com/fwlink/p/?linkid=81979).

- Nedostatek systémových prostředků. Ukončete některé aplikace chcete tento problém vyřešit.

- Nedostatečná oprávnění. Ověřte, že máte dostatečná oprávnění.

- Spustitelný soubor cesty zadané v **adresáře VC ++** neobsahují cestu pro nástroj, který se pokoušíte spustit. Informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md)

- Pro projekty souborů pravidel, jsou chybějící příkaz pro spuštění buď **sestavení příkazového řádku** nebo **opětovné sestavení příkazového řádku**.

## <a name="see-also"></a>Viz také

[Chyby a upozornění sestavení projektu (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)