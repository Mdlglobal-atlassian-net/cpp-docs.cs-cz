---
title: Co je objekt CArchive
ms.date: 11/04/2016
helpviewer_keywords:
- archive objects [MFC]
- archives [MFC], for serialization
- buffers, serializable objects
- CArchive class [MFC], about CArchive class [MFC]
- buffering, serializable objects
ms.assetid: 843f1825-288d-4d89-a1fa-70e1f92d9b8b
ms.openlocfilehash: 0a78385c81c43a4b0c925bbe89ccd3937873ee8b
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446015"
---
# <a name="what-is-a-carchive-object"></a>Co je objekt CArchive

Objekt `CArchive` poskytuje mechanismus pro ukládání do vyrovnávací paměti bezpečný pro zápis nebo čtení serializovatelných objektů do nebo z objektu `CFile`. Objekt `CFile` obvykle představuje soubor na disku; může to ale být i soubor paměti (`CSharedFile` objekt), třeba reprezentovat schránku.

Daný `CArchive` objekt buď ukládá (zapisuje, serializace) data nebo načítá (čte, deserializace) data, ale nikdy ne obojí. Životnost objektu `CArchive` je omezena na jeden průchod zápisem objektů do souboru nebo čtením objektů ze souboru. Proto dva úspěšně vytvořené `CArchive` objekty jsou vyžadovány k serializaci dat do souboru a jejich deserializaci ze souboru.

Když archiv ukládá objekty do souboru, archiv připojí název `CRuntimeClass` k objektům. Poté, když jiný archiv načte objekty ze souboru do paměti, jsou objekty odvozené `CObject`dynamicky přebudovány na základě `CRuntimeClass` objektů. Na daný objekt může být odkazováno více než jednou, protože je zapsán do souboru uložením archivu. Při načítání archivu však dojde pouze k rekonstrukci objektu. Podrobnosti o tom, jak archiv připojuje `CRuntimeClass` informace k objektům a rekonstruuje objekty, přičemž vezme v úvahu možné více odkazů, jsou popsány v [technické poznámce 2](../mfc/tn002-persistent-object-data-format.md).

Při serializaci dat do archivu archiv shromáždí data, dokud její vyrovnávací paměť nebude plná. Potom archiv zapíše svou vyrovnávací paměť na objekt `CFile`, na který ukazuje objekt `CArchive`. Podobně při čtení dat z archivu načte data ze souboru do vyrovnávací paměti a pak z vyrovnávací paměti do vašeho deserializovaného objektu. Toto ukládání do vyrovnávací paměti snižuje počet fyzického čtení pevného disku, což zlepšuje výkon vaší aplikace.

## <a name="see-also"></a>Viz také

[Serializace: Serializace objektu](../mfc/serialization-serializing-an-object.md)
