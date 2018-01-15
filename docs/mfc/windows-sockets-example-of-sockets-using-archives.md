---
title: "Windows Sockets: Příklady soketů využívajících archivy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- sockets [MFC], with archives
- examples [MFC], Windows Sockets
- Windows Sockets [MFC], with archives
ms.assetid: 2e3c9bb2-7e7b-4f28-8dc5-6cb7a484edac
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e0e70e8ecc14496b03bc758d91f078a926f33532
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="windows-sockets-example-of-sockets-using-archives"></a>Windows Sockets: Příklady soketů využívajících archivy
Tento článek představuje příklad použití třídy [CSocket](../mfc/reference/csocket-class.md). Aktivuje se v příkladu `CArchive` objekty k serializaci dat prostřednictvím soketu. Všimněte si, že se nejedná dokumentu serializace do nebo ze souboru.  
  
 Následující příklad ukazuje, jak používat archivu odesílat a přijímat data přes `CSocket` objekty. V příkladu je navržené tak, aby výměnu dat dvě instance aplikace (ve stejném počítači nebo na jiné počítače v síti). Jedna instance odešle data, která přijímá jako druhá instance a potvrdí, že četl. Buď aplikace můžete zahájit exchange a buď může fungovat jako server nebo jako klienta na jinou aplikaci. Následující funkce je definovaný ve třídě zobrazení aplikace:  
  
 [!code-cpp[NVC_MFCSimpleSocket#1](../mfc/codesnippet/cpp/windows-sockets-example-of-sockets-using-archives_1.cpp)]  
  
 Je třeba mít o tomto příkladu je, že jeho struktura je paralelní u knihovny MFC `Serialize` funkce. **PacketSerialize** – členská funkce se skládá z **Pokud** příkaz s **else** klauzule. Funkce obdrží dvě [CArchive](../mfc/reference/carchive-class.md) odkazy jako parametry: `arData` a `arAck`. Pokud `arData` archivu je nastavena pro ukládání (odesílajícím), **Pokud** firemní pobočky spustí; jinak, pokud `arData` je nastaven pro načítání (příjem) funkce přijímá **else** větve. Další informace o serializace v prostředí MFC najdete v tématu [serializace](../mfc/how-to-make-a-type-safe-collection.md).  
  
> [!NOTE]
>  `arAck` Archivu objektu předpokládá se, že je opakem `arData`. Pokud `arData` je pro odesílání, `arAck` obdrží, a konverzace je true.  
  
 Pro odesílání, cyklu Příklad funkce pro zadaného počtu opakování, pokaždé, když generování některé náhodná data pro demonstrační účely. Aplikace by získat reálná data z některé zdroje, jako je soubor. `arData` Operátor vložení archivu (**<<**) se používá k odesílání datového proudu ze tří po sobě jdoucích bloky dat:  
  
-   "Hlavičku" určující povaha dat (v tomto případě hodnotu `bValue` proměnné a kolik kopií se budou odesílat).  
  
     Obě položky jsou náhodně vygenerované v tomto příkladu.  
  
-   Zadaný počet kopií dat.  
  
     Vnitřní **pro** cykly zasílá `bValue` zadaného počtu opakování.  
  
-   Řetězec názvem `strText` zobrazující příjemce s uživatelem.  
  
 Pro příjem, funkce funguje podobně, s tím rozdílem, že používá operátor extrakce do archivu (**>>**) k získání dat z archivu. Má přijímající aplikace ověří data obdrží, zobrazí poslední zprávu "Přijaté" a poté odešle zpět se zpráva s oznámením "Odeslané" pro odesílající aplikací k zobrazení.  
  
 V tomto modelu komunikace je slovo "Přijaté", odeslání zprávy `strText` proměnnou, je pro zobrazení na druhém konci komunikace, takže určuje přijímající uživateli přijímání počet paketů data. Příjemce odpoví odpovědí s podobně jako řetězec, který uvádí "Odeslat", pro zobrazení na obrazovce původní odesílatele. Přijetí oba řetězce označuje, že došlo k úspěšné komunikaci.  
  
> [!CAUTION]
>  Pokud píšete aplikace MFC klienta ke komunikaci se servery zavedených (mimo MFC), Neodesílat objekty C++ prostřednictvím archivu. Pokud je server aplikace knihovny MFC, který rozumí druhy objektů, které chcete odeslat, nebude moci přijímat a deserializaci objektů. Příklad v článku [Windows Sockets: pořadí bajtů](../mfc/windows-sockets-byte-ordering.md) zobrazuje sdělení tohoto typu.  
  
 Další informace najdete v tématu Specifikace Windows Sockets: **htonl**, **htons**, **ntohl**, **ntohs**. Také další informace najdete v tématu:  
  
-   [Windows Sockets: Odvozování z tříd soketů](../mfc/windows-sockets-deriving-from-socket-classes.md)  
  
-   [Windows Sockets: Jak pracují sokety s archivy](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Windows Sockets: Pozadí](../mfc/windows-sockets-background.md)  
  
## <a name="see-also"></a>Viz také  
 [Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)   
 [CArchive::IsStoring](../mfc/reference/carchive-class.md#isstoring)   
 [CArchive::operator <<](../mfc/reference/carchive-class.md#operator_lt_lt)   
 [CArchive::operator >>](../mfc/reference/carchive-class.md#operator_lt_lt)   
 [CArchive::Flush](../mfc/reference/carchive-class.md#flush)   
 [CObject::Serialize](../mfc/reference/cobject-class.md#serialize)

