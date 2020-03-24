---
title: Chyba sestavení projektu PRJ0003
ms.date: 11/04/2016
f1_keywords:
- PRJ0003
helpviewer_keywords:
- PRJ0003
ms.assetid: fc5a84bb-c6d3-41d6-8dd6-475455820778
ms.openlocfilehash: 59028c6d886630ef7db115a2ea93327669b2fcfd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192923"
---
# <a name="project-build-error-prj0003"></a>Chyba sestavení projektu PRJ0003

> Došlo k chybě při vytváření*příkazového řádku*.

Příkaz *příkazového řádku* vytvořený ze vstupu v dialogovém okně **stránky vlastností** vrátil chybový kód, ale v okně **výstup** se nezobrazí žádné informace.

Mezi možné příčiny této chyby patří:

- Váš projekt závisí na ATL serveru. Počínaje verzí Visual Studio 2008 již Server ATL není součástí sady Visual Studio, ale byl vydán jako sdílený zdrojový projekt na webu CodePlex. Chcete-li stáhnout zdrojový kód a nástroje serveru ATL, přejdete na [ATL Server Library and Tools](https://go.microsoft.com/fwlink/p/?linkid=81979).

- Nedostatek systémových prostředků. Pokud chcete tento problém vyřešit, ukončete některé aplikace.

- Nedostatečná oprávnění zabezpečení Ověřte, zda máte dostatečná oprávnění zabezpečení.

- Cesty ke spustitelnému souboru zadané v **adresářích VC + +** neobsahují cestu pro nástroj, který se pokoušíte spustit. Informace najdete v tématu [Nastavení vlastností kompilátoru a sestavení](../../build/working-with-project-properties.md) .

- V případě projektů makefile nemáte příkaz ke spuštění buď na **příkazovém řádku sestavení** , nebo na **příkazovém řádku pro sestavování**.

## <a name="see-also"></a>Viz také

[Chyby a upozornění sestavení projektu (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)
