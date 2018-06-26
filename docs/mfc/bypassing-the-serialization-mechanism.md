---
title: Obcházení mechanismu serializace | Microsoft Docs
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
ms.openlocfilehash: 9252e08fe672f111dcf2b289b1b12891022a318d
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931084"
---
# <a name="bypassing-the-serialization-mechanism"></a>Obcházení mechanismu serializace
Protože jste viděli, rozhraní framework poskytuje výchozí způsob, jak číst a zapisovat data do a ze souborů. Serializace prostřednictvím objektu archivu nejlépe vyhovuje požadavkům na kvalitních mnoho aplikací. Takové aplikace načte soubor zcela do paměti, umožňuje uživateli aktualizovat soubor a zapíše aktualizovanou verzi na disk znovu.  
  
 Ale některé aplikace fungovat na data velmi jinak a pro tyto aplikace není vhodný serializace prostřednictvím archivu. Mezi příklady patří databáze programy, programy, které upravovat pouze části velkých souborů, programy, které zapisovat pouze textové soubory a programy, které sdílejí datových souborů.  
  
 V těchto případech je možné přepsat [serializace](../mfc/reference/cobject-class.md#serialize) funkce, které zprostředkovává akce souboru prostřednictvím jiným způsobem [cfile –](../mfc/reference/cfile-class.md) objekt ne [CArchive](../mfc/reference/carchive-class.md) objektu.  
  
 Můžete použít `Open`, `Read`, `Write`, `Close`, a `Seek` členské funkce třídy `CFile` k otevření souboru, přesuňte ukazatel na soubor (Hledat) na konkrétní bod v souboru přečíst záznam (zadaný počet bajtů ) v tomto bodě mohl uživatel aktualizovat záznam, pak znovu hledat do stejného bodu a zápisu záznamu do souboru. Rozhraní bude pro vás otevřete soubor, a můžete `GetFile` funkce člena třídy `CArchive` k získání ukazatele na `CFile` objektu. Pro použití i více sofistikovaná a flexibilní, je možné přepsat [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) a [OnSaveDocument](../mfc/reference/cdocument-class.md#onsavedocument) členské funkce třídy `CWinApp`. Další informace najdete v tématu třídy [cfile –](../mfc/reference/cfile-class.md) v *odkaz knihovny MFC*.  
  
 V tomto scénáři vaše `Serialize` přepsání nic neprovádí, pokud například chcete jej číst a zapisovat záhlaví souboru chcete zachovat aktuální při zavření dokumentu.  
  
## <a name="see-also"></a>Viz také  
 [Použití dokumentů](../mfc/using-documents.md)

