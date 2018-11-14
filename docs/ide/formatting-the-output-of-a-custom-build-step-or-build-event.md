---
title: Formátovaní výstupu vlastního kroku sestavení nebo události sestavení
ms.date: 08/27/2018
helpviewer_keywords:
- builds [C++], build events
- custom build steps [C++], output format
- events [C++], build
- build events [C++], output format
- build steps [C++], output format
- builds [C++], custom build steps
ms.assetid: 92ad3e38-24d7-4b89-90e6-5a16f5f998da
ms.openlocfilehash: 333d3af92da2388b42f51f197dee5da82900022d
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51330408"
---
# <a name="formatting-the-output-of-a-custom-build-step-or-build-event"></a>Formátovaní výstupu vlastního kroku sestavení nebo události sestavení

Pokud výstupu vlastního kroku sestavení nebo události sestavení je správný, uživatelé, získáte následující výhody:

- Upozornění a chyby se počítají v **výstup** okna.

- Výstup se zobrazí v **seznamu úkolů** okna.

- Kliknutím na výstup v **výstup** okně zobrazí příslušné téma.

- Jsou povoleny operace F1 v **seznamu úkolů** okno nebo **výstup** okna.

Formát výstupu by měl být:

> {<em>filename</em>**(**<em>řádek #</em> \[ **,** <em>sloupec #</em>]**)** &#124; *název nástroje*} **:** \[ <em>jakýkoli text</em> ] {**chyba** &#124;  **upozornění**} <em>+ číslo</em>**:**<em>zdrojů lokalizovatelných řetězců</em> \[ <em>jakýkoli text</em> ]

kde:

- {*a* &#124; *b*} je volbou buď *a* nebo *b*.

- \[<em>Položka</em>] je volitelný řetězec nebo parametru.

- **Tučné** představuje literál.

Příklad:

> C:\\*sourcefile.cpp*(134): chyba C2143: Chyba syntaxe: chybí ";" před "}"
>
> LINK: závažná chyba LNK1104: Nelze otevřít soubor "*somelib.lib*.

## <a name="see-also"></a>Viz také:

[Seznámení s kroky vlastního sestavení a s událostmi sestavení](../ide/understanding-custom-build-steps-and-build-events.md)