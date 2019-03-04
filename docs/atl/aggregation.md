---
title: Aggregation
ms.date: 11/04/2016
helpviewer_keywords:
- aggregation [C++]
- aggregate objects [C++]
ms.assetid: 7125bb8e-b269-4b50-9bba-295b467a54cc
ms.openlocfilehash: 2eec7a801f9fe16bc48fc888d10ce413ec7e79db
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265428"
---
# <a name="aggregation"></a>Aggregation

Existují situace, kdy implementátor objektu chtěli využívat služby nabízené objektem jiného, předem připravené. Kromě toho je vhodné tento druhý objekt jako přirozenou součástí první. COM dosahuje oba z těchto cílů prostřednictvím členství ve skupině a agregaci.

Agregace znamená, že nadřazený objekt (vnějšího) vytvoří obsaženého objektu (vnitřní) jako součást procesu vytváření a rozhraní vnitřní objekt jsou viditelné ve vnější. Objekt umožňuje sám být agregovatelné, nebo ne. Pokud se jedná, pak musí podstoupit určitá pravidla pro agregaci fungovala správně.

Především, všechny `IUnknown` volání metod na obsaženého objektu musí delegovat do obsahujícího objektu.

## <a name="see-also"></a>Viz také:

[Úvod do modelu COM](../atl/introduction-to-com.md)<br/>
[Opětovné použití objektů](/windows/desktop/com/reusing-objects)
