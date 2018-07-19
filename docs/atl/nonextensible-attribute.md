---
title: nonextensible – atribut | Dokumentace Microsoftu
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
ms.openlocfilehash: 1112f533e2e38dd90b1693e8bd31e5896ebca5e7
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848429"
---
# <a name="nonextensible-attribute"></a>nonextensible – atribut
Pokud nebude v době běhu rozšířit duální rozhraní (to znamená, že neposkytne metody nebo vlastnosti prostřednictvím `IDispatch::Invoke` , které nejsou k dispozici prostřednictvím tabulku vtable), byste měli použít **nonextensible –** atribut do vašeho rozhraní definice. Tento atribut obsahuje informace, které jazyky klienta (například Visual Basic), které slouží k povolení ověření úplného kódu v době kompilace. Pokud tento atribut není zadán, může zůstat chyby skryté v klientském kódu až do spuštění.  
  
 Další informace o **nerozšiřitelnou kategorii** atribut a příklad najdete v tématu [nerozšiřitelnou kategorii](../windows/nonextensible.md).  
  
## <a name="see-also"></a>Viz také  
 [Duální rozhraní a ATL](../atl/dual-interfaces-and-atl.md)

