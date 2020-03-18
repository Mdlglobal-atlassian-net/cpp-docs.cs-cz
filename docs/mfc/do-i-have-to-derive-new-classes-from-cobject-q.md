---
title: Je nutné odvozovat z objektu CObject novou třídu?
ms.date: 11/04/2016
helpviewer_keywords:
- derived classes [MFC], from CObject
- CObject class [MFC], when to use
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
ms.openlocfilehash: d38e589f371fc56f5566c56de7b19c366065a503
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446921"
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>Je nutné odvozovat z objektu CObject novou třídu?

Ne, nebudete.

Odvodit třídu z [CObject](../mfc/reference/cobject-class.md) , pokud potřebujete zařízení, která poskytuje, jako je například serializace nebo dynamické vytvoření. Mnoho datových tříd musí být serializovaných do souborů, takže je často vhodné je odvodit od `CObject`. Příklad třídy odvozené z `CObject`naleznete v [ukázce Klikyháky](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Viz také

[CObject – třída: Nejčastější dotazy](../mfc/cobject-class-frequently-asked-questions.md)
