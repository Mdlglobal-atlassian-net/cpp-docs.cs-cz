---
title: Správce vizualizace | Dokumentace Microsoftu
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
ms.openlocfilehash: fce4b036c6a6ae3692353ae02e7d36eb5ddfd1e1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46398481"
---
# <a name="visualization-manager"></a>Správce vizualizace

Správce vzhledu je objekt, který řídí vzhled aplikaci jako celek. Jako jednu třídu funguje, kde můžete ukládat výkresu kódu pro vaši aplikaci. Knihovna MFC obsahuje několik vizuální vedoucí. Můžete také vytvořit vlastní správce vzhledu, pokud chcete vytvořit vlastní zobrazení pro vaši aplikaci. Následující obrázky znázorňují tu samou aplikaci, pokud jsou povolené vizuální vedoucí jiné:

![Moje aplikace podle vykreslení CMFCVisualManagerWindows](../mfc/media/vmwindows.png "vmwindows") Moje aplikace, která používá správce vzhledu CMFCVisualManagerWindows –

![Moje aplikace podle vykreslení CMFCVisualManagerVS2005](../mfc/media/vmvs2005.png "vmvs2005") Moje aplikace, která používá správce vzhledu CMFCVisualManagerVS2005 –

![Moje aplikace podle vykreslení CMFCVisualManagerOfficeXP](../mfc/media/vmofficexp.png "vmofficexp") Moje aplikace, která používá správce vzhledu CMFCVisualManagerOfficeXP –

![Moje aplikace podle vykreslení cmfcvisualmanageroffice2003 –](../mfc/media/vmoffice2003.png "vmoffice2003") Moje aplikace, která používá správce vzhledu cmfcvisualmanageroffice2003 –

![Moje aplikace podle vykreslení cmfcvisualmanageroffice2007 –](../mfc/media/msoffice2007.png "msoffice2007") Moje aplikace, která používá správce vzhledu cmfcvisualmanageroffice2007 –

Ve výchozím nastavení udržuje správce vzhledu kód pro vykreslování. pro více prvků grafického uživatelského rozhraní. Pokud chcete zadat vlastní elementy uživatelského rozhraní, budete muset přepsání metody související výkresu správce vzhledu. Seznam těchto metod najdete v tématu [cmfcvisualmanager – třída](../mfc/reference/cmfcvisualmanager-class.md). Metody, které můžete přepsat poskytnout vlastní vzhled jsou všechny metody, které začínají `OnDraw`.

Vaše aplikace může mít pouze jeden `CMFCVisualManager` objektu. Získat ukazatel na správce vzhledu aplikace, zavolejte statickou funkci [CMFCVisualManager::GetInstance](../mfc/reference/cmfcvisualmanager-class.md#getinstance). Protože dědí všechny vizuální vedoucí `CMFCVisualManager`, `CMFCVisualManager::GetInstance` metoda se ukazatel na příslušné správce vzhledu, i v případě, že vytvoříte vlastní správce vzhledu.

Pokud chcete vytvořit vlastní správce vzhledu, musí být odvozen z vizuálního správce, který již existuje. Je výchozí třídu odvodit z `CMFCVisualManager`. Můžete však použít jiný správce vzhledu pokud lépe vypadá podobně jako vhodné pro vaši aplikaci. Například, pokud jste chtěli `CMFCVisualManagerOffice2007` správce vzhledu, ale chtěli pouze Změna vzhledu oddělovače, můžou odvozovat vlastní třídu z `CMFCVisualManagerOffice2007`. V tomto scénáři byste měli přepsat pouze metody pro kreslení oddělovače.

Existují dva možné způsoby, jak použít konkrétní vizuálního správce pro vaši aplikaci. Jedním ze způsobů je zavolat [CMFCVisualManager::SetDefaultManager](../mfc/reference/cmfcvisualmanager-class.md#setdefaultmanager) a předáte odpovídající správce vzhledu jako parametr. Následující příklad kódu ukazuje, jak můžete využít `CMFCVisualManagerVS2005` správce vzhledu pomocí této metody:

```cpp
CMFCVisualManager::SetDefaultManager (RUNTIME_CLASS (CMFCVisualManagerVS2005));
```

Druhý způsob použití vizuálního správce ve vaší aplikaci je vytvořit ručně. Aplikace pak bude používat tento nový správce vzhledu pro vykreslení všech prvků. Ale vzhledem k tomu může dojít k pouze jednomu `CMFCVisualManager` objektu na aplikaci, bude mít odstranit aktuální správce vzhledu a teprve potom vytvořte novou. V následujícím příkladu `CMyVisualManager` je vlastní vizuálního správce, který je odvozen z `CMFCVisualManager`. Následující metody se změní, co správce vzhledu se používá k zobrazení vaší aplikace, v závislosti na indexu:

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

[Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)<br/>
[CMFCVisualManager – třída](../mfc/reference/cmfcvisualmanager-class.md)
