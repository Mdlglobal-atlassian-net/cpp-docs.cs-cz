---
title: Použití archivu &lt; &lt; &gt; &gt; a operátorů
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], loading from previously stored values
- CArchive class [MFC], storing and loading objects
- CArchive class [MFC], operators
ms.assetid: 56aef326-02dc-4992-8282-f0a4b78a064e
ms.openlocfilehash: 91ea565867cc0cb3b27ad9d5597037b637cb6544
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368965"
---
# <a name="using-the-carchive-ltlt-and-gtgt-operators"></a>Použití archivu &lt; &lt; &gt; &gt; a operátorů

`CArchive`poskytuje \< <a >> operátory pro zápis `CObject`a čtení jednoduchých datových typů, stejně jako s do a ze souboru.

#### <a name="to-store-an-object-in-a-file-via-an-archive"></a>Uložení objektu do souboru prostřednictvím archivu

1. Následující příklad ukazuje, jak uložit objekt do souboru prostřednictvím archivu:

   [!code-cpp[NVC_MFCSerialization#7](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_1.cpp)]

#### <a name="to-load-an-object-from-a-value-previously-stored-in-a-file"></a>Načtení objektu z hodnoty dříve uložené v souboru

1. Následující příklad ukazuje, jak načíst objekt z hodnoty dříve uložené v souboru:

   [!code-cpp[NVC_MFCSerialization#8](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_2.cpp)]

Obvykle ukládáte a načítáte data do a `Serialize` ze `CObject`souboru prostřednictvím archivu ve funkcích odvozených tříd, které musíte deklarovat pomocí DECLARE_SERIALIZE makro. Odkaz na `CArchive` objekt je předán `Serialize` do funkce. Volání `IsLoading` funkce objektu `CArchive` k určení, `Serialize` zda byla funkce volána k načtení dat ze souboru nebo uložení dat do souboru.

Funkce `Serialize` serializovatelné `CObject`odvozené třídy má obvykle následující tvar:

[!code-cpp[NVC_MFCSerialization#9](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_3.cpp)]

Výše uvedená šablona kódu je přesně stejná `Serialize` jako ta, kterou Vytvoří `CDocument`AppWizard pro funkci dokumentu (třídu odvozenou od). Tato šablona kódu vám pomůže napsat kód, který je jednodušší zkontrolovat, protože ukládání kódu a načítací kód by měl být vždy paralelní, jako v následujícím příkladu:

[!code-cpp[NVC_MFCSerialization#10](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_4.cpp)]

Knihovna definuje ** < ** **>>** a `CArchive` operátory pro jako první operand a následující datové typy a typy tříd jako druhý operand:

||||
|-|-|-|
|`CObject*`|**VELIKOST** a`CSize`|**float**|
|**Slovo**|`CString`|**BOD** a`CPoint`|
|`DWORD`|**Bajt**|`RECT` a `CRect`|
|**Dvojité**|**Dlouhé**|`CTime` a `CTimeSpan`|
|`Int`|**COleCurrency**|`COleVariant`|
|`COleDateTime`|`COleDateTimeSpan`||

> [!NOTE]
> Ukládání a načítání `CObject`s přes archiv vyžaduje zvláštní pozornost. Další informace naleznete [v tématu Ukládání a načítání cobjects prostřednictvím archivu](../mfc/storing-and-loading-cobjects-via-an-archive.md).

**CArchive <\< ** **>>** a operátory vždy `CArchive` vrátit odkaz na objekt, který je první operand. To vám umožní řetězení obsluhy, jak je znázorněno níže:

[!code-cpp[NVC_MFCSerialization#11](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_5.cpp)]

## <a name="see-also"></a>Viz také

[Serializace: Serializace objektu](../mfc/serialization-serializing-an-object.md)
