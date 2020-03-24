---
title: Naplnění seznamu z druhé sady záznamů (přístup k datům MFC)
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
ms.openlocfilehash: 8eb2525ef8b749f58303cae13b87b21d7df73d1b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213405"
---
# <a name="filling-a-list-box-from-a-second-recordset--mfc-data-access"></a>Naplnění seznamu z druhé sady záznamů (přístup k datům MFC)

Ve výchozím nastavení je zobrazení záznamu přidruženo k jednomu objektu sady záznamů, jejichž pole jsou mapována na ovládací prvky zobrazení záznamu. Někdy můžete chtít umístit ovládací prvek seznamu nebo pole se seznamem do zobrazení záznamu a vyplnit ho hodnotami z druhého objektu sady záznamů. Uživatel může použít seznam pro výběr nové kategorie informací, které se mají zobrazit v zobrazení záznamu. Toto téma vysvětluje, jak a kdy to uděláte.

> [!TIP]
>  Uvědomte si, že vyplnění pole se seznamem nebo seznamu ze zdroje dat může být pomalé. Proveďte preventivní opatření proti pokusu o vyplnění ovládacího prvku ze sady záznamů s velkým počtem záznamů.

Model pro toto téma se skládá z primární sady záznamů, která vyplní ovládací prvky formuláře, zatímco sekundární sada záznamů vyplní seznam nebo pole se seznamem. Výběr řetězce ze seznamu způsobí, že program spustí dotaz na primární sadu záznamů na základě toho, co byl vybrán. Následující postup používá pole se seznamem, ale platí stejně pro seznam.

#### <a name="to-fill-a-combo-box-or-list-box-from-a-second-recordset"></a>Vyplnění pole se seznamem nebo seznamu z druhé sady záznamů

1. Vytvořte objekt sady záznamů ([CRecordset](../mfc/reference/crecordset-class.md).

1. Získejte ukazatel na objekt [CComboBox –](../mfc/reference/ccombobox-class.md) pro ovládací prvek pole se seznamem.

1. Vyprázdněte pole se seznamem libovolného předchozího obsahu.

1. Procházejte všemi záznamy v sadě záznamů, voláním [CComboBox –:: AddString](../mfc/reference/ccombobox-class.md#addstring) pro každý řetězec z aktuálního záznamu, který chcete přidat do pole se seznamem.

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

Tato funkce používá druhou sadu záznamů, `m_courseSet`, která obsahuje záznam pro každý kurz, který je k dispozici, a ovládací prvek `CComboBox`, `m_ctlCourseList`, který je uložen ve třídě zobrazení záznamu.

Funkce získá `m_courseSet` z dokumentu a otevře ji. Pak vyprázdní `m_ctlCourseList` a posuňte se přes `m_courseSet`. Pro každý záznam funkce volá členskou funkci `AddString` pole se seznamem, aby přidala hodnotu ID kurzu ze záznamu. Nakonec kód nastaví výběr pole se seznamem.

## <a name="see-also"></a>Viz také

[Zobrazení záznamů (přístup k datům MFC)](../data/record-views-mfc-data-access.md)<br/>
[Seznam ovladačů ODBC](../data/odbc/odbc-driver-list.md)
