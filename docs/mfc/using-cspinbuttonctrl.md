---
title: Používání atributu CSpinButtonCtrl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CSpinButtonCtrl
dev_langs:
- C++
helpviewer_keywords:
- up-down controls [MFC], spin button control
- up-down controls
- spin button control
- CSpinButtonCtrl class [MFC], using
ms.assetid: a91db36b-e11e-42ef-8e89-51915cc486d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 03b1e83977c1d75070e8878dfdcc53c7afca7a86
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384397"
---
# <a name="using-cspinbuttonctrl"></a>Používání atributu CSpinButtonCtrl
*Číselníku* ovládací prvek (také označované jako *obousměrný číselník* ovládací prvek) poskytuje dvojice šipek, které uživatel klepnutím na tlačítko můžete upravit hodnotu. Tato hodnota se označuje jako *aktuální pozici*. Pozice zůstane v rozsahu číselníku. Když uživatel klikne na šipku nahoru, pozice blíží maximální; a když uživatel klikne na šipku dolů, pozice blíží minimální.  
  
 Ovládací prvek typu číselník tlačítko je reprezentována v prostředí MFC pomocí [CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md) třídy.  
  
> [!NOTE]
>  Ve výchozím nastavení má rozsah číselníku nastavit na nulu (0) maximální a minimální nastavena na hodnotu 100. Vzhledem k tomu, že maximální hodnota je menší než minimální hodnota, klikněte na šipku nahoru snižuje pozice a kliknutím na šipku dolů zvyšuje. Použití [CSpinButtonCtrl::SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) upravit tyto hodnoty.  
  
 Obvykle se zobrazí aktuální pozici v ovládacím prvku doprovodné. Ovládací prvek doprovodné se označuje jako *kamarád okno*. Obrázek ovládacího prvku typu číselník, najdete v části [o – ovládací prvky typu číselník](http://msdn.microsoft.com/library/windows/desktop/bb759889) ve Windows SDK.  
  
 Pro vytvoření ovládacího prvku typu číselník a okno kamarád ovládací prvek úprav v sadě Visual Studio, nejdřív přetáhněte ovládací prvek upravit nebo dialogovém okně a poté přetáhněte ovládací prvek typu číselník. Vyberte ovládací prvek typu číselník a nastavit jeho **automaticky kamarád** a **nastavit celé číslo kamarád** vlastnosti, které chcete **True**. Také nastavit **zarovnání** vlastnost; **Zarovnat vpravo** je nejčastější. S těmito nastaveními textové pole je nastaven jako okno kamarád protože přímo předchází ovládacího prvku úprav v pořadí. Tento ovládací prvek upravit zobrazí celá čísla a ovládací prvek typu číselník vložené na pravé straně ovládacích prvků pro úpravy. Volitelně můžete nastavit platný rozsah ovládací prvek typu číselník pomocí [CSpinButtonCtrl::SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) metoda. Žádné obslužné rutiny událostí jsou vyžadované pro komunikaci mezi kamarád okno a ovládací prvek typu číselník, protože si vyměňují data přímo. Pokud používáte ovládací prvek typu číselník pro některé jinému účelu, například na stránku prostřednictvím pořadí systému windows nebo dialogových oken, přidejte obslužnou rutinu pro `UDN_DELTAPOS` zpráva a provedení vlastní akce došlo.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Styly číselníků](../mfc/spin-button-styles.md)  
  
-   [Členské funkce číselníku](../mfc/spin-button-member-functions.md)  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky](../mfc/controls-mfc.md)

