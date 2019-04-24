---
title: Standardní příkazy
ms.date: 11/04/2016
helpviewer_keywords:
- File menu
- identifiers [MFC], command IDs
- command IDs, standard commands
- OLE commands
- commands [MFC], standard
- standard command IDs
- Window menu commands
- standard commands
- View menu commands
- Edit menu standard commands
- Help [MFC], menus
- programmer-defined IDs [MFC]
ms.assetid: 88cf3ab4-79b3-4ac6-9365-8ac561036fbf
ms.openlocfilehash: 987023322e38584d10901c1ab1fe20ac46926bd2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307156"
---
# <a name="standard-commands"></a>Standardní příkazy

Rozhraní definuje počet zpráv standardních příkazů. ID pro tyto příkazy obvykle mít tuto podobu:

**Id_** *zdroj*_*položky*

kde *zdroj* je obvykle název nabídky a *položky* je položka nabídky. Id_file_new – je například ID příkazu pro příkaz Nový v nabídce Soubor. Identifikátory standardních příkazů jsou zobrazeny tučným písmem v dokumentaci. Programátorem definované identifikátory jsou uvedeny v písmo, které se liší od okolního textu.

Následuje seznam některé z vašich nejdůležitějších příkazy podporované:

*Příkazy nabídky Soubor*<br/>
Nový otevřete, zavřete, uložit, uložit jako, nastavení stránky, nastavení tisku, tisk, náhled tisku, ukončení a naposledy použitých souborů.

*Příkazy nabídky Upravit*<br/>
Vymazat, zrušte všechny, kopírování, vyjmutí, hledání, vložení, opakujte, nahradit, vyberte všechny vrátit zpět a znovu.

*Příkazy nabídky zobrazení*<br/>
Panel nástrojů a stavový řádek.

*Příkazy nabídky okna*<br/>
Nová uspořádejte, kaskádovitě přenést na, dlaždici vodorovně, svisle vedle sebe a rozdělení.

*Příkazy nabídky nápovědy*<br/>
Index, přes nabídku Nápověda a o.

*Příkazy OLE (nabídku Úpravy)*<br/>
Vložit nový objekt, upravit odkazy, Vložit odkaz, Vložit jinak a *typename* objektu (příkazy).

Rozhraní poskytuje různé úrovně podpory pro tyto příkazy. Některé příkazy jsou podporovány pouze jako identifikátory definovaných příkazů, zatímco jiné podporují důkladné implementace. Například rozhraní implementuje příkazu Otevřít v nabídce Soubor vytvořením nového objektu dokumentu, zobrazení otevřené dialogové okno a otevírání a čtení souboru. Naproti tomu je nutné implementovat příkazů v nabídce Úpravy sami, protože příkazů, jako jsou id_edit_copy – závisí na charakteru dat, kterou kopírujete.

Další informace o příkazech podporovány a úroveň implementace, které jsou k dispozici, najdete v části [Technická poznámka 22](../mfc/tn022-standard-commands-implementation.md). Standardní příkazy jsou definovány v souboru AFXRES. H.

## <a name="see-also"></a>Viz také:

[Identifikátory objektů uživatelského rozhraní a příkazů](../mfc/user-interface-objects-and-command-ids.md)
