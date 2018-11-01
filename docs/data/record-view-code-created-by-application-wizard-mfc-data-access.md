---
title: Kód zobrazení záznamu vytvořený pomocí Průvodce aplikací (přístup k datům MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [C++], record view code
- record views, refreshing controls
- record views, application wizard code
ms.assetid: 18fd4703-5939-491d-b759-985f767b951f
ms.openlocfilehash: 5340926789925d8243ecd20c27537c9690582a41
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50427973"
---
# <a name="record-view-code-created-by-application-wizard--mfc-data-access"></a>Kód zobrazení záznamu vytvořený pomocí Průvodce aplikací (přístup k datům MFC)

[Průvodce aplikací knihovny MFC](../mfc/reference/database-support-mfc-application-wizard.md) přepisuje zobrazení `OnInitialUpdate` a `OnGetRecordset` členské funkce. Poté, co rozhraní vytvoří okno rámce, dokumentů a zobrazení, volá `OnInitialUpdate` k inicializaci zobrazení. `OnInitialUpdate` získá ukazatel na sadu záznamů z dokumentu. Volání základní třídy [CView::OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) funkce otevře sadu záznamů. Následující kód ukazuje tento proces `CRecordView`:

```cpp
void CSectionForm::OnInitialUpdate()
{
   m_pSet = &GetDocument()->m_sectionSet;
   CRecordView::OnInitialUpdate();
}
```

Po otevření sady záznamů vybírá záznamy. [CRecordset::Open](../mfc/reference/crecordset-class.md#open) provede první záznam na aktuální záznam a DDX přesune data ze sady záznamů pole datových členů na odpovídající ovládací prvky formuláře v zobrazení. Další informace o RFX najdete v tématu [výměna pole záznamu (RFX)](../data/odbc/record-field-exchange-rfx.md). Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../mfc/dialog-data-exchange-and-validation.md). Informace o procesu vytváření dokumentů/zobrazení najdete v tématu [použití tříd pro zápis aplikace pro Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).

> [!NOTE]
>  Měl dát koncovým uživatelům možnost aktualizovat zobrazení záznamu ovládací prvky ze sady záznamů. Bez této schopnosti Pokud uživatel změní hodnotu ovládacího prvku na neplatnou hodnotu, uživatel může trvale uvíznout na aktuální záznam. Chcete-li aktualizovat ovládací prvky, zavolejte `CWnd` členskou funkci [UpdateData](../mfc/reference/cwnd-class.md#updatedata) s parametrem hodnotu FALSE.

## <a name="see-also"></a>Viz také

[Použití zobrazení záznamů](../data/using-a-record-view-mfc-data-access.md)