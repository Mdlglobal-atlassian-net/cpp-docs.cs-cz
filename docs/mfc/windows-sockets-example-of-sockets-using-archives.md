---
title: 'Windows Sockets: Příklady soketů využívajících archivy'
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], with archives
- examples [MFC], Windows Sockets
- Windows Sockets [MFC], with archives
ms.assetid: 2e3c9bb2-7e7b-4f28-8dc5-6cb7a484edac
ms.openlocfilehash: 253a65430ae230fbc4deeb9bd5288f28237310d2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371077"
---
# <a name="windows-sockets-example-of-sockets-using-archives"></a>Windows Sockets: Příklady soketů využívajících archivy

Tento článek představuje příklad použití třídy [CSocket](../mfc/reference/csocket-class.md). Příklad využívá `CArchive` objekty serializovat data prostřednictvím soketu. Všimněte si, že se nejedná o serializaci dokumentu do nebo ze souboru.

Následující příklad ukazuje, jak pomocí archivu odesílat `CSocket` a přijímat data prostřednictvím objektů. Příklad je navržen tak, aby dvě instance aplikace (na stejném počítači nebo na různých počítačích v síti) vyměňovat data. Jedna instance odešle data, která druhá instance přijímá a pozná. Obě aplikace mohou zahájit výměnu a buď může fungovat jako server nebo jako klient jiné aplikace. Následující funkce je definována ve třídě zobrazení aplikace:

[!code-cpp[NVC_MFCSimpleSocket#1](../mfc/codesnippet/cpp/windows-sockets-example-of-sockets-using-archives_1.cpp)]

Nejdůležitější věc, o tomto příkladu je, že jeho `Serialize` struktura rovnoběžná s funkce knihovny MFC. Členská `PacketSerialize` funkce se skládá z **příkazu if** s klauzulí **else.** Funkce obdrží dva [carchive](../mfc/reference/carchive-class.md) odkazy jako parametry: *arData* a *arAck*. Pokud je objekt archivu *arData* nastaven pro ukládání (odesílání), provede **se větev if;** jinak, pokud *arData* je nastavena pro načítání (příjem) funkce trvá **else** větev. Další informace o serializaci v knihovně MFC naleznete v [tématu Serializace](../mfc/how-to-make-a-type-safe-collection.md).

> [!NOTE]
> *ArAck* archiv objekt je považován za opak *arData*. Pokud *arData* je pro odesílání, *arAck* přijímá a converse je true.

Pro odesílání se ukázková funkce smyčkuje pro zadaný počet opakování pokaždé, když generuje některá náhodná data pro demonstrační účely. Vaše aplikace by získat skutečná data z některého zdroje, jako je například soubor. Operátor vložení archivu *arData* (**<<**) se používá k odeslání datového proudu tří po sobě jdoucích bloků dat:

- "Záhlaví", které určuje povahu dat (v tomto případě hodnota proměnné *bValue* a kolik kopií bude odesláno).

   Obě položky jsou generovány náhodně pro tento příklad.

- Zadaný počet kopií dat.

   Vnitřní **for** smyčky odešle *bValue* zadaný počet opakování.

- Řetězec s názvem *strText,* který příjemce zobrazí svému uživateli.

Pro příjem funguje funkce podobně, s tím rozdílem, že**>>** k získání dat z archivu používá operátor extrakce archivu ( ). Přijímající aplikace ověří data, která obdrží, zobrazí konečnou zprávu "Přijato" a potom odešle zpět zprávu s textem "Odesláno" pro odesílající aplikaci, která se má zobrazit.

V tomto komunikačním modelu je slovo "Přijato", zpráva odeslaná v proměnné *strText,* k zobrazení na druhém konci komunikace, takže určuje přijímajícímu uživateli, že byl přijat určitý počet paketů dat. Příjemce odpoví podobným řetězcem s nápisem "Odesláno", pro zobrazení na obrazovce původního odesílatele. Příjem obou řetězců označuje, že došlo k úspěšné komunikaci.

> [!CAUTION]
> Pokud píšete klientský program knihovny MFC pro komunikaci se zavedenými servery (jiné než MFC), neodesílejte objekty jazyka C++ prostřednictvím archivu. Pokud server není aplikace knihovny MFC, která rozumí typy objektů, které chcete odeslat, nebude moci přijímat a rekonstruovat objekty. Příklad v článku [Windows Sockets: Byte Ordering](../mfc/windows-sockets-byte-ordering.md) ukazuje komunikaci tohoto typu.

Další informace naleznete v tématu Windows Sockets Specification: **htonl**, **htons**, **ntohl**, **ntohs**. Další informace naleznete také v tématu:

- [Windows Sockets: Odvozování z tříd soketů](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Sockets: Jak pracují sokety s archivy](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets: Pozadí](../mfc/windows-sockets-background.md)

## <a name="see-also"></a>Viz také

[Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CArchiv::IsStoring](../mfc/reference/carchive-class.md#isstoring)<br/>
[CArchiv::operátor <<](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchiv::operátor >>](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchiv::Vyprázdnění](../mfc/reference/carchive-class.md#flush)<br/>
[CObject::Serializovat](../mfc/reference/cobject-class.md#serialize)
