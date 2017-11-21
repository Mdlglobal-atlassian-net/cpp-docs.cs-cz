---
title: 'Serializace: Serializace objektu | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- serializing objects [MFC]
- serialization [MFC], objects
- objects [MFC], serializing
ms.assetid: 1db772b1-ad55-4fcf-b133-126cca082510
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1339f7ab6b226da9f233e523171e318209e99ee4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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

