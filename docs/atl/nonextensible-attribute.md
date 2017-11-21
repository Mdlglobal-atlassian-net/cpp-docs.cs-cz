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
ms.openlocfilehash: 54c76d640171a6068421ff4199b6e77480db28d7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="nonextensible-attribute"></a>nonextensible – atribut
Pokud nebude v době běhu rozšířit duální rozhraní (to znamená, nebudou zajišťovat metody nebo vlastnosti prostřednictvím **volání metody IDispatch::Invoke** nejsou k dispozici prostřednictvím tabulce vtable), byste měli použít **nonextensible –** atribut vaše definice rozhraní. Tento atribut obsahuje informace, které jazyky klienta (například Visual Basic), které slouží k povolení ověření úplného kódu v době kompilace. Pokud je tento atribut není zadaný, mohou zůstat chyby skryté v klientském kódu až při spuštění.  
  
 Další informace o **nonextensible –** atribut a příklad najdete v části [nonextensible –](../windows/nonextensible.md).  
  
## <a name="see-also"></a>Viz také  
 [Duální rozhraní a knihovny ATL](../atl/dual-interfaces-and-atl.md)

