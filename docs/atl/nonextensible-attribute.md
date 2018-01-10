---
title: "nonextensible – atribut | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: nonextensible
dev_langs: C++
helpviewer_keywords:
- nonextensible attribute
- dual interfaces, nonextensible attribute
ms.assetid: 02a4a18b-ffd3-4d53-8fd1-feb1c05ad5ac
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: af16748bb3b2048ce854ccc7a03b2400039184a6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="nonextensible-attribute"></a>nonextensible – atribut
Pokud nebude v době běhu rozšířit duální rozhraní (to znamená, nebudou zajišťovat metody nebo vlastnosti prostřednictvím **volání metody IDispatch::Invoke** nejsou k dispozici prostřednictvím tabulce vtable), byste měli použít **nonextensible –** atribut vaše definice rozhraní. Tento atribut obsahuje informace, které jazyky klienta (například Visual Basic), které slouží k povolení ověření úplného kódu v době kompilace. Pokud je tento atribut není zadaný, mohou zůstat chyby skryté v klientském kódu až při spuštění.  
  
 Další informace o **nonextensible –** atribut a příklad najdete v části [nonextensible –](../windows/nonextensible.md).  
  
## <a name="see-also"></a>Viz také  
 [Duální rozhraní a ATL](../atl/dual-interfaces-and-atl.md)

