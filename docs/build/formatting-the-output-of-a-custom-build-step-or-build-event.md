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
ms.openlocfilehash: 09bf8485a352d6ec2c1297f8a1be508cb7476c31
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169822"
---
# <a name="formatting-the-output-of-a-custom-build-step-or-build-event"></a>Formátovaní výstupu vlastního kroku sestavení nebo události sestavení

Pokud je výstup vlastního kroku sestavení nebo události sestavení správně naformátován, uživatelé získají následující výhody:

- Upozornění a chyby se počítají v okně **výstup** .

- Výstup se zobrazí v okně **seznam úkolů** .

- Kliknutím na výstup v okně **výstup** se zobrazí příslušné téma.

- V okně **seznam úkolů** nebo okně **výstup** jsou povoleny operace F1.

Výstup by měl mít tento formát:

> {<em>filename</em>**(**<em>řádek #</em> \[ **,** <em>sloupec #</em>]**)** &#124; *název nástroje*} **:** \[ <em>libovolný text</em> ] {**Error** &#124; **Warning**} <em>Code + Number</em>**:**<em>lokalizovatelné řetězce</em> \[ <em>libovolný text</em> ]

Kde:

- {*a* &#124; *b*} je volba buď *a* , nebo *b*.

- \[<em>položka</em>] je volitelný řetězec nebo parametr.

- **Tučné** představuje literál.

Příklad:

> C:\\*požadovaný sourcefile. cpp*(134): Chyba C2143: Chyba syntaxe: chybějící znak; před}
>
> ODKAZ: závažná chyba LINKERŮ LNK1104: nejde otevřít soubor*somelib. lib.*

## <a name="see-also"></a>Viz také

[Seznámení s kroky vlastního sestavení a s událostmi sestavení](understanding-custom-build-steps-and-build-events.md)
