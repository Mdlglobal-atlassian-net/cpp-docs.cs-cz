---
title: 'TN070: MFC – názvy tříd oken'
ms.date: 11/04/2016
helpviewer_keywords:
- window class names [MFC]
- TN070 [MFC]
ms.assetid: 90617912-dd58-4a7c-9082-ced71736d7cd
ms.openlocfilehash: ad43f5af5d2e90cb5fc2bc90f0909c2b495b4a4c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373488"
---
# <a name="tn070-mfc-window-class-names"></a>TN070: MFC – názvy tříd oken

> [!NOTE]
> Následující technická poznámka nebyla aktualizována od doby, kdy byla poprvé zahrnuta do online dokumentace. V důsledku toho mohou být některé postupy a témata zastaralé nebo nesprávné. Chcete-li získat nejnovější informace, doporučujeme vyhledat téma zájmu v online indexu dokumentace.

Okna knihovny MFC používají dynamicky vytvořený název třídy, který odráží funkce okna. Knihovna MFC dynamicky generuje názvy tříd pro okna, zobrazení a automaticky otevíraná okna vytvářená aplikací. Dialogová okna a ovládací prvky vytvořené aplikací knihovny MFC mají název dodaný systémem Windows pro danou třídu okna.

Dynamicky zadaný název třídy můžete nahradit registrací vlastní třídy okna a jeho použitím v přepsání [precreatewindow](../mfc/reference/cwnd-class.md#precreatewindow). Jejich názvy tříd dodaných knihovnou MFC odpovídají jedné ze dvou následujících forem:

```
Afx:%x:%x
Afx:%x:%x:%x:%x:%x
```

Šestnáctkové číslice, `%x` které nahrazují znaky, jsou vyplněny z dat ze struktury [WNDCLASS.](/windows/win32/api/winuser/ns-winuser-wndclassw) Knihovna MFC používá tuto techniku tak, aby více tříd jazyka C++ vyžadujících identické struktury **WNDCLASS** mohlo sdílet stejnou registrovanou třídu okna. Na rozdíl od většiny jednoduchých aplikací Win32 mají aplikace Knihovny MFC pouze **jednu službu WNDPROC**, takže můžete snadno sdílet struktury **WNDCLASS,** abyste ušetřili čas a paměť. Nahraditelné hodnoty výše `%x` uvedených znaků jsou následující:

- **INSTANCE WNDCLASS.hInstance**

- **WNDCLASS.styl**

- **WNDCLASS.hKurzor**

- **WNDCLASS.hbrPozadí**

- **Ikona souboru WNDCLASS.hIkona**

První formulář`Afx:%x:%x`( ) se používá, když **hCursor**, **hbrBackground**a **hIcon** jsou všechny **NULL**.

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)<br/>
[TN020: Konvence pojmenování a číslování pro identifikátory](../mfc/tn020-id-naming-and-numbering-conventions.md)
