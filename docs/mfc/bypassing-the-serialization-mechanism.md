---
title: Obcházení mechanismu serializace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- archive objects [MFC]
- bypassing serialization
- archives [MFC], serialization
- serialization [MFC], bypassing
- archives [MFC]
- serialization [MFC], role of framework
- serialization [MFC], overriding
ms.assetid: 48d4a279-b51c-4ba5-81cd-ed043312b582
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 25fc281e35fc07151fa609d07be540430a6a1da6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399808"
---
# <a name="bypassing-the-serialization-mechanism"></a>Obcházení mechanismu serializace

Jak jste viděli, rozhraní poskytuje výchozí způsob, jak číst a zapisovat data do a ze souborů. Serializace prostřednictvím objektu archiv, který nejlépe vyhovuje požadavkům na skvělé mnoho aplikací. Takové aplikace načte soubor zcela do paměti, umožňuje uživatelům aktualizovat soubor a pak zapíše aktualizovanou verzi na disk znovu.

Ale některé aplikace pracují s daty nějak významně odlišně, a v případě těchto aplikací není vhodné serializace prostřednictvím archivu. Mezi příklady patří programy databáze, programy, které upravit jen části velkých souborů, programy, které zapisovat pouze textové soubory a programy, které sdílejí data souborů.

V těchto případech je možné přepsat [serializace](../mfc/reference/cobject-class.md#serialize) funkce jiným způsobem, které zprostředkovává akce souboru prostřednictvím [cfile –](../mfc/reference/cfile-class.md) objekt spíše než [CArchive](../mfc/reference/carchive-class.md) objektu.

Můžete použít `Open`, `Read`, `Write`, `Close`, a `Seek` členské funkce třídy `CFile` pro otevření souboru, přesuňte ukazatel na soubor (Posunout) k určitému bodu v souboru čtení záznamu (zadaný počet bajtů ) v tomto okamžiku umožní uživateli aktualizovat record, pak znovu pokusit se stejným bodem a zapsat záznam zpět do souboru. Rozhraní se otevře soubor pro vás a můžete použít `GetFile` členské funkce třídy `CArchive` získat ukazatel `CFile` objektu. Pro ještě větší propracované a flexibilní použití, můžete přepsat [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) a [OnSaveDocument](../mfc/reference/cdocument-class.md#onsavedocument) členské funkce třídy `CWinApp`. Další informace najdete v tématu třídy [cfile –](../mfc/reference/cfile-class.md) v *odkaz knihovny MFC*.

V tomto scénáři vaše `Serialize` přepsání nemá žádný účinek, pokud například chcete mít pro čtení a zápis záhlaví souboru k zajištění aktuálnosti při zavření dokumentu.

## <a name="see-also"></a>Viz také

[Použití dokumentů](../mfc/using-documents.md)

