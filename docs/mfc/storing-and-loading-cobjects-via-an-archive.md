---
title: "Ukládání a načítání objektů CObject prostřednictvím archivu | Microsoft Docs"
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
- CObjects [MFC], loading through archives
- CArchive class [MFC], storing and loading objects
- Serialize method, vs. CArchive operators
- CObject class [MFC], CArchive objects
- CObjects [MFC]
ms.assetid: a829b6dd-bc31-47e0-8108-fbb946722db9
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 23c403d5e872818345b319ea6786da6b2f42fabc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="storing-and-loading-cobjects-via-an-archive"></a>Ukládání a načítání objektů CObject prostřednictvím archivu
Ukládání a načítání `CObject`s prostřednictvím archivu vyžaduje další pozornost. V některých případech by měly volat `Serialize` funkce objektu, kde `CArchive` objekt je parametr `Serialize` volání, na rozdíl od použití  **< \<**  nebo  **>>**  operátor z `CArchive`. Fakt, který je třeba vzít v úvahu důležité je, že `CArchive`  **>>**  operátor konstrukce `CObject` v paměti na základě `CRuntimeClass` informace o ukládání archivu dříve zapíše do souboru.  
  
 Proto, ať už používáte `CArchive`  **< \<**  a  **>>**  operátory porovnání volání `Serialize`, závisí na tom, zda jste *potřebovat* načítání archivu do dynamicky rekonstrukci objektu na základě dříve uložené `CRuntimeClass` informace. Použití `Serialize` funkce v následujících případech:  
  
-   Při deserializaci objektu, znáte přesnou třída objektu předem.  
  
-   Při deserializaci objektu, máte již pro něj přidělené paměti.  
  
> [!CAUTION]
>  Pokud načtení pomocí objektu `Serialize` funkce, musí také uložit objekt pomocí `Serialize` funkce. Neukládejte pomocí `CArchive`  **<<**  operátor a potom pomocí zatížení `Serialize` funkce nebo úložiště pomocí `Serialize` funkce a pak můžete načíst pomocí **CArchive >>**operátor.  
  
 Následující příklad ilustruje případy:  
  
 [!code-cpp[NVC_MFCSerialization#36](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_1.h)]  
  
 [!code-cpp[NVC_MFCSerialization#37](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_2.cpp)]  
  
 V souhrnu, pokud serializovatelné třídy definuje embedded **CObjec**t jako člena, měli byste *není* použít `CArchive`  **< \<**  a  **>>**  operátory pro tento objekt, ale měla by volat `Serialize` funkce místo. Navíc pokud serializovatelné třídy definuje ukazatel `CObject` (nebo objekt odvozené od `CObject`) jako člena, ale konstrukce tento druhý objekt v jeho vlastní konstruktoru, měli byste také zavolat `Serialize`.  
  
## <a name="see-also"></a>Viz také  
 [Serializace: Serializace objektu](../mfc/serialization-serializing-an-object.md)
