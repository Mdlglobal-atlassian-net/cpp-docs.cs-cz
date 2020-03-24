---
title: Kód zobrazení záznamu vytvořený pomocí Průvodce aplikací (přístup k datům MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [C++], record view code
- record views, refreshing controls
- record views, application wizard code
ms.assetid: 18fd4703-5939-491d-b759-985f767b951f
ms.openlocfilehash: 69bebe978d03e5777f20765ac0bcf9a344f69320
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209154"
---
# <a name="record-view-code-created-by-application-wizard--mfc-data-access"></a>Kód zobrazení záznamu vytvořený pomocí Průvodce aplikací (přístup k datům MFC)

[Průvodce aplikací knihovny MFC](../mfc/reference/database-support-mfc-application-wizard.md) Přepisuje `OnInitialUpdate` a `OnGetRecordset` členské funkce zobrazení. Poté, co rozhraní vytvoří okno rámce, dokument a zobrazení, zavolá `OnInitialUpdate` k inicializaci zobrazení. `OnInitialUpdate` získá ukazatel na sadu záznamů z dokumentu. Volání základní třídy [CView:: OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) otevře sadu záznamů. Následující kód ukazuje tento proces pro `CRecordView`:

```cpp
void CSectionForm::OnInitialUpdate()
{
   m_pSet = &GetDocument()->m_sectionSet;
   CRecordView::OnInitialUpdate();
}
```

Když se sada záznamů otevře, vybere záznamy. [CRecordset:: Open](../mfc/reference/crecordset-class.md#open) vytvoří první záznam s aktuálním záznamem a DDX přesune data z datových členů pole sady záznamů do odpovídajících ovládacích prvků formuláře v zobrazení. Další informace o RFX naleznete v tématu [Výměna pole záznamu (RFX)](../data/odbc/record-field-exchange-rfx.md). Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../mfc/dialog-data-exchange-and-validation.md). Informace o procesu vytváření dokumentu/zobrazení najdete v tématu [použití tříd pro psaní aplikací pro Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).

> [!NOTE]
>  Koncovým uživatelům byste měli poskytnout možnost aktualizovat ovládací prvky zobrazení záznamu ze sady záznamů. Bez této možnosti platí, že pokud uživatel změní hodnotu ovládacího prvku na neplatnou hodnotu, uživatel může u aktuálního záznamu trvale zablokovat. Chcete-li aktualizovat ovládací prvky, zavolejte členskou funkci `CWnd` [UpdateData](../mfc/reference/cwnd-class.md#updatedata) s parametrem false.

## <a name="see-also"></a>Viz také

[Používání zobrazení záznamu](../data/using-a-record-view-mfc-data-access.md)
