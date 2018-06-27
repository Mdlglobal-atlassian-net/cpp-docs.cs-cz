---
title: Použití dialogového pruhu s ovládacím prvkem matrice | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- WM_EX_TRANSPARENT
dev_langs:
- C++
helpviewer_keywords:
- WS_EX_TRANSPARENT style
- rebar controls [MFC], dialog bars
- dialog bars [MFC], using with rebar bands
ms.assetid: e528cea0-6b81-4bdf-9643-7c03b6176590
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa2628df5f446105e6b7881709a0c72c19fe230e
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36950487"
---
# <a name="using-a-dialog-bar-with-a-rebar-control"></a>Použití dialogového pruhu s ovládacím prvkem matrice
Jak je uvedeno v [matrice – ovládací prvky a pruhy](../mfc/rebar-controls-and-bands.md), každý vzdálené správy může obsahovat pouze jeden podřízený okno (nebo ovládací prvek). To může být omezení, pokud chcete mít více než jeden podřízeného okna na vzdálené správy. Vhodné řešení je vytvořte zdroj panel dialogového okna s více ovládacích prvků a pak přidejte do ovládacího prvku matrice pásmo matrice (obsahující panel dialogového okna).  
  
 Pokud byste chtěli vzdálené panelu dialogové okno zobrazí transparentní, za normálních okolností byste nastavili ws_ex_transparent – rozšířený styl pro objektu panel dialogového okna. Ale protože ws_ex_transparent – má některé problémy s správně vykreslování pozadí panel dialogového okna, musíte udělat ještě další práci k dosažení požadované účinek.  
  
 Následující postup podrobnosti kroky potřebné k dosažení průhlednosti bez použití ws_ex_transparent – rozšířený styl.  
  
### <a name="to-implement-a-transparent-dialog-bar-in-a-rebar-band"></a>K implementaci transparentní dialogového pruhu ve svazku matrice  
  
1.  Pomocí [dialogové okno Přidat třídu](../mfc/reference/adding-an-mfc-class.md), přidejte novou třídu (například `CMyDlgBar`), která implementuje vaše objektu panel dialogového okna.  
  
2.  Přidání obslužné rutiny zpráv WM_ERASEBKGND.  
  
3.  V nové obslužnou rutinu upravte existující kód upravíte tak, aby odpovídaly v následujícím příkladu:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#29](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_1.cpp)]  
  
4.  Přidání obslužné rutiny zpráv WM_MOVE.  
  
5.  V nové obslužnou rutinu upravte existující kód upravíte tak, aby odpovídaly v následujícím příkladu:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#30](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_2.cpp)]  
  
 Nové obslužné rutiny simulovat průhlednost dialogového pruhu předávání zpráv WM_ERASEBKGND do nadřazeného okna a vynucení překreslit pokaždé, když je přesunut objektu panel dialogového okna.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

