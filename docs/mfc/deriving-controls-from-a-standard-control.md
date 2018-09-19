---
title: Odvozování ovládacích prvků ze standardního ovládacího prvku | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- standard controls [MFC], deriving controls from
- common controls [MFC], deriving from
- derived controls
- controls [MFC], derived
- Windows common controls [MFC], deriving from
- standard controls
ms.assetid: a6f84315-7007-4e0e-8576-78be81254802
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bc1b0b047bc8d594a34177cabf1081c0a1c67970
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399766"
---
# <a name="deriving-controls-from-a-standard-control"></a>Odvozování ovládacích prvků ze standardního ovládacího prvku

Stejně jako u libovolné [CWnd](../mfc/reference/cwnd-class.md)-odvozené třídy, můžete změnit chování ovládacího prvku pomocí odvození nové třídy z existující třídy ovládacího prvku.

### <a name="to-create-a-derived-control-class"></a>Chcete-li vytvořit třídu odvozenou ovládacího prvku

1. Odvodit třídu z existující třídy ovládacího prvku a volitelně můžete přepsat `Create` členské funkce tak, že poskytuje nezbytné argumenty, které mají základní třídy `Create` funkce.

1. Zadejte popisovač zpráv členské funkce a mapování zpráv položky k úpravě chování ovládacího prvku v reakci na konkrétní zprávy Windows. Zobrazit [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md).

1. Zadejte nové členské funkce rozšíření funkce pro ovládací prvek (volitelné).

Použití odvozené ovládacího prvku v dialogovém okně vyžaduje další práci. Typy a umístění ovládacích prvků v dialogovém okně jsou obvykle určeny v prostředku šablony dialogového okna. Pokud vytvoříte třídu odvozenou ovládacího prvku, nelze zadat v šabloně dialogu vzhledem k tomu, že kompilátor prostředků neví nic o odvozené třídy.

#### <a name="to-place-your-derived-control-in-a-dialog-box"></a>Umístit odvozené ovládacího prvku do dialogového okna

1. V deklaraci třídy odvozené dialogové okno vložte objekt třídy odvozené ovládací prvek.

1. Přepsat `OnInitDialog` členské funkce ve vlastní třídy dialogového okna pro volání `SubclassDlgItem` členské funkce odvozené ovládacího prvku.

`SubclassDlgItem` "dynamicky podtřídy" ovládací prvek vytvořen z šablony dialogového okna. Když je dynamicky rozčleněný ovládací prvek, integrovat do Windows, zpracování nějaké zprávy v rámci vlastní aplikace pak předávání zbývající zpráv do Windows. Další informace najdete v tématu [SubclassDlgItem](../mfc/reference/cwnd-class.md#subclassdlgitem) členské funkce třídy `CWnd` v *odkaz knihovny MFC*. Následující příklad ukazuje, jak můžete například napsat přepsání `OnInitDialog` volat `SubclassDlgItem`:

[!code-cpp[NVC_MFCControlLadenDialog#3](../mfc/codesnippet/cpp/deriving-controls-from-a-standard-control_1.cpp)]

Protože odvozené ovládací prvek je vložena do třídy dialogového okna, bude vytvořen při vytvořený dialogových oken a ho bude zničen při zničení dialogových oken. Porovnat tento kód v příkladu v [přidání ovládacích prvků podle ruční](../mfc/adding-controls-by-hand.md).

## <a name="see-also"></a>Viz také

[Příprava a použití ovládacích prvků](../mfc/making-and-using-controls.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

