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
ms.openlocfilehash: 73edae463051aca3ecafac53ae6200df103b8d90
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762138"
---
# <a name="nonextensible-attribute"></a>nonextensible – atribut

Pokud nebude v době běhu rozšířit duální rozhraní (to znamená, že neposkytne metody nebo vlastnosti prostřednictvím `IDispatch::Invoke` , které nejsou k dispozici prostřednictvím tabulku vtable), byste měli použít **nonextensible –** atribut do vašeho rozhraní definice. Tento atribut obsahuje informace, které jazyky klienta (například Visual Basic), které slouží k povolení ověření úplného kódu v době kompilace. Pokud tento atribut není zadán, může zůstat chyby skryté v klientském kódu až do spuštění.

Další informace o **nerozšiřitelnou kategorii** atribut a příklad najdete v tématu [nerozšiřitelnou kategorii](../windows/nonextensible.md).

## <a name="see-also"></a>Viz také

[Duální rozhraní a ATL](../atl/dual-interfaces-and-atl.md)

