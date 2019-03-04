---
title: Co je objekt CArchive
ms.date: 11/04/2016
f1_keywords:
- CArchive
helpviewer_keywords:
- archive objects [MFC]
- archives [MFC], for serialization
- buffers, serializable objects
- CArchive class [MFC], about CArchive class [MFC]
- buffering, serializable objects
ms.assetid: 843f1825-288d-4d89-a1fa-70e1f92d9b8b
ms.openlocfilehash: 4bae451168449ce3e120ba9d172a615864ac2157
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270394"
---
# <a name="what-is-a-carchive-object"></a>Co je objekt CArchive

A `CArchive` objekt, který poskytuje mechanismus bezpečnost typů vyrovnávací paměti pro zápis nebo čtení serializovatelné objekty do nebo z `CFile` objektu. Obvykle `CFile` objekt představuje soubor na disku, ale může také být souboru paměti (`CSharedFile` objektu), možná představující do schránky.

A uveden `CArchive` objekt buď úložišť (zapisuje, serializuje) dat nebo nahrávání (čtení, deserializuje) data, ale nikdy obojí. Životnost `CArchive` objektu je omezená na jednom průchodu přes zápis objektů do souboru nebo čtení objektů ze souboru. Díky tomu se dvěma postupně vytvořili `CArchive` objekty jsou nutné k serializaci dat do souboru a pak ho Deserializujte zpět ze souboru.

Není-li archiv ukládá objekty do souboru, připojí archivu `CRuntimeClass` název k objektům. Když jiný archivu načte objekty ze souboru do paměti, potom `CObject`-odvozené objekty jsou dynamicky znovu vytvořena na základě `CRuntimeClass` objektů. Daný objekt může odkazovat více než jednou, při zápisu do souboru pomocí ukládání archivu. Načítání archivu, ale bude rekonstruovat objekt pouze jednou. Podrobnosti o jak archiv připojí `CRuntimeClass` informace, které objekty a rekonstruuje objekty, s ohledem možné více odkazů, jsou popsány v [Technická poznámka 2](../mfc/tn002-persistent-object-data-format.md).

Podle data, je serializován do archivu, archivu nahromadí data, dokud jeho vyrovnávací paměť je plná. Pak archivu zapíše do vyrovnávací paměti `CFile` objekt, který odkazuje `CArchive` objektu. Podobně jak načíst data z archivu, čte data ze souboru do vyrovnávací paměti a potom z vyrovnávací paměti deserializovaného objektu. Tato ukládání do vyrovnávací paměti snižuje počet pokusů, které je pevný disk fyzicky čtení, tedy zvýšení výkonu vaší aplikace.

## <a name="see-also"></a>Viz také:

[Serializace: Serializace objektu](../mfc/serialization-serializing-an-object.md)
