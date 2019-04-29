---
title: 'Aktivace: Příkazy'
ms.date: 11/04/2016
helpviewer_keywords:
- verbs [MFC]
- OLE [MFC], activation
- edit verb [MFC]
- activation [MFC], verbs
- OLE [MFC], editing
- Primary verb [MFC]
- OLE activation {MFC]
ms.assetid: eb56ff23-1de8-43ad-abeb-dc7346ba7b70
ms.openlocfilehash: baf8e0ac3527407b2e5ba77dfdf3921419217fd7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392905"
---
# <a name="activation-verbs"></a>Aktivace: Příkazy

Tento článek vysvětluje play slovesa primární a sekundární roli v prostředí OLE [aktivace](../mfc/activation-cpp.md).

Dvojitým kliknutím vložená položka. obvykle umožňuje uživateli upravit. Některé položky, ale nefungují tak tímto způsobem. Například dvojitým kliknutím položky vytvořené v aplikaci pro záznam zvuku neotevře server v samostatném okně; Místo toho přehraje zvuk.

Důvodem tohoto chování rozdíl je, že záznam zvuku položky mají různé "primárního operaci." Primární požadavek je akce provést, když uživatel poklepe položky OLE. Pro většinu typů položek OLE je primárního operaci úprav, který spouští server, která vytvořila tuto položku. U některých typů položek, jako jsou položky záznam zvuku je primární požadavek Play.

Mnoho typů položek OLE podporují pouze jeden příkaz a upravit je nejčastěji používané. Některé typy položek, ale podporují více příkazů. Můžete třeba upravit záznam zvuku položky podporují jako sekundární příkaz.

Další příkaz použitý často je otevřít. Příkaz Otevřít se shoduje s úpravy, s výjimkou serverová aplikace spuštěna v samostatném okně. Tento příkaz má být použit při aplikace typu kontejner nebo serverové aplikace nepodporuje aktivace na místě.

Všechny příkazy než primárního operaci je nutné volat pomocí příkazu podnabídky při výběru položky. Tento podnabídky obsahuje všechny akce, které podporuje položky a obvykle se dostane *typename* **objekt** příkaz **upravit** nabídky. Informace o tom, *typename* **objektu** příkazu, najdete v článku [nabídky a prostředky: Kontejnerové doplňky](../mfc/menus-and-resources-container-additions.md).

Příkazy, které podporuje serverové aplikace jsou uvedeny v registrační databázi Windows. Pokud je serverová aplikace napsané pomocí knihovny Microsoft Foundation Class, se automaticky zaregistruje všechny akce při spuštění serveru. V opačném případě byste měli zaregistrovat během fáze inicializace aplikace serveru. Další informace najdete v článku [registrace](../mfc/registration.md).

## <a name="see-also"></a>Viz také:

[Aktivace](../mfc/activation-cpp.md)<br/>
[Kontejnery](../mfc/containers.md)<br/>
[Servery](../mfc/servers.md)
