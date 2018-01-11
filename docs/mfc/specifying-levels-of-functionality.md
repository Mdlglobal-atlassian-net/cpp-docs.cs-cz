---
title: "Určení úrovní funkčnosti | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CObject class [MFC], adding functionality to derived classes
- runtime [MFC], class information
- serialization [MFC], Cobject
- dynamic creation support
- levels [MFC], functionality in CObject
- run-time class [MFC], information support
- levels [MFC]
ms.assetid: 562669ba-c858-4f66-b5f1-b3beeea4f486
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 13a2897d5e442794198870e7f6bed36196744888
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="specifying-levels-of-functionality"></a>Určení úrovní funkčnosti
Tento článek popisuje, jak přidat následující úrovně funkcí, které vaše [CObject](../mfc/reference/cobject-class.md)-odvozené třídy:  
  
-   [Informace o run-time třída](#_core_to_add_run.2d.time_class_information)  
  
-   [Podpora dynamického vytváření](#_core_to_add_dynamic_creation_support)  
  
-   [Podpora serializace](#_core_to_add_serialization_support)  
  
 Obecné popis `CObject` funkce, najdete v článku [odvození třídy z objektu CObject](../mfc/deriving-a-class-from-cobject.md).  
  
-   [Informace o run-time třída](#_core_to_add_run.2d.time_class_information)  
#### <a name="_core_to_add_run.2d.time_class_information"></a>Chcete-li přidat informace run-time třída  
  
1.  Odvození třídě z `CObject`, jak je popsáno v [odvození třídy z objektu CObject](../mfc/deriving-a-class-from-cobject.md) článku.  
  
2.  Použití `DECLARE_DYNAMIC` makro ve vaší deklaraci třídy, jak je vidět tady:  
  
     [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/cpp/specifying-levels-of-functionality_1.h)]  
  
3.  Použití `IMPLEMENT_DYNAMIC` makro v souboru implementace (. CPP) vaší třídy. Toto makro přijímá jako argumenty název třídy a její základní třída následujícím způsobem:  
  
     [!code-cpp[NVC_MFCCObjectSample#3](../mfc/codesnippet/cpp/specifying-levels-of-functionality_2.cpp)]  
  
> [!NOTE]
>  Vždy uvést `IMPLEMENT_DYNAMIC` v souboru implementace (. CPP) pro třídu. `IMPLEMENT_DYNAMIC` – Makro by mělo být vyhodnoceno pouze jednou během kompilace a proto by neměl být použit v soubor rozhraní (. H), může potenciálně obsahovat více než jeden soubor.  
  
#### <a name="_core_to_add_dynamic_creation_support"></a>Chcete-li přidat Podpora dynamického vytváření  
  
1.  Odvození třídě z `CObject`.  
  
2.  Použití `DECLARE_DYNCREATE` makro v deklaraci třídy.  
  
3.  Definujte konstruktor bez argumentů (výchozí konstruktor).  
  
4.  Použití `IMPLEMENT_DYNCREATE` makro v souboru implementace třídy.  
  
#### <a name="_core_to_add_serialization_support"></a>Chcete-li přidat podporu serializace  
  
1.  Odvození třídě z `CObject`.  
  
2.  Přepsání `Serialize` – členská funkce.  
  
    > [!NOTE]
    >  Když zavoláte `Serialize` přímo, tedy nechcete k serializaci objektu prostřednictvím polymorfní ukazatele, vynechejte kroky 3 až 5.  
  
3.  Použití `DECLARE_SERIAL` makro v deklaraci třídy.  
  
4.  Definujte konstruktor bez argumentů (výchozí konstruktor).  
  
5.  Použití `IMPLEMENT_SERIAL` makro v souboru implementace třídy.  
  
> [!NOTE]
>  "Polymorfní ukazatel" odkazuje na objekt třídy (volání A) nebo do objektu všechny třídy odvozené od (indikované, B). K serializaci prostřednictvím polymorfní ukazatele, musíte určit rozhraní run-time třída objektu ho je serializace (B), protože může být objekt žádné třídy odvozené z některé základní třídy (A).  
  
 Další informace o tom, jak povolit serializace při odvození třídě z `CObject`, najdete v článcích [soubory v prostředí MFC](../mfc/files-in-mfc.md) a [serializace](../mfc/serialization-in-mfc.md).  
  
## <a name="see-also"></a>Viz také  
 [Odvození třídy z objektu CObject](../mfc/deriving-a-class-from-cobject.md)
