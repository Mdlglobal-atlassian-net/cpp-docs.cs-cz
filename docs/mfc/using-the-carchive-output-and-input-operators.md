---
title: Použití operátorů CArchive &lt;&lt; a &gt;&gt;
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], loading from previously stored values
- CArchive class [MFC], storing and loading objects
- CArchive class [MFC], operators
ms.assetid: 56aef326-02dc-4992-8282-f0a4b78a064e
ms.openlocfilehash: 8e175f35f2218341c69571c818711596180df4a6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442173"
---
# <a name="using-the-carchive-ltlt-and-gtgt-operators"></a>Použití operátorů CArchive &lt;&lt; a &gt;&gt;

`CArchive` poskytuje <\< a > > operátory pro psaní a čtení jednoduchých datových typů a také pro `CObject`s do a ze souboru.

#### <a name="to-store-an-object-in-a-file-via-an-archive"></a>Uložení objektu do souboru prostřednictvím archivu

1. Následující příklad ukazuje, jak uložit objekt do souboru prostřednictvím archivu:

   [!code-cpp[NVC_MFCSerialization#7](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_1.cpp)]

#### <a name="to-load-an-object-from-a-value-previously-stored-in-a-file"></a>Načtení objektu z hodnoty dříve uložené v souboru

1. Následující příklad ukazuje, jak načíst objekt z hodnoty dříve uložené v souboru:

   [!code-cpp[NVC_MFCSerialization#8](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_2.cpp)]

Obvykle ukládáte a načítáte data do a ze souboru prostřednictvím archivu ve funkcích `Serialize` `CObject`odvozené třídy, které musí být deklarovány s DECLARE_SERIALIZE makrem. Do funkce `Serialize` se předává odkaz na objekt `CArchive`. Voláním funkce `IsLoading` objektu `CArchive` určíte, zda byla volána funkce `Serialize` pro načtení dat ze souboru nebo uložení dat do souboru.

`Serialize` funkce serializovatelného `CObject`odvozené třídy má obvykle následující tvar:

[!code-cpp[NVC_MFCSerialization#9](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_3.cpp)]

Výše uvedená šablona kódu je přesně stejná jako jedna AppWizard vytvořena pro funkci `Serialize` dokumentu (třída odvozená z `CDocument`). Tato šablona kódu vám pomůže napsat kód, který je snazší kontrolovat, protože kód pro ukládání a načítání kódu by měl být vždy paralelní, jako v následujícím příkladu:

[!code-cpp[NVC_MFCSerialization#10](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_4.cpp)]

Knihovna definuje **<\<** a **>>** operátory pro `CArchive` jako první operand a následující datové typy a typy tříd jako druhý operand:

||||
|-|-|-|
|`CObject*`|**Velikost** a `CSize`|**float**|
|**WORD**|`CString`|**Point** a `CPoint`|
|`DWORD`|**BYTOVÉ**|`RECT` a `CRect`|
|**Klepat**|**DLOUHOU**|`CTime` a `CTimeSpan`|
|`Int`|**COleCurrency**|`COleVariant`|
|`COleDateTime`|`COleDateTimeSpan`||

> [!NOTE]
>  Ukládání a načítání `CObject`s prostřednictvím archivu vyžaduje další pozornost. Další informace najdete v tématu [ukládání a načítání objektů CObject prostřednictvím archivu](../mfc/storing-and-loading-cobjects-via-an-archive.md).

**CArchive <\<** a **>>** operátory vždycky vrátí odkaz na objekt `CArchive`, který je prvním operandem. To umožňuje zřetězení operátorů, jak je znázorněno níže:

[!code-cpp[NVC_MFCSerialization#11](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_5.cpp)]

## <a name="see-also"></a>Viz také

[Serializace: Serializace objektu](../mfc/serialization-serializing-an-object.md)
