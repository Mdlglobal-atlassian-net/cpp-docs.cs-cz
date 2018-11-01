---
title: Určení úrovní funkčnosti
ms.date: 11/04/2016
helpviewer_keywords:
- CObject class [MFC], adding functionality to derived classes
- runtime [MFC], class information
- serialization [MFC], Cobject
- dynamic creation support
- levels [MFC], functionality in CObject
- run-time class [MFC], information support
- levels [MFC]
ms.assetid: 562669ba-c858-4f66-b5f1-b3beeea4f486
ms.openlocfilehash: 3fb9b18712b24046e05f05834caaac2819fb73dc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494650"
---
# <a name="specifying-levels-of-functionality"></a>Určení úrovní funkčnosti

Tento článek popisuje, jak přidat následující úrovní funkčnosti do vaší [CObject](../mfc/reference/cobject-class.md)-odvozené třídy:

- [Informace o třídě za běhu](#_core_to_add_run.2d.time_class_information)

- [Podpora dynamického vytváření](#_core_to_add_dynamic_creation_support)

- [Podpora serializace](#_core_to_add_serialization_support)

Pro obecný popis `CObject` funkčnosti, najdete v článku [odvození třídy z objektu CObject](../mfc/deriving-a-class-from-cobject.md).

- [Informace o třídě za běhu](#_core_to_add_run.2d.time_class_information)
#### <a name="_core_to_add_run.2d.time_class_information"></a> Chcete-li přidat informace o třídě za běhu

1. Odvodit třídu z `CObject`, jak je popsáno v [odvození třídy z objektu CObject](../mfc/deriving-a-class-from-cobject.md) článku.

1. DECLARE_DYNAMIC – makro použijte v deklaraci vaší třídy, jak je znázorněno zde:

   [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/cpp/specifying-levels-of-functionality_1.h)]

1. V souboru implementace použijte IMPLEMENT_DYNAMIC – makro (. CPP) vaší třídy. Toto makro přijímá jako argumenty název třídy a její základní třídě, následujícím způsobem:

   [!code-cpp[NVC_MFCCObjectSample#3](../mfc/codesnippet/cpp/specifying-levels-of-functionality_2.cpp)]

> [!NOTE]
>  Vždy umístěte IMPLEMENT_DYNAMIC v souboru implementace (. CPP) pro vaši třídu. IMPLEMENT_DYNAMIC – makro by se mělo vyhodnotit pouze jednou během kompilaci a proto by neměl být použit v souboru rozhraní (. H), které můžou potenciálně obsahovat více než jeden soubor.

#### <a name="_core_to_add_dynamic_creation_support"></a> Chcete-li přidat Podpora dynamického vytváření

1. Odvodit třídu z `CObject`.

1. DECLARE_DYNCREATE – makro Použíjte v deklaraci třídy.

1. Definujte konstruktor bez argumentů (výchozího konstruktoru).

1. IMPLEMENT_DYNCREATE – makro Použíjte v souboru implementace třídy.

#### <a name="_core_to_add_serialization_support"></a> Chcete-li přidat podporu serializace

1. Odvodit třídu z `CObject`.

1. Přepsat `Serialize` členskou funkci.

    > [!NOTE]
    >  Při volání `Serialize` přímo, to znamená, že nechcete k serializaci objektu prostřednictvím polymorfní ukazatele, vynechejte kroky 3 až 5.

1. DECLARE_SERIAL – makro Použíjte v deklaraci třídy.

1. Definujte konstruktor bez argumentů (výchozího konstruktoru).

1. IMPLEMENT_SERIAL – makro Použíjte v souboru implementace třídy.

> [!NOTE]
>  "Polymorfní ukazatel" odkazuje na objekt třídy (říkat A) nebo na objekt libovolné třídě odvozené z (například B). K serializaci prostřednictvím polymorfní ukazatele, musíte určit rozhraní run-time třída objektu ho je serializace (B), protože může být objekt libovolné třídě odvozené z některé základní třídu (A).

Podrobné informace o tom, jak povolit serializace při odvodit třídu z `CObject`, najdete v článcích [soubory v prostředí MFC](../mfc/files-in-mfc.md) a [serializace](../mfc/serialization-in-mfc.md).

## <a name="see-also"></a>Viz také

[Odvození třídy z objektu CObject](../mfc/deriving-a-class-from-cobject.md)
