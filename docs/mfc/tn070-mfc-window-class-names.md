---
title: 'TN070: MFC – názvy tříd oken | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.classes
dev_langs:
- C++
helpviewer_keywords:
- window class names [MFC]
- TN070 [MFC]
ms.assetid: 90617912-dd58-4a7c-9082-ced71736d7cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c66c434503bbd2c6d7ee1b0557fa73d843e0caaa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385349"
---
# <a name="tn070-mfc-window-class-names"></a>TN070: MFC – názvy tříd oken
> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována vzhledem k tomu, že byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata může být zastaralý nebo není správný. Nejnovější informace se doporučuje, vyhledejte téma týkající se v indexu online dokumentaci.  
  
 MFC windows použijte název dynamicky vytvořené třídy, která zobrazuje funkce okna. MFC – třída vygeneruje názvy vyhledaných dynamicky okna s rámečkem, zobrazení a místní windows vytvořeného pomocí aplikace. Dialogová okna a vyprodukované aplikace MFC – ovládací prvky mají Windows zadaný název pro třídu okna nejistá.  
  
 Můžete nahradit název dynamicky zadané třídy pomocí registrace třídě okna a jeho použití přepsání [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow). Názvy tříd MFC zadané zařadit do jedné z těchto dvou:  
  
```  
Afx:%x:%x  
Afx:%x:%x:%x:%x:%x  
```  
  
 Šestnáctkových číslic, které nahrazují `%x` znaky jsou vyplněno z dat z [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) struktury. MFC používá tato technika tak, aby více třídy C++ vyžadující identické **WNDCLASS** struktury můžete sdílet stejnou třídu registrované okno. Na rozdíl od většiny jednoduché aplikace Win32 MFC aplikací mít jenom jeden **WNDPROC**, takže můžete snadno sdílet **WNDCLASS** struktury ušetříte čas a paměti. Nahraditelné hodnoty `%x` znaky uvedené výše jsou následující:  
  
- **WNDCLASS.hInstance**  
  
- **WNDCLASS.style**  
  
- **WNDCLASS.hCursor**  
  
- **WNDCLASS.hbrBackground**  
  
- **WNDCLASS.hIcon**  
  
 První formulář (`Afx:%x:%x`) se používá při **hCursor**, **hbrBackground**, a **hIcon** jsou všechny **NULL**.  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)   
 [TN020: Konvence pojmenování a číslování pro identifikátory](../mfc/tn020-id-naming-and-numbering-conventions.md)

