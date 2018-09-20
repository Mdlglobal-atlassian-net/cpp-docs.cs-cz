---
title: Použití CArchive &lt; &lt; a &gt; &gt; operátory | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CArchive
dev_langs:
- C++
helpviewer_keywords:
- objects [MFC], loading from previously stored values
- CArchive class [MFC], storing and loading objects
- CArchive class [MFC], operators
ms.assetid: 56aef326-02dc-4992-8282-f0a4b78a064e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 49ea94258c163c241243934f41d55d896d0d1fa2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46372454"
---
# <a name="using-the-carchive-ltlt-and-gtgt-operators"></a>Použití CArchive &lt; &lt; a &gt; &gt; operátory

`CArchive` poskytuje <\< a >> operátory pro zápis a čtení jednoduché datové typy a jednak `CObject`s do a ze souboru.

#### <a name="to-store-an-object-in-a-file-via-an-archive"></a>K uložení objektu v souboru prostřednictvím archivu

1. Následující příklad ukazuje, jak uložit objekt v souboru prostřednictvím archivu:

     [!code-cpp[NVC_MFCSerialization#7](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_1.cpp)]

#### <a name="to-load-an-object-from-a-value-previously-stored-in-a-file"></a>Chcete-li načíst objekt z hodnoty v souboru dříve uložena

1. Následující příklad ukazuje, jak načíst objekt z hodnoty dříve uložené v souboru:

     [!code-cpp[NVC_MFCSerialization#8](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_2.cpp)]

Obvykle, ukládání a načítání dat do a ze souboru prostřednictvím archivu v `Serialize` funkce `CObject`-odvozené třídy, které vám musí být deklarován s DECLARE_SERIALIZE – makro. Odkaz na `CArchive` objekt je předán do vaší `Serialize` funkce. Volání `IsLoading` funkce `CArchive` objektem pro určení, zda `Serialize` byla volána funkce k načtení dat ze souboru nebo ukládání dat do souboru.

`Serialize` Funkce serializovatelného `CObject`-odvozené třídy obvykle má následující formát:

[!code-cpp[NVC_MFCSerialization#9](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_3.cpp)]

Výše uvedené šablony kódu je přesně stejný jako jeden AppWizard nevytvoří pro `Serialize` funkce dokumentu (třída odvozená z `CDocument`). Tato šablona kódu vám pomůže psát kód, který bude jednodušší, pokud chcete zkontrolovat, protože kód pro uložení a načítání kódu by měla být vždy paralelně, jako v následujícím příkladu:

[!code-cpp[NVC_MFCSerialization#10](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_4.cpp)]

Definuje knihovnu **< \<** a **>>** operátory pro `CArchive` jako první operand a následující datové typy a typy tříd jako druhý operand :

||||
|-|-|-|
|`CObject*`|**VELIKOST** a `CSize`|**float**|
|**WORD**|`CString`|**BOD** a `CPoint`|
|`DWORD`|**BAJTŮ**|`RECT` a `CRect`|
|**Double**|**LONG**|`CTime` a `CTimeSpan`|
|`Int`|**COleCurrency**|`COleVariant`|
|`COleDateTime`|`COleDateTimeSpan`||

> [!NOTE]
>  Ukládání a načítání `CObject`s prostřednictvím archivu vyžaduje další zkoumání. Další informace najdete v tématu [ukládání a načítání objektů CObject prostřednictvím archivu](../mfc/storing-and-loading-cobjects-via-an-archive.md).

**CArchive <\<**  a **>>** operátory vždy vrátí odkaz na `CArchive` objekt, který je prvním operandem. To vám umožní řetězit operátory, jak je znázorněno níže:

[!code-cpp[NVC_MFCSerialization#11](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_5.cpp)]

## <a name="see-also"></a>Viz také

[Serializace: Serializace objektu](../mfc/serialization-serializing-an-object.md)

