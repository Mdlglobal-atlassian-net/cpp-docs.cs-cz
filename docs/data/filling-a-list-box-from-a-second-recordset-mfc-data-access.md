---
title: Naplnění seznamu druhou sadou záznamů (přístup k datům MFC) | Dokumentace Microsoftu
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
ms.openlocfilehash: ee56369948cbfbaff57a0f848da1b8b27bf309fe
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078046"
---
# <a name="filling-a-list-box-from-a-second-recordset--mfc-data-access"></a>Naplnění seznamu druhou sadou záznamů (přístup k datům MFC)

Ve výchozím zobrazení záznamů souvisí s objektem jedné sady záznamů, jejichž pole jsou namapované na ovládací prvky zobrazení záznamu. Někdy můžete chtít umístit seznamu nebo pole se seznamem ovládacího prvku v zobrazení záznamu a naplnit hodnotami z druhého objektu sady záznamů. Uživatele můžete použít pole se seznamem vyberte novou kategorii informací, které mají zobrazit v zobrazení záznamů. Toto téma vysvětluje, jak a kdy k tomu.  
  
> [!TIP]
>  Mějte na paměti vyplnění pole se seznamem nebo seznamu pole ze zdroje dat může být pomalé. Opatření proti pokusu vyplníte ovládací prvek ze sady záznamů s velké množství záznamů.  
  
Model pro toto téma se skládá z primární záznamů, který vyplní ovládací prvky formuláře, když sekundární záznamů vyplní pole se seznamem nebo pole se seznamem. Výběr řetězce z pole se seznamem způsobí, že program k requery primární záznamů podle co byla vybrána. Následující postup používá pole se seznamem, ale platí také pro pole se seznamem.  
  
#### <a name="to-fill-a-combo-box-or-list-box-from-a-second-recordset"></a>K vyplnění pole se seznamem nebo seznamu z druhé sady záznamů  
  
1. Vytvořit objekt sady záznamů ([CRecordset](../mfc/reference/crecordset-class.md).  
  
1. Získat ukazatel [CComboBox](../mfc/reference/ccombobox-class.md) objekt pro prvek pole se seznamem.  
  
1. Prázdná pole se seznamem jakékoli předchozí obsah.  
  
1. Přesuňte si všechny záznamy v sadě záznamů volání [CComboBox::AddString](../mfc/reference/ccombobox-class.md#addstring) pro každý řetězec z aktuální záznam, který chcete přidat do pole se seznamem.  
  
1. Inicializujte výběr v poli se seznamem.  
  
```cpp  
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
  
Tato funkce využívá druhé sady záznamů `m_courseSet`, který obsahuje záznam pro každou hodnoceného a `CComboBox` ovládacího prvku, `m_ctlCourseList`, které je uložený ve třídě zobrazení záznamu.  
  
Získá funkce `m_courseSet` z dokumentu a otevře jej. Pak vyprázdní `m_ctlCourseList` a procházení `m_courseSet`. Pro každý záznam, volá funkci pole se seznamem `AddString` členské funkce a přidejte požadovanou hodnotu ID kurzu ze záznamu. Nakonec kód nastaví pole se seznamem výběru pole.  
  
## <a name="see-also"></a>Viz také  

[Zobrazení záznamů (přístup k datům MFC)](../data/record-views-mfc-data-access.md)<br/>
[Seznam ovladačů ODBC](../data/odbc/odbc-driver-list.md)