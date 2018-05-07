---
title: Naplnění seznamu z druhé sady záznamů (MFC Data Access) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- record views, filling list boxes
- list boxes, filling from second recordset
- recordsets [C++], filling list boxes or combo boxes
- CComboBox class, filling object from second rowset
- ODBC recordsets [C++], filling list boxes or combo boxes
- combo boxes [C++], filling from second recordset
- CListCtrl class, filling from second recordset
ms.assetid: 360c0834-da6b-4dc0-bcea-80e9acd611f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ed294527b4335459ab6d0658d9f57a5cb64a8fd1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="filling-a-list-box-from-a-second-recordset--mfc-data-access"></a>Naplnění seznamu z druhé sady záznamů (Data MFC Access)
Ve výchozím nastavení je přidružen jeden záznamů objekt, jehož pole jsou namapované na ovládací prvky zobrazení záznamu zobrazení záznamů. V některých případech můžete chtít put pole se seznamem nebo pole se seznamem řízení v zobrazení záznamu a vyplňte v něm hodnotami z druhého objekt sady záznamů. Uživatel může použít pole se seznamem a vyberte novou kategorii informace zobrazené v zobrazení záznamů. Toto téma vysvětluje, jak a kdy k tomu.  
  
> [!TIP]
>  Mějte na paměti naplnění – pole se seznamem nebo pole se seznamem ze zdroje dat může být pomalé. Preventivní opatření proti pokusu vyplnění ovládacího prvku ze sady záznamů s velkému počtu záznamů.  
  
 Model pro toto téma se skládá z primární sady záznamů, které doplní ovládacích prvků formuláře, dokud sekundární sada záznamů nenaplní pole se seznamem nebo pole se seznamem. Výběr řetězec z pole se seznamem způsobí, že vaše programu Requery – primární záznamů založené na co nebyla vybrána. Následující postup používá pole se seznamem, ale platí stejně pro pole se seznamem.  
  
#### <a name="to-fill-a-combo-box-or-list-box-from-a-second-recordset"></a>Chcete-li vyplnit pole se seznamem nebo seznamu z druhé sady záznamů  
  
1.  Vytvořit objekt sady záznamů ([CRecordset](../mfc/reference/crecordset-class.md).  
  
2.  Získání ukazatele na [CComboBox](../mfc/reference/ccombobox-class.md) objekt ovládacího prvku pole se seznamem.  
  
3.  Prázdné pole se seznamem všech předchozích obsahu.  
  
4.  Pohyb všechny záznamy v sadě záznamů volání [CComboBox::AddString](../mfc/reference/ccombobox-class.md#addstring) pro každý řetězec z aktuální záznam, který chcete přidat do pole se seznamem.  
  
5.  Inicializujte výběr v pole se seznamem.  
  
```  
void CSectionForm::OnInitialUpdate()  
{  
    // ...  
  
    // Fill the combo box with all of the courses  
    CENROLLDoc* pDoc = GetDocument();  
    if (!pDoc->m_courseSet.Open())  
        return;  
  
    // ...  
  
    m_ctlCourseList.ResetContent();  
    if (pDoc->m_courseSet.IsOpen())  
    {   
        while (!pDoc->m_courseSet.IsEOF() )  
        {  
            m_ctlCourseList.AddString(  
                pDoc->m_courseSet.m_CourseID);  
            pDoc->m_courseSet.MoveNext();  
        }  
    }  
    m_ctlCourseList.SetCurSel(0);  
}  
```  
  
 Tato funkce využívá druhé sady záznamů, `m_courseSet`, který obsahuje záznam pro každý kurz, kterou nabízí a `CComboBox` řízení, `m_ctlCourseList`, který je uložen ve třídě zobrazení záznamu.  
  
 Získá funkce `m_courseSet` z dokumentu a otevře ji. Pak vyprázdní `m_ctlCourseList` a pomocí posouvá `m_courseSet`. Pro každý záznam volá funkci pole se seznamem `AddString` – členská funkce přidání hodnota ID kurzu ze záznamu. Nakonec kód nastaví se seznamem se výběr pole.  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení záznamů (Data MFC Access)](../data/record-views-mfc-data-access.md)   
 [Seznam ovladačů ODBC](../data/odbc/odbc-driver-list.md)