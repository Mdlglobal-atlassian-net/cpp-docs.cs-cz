---
title: "Přidání ovládacích prvků ručně | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Windows common controls [MFC], adding
- dialog box controls [MFC], adding to dialog boxes
- controlling input focus
- input focus control
- focus, controlling input [MFC]
- controls [MFC], adding to dialog boxes
- common controls [MFC], adding
ms.assetid: bc843e59-0c51-4b5b-8bf2-343f716469d2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b13f6fdfb3c11819eb8d8838e5617e7a349d1023
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="adding-controls-by-hand"></a>Ruční přidání ovládacích prvků
Můžete buď [přidání ovládacích prvků do dialogového okna pomocí editoru dialogových oken](../mfc/using-the-dialog-editor-to-add-controls.md) nebo je přidat sami, s kódem.  
  
 Pokud chcete vytvořit objekt ovládacího prvku, bude obvykle vložení C++ objekt ovládacího prvku v dialogovém okně C++ nebo objekt oken s rámečkem. Ovládací prvky jako mnoho dalších objektů v rámci vyžadují dvoufázová konstrukce. By měly volat ovládacího prvku **vytvořit** – členská funkce v rámci vytváření nadřazeného dialogové okno pole nebo rámce okna. Pro dialogová okna, to se obvykle provádí v [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)a okna s rámečkem v [OnCreate](../mfc/reference/cwnd-class.md#oncreate).  
  
 Následující příklad ukazuje, jak může deklarovat `CEdit` objektu v deklaraci třídy třídy odvozené dialogového okna a potom zavolejte **vytvořit** – členská funkce v `OnInitDialog`. Protože `CEdit` objektu je deklarovaný jako objekt, je automaticky vytvořený, když je vytvořený objektu dialogového okna, ale musí inicializovat stále vlastní **vytvořit** – členská funkce.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#1](../mfc/codesnippet/cpp/adding-controls-by-hand_1.h)]  
  
 Následující `OnInitDialog` funkce nastaví obdélníku, pak zavolá **vytvořit** vytvoření ovládacího prvku úprav Windows a jeho připojení k Neinicializovaný `CEdit` objektu.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#2](../mfc/codesnippet/cpp/adding-controls-by-hand_2.cpp)]  
  
 Po vytvoření upravit objekt, můžete také nastavit zaměření pro vstup do ovládacího prvku pomocí volání `SetFocus` – členská funkce. Nakonec se vraťte 0 z `OnInitDialog` zobrazíte fokus nastavit. Pokud jste vrátí nenulovou hodnotu, dialogové okno správce nastaví fokus na první položku ovládacího prvku v dialogovém okně položky seznamu. Ve většině případů budete chtít přidat ovládací prvky dialogových oken s editoru dialogových oken.  
  
## <a name="see-also"></a>Viz také  
 [Příprava a použití ovládacích prvků](../mfc/making-and-using-controls.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)   
 [CDialog::OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)

