---
title: nonextensible – atribut | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- nonextensible
dev_langs:
- C++
helpviewer_keywords:
- nonextensible attribute
- dual interfaces, nonextensible attribute
ms.assetid: 02a4a18b-ffd3-4d53-8fd1-feb1c05ad5ac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 40b4b79701862ca07e704aca098419479923ef1a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32355630"
---
# <a name="nonextensible-attribute"></a>nonextensible – atribut
Pokud nebude v době běhu rozšířit duální rozhraní (to znamená, nebudou zajišťovat metody nebo vlastnosti prostřednictvím **volání metody IDispatch::Invoke** nejsou k dispozici prostřednictvím tabulce vtable), byste měli použít **nonextensible –** atribut vaše definice rozhraní. Tento atribut obsahuje informace, které jazyky klienta (například Visual Basic), které slouží k povolení ověření úplného kódu v době kompilace. Pokud je tento atribut není zadaný, mohou zůstat chyby skryté v klientském kódu až při spuštění.  
  
 Další informace o **nonextensible –** atribut a příklad najdete v části [nonextensible –](../windows/nonextensible.md).  
  
## <a name="see-also"></a>Viz také  
 [Duální rozhraní a ATL](../atl/dual-interfaces-and-atl.md)

