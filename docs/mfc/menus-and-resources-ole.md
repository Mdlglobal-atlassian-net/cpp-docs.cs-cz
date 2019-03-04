---
title: Nabídky a prostředky (OLE)
ms.date: 11/04/2016
helpviewer_keywords:
- OLE visual editing servers [MFC]
- status bars [MFC], OLE document applications
- visual editing [MFC], application menus and resources
- string tables [MFC], visual editing applications
- OLE containers [MFC], menus and resources
- OLE applications [MFC], menus and resources
- OLE server applications [MFC], menus and resources
- toolbars [MFC], OLE document applications
- string editing [MFC], visual editing applications
- server applications [MFC], OLE menus and resources
- applications [OLE], menus and resources
- menus [MFC], OLE document applications
- in-place activation [MFC], OLE menus and resources
- containers [MFC], OLE container applications
- OLE menus and resources [MFC]
ms.assetid: 52bfa086-7d3d-466f-94c7-c7061f3bdb3a
ms.openlocfilehash: 4e8f8c7fa8e24349a741b99822f13d5473373e17
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57268522"
---
# <a name="menus-and-resources-ole"></a>Nabídky a prostředky (OLE)

Tato skupina článků popisuje použití nabídky a prostředky v aplikacích MFC OLE dokumentu.

OLE úpravy s náhledem umístí další požadavky v nabídce a další prostředky poskytované OLE – aplikace dokumentů, protože existuje několik režimů, ve které i kontejneru a aplikace serveru (součást) jde spustit a používat. Úplný server aplikace například můžete spustit v některém z těchto tří režimů:

- Samostatně.

- Na místě, pro úpravu položky v rámci kontejneru.

- Otevřete pro úpravu položky mimo kontext svého kontejneru, často v samostatném okně.

To vyžaduje tři samostatné nabídky rozložení, jeden pro každý možné režim aplikace. Tabulky akcelerátoru jsou také nezbytné pro každý nový režim. Aplikace typu kontejner může nebo nemusí podporovat aktivace na místě. Pokud ano, potřebuje novou strukturu nabídky a související tabulky akcelerátoru.

Aktivace na místě vyžaduje, že pro nabídky, nástrojů a stavový panel prostor musí si vyjednat kontejneru a serverové aplikace. Všechny prostředky musí být vytvořeny s to na paměti. Tento článek [nabídky a prostředky: Slučování nabídek](../mfc/menus-and-resources-menu-merging.md) popisuje Toto téma podrobněji.

Kvůli těmto problémům OLE dokumentu aplikace vytvořené pomocí Průvodce aplikací může mít až čtyři samostatné nabídky a prostředky tabulky akcelerátoru. Ty se používají z následujících důvodů:

|Název prostředku|Použití|
|-------------------|---------|
|IDR_MAINFRAME|Použít v aplikaci MDI, pokud není otevřený žádný soubor, nebo v aplikaci SDI bez ohledu na to otevřených souborů. Toto je standardní nabídky použít v aplikacích jiných než OLE.|
|IDR_\<project>TYPE|V aplikaci MDI použít, pokud existují otevřené soubory. Použít při spuštění samostatné aplikace. Toto je standardní nabídky použít v aplikacích jiných než OLE.|
|IDR_\<project>TYPE_SRVR_IP|Používané při objektu je otevřen v místě serveru nebo v kontejneru.|
|IDR_\<project>TYPE_SRVR_EMB|Používá serverové aplikace, pokud objekt je otevřen bez použití aktivace na místě.|

Každý z těchto názvů prostředků představuje nabídky a obvykle tabulky akcelerátorů. Podobně jako schéma by měl použít v aplikacích MFC, které nejsou vytvořeny pomocí Průvodce aplikací.

Následující články popisují témata související s kontejnery, servery a slučováním nezbytné k implementaci v místní aktivace nabídek:

- [Nabídky a prostředky: Kontejnerové doplňky](../mfc/menus-and-resources-container-additions.md)

- [Nabídky a prostředky: Serverové doplňky](../mfc/menus-and-resources-server-additions.md)

- [Nabídky a prostředky: Slučováním nabídek](../mfc/menus-and-resources-menu-merging.md)

## <a name="see-also"></a>Viz také:

[OLE](../mfc/ole-in-mfc.md)
