---
title: Dialogové pruhy
ms.date: 11/19/2018
helpviewer_keywords:
- MFC, control bars
- CDialogBar class [MFC], dialog bars
- control bars [MFC], dialog bars
- dialog bars
- dialog bars [MFC], about dialog bars
ms.assetid: 485c8055-6bb0-4051-8417-dd2971499321
ms.openlocfilehash: e4e843327daba6f0aa468cb07394165bc70fa7f0
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58779505"
---
# <a name="dialog-bars"></a>Dialogové pruhy

Panel dialogového okna je panel nástrojů, typ z [ovládací panel](../mfc/control-bars.md) , který může obsahovat libovolný druh ovládacího prvku. Protože ale mají i charakteristiky nemodálního dialogového okna, [CDialogBar](../mfc/reference/cdialogbar-class.md) objekt, který poskytuje výkonnější panelu nástrojů.

Existuje několik klíčových rozdílů mezi panelu nástrojů a `CDialogBar` objektu. A `CDialogBar` objekt je vytvořen z prostředků šablony dialogového okna, které můžete vytvořit pomocí editoru dialogového okna Visual C++ a který může obsahovat jakýkoli typ ovládacího prvku Windows. Uživatel může kartu z ovládacího prvku na ovládací prvek. A můžete zadat na zarovnání styl, zarovnání dialogového pruhu s libovolnou část nadřazené okno rámce, nebo dokonce ponechte na místě, pokud je velikost nadřazené. Následující obrázek znázorňuje dialogového pruhu s širokou škálu ovládacích prvků.

![Panel dialogového okna VC](../mfc/media/vc378t1.gif "VC panel dialogového okna") <br/>
Panel dialogového okna

V ostatních ohledech, práci s `CDialogBar` objektu je podobné jako u nemodální dialogové okno. Použití editoru dialogových oken pro návrh a vytvoření prostředku dialogového okna.

Jednou z přednosti dialogové pruhy je, že obsahují ovládací prvky než tlačítka.

I když je normální odvozovat vlastní třídy dialogového okna z `CDialog`, můžete neodvozuje obvykle vlastní třída pro panel dialogového okna. Dialogové pruhy jsou rozšíření pro hlavní okno a jakékoli zpráv s oznámením ovládacího prvku panel dialogového okna, jako je například **BN_CLICKED** nebo **EN_CHANGE**, odešlou se do nadřazené okno panelu hlavního okna.

## <a name="see-also"></a>Viz také:

[Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)<br/>
[Ukázka](../overview/visual-cpp-samples.md)
