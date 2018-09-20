---
title: Použití zobrazení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interacting with users and role of view class [MFC]
- drawing [MFC], data
- rendering data
- view classes [MFC], role in managing user interaction
- CView class [MFC], view architecture
- MFC, views
- views [MFC], using
- painting data
- user input [MFC], interpreting through view class [MFC]
- view classes [MFC], role in displaying application data
ms.assetid: dc3de6ad-5c64-4317-8f10-8bdcc38cdbd5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fcf4af038617cce8326a3e63ba9b4ea66c277f66
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442094"
---
# <a name="using-views"></a>Použití zobrazení

Odpovědnosti v zobrazení se graficky zobrazit data dokumentu pro uživatele a přijmout a interpretace vstupu uživatele jako operace v dokumentu. Vaše úkoly při psaní zobrazit třídu jsou:

- Zápis zobrazení třídy [OnDraw](../mfc/reference/cview-class.md#ondraw) členskou funkci, která vykresluje data dokumentu.

- Připojení k obslužná rutina zprávy členské funkce ve třídě zobrazení příslušné zprávy Windows a objekty uživatelského rozhraní, jako jsou položky nabídky.

- Implementujte tyto rutiny interpretace vstupu uživatele.

Kromě toho je nutné přepsat jiné `CView` členské funkce ve třídě odvozené zobrazení. Konkrétně můžete chtít přepsat [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) k provádění speciálních inicializace pro zobrazení a [OnUpdate](../mfc/reference/cview-class.md#onupdate) provést žádné speciální zpracování potřeba těsně před plánovaným začátkem zobrazení překreslí samotný. Vícestránkové dokumenty, je také nutné přepsat [OnPreparePrinting –](../mfc/reference/cview-class.md#onprepareprinting) Inicializace dialogového okna Tisk s číslem stránky k tisku a další informace. Další informace o přepsání `CView` členských funkcích třídy naleznete v tématu [CView](../mfc/reference/cview-class.md) v *odkaz knihovny MFC*.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Odvozené třídy zobrazení dostupné v prostředí MFC](../mfc/derived-view-classes-available-in-mfc.md)

- [Kreslení v zobrazení](../mfc/drawing-in-a-view.md)

- [Interpretace vstupu uživatele prostřednictvím zobrazení](../mfc/interpreting-user-input-through-a-view.md)

- [Role zobrazení v tisku](../mfc/role-of-the-view-in-printing.md)

- [Posouvání a změna měřítka zobrazení](../mfc/scrolling-and-scaling-views.md)

- [Inicializace a Uklízení dokumentů a zobrazení](../mfc/initializing-and-cleaning-up-documents-and-views.md)

## <a name="see-also"></a>Viz také

[Document/View – architektura](../mfc/document-view-architecture.md)<br/>
[CFormView – třída](../mfc/reference/cformview-class.md)<br/>
[Zobrazení záznamů (přístup k datům MFC)](../data/record-views-mfc-data-access.md)<br/>
[Obcházení mechanismu serializace](../mfc/bypassing-the-serialization-mechanism.md)

