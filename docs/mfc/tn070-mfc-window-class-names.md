---
title: "TN070: MFC – názvy tříd oken | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.classes
dev_langs: C++
helpviewer_keywords:
- window class names [MFC]
- TN070 [MFC]
ms.assetid: 90617912-dd58-4a7c-9082-ced71736d7cd
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6a652d4306e01d15d49ae6f931041d3d5dd9909f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [TN020: ID konvence pojmenování a číslování](../mfc/tn020-id-naming-and-numbering-conventions.md)

