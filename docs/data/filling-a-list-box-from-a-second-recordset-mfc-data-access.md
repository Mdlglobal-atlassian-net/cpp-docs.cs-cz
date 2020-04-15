---
title: Vyplnění seznamu ze druhé sady záznamů (přístup k datům knihovny MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, filling list boxes
- list boxes, filling from second recordset
- recordsets [C++], filling list boxes or combo boxes
- CComboBox class, filling object from second rowset
- ODBC recordsets [C++], filling list boxes or combo boxes
- combo boxes [C++], filling from second recordset
- CListCtrl class, filling from second recordset
ms.assetid: 360c0834-da6b-4dc0-bcea-80e9acd611f0
ms.openlocfilehash: 8664e98c6668568918cc0e6504a38119d2e71428
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336928"
---
# <a name="filling-a-list-box-from-a-second-recordset--mfc-data-access"></a>Vyplnění seznamu ze druhé sady záznamů (přístup k datům knihovny MFC)

Ve výchozím nastavení je zobrazení záznamů přidruženo k jedinému objektu sady záznamů, jehož pole jsou mapována na ovládací prvky zobrazení záznamů. Někdy můžete chtít umístit seznam nebo ovládací prvek pole se seznamem do zobrazení záznamu a vyplnit jej hodnotami z druhého objektu sady záznamů. Uživatel může pomocí seznamu vybrat novou kategorii informací, která se má zobrazit v zobrazení záznamu. Toto téma vysvětluje, jak a kdy to udělat.

> [!TIP]
> Uvědomte si, že vyplnění pole se seznamem nebo seznamu ze zdroje dat může být pomalé. Přijměte opatření proti pokusu o vyplnění ovládacího prvku ze sady záznamů velkým počtem záznamů.

Model pro toto téma se skládá z primární sady záznamů, která vyplňuje ovládací prvky formuláře, zatímco sekundární sada záznamů vyplňuje seznam nebo pole se seznamem. Výběr řetězce ze seznamu způsobí, že program znovu zadá dotaz na primární sadu záznamů na základě toho, co bylo vybráno. Následující postup používá pole se seznamem, ale platí stejně pro seznam.

#### <a name="to-fill-a-combo-box-or-list-box-from-a-second-recordset"></a>Vyplnění pole se seznamem nebo seznamu z druhé sady záznamů

1. Vytvořte objekt sady záznamů ([CRecordset](../mfc/reference/crecordset-class.md).

1. Získejte ukazatel na objekt [CComboBox](../mfc/reference/ccombobox-class.md) pro ovládací prvek pole se seznamem.

1. Vyprázdněte pole se seznamem všech předchozích obsahů.

1. Projděte všechny záznamy v sadě záznamů a najděte [CComboBox::AddString](../mfc/reference/ccombobox-class.md#addstring) pro každý řetězec z aktuálního záznamu, který chcete přidat do pole se seznamem.

1. Inicializovat výběr v poli se seznamem.

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

Tato funkce používá druhou `m_courseSet`sadu záznamů , která obsahuje záznam pro `CComboBox` každý `m_ctlCourseList`nabízený kurz, a ovládací prvek , který je uložen ve třídě zobrazení záznamu.

Funkce získá `m_courseSet` z dokumentu a otevře jej. Pak se `m_ctlCourseList` vyprázdní `m_courseSet`a posouvá se . Pro každý záznam funkce volá členská `AddString` funkce pole se seznamem, aby přidala hodnotu ID kurzu ze záznamu. Nakonec kód nastaví výběr pole se seznamem.

## <a name="see-also"></a>Viz také

[Zobrazení záznamů (přístup k datům knihovny MFC)](../data/record-views-mfc-data-access.md)<br/>
[Seznam ovladačů ODBC](../data/odbc/odbc-driver-list.md)
