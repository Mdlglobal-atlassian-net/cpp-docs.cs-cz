---
title: Je nutné odvozovat z objektu CObject novou třídu? | Dokumenty Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CObject
dev_langs:
- C++
helpviewer_keywords:
- derived classes [MFC], from CObject
- CObject class [MFC], when to use
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ec080e556b57afadbc3d958f4dba5ac6393108aa
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408905"
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>Je nutné odvozovat z objektu CObject novou třídu?

Ne, nemusíte.

Odvodit třídu z [CObject](../mfc/reference/cobject-class.md) když potřebujete zařízení, které poskytuje, jako je například serializace nebo dynamické creatability. Mnoho datových tříd muset být serializován do souborů, proto je často vhodné k odvození z `CObject`. Pro příklad třídy odvozené z `CObject`, najdete v článku [ukázky Scribble](../visual-cpp-samples.md).

## <a name="see-also"></a>Viz také

[CObject – třída: Nejčastější dotazy](../mfc/cobject-class-frequently-asked-questions.md)
