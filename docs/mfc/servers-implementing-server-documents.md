---
title: 'Servery: Implementace dokumentů serveru'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC], managing server documents
- OLE server applications [MFC], implementing OLE servers
- servers, server documents
- server documents [MFC], implementing
ms.assetid: cca1451a-ad09-47ed-b56e-bccd78fc86d1
ms.openlocfilehash: 17ced1cdb0b40b13fbda68150030efde5735ba7b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307910"
---
# <a name="servers-implementing-server-documents"></a>Servery: Implementace dokumentů serveru

Tento článek popisuje kroky, které je třeba provést při úspěšně implementovat dokument na serveru, pokud jste nezadali možnost serveru OLE v Průvodci aplikací.

#### <a name="to-define-a-server-document-class"></a>Chcete-li definovat dokumentové třídy serveru

1. Odvodit vaše dokumentové třídy z `COleServerDoc` místo `CDocument`.

1. Vytvořit položku server třídy odvozené od `COleServerItem`.

1. Implementace `OnGetEmbeddedItem` členské funkce třídy dokumentu serveru.

   `OnGetEmbeddedItem` je volána, když uživatel aplikace typu kontejner vytvoří nebo upraví vloženou položku. Měla by vrátit položku představující celý dokument. Měl by to být objekt vaše `COleServerItem`-odvozené třídy.

1. Přepsat `Serialize` členskou funkci k serializaci obsahu dokumentu. Není nutné k serializaci seznam položek serveru, pokud je používáte k reprezentaci nativní data v dokumentu. Další informace najdete v tématu *implementace položky serveru* v článku [serverů: Serverové položky](../mfc/servers-server-items.md).

Když se dokument na serveru, rozhraní automaticky zaregistruje dokumentu OLE systémové knihovny DLL. To umožňuje identifikovat dokumenty na serveru knihoven DLL.

Další informace najdete v tématu [odvozenou třídu COleServerItem](../mfc/reference/coleserveritem-class.md) a [coleserverdoc –](../mfc/reference/coleserverdoc-class.md) v *knihovny tříd*.

## <a name="see-also"></a>Viz také:

[Servery](../mfc/servers.md)<br/>
[Servery: Serverové položky](../mfc/servers-server-items.md)<br/>
[Servery: Implementace serveru](../mfc/servers-implementing-a-server.md)<br/>
[Servery: Implementace Windows rámečkem na místě](../mfc/servers-implementing-in-place-frame-windows.md)
