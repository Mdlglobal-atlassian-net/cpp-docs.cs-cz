---
title: Zaznamenejte kód zobrazení vytvořené průvodcem aplikací (MFC Data Access) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- application wizards [C++], record view code
- record views, refreshing controls
- record views, application wizard code
ms.assetid: 18fd4703-5939-491d-b759-985f767b951f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 15355d156b3c85c8f99ba638b30f831da96686af
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="record-view-code-created-by-application-wizard--mfc-data-access"></a>Kód zobrazení záznamu vytvořený pomocí Průvodce aplikací (Data MFC Access)
[Průvodce aplikací knihovny MFC](../mfc/reference/database-support-mfc-application-wizard.md) zobrazení přepsání `OnInitialUpdate` a `OnGetRecordset` členské funkce. Poté, co rozhraní framework vytvoří oken s rámečkem, dokumentů a zobrazení, volá `OnInitialUpdate` k inicializaci zobrazení. `OnInitialUpdate` získá ukazatel na sadu záznamů z dokumentu. Základní třídy [CView::OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) funkce otevře sadu záznamů. Následující kód ukazuje tohoto postupu `CRecordView`:  
  
```  
void CSectionForm::OnInitialUpdate()  
{  
   m_pSet = &GetDocument()->m_sectionSet;  
   CRecordView::OnInitialUpdate();  
}  
```  
  
 Když se otevře sadu záznamů, vybere záznamy. [CRecordset::Open](../mfc/reference/crecordset-class.md#open) umožňuje na první záznam aktuální záznam a DDX přesune data ze sady záznamů pole datových členů do odpovídajících formuláři ovládací prvky v zobrazení. Další informace o RFX najdete v tématu [výměna pole záznamu (RFX)](../data/odbc/record-field-exchange-rfx.md). Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../mfc/dialog-data-exchange-and-validation.md). Informace o procesu vytváření dokumentů/zobrazení najdete v tématu [použití tříd pro zápis aplikace pro Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).  
  
> [!NOTE]
>  Je třeba přiřadit koncovým uživatelům možnost aktualizovat ovládací prvky zobrazení záznamu ze sady záznamů. Bez této schopnosti Pokud uživatel změní hodnotu ovládacího prvku na neplatnou hodnotu, uživatel může být trvale umístěny na aktuální záznam. Chcete-li aktualizovat ovládací prvky, zavolejte `CWnd` – členská funkce [UpdateData –](../mfc/reference/cwnd-class.md#updatedata) s parametrem **FALSE**.  
  
## <a name="see-also"></a>Viz také  
 [Použití zobrazení záznamů](../data/using-a-record-view-mfc-data-access.md)