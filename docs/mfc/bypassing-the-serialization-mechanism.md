---
title: Obcházení mechanismu serializace
ms.date: 11/04/2016
helpviewer_keywords:
- archive objects [MFC]
- bypassing serialization
- archives [MFC], serialization
- serialization [MFC], bypassing
- archives [MFC]
- serialization [MFC], role of framework
- serialization [MFC], overriding
ms.assetid: 48d4a279-b51c-4ba5-81cd-ed043312b582
ms.openlocfilehash: 1937098de30884be327c67a698dbb0023be248bb
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345205"
---
# <a name="bypassing-the-serialization-mechanism"></a>Obcházení mechanismu serializace

Jak jste viděli, rozhraní poskytuje výchozí způsob, jak číst a zapisovat data do a ze souborů. Serializace prostřednictvím objektu archiv, který nejlépe vyhovuje požadavkům na skvělé mnoho aplikací. Takové aplikace načte soubor zcela do paměti, umožňuje uživatelům aktualizovat soubor a pak zapíše aktualizovanou verzi na disk znovu.

Ale některé aplikace pracují s daty nějak významně odlišně, a v případě těchto aplikací není vhodné serializace prostřednictvím archivu. Mezi příklady patří programy databáze, programy, které upravit jen části velkých souborů, programy, které zapisovat pouze textové soubory a programy, které sdílejí data souborů.

V těchto případech je možné přepsat [serializace](../mfc/reference/cobject-class.md#serialize) funkce jiným způsobem, které zprostředkovává akce souboru prostřednictvím [cfile –](../mfc/reference/cfile-class.md) objekt spíše než [CArchive](../mfc/reference/carchive-class.md) objektu.

Můžete použít `Open`, `Read`, `Write`, `Close`, a `Seek` členské funkce třídy `CFile` pro otevření souboru, přesuňte ukazatel na soubor (Posunout) k určitému bodu v souboru čtení záznamu (zadaný počet bajtů ) v tomto okamžiku umožní uživateli aktualizovat record, pak znovu pokusit se stejným bodem a zapsat záznam zpět do souboru. Rozhraní se otevře soubor pro vás a můžete použít `GetFile` členské funkce třídy `CArchive` získat ukazatel `CFile` objektu. Pro ještě větší propracované a flexibilní použití, můžete přepsat [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) a [OnSaveDocument](../mfc/reference/cdocument-class.md#onsavedocument) členské funkce třídy `CWinApp`. Další informace najdete v tématu třídy [cfile –](../mfc/reference/cfile-class.md) v *odkaz knihovny MFC*.

V tomto scénáři vaše `Serialize` přepsání nemá žádný účinek, pokud například chcete mít pro čtení a zápis záhlaví souboru k zajištění aktuálnosti při zavření dokumentu.

## <a name="see-also"></a>Viz také:

[Použití dokumentů](../mfc/using-documents.md)
