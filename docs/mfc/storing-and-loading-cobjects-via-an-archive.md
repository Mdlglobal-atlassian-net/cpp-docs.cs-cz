---
title: Ukládání a načítání objektů CObject prostřednictvím archivu | Microsoft Docs
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
- CObjects [MFC], loading through archives
- CArchive class [MFC], storing and loading objects
- Serialize method, vs. CArchive operators
- CObject class [MFC], CArchive objects
- CObjects [MFC]
ms.assetid: a829b6dd-bc31-47e0-8108-fbb946722db9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7a2dc227815f8888b85784ea92e58b3e91ffc83a
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954972"
---
# <a name="storing-and-loading-cobjects-via-an-archive"></a>Ukládání a načítání objektů CObject prostřednictvím archivu
Ukládání a načítání `CObject`s prostřednictvím archivu vyžaduje další pozornost. V některých případech by měly volat `Serialize` funkce objektu, kde `CArchive` objekt je parametr `Serialize` volání, na rozdíl od použití **< \<** nebo **>>** operátor z `CArchive`. Fakt, který je třeba vzít v úvahu důležité je, že `CArchive` **>>** operátor konstrukce `CObject` v paměti na základě `CRuntimeClass` informace o ukládání archivu dříve zapíše do souboru.  
  
 Proto, ať už používáte `CArchive` **< \<** a **>>** operátory porovnání volání `Serialize`, závisí na tom, zda jste *potřebovat* načítání archivu do dynamicky rekonstrukci objektu na základě dříve uložené `CRuntimeClass` informace. Použití `Serialize` funkce v následujících případech:  
  
-   Při deserializaci objektu, znáte přesnou třída objektu předem.  
  
-   Při deserializaci objektu, máte již pro něj přidělené paměti.  
  
> [!CAUTION]
>  Pokud načtení pomocí objektu `Serialize` funkce, musí také uložit objekt pomocí `Serialize` funkce. Neukládejte pomocí `CArchive` **<<** operátor a potom pomocí zatížení `Serialize` funkce nebo úložiště pomocí `Serialize` funkce a pak můžete načíst pomocí `CArchive >>` operátor.  
  
 Následující příklad ilustruje případy:  
  
 [!code-cpp[NVC_MFCSerialization#36](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_1.h)]  
  
 [!code-cpp[NVC_MFCSerialization#37](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_2.cpp)]  
  
 V souhrnu, pokud serializovatelné třídy definuje embedded `CObject` jako člena, měli byste *není* použít `CArchive` **< \<** a **>>** operátory pro tento objekt, ale měla by volat `Serialize` funkce místo. Navíc pokud serializovatelné třídy definuje ukazatel `CObject` (nebo objekt odvozené od `CObject`) jako člena, ale konstrukce tento druhý objekt v jeho vlastní konstruktoru, měli byste také zavolat `Serialize`.  
  
## <a name="see-also"></a>Viz také  
 [Serializace: Serializace objektu](../mfc/serialization-serializing-an-object.md)

