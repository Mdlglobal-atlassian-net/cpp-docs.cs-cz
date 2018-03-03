---
title: "Pomocí CArchive &lt; &lt; a &gt; &gt; operátory | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CArchive
dev_langs:
- C++
helpviewer_keywords:
- objects [MFC], loading from previously stored values
- CArchive class [MFC], storing and loading objects
- CArchive class [MFC], operators
ms.assetid: 56aef326-02dc-4992-8282-f0a4b78a064e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0ab2da8cc885f94bf15164ff17fdef2b2af13a41
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="using-the-carchive-ltlt-and-gtgt-operators"></a>Pomocí CArchive &lt; &lt; a &gt; &gt; operátory
`CArchive`poskytuje <\< a >> operátory pro zápis a čtení jednoduché datové typy a také `CObject`s do a ze souboru.  
  
#### <a name="to-store-an-object-in-a-file-via-an-archive"></a>K ukládání objektů v souboru prostřednictvím archivu  
  
1.  Následující příklad ukazuje, jak k ukládání objektů v souboru prostřednictvím archivu:  
  
     [!code-cpp[NVC_MFCSerialization#7](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_1.cpp)]  
  
#### <a name="to-load-an-object-from-a-value-previously-stored-in-a-file"></a>K načtení objektu z hodnoty dříve uložené v souboru  
  
1.  Následující příklad ukazuje, jak načíst objekt z hodnoty dříve uložené v souboru:  
  
     [!code-cpp[NVC_MFCSerialization#8](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_2.cpp)]  
  
 Obvykle, uložení a načtení dat do a ze souboru prostřednictvím archivu v `Serialize` funkce `CObject`-odvozené třídy, které je nutné mít deklarovat s **DECLARE_SERIALIZE** makro. Odkaz na `CArchive` objekt předaný vaší `Serialize` funkce. Volání `IsLoading` funkce `CArchive` objekt, který chcete určit, zda `Serialize` funkce byla volána k načtení dat ze souboru nebo ukládání dat do souboru.  
  
 `Serialize` Funkce serializable `CObject`-odvozené třídy obvykle má tento formát:  
  
 [!code-cpp[NVC_MFCSerialization#9](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_3.cpp)]  
  
 Výše uvedené šablony kód je přesně stejný jako ten, který je pro vytvoří objekty AppWizard `Serialize` funkce dokumentu (třídy odvozené od **CDocument)**. Tato šablona kódu umožňuje psát kód, který je snazší zkontrolovat, protože kód ukládání a načítání kódu by měla být vždy paralelní, jako v následujícím příkladu:  
  
 [!code-cpp[NVC_MFCSerialization#10](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_4.cpp)]  
  
 Definuje knihovny  **< \<**  a  **>>**  operátory `CArchive` jako první operand a následující datové typy a typy tříd jako druhý operand :  
  
||||  
|-|-|-|  
|`CObject*`|**VELIKOST a CSize**|**float**|  
|**WORD**|`CString`|**BOD** a`CPoint`|  
|`DWORD`|**BAJTŮ**|`RECT`a`CRect`|  
|**Double**|**DLOUHÁ**|`CTime`a`CTimeSpan`|  
|`Int`|**COleCurrency**|`COleVariant`|  
|`COleDateTime`|`COleDateTimeSpan`||  
  
> [!NOTE]
>  Ukládání a načítání `CObject`s prostřednictvím archivu vyžaduje další pozornost. Další informace najdete v tématu [ukládání a načítání objektů CObject prostřednictvím archivu](../mfc/storing-and-loading-cobjects-via-an-archive.md).  
  
 **CArchive <\<**  a  **>>**  operátory vždy vrátí odkaz na `CArchive` objekt, který je první operand. To vám umožní řetězit k operátory, jak je uvedeno dále:  
  
 [!code-cpp[NVC_MFCSerialization#11](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_5.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Serializace: Serializace objektu](../mfc/serialization-serializing-an-object.md)

