---
title: Agregace
ms.date: 11/04/2016
helpviewer_keywords:
- aggregation [C++]
- aggregate objects [C++]
ms.assetid: 7125bb8e-b269-4b50-9bba-295b467a54cc
ms.openlocfilehash: d5a09dcd8c289447491ebc7111a77549166a7d00
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633408"
---
# <a name="aggregation"></a>Agregace

Existují situace, kdy implementátor objektu chtěli využívat služby nabízené objektem jiného, předem připravené. Kromě toho je vhodné tento druhý objekt jako přirozenou součástí první. COM dosahuje oba z těchto cílů prostřednictvím členství ve skupině a agregaci.

Agregace znamená, že nadřazený objekt (vnějšího) vytvoří obsaženého objektu (vnitřní) jako součást procesu vytváření a rozhraní vnitřní objekt jsou viditelné ve vnější. Objekt umožňuje sám být agregovatelné, nebo ne. Pokud se jedná, pak musí podstoupit určitá pravidla pro agregaci fungovala správně.

Především, všechny `IUnknown` volání metod na obsaženého objektu musí delegovat do obsahujícího objektu.

## <a name="see-also"></a>Viz také

[Úvod do modelu COM](../atl/introduction-to-com.md)<br/>
[Opětovné použití objektů](/windows/desktop/com/reusing-objects)

