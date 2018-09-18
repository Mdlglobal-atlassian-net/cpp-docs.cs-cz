---
title: Příkaz obslužné rutiny pro záznam posouvání (přístup k datům MFC) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- record views [C++], scrolling
- record scrolling [C++]
- scrolling records
ms.assetid: f8b13477-2a37-459e-a30c-806fb78165ac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b51a6e9c9cf9516ed86066f712a17fea69c3cb50
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112236"
---
# <a name="command-handlers-for-record-scrolling--mfc-data-access"></a>Obslužné rutiny příkazů pro záznam posouvání (přístup k datům MFC)

[CRecordView](../mfc/reference/crecordview-class.md) třída poskytuje výchozí zpracování příkazů pro následující standardní příkazy:  
  
- ID_RECORD_MOVE_FIRST  
  
- ID_RECORD_MOVE_LAST  
  
- ID_RECORD_MOVE_NEXT  
  
- ID_RECORD_MOVE_PREV  
  
`OnMove` Členskou funkci poskytuje výchozí příkaz zpracování pro všechny čtyři příkazy, které se pohybují mezi záznamy. Tyto příkazy jsou používány, RFX (nebo DFX) načte nový záznam do sady záznamů v polích a DDX přesune hodnoty do ovládacích prvků formuláře záznamu. Informace o RFX najdete v tématu [výměna pole záznamu (RFX)](../data/odbc/record-field-exchange-rfx.md).  
  
> [!NOTE]
>  Nezapomeňte použít tyto identifikátory standardních příkazů pro všechny objekty uživatelského rozhraní přidružené k standardní navigace mezi příkazy.  
  
## <a name="see-also"></a>Viz také  

[Podpora navigace v zobrazení záznamu](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)