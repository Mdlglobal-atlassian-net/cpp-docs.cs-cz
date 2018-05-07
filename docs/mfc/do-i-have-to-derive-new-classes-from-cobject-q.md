---
title: Je nutné odvozovat z objektu CObject novou třídu? | Microsoft Docs
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
ms.openlocfilehash: 51904ac06ae6c2db5586f8dc405f85145c5b1f30
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>Je nutné odvozovat z objektu CObject novou třídu?
Ne, můžete si.  
  
 Odvození třídy z [CObject](../mfc/reference/cobject-class.md) Pokud budete potřebovat zařízení, které poskytuje, jako je například serializace nebo dynamické creatability. Mnoho datových tříd, které jsou potřeba serializovat na soubory, proto je často vhodné odvozena z `CObject`. Pro příklad třídy odvozené od `CObject`, najdete v článku [Scribble ukázka](../visual-cpp-samples.md).  
  
## <a name="see-also"></a>Viz také  
 [CObject – třída: Nejčastější dotazy](../mfc/cobject-class-frequently-asked-questions.md)
