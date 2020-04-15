---
title: Kód zobrazení záznamů vytvořený Průvodcem aplikací (Přístup k datům knihovny MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [C++], record view code
- record views, refreshing controls
- record views, application wizard code
ms.assetid: 18fd4703-5939-491d-b759-985f767b951f
ms.openlocfilehash: 69481299980329b98e378f02e090670fa3d7ece2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376024"
---
# <a name="record-view-code-created-by-application-wizard--mfc-data-access"></a>Kód zobrazení záznamů vytvořený Průvodcem aplikací (Přístup k datům knihovny MFC)

[Průvodce aplikací knihovny MFC](../mfc/reference/database-support-mfc-application-wizard.md) přepíše funkce zobrazení `OnInitialUpdate` a `OnGetRecordset` členů. Po rozhraní vytvoří okno rámce, dokument a `OnInitialUpdate` zobrazení, volá k inicializaci zobrazení. `OnInitialUpdate`získá ukazatel na sadu záznamů z dokumentu. Volání základní třídy [CView::OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) funkce otevře sadu záznamů. Následující kód ukazuje tento `CRecordView`proces pro :

```cpp
void CSectionForm::OnInitialUpdate()
{
   m_pSet = &GetDocument()->m_sectionSet;
   CRecordView::OnInitialUpdate();
}
```

Když se sada záznamů otevře, vybere záznamy. [CRecordset::Open](../mfc/reference/crecordset-class.md#open) vytvoří první záznam aktuálního záznamu a DDX přesune data z datových členů pole sady záznamů do odpovídajících ovládacích prvků formuláře v zobrazení. Další informace o RFX naleznete v [tématu Record Field Exchange (RFX)](../data/odbc/record-field-exchange-rfx.md). Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../mfc/dialog-data-exchange-and-validation.md). Informace o procesu vytváření dokumentu nebo zobrazení naleznete [v tématu Použití tříd k zápisu aplikací pro systém Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).

> [!NOTE]
> Koncovým uživatelům byste měli dát možnost aktualizovat ovládací prvky zobrazení záznamů ze sady záznamů. Bez této funkce, pokud uživatel změní hodnotu ovládacího prvku na neplatnou hodnotu, může být uživatel trvale zablokovaný v aktuálním záznamu. Chcete-li aktualizovat ovládací `CWnd` prvky, volání členské funkce [UpdateData](../mfc/reference/cwnd-class.md#updatedata) s parametrem FALSE.

## <a name="see-also"></a>Viz také

[Použití zobrazení záznamů](../data/using-a-record-view-mfc-data-access.md)
