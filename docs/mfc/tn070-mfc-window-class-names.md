---
title: 'TN070: MFC – názvy tříd oken'
ms.date: 11/04/2016
helpviewer_keywords:
- window class names [MFC]
- TN070 [MFC]
ms.assetid: 90617912-dd58-4a7c-9082-ced71736d7cd
ms.openlocfilehash: 1d9b5de07bcc2545df6294557d1ac9f9d29e856c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513352"
---
# <a name="tn070-mfc-window-class-names"></a>TN070: MFC – názvy tříd oken

> [!NOTE]
>  Následující technická Poznámka nebyla od prvního zařazení do online dokumentace aktualizována. V důsledku toho mohou být některé postupy a témata neaktuální nebo nesprávné. Nejnovější informace najdete v tématu informace o tom, co je důležité v online katalogu dokumentace najít.

MFC Windows používá dynamicky vytvořený název třídy, který odráží funkce okna. Knihovna MFC generuje dynamicky názvy tříd pro okna oken, zobrazení a automaticky otevíraná okna vytvořená v rámci aplikace. Dialogová okna a ovládací prvky vytvářené aplikací knihovny MFC mají název zadaný v systému Windows pro příslušnou třídu okna.

Dynamicky poskytnutý název třídy můžete nahradit registrací vlastní třídy okna a jeho použitím v přepsání. [](../mfc/reference/cwnd-class.md#precreatewindow) Názvy tříd poskytovaných v knihovně MFC odpovídají jednomu z těchto dvou forem:

```
Afx:%x:%x
Afx:%x:%x:%x:%x:%x
```

Šestnáctkové číslice, které nahrazují `%x` znaky, jsou vyplněny z dat ze struktury [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw) . Knihovna MFC používá tuto techniku, takže C++ více tříd vyžadujících identické struktury **WNDCLASS** může sdílet stejnou registrovanou třídu okna. Na rozdíl od většiny jednoduchých aplikací Win32 mají aplikace MFC pouze jeden **WndProc**, takže můžete snadno sdílet struktury **WNDCLASS** a ušetřit tak čas a paměť. Nahraditelné hodnoty pro `%x` výše zobrazené znaky jsou následující:

- **WNDCLASS. hInstance**

- **WNDCLASS. Style**

- **WNDCLASS.hCursor**

- **WNDCLASS.hbrBackground**

- **WNDCLASS.hIcon**

`Afx:%x:%x`První tvar () se používá v případě, že jsou **hCursor**, **hbrBackground**a **HICON** všechny **hodnoty null**.

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)<br/>
[TN020: Konvence pojmenování a číslování pro identifikátory](../mfc/tn020-id-naming-and-numbering-conventions.md)
