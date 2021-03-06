---
title: Servery pro aktivní dokumenty
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], servers
- servers [MFC], active document
- active document servers [MFC]
ms.assetid: 131fec1e-02a0-4305-a7ab-903b911232a7
ms.openlocfilehash: 7050b810bb5e1f0c240222cd9b8c4922ced4238a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394966"
---
# <a name="active-document-servers"></a>Servery pro aktivní dokumenty

Servery pro aktivní dokumenty třeba Wordový, Excelový nebo Powerpointový hostitele z ostatních typů aplikací aktivní dokumenty. Na rozdíl od OLE – vložené objekty (které jsou zobrazeny pouze v rámci stránky jiného dokumentu), aktivní dokumenty poskytují úplné rozhraní a kompletní nativní funkce serverové aplikace, která je vytvořila. Uživatelé můžou vytvářet dokumenty pomocí všech možností jejich oblíbených aplikací (v případě, že jsou povolené aktivní dokument), ještě můžete považovat za výsledný projekt jednu entitu.

Aktivní dokumenty může mít více než jednu stránku a jsou vždy aktivní na místě. Aktivní dokumenty řídit součástí uživatelského rozhraní, slučování své nabídky s **souboru** a **pomáhají** nabídky kontejneru. Jejich zabírat celou oblast úprav kontejneru a určovat, zobrazení a rozložení stránky tiskárny (okrajů, zápatí a tak dále).

Knihovna MFC implementuje servery pro aktivní dokumenty s document/view – rozhraní, mapy odesílání příkazů, tisku, správy nabídky a správu registru. Konkrétní programovací požadavky jsou uvedeny v [aktivní dokumenty](../mfc/active-documents.md).

MFC podporuje aktivní dokumenty s [cdocobjectserver –](../mfc/reference/cdocobjectserver-class.md) třídu odvozenou z [CCmdTarget –](../mfc/reference/ccmdtarget-class.md), a [cdocobjectserveritem –](../mfc/reference/cdocobjectserveritem-class.md)odvozenou z [ Coleserveritem –](../mfc/reference/coleserveritem-class.md). MFC podporuje kontejnery pro aktivní dokument s [coledocobjectitem –](../mfc/reference/coledocobjectitem-class.md) třídu odvozenou z [COleClientItem](../mfc/reference/coleclientitem-class.md).

`CDocObjectServer` mapy rozhraní pro aktivní dokument a inicializuje a aktivuje aktivní dokument. Knihovna MFC poskytuje také makra pro zpracování, směrování příkazů v aktivní dokumenty. Pokud chcete použít aktivní dokumenty ve vaší aplikaci, zahrnují AfxDocOb.h v souboru StdAfx.h.

Regulární knihovny MFC serveru zavěšení vlastní `COleServerItem`-odvozené třídy. Průvodce aplikací knihovny MFC generuje této třídy za vás, pokud vyberete **mini serveru** nebo **úplný server** zaškrtávací políčko a poskytnout vaší aplikační server podpoře složeném dokumentu. Pokud vyberete také **server pro aktivní dokument** zaškrtávací políčko, Průvodce aplikací knihovny MFC generuje třídy odvozené od `CDocObjectServerItem` místo.

`COleDocObjectItem` Třída umožňuje kontejneru OLE se kontejner pro aktivní dokument. Můžete použít Průvodce aplikací knihovny MFC a vytvoří kontejner aktivního dokumentu výběrem **kontejner pro aktivní dokument** zaškrtávacího políčka na stránce Podpora složených dokumentů, Průvodce aplikací knihovny MFC. Další informace najdete v tématu [vytvoření aplikace kontejnerů pro aktivní dokument](../mfc/creating-an-active-document-container-application.md).

## <a name="see-also"></a>Viz také:

[Zahrnutí aktivního dokumentu](../mfc/active-document-containment.md)
