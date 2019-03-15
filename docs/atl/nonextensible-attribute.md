---
title: nonextensible – atribut
ms.date: 11/04/2016
helpviewer_keywords:
- nonextensible attribute
- dual interfaces, nonextensible attribute
ms.assetid: 02a4a18b-ffd3-4d53-8fd1-feb1c05ad5ac
ms.openlocfilehash: cc57acb8bd7bc3e32c764606da651f57316ceabf
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811846"
---
# <a name="nonextensible-attribute"></a>nonextensible – atribut

Pokud nebude v době běhu rozšířit duální rozhraní (to znamená, že neposkytne metody nebo vlastnosti prostřednictvím `IDispatch::Invoke` , které nejsou k dispozici prostřednictvím tabulku vtable), byste měli použít **nonextensible –** atribut do vašeho rozhraní definice. Tento atribut obsahuje informace, které jazyky klienta (například Visual Basic), které slouží k povolení ověření úplného kódu v době kompilace. Pokud tento atribut není zadán, může zůstat chyby skryté v klientském kódu až do spuštění.

Další informace o **nerozšiřitelnou kategorii** atribut a příklad najdete v tématu [nerozšiřitelnou kategorii](../windows/nonextensible.md).

## <a name="see-also"></a>Viz také:

[Duální rozhraní a ATL](../atl/dual-interfaces-and-atl.md)
