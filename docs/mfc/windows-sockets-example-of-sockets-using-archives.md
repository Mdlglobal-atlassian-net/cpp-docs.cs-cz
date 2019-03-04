---
title: 'Windows Sockets: Příklady soketů využívajících archivy'
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], with archives
- examples [MFC], Windows Sockets
- Windows Sockets [MFC], with archives
ms.assetid: 2e3c9bb2-7e7b-4f28-8dc5-6cb7a484edac
ms.openlocfilehash: 4ea1e2911b156066360da09993fa7302db79f12b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57295252"
---
# <a name="windows-sockets-example-of-sockets-using-archives"></a>Windows Sockets: Příklady soketů využívajících archivy

Tento článek představuje příklad používání třídy [csocket –](../mfc/reference/csocket-class.md). Tento příklad využívá `CArchive` objekty k serializaci dat přes soket. Všimněte si, že to není serializace dokumentu do nebo ze souboru.

Následující příklad ukazuje, jak používat archivu odesílat a přijímat data přes `CSocket` objekty. V příkladu je navržený tak, aby výměnu dat dvě instance aplikace (ve stejném počítači nebo na různých počítačích v síti). Jedna instance odesílá data, které druhá instance přijímá a bere na vědomí. Pokud aplikace můžete zahájit výměnu a buď může fungovat jako server nebo klienta s jinou aplikací. Následující funkce je definována ve třídě zobrazení vaší aplikace:

[!code-cpp[NVC_MFCSimpleSocket#1](../mfc/codesnippet/cpp/windows-sockets-example-of-sockets-using-archives_1.cpp)]

Nejdůležitější informace o tomto příkladu je, že jeho strukturu parallels, která z knihovny MFC `Serialize` funkce. `PacketSerialize` Členská funkce se skládá z **Pokud** příkazem **else** klauzuli. Funkce přijímá dva [CArchive](../mfc/reference/carchive-class.md) odkazy jako parametry: *arData* a *arAck*. Pokud *arData* objekt archivu je nastaven pro ukládání (odesílání), **Pokud** spustí se větev; jinak, pokud *arData* je nastavena pro načtení (přijímání) funkce přijímá **else** větve. Další informace o serializace v prostředí MFC naleznete v tématu [serializace](../mfc/how-to-make-a-type-safe-collection.md).

> [!NOTE]
>  *ArAck* archivní objekt je považován za opak *arData*. Pokud *arData* je pro odesílání, *arAck* obdrží, a je první hodnotu true.

Pro odesílání, ukázkovou funkci smyčky pro do zadaného počtu opakování, pokaždé, když generování náhodných dat pro demonstrační účely. Vaše aplikace by získat reálná data z některé zdroje, jako je například soubor. *ArData* operátor vkládání archivu (**<<**) se používá k odesílání posloupnost tří po sobě jdoucích bloky dat:

- "Záhlaví", který určuje charakteru dat (v tomto případě hodnoty *bValue* proměnné a kolik kopií se budou odesílat).

   Obě položky jsou náhodně vygenerované v tomto příkladu.

- Zadaný počet kopií dat.

   Vnitřní **pro** smyčky odešle *bValue* zadaný počet.

- Volá se řetězec *strText* zobrazující příjemce s uživatelem.

Pro příjem, funkce funguje podobně, s tím rozdílem, že používá operátor extrakce archivu (**>>**) k získání dat z archivu. Přijímající aplikace ověří data obdrží, zobrazí závěrečná zpráva "Přijaté" a potom odešle zpět zpráva, že "Odeslané" pro odesílání aplikací pro zobrazení.

V tomto modelu komunikace, slovo "Přijaté" zprávu odeslat *strText* proměnná, je pro zobrazení na druhém konci komunikace, takže určuje přijímající uživateli, byly pro určitý počet paketů dat přijata. Příjemce odpovědi podobně jako řetězec, který říká: odesláno, zobrazí na obrazovce původního odesilatele. Přijetí obou řetězců označuje, že došlo k chybě komunikace úspěšná.

> [!CAUTION]
>  Při psaní aplikace knihovny MFC klienta ke komunikaci se servery zavedené (non-MFC) objektů jazyka C++ prostřednictvím archivu neodesílají. Pokud je server aplikace knihovny MFC, která analyzuje typy objektů, které chcete odeslat, nebude moci přijímat a deserializaci objektů. Příklad v tomto článku [rozhraní Windows Sockets: Řazení bajtů](../mfc/windows-sockets-byte-ordering.md) ukazuje sdělení tohoto typu.

Další informace najdete v tématu Specifikace Windows Sockets: **htonl**, **htons**, **ntohl**, **ntohs**. Další informace viz také:

- [Windows Sockets: Odvozování z tříd soketů](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Sockets: Jak pracují sokety s archivy](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets: Background](../mfc/windows-sockets-background.md)

## <a name="see-also"></a>Viz také:

[Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CArchive::IsStoring](../mfc/reference/carchive-class.md#isstoring)<br/>
[CArchive::operator <<](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchive::operator >>](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchive::Flush](../mfc/reference/carchive-class.md#flush)<br/>
[CObject::Serialize](../mfc/reference/cobject-class.md#serialize)
