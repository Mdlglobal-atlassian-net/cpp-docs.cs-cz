---
title: Je nutné odvozovat z objektu CObject novou třídu?
ms.date: 11/04/2016
f1_keywords:
- CObject
helpviewer_keywords:
- derived classes [MFC], from CObject
- CObject class [MFC], when to use
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
ms.openlocfilehash: c2361967dcfce5e46aeec65ade3d7056b362949d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636602"
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>Je nutné odvozovat z objektu CObject novou třídu?

Ne, nemusíte.

Odvodit třídu z [CObject](../mfc/reference/cobject-class.md) když potřebujete zařízení, které poskytuje, jako je například serializace nebo dynamické creatability. Mnoho datových tříd muset být serializován do souborů, proto je často vhodné k odvození z `CObject`. Pro příklad třídy odvozené z `CObject`, najdete v článku [ukázky Scribble](../visual-cpp-samples.md).

## <a name="see-also"></a>Viz také

[CObject – třída: Nejčastější dotazy](../mfc/cobject-class-frequently-asked-questions.md)
