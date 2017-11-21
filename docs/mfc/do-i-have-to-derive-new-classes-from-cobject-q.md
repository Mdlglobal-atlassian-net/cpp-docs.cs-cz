---
title: "Je nutné odvozovat z objektu CObject novou třídu? | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CObject
dev_langs: C++
helpviewer_keywords:
- derived classes [MFC], from CObject
- CObject class [MFC], when to use
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 10254dbfe4f8db61aebfaa934d86adee36b64c83
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>Je nutné odvozovat z objektu CObject novou třídu?
Ne, můžete si.  
  
 Odvození třídy z [CObject](../mfc/reference/cobject-class.md) Pokud budete potřebovat zařízení, které poskytuje, jako je například serializace nebo dynamické creatability. Mnoho datových tříd, které jsou potřeba serializovat na soubory, proto je často vhodné odvozena z `CObject`. Pro příklad třídy odvozené od `CObject`, najdete v článku [Scribble ukázka](../visual-cpp-samples.md).  
  
## <a name="see-also"></a>Viz také  
 [CObject – třída: Nejčastější dotazy](../mfc/cobject-class-frequently-asked-questions.md)
