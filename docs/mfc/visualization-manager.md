---
title: Správce vizualizace | Microsoft Docs
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visualization Manager
ms.assetid: c9dd1365-27ac-42e5-8caa-1004525b4129
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 590c21c3a628af3d8e4c7fc3e5cb0330a0af439a
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37123341"
---
# <a name="visualization-manager"></a>Správce vizualizace

Visual správce je objekt, který řídí vzhled aplikaci jako celek. Jako jednu třídu funguje, kde můžete ukládat všechny kód vykreslování pro aplikaci. Knihovny MFC zahrnuje několik visual správci. Můžete také vytvořit vlastní visual správce, pokud chcete vytvořit vlastní zobrazení pro vaši aplikaci. Následující obrázky znázorňují stejnou aplikaci, pokud jsou povolené různé visual správce:

 ![Moje aplikace podle vykreslení CMFCVisualManagerWindows](../mfc/media/vmwindows.png "vmwindows") Moje aplikace, který používá správce visual CMFCVisualManagerWindows

 ![Moje aplikace podle vykreslení CMFCVisualManagerVS2005](../mfc/media/vmvs2005.png "vmvs2005") Moje aplikace, který používá správce visual CMFCVisualManagerVS2005

 ![Moje aplikace podle vykreslení CMFCVisualManagerOfficeXP](../mfc/media/vmofficexp.png "vmofficexp") Moje aplikace, který používá správce visual CMFCVisualManagerOfficeXP

 ![Moje aplikace podle vykreslení CMFCVisualManagerOffice2003](../mfc/media/vmoffice2003.png "vmoffice2003") Moje aplikace, který používá správce visual CMFCVisualManagerOffice2003

 ![Moje aplikace podle vykreslení CMFCVisualManagerOffice2007](../mfc/media/msoffice2007.png "msoffice2007") Moje aplikace, který používá správce visual CMFCVisualManagerOffice2007

Ve výchozím nastavení udržuje správce visual kreslení kód pro několik elementy grafického uživatelského rozhraní. Pokud chcete zadat vlastní elementy uživatelského rozhraní, budete muset přepsat související metody kreslení visual správce. Seznam těchto metod najdete v tématu [CMFCVisualManager třída](../mfc/reference/cmfcvisualmanager-class.md). Metody, které můžete přepsat poskytnout vlastní vzhled jsou všechny metody, které začínají `OnDraw`.

Aplikace může mít jen jeden `CMFCVisualManager` objektu. K získání ukazatele na visual správce pro vaši aplikaci, zavolejte statickou funkci [CMFCVisualManager::GetInstance](../mfc/reference/cmfcvisualmanager-class.md#getinstance). Protože dědí všechny visual správce `CMFCVisualManager`, `CMFCVisualManager::GetInstance` metoda se ukazatel na příslušné visual správce, i v případě, že vytvoříte vlastní visual správce.

Pokud chcete vytvořit vlastní visual manager, musí být odvozeny od visual správce, který již existuje. Je odvozena od třídy pro výchozí `CMFCVisualManager`. Můžete však jiný visual manager pokud lépe podobá, co chcete použít pro vaše aplikace. Například, pokud jste chtěli použít `CMFCVisualManagerOffice2007` visual správce, ale chtěli pouze Změna vzhledu oddělovačů, může být vaše vlastní třídy z `CMFCVisualManagerOffice2007`. V tomto scénáři byste měli přepsat pouze metody pro kreslení oddělovačů.

Existují dvě možné způsoby, jak používat konkrétní visual správce pro vaši aplikaci. Jedním ze způsobů je volání [CMFCVisualManager::SetDefaultManager](../mfc/reference/cmfcvisualmanager-class.md#setdefaultmanager) metoda a předejte jí odpovídající visual manager jako parametr. Následující příklad kódu ukazuje, jak byste použili `CMFCVisualManagerVS2005` visual manager pomocí této metody:

```cpp
CMFCVisualManager::SetDefaultManager (RUNTIME_CLASS (CMFCVisualManagerVS2005));
```

Druhý způsob použití visual správce ve vaší aplikaci je vytvořit ručně. Aplikace pak bude používat tento nový visual správce pro všechny vykreslování. Ale vzhledem k tomu může být jen jeden `CMFCVisualManager` objektu na aplikaci, budete muset odstranit aktuální visual manager předtím, než vytvoříte nový. V následujícím příkladu `CMyVisualManager` je vlastní visual manager, který je odvozený od `CMFCVisualManager`. Následující metodu změní, jaké visual správce se používá k zobrazení vaší aplikace, v závislosti na index:

```cpp
void CMyApp::SetSkin (int index)
{
    if (CMFCVisualManager::GetInstance() != NULL)
    {
        delete CMFCVisualManager::GetInstance();
    }

    switch (index)
    {
    case DEFAULT_STYLE: 
        // The following statement creates a new CMFCVisualManager
        CMFCVisualManager::GetInstance();
        break;

    case CUSTOM_STYLE:
        new CMyVisualManager;
        break;

    default:
        CMFCVisualManager::GetInstance();
        break;
    }

    CMFCVisualManager::GetInstance()->RedrawAll();
}
```

## <a name="see-also"></a>Viz také:

[Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)  
[CMFCVisualManager – třída](../mfc/reference/cmfcvisualmanager-class.md)  
