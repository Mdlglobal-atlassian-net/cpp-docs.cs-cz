---
title: Určení úrovní funkčnosti | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CObject class [MFC], adding functionality to derived classes
- runtime [MFC], class information
- serialization [MFC], Cobject
- dynamic creation support
- levels [MFC], functionality in CObject
- run-time class [MFC], information support
- levels [MFC]
ms.assetid: 562669ba-c858-4f66-b5f1-b3beeea4f486
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 425cbf2f9c769dbbb6cd054b9af6b7f6f5fc9d52
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954462"
---
# <a name="specifying-levels-of-functionality"></a>Určení úrovní funkčnosti
Tento článek popisuje, jak přidat následující úrovně funkcí, které vaše [CObject](../mfc/reference/cobject-class.md)-odvozené třídy:  
  
-   [Informace o run-time třída](#_core_to_add_run.2d.time_class_information)  
  
-   [Podpora dynamického vytváření](#_core_to_add_dynamic_creation_support)  
  
-   [Podpora serializace](#_core_to_add_serialization_support)  
  
 Obecné popis `CObject` funkce, najdete v článku [odvození třídy z objektu CObject](../mfc/deriving-a-class-from-cobject.md).  
  
-   [Informace o run-time třída](#_core_to_add_run.2d.time_class_information)  
#### <a name="_core_to_add_run.2d.time_class_information"></a> Chcete-li přidat informace run-time třída  
  
1.  Odvození třídě z `CObject`, jak je popsáno v [odvození třídy z objektu CObject](../mfc/deriving-a-class-from-cobject.md) článku.  
  
2.  Použijte DECLARE_DYNAMIC – makro v deklaraci vaší třídy, jak je vidět tady:  
  
     [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/cpp/specifying-levels-of-functionality_1.h)]  
  
3.  Použít implement_dynamic – makro v souboru implementace (. CPP) vaší třídy. Toto makro přijímá jako argumenty název třídy a její základní třída následujícím způsobem:  
  
     [!code-cpp[NVC_MFCCObjectSample#3](../mfc/codesnippet/cpp/specifying-levels-of-functionality_2.cpp)]  
  
> [!NOTE]
>  Vždy uvést implement_dynamic – v souboru implementace (. CPP) pro třídu. Implement_dynamic – makro by mělo být vyhodnoceno pouze jednou během kompilace a proto by neměl být použit v soubor rozhraní (. H), může potenciálně obsahovat více než jeden soubor.  
  
#### <a name="_core_to_add_dynamic_creation_support"></a> Chcete-li přidat Podpora dynamického vytváření  
  
1.  Odvození třídě z `CObject`.  
  
2.  DECLARE_DYNCREATE – makro Použíjte v deklaraci třídy.  
  
3.  Definujte konstruktor bez argumentů (výchozí konstruktor).  
  
4.  IMPLEMENT_DYNCREATE – makro Použíjte v souboru implementace třídy.  
  
#### <a name="_core_to_add_serialization_support"></a> Chcete-li přidat podporu serializace  
  
1.  Odvození třídě z `CObject`.  
  
2.  Přepsání `Serialize` – členská funkce.  
  
    > [!NOTE]
    >  Když zavoláte `Serialize` přímo, tedy nechcete k serializaci objektu prostřednictvím polymorfní ukazatele, vynechejte kroky 3 až 5.  
  
3.  Declare_serial – makro Použíjte v deklaraci třídy.  
  
4.  Definujte konstruktor bez argumentů (výchozí konstruktor).  
  
5.  Implement_serial – makro Použíjte v souboru implementace třídy.  
  
> [!NOTE]
>  "Polymorfní ukazatel" odkazuje na objekt třídy (volání A) nebo do objektu všechny třídy odvozené od (indikované, B). K serializaci prostřednictvím polymorfní ukazatele, musíte určit rozhraní run-time třída objektu ho je serializace (B), protože může být objekt žádné třídy odvozené z některé základní třídy (A).  
  
 Další informace o tom, jak povolit serializace při odvození třídě z `CObject`, najdete v článcích [soubory v prostředí MFC](../mfc/files-in-mfc.md) a [serializace](../mfc/serialization-in-mfc.md).  
  
## <a name="see-also"></a>Viz také  
 [Odvození třídy z objektu CObject](../mfc/deriving-a-class-from-cobject.md)
