---
title: "Je nutné odvozovat z objektu CObject novou třídu? | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CObject
dev_langs:
- C++
helpviewer_keywords:
- derived classes [MFC], from CObject
- CObject class [MFC], when to use
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c485bba4d62d279b0f17b887080284940a8bbdd5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>Je nutné odvozovat z objektu CObject novou třídu?
Ne, můžete si.  
  
 Odvození třídy z [CObject](../mfc/reference/cobject-class.md) Pokud budete potřebovat zařízení, které poskytuje, jako je například serializace nebo dynamické creatability. Mnoho datových tříd, které jsou potřeba serializovat na soubory, proto je často vhodné odvozena z `CObject`. Pro příklad třídy odvozené od `CObject`, najdete v článku [Scribble ukázka](../visual-cpp-samples.md).  
  
## <a name="see-also"></a>Viz také  
 [CObject – třída: Nejčastější dotazy](../mfc/cobject-class-frequently-asked-questions.md)
