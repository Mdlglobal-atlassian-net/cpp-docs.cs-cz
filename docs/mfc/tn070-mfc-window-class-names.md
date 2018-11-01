---
title: 'TN070: MFC – názvy tříd oken'
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.classes
helpviewer_keywords:
- window class names [MFC]
- TN070 [MFC]
ms.assetid: 90617912-dd58-4a7c-9082-ced71736d7cd
ms.openlocfilehash: d59dc052cc253c8d036de0559018065e4ba7457d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50533611"
---
# <a name="tn070-mfc-window-class-names"></a>TN070: MFC – názvy tříd oken

> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována, protože byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata mohou být nesprávné nebo zastaralé. Nejnovější informace se doporučuje vyhledat téma zájmu v dokumentaci online index.

MFC windows použijte název dynamicky vytvořené třídy, která zohledňuje, funkce v okně. Knihovny MFC generuje názvy tříd dynamicky pro okna s rámečkem, zobrazení a automaticky otevírané okno windows vytvářené aplikace. Dialogová okna a ovládací prvky vytvořené metodou aplikace knihovny MFC mají Windows zadaný název třídy okna dotyčný.

Název dynamicky zadané třídy můžete nahradit pomocí registrace vlastní třídu okna a jeho použití v přepsání [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow). Jejich názvy tříd knihovny MFC zadaný zařadit do jedné z těchto dvou tvarů následující:

```
Afx:%x:%x
Afx:%x:%x:%x:%x:%x
```

Šestnáctkových číslic, které nahrazují `%x` znaky jsou vyplněna z dat z [WNDCLASS](https://msdn.microsoft.com/library/windows/desktop/ms633576) struktury. Knihovna MFC používá tuto techniku tak, aby více tříd jazyka C++ vyžaduje identické **WNDCLASS** struktury můžete sdílet stejnou třídu registrované oken. Na rozdíl od většiny jednoduchých aplikací Win32, aplikace knihovny MFC mít pouze jeden **WNDPROC**, takže můžete snadno sdílet **WNDCLASS** struktury ušetříte čas a paměti. Hodnoty pro nahraditelné `%x` znaky uvedené výše jsou následující:

- **WNDCLASS.hInstance**

- **WNDCLASS.style**

- **WNDCLASS.hCursor**

- **WNDCLASS.hbrBackground**

- **WNDCLASS.hIcon**

První formulář (`Afx:%x:%x`) se používá při **hCursor**, **hbrBackground**, a **hIcon** jsou všechny **NULL**.

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)<br/>
[TN020: Konvence pojmenování a číslování pro identifikátory](../mfc/tn020-id-naming-and-numbering-conventions.md)

