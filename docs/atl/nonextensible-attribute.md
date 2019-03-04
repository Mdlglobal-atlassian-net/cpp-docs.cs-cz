---
title: nonextensible – atribut
ms.date: 11/04/2016
f1_keywords:
- nonextensible
helpviewer_keywords:
- nonextensible attribute
- dual interfaces, nonextensible attribute
ms.assetid: 02a4a18b-ffd3-4d53-8fd1-feb1c05ad5ac
ms.openlocfilehash: 5aa5b8514435e9876500daa4d92504d75eb6dc23
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57257628"
---
# <a name="nonextensible-attribute"></a>nonextensible – atribut

Pokud nebude v době běhu rozšířit duální rozhraní (to znamená, že neposkytne metody nebo vlastnosti prostřednictvím `IDispatch::Invoke` , které nejsou k dispozici prostřednictvím tabulku vtable), byste měli použít **nonextensible –** atribut do vašeho rozhraní definice. Tento atribut obsahuje informace, které jazyky klienta (například Visual Basic), které slouží k povolení ověření úplného kódu v době kompilace. Pokud tento atribut není zadán, může zůstat chyby skryté v klientském kódu až do spuštění.

Další informace o **nerozšiřitelnou kategorii** atribut a příklad najdete v tématu [nerozšiřitelnou kategorii](../windows/nonextensible.md).

## <a name="see-also"></a>Viz také:

[Duální rozhraní a ATL](../atl/dual-interfaces-and-atl.md)
