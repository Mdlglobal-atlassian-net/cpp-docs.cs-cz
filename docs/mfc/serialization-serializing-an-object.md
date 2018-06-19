---
title: 'Serializace: Serializace objektu | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- serializing objects [MFC]
- serialization [MFC], objects
- objects [MFC], serializing
ms.assetid: 1db772b1-ad55-4fcf-b133-126cca082510
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3439857f14f4c4fa78aa2df3e3da8e5c8941938d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379655"
---
# <a name="serialization-serializing-an-object"></a>Serializace: Serializace objektu
Článek [serializace: Příprava serializovatelné třídy](../mfc/serialization-making-a-serializable-class.md) ukazuje, jak vytvořit třídu serializable. Jakmile máte serializovatelné třídy, může serializovat objekty do a ze souboru pomocí třídy [CArchive](../mfc/reference/carchive-class.md) objektu. Tento článek vysvětluje:  
  
-   [Co je objekt CArchive](../mfc/what-is-a-carchive-object.md).  
  
-   [Dva způsoby vytvoření CArchive](../mfc/two-ways-to-create-a-carchive-object.md).  
  
-   [Postup použití CArchive <\< a >> operátory](../mfc/using-the-carchive-output-and-input-operators.md).  
  
-   [Ukládání a načítání objektů CObject prostřednictvím archivu](../mfc/storing-and-loading-cobjects-via-an-archive.md).  
  
 Můžete je nechat framework vytvořit archivu pro serializovatelný dokumentu nebo explicitně `CArchive` objektu sami. Přenášet data mezi soubor a serializovatelný objekt pomocí <\< a >> operátory `CArchive` nebo v některých případech voláním `Serialize` funkce `CObject`-odvozené třídy.  
  
## <a name="see-also"></a>Viz také  
 [Serializace](../mfc/serialization-in-mfc.md)

